---
title: "Saving line numbers in vim"
date: 2008-09-30
forum: General Help
---

### Post by test006 on 2008-09-30
Hi,
I would like to know how i can save the line numbers to the file. i.e. i know that you can turn line numbers on by using :set number but this is not saved to the file when you close and exit the vim editor. How can i make it so that the numbers are saved in the file and when i open the file with some other editor such as wordpad so that i can still see the line numbers.

Thanks

---

### Post by kpkeerthi on 2008-09-30
To save the file with line numbers as a new file:
```
cat -n MyFile.txt > MyFile_New.txt
```

The below command will overwrite the original file with the line numbers:
```
cat -n MyFile.txt > MyFile.txt
```

---

