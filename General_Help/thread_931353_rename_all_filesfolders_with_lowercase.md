---
title: "rename all files/folders with lowercase"
date: 2008-09-27
forum: General Help
---

### Post by fallen seraph on 2008-09-27
is there any command I can use to rename all folders in my home directory to start with lowercase letters?

---

### Post by ghostdog74 on 2008-09-27
You can try the Python script in my signature.
example usage to rename folders:
```

 # ls -l *
TEST1UPPER:
total 4
drwxr-xr-x 2 root root 4096 Sep 26 20:10 DUDe1

TEST2UPPER:
total 4
drwxr-xr-x 2 root root 4096 Sep 26 20:10 lowercasedirectory

Test3uppER:
total 0
-rw-r--r-- 1 root root 0 Sep 26 20:10 testfile

/home/user # filerenamer.py -d 2 -t d -p ".*" -e "[a-z]" -l "*" #use -l to list 
==>>>>  [ /home/user/TEST1UPPER/DUDe1 ]==>[ /home/user/TEST1UPPER/dude1 ]
==>>>>  [ /home/user/TEST1UPPER ]==>[ /home/user/test1upper ]
==>>>>  [ /home/user/Test3uppER ]==>[ /home/user/test3upper ]
==>>>>  [ /home/user/TEST2UPPER ]==>[ /home/user/test2upper ]

/home/user # filerenamer.py -d 2 -t d -p ".*" -e "[a-z]"  "*" #remove -l to commit
/home/user/TEST1UPPER/DUDe1  is renamed to  /home/user/TEST1UPPER/dude1
/home/user/TEST1UPPER  is renamed to  /home/user/test1upper
/home/user/Test3uppER  is renamed to  /home/user/test3upper
/home/user/TEST2UPPER  is renamed to  /home/user/test2upper

/home/user # ls -l *
test1upper:
total 4
drwxr-xr-x 2 root root 4096 Sep 26 20:10 dude1

test2upper:
total 4
drwxr-xr-x 2 root root 4096 Sep 26 20:10 lowercasedirectory

test3upper:
total 0
-rw-r--r-- 1 root root 0 Sep 26 20:10 testfile


```

---

### Post by stylishpants on 2008-09-27
If the perl package is installed, then you have access to the simple and powerful 'rename' (sometimes called 'prename'):

```

# rename all folders to start with a lowercase letter
rename '$_=lcfirst' */

```

---

