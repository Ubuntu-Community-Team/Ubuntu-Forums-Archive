---
title: "Installing 8.10 on Thinkpad R52"
date: 2008-11-01
forum: Hardware
---

### Post by tankslappa on 2008-11-01
Hi,

I have a Thinkpad R52 which is currently dual booted with XP Pro and Debian Etch.
I've given up trying to get the wireless to do WPA2, and thought I'd try Ubuntu as it's generally regarded as a more user friendly Debian.

However I've hit a bit of a problem at step 1...

I boot from the 8.10 desktop ISO CD I just downloaded and burnt, and I'm presented with the Ubuntu logo and a menu.
I pick English from the language menu, which closes and leaves me with the English language main front menu.
However none of the main menu options work. Selecting any of them just hangs the machine solid. I can use up and down cursor to highlight options, and the F keys bring up the different submenus.
Install just locks the machine. There's an initial couple of seconds of activity from the CD drive, then silence. No drive activity from the CD of hard drive.
I tried the check CD option. Machine just locks. I tried check the memory, same happens.
I went into the F4 menu and selected the second option down, the safe graphics one, and tried again. Same result.

So not a good start, especially as Debian Etch DVD booted and installed on the very same machine without a problem. The only manual work I had to do was for the centrino wifi driver.

Any ideas?

---

### Post by Earl_Maroon on 2008-11-01
Did you verify the checksum when you downloaded the ISO and burnt the disk? It sounds like you have a faulty install disk. Make sure the checksum of your ISO is correct and burn another. If not, try downloading again.

If you aren't familiar with checksums this should help:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by tankslappa on 2008-11-01
Hi Earl, no I hadn't, but I just did, and it's perfect.

I burnt the CD with the verify option in Nero, so I know the CD matches the iso too.

I know the R52 uses the Intel 915 chipset, and the hard drive is an IDE unit which is connected to the chipset's SATA interface via a PATA-SATA bridge.

I'm not sure about the connection for the Multi CD/DVD-RW drive.

I wonder if this might be causing a problem.

---

### Post by tankslappa on 2008-11-03
No other ideas from anyone then?

Guess it's back to Debian...

---

### Post by onno-itmaze on 2008-11-09
I'm typing this on 8.10 - installed via the Alternate CD - because I needed LVM and Crypt. No issues - that is, no "booting" issues :)

---

### Post by Cirion75 on 2008-11-25
As said earlier, I also think you have a defect CD...
I'm typing this on my Thinkpad R52 that installed 8.10 fine.
Everything works out of the box :)

The only thing bugging me, is that the fan runs continously. Anyone know how to fix that?

---

