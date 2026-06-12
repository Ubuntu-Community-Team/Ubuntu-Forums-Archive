---
title: "install failed, dual boot win7, ubuntu 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by mhoy06 on 2009-11-02
tried to install 9.10 beside win7 on same hard drive. Install failed, assumed bad disk during reboot 'missing operating system'.

booted to win7 install disk. in past did 'fixmbr' no option for that now. Google shows bootsect.exe fixes it. Tried 'bootsect /nt64 all' among others, no luck. Note that when I choose repair it does not show any operating systems to choose. gives option of loading hard disk drivers. attempted to do so, didn't work. downloaded western digital se16 drivers and burned them to disk. None of the files in the folder I burned are apparently hard drive drivers. Never messed with hard drive drivers before so not sure what to do on that front. Would just reinstall win7 and just give up but it's really a hell of a lot of installation of applications and games. 

did learn one important thing: My days of dual booting are over. No longer going to try and make windows and linux play together on same hard drive. In the end it's just not worth the hassle. Should note though this is the very first time I've ever had any trouble doing this.

Any tips appreciated before I bite the bullet and do a complete reinstall of win7.

Thanks!

---

### Post by ram130 on 2009-11-02
Its worth it. i just did something simular yesterday except mine was a triple boot. Leopard, Windows 7 and Ubuntu 9.10. All installs went perfect but after my second boot i got no menu again. Still troubleshooting before i try and reinstall ubuntu one more time. As for your problem, how long you have had your  hard drive now? and what did you format it in?

---

### Post by mhoy06 on 2009-11-02
> **ram130 said:**
> Its worth it. i just did something simular yesterday except mine was a triple boot. Leopard, Windows 7 and Ubuntu 9.10. All installs went perfect but after my second boot i got no menu again. Still troubleshooting before i try and reinstall ubuntu one more time. As for your problem, how long you have had your  hard drive now? and what did you format it in?

Seems like I've had the hdd for < year

pretty sure chose reiser for ubuntu and I assume win7 was ntfs by default


when you say it's worth it do you mean in general dual booting is worth it or just giving up and reinstalling is worth it?

---

### Post by akand074 on 2009-11-02
Thats odd, there is absolutely no hassle at all to dual boot linux and windows. Matter of fact they are completely independent of eachother meaning neither should effect the other. When your saying: 

> tried to install 9.10 beside win7 on same hard drive.

You mean same hard drive, but different partitions right? Otherwise that doesn't make sense. If they were on different partitions and you installed it correctly with the swap partition on its own separate EXT3 or EXT4 partition then there should not have been any problems. About your windows 7, I honestly don't personally know of anyway in which you could fix it without reinstalling 7, in linux it would be a possibility, but windows I think your out of luck. Someone please point me wrong if I am. But I would say reinstall 7, and let us know how you installed 9.10, just give as much detail as possible to make helping you a bit easier.

---

### Post by ram130 on 2009-11-02
> **mhoy06 said:**
> Seems like I've had the hdd for < year

pretty sure chose reiser for ubuntu and I assume win7 was ntfs by default


when you say it's worth it do you mean in general dual booting is worth it or just giving up and reinstalling is worth it?

lol dual booting is. What boot loader where you using before? also you might want to turn your pc off for 10min, try checking your jumpers and if your drive is detected properly in the bios.

---

### Post by mhoy06 on 2009-11-02
> **akand074 said:**
> Thats odd, there is absolutely no hassle at all to dual boot linux and windows. Matter of fact they are completely independent of eachother meaning neither should effect the other. When your saying: 



You mean same hard drive, but different partitions right? Otherwise that doesn't make sense. If they were on different partitions and you installed it correctly with the swap partition on its own separate EXT3 or EXT4 partition then there should not have been any problems. About your windows 7, I honestly don't personally know of anyway in which you could fix it without reinstalling 7, in linux it would be a possibility, but windows I think your out of luck. Someone please point me wrong if I am. But I would say reinstall 7, and let us know how you installed 9.10, just give as much detail as possible to make helping you a bit easier.

yea same hard drive and win 7 on one partition and swap and ubuntu on another partition. 

here's more details on the whole thing. I get win7 and during setup I create a 128 g partition for it. It also creates some other partition for whatever reason. All is well. Today I attempt to install 9.10. I make an 8 gig swap partition and a 60 gig root partition. I choose Reiser fs for the root partition. I go through install. It fails. Can't read tons and tons of files. Upon reboot 'operating system missing'

