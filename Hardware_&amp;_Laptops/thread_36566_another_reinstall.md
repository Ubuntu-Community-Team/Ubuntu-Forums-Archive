---
title: "another reinstall"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by simple on 2005-05-23
well, i had troubles nobody seemed to care to answer or help about, so i reinstalled, now i need to setup my sound card, one more time! 8 now, well the very first time i installed it with alsa, it was great, clear, smooth perfect, last few times its been crackly when i've been doing it the same way... here [https://www.ubuntulinux.org/wiki/HdaIntelSoundHowto](https://www.ubuntulinux.org/wiki/HdaIntelSoundHowto)  i've tried the second guide on the page, and get to the very last step fine then...> root@ubuntu:/usr/src/linux-headers-2.6.10-5-686 # dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb
dpkg: error processing alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb
 so i guess i will just wait until somebody can help me as to why i get that error, and how to correct it

---

### Post by Xian on 2005-05-23
You generally get that message when the .deb package is not in the directory you that you have provided. From the command line you listed, you are telling dpkg that 'alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb' is in the /usr/src/linux-headers-2.6.10-5-686 path. Is that correct? 

If not, then adjust the path and issue the command again.

---

### Post by simple on 2005-05-23
[QUOTE=Xian]You generally get that message when the .deb package is not in the directory you that you have provided. From the command line you listed, you are telling dpkg that 'alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb' is in the /usr/src/linux-headers-2.6.10-5-686 path. Is that correct? 

If not, then adjust the path and issue the command again.[/QUOTE]
 > root@ubuntu:/usr/src # dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb
(Reading database ... 72713 files and directories currently installed.)
Preparing to replace alsa-modules-2.6.10-5-686 1.0.8-4ubuntu4+10.00.Custom (using alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb) ...
Unpacking replacement alsa-modules-2.6.10-5-686 ...
Setting up alsa-modules-2.6.10-5-686 (1.0.8-4ubuntu4+10.00.Custom) ...
FATAL: Could not open '/boot/System.map-2.6.10-5-686': No such file or directory
root@ubuntu:/usr/src #
 yeah thank you, now i need help because something else isn't working

---

### Post by Xian on 2005-05-24
What is the content of your /boot directory. 
Listed below is mine (notice the System.map-2.6.10-5-386).

```
$ cd /boot
$ ls
config-2.6.10-5-386  initrd.img-2.6.10-5-386  System.map-2.6.10-5-386
grub                 memtest86+.bin           vmlinuz-2.6.10-5-386
```

---

### Post by simple on 2005-05-24
> root@ubuntu:/home/simple # cd /boot
root@ubuntu:/boot # ls
config-2.6.10-5-386  initrd.img-2.6.10-5-386  System.map-2.6.10-5-386
grub                 memtest86+.bin           vmlinuz-2.6.10-5-386

mine too, but still i get that FATAL ERROR, tried changing the system map file...
> root@ubuntu:/boot # dpkg -i alsa-modules-2.6.10-5-386_1.0.8-4ubuntu4+10.00.Custom_i386.deb
dpkg: error processing alsa-modules-2.6.10-5-386_1.0.8-4ubuntu4+10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alsa-modules-2.6.10-5-386_1.0.8-4ubuntu4+10.00.Custom_i386.deb


---

### Post by Xian on 2005-05-24
[QUOTE=simple]mine too, but still i get that FATAL ERROR, tried changing the system map file...[/QUOTE]
The way to change the system map file to the *.686 version is to install the matching linux-image-686 package. See, you've got a 2.6.10-5-386 kernel currently installed, and your alsa-modules-2.6.10-5-686 is not accepting the System.map-2.6.10-5-386 in /boot. It wants the corresponding 2.6.10-5-686 version.

---

### Post by simple on 2005-05-24
i'm really not sure how to do that :/

---

### Post by az on 2005-05-24
That howto was written for someone with a 686 kernel.  Start over with the 386 linux headers.

---

### Post by Xian on 2005-05-24
[QUOTE=azz]Start over with the 386 linux headers.[/QUOTE]
Heh. An even better idea. :)

---

### Post by simple on 2005-05-24
[QUOTE=azz]That howto was written for someone with a 686 kernel.  Start over with the 386 linux headers.[/QUOTE]
well..will i need the 386 headers?
```

 root@ubuntu:/home/simple # uname -a
Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

```i see 386 and i686...so i never really knew :/

---

### Post by Xian on 2005-05-25
[QUOTE=simple]```

 root@ubuntu:/home/simple # uname -a
Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

```i see 386 and i686...so i never really knew :/[/QUOTE]
That's telling you that you're running the 386 kernel on a 686 capable box.

---

### Post by simple on 2005-05-25
ahh, thank you sir, been very good help :D how hard it is, being as i've asked what i asked, and how much i don't know...to use the 686 kernel..or is it really a difference? at all between the two. i guess since there is either or theres a difference.

---

### Post by simple on 2005-05-25
ahh, thank you sir, been very good help :D how hard it is, being as i've asked what i asked, and how much i don't know...to use the 686 kernel..or is it really a difference? at all between the two. i guess since there is either or theres a difference.

---

### Post by Xian on 2005-05-25
[QUOTE=simple]ahh, thank you sir, been very good help :D how hard it is, being as i've asked what i asked, and how much i don't know...to use the 686 kernel..or is it really a difference? at all between the two. i guess since there is either or theres a difference.[/QUOTE]
My box is also 686 kernel capable but I just use the 386, as I've run the optimized one and haven't noticed any substantial difference in speed. However, if you have a large swap file (in the 1G range) then you will definitely want to do an kernel upgrade as the 386 will not load that size swap file for your system.

---

