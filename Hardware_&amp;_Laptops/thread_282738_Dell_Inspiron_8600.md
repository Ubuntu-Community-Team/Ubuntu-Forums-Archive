---
title: "Dell Inspiron 8600"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by IslandGuy on 2006-10-23
Hello

i have an issue with wireless on a dell 8600, i am knew to linux so bare with me if i say the wrong termonology.

Ok, wired connection works fine on the laptop, but wireless no joy. i have tried to installed network manager, but can not find it in the apllication area.  

can anyone please find advise the best way to proceed.

---

### Post by ReverendJT on 2006-10-23
Do you have a broadcom or an intel wireless card?

---

### Post by IslandGuy on 2006-10-23
I have to say, i do not know.  it was my parents laptop.  How can i find out in Ubuntu?

---

### Post by W3p on 2006-12-10
"lspci" in the console. It will write out the name and version of you card.

---

### Post by river-1 on 2006-12-21
I guess I'll pick up where the last guy left off... have been struggling with this for the last couple days.

card details:
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

**ndiswrapper -l yields:**
Installed ndis drivers:
bcmwl5a driver present, hardware present

**iwconfig yields:**

lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

since I am a little bit of a newbie and have been cruising a number of places without success - anything will help.

thanks.

---

### Post by meul on 2006-12-23
Hello, I have 8600 with bcm4306 wifi card.
I've tested ndis wrapper too but with no result .

I've reinstalled Ubuntu Edgy and trying this:

You must have BCMWL5.SYS file, 2 solutions:
1) on a win xp partition > look for BCMWL5.SYS at /windows/system32/drivers/

ex. with /xp/ as mounted xp partition:
  ```
 cp /media/xp/WINDOWS/system32/drivers/BCMWL5.SYS ~/Desktop/ 
```

2) on a dell driver cd > extract from /media/cdrom0/zipfiles/r83959.exe
```
 cp /media/cdrom0/zipfiles/r83959.exe ~/Desktop/ 
unzip ~/Desktop/r83959.exe -d ~/Desktop/tmp/

```
 copy BCMWL5.SYS on your desktop and delete other files.

Now you must install bcm43ww-fwcutter:
```
sudo apt-get install bcm43xx-fwcutter
```
Extract .fw files in /lib/firmware/ directory with it:
```
sudo bcm43xx-fwcutter -w /lib/firmware/ ~/Desktop/BCMWL5.SYS

```
Module and network restart:
```
sudo rmmod bcm43xx
sudo modprobe bcm43xx
sudo /etc/init.d/networking restart
```

That's all, active and config your network card with system>admin>network (ssid + key)
I have no encryption key and my wifi network will run now.

Sorry for my bad english :° )

---

### Post by eurgain on 2006-12-28
Frankly, if you want to use this machine seriously with Linux, buying an Intel card is probably the way to go.  I have a spare IPW2100 (802.11b) card from my 8600 machine (I replaced it with an IPW2200 (802.11g).)  Both of these cards have *excellent* support (thanks are due to Intel).

If you are happy with an 11M connection, send me a private message, and you can have my IPW2100 if you want for 10&#8364; + postage.  It is a simple job to fit - about 5 mins, but you do have to remove one of the covers on the bottom with a screwdriver.

A

---

