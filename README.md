# DSA-LeetCode-Potd
# 2nd JAN 2025
Link for Ques : https://leetcode.com/problems/count-vowel-strings-in-ranges/description/?envType=daily-question&envId=2025-01-02

class Solution {
    public int[] vowelStrings(String[] word, int[][] queries) {
        int n = word.length;
        int[] prefixSum = new int[n+1];
        
        // Precompute prefix sums for valid vowel strings
        for (int i = 0; i < n; i++) {
            if (isVowelString(word[i])) {
                prefixSum[i + 1] = prefixSum[i] + 1;
            } else {
                prefixSum[i + 1] = prefixSum[i];
            }
        }
        
        int[] ans = new int[queries.length];
        for (int j = 0; j < queries.length; j++) {
            int start = queries[j][0];
            int end = queries[j][1];
            ans[j] = prefixSum[end + 1] - prefixSum[start];
        }
        return ans;
    }
    
    private boolean isVowelString(String s) {
        char start = s.charAt(0);
        char end = s.charAt(s.length() - 1);
        return isVowel(start) && isVowel(end);
    }
    
    private boolean isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    }
}
