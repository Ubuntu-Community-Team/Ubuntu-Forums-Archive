---
title: "Ubuntu refuses to detect my SD Card"
date: 2011-05-17
forum: Hardware
---

### Post by Kitkin15 on 2011-05-17
I have an SD Card for my Camera and Ubuntu seems to refuse to detect it. When i put it in it will not show up, no matter how long its in. When i boot up in Windows (On the same Laptop) It detects it right away with no problem. Why does this happen?

Thanks

  -Kitkin15

---

### Post by 3xp10r3r|X13 on 2011-05-17
Hello there,
I once had a similar problem on opensuse. The filesystem format of the medium I wanted to mount wasn't installed, so I had to add it to /etc/filesystem.

- BUT the external hard drive was at least recognised
- AND I'm not sure if there's an /etc/filesystem file in ubuntu

Hope this helped :)

---

### Post by coffeecat on 2011-05-17
Is this an SD card or a SDHC card? What capacity?

---

### Post by danjh2705 on 2011-05-17
Try inserting the SD card BEFORE you boot the machine .. it usually works then.

---

### Post by Kitkin15 on 2011-05-17
> **danjh2705 said:**
> Try inserting the SD card BEFORE you boot the machine .. it usually works then.

Tried that as well, and it didnt work.


Also, this is a SDHC Card, i didnt know there was a difference. Its 8 GIG, SanDisc.

---

### Post by Kitkin15 on 2011-05-17
P.S. It detects EVERYTHING except this card, i have Ubuntu installed on my EXT HDD (I took my HDD out of my computer and tricked the disc to believe that my EXT was in INT) and it detects the side of my EXT HDD that has files that i use on Windows and everything (Which is what it should do) And it detects all flashdrives, Zunes, and phones that are plugged in. Its just the SDHC

---

### Post by coffeecat on 2011-05-18
> **Kitkin15 said:**
> Also, this is a SDHC Card, i didnt know there was a difference. Its 8 GIG, SanDisc.

Yes, I thought it might be. I've found that SDHC cards are detected on some readers but not others. I first noticed this with an old card reader integrated with a floppy drive that I'd incorporated into my main desktop machine. In Ubuntu a standard SD card was detected but not an 8GB SDHC, whereas in Windows 7 on the same machine both SD and SDHC cards are detected. I tried other card readers and Ubuntu could detect SDHC in some but not others. I suspect that there is a driver issue with some card reader chipsets. 

For example, I have two of those little USB card readers about the size of a large USB pendrive with one SD slot. The one that works with an SDHC card gives this output with lsusb:

```
Bus 001 Device 003: ID 04cf:8819 Myson Century, Inc. USB 2.0 SD/MMC Reader

```The one that works with SD cards only (in Ubuntu) gives this:

```
Bus 002 Device 004: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
```Which is interesting because I also have a USB optical drive enclosure with a Genesys chipset which is problematic in some versions of Ubuntu, but that's another story.

I don't know of any solution if your particular card reader won't read SDHC cards - it's probably a faulty driver. The only solution I know is to get one of the small USB card readers and use that. They're not expensive but it would be a gamble. If you were unlucky you might end up with one which won't read SDHC cards either.

It's not much consolation, but your laptop card reader will probably detect and read a standard SD card in Ubuntu. SD cards are 4GB or less, although some 4GB cards are SDHC.

---

### Post by Kitkin15 on 2011-05-18
Ok, so i guess im just going to have to put up with using Windows...... :( Lol. I dont have the money to spend right now to get a USB Card Reader (Not trying to play the "poor card") so ill just tolerate it for the next few months.

Thanks for the help everyone

  -Kitkin15

---

### Post by coffeecat on 2011-05-18
> **Kitkin15 said:**
> I dont have the money to spend right now to get a USB Card Reader (Not trying to play the "poor card") so ill just tolerate it for the next few months.


I sympathise. Out of interest, post the terminal output of:

```
lsusb
```It would be useful to get the details of your particular card reader. I'll be doing the same with my collection of card readers and a list of those that do and don't work with SDHC cards will come in handy for others.

The ironic thing is that my thumbdrive-sized USB card reader that works with SDHC cards came "free" with a 4GB standard SD card. Whereas the one that doesn't work with SDHC cards is one I paid good money for. :(

---

### Post by iluminameluna on 2012-01-10
> **coffeecat said:**
> I sympathise. Out of interest, post the terminal output of:

```
lsusb
```It would be useful to get the details of your particular card reader. I'll be doing the same with my collection of card readers and a list of those that do and don't work with SDHC cards will come in handy for others.

The ironic thing is that my thumbdrive-sized USB card reader that works with SDHC cards came "free" with a 4GB standard SD card. Whereas the one that doesn't work with SDHC cards is one I paid good money for. :(
I'm having a similar problem. Mine is a Kingston SDHC 4G card in a TravelLite SD/MMC card reader (1 slot) that's never given me a problem w/ up to 2G SD & SDHC Class 4 cards. Now, I just took a brand-spanking-new Kingston 4G SDHC card Class 4 & stuck in said card reader & NOTHIN'! Here's the result of lsusb:


jessie@jessie-OptiPlex-GX270:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 001 Device 002: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I tried adding after starting Ubuntu & before. If during a session & using Disk Utility to find it, it did but cldn't even power it down, said device busy.

Unfortunately, I don't have another card reader & it'll take WEEKS to get one down here (I'm in El Salvador).

Any ideas AFTER the last post (3 wks ago)?

---

### Post by iluminameluna on 2012-01-10
Here's the result for "lsusb" w/ the self-same card reader but this time w/ a Kingston 1G SD card:

jessie@jessie-OptiPlex-GX270:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 008: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 001 Device 002: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And w/ the Kingston 8G SDHC Class 4 micro-card w/ a full-size adapter:

jessie@jessie-OptiPlex-GX270:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 008: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636
Bus 001 Device 002: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Though I have to say I can't see what's on it but that might be 'cause it's been in my BlackBerry ..

One last thing: I don't have Windows on ANY of my machines (desktop, ASUS netbook) so have no alternative way of viewing or accessing these cards unless it's thru my netbook & THAT "paperweight" is the reason I'm trying to use my 4G card. I need to install an OS on it & haven't been able to ... :/

---

### Post by Mark Phelps on 2012-01-11
Sorry ... but I have the same problem with my PC -- refuses to recognize the internal card reader in Linux (works FINE in Win7!)

These card readers all seem to need special drivers -- which Linux has a real hard time providing.

I "solved" my problem by buying a cheap USB-plugin card reader. Works every time.  Bit clumsy, but it works.

---

### Post by Kitkin15 on 2012-01-18
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 058f:a001 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


That is what comes up.


Sorry it took so long for me to reply, i was in AIT training and didnt have much time to get on my laptop the last 2 weeks lol.


So basically all i need is a driver for it, i googled and didnt find any Linux support for it. 

Anyone know where i can get a Driver?

  -Kitkin15

---

### Post by Procrastes on 2013-04-09
Just to chime in with more information that might be related. I just updated my laptop from 10.04 to 12.04 and see problems recognizing a 2gb SD card in the multi media slot which worked fine under 10.04.

Unlike the original post, I have not had much luck  recognizing any other USB storage either.
I inserted an IPOD mini which had always worked before and, while it showed up in diskstats, it did not automount. I mounted it manually but was not able to get Rhythmbox to recognize it. This all worked before the upgrade.

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b036 Chicony Electronics Co., Ltd Asus Integrated 0.3M UVC Webcam
Bus 002 Device 006: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader

---

