public class Main {

    public static final int MAX_COUNT_SPLIT = 100;

    public static void main(String[] args) {
        first();
        second();
        third();
        four();



    }
    static void first() {

        // TODO научиться работать с матрицами
        System.out.println(" Первое задание ");
        int[][] matrix = {
                {8, 2, 1},
                {7, 5, 6},
                {4, 8, 9}
        };


        int max = matrix[0][0];
        int maxIndex = 0;

        for (int i = 1; i < matrix.length; i++) {
            if (matrix[i][0] > max) {
                max = matrix[i][0];
                maxIndex = i;
            }else {
                max = matrix[0][0];
            }
        }

        System.out.println("Максимальный элемент первого столбца: " + max);


        for (int i = 0; i < matrix.length; i++) {
            if (i != maxIndex) {
                for (int j = 0; j < matrix[i].length; j++) {
                    matrix[i][j] = matrix[i][j] * max;
                }
            }
        }


        System.out.println("Преобразованная матрица:");
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }
    static void second() {

        System.out.println(" Второе задание ");
        String sentence = "Топот капыт по полю летит";

        String[] words = sentence.split(" "); // разделяем строку на слова

        System.out.println("Палиндромы в предложении:");
        for (String word : words) {

            if (isPalindrome(word)) {
                System.out.println(word);
            }
        }
        System.out.println(" ");
    }
    static void third() {
        // TODO научиться определять число слов в предложении
        System.out.println(" Третье задание ");

        String sentence = "Определите число слов в предложении";
        String[] words = customSplit(sentence, " ");


        System.out.println("Число слов в предложении: " + words.length);
        System.out.println(" ");

    }
    static void four() {

        // TODO научиться определять число возможных перестановок слов
        System.out.println(" Четвертое задание ");

        String sentence = "Определите число возможных перестановок слов слов";
        String[] words = customSplit(sentence, " "); // разделяем строку на слова
        System.out.println("Число слов в предложении: " + words.length);
        int faqt = words.length;
        int result = 1;
        for (int i=1; i<=faqt; i++) {
            result = result * i;
        }
        System.out.println("Максимальное число перестановок = " + result);
        System.out.println(" ");
    }
    public static String[] customSplit(String sentence, String delimiter) {
        String[] parts = new String[MAX_COUNT_SPLIT];
        int partCount = 0;
        int startIndex = 0;

        while (true) {
            int end = sentence.indexOf(delimiter, startIndex); // Ищет пробел

            if (end == -1) {
                parts[partCount++] = sentence.substring(startIndex); // Добавляет в массив последнюю часть
                break;
            }
            parts[partCount++] = sentence.substring(startIndex, end); // Добавляет подстроку

            startIndex = end + 1;
        }


        String[] result = new String[partCount];
        return result;
    }


    public static boolean customEquals(String a, String b) {

        if (a.length() != b.length()) {
            return false;
        }

     
        for (int i = 0; i < a.length(); i++) {
            if (a.charAt(i)  !=b.charAt(i)) {
                return false;
            }
        }

        return true;
    }
    public static boolean isPalindrome(String word) {
        String lowerWord = word.toLowerCase();

        String reversedWord = new StringBuilder(lowerWord).reverse().toString();

        return customEquals(lowerWord, reversedWord);
    }

}
