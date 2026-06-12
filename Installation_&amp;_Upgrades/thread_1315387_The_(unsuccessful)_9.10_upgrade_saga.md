---
title: "The (unsuccessful) 9.10 upgrade saga"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by kwalters on 2009-11-05
Been with Ubuntu since about version 6 and never had so much trouble as I have had this week with the 9.10 install process.  I have now tried 3 separate .ISO downloads and done 2 CD burns from each; I keep assuming that something has gone wrong with that process  -  but not 6 times, I don't think.

The first sign of problems, after an apparently successful installation, was that my Draft N Belkin wireless dongle would not connect to my wireless network (and therefore this machine could not connect to the internet)  The blue light came on on the dongle, and the screen picked up the usual crop of available networks round here.  But it would not connect to mine or to the BT OpenZone in range.  It just kept coming back and asking for the WEP security code again and again.  This has now happened on 6 separate installations.

I sustituted my 8011G Belkin dongle and everything connected as advertised, but only at 54 Mb/sec.  That allowed me to download the NDIS Wrapper GUI program.  This told me that no wireless driver was installed. 

I attempted to install it, (the Draft N one) and here came a second major disaster.  I keep the appropriate .INF file (and the others that go with it) on a partition called FATSWAP   -  formatted as FAT and able to transfer files between Windows and Linux.  That partition could not be found by Ubuntu 9.10.  I tried putting the files required on to a USB stick; but that could not be seen either. The only locations that appear if I go to Places and Computer are File System and CDROM0.  Normally that takes you to every partition and USB location on the machine.

I suppose I could have tried putting the files on to a CD to activate (presumably) the right wireless drivers.  But an inability to address any other partitions or USB devices made me not bother to persevere with wirelss drivers. That is not the sort of installation I want to work with.

The only other solution I can think of is to install 9.04 again and do an upgrade.  But I don't want to do that really unless someone convinces me that all my problems have arisen from a fault (several faults) in the install CD.

Incidentally, there is a peculiar version of Grub in this 9.10 installation.  It is called version 1.97 beta and it certainly is a beater as far as I am concerned.  There is no Menu.lst file in /boot/grub, so I would have no idea how to change the default OS selected at startup.  At present I am back on version 9.04 and a Grub version that I can understand.

Any ideas out there?

[email]keithwalters2002@yahoo.co.uk[/email]

---

### Post by jjcv on 2009-11-05
You might have to do some research before you attempt the upgrade again.

Have a look what your wireless drivers is in 9.04 and then see if you can find any information in the ubuntu forms for that driver, especially with 9.10.

Grub in 9.10 is version 2 and there is not longer a /boot/grub but rather a /etc/grub.d and /etc/default/grub

The new grub seems to have created a few problems for people on 9.10 and it is worth doing some further reading on this also.  Here is something that may help:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

---

### Post by kwalters on 2009-11-06
Thanks for the link on grub2 - I will read that and follow up.

However, the wireless driver is not the key problem.  I am sure I could get it to work, if necessary by emailing the .INF file for RT2870. However, an operating system in which I can only see the Ubuntu root file system and no other partitions; and in which I cannot use any usb flash drive or usb HD, seems a pretty questionable asset.

Merely en passant, I just installed again (that is the 7th install from 3 different .ISO downloads) and formatted the partition to EXT4 instead of the EXT3 I have used thus far.  No change; the same limitations apply.

Now back on 9.04 and legacy Grub

KW

---

### Post by Onesimus on 2009-11-06
Presumably you have followed this guide:

[http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

---

### Post by Lateralis on 2009-11-06
I may have grabbed the wrong end of the stick, and so I apologise in advance if I am giving advice which isn't relevant.  But there are knownn issues surrounding the mounting of NTFS and vfat partitions in Karmic, and this has been raised in a few threads about the forum.  I had some issues on my laptop but not on my desktop, for instance.  However, my laptop partition issues surround the use of USB flash drives and external hard drives, rather than internal drives.  

The solution for me was to update my udev from the proposed repository.  USB keys and whatnot now automagically mount.  Before that I had to mount them by hand...

... which leads me to ask you whether Ubuntu has found the drives and not mounted them, or whether it just can't see the drives at all.  

With a USB flash drive connected type 

```
lsusb
```

into the command line to see if it can find the drive. 

Also type 

```
sudo fdisk -l
```

into the command line.  If you can see the USB flash drives and the vfat/Windows partitions listed then you can mount them by hand and access the data.  This though is a "work around" to something which before just used to work.  The only solution I have seen so far for this particular problem is to update udev from the proposed repository.  

Hope this helps.  


As for Grub, I'm still using 1.5.  I upgraded from Jaunty to Karmic but Grub wasn't updated.  And to be honest, Grub 1.5 works fine for me so I don't see much need to upgrade.

---

### Post by kwalters on 2009-11-08
Many thanks for all the replies. Yes, I have read the guide to installing NDIS wrapper using the command line and I did make it work once when the Belkin 8057 was too new for Ubuntu to recognise.

Since about Ubuntu 8.10 (it might even have been 8.04) my USB dongle has been recognised and installed without any input from me;  until version 9.10 that is.

I did lose the drivers once and used a GUI program to reinstall them.  It was a package I downloaded, but cannot remember whether it was using Synaptic or the Add/Remove tag.  I found it by searching for NDIS and, when installed, there emerges a new entry under System then Administration: it is called Windows Wireless Drivers and only requires you to tell it where the appropriate .INF file can be found for the wireless device.  I find this GUI system a lot easier (probably BECAUSE it is less challenging for people of my limited skills.

Also, in actuarial terms, my chances of living long enough to solve any significant problem using my limited command line skills are probably remote.

I am convinced, as I said above, that this program would allow me to make the wireless driver work.  But an inability to see any other particions or USB devices is, to me, a showstopper.

Merely for info, I had one last effort today.  I installed another copy of Ubuntu 9.04 on another partition and then did the online upgrade to 9.10.  Why I thought that might be different I don't know.  But I ended up with exactly the same limitations as on the direct install from the live CD:

No wireless driver
No ability to see partitions other than the Ubuntu partition in use and no ability to use USB devices

The one difference was that it did not impose Grub 2 upon me; for this relief, much thanks.

I am now closing this thread as I am happy with version 9.04.  I shall await version 10.04 next April and hope for a happier transition

Thanks again to those who responded

KW1

---

