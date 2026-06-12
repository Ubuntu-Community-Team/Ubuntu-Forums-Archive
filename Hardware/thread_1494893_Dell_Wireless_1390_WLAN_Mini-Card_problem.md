---
title: "Dell Wireless 1390 WLAN Mini-Card problem"
date: 2010-05-27
forum: Hardware
---

### Post by irv on 2010-05-27
I have a Dell Inspiron 1521 which has issues with Ubuntu 9.04. I did get it going but I needed to use some windows drivers with my wireless card. I wanted to install 10.04 with a clean install, but before doing so I popped in the CD and booted to the live OS and low and behold, no wireless. The laptop came with a Dell Wireless 1390 WLAN Mini-Card, and I was wondering if I change out the card with one that would work with my Dell and 10.04 would this work to eliminate the wireless problem. And if so, does anyone have an idea what card I could get? 
If no one has the answer, I could call Dell to find out if I can do this, but I am afraid I will get someone who does not know Linux. That’s always the problem with tech support, no one seem to know much when it come to Linux OS’s. I think these companies need to hire skilled Linux users not only Window’s guys.
Thanks for the help to those who might reply to this post.

---

### Post by irv on 2010-05-27
After searching the web, I found a real easy fix for this card problem.
This was simple, with the laptop plugged into the internet: 
Go to "SYSTEM" select "ADMINISTRATION" then "HARDWARE DRIVERS" 
This will search for drivers then showed that "broadcom STA wireless driver" was not activated.
Select it then click on the "ACTIVATE" button.
Restart your computer 
Thank you for your help folks and I hope this can help others in the same fix.
I tried it with the live CD so I didn’t have to restart. It loaded the driver and found my network, and also my neighbor and a few business in my area. Now that I have this fixed I am going to do a fresh install of 10.04.

---

### Post by irv on 2010-05-27
Just for the record, I did the fresh install; did all the updates; loaded the codec's; loaded a few software packages; did the "SYSTEM" select "ADMINISTRATION" then "HARDWARE DRIVERS" selected the "broadcom STA wireless driver" then click on the "ACTIVATE" button, and everything went great, and all in about a hour.
I now have 10.04 and Win7 running on my Dell Inspiron 1521 without jumping through hoops.
Ubuntu has come a long way since I started using it back in 2005. Great stuff Guy and Gals, keep up the good work. I now have the best of both world.
I still have a few things I do in Windows, but my everyday computing is done in Ubuntu Linux and I love it.

---

### Post by mandmsf on 2010-06-09
Hey irv,
 
Thanks for this. I just got my hands on my wife's old Dell 1501 and want to use ubuntu 10.04 on it with wifi... i will follow your concise directions and let you know how it turned out for me!
 
- mike
 
ps:  any other tips on getting my dell up and running on ubuntu would be greatly appreciated!  thanks.

---

### Post by irv on 2010-06-10
Don't forget to load the Ubuntu restricted extras.
go to Applications > Ubuntu Software Center > and do a search for restricted extras and then select the install button.
[ATTACH]159950[/ATTACH]

---

### Post by dbwink on 2011-01-10
Thanks, this is the simple, straight forward solution I was looking for!

---

### Post by user19 on 2011-04-03
Hi all,
I have this same wireless hardware on a Dell Vostro 1500. I have read this thread, but my problem is that I am not connected to any network, no physical connection available. So the solution given here is not applicable. Can anyone please tell me of a file that I could maybe download from this windows pc connected to internet and transfer it to the ubuntu installation and build/run it so that my laptop's wireless comes alive? Waiting for a reply,

thanks,

..ab

---

### Post by TBABill on 2011-04-03
Yes, you make sure the CD or DVD is marked as a repository so the system will look to it for the firmware. Once it is, just go to System >> Administration >> Hardware (or additional drivers if it's 10.10). Select the STA driver (if your device is a Broadcom BCM4312 or another it supports) and it will say "activate". Click activate and restart. If you don't want to restart to begin using the newly established connection, just ```
sudo modprobe wl
``` and then go back and connect.

I just did this right from the DVD during a live session of 11.04 beta. I'm online and have not connected to ethernet since starting up the system so I know it works (at least for 11.04). I have a BCM4312 and it's working perfectly with strong signal strength and that's all I did.

---

### Post by user19 on 2011-04-03
i open the system>administration>additonal-drivers, the window that comes up is showing the broadcom sta wireless drivers, however when i click it to click Activate a box comes up saying:
Failed to fetch cdrom:[ubuntu 10.10_maverick meerkat_-release .. (snip) /pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb File not found.

---

### Post by user19 on 2011-04-03
I'm typing this from ubuntu running on my laptop and connected to the internet. In the previous post I said that I was stuck at that prompt coming again and again when I used to click the Activate button. Since the file name was mentioned that this software failed to "fetch", i started looking at dvd contents, and manually started installing all the files that were necessary. Each file that it reported that it failed to fetch, I would look for that file in the dvd, copy to my local directory and use the command:
sudo dpkg -i packagenamehere
to install it. Then go back to the software and click Activate again and it would tell me another file and I would do the same. In the end the total number of files that I installed are the following

bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb
dkms_2.1.1.2-3ubuntu1_all.deb
fakeroot_1.14.4-1ubuntu1_i386.deb
patch_2.6-2ubuntu1_i386.deb

(i installed them in the reverse order of how they are listed above, ie bottom up)

remember in linux, if you want to find a file, you can find it using the find command. For example at one place it said the dkms package is missing, so I issued:
find -name '*dkms*'
and it located the dkms package for me and i copied and installed it.
Also when your dvd is inside the dvd tray its usually going to be mounted on /media. For me, doing:
cd /media/Ubuntu\ 10.10\ i386/
would take me to the correct directory where I would then issue that "find" command that I mentioned above.

After all this, write on terminal:
sudo modprobe wl
and then the scanning and the password for your wifi and you'll get connected.

Thanks all for help!

---

### Post by GR-FI on 2011-09-13
Hi,
I executed what (irv_#2) said and it worked for the driver activation. But I still can't connect to Internet through the wireless. The wifi icon won't sparkle. 
Any idea?
Thanks.

---

### Post by irv on 2011-09-16
> **GR-FI said:**
> Hi,
I executed what (irv_#2) said and it worked for the driver activation. But I still can't connect to Internet through the wireless. The wifi icon won't sparkle. 
Any idea?
Thanks.
If you can see your network but not the Internet, then it is a Internet problem not a network problem.

---

