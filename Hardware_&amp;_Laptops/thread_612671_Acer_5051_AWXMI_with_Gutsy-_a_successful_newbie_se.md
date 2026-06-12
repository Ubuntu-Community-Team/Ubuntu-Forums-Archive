---
title: "Acer 5051 AWXMI with Gutsy- a successful newbie setup from scratch"
date: 2007-11-14
forum: Hardware &amp; Laptops
---

### Post by codeandeffect on 2007-11-14
Hello all, this is my first post and hopefully will help others using the same Laptop to save some time.

I should say first that it took time to get right. It was almost always the shortest, fastest solution that (if I'd tried it first!) worked in the end, so here's my setup and how it was achieved.

**Acer 5051 AWXMI, AMD Turion 64 with ATI graphics and Atheros Wireless.**

**Vista and Acer Tools**
Out of the box it came with Vista, but more importantly the Acer tools preloaded. However the one I really needed was the *eRecovery *tool so that I could back up and burn my factory set Vista install. Despite being mentioned in the manaul it was missing from the Acer toolbar.

I found the *eRecovery * standalone EXE for the specific model on the Acer website for my region, downloaded it, and burned two DVD's of the factory set up.

I then restored the laptop from both discs in turn (they just boot from CD) to make sure it worked, and it did. The backup discs were then thrown in a drawer hopefully never to be used.

**Gutsy Install, what I got**
I had the gutsy disc ready, a network cable in the back for any updates and device specific info, and loaded it. The install ran without a problem. Two Restricted drivers were available for my *Atheros *and *ATI *kit. I had no actions from the additional buttons and no lights from the Wireless or Bluetooth switches on the front (I don't think it has bluetooth anyway).

**Additional partitioning**
Running from the Boot CD again, I re-partitioned the drive so as to get a spare extended partition for partition imaging when I get each bit of setup successfully working.

**First Backup**
So I didn't have to go reinstalling should things not go right, I backed up the initial bland install for speedy recovery later.

**Wireless** After two days of faffing around I used NDISWRAPPER to get my ethernet and wireless going, this worked fine after a few reboots. I continue to have issues with it's automatic choice of the last wireless connection even when I get a cable in the back.Atheros restricted driver remains out of use. No lights appear when I flick the Wireless switch and I cannot tell if they affect it. I think it's disabled.

**Sound:** Messing about in the sound, switching from Surround to Front and mapping them to the main volume preferences I got my Function Key + vol controls going, but they seem work independently of Gutsy's own volume controls. 

**Extra keys:** I used the guide here: [people.freedesktop.org/~hughsient]("http://people.freedesktop.org/~hughsient/quirk/quirk-keymap-index.html") and the pre-written XML for my laptop to get my keys going. Some are still not responding but I can now launch browser and email with them.

**Built in Card Reader:** Following everything already done, it just worked without problem.

**Additional Desktop Effects:** Every enabling attempt failed. I tried Xgl but really got nowhere. Then when I enabled the ATI driver, and used this tutorial [http://ubuntuforums.org/ ... p=3547657&postcount=7]("http://ubuntuforums.org/showpost.php?p=3547657&postcount=7") everything got going in under 5 minutes!

**External WD Passport:** This would not mount automatically as everyone said it should. I tried drivers and tools til I was blue in the face and all I could do was mount it manually. Then I ran checkdisk on Windows to ensure the FAT32 was okay. This did not change anything.
Then I ran it again on another WinXP machine, and it hung. Then I ran defrag, and it said it didn't need it.
Then I plugged it back into the Acer (having removed all previous software and settings in *fstab *and *udev *I'd tried), and it was found, mounted for the user and no longer a problem!

**SSH:** as a web developer, I needed something akin to *WINSCP*, and found this to be very useful: [http://www.ubuntux.org/fuse-sshfs]("http://www.ubuntux.org/fuse-sshfs").

**Hex Editor:** Another essential tool, *ghex* doesn't seem to like the AMD 64, so I am using *hexedit*.

**TrueType fonts:** I needed some of these addiing in, and used forum posts here that used *Nautilus *to easily install them. This was useful: [http://www.stchman.com/install_fonts.html]("http://www.stchman.com/install_fonts.html").

**Backups: ** When I'm happy with everything I have running well so far, I boot from the CD, install partimage and backup the main partition to a spare bit of the disc. So far partimage can backup or restore from backup in under half an hour.

When I first booted Vista I spent over an hour, one hang and two reboots just having it set up, then it ran slow and ran hot.With Gutsy the machine boots in under a minute and runs the 3d desktop items no trouble. I couldn't be happier with it.

---

### Post by ugm6hr on 2008-01-15
My experience was much easier that yours.  I also have an Acer 5051AWXMi laptop.

I used Gutsy 32-bit, and found my wifi just worked (Atheros).  My WD Passport (which I also have!) also works just fine.

Most importantly, I *was* using that advice for Compix (with xserver-xgl), but have no found that the new ATI drivers support AIGLX / Compiz, and are much better than XGL.

See my post (no 3) here: [http://ubuntuforums.org/showthread.php?t=640467](http://ubuntuforums.org/showthread.php?t=640467) in the section under 3D Effects.  You will have to uninstall xserver-xgl to make it work.  You will also get full control / configurability in the ATI Catalyst Control Centre.

PS: I wiped Vista *without* a DVD backup, cos I couldn't get it to make a backup!  I have left my restore partition though.  Shame - I would like to recover the extra 5GB HD space for a new /home partition.

---

### Post by Anup Jayapal Rao on 2008-01-21
Hi,

I installed Gutsy(tried Ubuntu and finally settled for Kubuntu) on my Acer 5051. 
However, I am unable to use it on battery power. I can use this only with AC Power. I have no issues using Vista on battery power(except that I do not want to use it). 

If I boot using battery, as soon as the boot splash finishes (before the login is shown), I see a blank screen with patchy white artifacts.:(
After this it is pretty much CTRL ALT DEL to turn the laptop off.

Can you help me in this regard?

Regards,
Anup

---

### Post by surge89 on 2008-02-19
I have the same problem, someone told me to update my BIOS but I don't think I've got the balls :P So if you have, give it a try.

---

### Post by ugm6hr on 2008-02-19
I have no idea what BIOS I run, but my 5051AWXMi runs on battery just fine.

---

### Post by Darkchef on 2008-06-20
Hi,

I also have an Acer 5051AWXI AND i've seriously been considering of installing ubuntu over vista as it is seriously lagging?

I wonder how you exactly got the wireless working and what driver you used with ndiswrapper to get it going ?

This is the only thing keeping me from switching to ubuntu, any help will be most grateful!!

Dan

P.S. will using 32bit make a difference to using 64bit at all?

And if the wireless will work out of the box shudn't it work while booting from a live cd?

---

### Post by ugm6hr on 2008-06-20
> **Darkchef said:**
> P.S. will using 32bit make a difference to using 64bit at all?

And if the wireless will work out of the box shudn't it work while booting from a live cd?

32- and 64-bit both work fine (I have now moved to Hardy 64-bit via Hardy 32-bit).  Although I think suspend needs fixing (I don't use it) on both.  And the card reader only manages SD cards.

As for wifi - if it is the AWXMi, then your wifi should work from the LiveCD.  It has an Atheros chipset, although someone has told me before that Acer swapped chipsets mid-production.

Check your chipset (on LiveCD) with:
```
lshw -C network
```

If it is the same as mine, it should read:
```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:c7:d9:1e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       logical name: wifi0
       version: 01
       serial: 00:19:7d:33:e4:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.4 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

Good luck with swapping - I did.

---

### Post by Darkchef on 2008-07-06
ok i have this laptop but i've had no luck getting the wireless working on the live CD, i ran "lshw -C network" with these results

```
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:32:31:37
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
```

If anyone can point me in the right direction or to a driver I can use with ndiswrapper it would be much appreciated 

Cheers

Dan

---

### Post by ugm6hr on 2008-07-06
From memory - AR242x in Hardy is actually AR5007.

There are How-tos in here for that (just search in Tips and Tutorials for AR5007).

Note that the instructions for 32 and 64-bit Hardy are different.

---

### Post by Darkchef on 2008-07-07
Thanks, i'll try that out, although i found out that mandriva 2008.1 runs the acer 5051 out of the box, all the hardware just worked, compiz even worked on the live cd.

---

### Post by ugm6hr on 2008-07-07
> **Darkchef said:**
> Thanks, i'll try that out, although i found out that mandriva 2008.1 runs the acer 5051 out of the box, all the hardware just worked, compiz even worked on the live cd.

Your 5051 must be slightly different than mine (my wifi works out of the box).

I think you are right - Mandriva should just work, since your wifi is the same as the EeePC, which Mandriva supports out of the box.

---

