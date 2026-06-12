---
title: "Two instances of ubuntu with Wubi"
date: 2008-10-29
forum: General Help
---

### Post by redscorp on 2008-10-29
Hi all!

I have a question concerning dual linux installation with wubi.
So, What I need:
- I cannot touch (move/resize) NTFS partition I have.
- I need 64-bit ubuntu installed.
- I need 32-bit ubuntu installed.

So, the question itself: How can I install two Linux OS'es with Wubi? (I have already 64-bit one)

Of cause I can by a second HDD for linuxes, but it's not a case..
Virtual machine is also not a case, because I need direct HW access in linux.

Thanks!

--
WBR,
AG

---

### Post by ago on 2008-10-29
Why exactly do you need both version, if it is for compiling stuff targeting 32bit machines that can be achieved from ubuntu 64

---

### Post by redscorp on 2008-10-29
I need to build and TEST software in both versions of linux.
Assuming that something works on all platforms if it builds on one of platforms does not much my needs... unfortunately.

---

### Post by ago on 2008-10-29
You can by renaming C:\ubuntu to say c:\ubuntu64, then installing again and finally modifying C:\ubuntu\disks\boot\grub\menu.lst so that the first menu option is 

title Ubuntu 64bit
configfile /ubuntu64/disks/boot/grub/menu.lst

Check also pbuilder and friends, for instance 

[http://ubuntuforums.org/showthread.php?t=289139](http://ubuntuforums.org/showthread.php?t=289139)

[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

You could use kvm with some scripting for further testing in one of the 32bit platforms

---

### Post by redscorp on 2008-10-29
> **ago said:**
> You can by renaming C:\ubuntu to say c:\ubuntu64, then installing again and finally modifying C:\ubuntu\disks\boot\grub\menu.lst so that the first menu option is 

title Ubuntu 64bit
configfile /ubuntu64/disks/boot/grub/menu.lst


Thanks! I'll try it.

---

### Post by brandon88tube on 2008-10-29
Instead of me trying to post a new thread I figured I would try and ask my question here as it is very similar to what was already asked.

I wanted to know if I renamed my Ubuntu folder that contains my Ubuntu 8.04, would it get deleted if I used the wubi installer again to install a clean install of intrepid? I was looking to keep my current Ubuntu 8.04, but try out intrepid as a clean install and see if wireless etc. worked right out of the box.

---

### Post by ago on 2008-10-29
No if you rename the ubuntu folder it will not be deleted.

---

### Post by brandon88tube on 2008-10-29
Thanks...Lupin lol

---

