---
title: "How to install ubuntu on a panasonic toughbook?"
date: 2010-10-01
forum: Hardware
---

### Post by poodoopealeoaph on 2010-10-01
I have a panasonic toughbook in my possession and I have been trying to put ubuntu on it for a few hours now with no avail. Whenever I put the disk in and start it up, it will read the usual .iso linux string and start the installer. Then it will show the ubuntu loading screen like at startup but then the screen goes black after it caches the whole disk and it refuses to go any further. I actually just let it sit for 5 or 6 hours to see if it was just being slow and nothing happened. So, my only conclusion is that the install disk didn't have the necessary hardware drivers. So, is there any way around this issue?

oh by the way, I also ran active kill disk on the drive in the case that there was something written on the disk to stop people from putting other than windows on it(down with windows!). I killed to the standard department of defense specs and I had the same issue.

---

### Post by wojox on 2010-10-01
Try F6 at the options screen and set it to "nomodeset"

---

### Post by poodoopealeoaph on 2010-10-01
I tried the nomodeset setting in the options but it just did the same thing as last time. It will show the ubuntu loading screen and the disk will be caching but after the disk is done the screen just goes black and won't do anything.

---

### Post by wojox on 2010-10-01
Do you know what graphics card/chipset you have? What version of Ubuntu are you trying to install?

---

### Post by poodoopealeoaph on 2010-10-02
Details on the computer:

Name	Panasonic Toughbook CF-18 TPentium M 753
Description	Intel Pentium M, 1.2 Ghz, 512 MB, 60 GB
Platform	PC
CPU Type	Intel Pentium M
CPU Speed	1.2 GHz
Internal Memory	512 MB
Hard Drive Size	60.0 GB
Screen Type	TFT
Screen Size	10.4 in
Screen Resolution	1024x768
Optical Drive	None
Graphics Card	Intel 915GMS
Graphic Card Memory Size	64MB
WLAN	Yes
WLAN Standard	802.11a/b/g
Modem	Yes
Network Card	Yes
Bluetooth	Yes
USB Ports	Yes
Operating System	Windows XP Professional
Battery Type	Lithium Ion
Weight	2.1 kg


These specs were pulled off of the panasonic site. The only thing that confuses me is that everything seems ok beside the fact that the processor seems wrong. The processor on their specs is the pentium m but the sticker on the top of the computer says intel centrino.

by the way, I also just tried to go through my bios setup and change around some things and to no avail. I turned off extra video settings and security settings. The thing that makes me think that it may be a security issue in the computer though is that if I wait until the ubuntu loading screen, while it is caching the disk, and I try to hit F6 it stops everything and says that the security isn't recognized and can not go any further. This isn't a new issue either, this happened before I looked through and changed some of the bios settings.

---

### Post by poodoopealeoaph on 2010-10-02
oh I would just like to add that I just checked the bios again and it seems that the processor is the pentium m. sorry about the confusion and also if I sounded like an idiot with my explenation.

---

### Post by poodoopealeoaph on 2010-10-02
Ok so I figured it out!! I feel like a complete idiot for not trying it sooner! I realized that it was just having trouble opening the drivers for the regular install. So, I just tried to run it with the "install as text" option and valla! Only issue though is that since I don't want to burn more disks, I only have the alternate 32bit disk for kubuntu lucid. Though I hate kubuntu, this is for a business that is very used to windows 7. So, they may actually find it to be very similar. If not anything else, they will definitely think it is way prettier than any os they have used lol. Thanks for the help though!

---

### Post by wojox on 2010-10-02
Once you get the base installed if you want to go back to gnome just install

```
ubuntu-desktop
``` 

Then [uninstall kubuntu]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by poodoopealeoaph on 2010-10-03
Ok so false alarm. I didn't get it to work. Every time it finishes the install, it restarts and says

```
starting:"terminal"
unknown command:"terminal"
```

this happened when installing kubuntu 32 bit, xubuntu 32 bit, and ubuntu studio 32 bit. So, I'm fairly certain that it has nothing to do with the os.

So... what would be the reasoning behind this issue?

---

