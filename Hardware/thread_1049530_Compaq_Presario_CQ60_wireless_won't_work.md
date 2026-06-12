---
title: "Compaq Presario CQ60 wireless won't work"
date: 2009-01-24
forum: Hardware
---

### Post by chepprey on 2009-01-24
I just bought a Presario CQ60, specifically because of its Intel graphics and Atheros wifi chips.

I boot up Ubuntu 8.10 from the live CD, but I can't get wifi to work.

This laptop (like many Compaqs, from what I'm reading) has this "wireless button" on it, next to the power button.  The button has a red light, meaning "wireless is off".

When using Vista, you can press this wifi button, and the light becomes blue.  Now wireless is on, and I can connect the laptop to the internet.

When using Ubuntu 8.10, the wifi button light remains red, no matter what.

Other postings have said that even though the light remains red, you can press the button, wait 5-10 seconds, and use the wireless connection thingy (nm applet) to connect.  This does not work for me.

I looked at System / Admin / Hardware Drivers.  Ubuntu reports that it is using the open-source Atheros drivers.  It reports that the driver is activated and currently in use.

How can I get this to work?  Thanks for your help.

---

### Post by dBuster on 2009-01-24
> **chepprey said:**
> I just bought a Presario CQ60, specifically because of its Intel graphics and Atheros wifi chips.

I boot up Ubuntu 8.10 from the live CD, but I can't get wifi to work.

This laptop (like many Compaqs, from what I'm reading) has this "wireless button" on it, next to the power button.  The button has a red light, meaning "wireless is off".

When using Vista, you can press this wifi button, and the light becomes blue.  Now wireless is on, and I can connect the laptop to the internet.

When using Ubuntu 8.10, the wifi button light remains red, no matter what.

Other postings have said that even though the light remains red, you can press the button, wait 5-10 seconds, and use the wireless connection thingy (nm applet) to connect.  This does not work for me.

I looked at System / Admin / Hardware Drivers.  Ubuntu reports that it is using the open-source Atheros drivers.  It reports that the driver is activated and currently in use.

How can I get this to work?  Thanks for your help.

I am running 9.04 alpha 3 since I could not get intrepid 64 to run or hardy for that matter.  When it comes up with the wireless is working you need to configure for your wireless network and then all I did was restart the same cq60 laptop.

Now my wifi indicator light is still red/orange, but I am using the wifi as it is on.  I am not having any problems and actually for an alpha this is one stable alpha!  

I take it that you must be using the 32 bit intrepid?  Otherwise you would have had errors booting into the 64bit version.....

Some have reported on their HP counterpart to a similar cq60 model that they have been able to get the blue light to work, but I am not going to mess with it.  If you are having problems check out this link with atheros install script to follow.  Ensure you read the entire post and then install.

[http://ubuntuforums.org/showthread.php?t=798485]("http://ubuntuforums.org/showthread.php?t=798485")

---

### Post by bubba_169 on 2009-02-23
It wont work because the drivers that support your wireless chip properly are not present by default in ubuntu intrepid. You can install them from the ubuntu CD however as they are in a package called linux-backports-modules found in CDROM/pool/main/l

These drivers are present in 9.04

Hope this clears things up :D

---

### Post by ebug on 2009-05-05
Try

[http://ubuntuforums.org/showthread.php?p=7214055](http://ubuntuforums.org/showthread.php?p=7214055)

---

### Post by dBuster on 2009-05-05
Interesting, I tried the pushing of the button like that one post mentioned and it did nothing to my system.  The light is still orange/red....  Could be because the only way my system seems to work is with the madwifi that it loads.  Okay it is the ATH5K driver but that is what the wadwifi drops in.

I do also have a non functioning touchpad button, the one that supposedly turns it off, it doesn't which isn't a bad thing for me...

---

### Post by Estelion on 2009-05-11
Hello,

I installed 9.04 @my Q60 laptop and wireless seemed to work fine. I tried the "recommended" Madwifi driver and now I can't connect neither via wireless nor via ethernet... Is there any way to restore default wireless driver? :(

Thanks in advance...

---

### Post by SilkSmooth on 2011-02-12
I have a Compaq Presario Cq60-224NR.  I had to end up replacing the internal Atheros WiFi Card with an Intel Pro Wireless 3945abg which I bought on Amazon.com.  I also bought a brand new hard drive on Amazon.com and did a fresh install of Ubuntu 10.10.  I don't use Wifi Radar. I use Wicd Network Manager.
To install, follow these commands:

sudo apt-get install wicd-gtk

Reboot.

sudo apt-get remove network-manager

Wait for it to do its thing, then enter the command:

sudo /etc/init.d/wicd restart

Reboot - when computer is rebooting, press the wireless button once,
for sometimes it will not turn on when the computer is completely on.
[B]
[/B]To launch **Wicd Network Manager**, refer to **Applications** >> **Internet**

I hope this helps.

---

### Post by dBuster on 2011-02-13
> **SilkSmooth said:**
> I have a Compaq Presario Cq60-224NR.  I had to end up replacing the internal Atheros WiFi Card with an Intel Pro Wireless 3945abg which I bought on Amazon.com.  


So you were able to buy a replacement internal wifi card?!  Oh my!  I have been looking for one that is compatible with the Presario CQ60 as I have the CQ60-215dx and would like to update my internal to a wireless N card...  If that is even possible.

For now I am using a usb adapter to get my N speeds.

---

### Post by marcopolo1981 on 2011-03-02
I have a CQ60-114em, and similar problems. Only it is not unique to linux. When I start my laptop, even with all versions of windows, I have to turn the wifi off and back on again for it to turn blue and usable.
In linux, I can't get it to come on - no matter what I do. The only distro I am able to use at the moment is lubuntu 10.04. For some reason, I can press the button twice like I do in Windows, and I can then connect to my network.
I also bought a Intel Pro Wireless 3945abg to try and see if that solves the problem. But my laptop wouldn't even get past the BIOS which said that an unrecognised card was being used. To remove it and restart the laptop. I thought it was because my graphics is Nvidia.

I am inclined to think that this problem is a hardware fault rather than a OS problem. But I am well out of warranty. Does anybody have anything else worth trying?

---

### Post by dBuster on 2011-03-08
> **marcopolo1981 said:**
> I have a CQ60-114em, and similar problems. Only it is not unique to linux. When I start my laptop, even with all versions of windows, I have to turn the wifi off and back on again for it to turn blue and usable.
In linux, I can't get it to come on - no matter what I do. The only distro I am able to use at the moment is lubuntu 10.04. For some reason, I can press the button twice like I do in Windows, and I can then connect to my network.
I also bought a Intel Pro Wireless 3945abg to try and see if that solves the problem. But my laptop wouldn't even get past the BIOS which said that an unrecognised card was being used. To remove it and restart the laptop. I thought it was because my graphics is Nvidia.

I am inclined to think that this problem is a hardware fault rather than a OS problem. But I am well out of warranty. Does anybody have anything else worth trying?


Have you tried to use the MADWIFI drivers?  Search out the forums and read up on this.  Up until my install of 10.04 I had to use the madwifi drivers with my cq60.  I believe it is something about the atheros chipset cards that are used in the model line.

As far as trying the intel card, good luck, Compaq hard coded into the bios only certain cards that are acceptable to use.  Getting that list is impossible.  They want you to go to them for help.

As far as trying a replacement, look at some of those USB wifi adapters out now a days.  The one I use for my wireless N is smaller than my blue tooth adapter!  It is hardly noticed.

---

### Post by ClaskoTheKnight on 2011-11-10
None of this has helped me, I am at a complete loss here.
When I click on the network icon there isn't even a wireless option.

I know this thread is over 2 years old, but I hope someone can help.

Ubuntu 11.10 
Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Umeaboy on 2011-11-27
Have you tried doing the following:

ifdown eth0

rmmod -f ath5k
rfkill unblock all
modprobe ath5k

That worked for me.

---

### Post by dBuster on 2011-12-04
With 10.04 my CQ60 wireless worked out of the box.  No need to do anything special.  Whereas prior to 10.04 I had all kinds of problems.  

Just a thought, install 10.04.0? what ever the recent LTS is, or even try the Live version first to make sure the wireless works out of the box, and then install and upgrade to the version you want to be running. 

Personally I am going to stick with 10.04.02 until the next LTS comes out in April...  I have checked out the Alpha of that upcoming LTS and it looks sweet!

---

