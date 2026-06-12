---
title: "[SOLVED] Nothing works...Missing libraries ?"
date: 2008-09-30
forum: General Help
---

### Post by ashmew2 on 2008-09-30
hi , 
Whenever i boot up my ubuntu install  , it takes me to the command line and when i try to open up gdm , it tells me that it cannot find a libgtk-x11-so.(something something) library.

When i try using apt-get , it gives me :
```

apt-get: error while loading shared libraries: libapt-pkg-libc6.8-6.so.4.6: cannot open shared object file: No such file or directory
```

Ive looked in the /lib folder and the file isnt there (unsurprisingly..)

wget wont work as well..it says libssl0.9.6 is missing..

My system is screwed :(

Where can i get back all these libraries ? It was working fine before...

Thanks..

---

### Post by Sycron on 2008-09-30
Well do a **fsck** and reboot.

---

### Post by oldos2er on 2008-09-30
> **ashmew2 said:**
> hi , 
Whenever i boot up my ubuntu install  , it takes me to the command line and when i try to open up gdm , it tells me that it cannot find a libgtk-x11-so.(something something) library.

When i try using apt-get , it gives me :
```

apt-get: error while loading shared libraries: libapt-pkg-libc6.8-6.so.4.6: cannot open shared object file: No such file or directory
```Ive looked in the /lib folder and the file isnt there (unsurprisingly..)

wget wont work as well..it says libssl0.9.6 is missing..

My system is screwed :(

Where can i get back all these libraries ? It was working fine before...


 
Before what? 

 If this machine has internet access, try the command "sudo aptitude update && sudo aptitude install libapt". Please post back the results.

---

### Post by ashmew2 on 2008-09-30
Before I installed Vector Linux , but i installed it to a different partition on a different hard drive...so i dont think that effed me up...

Ill post back the results asap..
Im shifting houses right now so i wont be able to post the output for about a day or two...Ill get back asap...Thanks for the replies !

---

### Post by oldos2er on 2008-09-30
> **ashmew2 said:**
> Before I installed Vector Linux , but i installed it to a different partition on a different hard drive...so i dont think that effed me up...
  

 Your UUIDs may have changed. When you installed Vector, did you also install lilo?

---

### Post by Sycron on 2008-10-01
Well you can see the UUID with **blkid** command.

---

### Post by ashmew2 on 2008-10-01
I didnt install lilo... Just added Vector Linux to grub using some tutorials @ google..
and ill give blkid a try...

---

### Post by ashmew2 on 2008-10-01
> **oldos2er said:**
> Before what? 

 If this machine has internet access, try the command "sudo aptitude update && sudo aptitude install libapt". Please post back the results.

Aptitude gives the same error when running apt-get...says its missing libapt-blahblah...

> **oldos2er said:**
> Your UUIDs may have changed. When you installed Vector, did you also install lilo?

And 

> **Sycron said:**
> Well you can see the UUID with **blkid** command.

I ran blkid and the UUIDs there are exactly the same in my /etc/fstab on ubuntu...

Any more ideas ? :((

Thanks for so much time and help guys!

---

### Post by oldos2er on 2008-10-01
"Any more ideas ?"

 Start enjoying Vector (I do). Sorry I don't have any further advice for you. Hopefully someone else will.

---

### Post by hyper_ch on 2008-10-01
Ok, I get this:

(1) libapt-pkg-libc6.8-6.so.4.6
that means, this file is somehow missing... now question is, how to find out how to get this file... for this I'd

(2) go to [http://packages.ubuntu.com](http://packages.ubuntu.com)

(3) search for "apt-file"

(4) download the according version

(5) install it running
```

sudo dpkg -i APT_FILE_PACKAGENAME.deb

```
Replace of cour APT_FILE_PACKAGENAME.deb with the real filename of apt-file

(6) If that works, we have a tool ready that can check in what package a given file is. Before we can use it, however, we need to update it (sort of like the slocate db)
```

sudo apt-file update

```
This will take a little while.

(7) Once it's done, you can now search for that file
```

apt-file search libapt-pkg-libc6.8-6.so.4.6

```
It will then list all packages that file is in there.

(8) Now that you know what package you need to (re)install, go again to [http://packages.ubuntu.com](http://packages.ubuntu.com) --> download it, install it with sudo dpkg -i PACKAGE

(9) As the file should now be installed, you can use apt-get as usual ;)

---

### Post by ashmew2 on 2008-10-02
> **oldos2er said:**
> "Any more ideas ?"

 Start enjoying Vector (I do). Sorry I don't have any further advice for you. Hopefully someone else will.

Thanks for all the help you provided oldos2er :)

---

### Post by Sycron on 2008-10-02
Lol indeed.

---

### Post by ashmew2 on 2008-10-06
Thanks for the help everyone...But i ultimately installed Intrepid Beta..
Thread Solved i guess ;)

---