I have tried to get windows to fix the mbr. Which is what I assume is the problem here. I assume Ubuntu attempted to write the mbr and failed to do so.

---

### Post by mhoy06 on 2009-11-02
> **ram130 said:**
> lol dual booting is. What boot loader where you using before? also you might want to turn your pc off for 10min, try checking your jumpers and if your drive is detected properly in the bios.


yea used to think dual booting was great until now :)

never had a boot loader on this hard drive before. Only win 7.

bios detects my hard drive. Also no jumpers on my hard drive.

I can boot up to an old xp/9.04 dual boot hard drive and access the win7 data on the other hard drive so the data wasn't overwritten or anything. The whole thing just seems like an mbr problem. Had a thought that I would just reinstall ubuntu (this time 9.04) and hope that I can properly install and set up grub to point to win7 and boot it up when I choose that option.

Any thoughts on trying 9.04? My 9.10 disk must be bad. 

Should note that I tried 64 bit server iso and the 32 bit desktop both fail during install. As always I burn as slowest speeds. Which was 8x (slowest option available).

---

### Post by ram130 on 2009-11-02
> **mhoy06 said:**
> yea used to think dual booting was great until now :)

never had a boot loader on this hard drive before. Only win 7.

bios detects my hard drive. Also no jumpers on my hard drive.

I can boot up to an old xp/9.04 dual boot hard drive and access the win7 data on the other hard drive so the data wasn't overwritten or anything. The whole thing just seems like an mbr problem. Had a thought that I would just reinstall ubuntu (this time 9.04) and hope that I can properly install and set up grub to point to win7 and boot it up when I choose that option.

Any thoughts on trying 9.04? My 9.10 disk must be bad. 

Should note that I tried 64 bit server iso and the 32 bit desktop both fail during install. As always I burn as slowest speeds. Which was 8x (slowest option available).
Sounds like your hard drive might be failing. Try selecting ext4 for your root instead and see how that goes, there is normally no problems in setting up the two. If it fails again, you might wanna run a test on your disk for bad sectors, then again karmic would have warn you of that in Disk Utility.

---

### Post by mhoy06 on 2009-11-02
Thanks for all the help, all is well for now. Did a new install with my old 9.04 disk and can choose windows from the grub menu. Still don't have 9.10 but I'll leave that for another day.

---

### Post by Torquemada28 on 2009-11-02
> **ram130 said:**
> there is normally no problems in setting up the two.

Survey says "No".

Take a walk through the forum; lots of people (myself included) are having massive issues trying to get Windows 7 and Ubuntu 9.10 to dual boot happily. Seems like the Windows 7 bootloader (BCD) doesn't want to share the MBR with GRUB2. If W7 was there first, GRUB2 hoses the windows bootloader and then refuses to add in into the menu list. This happens even if Ubuntu and W7 are installed on separate disks. After that, you can't even load W7 by changing the BIOS to boot from the disk it's installed on.

It's all very frustrating.

---

### Post by Torquemada28 on 2009-11-02
> **mhoy06 said:**
> Thanks for all the help, all is well for now. Did a new install with my old 9.04 disk and can choose windows from the grub menu. Still don't have 9.10 but I'll leave that for another day.

That's because 9.04 uses GRUB legacy, not GRUB2.
I'd leave 9.10 alone until this bootloader clash gets solved.

---

### Post by ram130 on 2009-11-02
> **Torquemada28 said:**
> That's because 9.04 uses GRUB legacy, not GRUB2.
I'd leave 9.10 alone until this bootloader clash gets solved.

Well I'm determined to get my grub2 back up. I mean  it work right after install, then after one reboot i just get a blinking line. No errors or nothing...


p.s: nice system specs :D

---

### Post by ram130 on 2009-11-02
> **Torquemada28 said:**
> Survey says "No".

Take a walk through the forum; lots of people (myself included) are having massive issues trying to get Windows 7 and Ubuntu 9.10 to dual boot happily. Seems like the Windows 7 bootloader (BCD) doesn't want to share the MBR with GRUB2. If W7 was there first, GRUB2 hoses the windows bootloader and then refuses to add in into the menu list. This happens even if Ubuntu and W7 are installed on separate disks. After that, you can't even load W7 by changing the BIOS to boot from the disk it's installed on.

