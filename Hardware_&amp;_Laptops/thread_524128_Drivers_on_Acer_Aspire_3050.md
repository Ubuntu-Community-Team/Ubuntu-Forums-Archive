---
title: "Drivers on Acer Aspire 3050"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by patrickalexson on 2007-08-12
Ok first off, im very very very familiar with Windows as probably most people here are. Im trying out ubuntu and im real happy with it. Open source stuff is the way to go.

Now here is my problem, which probably has already been resolved in about a thousand other posts.

Ive got the Acer Aspire 3050

AMD Sempron 3400
1.5Gigs of DDR2 5300
ATI Radeon Xpress 1100
Atheros Wireless Card
Dont know what the sound card is, but the sound works so it doesnt matter.

NOW... I need to figure out, first of all, how to install a driver. I can find the terminal window, and I know you have to enter in some sort of command.

Also ive opened up the restricted drivers window, to see what it was, and it lists:

ATI Accelerated Graphics Driver Driver
Atheros Hardware Access Layer (HAL)

Atheros is checked and in use, however, the ATI driver is NOT. If I try to enable it, the screen will refresh and nothing happens. Seems like it wont let me enable it.

Someone explain how to install drivers. Specifically the ATI and Atheros Wireless ones.

Thanks.

---

### Post by marshak on 2007-08-13
I am having the same problem. I am completely new to linux and just bought an asipre 3050-1092 (best buy canada exclusive). the wifi card is an atheros ar5007eg. this laptop has the most annoying wifi power switch. its a spring loaded slide (so it is always in the same position) but you do not know if it is on or off because it only lights up when it has network activity. I'm not too concerned about the ATI stuff but I NEED my wifi working!

---

### Post by ugm6hr on 2007-08-13
@marshak:
You might be out of luck with that card - I don't think it is supported by madwifi:
[http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5007EG)

@patrickalexson:
If Atheros is checked and in use - then it's already installed.  As for whether it works - have a look at the compatibility list above to see if your card is supported
As for ATI - from memory, I needed to restart after ticking the boxes (and it gave me some warnings).

---

### Post by jordman2001 on 2007-08-22
how can you even install ubuntu i have the exact same laptop and All my distros but freebsd wont work,

i would love to install ubuntu with this laptop but nothing boots (its set to boot but at splash screen it freezes with a thumb nail loaded, how do you get past that?!

---

### Post by dsquared2 on 2007-09-07
I too have the a 3050-1092 am just starting to figure out which distro to use. I have a suggestion regarding the WiFi adapter - I don't know if it will work (or how you go about setting it up) but I see that NDISwrapper works with the Atheros AR5007EG catd #11 on the following[ page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/")

---

### Post by marshak on 2007-09-08
tried that, doesn't work on this laptop.

---

### Post by shaun_paul on 2008-01-28
you can install the latest distro of ubuntu on an acer aspire 3050 but the front speakers

 dont work and cant seem to put card in monitor mode yet all though there is a patch i just

 dont understand linux enough yet but the backtrack 3 beta live cd works and even the 

bcm43xx drivers for wifi msg me for more info on putting ur card in monitor mode in bt3 its

 easy any info on driver for my acer aspire 3050 for sound, mouse (so i can use my middle

 mouse scroll button).....any help in these areas would help thanks guys:popcorn:

---

### Post by shaun_paul on 2008-01-28
Hey Again i just got the card in monitor mode but i have to restart linux to get my card back so i can surf the web..code is as follows :

for me its:

Airmon-ng Start eth1 <channel> optional

---

### Post by shaun_paul on 2008-01-28
i fugured it out just open a terminal and type this and unmute ur front speakers

#alsamixer

---

### Post by hk7589 on 2008-02-03
I have an acer with all of the same hardware

for the wireless card look up madwifi 1679, your card is supported
for sound look up ALSA they make sound drivers for your laptop
for your ATI display check the box click ok, log out and log back in. should work

---

