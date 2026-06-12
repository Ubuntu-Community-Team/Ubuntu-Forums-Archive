---
title: "Your experience with Ubuntu on laptops"
date: 2005-11-16
forum: Hardware &amp; Laptops
---

### Post by Paul Casey on 2005-11-16
I teach linux at http:[www.longmontfreeu.com](www.longmontfreeu.com) using Ubuntu. I'm looking for ideas for my class called 'Build your own computer'  What I'd like to do is have a class where we build laptops and install Ubuntu 5.10
The laptop pc will have wireless to connect to well-known wifi hotspots in town.

build options will be:  
1. buy used laptop and rebuild with Ubuntu
2. buy new laptop and reinstall with Ubuntu
3. buy whitebox laptop and install Ubuntu

Budget range $400 - up
Question is:  What is your pick for wireless laptop with Ubuntu?

---

### Post by firetux on 2005-11-16
I would look at laptops with wireless devices that are powered bij the ralink 2500 or RT2400 chipset. Look [here]("http://www.fsf.org/campaigns/hardware.html") they make recommendations for devices that work with open source drivers. 
Things like broadcom work too but there you have to use ndiswrapper in combination with the windows drivers, thats less elegant.

---

### Post by Paul Casey on 2005-11-16
good resource, thanks.

---

### Post by scflymedic on 2005-11-16
I've had a pretty good experience so far thanks (and MUCH Thanks)to all the folks on this website!  I have an emachines M6810, AMD64 3200+, 60gb HDD, 512mb RAM, ATI M9600 64mb, broadcom wireless.  I think it is great that you are teaching this to others...good luck!

---

### Post by unless on 2005-11-16
[QUOTE=firetux]
Things like broadcom work too but there you have to use ndiswrapper in combination with the windows drivers, thats less elegant.[/QUOTE]

Broadcom fixed LAN doesn't require ndiswrappers. I don't think their wi-fi requires ndiswrapper any more, either... Seems like I saw support for both Broadcom 802.11b and 802.11b/g in the kernel last time I was walking through menuconfig. (2.6.13, I think it was.)

---

### Post by Paul Casey on 2005-11-17
thanks,   that emachine m6810 is a nice looking computer.

---

### Post by cstudent on 2005-11-17
I just installed Breezy as dual boot with XP on my recently purchased Acer Aspire 3500. Everything worked right out of the box.

Specs

[http://us.acer.com/acerpanam/page9.do?dau34.oid=9721&UserCtxParam=0&GroupCtxParam=0&dctx1=25&CountryISOCtxParam=US&LanguageISOCtxParam=en&crc=2838502062](http://us.acer.com/acerpanam/page9.do?dau34.oid=9721&UserCtxParam=0&GroupCtxParam=0&dctx1=25&CountryISOCtxParam=US&LanguageISOCtxParam=en&crc=2838502062)


Bill

---

### Post by Donnut on 2005-11-17
I only have a laptop currently, and everything works MUCH better than it did with windows.  (Compaq Presario Pentium M with centrino)

---

### Post by sigma2805 on 2005-11-17
the only real setup i had to do was configure the laptop to use the broadcom bcmwl5 drivers. i used ndiswrapper for that. plus i also had to configure wpa_supplicant(allows you to connect to wpa protected hotspots)

i think setting up ndiswrapper is important to learn, at least until hardware manufacturers release linux drivers.....

---

### Post by matthew on 2005-11-17
For consideration in the whitebox option I have an AOpen 1557gls detailed on the wiki.

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsOthers]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsOthers")

and here

