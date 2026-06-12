---
title: "How to install sis_vga_150508_ubuntu_8.04.tar.bz2"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by ex-para on 2009-03-11
I have on my desktop this file (sis_vga_150508_ubuntu_8.04.tar.bz2) how do I put it where it should be to make it work. It is a driver that should get me the resolution I need 1280x800 on a wide screen ASUS laptop. If any one could tell me in a step by step way would be appreciated.

---

### Post by taurus on 2009-03-11
Open a terminal and change to your ~/Desktop directory.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
```
Now, unpack it.

```
tar xvjf sis_vga_150508_ubuntu_8.04.tar.bz2
```
It is more likely it will create a new directory where you have to change to it.  If you don't know for sure, just look at the output of this command.  The one that start with letter d in front, drwx, is the directory.

```
ls -la
```

Then, change to the new directory and have a look at either the readme or INSTALL.

```
cd that_new_directory
ls -la
```

---

### Post by ex-para on 2009-03-12
Thank you very much for your reply. After following the instructions you sent me this is what I have but not sure what to do next.

papion@papion-laptop:~$ cd ~/Desktop

papion@papion-laptop:~/Desktop$ tar xvjf sis_vga_150508_ubuntu_8.04.tar.bz2

sis_vga_drv_150508/

sis_vga_drv_150508/sis_drv.la

sis_vga_drv_150508/sis_drv.lai

sis_vga_drv_150508/sis_drv.so

papion@papion-laptop:~/Desktop$ ls -la

total 718644

drwxr-xr-x  3 papion papion      4096 2009-03-12 09:59 .

drwxr-xr-x 36 papion papion      4096 2009-03-12 09:55 ..

-rw-r--r--  1 papion papion      1152 2009-03-07 13:06 auto915Resolution.tar.gz

-rw-r--r--  1 papion papion       203 2009-02-16 17:13 Ebay UK.desktop

-rw-r--r--  1 papion papion       209 2009-02-11 15:33 firefox.desktop

-rw-r--r--  1 papion papion    275190 2009-03-10 16:24 intelbin.tar.bz2

-rw-r--r--  1 papion papion    808714 2009-03-10 16:25 intelsrc.tar.bz2

-rw-r--r--  1 papion papion     10968 2009-02-25 14:49 officialpenguin.gif

-rwx------  1 papion papion 731668480 2009-03-05 15:20 pclinuxos-2007.iso

-rw-r--r--  1 papion papion   1073183 2009-03-11 16:16 sis_vga_150508_ubuntu_8.04.tar.bz2

-rw-r--r--  1 papion papion   1281864 2009-03-08 07:53 sis_vga_200807_ubuntu_7.04.tgz

drwxr-xr-x  2 papion papion      4096 2008-05-22 18:43 sis_vga_drv_150508

papion@papion-laptop:~/Desktop$ cd that_new_directory

bash: cd: that_new_directory: No such file or directory

papion@papion-laptop:~/Desktop$ ls -la

---

### Post by Partyboi2 on 2009-03-12
It should be
```
cd sis_vga_drv_150508
```
not ```
cd that_new_directory
```you are meant to replace "that_new_directory" with the correct directory name.

---

### Post by ex-para on 2009-03-12
Thanks for the reply is this how it should be?

papion@papion-laptop:~$ cd ~/Desktop

papion@papion-laptop:~/Desktop$ tar xvjf sis_vga_150508_ubuntu_8.04.tar.bz2

sis_vga_drv_150508/

sis_vga_drv_150508/sis_drv.la

sis_vga_drv_150508/sis_drv.lai

sis_vga_drv_150508/sis_drv.so

papion@papion-laptop:~/Desktop$ ls -la

total 718644

drwxr-xr-x  3 papion papion      4096 2009-03-12 09:59 .

drwxr-xr-x 36 papion papion      4096 2009-03-12 15:13 ..

-rw-r--r--  1 papion papion      1152 2009-03-07 13:06 auto915Resolution.tar.gz

-rw-r--r--  1 papion papion       203 2009-02-16 17:13 Ebay UK.desktop

-rw-r--r--  1 papion papion       209 2009-02-11 15:33 firefox.desktop

-rw-r--r--  1 papion papion    275190 2009-03-10 16:24 intelbin.tar.bz2

-rw-r--r--  1 papion papion    808714 2009-03-10 16:25 intelsrc.tar.bz2

-rw-r--r--  1 papion papion     10968 2009-02-25 14:49 officialpenguin.gif

-rwx------  1 papion papion 731668480 2009-03-05 15:20 pclinuxos-2007.iso

-rw-r--r--  1 papion papion   1073183 2009-03-11 16:16 sis_vga_150508_ubuntu_8.04.tar.bz2

-rw-r--r--  1 papion papion   1281864 2009-03-08 07:53 sis_vga_200807_ubuntu_7.04.tgz

drwxr-xr-x  2 papion papion      4096 2008-05-22 18:43 sis_vga_drv_150508

papion@papion-laptop:~/Desktop$ cd sis_vga_drv_150508

papion@papion-laptop:~/Desktop/sis_vga_drv_150508$ ls -la

total 2656

drwxr-xr-x 2 papion papion    4096 2008-05-22 18:43 .

drwxr-xr-x 3 papion papion    4096 2009-03-12 09:59 ..

-rwx------ 1 papion papion     794 2008-05-16 23:52 sis_drv.la

-rwx------ 1 papion papion     795 2008-05-16 23:52 sis_drv.lai

-rwx------ 1 papion papion 2698626 2008-05-16 23:52 sis_drv.so

papion@papion-laptop:~/Desktop/sis_vga_drv_150508

---

