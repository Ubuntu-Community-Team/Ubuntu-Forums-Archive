---
title: "Broadcom Wireless Problem With HP Pavilion dv2710us"
date: 2008-04-26
forum: Hardware
---

### Post by rodrigo.prestes on 2008-04-26
Hello Guys, 

I’m trying to use the Broadcom wireless card of my laptop HP Pavilion dv2710us. 

After install Ubuntu 8.04, ndiswrapper and cabextract, I have downloaded Windows Vista wireless card driver (see below) and I follow some commands that I have read in another thread, the command was:

cabextract  sp37745.exe
sudo ndiswrapper –i bcmwl6.inf
sudo ndiswrapper –l (it’s showing that my driver is installed and the device is present)
sudo modeprobe ndiswrapper
sudo ndiswrapper –m
reboot it

Unfortunately my wireless is not working properly, the light of wireless still orange and I can’t access my wireless network. 

I believe that I missed some step, so, have anybody solve this wireless issue in that configuration/situation?

Thank you
Rodrigo

HP dv2710us drivers:
 [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=us&lang=&product=3646848&dlc=#](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=us&lang=&product=3646848&dlc=#)

---

### Post by piratesmack on 2008-04-26
My brother was also having this problem with the same wireless card.

It's the only thing keeping him from switching to Linux.

---

### Post by rodrigo.prestes on 2008-04-26
Yep, This is a pain. If I solve this problem, I can switch to Linux.

Let's try to solve it ...

Rodrigo

---

### Post by piratesmack on 2008-04-26
anyone?

---

### Post by rodrigo.prestes on 2008-04-26
I was reading some threads about this issue. I have tested some solutions without success. I don't know what happened with this specific card/laptop.

If you solve this issue, please help us!

---

### Post by KillerMRK on 2008-04-26
Oh joy, this is the card my laptop has.  There goes the Linux practicality. I'll have to wait until I have access to a wired connection...

---

### Post by piratesmack on 2008-04-26
I hear what a lot of people do is just buy a Linux-compatible USB wireless adapter and use it instead of their wireless card

Can anyone recommend a good usb wireless adapter for Linux? Preferably something that will work right out of the box

---

### Post by rodrigo.prestes on 2008-04-26
I found a thread that can be useful. I'll test it and after I can post if this works properly for me: 

[http://ubuntuforums.org/archive/index.php/t-650729.html](http://ubuntuforums.org/archive/index.php/t-650729.html)

Rodrigo

---

### Post by Ayuthia on 2008-04-26
> **rodrigo.prestes said:**
> Hello Guys, 

I’m trying to use the Broadcom wireless card of my laptop HP Pavilion dv2710us. 

After install Ubuntu 8.04, ndiswrapper and cabextract, I have downloaded Windows Vista wireless card driver (see below) and I follow some commands that I have read in another thread, the command was:

cabextract  sp37745.exe
sudo ndiswrapper –i bcmwl6.inf
sudo ndiswrapper –l (it’s showing that my driver is installed and the device is present)
sudo modeprobe ndiswrapper
sudo ndiswrapper –m
reboot it

Unfortunately my wireless is not working properly, the light of wireless still orange and I can’t access my wireless network. 

I believe that I missed some step, so, have anybody solve this wireless issue in that configuration/situation?

Thank you
Rodrigo

HP dv2710us drivers:
 [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=us&lang=&product=3646848&dlc=#](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=us&lang=&product=3646848&dlc=#)

Right now, you are not able to use Vista drivers with NDISwrapper.  You might want to try using the driver for XP instead.

---

### Post by Nathan.Flow on 2008-04-26
> **rodrigo.prestes said:**
> Hello Guys, 

I’m trying to use the Broadcom wireless card of my laptop HP Pavilion dv2710us. 

After install Ubuntu 8.04, ndiswrapper and cabextract, I have downloaded Windows Vista wireless card driver (see below) and I follow some commands that I have read in another thread, the command was:

cabextract  sp37745.exe
sudo ndiswrapper –i bcmwl6.inf
sudo ndiswrapper –l (it’s showing that my driver is installed and the device is present)
sudo modeprobe ndiswrapper
sudo ndiswrapper –m
reboot it

Unfortunately my wireless is not working properly, the light of wireless still orange and I can’t access my wireless network. 

I believe that I missed some step, so, have anybody solve this wireless issue in that configuration/situation?

Thank you
Rodrigo

HP dv2710us drivers:
 [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=us&lang=&product=3646848&dlc=#](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&cc=us&lang=&product=3646848&dlc=#)


Hey. I have a dv2710us and have working wireless here's what you do..
first install all ndiswrapper-common, and ndiswrapper-utill

Then you need to uninstall what ever driver you currently using...

then get the DELL driver.. :lolflag: it will work here's the url
[ftp://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](ftp://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe)

unzip the folder, you can use wine to extract the files... after that navigate to the drivers directory and 
sudo ndiswrapper -i bcmwl5.inf
if all go's well you will get a message form ndiswrapper -l like

bcmwl5 : driver installed
        device (14E4:4315) present

then edit /etc/modules and type ndiswrapper in their so the module will load on boot....

let me know

Maby some one can help me with my dvd problem... I'm using 64bit harty. and it tell's me when ever I try to play a dvd that I don't have enough permissions. or their's no disk, or their's nothing on the disk. but it will play some previews???:confused:

---

### Post by rodrigo.prestes on 2008-04-26
Hey Guys, 

I solved the problem with Broadcom wireless card used in HP dv2710us and Ubuntu 8.04 Linux.

I have followed the messages of this thread: [http://ubuntuforums.org/archive/index.php/t-650729.html](http://ubuntuforums.org/archive/index.php/t-650729.html)

Basically, I downloaded a Dell driver from [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe) and I use the instructions from this Dell tutorial:

[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

 It has worked fine for me!

Nathan, thank you!
Rodrigo

Just a comment: Dell driver and tutorial to solve an issue in HP laptop, Weird!!

---

### Post by rodrigo.prestes on 2008-04-26
Hey Guys,

Let&#8217;s try to figure out what's going on with DVD grants

Rodrigo

---

### Post by Ayuthia on 2008-04-27
> **Nathan.Flow said:**
> 
Maby some one can help me with my dvd problem... I'm using 64bit harty. and it tell's me when ever I try to play a dvd that I don't have enough permissions. or their's no disk, or their's nothing on the disk. but it will play some previews???:confused:
Have you loaded the codecs from medibuntu([https://help.ubuntu.com/community/Medibuntu)?](https://help.ubuntu.com/community/Medibuntu)?)

---

### Post by jeffreyvergara.NET on 2008-04-27
I have dv2715nr and successfully installed Wireless Driver but unfortunately it just keeps on acquiring IP Adress. I don't know if  the problem is the router's configuring but In vista it's not a problem.

I'm trying to fix it again because my Vista Recovery is not working anymore.

---

### Post by rodrigo.prestes on 2008-04-27
Are you using DHCP to obtain your IP?

---

### Post by jeffreyvergara.NET on 2008-04-27
I already fixed the problem I used HP Driver sp37950.exe and my HP Pavilion Dv2715nr is now online! hehehe..

---

### Post by Nathan.Flow on 2009-05-12
Hello again, 
Just want to add an update.
In 8.04 Harty, if you  use the drivers tool to automatically get and download the driver. It will work.
Here's the great thing about that....
It enables wext or linux's wireless driver, You can use this when you use wpa-supplicant and enable 802.1X "IEEE" data encryption. 
If only I could figure out how to modify KnetworkManager to take the settings needed for this network. Does any one know where to mod the config files of KnetworkManager??
Thanks.
Nathan

---

