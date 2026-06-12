---
title: "Dell Inspiron 1720 Wlan issues"
date: 2008-09-19
forum: Hardware
---

### Post by Katsu!! on 2008-09-19
So basically I have no Wlan when running Ubuntu, the Wlan works fine in vista so It's deffo not the card.

Problem, I can only access the internet with the Wlan so I cannot run Ubuntu and download any drivers needed from there, I need to be able to download the files and then install them when I switch to ubuntu.

---

### Post by Katsu!! on 2008-09-20
(Bump)

Any ideas at all

---

### Post by Ben Leedham on 2008-09-22
I had the same problem. It is probably that your wireless card is the broadcom one the same as mine. Here is what I did:

You will need a wired connection plug it in.

 

run in terminal:

lspci

 

My output ended with this: Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

 

Go to System >  Administration > Software Sources

Make sure you have selected the Ubuntu CD and alternative sources.
 

Go to System > Administration > Synaptic Package Manager

select and apply the following packages :

ndisgtk

ndiswrapper-common

ndiswrapper-utils-1.9

 

run in terminal:

mkdir wirelessdriver

cd wirelessdriver

 

Read instructions from step 2 from this link. ONLY identify, download and unzip drivers:

[Broadcom Wireless Driver]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")

 

Go to System > Administration > Windows Wireless Drivers (this was installed when you selected ndisgtk)

Select Install New Driver

Locate the wirelessdriver folder you created and select the .inf file.

Select Install

If you have downloaded the correct driver the window will display "Hardware present: yes"

 

Your wireless should now be working. Check by:

 

run in terminal:

sudo lshw -C network

 

Your network devices will be displayed, if the wireless device has UNCLAIMED next to it, it hasn't worked (make sure you identified the correct driver from external link), if not it's all good.

 

Click your network icon in the top right and you should be able to see wireless networks to connect to. If your network has securitry and you can't connect initially, disable it and the work from there.

---

