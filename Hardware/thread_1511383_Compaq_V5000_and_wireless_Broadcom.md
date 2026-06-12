---
title: "Compaq V5000 and wireless Broadcom"
date: 2010-06-16
forum: Hardware
---

### Post by mikelspencr on 2010-06-16
hey guys, im working with another thread in the newbie forum, but this thread is for my fiancee's laptop.. i installed lucid over her windows and completely removed that "virus" lol. now we have a small problem. her Broadcom card (Broadcom BCM4318 [AirFprce One 54g] 802.11g Wireless LAN controller {rev.02} ) isn't turning on (ie. the LED switch won't turn on period) i have run iwconfig and i have these notes: 

lo: no wireless extensions
eth0: same
wlan0: IEEE 802.11bg ESSID: off/any Mode: Managed Access Point: Not-Associated Tx-Power=0 dBm Retry long limit:7 RTS thr:off Fragment thr:off Power Management:off

i have tried all threads i can find, including [http://ubuntuforums.org/showthread.php?t=578544](http://ubuntuforums.org/showthread.php?t=578544) and [http://ubuntuforums.org/showthread.php?t=438903&highlight=compaq+presario+v5000](http://ubuntuforums.org/showthread.php?t=438903&highlight=compaq+presario+v5000)

if there is anything else i can do, please let me know. im hoping to have her laptop up and running within a few days maximum.

---

### Post by mikelspencr on 2010-06-19
bump to ask for help..

thanks

---

### Post by gunfyter on 2010-06-19
Mike 

I have the same broadcom card as you....

I believe the problem is that the drivers you need have to be downloaded....  (which is hard if you have no internet connection)

You need a wired connection or a usb wireless dongle to download the proprietry drivers that do not come with Ubuntu.

Connect to the internet and then 
[INDENT] copied from [http://www.pcmech.com/article/windows-to-ubuntu-transition-guide/3/](http://www.pcmech.com/article/windows-to-ubuntu-transition-guide/3/)

The first thing we need to do is configure Synaptic to display every program available in the Ubuntu “repositories”. The repositories are simply locations which store information on which programs are available and where to download them. To enable all the repositories do this:


[LIST=1]
[*]Open Synaptic (System > Administration > Synaptic Package Manager)
[*]Enter your password (remember, installations require root access)
[*]Select Settings > Repositories
[*]Click Add
[*]For each option under Repository combo box, select all the check boxes
*Note: This will enable certain closed source and sometimes non-free applications. Be sure you understand any EULA’s for packages these may apply to (such as MP3 codecs).*
[*]Click Ok
[*]In the Software Sources listing, make sure every box is checked, except for the CD Sources (should be the one at the top of the list)
[*]Click Ok
[*]Close and reopen Synaptic
[*]Refresh the packages via Edit > Reload Package Information
[/LIST]
[/INDENT]   

THEN...

SYSTEM>ADMINISTRATION>HARDWARE DRIVERS

click on the B43 driver to have it automatically installed.

---

### Post by mikelspencr on 2010-06-25
got it running a few days ago.. havent had a chance to post... thanks for that!

---

