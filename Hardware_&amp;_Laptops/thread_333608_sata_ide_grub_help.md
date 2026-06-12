---
title: "sata ide grub help"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by oqnet on 2007-01-07
I have my system setup and its working fine but when I first went to install the OS after it had finished installing it loaded up grub and gave me loading stage 1.5 and on the next line said please wait.  I haven't had this problem before but I was trying to trouble shoot it and as I had two other drives with ntfs file systems on them I disconnecte them and did the install again thinking it was a problem with detecting the drives durring install. I got everything installed no problem. I plugged my second IDE drive in and everything was fine.  I plugged the third drive the SATA drive and it froze up at grub again durring stage 1.5.  I've looked around but I can't find a way to fix the problem.  I have heard from someone that IDE and SATA won't work together if thats true I have anouther IDE drive laying around but I would have to get the files off of the SATA drive onto the IDE drive.

---

### Post by geek_Man on 2007-01-07
Have you tried reconfiguring GRUB?

---

### Post by oqnet on 2007-01-07
yeah I did, is there something specific I should look at? Thanks.

---

### Post by oqnet on 2007-01-08
I have found that if I don't power on my sata drive until after grub has loaded to the menu I can boot into ubuntu and have my sata drive working. I don't like this but it is the only current work around I can come up with at this time.  I believe what is happening is that when the sata drive is plugged in grub wants to boot to that device first, I'm not sure why.  My bios is set to boot to the IDE drive first.

Is there some setting in grub that I should be checking for or something I can do so that it does not try to load the sata drive in grub?

I would like someone to point me in the right direction. Thanks a bunch. :-k

---

### Post by geek_Man on 2007-01-08
GRUB does some funny stuff with naming drives. Your BIOS is working right (I think), so it's probably GRUB not working right. First run "sudo fdisk- l" (l as in Linux), find what the partition setup is and then try: ```
you@your-computer:~$ **sudo grub**
```

```
you@your-computer:~$ **root (hdx,y)**
```

```
you@your-computer:~$ **setup (hdx)**
```

GRUB is probably looking at the wrong drive, so you need to change which drive it looks at (that's what you're doing above).
See if that works, or if it blows your computer up.

---

### Post by Toufik on 2007-01-08
Funny,

I didn't saw you post and wrote this one [http://www.ubuntuforums.org/showthread.php?t=333993](http://www.ubuntuforums.org/showthread.php?t=333993) at the same time as yours 

Maybe it's the same issue?  Have you try to install (and use) the 2.6.17-10-386 kernel?
$ sudo apt-get install linux-386

---

### Post by oqnet on 2007-01-08
thanks tons for both of your replies I'll try both when I get home from work.  I'll let you know the results.:-D

---

### Post by geek_Man on 2007-01-08
Toufik, I have no idea how to help. I would just say stick with Dapper, but that's just me. Did you download the ISO, or did you do something like apt-get dist-upgrade?

And to Oqnet, experiment a little with what you're doing. Just so that you know, GRUB (like Perl) starts counting at zero, so hd0,1 would be hda2 in fdisk or your fstab file.

---

### Post by oqnet on 2007-01-13
Yeah I still haven't got it to work but I'm 100% sure its something with grub or my bios making my sata IDE0 or something.   I'm going to try my ide drive as being HD2.0

---

### Post by geek_Man on 2007-01-14
Yeah, keep experimenting with it. I still haven't gotten my GRUB to work either. (sigh)...

---

