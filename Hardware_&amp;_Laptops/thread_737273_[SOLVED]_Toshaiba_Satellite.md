---
title: "[SOLVED] Toshaiba Satellite"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by maustin2 on 2008-03-27
I will soon purchase a Toshaiba Satellite laptop with AMD Turion 64 X2
technology. It will be utilized for navigational purposes. I plan to install
Ubuntu, Wine and Seaclear on it for this purpose.

I am just trying to get some advance feel for what might lay ahead for me.
What distribution of Ubuntu would be suitable for this project? 32 or 64 bit?
My experience so for with Ubuntu has been enlightening, as I suspect this will be.

Thanks for any assist

---

### Post by CorDawg on 2008-03-27
I just bought a Toshiba Satellite a month ago, its the A210 with AMD X2, It came with Realtek RTL8187B Wireless (Very hard to get it working, had to use ndiswrapper with Windows Drivers) and for the life of me i could not get the Sound card to work, Definitely check the specs of the laptop your going to get to make sure it does have Linux compatible hardware inside.

---

### Post by mentalcic on 2008-03-27
I bought Toshiba Satellite A210-19J a week a go. 
No problems with sound...it works in KDE with default drivers.
I have problems with making Atheros WiFi card to work properly on KUbuntu 7.10 (Gutsy).
lspci shows: 
Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

The same is listed in H/W specs on Toshiba website and many others for this model.
I searched through the forum and learned that sometimes lspci would show incorrect hardware details (?!).

Question No.1: Is there any other way (beside lspci) to find out which is the correct version of your hardware in a laptop without opening it? :) 

Taking in consideration results from lspci I tried couple of instructions posted to make WiFi work but with no success - the one with using widnows drivers through K Menu > System > Windows Wireless Drivers actually wont start the application (core dumped - !?)

Question No.2: I would appreciate any help or instructions on how to set up this baby to run properly.

Thanks in advance!

PS> I have rescently started using Linux and am very new with this (pure noob) and I'm willing to learn - pelase help.

---

### Post by CorDawg on 2008-03-27
My A210 has a sticker on the bottom that tells me what wireless is in it, and the sticker attached to the AMD/ATI sticker has Realtek Wireless on it as well, My A210 is model A210-FS3 (I Think thats the model Number) but its on the bottom of the laptop as well

As for the sound, I couldn't get it to work in Ubuntu at all, but i just installed Kubuntu and the sound worked just fine right after the installation/reboot.

Maybe the other version(s) I tried it with were 64 bit or early betas or something, but i can confirm that the sound works fine with Kubuntu 8.04 beta

There are different modified versions of the wireless rtl8187B driver (aka this page is where you can download them - [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/) )

I don't feel like getting a wire out to hook up to the laptop, so I'm downloading everything now and im about to boot back into Kubuntu and get it working, I will post again when im connected in Linux

On a side note, the RTL8187B gets detected as a USB even though it is internal (lsusb - 0bda:8197 Realtek Semiconductor Corp)


After typing this up I did realize you said yours has the Atheros in it (Wish mine did *cough* aircrack-ng *cough*) so if I were to post on this thread again about the wireless it really wouldn't benefit your situation at all.

Good Luck :)

---

### Post by latanerp on 2008-03-29
Just bought Toshiba Satellite A210 ... New distro of Ubuntu 64 the sound works "right out of the box" which saved me from having to repair it as I had to last year when I bought my desktop with Realtek sound card.  But wireless is not working with the Toshiba lap top, did you have any luck getting yours to work ?

---

### Post by Resurrection on 2008-03-29
With regard to the original post, go with the 32 bit version.  I run unbuntu on a desktop that has a 64x2 processor in it, and there is no need to run the 64 bit version especially if you are just planning on running 32 bit applications.  You have a better chance of getting wine and seaclear to work properly on the 32 bit version.

I have installed Ubuntu on an older (4 yrs old) Toshiba Satelite laptop recently, and I could not get the Live CD versions to run properly.  I used the Alternate Install CD, and everything went fine, including automatically recognizing my wireless connection, and other hardware without any issues.  But keep in my that this was an older machine, not sure how well it will work on a newer one.

Here is another thread about Seaclear on Ubuntu:
[http://ubuntuforums.org/showthread.php?t=271201]("http://ubuntuforums.org/showthread.php?t=271201")

---

### Post by latanerp on 2008-03-29
I have spent a few hours trying to get the Realtek wireless working.  No luck.  Might give up and buy cheap but trusty D-Link PCMCIA or USB card.  Not sure how much more time I want to spend trying to save myself $50.

---

### Post by Tom--d on 2008-03-29
> **latanerp said:**
> I have spent a few hours trying to get the Realtek wireless working.  No luck.  Might give up and buy cheap but trusty D-Link PCMCIA or USB card.  Not sure how much more time I want to spend trying to save myself $50.

[Look here to fix the wireless problem]("http://ubuntuforums.org/showthread.php?t=708605")

I have the RTL8187B and it works perfect now :D
No problems after that.

---

### Post by latanerp on 2008-03-30
UPDATE--THIS worked for me
[http://ubuntuforums.org/archive/index.php/t-707447.html](http://ubuntuforums.org/archive/index.php/t-707447.html)
Scroll to bottom, post by Kachline

No signal strength indication shown but wireless connects to my network which is good enough for me.

[I can't remember if I already said this, but as for sound, in the new (beta) version of Ubuntu 8.04 my sound card worked right away. (Though it not work without tweaking in Edgy.)]

---

