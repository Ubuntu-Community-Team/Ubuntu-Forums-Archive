---
title: "Scared to put Xubuntu on my laptop"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by ccalvinfowler@aol.com on 2007-07-23
First off let me list specs of laptop

Compaq Presario R3120US

AMD Athlon XP PRocessor 3000+
797 MHZ
512 MB RAM
Nvidia GeForce 4 420 go 32m video card
Agere systems Ac'97 Modem
Broadcom 54g MaxPerformance 802.11g Wireless adapter
Realtex RTL 8139 Family PCI Fast Ethernet NIC
TI PCI-1620 Card Bus Controller w/ultramedia (x2) PCMCIA Adapter
SoundMax Integrated Digital Audio Card
and USB Controller 


Now, I previously nstalled Red Hat and had a real b***c of a time trying to figure out how to get the wireless network card to work.  Everything else seemed to work, but i really couldn't tell. I spent 6 months trying to figure it out and i couldn't.  So here I am again.  Since my laptop is my only connection to the internet, i need to know what i am doing before i try this again.  I am going to use xubuntu 7.04.

Also, in case you are wondering why i don't just use the Realtek adapter w/cable, the answer is simple.  It is a laptop. I would like to be anywhere in my house and go online.

I am not trying to sound like a smart-a**, I just want to make everythiing clear.  I have read a lot of posts here and i notice that a lot of questions are asked before the problem even gets answered.  I am jsut trying to answer as many questions as i can so that i can get as much help as i can.


Thanks in advance.

---

### Post by arrenlex on 2007-07-23
The installation CD is a liveCD. Boot from it and see if you can connect to your home network. If you can, then everything works and you can go ahead and install. That's how I tested the water, and everything Just Worked(tm) for me.

---

### Post by mrreality13 on 2007-07-23
Ive used 6.10 on a lappy that had a net gear a/b card and i saw it so just look in ubuntus hardware repository to see if its there
[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)
:popcorn:

---

### Post by ccalvinfowler@aol.com on 2007-07-23
Still looking in other places, but i would like to know if the alternate cd from xbuntu is also a live cd (600+mb) or just the smaller install image(400+mb)  I am downloading the larger one at this moment

---

### Post by mrreality13 on 2007-07-23
sorry on that front ive never used the alternate cd's

---

### Post by ugm6hr on 2007-07-24
> **ccalvinfowler@aol.com said:**
> Still looking in other places, but i would like to know if the alternate cd from xbuntu is also a live cd (600+mb) or just the smaller install image(400+mb)  I am downloading the larger one at this moment

Nope. AlternateCD is not a LIveCD.

Your wireless will not work out of the box.  However, there are plenty of (relatively) straightforward How-To's on the subject of Broadcom wifi.  Your ethernet cable will make installing easier, but you will hopefully be free within a few minutes.  Unfortunately, you will probably not get it to work from the LiveCD, so you will have to take the plunge and install.

This looks like the easiest:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
This is also popular (if BCM4318 )
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

Also, the wifi management in Xubuntu is a bit harder than Ubuntu (no easy WPA support) - I would recommend using Wicd:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
Go to the latest download (v1.3.1 is stable now), and double-click to install.
Then add */opt/wicd/tray.py* to Settings->Autostarted Applications and reboot.  The preferences are pretty self-explanatory.

Hope that helps to get you started.  I think Xubuntu7.04 is worth a bit of trouble to get it working.

---

### Post by ccalvinfowler@aol.com on 2007-07-24
Thank you to everyone that gave me assistance.  I am currently using my laptop - wirelessly - as I type this Post.  I am extremely pleased with the Xubuntu 7.04.  I am also currently installing Counter-strike using WINE, and so far it is working beautifully.  I am trying to play DVDs and I am kinda lost. So, if anyone can tell me where to get a media player that will play DVDs (encrypted) it would greatly appreciated.  The initial media player i have is GXINE.

 

Thanks Again and in Advance,

---

### Post by ccalvinfowler@aol.com on 2007-07-24
Also, i am trying to install the Nvidia pkg, but it says that it needs to be run from root.  HOW DO I COPY THE FILE TO THE ROOT.

---

### Post by stchman on 2007-07-24
> **ccalvinfowler@aol.com said:**
> First off let me list specs of laptop

Compaq Presario R3120US

AMD Athlon XP PRocessor 3000+
797 MHZ
512 MB RAM
Nvidia GeForce 4 420 go 32m video card
Agere systems Ac'97 Modem
Broadcom 54g MaxPerformance 802.11g Wireless adapter
Realtex RTL 8139 Family PCI Fast Ethernet NIC
TI PCI-1620 Card Bus Controller w/ultramedia (x2) PCMCIA Adapter
SoundMax Integrated Digital Audio Card
and USB Controller 


Now, I previously nstalled Red Hat and had a real b***c of a time trying to figure out how to get the wireless network card to work.  Everything else seemed to work, but i really couldn't tell. I spent 6 months trying to figure it out and i couldn't.  So here I am again.  Since my laptop is my only connection to the internet, i need to know what i am doing before i try this again.  I am going to use xubuntu 7.04.

Also, in case you are wondering why i don't just use the Realtek adapter w/cable, the answer is simple.  It is a laptop. I would like to be anywhere in my house and go online.

I am not trying to sound like a smart-a**, I just want to make everythiing clear.  I have read a lot of posts here and i notice that a lot of questions are asked before the problem even gets answered.  I am jsut trying to answer as many questions as i can so that i can get as much help as i can.


Thanks in advance.

First off with a 3000+ XP processor you can run Ubuntu no problem.  Everything else looks OK, but you might want to replace that Broadcom with an Intel 3945 or Atheros 5005EG card.

You may need to find a driver for that media reader, but try the Live CD and see if it is recognized.

---

### Post by ccalvinfowler@aol.com on 2007-07-25
i figured it out

A. type 'sudo su' in the command prompt
     this will ask you for root password
     after entering password it will auto put you n root folder
B. now copy nvidia package from desktop to root drectory.
     ichanged directory to Desktop first.  'cd Desktop'  make sure you capitalize the D.
     then i just copied the nvidia package to /root.
     but when i run the program i keep getting the error that xserver is running. 
     when i type 'exit xserver' the command box exits

---

### Post by Spartan.II.117 on 2007-07-25
it's only reading the first part of that comand, what you need to do is exit all programs but the terminal and type:```
 sudo telinit 1
``` this will put you in single user mode (root console) and from there you can run the nvidia installer, once you're done type ```
sudo telinit 2
```

---

### Post by ugm6hr on 2007-07-25
> **ccalvinfowler@aol.com said:**
> I am trying to play DVDs and I am kinda lost. So, if anyone can tell me where to get a media player that will play DVDs (encrypted) it would greatly appreciated.

I got rid of Gxine in favour of VLC (from Synaptic) - although I haven't tried playing DVDs.  I have heard that VLC offers excellent support for most formats without extra codecs being required.

But these references might help:
[https://help.ubuntu.com/xubuntu/desktopguide/C/multimedia.html](https://help.ubuntu.com/xubuntu/desktopguide/C/multimedia.html)
[http://www.medibuntu.org/index.php](http://www.medibuntu.org/index.php)

---

