---
title: "HP DV6500t Installation Woes"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by Exvin on 2007-07-24
Hi there, 

I recently purchased a new HP DV6500t CTO with the following specs:

Intel Core 2 Duo T7300 at 2.00 Ghz
15.4" WXGA Widescreen at 1280 x 800
Nvidia Geforce 8400M GS (with 383MB of shared RAM)
Intel 4965AGN with Bluetooth wireless
160GB 5400RPM SATA drive
2 Gigs of RAM
...and a few extras: Fingerprint reader, webcam, and mic

I tried Vista for a few days but after being hit with several BSODs (Blue Screen of Death) I'm not liking it. I had always wanted to try Ubuntu, and figured what better time to try than now.

At first I tried the regular GUI installer for 7.04, but that didn't work -- the X Server failed. Then I tried the Alternative text-based installer. I was able to find my way through the installer setup and Ubuntu seemed to install just fine.

However, when I restarted, I got the splash screen and after that the same X Server failure -- screen detected, but nothing usable. I did some searching on these forums and on Google, but didn't find anything too specific to my hardware setup. I tried updating the kernel to 2.6.20-16-generic, but that didn't do anything. I've also tried to reconfigure X, but that didn't help either...

And besides the X Server problem, I also noticed that right before X fails the screen reads:

Starting up ...
[0.530978] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
Loading, please wait...

Being a Linux noob, I'm pretty much at the end of my rope and would appreciate any and all insight.

Is there a way that I can download the latest nVidia drivers via a repo -- would that work/help?

---

### Post by NickArgyle on 2007-07-24
Do you have terminal access?

---

### Post by Exvin on 2007-07-24
I'm pretty new at Linux, but I assume that by terminal access you mean can I enter commands and such?

If so, then yes. After X  informs me that it failed to start, it drops me back to a black screen  where I can login and issue commands... It's DOS-like, for lack of a better word... :(

---

### Post by NickArgyle on 2007-07-24
try running  "sudo apt-get install nvidia-glx" If the install is succesfull then type "sudo dpkg-reconfigure xserver-xorg" and follow the guided instructions to reconfigure X. Make sure you select the nvidia driver.

---

### Post by Exvin on 2007-07-25
I tried what you suggested, and made sure that I selected nVidia during the setup. But, alas, I'm still having the same problem. When I reboot the computer, X still fails in the same place and I still get the mem resource error.

Any other suggestions?

---

### Post by NickArgyle on 2007-07-25
Sorry, if its not a basic X issue dont know that I can help you as I am still a bit of a noob myself. If you cant get this to work then keep in mind that there are other linux distrobutions. My hp dv 9000 wouldnt boot ubuntu (although after a few weeks I eventually got it) and I tried several other distros. You could try out Mepis, pclinuxos, or sabayon. Those all worked mostly out of the box on my hp.  Although if you are dead set on ubuntu best of luck to you.

---

### Post by Exvin on 2007-07-25
Haha, no worries. I'll spend a few more days on the forums trying to figure this problem out and then I'll be hunting for another distro...

I know that there are a few people out there who have managed to get Ubuntu working on a DV6500T, so I'm hoping that I might run into a few on them pretty soon.

But, anyways, thanks for trying to help, Nick

---

### Post by mooseboy on 2007-07-25
It sounds like you got my laptop :) I'd ordered one with an identical configuration 2 weeks ago and HP sent me somebody else's laptop with a different configuration. Now I get to wait another 2 weeks for them to build me ANOTHER one. Ugh. 
Incompetency issues aside, I look forward to try to get this laptop to work. It has a lot of neat new features that I'd really like to try and get working right. That said, I'm pretty sure that the non-working video problem has been documented already. Some people had success with using the alternate install CD and using the kernel flags "noapic" and "nolapic". The chipsets are bleeding edge (just having been released in may) and thus not supported by Feisty Fawn (released in march). Some people have had better luck with Gutsy Gibbon, though it's still in alpha. I've played wtih Gutsy some on my current laptop and it worked rather fast and nicely. I hadn't run enough apps to test stability.

---

### Post by Exvin on 2007-07-25
Besides the fact that the dv6500t comes with a boatload of crapware, it's a really nice laptop, and  I'm quite pleased with it so far. Sorry to hear that HP screwed up...

At first I tried the regular GUI installer for 7.04, and then after that failed, I tried the alternative text-based installer. With the text-based installer, I managed to get the drive formatted and Ubuntu installed, but when installation completed and I rebooted for the first time, it didn't load past the splash screen -- that's when the x server tries to start, but fails.

