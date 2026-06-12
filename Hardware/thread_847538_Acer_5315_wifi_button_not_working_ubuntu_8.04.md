---
title: "Acer 5315 wifi button not working ubuntu 8.04"
date: 2008-07-02
forum: Hardware
---

### Post by yostane on 2008-07-02
hello,
 I installed ubuntu hardy on acer 5315, the proprietary atheros wifi driver is present but the button on the laptop that turns on/off the wifi does not work. And by default wifi is off.
 Is there a way to replace the button's job so I can turn wifi on.
thanks

---

### Post by Xenia on 2008-09-02
Hi. I too would be very interested in the answer to this question... though also having difficulties getting wired internet to go, on an Acer 5315?

Thanks, Xen

---

### Post by windozehater on 2008-09-02
Give this a try:
you need to have a working ethernet

Open a terminal and do these commands, each in order and in turn.
Code:

sudo apt-get install build-essential linux-headers-generic
wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/

The file name will change as the current build changes. Just watch what the file is that is extracted.
Code:

make
sudo make install
sudo modprobe ath_pci
sudo reboot

---

### Post by Xenia on 2008-09-02
Thanks for that - I'll give it a try in the morning... though, since I can't even get the Ethernet going, I'll try by DLing the tar.gz in Windows to the shared partition I have set up, and wgetting from there... *hopefully* that will work.

Or, is it a prerequisite for this to work, to have ethernet working? I've not been able to get that going at all either, with Ubuntu.

---

### Post by windozehater on 2008-09-02
the Ethernet has always worked on my aspire, but i think as long as you have the file accessible you should be o.k. i also had success with a wifi pci card (linksys WPC54G), and i also swapped out the internal card for the broadcom that was in my wifes compaq, before i came opon that script. the only problem i have had is the wifi light has only worked with the broadcom card, although the switch is fine.

---

### Post by Circus-Killer on 2008-09-02
> **windozehater said:**
> Give this a try:
you need to have a working ethernet

Open a terminal and do these commands, each in order and in turn.
Code:

sudo apt-get install build-essential linux-headers-generic
wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/

The file name will change as the current build changes. Just watch what the file is that is extracted.
Code:

make
sudo make install
sudo modprobe ath_pci
sudo reboot

for an in-depth howto, see [HERE]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html").

---

### Post by Xenia on 2008-09-02
So, I'm trying this process, and when I tried:

sudo apt-get install build-essential

it told me (translated from Hungarian):
the build-essential package is unreachable, but another one refers to it. The requested package is thus: missing, outdated or reachable only through a different stream.
E: there is no identifiable (markable?) variant of the build-essential package for this install.

So now what?

---

### Post by Xenia on 2008-09-02
Further question: will 'wget' work with something not online but saved onto disk locally? If not, then the listed process won't work, because I can't get even the wired 'net connection going...

---

### Post by Xenia on 2008-09-15
Peeking in again... wondering if anyone might give an answer to the previous question? Nevermind just wireless, I can't even get the wired connection working...

Xen

---

