---
title: "HP Mini 210-1021eg Ubuntu installation"
date: 2010-10-20
forum: Hardware
---

### Post by nearlymagicman on 2010-10-20
Hey,

I want to install Ubuntu on my HP Mini, but now there are two major problems coming at me:
First, there are no drivers at the HP homepage for Linux-Distributions, so how do i get the proper driver?
Second, i have Win7 as a OS at the moment, and there is a recovery hard drive, and i really wanna restore it so i can reinstall Windows if I want to. Anyone has any experience with this kind of problems?


Well, the easiest way to solve that problem would be a installation of Ubuntu as a second OS on the netbook via USB, but I tried it and it only offers me the possibility to eliminate the whole hard drive, and well that would include like everything, HP-Tools, Win7 recovery and my "old" OS.
So if anyone could give me a hand here, the upper problems wouldn't even occur (except for the driver, this problem will stay).

Thanks for your help.


PS: I hope this is the right board, i looked but u only have Laptops, no netbooks, so i posted here 'cause they are kinda similar.

---

### Post by CarlGWatts on 2010-11-05
I've had Ubuntu running on my HP Mini 210 for awhile now just fine.

You don't need to download any drivers from HP.  Ubuntu contains all the necessary drivers except maybe for the WiFi chip.

There should be a program in Windows on your HP Mini that will allow you to burn recovery CDs (assuming you have an external USB CD Burner) that you can use to create recovery CDs for Windows for your HP Mini. But you don't have to burn recovery CDs.

What you probably want to do is install Ubuntu along-side Windows by resizing the hard disk partition containing Windows so it is smaller making room for the new partition where Ubuntu will be stored and run.

I resized the Windows partition so it was 60GB smaller and then used that free space to make a 60GB partition for Ubuntu.  When you do this Ubuntu will automatically install GRUB which will ask you whenever you start the computer whether you want to use Windows or Ubuntu.

Note, there is currently an issue with Ubuntu recognizing the right-click button on the HP Mini 210. To fix this issue after you have installed Ubuntu see the thread titled "HP Mini 210 touchpad right click not working".

If I remember correctly I needed to install an extra Ubuntu driver (using Ubuntu while connected to the Internet via an Ethernet cable) to get the WiFi working.  If so there is an article about it here that describes what to do.  But that driver may automatically be installed now in Ubuntu 10.10

---

