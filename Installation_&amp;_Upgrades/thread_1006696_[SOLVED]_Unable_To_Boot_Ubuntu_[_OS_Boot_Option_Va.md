---
title: "[SOLVED] Unable To Boot Ubuntu [ OS Boot Option Vanished!]"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by LequidMetal on 2008-12-09
Hello all,

          I am a new Ubuntu user . I just recently installed ubuntu Intrepid Ibex . I also had Windows XP installed in the same computer .I have 2 Internal Hard drives [Drive 1 = 240GB , Drive2 = 80GB ] . I had installed ubuntu  in the second drive making a seperate ext3 partition for it .


Today i decided to re install xp after i lost some essential system files[dll files] . Everything went of well . Normally when i boot i get Options for selecting OS [grub loader ??]. But after reinstalling XP this has vanished ! 

[COLOR="Red"]Now when i start the computer , it boots XP straight away ! . I installed XP in a NTFS partition in the other hard drive , so Ubuntu has nt been erased , i am sure ... But how do i boot it now ? Pls Help[/COLOR] :(

---

### Post by Catalyst2Death on 2008-12-09
You just need to re-install grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

also check:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by LequidMetal on 2008-12-09
I managed to bring up Grub 

But now another problem has cropped up 

Grub gives me an option to boot up XP . But it boots up the old XP which was overwritten . 

So when i select XP , it says 

Ntldr missing

press ctrl+Alt+Del to reboot 

and wont load up xp  :(

what do i do now ?

---

### Post by LequidMetal on 2008-12-09
Can i make a new Grub loader?

---

### Post by LequidMetal on 2008-12-09
I need help with this command 

```
 title Windows XP/Vista # You can use any title you wish, this will appear on your grub boot menu
 rootnoverify (hd0,0) #(hd0,0) will be most common, you may need to adjust accordingly
 makeactive
 chainloader +1
```


i have no idea what location(hd?,?) my windows is loaded into .... how do i find out ?

---

### Post by LequidMetal on 2008-12-09
Yeah baby ! Solved my problem :guitar:

---

### Post by caljohnsmith on 2008-12-09
How about posting:
```
sudo fdisk -lu
```
And please identify which Windows partition you are trying to boot.

---

