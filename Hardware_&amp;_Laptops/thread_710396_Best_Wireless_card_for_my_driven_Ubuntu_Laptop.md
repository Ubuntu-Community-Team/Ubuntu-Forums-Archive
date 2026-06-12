---
title: "Best Wireless card for my driven Ubuntu Laptop"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by Troy Mac on 2008-02-28
Can anyone suggest a wireless USB or PCMIA card for my Compaq n610 laptop.  it has a WL200 internally which I cannot get to work with Fedora, Redhat or SuSe.  A friend and Linux Guru told me to try Ubuntu because it is the best and easiest for hardware setup.

So if Ubuntu does not see my wireless which one would be the best for me to buy.

---

### Post by TopDog on 2008-02-28
I use the [Gigabyte GN-WMKG]("http://www.gigabyte.com.tw/Products/Communication/Products_Spec.aspx?ProductID=956&ProductName=GN-WMKG"). It works out of the box with all Linux distro's I've tried. 

That it's really cheap is just an added bonus :)

---

### Post by myddewji13 on 2008-02-28
if it cant see your wireless ...y dont u fix it using ndiswrapper...thats free...

---

### Post by Troy Mac on 2008-02-28
Thanks TopDog,  Hard to find I must have searched 5 or 6 top web sites for purchase only one had it.  but I did find some post with people that had issues with this card.  

Does anyone else have any suggestions???

---

### Post by Troy Mac on 2008-02-28
Thanks myddew I did give that a few minutes of testing work but I figured if I can buy a card that works out of the box that would be better.  I have heard that there are performance issues with card drivers that use the wrapper.   I have to first find the ndis driver for the card which is not easy.  Compaq WL200 Multi port. anyone have the driver?

---

### Post by myddewji13 on 2008-02-28
[http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?lc=en&cc=us&softwareitem=ob-27036-1](http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?lc=en&cc=us&softwareitem=ob-27036-1)

download....extract + install w. ndiswrapper

---

### Post by MiataMuc on 2008-02-28
I put an Intel 2200 in my Compaq Evo N610, and it always worked like charm (I had to get rid of the internal modem card). This Compaq is not beeing locked for non-Compaq cards, so there should be no problem. I took the antenna from another laptop and just fiddled it to the batterie compartment, which gave (and gives, but it isn't my main computer any more) me a good signal strength; with the Comapq's antenna (only one) in the battery compartment I see 11 networks, with my new laptop I can see 15 networks sitting in the living room.

Flo

P.S. sorry, I didn't made clear that the card I described is an internal card.

---

### Post by Yellow Pasque on 2008-02-28
FWIW, I noticed no difference in download speed between my wired PCIe Realtek 8169 LAN and my wireless Realtek 8180 using ndiswrapper with WinXP-64 drivers. Both gave me a good sustained 500KB/s downloads.

---

### Post by Troy Mac on 2008-02-28
Thanks for all the replies, I may try again to get the driver for the WL200 and try the ndiswrapper although I have read elsewhere that people did not have good luck with this card.

---

### Post by myddewji13 on 2008-02-28
well then good luck to you...and dont give up...i was in your situation with a broadcom card...ended up using a usb adapter and then 3 weeks later...got it working... lol...heres my post on how...although i dont noe if it will help much

[http://ubuntuforums.org/showthread.php?t=709447](http://ubuntuforums.org/showthread.php?t=709447)

---

### Post by Troy Mac on 2008-02-29
Myddew,  I installed ubuntu and have been fighting with ndiswrapper.  Not sure how much you know about this program but I follow the directions to the tee and when trying to run ndiswrapper -l or any command I get not installed or command not found I even used ./ndiswrapper.  I then installed it using sudo apt-get install ndiswrapper-common and that didn't work either. 

When I do a make I get 2 errors first make[1]:***[loadndisdriver] Error 1 and the 2nd make *** [all] Error2 what gives? is there a trick to doing this?  I am using sudo and I am thinking these errors are my problems has anyone seen these errors before.

---

### Post by Yellow Pasque on 2008-02-29
Why doesn't sudo apt-get install ndiswrapper-common work? Did you also install ndiswrapper-utils-1.9 ?

For your second question, are you trying to build ndiswrapper from source there?

---

### Post by Troy Mac on 2008-03-01
Not sure why ndiswrapper-common didn't work but in any event I found another post while searching for an answer that suggested the install of build-essentials.  I installed that and finally I could install ndiswrapper with no errors.  Now that I have it installed Network manager does not see the hardware I pushed the button to turn on the wifi and it lite once but I was too quick on pressing it and it shut off now it will not come on again.  it seem to light up after I ran sudo modprobe ndiswrapper.  I am going to unistall and start from the beginning maybe that will work?

---

