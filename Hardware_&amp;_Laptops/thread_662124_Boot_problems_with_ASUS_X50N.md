---
title: "Boot problems with ASUS X50N"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by jpr0 on 2008-01-08
Hi, 

I have an ASUS X50N laptop, and I'm trying to install Gutsy Gibbon, but failing miserably. I'm new to linux so I have no idea what I'm doing either :)

There are 2 problems I'm having with booting (and even the initial installion) - one is due to the graphics card and the other due to the SD card reader.

So, the first problem with the graphics card, I've seen well documented - lots of people have installation problems due to the graphics card on this laptop, which is an nVidia GeForce 7000M. I run the ubuntu live CD, and managed to install the system using the safe graphics mode option. When I tried booting the system, it would get to the splash screen where there are little bars showing the boot progress, and then just hang almost immediately. I pressed ALT + F2, and the output on the screen was 

Usplash: setting mode 1280x1024 failed
Usplash: setting mode 1152x864 failed
Usplash: using mode 1024x768

I loaded ubuntu again from the live CD, and edited the file 

/boot/grub/menu.lst 

and changed the line: 

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=[somethinglong] ro quiet splash

to: 

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=[somethinglong] ro nosplash

So this temporarily solves the problem of Usplash, but as ubuntu is booting it hangs at another point. The last few lines on the screen before the freeze are: 

[   10.652000] scsi 0:0:0:0: Direct-Access     Generic- xD/SDMMC/MS/Pro  1.00 PQ: 0 ANSI: 0 CCS
[   10.656000] sd 0:0:0:0: [sdb] Attached SCSI removable disk
[   10.656000] sd 0:0:0:0: Attached scsi generic sg1 type 0

(I actually took this from /var/log/dmesg on the live CD file system because I couldn't get the installation on the hard disk to produce boot logs). After googling I found that it's been reported as a bug here: 

[https://bugs.launchpad.net/ubuntu/+bug/147574](https://bugs.launchpad.net/ubuntu/+bug/147574)

I'm not sure what the problem is but it looks like it's because there's no SD card in the SD card reader. (??). I just don't know what to do now - how can I get ubuntu to boot? Is there anyway to tell it to ignore the SD card reader? Or some other way I can fix this? 

By the way sorry for the length of the post, I just wanted to write out the details in case anyone else is having similar problems with this laptop. 

Any help would be really appreciated
John

---

### Post by presston on 2008-05-08
have you solved this problem?

---

### Post by jpr0 on 2008-05-08
Hi
Yeah, apparently there was a bug in the kernel which was detecting the drives in the wrong order or somesuch. Anyway, I installed Hardy and it works fine now.

Do you have an x50?

---

### Post by presston on 2008-05-08
yeah:) but until today i have only win xp on it. 

but i install 7.10 ubuntu, not hardy. how you  fix bug with booting?

---

### Post by jpr0 on 2008-05-08
You can't.. at least I couldn't. 

Different people I spoke to with this laptop have mixed success. Some managed to install it with no problems, others not atall. 

The problem I had was with the card reader, which would hang the boot-up process. They fixed this in hardy. Anyway, I had to install the last long-term support to get an OS that would boot.

Why don't you want to use hardy? Because it was just released? I don't have any problems with it, and it seems to work better with this laptop than the last long-term supported version. 

Anyway, once you have the OS installed, it's a pain to get everything working - graphics card, wireless, sound card - none of these worked out of the box. With hardy, graphics works straight away, but you still have to do (minor) fiddling to get the sound card and wireless working. I found a really good cook-book for installing ubuntu on this laptop, and how to get everything working. When I find it I'll send the link.

---

### Post by jpr0 on 2008-05-08
Here's the link for the cook-book : 

[http://ubuntuforums.org/showthread.php?t=716371](http://ubuntuforums.org/showthread.php?t=716371)

It says F5N (rather than X50N) but the motherboard for this laptop is F5N, and all the steps on the above page apply to this laptop.

---

