---
title: "Need help installing UDF 2.5"
date: 2008-07-16
forum: General Help
---

### Post by Bruynz on 2008-07-16
I just switched from Vista to ubuntu yesterday. This is my first experience with any kind of linux distro, and so far it's going pretty well. However I am in need of some file I backed up which I burnt using vista. 

I tried following the steps from [here]("http://ubuntuforums.org/showthread.php?t=718744") and [here]("http://ascending.wordpress.com/2008/06/14/howto-read-vista-burnt-udf-dvds-on-ubuntu-linux/") but I can't understand anything. 

Could anyone mind making the instructions more noob friendly please ???

Thanks,
Keith

---

### Post by tamoneya on 2008-07-16
can you tell us which steps you followed and where they failed.  Copy and paste what you typed into terminal and post here.  Please include the commands that you ran and what the error messages were.

---

### Post by Bruynz on 2008-07-16
I followed the steps given out by the latter. I got stuck at step 2 part 1. I typed in the terminal "cd src patch -l <smak/root/udf-vista/udf-filesystem-2.5/src" and  "cd src patch -l <smak/root/udf-vista/udf-filesystem-2.5/src " since I was not sure what is meant by ~. In both cases I received bash: cd: src: No such file or directory. However I'm sure that directory exists.

Edit: That path was infact wrong but correcting it still gives the same error message

```
smak@S:~$ cd src patch -l </home/smak/root/udf-vista/udf-filesystem-2.5/src
bash: cd: src: No such file or directory

```



```
smak@S:~$ cd src patch -l </home/smak/root/udf-vista/udf-filesystem-2.5/vista-patch
bash: cd: src: No such file or directory

```



```
smak@S:~$ cd src patch -l <../vista-patch
bash: ../vista-patch: No such file or directory
```

Re-Edit:

I found this command in the first thread, not sure what it's for but anyways here it is.

```
smak@S:~$ apt-get install linux-headers-amd64
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```


Re-Edit:
I figured out I need to add sudo before the command. Now it gives:


```
smak@S:~$ sudo apt-get install linux-headers-amd64
[sudo] password for smak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-amd64

```

---

### Post by tamoneya on 2008-07-16
the latter of the two links you gave while it works is very confusing in the way it does it so lets stay away from that one.  I have udf 2.5 in my kernel (64 bit) and I used the former thread when I did it.  The kernel headers should already be installed so lets skip step one and do step 2.

---

### Post by Bruynz on 2008-07-16
Ok, so I downloaded the archive and extracted it on the spot. That should be step 2. Now step 3. I assume it's a terminal command (the one I've been using "cd src patch ...") but what do I need to do exactly?

---

### Post by tamoneya on 2008-07-16
yes it is a terminal command and it changes depending on where you extracted the files.  Assuming you extracted the files to your desktop into a folder called udf-filesystem-2.5 the command would be this:```
cd /home/smak/Desktop/udf-filesystem-2.5
```
Since you were confused about "~" earlier let me explain.  ~ equals your home directory so when logged in as smak ~ equals /home/smak so you could just as easily run this command since it has the same effect:```
cd ~/Desktop/udf-filesystem-2.5
```

---

### Post by Bruynz on 2008-07-16
Thanks very much.That makes step 3 much more clear. The rest of commands were easy, however step 7 didn't work so I added sudo before and I think I managed to make it work. I just need to restart and see.

Well I am still receiving: Invalid mount option when attempting to mount the volume 'UDF Volume'. I'll try again tomorrow. If it still doesn't work I'll just install vista on a virtual machine and try to get the data from there.

Thanks anyways.

---

