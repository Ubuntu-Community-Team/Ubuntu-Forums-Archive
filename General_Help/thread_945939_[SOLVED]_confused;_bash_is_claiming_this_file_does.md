---
title: "[SOLVED] confused; bash is claiming this file doesn't exist"
date: 2008-10-12
forum: General Help
---

### Post by jerome1232 on 2008-10-12
I don't get it... the only thing I can think of is I just restored my /home from a backup using rsync, I don't see how that could mess things up though.

edit: Just to add other executables work (scripts I've made and etc... )

```
jeremy@direbane:~$ tar xjvf pSX_linux_1_13.tar.bz2 
pSX/
pSX/pSX
pSX/readme.txt
pSX/cdimages/
pSX/bios/
jeremy@direbane:~$ cd pSX/
jeremy@direbane:~/pSX$ ./pSX 
bash: ./pSX: No such file or directory
jeremy@direbane:~/pSX$ ls -l
total 2144
drwxr-xr-x 2 jeremy jeremy    4096 2007-08-27 14:55 bios
drwxr-xr-x 2 jeremy jeremy    4096 2007-08-27 14:55 cdimages
-rwxr-xr-x 1 jeremy jeremy 2162024 2007-08-27 14:57 pSX
-r--r--r-- 1 jeremy jeremy   17925 2007-08-27 14:57 readme.txt
jeremy@direbane:~/pSX$ wtf?
```

---

### Post by patrickballeux on 2008-10-12
Have you checked that you can "read" in that folder?  Just an idea like that...

---

### Post by jerome1232 on 2008-10-12
Yeah I can rename the file, I can move it around, I can delete it and everything.

I even downloaded a brand new archive of pSX and am getting the same problem... it worked before the reinstall.

```
jeremy@direbane:~/pSX$ ls
bios  cdimages  pSX  readme.txt
jeremy@direbane:~/pSX$ mv pSX randomname
jeremy@direbane:~/pSX$ ls
bios  cdimages  randomname  readme.txt
jeremy@direbane:~/pSX$ ./randomname
bash: ./randomname: No such file or directory
jeremy@direbane:~/pSX$ ls -l randomname
-rwxr-xr-x 1 jeremy jeremy 2162024 2007-08-27 14:57 randomname

```

---

### Post by patrickballeux on 2008-10-12
Can you do "cat readme.txt"? and cat "pSX"?
Can you run /home/jeremy/pSX/pSX?

---

### Post by lswb on 2008-10-12
Maybe pSX is something like this?

cat pSX

#/bin/bash
echo "bash: $1: No such file or directory"
# about 216180 bytes of comments follow
#....


Seriously what does "file psX" show?

---

### Post by jerome1232 on 2008-10-12
yes 'cat pSX' gives me a bunch of binary junk (as expected)
'cat readme.txt' gives me the readme file.

---

### Post by patrickballeux on 2008-10-12
Another idea...

Since you restored from a backup, you're hidden files were restored also?  .bashrc?

Did you have the same username (and UID) as what you had in your backup?

Maybe lauching a "sudo chown -R jeremy:jeremey /home/jeremey" to make sure that all the files (including hidden ones are yours).  Then logout/login to apply.

Let me know!

---

### Post by Sam on 2008-10-12
What if you download the file from the web instead of using the one from the backup ?

---

### Post by jerome1232 on 2008-10-12
I tried the sudo chown, good idea but didn't work.

I did try redownloading but that didn't work.

I tried creating a new user, copying the file over and executing it as the new user and still no go so it's not profile related...

```
jeremy@direbane:~$ sudo adduser test
[sudo] password for jeremy: 
Adding user `test' ...
Adding new group `test' (1001) ...
Adding new user `test' (1001) with group `test' ...
Creating home directory `/home/test' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for test
Enter the new value, or press ENTER for the default
	Full Name []: 
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [y/N] y
jeremy@direbane:~$ su test
test@direbane:/home/jeremy$ cd ~
test@direbane:~$ cp -r /home/jeremy/pSX ~/
test@direbane:~$ cd pSX
test@direbane:~$ ./pSX
bash: ./pSX: No such file or directory
test@direbane:~/pSX$ ls -l
total 4260
drwxr-xr-x 2 test test    4096 2008-10-12 18:14 bios
drwxr-xr-x 2 test test    4096 2008-10-12 18:14 cdimages
-rw-r--r-- 1 test test 2162024 2008-10-12 18:14 output.txt
-rwxr-xr-x 1 test test 2162024 2008-10-12 18:14 pSX
-r--r--r-- 1 test test   17925 2008-10-12 18:14 readme.txt
```

I'm going to redownload that archive and try again... thanks for the ideas thus far.

---

### Post by jerome1232 on 2008-10-12
Progress!

I guess it was in reality it was not finding a different file that was a  dependency? 

I just downloaded some apps I remember as being dependencies and now at least it's just complaining about not finding blah blah blah.so; so I think I can tackle it from here now that the file will execute. Once again thanks for the help.

---

### Post by patrickballeux on 2008-10-12
There is a debian package there: [http://doc.ubuntu-fr.org/psx](http://doc.ubuntu-fr.org/psx)

I tried the tar.gz and it worked.  I was able to run it (AMD64 in my case).

So the archive is working. 

I did uncompress using the default Gnome archiver.

---

### Post by jerome1232 on 2008-10-12
Thank you for that .deb (64bit here too) I would've spent all night guessing dependencies!

---

