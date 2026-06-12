---
title: "fool needs help"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by thecountofpumpkinhill on 2009-09-24
Hi,
    i am new to forums and linux so i apologise if i sound a bit dim! I have just installed kubuntu 9.04 on my toshiba satalite a205-s5804, and am having a couple of problems....
      1,  I cannot get the wifi to work ? 
      2, i cant play dvds or avi files?
      3,  i have a usb modem from a mobile phone company here in honduras (by the        name  TIGO ) it is 3g capable but has a very slow dial up connection locally. How can i use this ( with wine? )
      Thankyou in advance to anyone who can give me any advice or help
                                                                                                        steve

---

### Post by mikewhatever on 2009-09-25
Hi, and welcome to the forums. You need to provide a bit more info about your hardware to get help. Go to Applications->Accessories->Terminal and post the outputs of the following commands:

sudo lshw -C network

ifconfig

DVD, avi and other proprietary formats are not free to redistribute, and therefor aren't included by default. The included media player should offer to download and install codecs for mostly everything, but you need to be connected for it to succeed. Dvd playback is a bit trickier, read here for more [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).

Hope someone will help you with that 3g modem soon enough.

---

