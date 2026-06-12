---
title: "Help! Installing ubuntu server broke my Proliant DL380 G2"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by johnzbesko on 2007-08-05
Well, maybe it wasn't ubuntu that broke it...

I have a Proliant DL380 G2 with 2x18 GB in the first bay and two 36GB drives in the second. I was successful in partitioning the drives and installing the latest server version of ubuntu. I then removed the PCI carriage and added an inexpensive Realtek gigabit ethernet card. That's when my trouble started.

The drives are no longer recognized, even by the Smart Start boot diagnostic CD. This is in spite of the fact that all of the lights for the drives initially come on when the machine is turned on, but then go dark, except for the two 18GB drives. Removing the Realtek card makes no difference and I've dis/re-connected several cables, the PCI carriage, etc. in hopes that perhaps something was loose.

I'm at wits-end and any thoughts/ideas are appreciated. BTW, ubuntu did recognize the Realtek card.

---

### Post by rpradeep on 2007-08-05
Did you try with your bios settings..?
Is ubuntu booting but hard disks unrecognised or ubuntu not booting at all..?

---

### Post by johnzbesko on 2007-08-05
Yes, I tried different BIOS settings. I updated the firmware. I tried moving the disks to different bays. The same two disks that do light up green, do so in any bay. The ones that go dark, stay dark. I also reset the ROM by playing with the S-switches on the motherboard, like another forum post mentioned. Nothing helps.

---

### Post by johnzbesko on 2007-08-08
Fixed! Apparently, I had a loose cable. Now I can get on with configuring the machine as a server. ;-)

---

### Post by tenikiwon on 2007-08-15
I'm new to Ubuntu and just purchased a DL380 G5 and ran the install.  during the install it said something about not NIC but a firewire device that "could" be your NIC.  I chose to continue with it and/or install it.

Anyway, No NIC after install.  Just wondering if the built in dual NC373i Gigibit NICs are compatible or if I need to install a regular NIC.

Thanks,

---

### Post by creedog on 2007-08-15
What exactly are you doing with a DL380 G5? That is not exactly a cheap box.


If I recall correctly I had some issues installing RHEL 4 on a Dl385 due to driver issues, had no issues with RHEL 5.

---

### Post by tenikiwon on 2007-08-15
Plan is to run Zimbra Mail Server.

---

### Post by tenikiwon on 2007-08-16
For what it's worth Fedora Core 5 found and installed the drivers w/o any problems.

---

### Post by eisublime on 2007-08-20
I'm having the same problem with 2 DL360 G5s - were you able to find a working driver?

---

### Post by ipguru99 on 2007-11-27
Have a stack of DL3[8,6]0's here myself.  I load the 'dummy' driver during the install.   It takes a bit because the machine thinks the internet is 'down'.  After the install is complete, I edit the /etc/network/interfaces file and change 'dummy0' to 'eth0' and it works just fine.  I think it is loading the bcm43xx driver.. if I recall correctly.  

I figured all this out with the very first one.. by loading up Zimbra.. glad to hear someone else is using it!

---

