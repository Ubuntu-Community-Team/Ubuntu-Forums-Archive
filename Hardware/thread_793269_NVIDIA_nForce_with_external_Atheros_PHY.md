---
title: "NVIDIA nForce with external Atheros PHY"
date: 2008-05-13
forum: Hardware
---

### Post by Harag on 2008-05-13
ASUS M3N78-EMH HDMI mother board with onbaord lan problem.

After one or two hitches with install and the sata drives I got 8.04 installed, but I have not been able to get the onboard lan card to work...yes i did try every combination od setting up the network ...dchp...fixed ip etc that I could find and/or understand.

I have been reading articles found on google for the last two days and my only real hope has been these links

[http://ubuntuforums.org/showthread.php?t=392453](http://ubuntuforums.org/showthread.php?t=392453)
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346)

but allas it was not to be because the compile comes up with tons of errors...and yes I did change the version number to the correct version...and yes i did install build-essential and gcc (both report latest version). 

In the same breath I must admit that I am a very raw newby at linux/ubuntu. Been running Ubuntu 7.10 and 8.4 in a VM on XP box for the last two months and now accuired a brand new box just to install Ubuntu on.

Anybody got any suggestions(or rather recipes or step for step instructions)?

I am about to go out and buy an alternative network card or wireless-usb dongle or something just so I can get on with my life.

---

### Post by twinkletoes on 2008-05-31
Hi,

Can you let me know what you did to get the sata drives working? I have this same motherboard and am not having any luck getting ubuntu 8.04 to recognise the SATA drives.

Thanks

---

### Post by Harag on 2008-06-02
Hi

I set some switch using F6 on installation but could not rember what it was for the life of me...

Fortunately some googling got it for me !

all_generic_ide

Here follows the original post that got me going ...

[http://ubuntuforums.org/showthread.php?t=782281](http://ubuntuforums.org/showthread.php?t=782281)

After installation grub still uses all_generic_ide ...i checked my menu.lst to make sure.

Hope it helps.

---

### Post by twinkletoes on 2008-06-02
Thanks, I ended up finding that switch method out, but used a different switch to get ubuntu 8.0.4 to recognise my sata drives (pci=nomsi from here => [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199573)).

I also had issues with my network card. The system would recognise it as eth0 and would request an IP address from the DHCP server, which the  DHCP would offer it, but it would not take it!

I ended up having to do the following to get my Atheros PHY network card working with DHCP..

Comment out link-local line in /etc/networks (Add a # at the beginning of the line)
Disable Roaming Mode in the network-admin app (I accessed this from the top right hand corner of the screen beside the time). In network-admin app, set mode to dhcp.

Check /etc/network/interfaces to make sure that the following two lines are there:

auto eth0
iface eth0 inet dhcp

Then restart your networking:

/etc/init.d/networking restart

This should give you a few lines of info of your network card trying (and hopefully getting) to get an IP address from the DHCP server. 

Hope this helps you getting your network card working.

---

### Post by tobiz on 2008-08-06
Has anyone got the onboard LAN on the M3N78-EMH M/B working with Ubuntu 8.04?  Mine seems to think it's active but has a DHCP deivered IP address of 169.254.7.107 whereas it should be in the 192.168 range.  Any idea where it got the 169.254.7.107 address from?

---

### Post by dbutler1986 on 2008-08-07
No, but I have the same problem - the exact same IP is showing up, even. I'm pretty angry, actually; I spent a lot of money putting this PC together only to find that Ubuntu doesn't work with the motherboard. I never had any problem with recognizing the SATA drives, though, that everyone else seems to be having.

---

### Post by twinkletoes on 2008-08-08
Hi dbutler1986 and tobiz,

Did you read my post regarding what I had to do to get my Atheros PHY network card working with DHCP??

The Atheros PHY network card is what the M3N78-EMH has on board...

tobiz, a 169.254.x.x ip address is a self assigned IP address and is indicative of not being able to gain a DHCP lease from a DHCP server. This is the problem I had before I went through the steps indicated in my previous post. 

Try my steps and see, you never know!!

---

### Post by tobiz on 2008-08-11
Hi Butler1986 & Twinkletoes

Ok, this may be a bit off thread so need to consider how to progress.

Butler1986
I now have my M3N78 m/b up and running on Ubuntu 8.04, Samsung Spinpoint SATA drives and the Nvida graphics working, only took 5 days to work it out! I can let you know how I did it but perhaps need to go to, or start another thread.

Twinkletoes
Thanks for the info re IP address default.  Strange that it is the result of not contacting the DHCP server ok since the other 'vanilla' NCI in the box connected to the same DHCP server gets its IP address etc ok.  I will try your Atheros fixes.

Tobiz

---

