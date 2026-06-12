---
title: "Dell Inspiron Wireless help"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by Riona on 2006-03-27
New to ubuntu and trying to get the wireless setup.  I found a website called Linuxant and downloaded the broadcom files. I don't see any iinstructions for ubuntu on that site. So I'm lost. The file that was downloaded was an exe extension. 
I've also tried the ndiswrapper route with no luck. Any suggestions or help to make this easeir would be much appreciated.  the machine is a dell inspiron b120 broadcom 1450 i believe. :neutral:

---

### Post by d3dtn01 on 2006-03-29
I've got a B120 also and just installed ubuntu. I'm new to linux, but have spent a lot of time trying to get everything to work. I've yet to get wireless to work, but I've gotten close. Follow these steps:

1. Download this zip drive to get the drivers you need.
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

2. Unzip the file (double-click on it). The files you need from it are bcmwl5.inf and bcmwl5.sys.

3. Get the ndiswrapper-utils.
~$sudo apt-get install ndiswrapper-utils

4. Run ndiswrapper.
~$sudo ndiswrapper -i bcmwl5.inf

5. Write an alias for the wireless device.
~$sudo ndiswrapper -m

6. Create list of module dependancies.
~$sudo depmod -a

7. Add module to kernel
~$sudo modprobe ndiswrapper

8. Configure wireless. Navigate to System>Administration>Networking. You should should a wireless device listed. To configure it, highlight the wireless connection and click on properties. From here you'll put in info about your wireless network (SSID, key, etc.).

I've reached step 8, but I still can't connect. If you get past this let me know how, please.

Thanks to alceste (and many others) for providing most of the above info:
[http://www.allthingsalceste.com/useful-ubuntu-breezy-on-a-dell-b130/](http://www.allthingsalceste.com/useful-ubuntu-breezy-on-a-dell-b130/)

By the way, have you had any success with the sound on your B120. When I plug in my earphones, they work but the external speakers don't mute. Kinda pointless, huh? This is a problem with lots of laptops. I've read all sorts of stuff but haven't yet solved the problem.

[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

---

### Post by Riona on 2006-03-29
ok this is a dumb question but...
~$sudo ndiswrapper -i bcmwl5.inf
what is the letter between the w and 5? when i type the number 1 it doesn't like it.

---

### Post by Riona on 2006-03-29
.

---

### Post by ZeromusMog on 2006-03-30
[QUOTE=Riona]ok this is a dumb question but...
~$sudo ndiswrapper -i bcmwl5.inf
what is the letter between the w and 5? when i type the number 1 it doesn't like it.[/QUOTE]

it's an L, hit tab in linux whenever you are in doubt as it autocompletes most things for you :)

I finally got ndiswrapper to work (no idea why it just started working) but now Ubuntu has taken to turning off my wireless card at boot! :( I can't get it to enable unless I boot into Windows, but then it turns off again while Ubuntu is booting (around when it tries to set the time). I'm trying to find some information on this, perhaps someone has some ideas?

---

### Post by d3dtn01 on 2006-04-03
Did you check your BIOS settings. The default setting may be to have your wireless card off. I believe that Windows turns it on at boot-up, but that Ubuntu won't. 

And I finally got my wireless working on my Dell Inspiron B120. I didn't have to do anything more than what I explained above. All of a sudden it's working. Now I just have to figure out how to get my external speakers to mute when I plug in headphones.

---

### Post by Riona on 2006-04-06
Still having trouble

followed the steps below and got all the way down to #7.
If I Navigate to System>Administration>Networking I see no wireless option.
Also If i do a iwfconfig I get the following :

lo No wireless conecction
eth0 no wireless connection
sit0 no wireless connection

If I run ndiswrapper -l  , I see
installed ndis driver:
bcmwl5 driver present hardware present.

Not sure what step I need to take now to see wireless when navigatin to System>Administration>Networking .
 The driver i'm using was dowloaded from the dell website . 

--------------------------------------------------------------------------------

I've got a B120 also and just installed ubuntu. I'm new to linux, but have spent a lot of time trying to get everything to work. I've yet to get wireless to work, but I've gotten close. Follow these steps:

1. Download this zip drive to get the drivers you need.
[ftp://ftp.support.acer-euro.com/note...ver/80211g.zip](ftp://ftp.support.acer-euro.com/note...ver/80211g.zip)

2. Unzip the file (double-click on it). The files you need from it are bcmwl5.inf and bcmwl5.sys.

3. Get the ndiswrapper-utils.
~$sudo apt-get install ndiswrapper-utils

4. Run ndiswrapper.
~$sudo ndiswrapper -i bcmwl5.inf

5. Write an alias for the wireless device.
~$sudo ndiswrapper -m

6. Create list of module dependancies.
~$sudo depmod -a

7. Add module to kernel
~$sudo modprobe ndiswrapper

8. Configure wireless. Navigate to System>Administration>Networking. You should should a wireless device listed. To configure it, highlight the wireless connection and click on properties. From here you'll put in info about your wireless network (SSID, key, etc.).

---

### Post by Riona on 2006-04-09
Followed the instructions below but my settings well not stay. When I reboot the machine the wireless connection goes away. Also two other probles, i'm using WPA and I'm not able to acess any web pages.

To get the Wlan working we are gonna install a wrapper to handle the windows drivers for the card. install Ndiswrapper by putting the following command in the terminal :

sudo apt-get install ndiswrapper-utils

it will say that the ndiswrapper is installed , now we are gonna be needing those 2 files i named above so if you havent downloaded them yet get them from the urls below :

wget [http://biginoz.free.fr/linux/bcmwl5.sys](http://biginoz.free.fr/linux/bcmwl5.sys)
wget [http://biginoz.free.fr/linux/bcmwl5a.inf](http://biginoz.free.fr/linux/bcmwl5a.inf)

now go to the folder where you downloaded the .sys and the .inf to, in the terminal type this :

sudo ndiswrapper -i bcmwl5a.inf (or the driver that your inspiron needs)

the driver should install without any problems, to check if it was installed ok type :

ndiswrapper -l

it should give 1 error and 1 succesfull message (the message should be something like this below)

Installed ndis drivers: bcmwl5a driver present, hardware present

To start the module type :

sudo ndiswrapper

To let Ubuntu find the Wlan card type :

sudo modprobe ndiswrapper

afterwards you type the following line to make sure that the wlan card will be started when you boot linux :

sudo ndiswrapper -m

---

