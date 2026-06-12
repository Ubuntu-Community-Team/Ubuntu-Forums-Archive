---
title: "Re: Installation Problems"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by tomeriker on 2008-12-24
Hello, I am currently trying to get 8.10 installed on my alienware laptop. I cant get past the Ubuntu with the scanning bar. I know my hardware is rather new but I was wondering if your version might have better hardware support?

---

### Post by Sef on 2008-12-25
What are your system specs?

---

### Post by namdung on 2008-12-25
Hardware specs? Any chance the CD ROM is dirty or media corrupted? Try Alternate CD.

Try boot using USB or other variants like Xubuntu or Kubuntu. 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Pumalite on 2008-12-25
Start from basics: do md5sum on the iso, burn at 4x or less. Do no use CD-RW. Check CD integrity before install. Clean the lens in your burner.

---

### Post by tomeriker on 2008-12-25
thanks for all the advice but I have tried all that. I have a PC and a laptop; the PC will run the live cd but the laptop won't. I will try to give as much info as I can.

laptop scecs:
Alienware M17
Intel P8400
1 gig ddr3 @ 1067 MHZ
dual ATI HD3870's with 512 ram each
bluetooth
seagate 160 HDD
NEC dvd sata optical drive
intel 5300 AGN wireless
windows vista sp1 installed

I can run Ubuntu 8.04 but no wireless will work. If I could get 8.04 to work I would be happy.

8.10 will get past the Ubuntu load screen with the scanning bar then a message window comes up saying Ubuntu comes with absolutely no warranty. It says some other stuff and at the bottom is this:

ubuntu@ubuntu : ~$


And that is as far as it goes.

When I use the same cd on my PC, I do not get that window.

Could I install 8.04 and somehow get my wireless working?

Is there a command I can type at the "ubuntu@ubuntu : ~$"  that will get me past that point??

Is there an option at start-up I can choose?

those are my questions and the facts about my system...

Thanks to all that help..:)

---

### Post by Pumalite on 2008-12-25
Have you tried the Alternate CD?

---

### Post by tomeriker on 2008-12-25
I am downloading the alternate cd as I type this.  Is there anything I should know, such as, is there anything I will need to type in. I do not know how to type code. I always fing a site that has the code and just copy/ paste it. Is there a guide somewhere?, or will it just be follow the promts and answer questions just like the other 8.10?

thanks for your help

---

### Post by Pumalite on 2008-12-25
[https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD](https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD)

---

### Post by tomeriker on 2008-12-26
Ok, here is where I'm at.

I decided to load 8.04 and try to compile a newer kernel to get wireless to work. Failed. I then thought I would do an online upgrade to 8.10, since 8.10 seems to have the support for my wireless card. The upgrade appeared to work, but upon reboot I get that same screen telling me there is no warranty with ubuntu, etc, etc. that finishes with a bash prompt. "ubuntu@ubuntu~$"

I don't understand why an older OS can load but 8.10 can't.
The 8.10 cd passes every test, The alternate cd loads so far then asks me for a second cd called "ubuntu8.10-intrepid ibex" then a date in perenthesis like (081225). I can't find such cd so I tried putting in the 8.10 desktop cd but failed.

I am really pulling my hair out..Can I just shut off the internal wireless and buy a freaking pcmcia wireless card?

If so which card "will" work with 8.04....

I really want to thank you all for your help...](*,)

---

### Post by Pumalite on 2008-12-26
Read some. Maybe you'll find your answer:

[http://ubuntuforums.org/showthread.php?t=618596&page=2](http://ubuntuforums.org/showthread.php?t=618596&page=2)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=618596&page=2](http://ubuntuforums.org/showthread.php?t=618596&page=2)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
[http://ubuntuforums.org/showthread.php?t=612065](http://ubuntuforums.org/showthread.php?t=612065)

---

### Post by JonNicholson on 2008-12-26
I can run the live version of Ubuntu 8.10 (64 bit) from the CD, but when I install it on my hard drive, my PC startup stops with the message "No operating system present".  How can the operating system be detected on the CD drive, but not on the hard drive?

---

### Post by tomeriker on 2008-12-28
What is the difference between a fairy tale and a truckers tale?? A fairy tale starts out "once upon a time"; a truckers tale start out " You ain't gonna believe this".

You aint gonna believe this. My wireless works in ubuntu 8.04 now...
I visited several websites and found out I needed to install firmware and the 5000 series driver. so I found the firmware and placed it where it said to, found the driver and followed the instructions to load it and all went well....no wireless...I did a reboot.. no go..I am also running wicd..

so I wen't to office max and got a USB belkin wireless G. I plugged it in and wham, wicd pops up and there is my wireless....BOTH OF THEM....so I unpugged the usb drive and rebooted and I now have my onboard wireless..I then found a site with instruction on how to turn off ipv6 because of a drop out problem... All is right in the world

I know this is a long post but this info might help someone else. If some one else can check and see if it works again then make a sticky, because I've seen many posts on the intel 5100/5300 not working in 8.04.. here's what I have found.

The newest kernel for 8.04 has the driver but not the firmware so all you need is the firmware..  [http://intellinuxwireless.org/?p=iwlwifi&n=Downloads](http://intellinuxwireless.org/?p=iwlwifi&n=Downloads)   

This is a good place for instructions:  [http://intellinuxwireless.org/tar.php?p=iwlwifi&a=iwlwifi-1.2.25.tgz&f=INSTALL](http://intellinuxwireless.org/tar.php?p=iwlwifi&a=iwlwifi-1.2.25.tgz&f=INSTALL)

these are the instructions that I used:  [http://linuxwireless.org/en/users/Download#Wheretodownload](http://linuxwireless.org/en/users/Download#Wheretodownload)

keep in mind i also installed wicd to controll the network and it didnt detect my wireless until I plugged in a usb wireless stick..

I hope this helps someone else...

---

### Post by tomeriker on 2008-12-28
To John:

I need some information about how you installed your OS.

Is it a dual boot ( windows and ubuntu on same computer)??

In the setup did you select Guided - use entire hard drive- or did you do a custom install where you select the options on where and how to install?

---

### Post by tomeriker on 2008-12-30
Ok, I just wanted to update on my wireless problem. I thought all was fine but for some reason it still kept dropping out.

So far I tried another fix and it seems to be working.

I have a belkin router and in the setup I have turned off "QOS".
I hope this finally fixes my problem. I will keep you posted.

---

