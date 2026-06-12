---
title: "VAIO VGN S-360 (P) &quot;Fn&quot; keys not working"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by nimzo on 2005-05-17
How can I enable the "Fn" keys to increase/decrease brightness in Ubuntu Linux?

Details:

Laptop : Sony Vaio VGN S-360

OS: dual boot (Windows XP Pro NTFS) and Ubuntu Linux

All other hardware including sound, video, and Centrino wireless card were auto-detected and work wonderfully!

Ubuntu is Great

---

### Post by blinksilver on 2005-05-17
sorry i can't be of any  help, there is a package for sony laptops in the repo that you might try, but this is a very unique situation for me, as i am considering buying one of those laptops, if it is not to much trouble i have a couple questons.

first, have you tried standy and hibernate in ubuntu???

second have you gotten the ati drivers to work with standy or hiberante

third:with the ati drivers,  what is your glxgears score?

and finally are there any bugs other the one you mentioned above that you can tell me about??

sorry i could not help, thanks for any info, and for both of us i hope someone can help.

oh wait maybe i can. [http://tuxmobil.org/sony.html](http://tuxmobil.org/sony.html) at the bottom are a bunch stories from people getting the s150 s260 and 360 (all basically the same) working under various linux distros, maybe there is an answer there.

[http://www.eng.uwaterloo.ca/~demalea/](http://www.eng.uwaterloo.ca/~demalea/) is the best i could do

---

### Post by nimzo on 2005-05-17
***first, have you tried standy and hibernate in ubuntu???***
Standby and Hibernate worked without any problems to report.

***second have you gotten the ati drivers to work with standy or hiberante***

I assume that you are wondering if the lcd screen comes on correctly coming out of standby/hibernate... The laptop's screen and X-Windows works fine coming out of standby/hibernate.
[B]
*third:with the ati drivers, what is your glxgears score?*[/B]

I did not run glxgears yet; I'll send you the results once i do.

***and finally are there any bugs other the one you mentioned above that you can tell me about??***

I think that my Ubuntu Linux was one of cleanest and smoothest linux installations I tried. And it's only one CD !

The only things i found that do not function for me yet are: The Fn keys, and Sony's propriotery memory stick reader.

I am currently reinstalling the Ubuntu, not because of bugs; but because I did not set a mount point on my Fat32 partition (a shared download partition for both WinXP and Linux). I'm not fully savvy in Linux yet... so i opted out for the simple reinstall opposed to using the "mount" command....

---

### Post by nimzo on 2005-05-17
Here are my glxgears results for the vaio vgn s-s60:

nimzo@ubuntu:~$ glxgears
1008 frames in 5.0 seconds = 201.600 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1356 frames in 5.0 seconds = 271.200 FPS
1469 frames in 5.0 seconds = 293.800 FPS
1469 frames in 5.0 seconds = 293.800 FPS

Are those comparatively good results?

---

### Post by blinksilver on 2005-05-17
i am talking about the drivers on ati website... those drivers should get about  1200+

---

### Post by nimzo on 2005-05-19
FYI:

ATI does not offer drivers on their website for the ATI MOBILITY RADEON 9700. ATI reccomends the drivers be obtained from the motherboard manufacturer's website. - I used Sony's website to download all drivers.

Cheers :-P

---

### Post by blinksilver on 2005-05-20
[http://www2.ati.com/drivers/linux/linux_8.12.10.html](http://www2.ati.com/drivers/linux/linux_8.12.10.html) <- link to ati release notes for the linux drivers, note the section on the mobiltiy stuff, its say 9600, the 9600 and the 9700 are the same chip at different clock speeds

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)  and link to third party guy who converted ati's rpm in to deb file for debian based distros as well as how to install them, good luck. 

OH and if you try play a game like tux racer (or even a screen saver on really fast laptop) and realize that it wont run, then you will understand that the standard drivers will just not do....

---

### Post by Corey on 2005-07-06
I have a slightly older s260 (with an ati mobility 9200)
Ubuntu did wonders configureing everything! Hibernate and Frequency scaling worked out of the box. Wifi required no work on my part either. X correctly came configured at 1200x800 widescreen. ATI drivers are actually working good too (I love this machine but I almost didn't get it because it had an ati chip instead of nvidia, but I couldn't find anything comperable with a non integrated memory nvidia chip)

some quick glxgears scores:
3319 frames in 5.0 seconds = 663.800 FPS
3900 frames in 5.0 seconds = 780.000 FPS
4007 frames in 5.0 seconds = 801.400 FPS
4013 frames in 5.0 seconds = 802.600 FPS
3887 frames in 5.0 seconds = 777.400 FPS
3705 frames in 5.0 seconds = 741.000 FPS
(note these are with the ubuntu ati drivers, I didn't need to download anything extra from ati)

Only 2 things that don't work are the modem (there is a hsfmodem linux driver but it is proprietary and costs something like 20 bucks) I believe you can get a demo version that is limited to 14.4 but even that one is a bit of a pain to setup so I didn't bother. Also the function keys do not work at all. I think this is fixable with a little work though. I'll post any results I have here.

---

