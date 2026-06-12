---
title: "PCMCIA pc card causes total freeze crash"
date: 2009-03-02
forum: Hardware
---

### Post by bobalice on 2009-03-02
Hi.
My issue is that whenever I insert a pcmcia pc card into the slot with the system running, the system freezes up and nothing gets it back other than powering off and back on.
If the card is already inserted during boot time, the system will freeze during boot and again powering off is the only way to restore it.
This issue is occuring with a clean installation out of the box, no changes made to any config files at all..
Recently, there have been a few methods circulating on how to use mobile broadband cards with Linux that are typically supported only with windows. Sprint released a guide for this on their website, but I have not been able to try it because of the freezing issue. The card I use is a Pantech PX-500 pcmcia pc card, with service from Sprint. I have not tried any other pcmcia cards to see if the results are different because I do not have any besides this one.

I am using Linux Mint Release 6 (felicia), which I believe uses Ibex 8.10 as the base.
Kernel Linux 2.6.27-7-generic
gnome 2.24.1

the notebook is an acer aspire 5672. intel core duo t2300 @ 1.66ghz.
I suspect that the issue is due to a configuration problem.. some sort of conflict with usb or serial drivers maybe.. I don't really know.
Any suggestions or help would be much appreciated. I am somewhat new with linux so if any other info, logs, etc would be helpful just let me know how to fetch them and i'll gladly post it.
Thanks.

---

### Post by khelben1979 on 2009-03-02
Maybe [this]("http://www.sagrad.com/info/EVDO/") can help you out?

---

### Post by bobalice on 2009-03-03
I have already read that page and others regarding setting up the card to connect; that is not the issue. The issue is that the entire system completely freezes as soon as I insert the card. I am going to try another PCMCIA card to see if it causes the same problem later today and will post back. Thanks anyway

---

### Post by tent405 on 2009-07-29
I have the same problem. No idea what to do yet.
The laptop also freezes when I try to sudo lsusb -v 
It's a Curitel Pantech PX-500 from sprint. 
The output of lsusb is attached.
The major,minor device corresponding is 189,641
I'm stumped but working on it
update: no freeze with lsusb -v in runlevel 1
i'll be working on this one all night prolly

---

### Post by tent405 on 2009-07-29
:P add the following word to your grub boot stanza: irqpoll
worked for me, no more freeze up!

---

### Post by piton on 2009-08-24
Hi, 
at the moment I have the same problem TENT405 and BOBALIANCE, had before,
I ask to TENT how he solved the problem, I've not understand what
" 		:razz: add the following word to your grub boot stanza: irqpoll" means.

Hoping that your solutions works also for me. Bye

---

### Post by tent405 on 2010-03-18
If you're using grub 1.x (pre ubuntu 9.10) , then to add this option to the kernel at bootup open the file /boot/grub/menu.lst and edit it as root.
this is the file that controls your boot-time options, which OS starts, etc.
find a line that starts with 
```
# defoptions=
```
After # defoptions= is a space separated list of options for the kernel, usually defaults, which suppresses diagnostic messages, are
```
#defoptions=quiet splash
#defoptions=quiet splash irqpoll
```
Make sure you leave the # in there. Add irqpoll to the end of this line.
then run ```
sudo update-grub
```.

---

