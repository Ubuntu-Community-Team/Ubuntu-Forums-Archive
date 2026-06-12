---
title: "Sound and wireless on Westinghouse laptop"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by nardis_Miles1 on 2006-12-06
I have just installed Edgy on the Westinghouse laptop and several pieces are not working. The ATI sound card is not recognized although it is supposed to by AC 97 compatible. The wifi card is also not recognized. Finally the ATI Express card is recognized and X comes up under the standard ati driver. However, when I try to install the ATI proprietery driver I receive a substitution error.](*,) 

Has anyone had success with any of these three items?

Art Edwards

---

### Post by jhaitas on 2006-12-06
Westinghouse laptop??

---

### Post by nardis_Miles1 on 2006-12-06
Yes a  Westinghouse Laptop! It is on sale on Tiger Direct for 399.00 after rebate and it's a pretty nice box. I attach the exact error 

./ati-installer.sh: 176: Syntax error: Bad substitution

This comes after reassurances that the the archive is intact.

I have since started to hack the scripts and it appears to be actual bad scripting code. 

Art Edwards

---

### Post by tominsf on 2006-12-08
I also just got this laptop, and think it's a great machine, and want to assure you that since I have the same problems (wifi and sound - haven't tried the ATI thing) there's nothing wrong with your box.  Since I'm pretty much a newbie, I haven't got much to add except my enthusiastic encouragement in solving this problem.  Keep us posted, please.

---

### Post by tominsf on 2006-12-08
I will add, however, that the wifi card shows up as wlan0 and wmaster0 under system->administration->networking, and that if I insert the scanning module [sudo -s, then modprobe wlan_scan_sta], I can then bring up the wireless module [ifconfig wlan0 up] and scan [iwlist wlan0 scan]. This gets me actual scan results; I see access points.  But I just can't associate with them, even if I explicitly do iwconfig wlan0 ap "theSSIDgoeshere", or iwconfig wlan0 ap any.

I got the info on doing the scanning stuff from madwifi.org/wiki/UserDocs/FirstTimeHowTo

---

### Post by tominsf on 2006-12-09
Just ran Feisty Fawn (alpha version) off the disk in the hope that the problems got fixed.  No luck, though.

---

### Post by nardis_Miles1 on 2006-12-28
I just got the wireless working using ndiswrapper. The card responds using the rt73.inf windows driver. Here are my specific steps

1. Install a 2.6.19 kernel from kernel.org, including the sources.
a. I attach the .config file I used successfully to build the kernel on the Westinghouse. Crucial was the inclusion of the module for the SiS SATA driver. This means that the ATI SATA driver actually uses the SiS SATA driver.
b. I used the kernel HOWTO at

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

so that I could build a .deb package, which allowed me to load the kernel on a second laptop.

2. Install the newest ndiswrapper package from sourceforge. Follow the directions at

