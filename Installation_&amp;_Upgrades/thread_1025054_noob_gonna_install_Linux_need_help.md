---
title: "noob gonna install Linux need help"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by Duero on 2008-12-29
I plan to install Linux on my computer but I need to as question before I do it.

1. Can I install Linux so I when i start the computer I can chose Windows or Linux ?? and how do I do that ?

2. because I have NTFS I need Wubi but how does Wubi work ? do I need to make a CD or install Ubuntu fist and then Wubi on it ??

3.because im using a D-Link airplus G DWL-G122 USB adapter to get wireless internet I need help to get Drivers for it on Linux because I Windows finds it self but im not sure Linux does and I tryed google drivers but I can´t find any what I know hope some of u can help.

and last question what MP3 player and video player shall I install and what MSN program ?

---

### Post by howefield on 2008-12-29
1. The Ubuntu install will take care of the bootloader, it will install grub which will pick up your windows system and give you the option at boot to load the operating system you are going to use.

2. If you are using Wubi, download the ubuntu iso and burn it to a CD, then pop it into your computer with windows running, you'll get a window from which you can install via Wubi.

3. Looks like you'll need to use ndiswrapper for that card to get it up and running. So yes, it will work.

---

### Post by bgerlich on 2008-12-29
1. If you plan to keep windows, setup will create the boot menu for you.

2. You don't need WUBI, if I were you I would free up some space on one of the NTFS partitions. The Ubuntu setup will automagically resize the partition and make room for itself. Remember to check the disks for errors and defragment them to ensure smooth and fast setup.

3. Here are instructions on how to get your USB wifi working in ubuntu:[https://wiki.ubuntu.com/NdisWrapper_DWL-G122](https://wiki.ubuntu.com/NdisWrapper_DWL-G122)

You will have a MP3 and movie player installed in your system. After installation you can install/uninstall a lot of other players using Add/Remove programs - it will provide you with a handy list of available options and download them from official site automatically. Personally I use Rhythmbox for music and VLC for movies.

---

### Post by Duero on 2008-12-29
> **bgerlich said:**
> 1. If you plan to keep windows, setup will create the boot menu for you.

2. You don't need WUBI, if I were you I would free up some space on one of the NTFS partitions. The Ubuntu setup will automagically resize the partition and make room for itself. Remember to check the disks for errors and defragment them to ensure smooth and fast setup.

3. Here are instructions on how to get your USB wifi working in ubuntu:[https://wiki.ubuntu.com/NdisWrapper_DWL-G122](https://wiki.ubuntu.com/NdisWrapper_DWL-G122)

You will have a MP3 and movie player installed in your system. After installation you can install/uninstall a lot of other players using Add/Remove programs - it will provide you with a handy list of available options and download them from official site automatically. Personally I use Rhythmbox for music and VLC for movies.


is 17 GB enough 

I have a original Ubuntu DVD Ordered and got free.

and thanks for the help.

---

### Post by bgerlich on 2008-12-29
If you don't plan to store movies or other big files like cd/dvd images on your Ubuntu partition it will be more than enough.

---

### Post by emshains on 2008-12-29
The size of the partition depends on the use of the os on the partition.

17 gigs for me is about a 1/2 to fill up.

---

### Post by Duero on 2008-12-29
> **bgerlich said:**
> If you don't plan to store movies or other big files like cd/dvd images on your Ubuntu partition it will be more than enough.

my C: is total of 30 and it 17 left 

so I hope I can use my 17GB on C for linux

and then I have D:111GB 
and E: 120gb

---

### Post by bgerlich on 2008-12-29
It should suffice. Remember to leave some free space on your windows partition

---

### Post by Duero on 2008-12-29
okey I think I have a new problem the CD I have is Ubuntu for Intel x86 but I have AMD 32 or 64 I think and I have no empty CD´s can I use a usb device to fix that or must  i have a cd??

---

### Post by bgerlich on 2008-12-29
No problem - the architecture will work on your processor. You will only benefit from the 64-bit architecture if you have more than 3 or 4 GB of ram.

---

### Post by pirattrev on 2008-12-29
> **bgerlich said:**
> No problem - the architecture will work on your processor. You will only benefit from the 64-bit architecture if you have more than 3 or 4 GB of ram.

really? how so?

---

### Post by Duero on 2008-12-29
im using my old computer for linux an it is a amd 1.6ghz and 1gb ram

---

### Post by Nathan Sweeney on 2008-12-29
> **pirattrev said:**
> really? how so?

Are you asking how it will work with that architecture or how do you benefit from 64 bit?

---

### Post by bgerlich on 2008-12-29
64 bit architecture allows you to map more than 4 GB of physical memory in your computer (RAM + Video RAM + ?) so you will only benefit when you have , lets say 4 GB RAM and 512 mb graphics card. There are some other cases like BIOS reserving address space for no reason, but other than that you'll need more than 4GB of physical ram to see any difference.

The cd you have will be fine for your system.

---

### Post by Duero on 2008-12-29
> **bgerlich said:**
> 64 bit architecture allows you to map more than 4 GB of physical memory in your computer (RAM + Video RAM + ?) so you will only benefit when you have , lets say 4 GB RAM and 512 mb graphics card. There are some other cases like BIOS reserving address space for no reason, but other than that you'll need more than 4GB of physical ram to see any difference.

The cd you have will be fine for your system.

Thank u because I wanted to use to old crappy computer to learn using Linux then install it on my Better computer.

---

