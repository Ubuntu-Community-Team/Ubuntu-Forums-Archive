---
title: "Lenovo ThinkaPad SL510 and Ubuntu-reviwe, opinions, tipps..."
date: 2010-04-23
forum: Hardware
---

### Post by vickoxy on 2010-04-23
Hi,
i want to buy ThinkPad SL510 ([http://geizhals.at/a501658.html](http://geizhals.at/a501658.html)), but i am not sure if Ubuntu would work on it properly. So, if anyone has Ubuntu running on this machine i would be thankful for little suggestion. Maybe if someone can describe how much noise produces ThinkPad...

And yes, i will probably buy ThinkPad with Free Dos 2000 (if it is important regarding to Ubuntu Installation)

Hardware Spec:

Lenovo **Thinkpad SL510**
&#8226; Core 2 Duo T6570 2x 2.10GHz
&#8226; 2048MB &#8226; 250GB &#8226; DVD+/-RW DL
&#8226; Intel GMA X4500HD (IGP) max.384MB shared memory
&#8226; 4x USB 2.0/Gb LAN/WLAN 802.11abgn/Bluetooth/eSATA
&#8226; HDMI
&#8226; ExpressCard/54 Slot
&#8226; 7in1 Card Reader
&#8226; Webcam (2.0 Megapixel)
&#8226; 15.6" WXGA non-glare LED TFT (1366x768)

---

### Post by vickoxy on 2010-04-25
Bump

---

### Post by vickoxy on 2010-04-28
No one here uses this thinkpad?

Just asking...:KS

---

### Post by vickoxy on 2010-05-01
Just bump. It would interest me if all hardware is recognized...

---

### Post by visual_decoy on 2010-05-01
have you tried the thinkwiki site?

[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

specifically, [http://www.thinkwiki.org/wiki/Category:T510](http://www.thinkwiki.org/wiki/Category:T510) where it says 

> Linux Installation
As of 2010-04-03 the following problems exist with the T510 under Linux:
No support for display brightness controls when using binary video driver
To enable brightness control in X, append 'Option "RegistryDwords" "EnableBrightnessControl=1"' to the Device-Section of xorg.conf, orginal source: [http://www.nvnews.net/vbulletin/showthread.php?p=2204839#post2204839](http://www.nvnews.net/vbulletin/showthread.php?p=2204839#post2204839). This may result in a high-pitched whine after lowering the brightness within X. ALso, brightness is not lowered and raised in the same increments (on Archlinux).
System can only resume from suspend once - acpi related kernel crash occurs on resume (but system continues to operate), next resume shows BIOS screen and hangs - [https://bugzilla.kernel.org/show_bug.cgi?id=15407](https://bugzilla.kernel.org/show_bug.cgi?id=15407)
Suspend to RAM and Hibernate( suspend to disk ) works very well under Fedora 13 BETA (kernel 2.6.33), using both the proprietary Nvidia driver and the open source Nouveau driver.
Lenovo will solve this resume issue in a BIOS update expected near the end of April. [https://bugs.launchpad.net/bugs/532374](https://bugs.launchpad.net/bugs/532374)

I use 9.10 on a t400. The only major issues for me are lack of support for integrated graphics and problems with suspend/hibernate.

Sorry if you knew all this already (i.e. you already own a thinkpad and wanted something more specific)

---

### Post by visual_decoy on 2010-05-01
just saw the other thread you started. your specs are quite different from mine. and i guess it's hard for you to test using a live cd when you haven't bought the laptop yet :)

---

### Post by tgalati4 on 2010-05-02
Sounds like you might need the newer kernel (2.6.33) and Lucid ships with 2.6.32.  If suspend doesn't work right, then the laptop becomes a real pain to use.  Many fixes to suspend come in the form of kernel updates.  So, it's possible that it works better with Fedora 13 Beta (using 2.6.33).  

So, either get an older thinkpad or use Fedora 13 beta until Ubuntu catches up in 6 months or so.

Or load the newer kernel with Lucid and pray that you don't have too much breakage.

The noise is common for thinkpads.  Some are worse than others.  The high-pitched whine is the power inverter for the backlight.  It's similar to a wall dimmer that makes noise when the lights are dimmed.

---

### Post by vickoxy on 2010-05-02
> **visual_decoy said:**
> have you tried the thinkwiki site?

[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

specifically, [http://www.thinkwiki.org/wiki/Category:T510](http://www.thinkwiki.org/wiki/Category:T510) where it says 



I use 9.10 on a t400. The only major issues for me are lack of support for integrated graphics and problems with suspend/hibernate.

Sorry if you knew all this already (i.e. you already own a thinkpad and wanted something more specific)


Hi,
thanks for answer-i didn´´t know for this site. Still, you are reffering to T500 and i am to buy **SL510**: [http://www.thinkwiki.org/wiki/Category:SL510](http://www.thinkwiki.org/wiki/Category:SL510)
 
But i do not see there any notice regarding Linux Installation. Submenus are just describing hardware components.

Or i am wrong?

And, no, i still didn´t buy this notebook. So, i plan to buy it whitout OS (or with free dos)-so, if there is some BIOS update, can i install it from bios or from some other OS?

---

### Post by visual_decoy on 2010-05-03
The Thinkwiki site doesn't have exactly what you're looking for because both the SL500 and Ubuntu 10.04 are new.

Your best option is to go to forums such as [http://forum.thinkpads.com/](http://forum.thinkpads.com/) or [http://forums.lenovo.com/](http://forums.lenovo.com/)

Both of these sites have Linux discussion pages. Hopefully, they will have users who have experience with ubuntu/linux on an SL510.

---

### Post by vickoxy on 2010-05-03
Thanks for answers-but today i was at one laptop store and saw again SL510-it is really beautiful computer. In that price segment i saw nothing better (430 EUR). And there was exactly the cheapest model wit win 7 on it-it is really quiet. I put my ears to vent and was able to hear HDD spinning, but no fan. Of course there was background noise-but if it would be so quiet, i would buy it.

Another thing bothering me now is that some people on thinkpad-forum.de are suggesting me to buy second hand thinkpad t60-and they are really cheap/about 300 EUR (there is one big minus for me-saw no webcam on them...)

So, i know i am borring, but if someone can give me more advices....

As i said, i like SL510, and newer used thinkpad before. And even like its keyboard more then my chiclet apple keyboard...

---

### Post by adoomer on 2010-05-05
I use karmic on SL500 (without any other OS) - it's working good and it's very quiet also.

The only problem for now is setting special buttons - majority of Fn+... combinations are working good (like brightness controls, sleep, print screen, etc.), but I don't have enough patience to configure ThinkVantage button, zoom, mute, volume controls.

According to thinkwiki it is possible. After all I really don't feel bad without using these.
I tried lucid livecd (Beta 2, RC and final version) and it's looking good, so I'm going to upgrade to lucid today.

---

### Post by adoomer on 2010-05-05
Just after upgrade - everything except ThinkVantage button and zoom (Fn+Space) works out of the box! In fact I didn't expect, that these would work without proper software, so I'm satisfied ;-).

---

### Post by vickoxy on 2010-05-13
Thanks for replies. I bought Sl510 few days ago. As main computer i have untill now MacBook White (5.2-i think). So i am going to write some impressions. 

The build quality is for so cheap noteook very good ( i know that some ThinkPad users will say that SL510 is not a real ThinkPad-and if you compare in shop some T/X series with SL, you will notice the difference. But, if you compare it to another manufacturers in this price area, you will find few notebooks that are comparable to this SL510...
So, the plastic looks just fine, it is not so prone to finger prints as other/and MacBook White/ notebooks. That is because the plastic is matt.

The keyboard is also very good to my opinion. Nice typing feeling-precise and stable.

Ubuntu 10.04 works out of the box. I installed 64bit version. Of course i am no power user, and there are surely some things that maybe are not working (as thinkvantage option), but that, what i need, works very smooth. Ubuntu 10.04 64bit works on this configuration very, very fast. I have much more pleasure to work in Ubuntu on this Laptop, as in MacOS on MacBook. OpenOffice, Firefox/Chrome... are behaving much more stable and faster. Another thing that i found good - that is Display. Resolution is only 1366x768, but the dsiplay is non glare/matt, so it is much more usable as on other (even on MacBooks) Laptops. Another big plus with this display is its brightness-it is brighter than - again on my MacBook - and it is really much more pleasant to work on it.

Another big surprise for me are speakers. They are actually much better than on my MacBook, and watching movies/videos is also very nice experience.
This also goes for dvd player/driver. It is not a fancy slot-in, but it works very silently. 

The only thing that bothers me for now-is cooling fan. Actually it works almost constantly at 1. (i think) speed - although, now when i am typing i can hear only hdd spinning. But it works most of the time. I am very sensible to noise, but, fortunately, the sound of this cooling fan has low frequency, and there are no many oscillation in speed (yesterday i had 100% CPU installing win xp in virtual box, and it always worked at speed 1-more than 1 hour). 
On the other side, the laptop is always very cool-maximum, with 100% CPU Load and multiple programs opened - i had 53 Celsius). 
I read that in windows there is possible to adjust fan speed so that the laptop is almost unhearable. Unfortunately acpi_thinkpad module is not working in Ubuntu/LInux, so there is for now no efficient method to control the cooling fan in linux (i opened one thread here regarding to this problem, so if anyone want to help, please: [http://ubuntuforums.org/showthread.php?t=1478820](http://ubuntuforums.org/showthread.php?t=1478820)).    So, i will tolerate this behavior, because i am very pleased with all other stuff/performance.

So to conclude. I don´t want to say that MacBook is bad computer (it is actually very good computer), but this is only one i can compare myself, i just get feeling that i am getting much more from this SL510 at 50% of the price (and of course with Linux on it) than with Apple MacBook. Also, the performance of the Linux is much better than that of the MacOS. Of course, there are plenty of other programs that works only on Apple (and Windows-therefore, i need to have one Windows virtual machine on my computers), but for every day home using (Office Apps, Internet, Movies/DVD) Linux on SL510 is for me the best solution i had for now on Lapops (once i had the MacBook Pro. Nice display, performance-but its fan nose was horrible...).

Hoping just that Linux community will grow to stable and programmer attractive user group. Because, lots of thinks that i use with linux are apps made from only one person, or some small team, and it is (i presume) very hard to maintain and work as voluntary under such conditions...

---

### Post by Blümchen Blau on 2010-05-29
I read your thread too late ...
I have Lucid (32 bit) installed since Alpha2. Never had any problems with fan speed! The SL510 is nicely silent and the fan speeds up very seldom.

Working on the lap I recognise, that the harddisk is becoming quite hot after a while.

The rest is working nicely (some Fn+.. do not work - but that's no issue at all).

BIOS-Updates can be made via the iso-images that are provided by Lenovo. But watch out! BIOS versions from 1.31 upwards restrict you from buying batteries other than Lenovo! So I'll stick to 1.30 - works fine - no need to upgrade. I more likely keep my Ubuntu updated :P

---

### Post by vickoxy on 2010-05-29
Maybe i could try with 32bit? I don´t know how hotter can 64bit system  be...

---

### Post by beschu on 2010-12-26
> **adoomer said:**
> Just after upgrade - everything except ThinkVantage button and zoom (Fn+Space) works out of the box! In fact I didn't expect, that these would work without proper software, so I'm satisfied ;-).

And what about Bluetooth/Wireless button (Fn+F5)? It doesn't work for me.

---