I'll give the "noapic" and "nolapic" commands a go, and I'll see what happens. I'll post the results sometime today...

Yeah, it makes sense that 7.04 might not work with the dv6500t because of the brand new hardware...but it'd still be nice to get Ubuntu running...

---

### Post by Exvin on 2007-07-25
I just tried running the GUI installer with the "noapic" and the "nolapic" commands appended to the parameters, and I got something new...not sure if it's any better than before though

After the splash screen I see the following:

BusyBox v.1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

Since I'm quite new in the world of Linux, I have no clue what this means....

Any suggestions? I might just give Gutsy Gibbon a shot...

---

### Post by mooseboy on 2007-08-04
gutsy tribe 3 supports the video straight out of the box. 802.11n is supported when you upgrade to the latest "stable" kernel in gutsy. Next priority for me is getting sound working.

---

### Post by dansen926 on 2007-08-15
I've found and installed workarounds for the video card and sound card, but now I can't get the cdrom drive to mount at all! It is the strangest thing I have ever seen, because I installed fiesty from the CD-ROM drive! in the /dev folder I can't find anything to suggest a cd-rom drive. I have:

sda1 for my NTFS (Windows Vista)
sda2 for my ext3 (Ubuntu)
sda3 for ??? who knows what ???

and 

< sda 5 > for swap space

I'm wondering if sda3 is the cd-rom drive, but when i try mounting it (mount -t iso9660 /dev/sda3 /mnt/testcdrom), it gives me an error due to a wrong filesystem. So I'm totally lost on that one. Please help!!:confused:

---

### Post by cynic99 on 2007-11-20
I just tried installing GG 7.10 on my new dv6500t SE today and it still appears to be a crapper. Did any of you find a resolution?

thanks 
c99

---

### Post by lde on 2007-11-26
Hi there, 

I see that most of the activity on this forum happened several months ago, but I have the same machine and have been driving myself crazy trying to get Kubuntu 7.04 or 7.10 running on it.  The specs: 

HP Pavilion dv6500t CTO NB
- Genuine Windows Vista Home Premium (32-bit)
- Intel(R) Core(TM) 2 Duo processor T7500 (2.20 GHz, 4 MB L2 Cache, 800MHz FSB)
- 15.4" WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
- 2GB DDR2 System Memory (2 Dimm)!
- 128MB NVIDIA GeForce 8400M GS
- Intel(R) PRO/Wireless 4965AGN Network Connection and Bluetooth(TM)
- 250GB 5400RPM SATA Hard Drive
- SuperMulti 8X DVD+/-R/RW with Double Layer Support

I am trying to set up a dual-boot machine, keeping Vista on it for now, even though it is of little use to me for what I need to do with it.  I have posted some of what I have done here, for background: [http://kubuntuforums.net/forums/index.php?topic=3088975.0](http://kubuntuforums.net/forums/index.php?topic=3088975.0), and have gotten a bit further with running the Feisty Alternate CD.  Actually got it installed, but then couldn't get the NVIDIA driver sorted out properly (probably because I am not entirely sure how to do it line by line), and the DVD drive suddenly seemed not to work any longer (not mounting, I suppose). 

So, I ran VIsta's recovery CD, and have tried again, but with the Gutsy (Kubuntu) live CD, and I still have the same hardware problems (screen goes black, even though I can hear things running and setting up).  This despite entering some of the boot parameters.  

I am going to give another bash with Feisty Alternate CD, and see if i can get it running again with the NVidia fix, but I really need to get back to work, and I need the computer to have some linux capability. 

Can any of you who knows the idiosyncrasies of a Feisty or Gutsy install with this particular machine please help with a brief guide as to how to cut through this stuff?  It is daunting for a newcomer to try work these issues out surfing various fora, especially since most tell you what needs to be done, but not quite how to do it.  

Will greatly appreciate any help. 

Thanks!

---

### Post by fenixartzz on 2008-01-02
i have same machine just with smaller hdd and a 12 cell battrey

i did clean install of xp the very first following the guide on notebookreview.com forum

and then i did clean install of gutsy gibbon, with dual boot using grub loader of ubuntu

though i did  face few issuesbut now have very much everything running

regarding that mem pci allocation error on first page i get it too but its general error which many other ppl get using other notebook but everythings working fine

let me know your exat issue to see if i can be of any help

very much everthing worked out of the box two general issues i can recall of 1) sound soln - install backport generic package
                                                                                                                          2) Video soln - enable restricted drivers for nvidia  

thanks

---

