---
title: "how to execute a.out file?"
date: 2008-10-06
forum: General Help
---

### Post by abhilashm86 on 2008-10-06
abhilash@abhilash-desktop:/bin$ gcc asd.c
/usr/bin/ld: cannot open output file a.out: Permission denied
collect2: ld returned 1 exit status

when i execute above asd.c program,error is occuring................how to execute a.out file.................

---

### Post by Titan8990 on 2008-10-06
Try sudo with it:

sudo gcc asd.c

Then to execute it:


./a.out

---

### Post by tonybaqain on 2008-10-06
in addition, do a ```
gcc -o *[output_file_name] [c_file]*
```
the output file will have +x permission for you **./*[output_file_name]*** (dot slash) will execute it.

---