[http://ndiswrapper.sourceforge.net/m...on#Downloading](http://ndiswrapper.sourceforge.net/m...on#Downloading)
and
[http://ndiswrapper.sourceforge.net/m...le_and_install](http://ndiswrapper.sourceforge.net/m...le_and_install)

3. For the specific windows driver go to

[http://www.msi.com.tw/program/suppor...UID=626&kind=8](http://www.msi.com.tw/program/suppor...UID=626&kind=8)
and download the file for the 32-bit windows systems. The name of the downloaded file is:

MSI_RT6x_RT7x_1.0.0.0302.exe

execute this on a windows XP machine. It will create an MIS folder under Program Files. Several levels below this directory you will find a WINXP directory. Copy this to the laptop.

4. From inside the WINXP directory on the laptop, issue the command:

sudo ndiswrapper -i rt73.inf

If you have been successful, the command

ndisswrapper -l

will return

rt73: driver installed
device (0DB0:6877) present

issue the command

sudo depmod -a

followed by

sudo modprobe ndiswrapper

and your wireless card should come up.

Finally, add the line

ndiswrapper

to the file

/etc/modules

To automatically load the wifi driver at bootup


HTH

---

### Post by computerguydd on 2007-02-12
I am having sound issues as well. I got the Wifi to work. but it doesnt seem what distro i use or kernel 2.6.19 still can not get the sound to work. is there any one out there that has got it to work?

---

### Post by rlcmcallen on 2007-04-25
I decided to join so I could share the good news. I have one of the Westinghouse laptops you're talking about, and tonight I booted it with a 7.04 Ubuntu Desktop CD (Final release, not beta).

Lo and behold, the SOUND WORKS!  I guess I'll do a real install and see if the wireless will work of if I have to go the NDIS wrapper route.

I'd love to hear from any others who try an install with the latest 7.04 disc.

By the way, has anyone gotten the built in telephone modem to work?

---

### Post by tominsf on 2007-04-27
Yes, I had been playing with the alpha and beta releases of Feisty, and noticed that sound started working sometime in March or so.  Unfortunately, wifi doesn't really work; I can see access points but I can't get to them, even if they're unencrypted.

If anyone has this problem and comes up with a workaround, please let us know what you did!

I guess I should try nardis_Miles1's ndiswrapper solution next; I haven't got to it yet.  If anyone has tried this with Feisty and can confirm that it works, let us know.

---

### Post by nardis_Miles1 on 2007-04-30
In case your interested, feisty brings up the sound automatically on this laptop. Unfortunately, the wireless seems just a little broken. At this moment, I cannot use the recipe on this list to bring it up. It sees the network, it simply will not connect.

---

### Post by tominsf on 2007-05-01
nardis_Miles1 -

Do you mean that with Feisty, you can no longer make wireless work even with ndiswrapper, as you could with Edgy?

---

### Post by Fxymmnance on 2007-06-02
My husband bought his westinghouse off ebay, and i cannot get the sound going. I hooked his laptop to my desktop threw the roughter, and was able to get the wireless working. Where did you get your disk you used to get the sound to working? Sounds like i could use one.

---

### Post by crimsun on 2007-06-03
> **Fxymmnance said:**
> My husband bought his westinghouse off ebay, and i cannot get the sound going. I hooked his laptop to my desktop threw the roughter, and was able to get the wireless working. Where did you get your disk you used to get the sound to working? Sounds like i could use one.

Please read [http://www.linux-sound.info/alsa/index.php?task=support](http://www.linux-sound.info/alsa/index.php?task=support) and tell me the URL of the paste generated by the alsa-info.sh script linked from that page.

---

### Post by MartezNJ on 2007-06-15
I have this same laptop, and I just installed Feisty. Sound works, but wireless will not. I've tried a couple of tutorials, and was going to try the ndiswrapper technique, but I can't navigate to it on the MSI page anymore. Nardis, do you still have the rt73.inf file? Or were you saying that the ndiswrapper technique doesn't work in Feisty?

If anyone has had any luck or can recommend some things to try, I'd really appreciate it. I love Ubuntu, but a laptop without wireless kind of defeats the purpose.

---

### Post by moslofu on 2007-10-06
I'm sorry to resurrect this thread and I know I'm a little off topic but I need help fixing my Westinghouse laptop. I was wondering if someone with the laptop could tell me if the fan turns on immediately the comp is turned on or if it turns on minutes later. Thx

---

### Post by tominsf on 2007-10-09
Definitely the fan comes on after things warm up (after a few minutes), and cycles on and off.  You can also hear some liquid gurgling from time to time - there's a heat pipe affair inside that is doubtless the source of this.

So nobody's managed to get the wireless working?

---

### Post by tominsf on 2007-10-26
For the record, wireless now works under Gutsy - no setup, no problems.

Sound of course works, although I'm having a problem with RealPlayer, which hiccups regularly, at least with streams.  I need to look into this.

---

