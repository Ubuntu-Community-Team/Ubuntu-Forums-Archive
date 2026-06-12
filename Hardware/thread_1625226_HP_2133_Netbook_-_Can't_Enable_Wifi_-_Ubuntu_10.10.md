---
title: "HP 2133 Netbook - Can't Enable Wifi - Ubuntu 10.10"
date: 2010-11-18
forum: Hardware
---

### Post by erichhaubrich on 2010-11-18
I was having an issue where my HP 2133 was not recognizing the keyboard/trackpad. I managed to use a USB mouse and the on-screen keyboard to finally get it to run the updates. It downloaded the updates and installed them just fine.

When the machine came back up after the reboot the keyboard and trackpad worked fine, but **Wifi is now disabled and the hardware switch does nothing** (neither does FN+F2).

I can't seem to find any way in the software to enable it.

Under '**Additional Drivers**' I see the '**Broadcom STA wireless driver**' but there is no obvious way to enable the Wifi card at all.

What's really strange is that it worked just fine before the update so I know that the hardware can work with U 10.10, it has just decided not to.

I'm really looking forward to using this OS on this little machine. Windows 7 made it run like a pig. Ubuntu 10.10 is really fast and stable and smooth. *I just need the **NET** part of it to work on this **Netbook.***

*Note: I am not using the Netbook Edition.*

---

### Post by beloved88 on 2010-11-19
This is a small issue with all HP mini models i've seen.  To activate the broadcom proprietary driver, you need to be connected to the internet.  Use an ethernet cable or usb to connect to a router/modem directly.  If you can't get that working that way, you will need to download and compile the driver yourself, which is not quite as scary as it sounds

---

### Post by Cernael on 2010-11-21
I'm having the same problem - HP mini 2133, upgraded to Ubuntu 10.10, wireless stopped working. I found [this thread]("http://georgia.ubuntuforums.org/showthread.php?t=1592544"), and tried the solutions there, in particular [this post]("http://georgia.ubuntuforums.org/showpost.php?p=9988773&postcount=17"), which to my noob eyes seems to initiate the driver compilation process suggested above, and...


...didn't work. I'm back where I started, it seems. What's the next step?

---

### Post by pancyber on 2010-12-06
still does not work... any ideas ?

---

### Post by bnjmnwroberts on 2010-12-06
Hello, everyone. I too had the same problem. Here's what I did.
1. Make sure you are connected to the internet.(via ethernet cable)
2. go to "System-Administration-Additional drivers.
3.You will see a gold lock on top of a sound card or whatever that cheesy graphic is.Click on that icon.
4. It will look for 3rd party updates.
5. It will show you the available drivers for your system.
( I use the STA driver, I have an e-machines m-250 netbook)
6.If you download and install the B43 driver, and it fails, try the STA driver.
7. Restart your computer.
8. Go online with your wi-fi enabled computer.
Hope this helps.

---

### Post by Cernael on 2010-12-06
That did not work for me, IIRC.

I went back to 10.04 instead. Works tolerably. (Though for some reason, the WIRED network has stopped working. Weird, huh?)

---

### Post by AmitProgrammer on 2010-12-31
Hi, I got the similar problem in Ubuntu 10.10,

I was working with WiFi for days and then suddenly it shows it as disabled, I was able to make it work using the following command.

rfkill unblock all

try this, it may work for you too. If it has already worked the drivers are there, and you just have to enable the device. 

Hope this helps.

Amit Singh

---

### Post by cil_8 on 2010-12-31
Same problem with HP Envy 17 and Ubuntu 10.10

---

### Post by crunkyboy on 2011-02-01
Same problem with my HP G62 notebook. Everything was working fine under 10.04 and yesterday I upgraded it to 10.10 and boooom, the WiFi stopped working. Basically, it seems that it is disabled, because the Broadcom drivers are installed but the Fn+Keys are not working and I can't activate the WiFi (Fn + f12). (under 10.04 the Fn keys were also not working but the wifi was working).

Also, did some research and none of the solutions I found worked. Is this a known bug or something? I experienced the same issue while I was under Arch one month ago and did not find a solution on this. 

After that, I switched back to Ubuntu because I did manage to get my hybrid graphic working, but seem that I can not use 10.10 so the best option would be to downgrade to 10.04.

Any help appreciated.

Out

---

### Post by wyrdR on 2011-03-11
Wifi on a HP Mini 2133 was always disabled until I updated the BIOS firmware.  

After that, wireless was perfect on Ubuntu 10.10.

If you're already running the latest firmware version, then sorry.  I don't know.

---

### Post by isabeau on 2011-04-22
> **AmitProgrammer said:**
> Hi, I got the similar problem in Ubuntu 10.10,

I was working with WiFi for days and then suddenly it shows it as disabled, I was able to make it work using the following command.

rfkill unblock all

try this, it may work for you too. If it has already worked the drivers are there, and you just have to enable the device. 

Hope this helps.

Amit Singh



I had the same problem on a HP Pavilion and it worked! Thank you so much!

---

### Post by jeevak on 2011-05-17
> **AmitProgrammer said:**
> Hi, I got the similar problem in Ubuntu 10.10,

I was working with WiFi for days and then suddenly it shows it as disabled, I was able to make it work using the following command.

rfkill unblock all

try this, it may work for you too. If it has already worked the drivers are there, and you just have to enable the device. 

Hope this helps.

Amit Singh

hey Amit, 

i'm trying to use the 11.04 on my mini 2133 but every time it tries to connect to the net via the wifi it freezes. have started downloading the 10.10. just wanted to know where i need to type the command"rfkill unblock all? in the terminal window? do i need to type sudo before that?
please lemme know
thanks

---

