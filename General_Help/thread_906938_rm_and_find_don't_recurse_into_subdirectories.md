---
title: "rm and find don't recurse into subdirectories"
date: 2008-09-01
forum: General Help
---

### Post by 77bridge on 2008-09-01
Hi *,

I'm getting strange behavior from 'rm' and 'find' where it seems they are not checking subdirectories when instructed to, and I'm pretty sure my permissions are correct.  Have a look at the shell excerpts below and let me know what I have wrong, please!

Thanks!!!!  :)

##1) here is my top directory, note the subdirectory 'part0'
beans@blue:~/d1/project1$ ls -al
total 32
drwxr-xr-x 3 beans beans 4096 2008-08-31 23:42 .
drwxr-xr-x 7 beans beans 4096 2008-08-30 16:50 ..
-rw-r--r-- 1 beans beans  188 2008-08-31 23:38 makefile
-rw-r--r-- 1 beans beans  147 2008-08-31 23:37 makefile~
drwxr-xr-x 4 beans beans 4096 2008-08-31 23:34 part0
-rw-r--r-- 1 beans beans  705 2008-08-31 23:44 Test_part0.class
-rw-r--r-- 1 beans beans  350 2008-08-31 23:13 Test_part0.java
-rw-r--r-- 1 beans beans  350 2008-08-30 16:55 Test_part0.java~

##2) I goto subdirectory 'part0'
beans@blue:~/d1/project1$ cd part0

##3) see the contents of directory 'part0'.  notice that there is 
##a file Class1.class (also, there is no trailing space in the 
##filename- I checked)
beans@blue:~/d1/project1/part0$ ls -al
total 28
drwxr-xr-x 4 beans beans 4096 2008-08-31 23:34 .
drwxr-xr-x 3 beans beans 4096 2008-08-31 23:42 ..
-rw-r--r-- 1 beans beans  400 2008-08-31 23:38 Class1.class
-rw-r--r-- 1 beans beans  106 2008-08-31 23:34 Class1.java
-rw-r--r-- 1 beans beans  120 2008-08-31 23:34 Class1.java~
drwxr-xr-x 3 beans beans 4096 2008-08-30 17:05 usefulStuff1
drwxr-xr-x 2 beans beans 4096 2008-08-30 17:05 usefulStuff2

##4) back up to the parent directory
beans@blue:~/d1/project1/part0$ cd ..

##5) now the problem:  I issue an rm command which is supposed to
##recurse into subdirectories (because of r option) and it doesnt
##check even the part0 directory.  I have tried rm -rf and it is
## the same result.  also 'find . -name *.class' seems to have the
##same result.  Any ideas???
beans@blue:~/d1/project1$ rm -rv *.class
removed `Test_part0.class'

##6) goto subdirectory for confirmation
beans@blue:~/d1/project1$ cd part0/

##7) confirmed: Class1.class has not been removed!?
beans@blue:~/d1/project1/part0$ ls -al
total 28
drwxr-xr-x 4 beans beans 4096 2008-08-31 23:34 .
drwxr-xr-x 3 beans beans 4096 2008-08-31 23:48 ..
-rw-r--r-- 1 beans beans  400 2008-08-31 23:38 Class1.class
-rw-r--r-- 1 beans beans  106 2008-08-31 23:34 Class1.java
-rw-r--r-- 1 beans beans  120 2008-08-31 23:34 Class1.java~
drwxr-xr-x 3 beans beans 4096 2008-08-30 17:05 usefulStuff1
drwxr-xr-x 2 beans beans 4096 2008-08-30 17:05 usefulStuff2

---

### Post by spec-chum on 2008-09-01
In the find statement you need to escape the * so the shell doesn't interpret it.  You should be able to do what you want with this

```

find . -name \*.class -exec rm {} \;

```

That'll find all files from the current directory downwards ending in .class and then execute an rm command on each one to remove it.

---

### Post by aloshbennett on 2008-09-01
'rm -r' removes the contents of the folders recursively, but doesnt search the folders recursively for delete.

If you call 'rm -r *class'
This would delete all *class files and folders (and all its contents) in the current directory. It wouldnt delete a class file lying inside part0, because part0 does match *class.

With find, I think this should work
> find . -iname '*.class'

---

