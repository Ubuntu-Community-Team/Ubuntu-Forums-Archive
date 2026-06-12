---
title: "Crashes: Live CD boot, Installation, Login Screen, &amp; Session"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by &gt;:3 on 2009-06-01
I appear to be having some problems doing a fresh install of 9.04 on my deskop. 

Attempting to boot from a livecd or liveusb results in the system freezing. Using the GUI I cannot install 9.04 as it freezes before I even get to the paritioning table. I have checked for errors on memory, CD & USB using the self diagnostic enclosed. 

**Hardware**
It's A Dell dimension 5000, with: 
PCI Wireless card (Netgear WG311) [using ndiswrapper under 8.04]
PCI Audio card (M-Audio Audiophile 2496)
Extra RAM (Total now 2GB + 512 MB)
2 x SATA Hard drives

**Current Software & Partitions**
I am currently running 8.04 with no problems.
On my 80 GB SATA drive, I have grub and XP (which I want to get rid of)
On my 250 GB SATA drive, I have an NTFS partition with media (backed up), an ext3 partition with ubuntu, and my swap partition. 

** What I'd like **
On my 250 GB SATA drive: Grub, Swap, Ubuntu 9.04 (ext4) and /home (ext4) - making 4 partitions. 
On my (lovely new) 1TB SATA drive: media (ext4) - To be mounted under /mnt as one partition. 

**The system freezes/ hangs when: **
- Trying to boot from a livecd or liveusb. It gets as far as giving me a command prompt, which is responsive, for approximately 5 seconds, then it dumps a list of times, and information/ errors, and becomes unresponsive. 
- Trying to install from a livecd or liveusb. Freezing time varies, I've managed to get as far as selecting my keyboard type and time zone. 
- Login Screen. Having installed on the 1TB drive (as a test) using the text based installer (alternate install CD), I can get the jaunty login screen! Which then freezes. I tried installing using both ext4 and ext3. Both invariably freeze. 
- Session. Having managed to escape freezing once or twice on the jaunty login screen, I can login, and am shown the wallpaper, and menu bars, before it freezes again. 

**What I've tried/ think **
- Check disks for errors. All discs/ USB's were checked for errors before installation
- Test memory. I've tested the hardware, using the option on the liveCD
- Install via Alternate install CD: Works great, but the OS itself still freezes. 
- Hardware problem: I don't think it's a hardware problem, because 8.04 has been running on it for over a year. 
- ext3 Vs ext4: Seems to make no difference. Currently the 1TB drive is formatted with ext3, and is recognised by 8.04, and works fine & dandy. 
- Videocard Compatability: Having read a few threads, there appear to be some problems with Jaunty/ Video Cards. I don't have one, so I'm pretty sure it's not that. 
- Google: Many, Many results. None ofwhich seem *quite* relevant.
- Ubuntu forums: Same as Google.

**Conclusion:** It doesn't work and I don't know why!!!

---

### Post by MichaelSammels on 2009-06-01
Hi. I noticed you used Ubuntu 8.04. Have you tried upgrading to 9.04 using Update Manager?

Also, have you tried burning your Ubuntu disc at a low speed of say x8? This ensures everything is burned correctly.

---

### Post by &gt;:3 on 2009-06-01
I daren't use update manager, because:
I don't want to loose 8.04 till I'm sure 9.04 works
I want a fresh install, because I've added and changed a lot of crap, and it's time for a fresh start. 

Do you think that's my only way?

With regards to the CD burning, I did use a low speed, I can't remember *how* low, but it was definitely towards the low end.

---

### Post by merlinus on 2009-06-01
Did you do a checksum on your downloaded .iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by &gt;:3 on 2009-06-01
No, but I have now, and it checks out.

---

### Post by &gt;:3 on 2009-06-20
*Bump*

Any help here?

---

### Post by &gt;:3 on 2009-07-21
*re-bump*

---

### Post by raven01 on 2009-09-11
i am having the same issues. cept here is another twist. this cd has been used 3 times total to install working systems. my roomates. and mine but i messed up the dual booting 2 times. (tired that night ;) ) but now. i resized windows made plenty of room. and it stalls at the partition editor. and the cd is still basically brand new. not a scratch on the thing.

so any help is appreciated so me and this other guy dont pull our hair out

k thanks!

---

### Post by itsjennifer on 2009-09-11
I am having the same problem but I am not at the late stages of frustration where I am pulling anything out or thinking crazy thoughts rather just waiting patiently for a fix to this little problem!

---

### Post by raven01 on 2009-09-11
its a wild guess but maybe its being confused since my cdrom is on slave...now off to find the jumper diagram...

---

### Post by presence1960 on 2009-09-11
> **>:3 said:**
> I daren't use update manager, because:
I don't want to loose 8.04 till I'm sure 9.04 works
I want a fresh install, because I've added and changed a lot of crap, and it's time for a fresh start. 

Do you think that's my only way?

With regards to the CD burning, I did use a low speed, I can't remember *how* low, but it was definitely towards the low end.

[Boot Options]("https://help.ubuntu.com/community/BootOptions")...I would look into the section dealing with F6

---

### Post by raven01 on 2009-09-11
yea that was it on my end. im all dual booted the right way. changed my rom over to the master secondary and it stopped being mean to me.

---

