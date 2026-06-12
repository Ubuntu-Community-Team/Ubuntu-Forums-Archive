---
title: "grub finds no kernel"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2009-08-26
after (thought) successfull installation of 8.10 ubuntu via wubi, after reboot and selection of ubuntu, only the grub 'bash' appears, the grub does not find any kernel apparently.
Checked all the files, all seem to be correct, the linuz kernel files in position as it should be, all other results of the wubi too.

Any advise how to proceed or derect the grub to the kernel?

I installed as follows: iso file of the appropriate desktop version and the propper wubi (for version 8.10) placed into one folder then started wubi and from there all seemed to go fine. BUt at the end the grub is not correctly set.

---

### Post by ottosykora on 2009-08-27
first it looks that all is set correctly to the path to the kernel, but no luck, kernel is not found.

I tried then the next, wubi installation of the ubuntu 9, and this time I took the netinstall , downloading the iso by wubi. 
It did try to make the disks, but rather then producing the disks it produced a text log file of the same size (8GB) in appdata folder on drive C.
Also here when tried to boot into the install, only grub bash came up, kernel not found, thought all pointers seem to be set correctly to the install folder where all is contained at this time.
Here I then copied the the vmlinuz and initrd to the final location manually , the installer then started, but since there were no disks for installation, all failed.

I am not sure if I am here in the right forum, is this the place to get some support for wubi?

host: XP sp3, target drive with 22gb free, fat32 formated.

Using desktop iso and the associated wubi with 8.10 and 9.04 with associated wubi.

---

### Post by oboedad55 on 2009-08-27
> **ottosykora said:**
> first it looks that all is set correctly to the path to the kernel, but no luck, kernel is not found.

I tried then the next, wubi installation of the ubuntu 9, and this time I took the netinstall , downloading the iso by wubi. 
It did try to make the disks, but rather then producing the disks it produced a text log file of the same size (8GB) in appdata folder on drive C.
Also here when tried to boot into the install, only grub bash came up, kernel not found, thought all pointers seem to be set correctly to the install folder where all is contained at this time.
Here I then copied the the vmlinuz and initrd to the final location manually , the installer then started, but since there were no disks for installation, all failed.

I am not sure if I am here in the right forum, is this the place to get some support for wubi?

host: XP sp3, target drive with 22gb free, fat32 formated.

Using desktop iso and the associated wubi with 8.10 and 9.04 with associated wubi.

Underneath the search button pick "tag" search and put in wubi as the search string. I think you'll be able to easily find what you need. It's always a good idea to search these forums, and google if appropriate, as you may find your answer more quickly without having to wait. I don't use the wubi install so I can't be more help, except to say that if you really dig Ubuntu it might be more fun to create some space for it and install alongside windows. In either case I believe I'd use 9.04 over 8.10. Or 8.04 which is the LTS version.
Incidentally, you are in the right forum since you have wubi questions.
Jon

---

### Post by ottosykora on 2009-08-27
have tried to search, but no luck, no real answers how to install under wubi.

I am getting now rather desperate.

After 3 nights trying to install ubuntu with wubi without results I need really some help with that.

My system is desktop XP sp3, 1g ram, partition to be used is 22gb.


I tried to install ubuntu 9.04 with its wubi 9.04
Creating of disk finaly possible, then started the installation. Check of the installtion iso was ok, then some formating messages.
Then : creating swap file in disk1... or similar, there stuck for ever. Tried 3 times, have given up.


tried ubuntu 8.10 with wubi 8.10
number of times no luck, grub 'bash ' was only I get and it was all in it pointed to drive C apparently.
After few tries, I managed to reboot and installation started, Some tests, formating, harware test, then reboot
And
again landed in grub 'bash'
this time I seem to be on the right drive, but still no booting. Manually entering string for the vmlinuz, which is now in the ubuntu/disks/boot, but trying to boot crahes , no way to continue.

Please need any experts on the wubi installtion.

---

### Post by raymondh on 2009-08-27
Have you tried running chkdsk in windows as well as defragging your XP?

See the [wubiguide]("https://wiki.ubuntu.com/WubiGuide") for possible solutions.

---

### Post by ottosykora on 2009-08-27
yes disk checked, all fine, defragged all fine, there is not much on that disk otherwise so far.

The wubi manual is printed and in front of me, reading all dozen times, it gives no answer at all unfortunately.

The strange thing is, on identical computer at work I did wubi install with no problems, on other laptops and dektops too, count so 10 or more installs I did. Here I have no idea what is wrong.

I cna not more check the iso file if the md5 is right and it is checked by the installer and found ok.

The 9 simply hangs on some formating job, the 8 will end up with broken grub which can not find kernel etc.

Should I look for some logfiles?

---

### Post by ottosykora on 2009-08-28
just tried again with 9.04 and wubi 9.04

this time on other partition where even less data is on. all defragged and chkdisked.

the wubi started , made the disks, this time I have choosen the small 5gb. Then rebooted, ok the installation started, after some checking and formating job it again stopped for the rest of the night at some task saying it does create swap space inside the drive.... this is then for ever, not comming any further.

Did anybody managed to make such wubi install? 

is there someone who knows how all this works so I could give some more infos abt it?

---