[http://solution.aopen.com.tw/products/nb/1557-G.htm]("http://solution.aopen.com.tw/products/nb/1557-G.htm")

and have been very pleased. A simple installation was not difficult and everything worked in a basic way right off the bat. There was a little work required to bump the video drivers up from the 2D ati driver to the 3D capable fglrx and to get wpa working for the 802.11g but neither was especially difficult under Breezy with the howtos here on the forums.

---

### Post by ThirdWorld on 2005-11-18
I am thinking in buying a laptop. I found the dell inspiron 2200 will cost me around $664 or $715 (with DVD rewritable) and it comes with a centrino 1.70Ghz /2mb cache procesor. Im thinking in buying the 256mb ram version and upgrade the ram later to 1Gb. Any of you have expirience with this laptop? I heard in other forums that the video performance is not great, but my question is if it would be enough to  make cool presentations with smooth animations or it will deliver a crappy performance? I dont use my computers to play any video games. Any advice about this particular laptop or something similary priced?

Thanks

---

### Post by aznboi on 2005-11-18
what are the specs? like video card specs and stuff like HD capactiy

---

### Post by desquer on 2005-11-18
As a newbie, I have Breezy running on an OLD Dell CpiA Pentium II 366 mhz machine. It dual boots with Win98 on a 10gb, 256 mb ram system. I have both Gnome and XFCE 4.2 running on it. I use a linksys 802.11g wireless pci card with the netwrapper driver from windows installed. It's a little slower than win98, I'm trying to speed it up.

I added Xmms for Internet radio streaming. Using Firefox, I have a cheap Internet terminal resurrected. All for free!

Dave

---

### Post by desquer on 2005-11-18
As a newbie, I have Breezy running on an OLD Dell CpiA laptop Pentium II 366 mhz machine. It dual boots with Win98 on a 10gb, 256 mb ram system. I have both Gnome and XFCE 4.2 running on it. I use a linksys 802.11g wireless pci card with the ndiswrapper driver from windows installed. It's a little slower than win98, I'm trying to speed it up.

I added Xmms for Internet radio streaming. Using Firefox, I have a cheap Internet terminal resurrected. All for free!

Dave

---

### Post by drakeoutlaw on 2005-11-19
Hi all, 

I just installed Ubuntu 5.10 Breezy on a brand new Sony Vaio FS630 Laptop. It was a flawless install. All hardware except S1 S2 hot buttons. ( I am looking for an elegant solution.). A few caveats: 

1. Breezy install will suggest resizing the existing Windows XP partition to 5.7GB. Give it at least 8 GB so windoze doesn't choke.

2. Sound will not seem to work at first. DO NOT GO CRAZY TRYING TO FIX IT! Simply right click the speaker applet in the top right hand corner, choose preferences and choose front (speakers). Now it will show that the speakers are simply muted. Just move the slider up after clicking the speaker icon.

3. There is an intermittent freezing  problem which i suspect is due to acpi.

This is by far the finest Linux install I've ever seen on any laptop .

---

### Post by Paul Casey on 2005-11-21
the AOpen notebook looks pretty good.  I've been lookin into the whitebox laptops and it looks like they are not so available thru suppliers as the whitebox or barebones desktops are.  Nice review of your system.  thanks.

---

### Post by Paul Casey on 2005-11-21
for your radio pleasure on xmms these 6 presets might be enjoyable

-----  [http://www.axelweston.com/radioStations.htm](http://www.axelweston.com/radioStations.htm)

---

### Post by Paul Casey on 2005-11-21
[QUOTE=aznboi]what are the specs? like video card specs and stuff like HD capactiy[/QUOTE]


good question... for video would want resolution greater than 1024x768 and would want it to play well on a projector for presentations.  for disk would want 40 gb disk min  and would want cd rw with dvd rom.  dvd rw with cd rw would be good .  for internet would want wireless connection working for use around town at the well known hotspots.

---

### Post by Paul Casey on 2005-11-21
[QUOTE=ThirdWorld]. . .  dell inspiron 2200 will cost me around $664 or $715 (with DVD rewritable) and it comes with a centrino 1.70Ghz /2mb cache procesor.  . . [/QUOTE]


that price sounds like the place to be.  I'm guessing this is new price.   for people in my 'learn to buiild your own pc' class [http://axelweston.com/theNewAxelwestonWebsite/training/MakeYourOwnComputerCoverPage.pdf](http://axelweston.com/theNewAxelwestonWebsite/training/MakeYourOwnComputerCoverPage.pdf)

that would be a great price.  thanks.  no personal experience with that one from dell.  maybe someone who has used it will chime in.

---

### Post by emmo on 2005-11-22
running ubuntu 5.10 on an Fujitsu Siemens, PIII 450 256mb rams. Everything worked out of the box. Ndiswrapper used for linksys 54 G pcmcia card, and works fine to. Its just a weebit slower as the XP that was installed before. Any tricks to speed things up?

---

### Post by Florian Hufsky on 2005-11-25
I successfully ran ubuntu 5.10 on a thinkpad t42 and a samsung x20 1730 out-of-the box.

There are some real PITA issues though:
Getting WPA encryption support working (you *will* need this if you want to connect to various hotspots in town) is *no* easy job. I was unable to do it for now (spent two days so far).
The default touchpad sensitivity is to for people used to mac/windows - changing is a PITA.
Batterie time? Forget it with the default settings. Haven't invested much time into that jet though (but let alone the fact that i need to invest ~a day to get it working speek for itself).

I guess WPA will be the biggest Problem. Have fun.

---

### Post by Bachstelze on 2005-11-25
On my Presario R3000, everything worked fine out-of-the-box except the winmodem (I got it working with kind help from [http://www.linmodems.org](http://www.linmodems.org)) and the Suspend/Hibernate which I never use.

---

### Post by grunion on 2005-11-27
I've an install on an older Gateway Solo 5300 that works flawlessly for everything I've thrown at it.  As memory serves, it's a Celeron 533 with 25MB of ram on a 6GB HD.  

So there IS life on older laptops to be had if you find a system you like there.

---

### Post by fezzik on 2005-11-30
My R3440US works great.  The only major set up was Ndiswrapper for built in WiFi.  My suggestion for the class since you teach Linux and building computers is to Build them using a WiFi Card you have to configure with Ndiswrapper.  It would give them more examples on how to use Linux.  Also it gives more experience with the Shell.  I know that when I used all that stuff and had to learn Ndiswrapper and all that it really helped get me used to getting into Terminal and finding my way around.  It really helped me understand everything better.  That would be my recommendation use a broadcom chip or something that needs Ndiswrapper to work.  It would be good for Linux Newbies that actually have an instructer to help.  It helped me.  Ubuntu was my first commitment to learning how to use Linux and I had to start from absolutely no idea what they meant by just type this command.  My question was where, how, what do I do next.  Now I know how to open Terminal and put commands in and all that.  So for the class I would suggest having a few things that you have to tweak or do the hard way so they see that even the hard way isn't that hard.  It kind of takes the intimidation factor out of learning Linux.  I know from experience that starting with no previous knowlege of Linux can be intimidating and you get really frustrated if you are just starting out cause these forums tend to assume some previous knowlege or experience with Linux.  Help them take the mystery and intimidation out of it and you may just win Linux converts for life.

---

### Post by KurtB on 2005-12-01
I installed Hoary Hedgehog a while ago on my DELL INSPIRON 5150.

It dual boots with Win XP. Only problem was my wifi Belkin54G PC Card, even with following all the steps I didn't manage to get my wifi connection up and running (my AP uses WEP64 bits enc). Sadly following different tutorials here, didn't help either :(

For the rest: ubuntu really looks to be a worthwile OS (but not yet useful to me without wifi...)

Now I recently received my Breezy copy, but didn't have the time to upgrade.

I also had some questions:

* How to upgrade my dualboot system when you have a Breezer copy and Hoary installed?
* Is ndiswrapper / wifi support better with Breezy?
* What are the odd that I FUBAR my GRUB, and so als lose my Win XP partition?
* How come that when I worked in ubuntu and afterwards reboot in XP, my fan starts blowing like nuts?

---

### Post by mandrakeghost on 2005-12-01
oh...i guess it's fine with my LG LM50. the only problem is the infrared port and mmc...i can't seem to work them out still...

---

### Post by arkangel on 2005-12-01
Well i am bussy to do a Howto install ubunto on dell c840,  my old laptop was a perfect candidate for linux ,I tried mandriva  everithing ok , but  then I heard  about ubunto in distrowatch , since I had nothing to loose I decide for ubunto ,  
the installation didnt come with a beatiful GUI ok ,  but then start working ,  so well that my old computer is my principal computer , I read about people hving troubles everywhere and with all distro ,  well how lucky I am !! anly because I have soem work in my new laptop  I havent install Ubunto on it yet ,  for those who havent decided yet for giving a linux (ubunto,etc )a chance do not hesitate, as every linux user U will have some problems , but  trust me , it is worth :)

---

### Post by Paul Casey on 2005-12-03
[QUOTE=fezzik] . . . . . My suggestion for the class since you teach Linux and building computers is to Build them using a WiFi Card you have to configure with Ndiswrapper.  It would give them more examples on how to use Linux. . . . .[/QUOTE]


Thanks for the suggestion.  nice write up of personal experience.

---

### Post by Paul Casey on 2005-12-03
[QUOTE=KurtB]. . . 
I also had some questions:

* How to upgrade my dualboot system when you have a Breezer copy and Hoary installed?
* Is ndiswrapper / wifi support better with Breezy?
* What are the odd that I FUBAR my GRUB, and so als lose my Win XP partition?
* How come that when I worked in ubuntu and afterwards reboot in XP, my fan starts blowing like nuts?[/QUOTE]


the install of Breezy on dual boot I would go in for Breezy install and at the disk  partitioning would just delete the partition where Hoary was and start new with Breezy.  (that's if you don't have lots of saved files)

When Grub loads (has been my experience) that it does pretty good job of id ing a windows partition and gives you a choice of how to edit it's boot menu.  I guess you can do something wrong though and then make a computer not bootable. Then I guess you boot from cd.

don't know about the fan or the ndiswrapper.

---

### Post by KurtB on 2005-12-04
Thx for the reply,

Meanwhile I've got my laptop working and both my Win XP and Ubuntu OS'es work fine (GRUB idd does his job :cool: )

I've noticed that the fan issue disappeared after the upgrade (in my case)...so it could have been something that was 'wrong' in Hoary and got fixed by Breezy :) 

Only thing left is my Wifi Belkin PC Card (yep, the dreaded Broadcom-chip *sigh* -> **F5D7011**, further looking around on the fora just got me more confused on which is the driver to use)

Both tried the *.inf files that came with the wifi-NIC CD-ROM (bcmwl5 & bcmwl5a), but now I get an "incorrect driver" with both when I list the ndiswrapper drivers. 

If I get this fixed, I really think that ubuntu is going worthwile testing/using...;)

EDIT: removed bcmwl5a.inf, reinstalled it...rebooted my PC...and all lights blinkin' on my wifi-NIC, just had to enter my WEP-key and it works!!

Let the testing begin! :):)

---

### Post by Mizzou_Engineer on 2005-12-04
I run a late-2002-vintage Gateway 600YG2 and it runs pretty well on Ubuntu. Wireless (Orinoco) works fine, Pentium 4-M CPU scaling does too. Hibernation does NOT work, I have filed a bug on it.

---

### Post by fezzik on 2005-12-04
Yeah I Have just found that the more stuff I have to tweak the better I understand the operating system and environment.  I now have scrolling working on my touchpad and I was told that that would be impossible. Still working on the finer settings of stuff just the stuff to make it work more for my personal preferences.  You know all the stuff you can't do with Windows.lol.;)

---