It's all very frustrating.

sorry bout that. I just realize I'm having problem with grub2 working with my triple booting(in progress). It worked after but still no go after a second reboot. I feel Im close tho.

---

### Post by Torquemada28 on 2009-11-02
> **ram130 said:**
> Well I'm determined to get my grub2 back up. I mean  it work right after install, then after one reboot i just get a blinking line. No errors or nothing...

I hate to say it but GRUB2 is looking like a disaster. I've been multi-booting various Linux distros and windows versions for years and any problems with GRUB (legacy) not detecting a windows install has always been easy to fix. GRUB2 just refuses to play the game and no one seems to know WTF is going on.

> **ram130 said:**
> p.s: nice system specs :D

Thanks. Unfortunately, all that nice hardware counts for naught when you can't even get an OS to boot.](*,)
> **ram130 said:**
> sorry bout that. I just realize I'm having problem with grub2 working with my triple booting(in progress). It worked after but still no go after a second reboot. I feel Im close tho.

I still can't work out why Ubuntu 9.10 beta dual booted with W7 fine but the 9.10 final release screwed everything up.
If you find a solution, let me know.

---

### Post by mhoy06 on 2009-11-02
Thanks for the info :)

I just was downloading the files for an upgrade to 9.10 when I hopped over to this laptop and happened to see this thread had been updated. Needless to say I immediately canceled the upgrade. 

Very relieved that this wasn't me, like many of you I have been dual booting linux and winblows for years w/out any real issues. The only thing I can ever think of being remotely close to a grub problem was back when one version didn't automagically include the windows bootloader info and I had to add it manually. Lesson learned. From now on, no matter how confident I am in the previous releases I will check forums for known issues on bleeding edge releases.

---

### Post by Torquemada28 on 2009-11-02
> **mhoy06 said:**
> Thanks for the info :)

I just was downloading the files for an upgrade to 9.10 when I hopped over to this laptop and happened to see this thread had been updated. Needless to say I immediately canceled the upgrade. 

Very relieved that this wasn't me, like many of you I have been dual booting linux and winblows for years w/out any real issues. The only thing I can ever think of being remotely close to a grub problem was back when one version didn't automagically include the windows bootloader info and I had to add it manually. Lesson learned. From now on, no matter how confident I am in the previous releases I will check forums for known issues on bleeding edge releases.

I'm about to attempt a couple of new things to retore the windows MBR and then hopefully reinstall GRUB2. All goes well, GRUB2 might find Win7's bootloader and put it on the boot menu.
I'll let you know how I get on.

P.S.
I think in future, this Ubuntu release will be known as "Bad Karmic".

---

### Post by weaselnet on 2009-11-02
Well the quickest fix is to use EasyBCD from [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) and add your Ubuntu to the Windows 7 bootloader.

To fix your Windows 7 boot start up with the installation CD. Next open a command prompt and type the following.

bootrec.exe /fixmbr
e:\boot\bootsect.exe /nt60 all /force

del e:\boot\bcd
bootrec.exe /rebuildbcd

shutdown -r -t 0

Note: replace e: with the drive your CD is in.

---

### Post by Torquemada28 on 2009-11-02
> **weaselnet said:**
> Well the quickest fix is to use EasyBCD from [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) and add your Ubuntu to the Windows 7 bootloader.

To fix your Windows 7 boot start up with the installation CD. Next open a command prompt and type the following.

bootrec.exe /fixmbr
e:\boot\bootsect.exe /nt60 all /force

del e:\boot\bcd
bootrec.exe /rebuildbcd

shutdown -r -t 0

Note: replace e: with the drive your CD is in.

Yeah, what he said.

I've managed to get back into my original Win7 installation so I'm 50% fixed.

I ran...
```
bootsect /nt60 E: /force /mbr
```
(E: is the Win7 drive)
then
```
bootrec.exe /fixmbr
```
then
```
bootrec.exe /fixboot
```
and finally
```
bootrec.exe /rebuildbcd
```
This last command scanned my drives and allowed me to add any windows installations to my BCD list.

weaselnet's instructions might also work but I didn't follow them exactly (I didn't even read his post before I fixed my bootloader).

Next will be booting to the Ubuntu 9.10 LiveCD and seeing if I can reinstall GRUB2. With any luck, it will now see the Win7 bootloader and add it to the menu.

---

