---
title: "USB wirelss adapter not recognized by ubuntu"
date: 2008-08-06
forum: General Help
---

### Post by hgfdsa on 2008-08-06
The list of networking options only has what I believe is a dial-up modem and wired networking, not my wireless. This was under the live CD, but I'm defragmenting my drive to install ubuntu know, and I want to know how to set up my internet connection. Do I need to get drivers or something? Model is WUSB11v4, by linksys. Thanks.

---

### Post by hgfdsa on 2008-08-06
OK, I took a peek at that driver. Can I get you to remove the wusb11v4 driver and try the netusb driver instead.

Code:

ndiswrapper -e wusb11v4
ndiswrapper -i NETUSB.inf
ndiswrapper -l

And if that looks like it worked can I get you to go through the modprobe, dmesg, iwconfig from the earlier post.

Let us know how you get on,

Chris...


I found the above post on another linux forum about my adapter. How do I get/use NETUSB.inf?

---

### Post by hgfdsa on 2008-08-07
Is there anyway to get my usb adapter to work or will I be forced to run ethernet cable all the way from my router?

---

### Post by hgfdsa on 2008-08-07
anyone?

---

### Post by hgfdsa on 2008-08-07
C'mon, there's gotta be someone who knows what to do. Or at least someone who can say it's not possible.

---

### Post by hgfdsa on 2008-08-09
Bump again...

---

### Post by Sycron on 2008-08-09
You may look here [http://ubuntuforums.org/showthread.php?t=383466&highlight=wusb11v4](http://ubuntuforums.org/showthread.php?t=383466&highlight=wusb11v4) then here [http://ubuntuforums.org/showthread.php?t=473701](http://ubuntuforums.org/showthread.php?t=473701) . 

A search on ubuntuforums is not hard at all...

---

### Post by the real omni on 2008-08-09
It is indeed possible.

1) Go to the manufacturer's website and download the driver installation file for Windows XP. (This will almost certainly be a .EXE file or a .ZIP containing a .EXE file.)

2) Whip out your trusty terminal window (ALT+F2 and type 'gnome-terminal')

3) Extract the data from the .EXE file. This will extract all the files into the directory the .EXE is in, so before you do this if your .EXE is on the desktop it's a good idea to create a folder and move the .EXE into the folder before performing the cabextract. 

cd your way to wherever the .EXE file is and type

```

cabextract (filename)

```

4) Locate the .INF file within the pile'o'files that gets dumped into the folder with the .EXE in it.

5) Open System -> Administration -> Windows Wireless Drivers

6) Click "Install..." and navigate to where the new .INF file is located.

Select the file and once it's installed you should be good to go. I don't think a log-out or reboot is necessary. 

Hope this helps :)

---

### Post by hgfdsa on 2008-08-09
> **the real omni said:**
> It is indeed possible.

1) Go to the manufacturer's website and download the driver installation file for Windows XP. (This will almost certainly be a .EXE file or a .ZIP containing a .EXE file.)

2) Whip out your trusty terminal window (ALT+F2 and type 'gnome-terminal')

3) Extract the data from the .EXE file. This will extract all the files into the directory the .EXE is in, so before you do this if your .EXE is on the desktop it's a good idea to create a folder and move the .EXE into the folder before performing the cabextract. 

cd your way to wherever the .EXE file is and type

```

cabextract (filename)

```

4) Locate the .INF file within the pile'o'files that gets dumped into the folder with the .EXE in it.

5) Open System -> Administration -> Windows Wireless Drivers

6) Click "Install..." and navigate to where the new .INF file is located.

Select the file and once it's installed you should be good to go. I don't think a log-out or reboot is necessary. 

Hope this helps :)

thanks, I'm going to try this. I found some other guides, but I just installed ubuntu and haven't even used it yet because of it, so really basic stuff confuses the crap out of me.

---

### Post by hgfdsa on 2008-08-09
I tried cabextract but was told I didn't have it installed and sudo apt-get and whatever else it said to do gave me an error saying I didn't have the package. So, can I download it from my XP installation and install it in ubuntu, or can I preferably just extract the .exe from within windows?

EDIT: Winrar was able to extract the .exe and there is an autorun.inf file in there, is that what I'm supposed to use? I'm not going to try this yet though because I need to repartition/reinstall ubuntu.

---

### Post by hgfdsa on 2008-08-09
> **the real omni said:**
> It is indeed possible.

1) Go to the manufacturer's website and download the driver installation file for Windows XP. (This will almost certainly be a .EXE file or a .ZIP containing a .EXE file.)

2) Whip out your trusty terminal window (ALT+F2 and type 'gnome-terminal')

3) Extract the data from the .EXE file. This will extract all the files into the directory the .EXE is in, so before you do this if your .EXE is on the desktop it's a good idea to create a folder and move the .EXE into the folder before performing the cabextract. 

cd your way to wherever the .EXE file is and type

```

cabextract (filename)

```

4) Locate the .INF file within the pile'o'files that gets dumped into the folder with the .EXE in it.

5) Open System -> Administration -> Windows Wireless Drivers

6) Click "Install..." and navigate to where the new .INF file is located.

Select the file and once it's installed you should be good to go. I don't think a log-out or reboot is necessary. 

Hope this helps :)

I couldn't find windows wireless drivers under administration and running the .inf both inside and outside terminal didn't work.

---

### Post by hgfdsa on 2008-08-09
It seems as if though a pre-existing internet connection is needed to get wireless to work so I'll install that before following this guide: [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

---

### Post by the real omni on 2008-08-09
> **hgfdsa said:**
> I tried cabextract but was told I didn't have it installed and sudo apt-get and whatever else it said to do gave me an error saying I didn't have the package. So, can I download it from my XP installation and install it in ubuntu, or can I preferably just extract the .exe from within windows?

EDIT: Winrar was able to extract the .exe and there is an autorun.inf file in there, is that what I'm supposed to use? I'm not going to try this yet though because I need to repartition/reinstall ubuntu.

In order to install just about anything using apt-get you need to be connected to the internet. If your wireless isn't working you'd need to plug in via ethernet cable in order to install cabextract (sorry I just assumed you were wired in)

The autorun.inf file is not the inf you're looking for. It's probably in a sub-directory or something. Look for all the files ending in .INF and if there's only one other than the autorun, I'd wager that's the lil' bugger we're looking for.

---

