---
title: "TVTIME / TV Card Configation Help Needed."
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by rickldavis1 on 2005-06-12
I need some help setting up tvtime with my tv card. I have forgotten what type of card I have, but it uses a Phillips tuner.

If I open a terminal and type the commands listed below TVtime works fine.
I would like to know how to get the driver to load at startup.

In Fedora I just entered "saa7134 tuner=39 card=2 gbuffers=4" in "etc/modprobe.conf." I don't have a modprobe.conf file on 5.04. I tried the using the update-modules, but I'm not familar with that tool and I wasn't lucky.

Thanks in advance for the help.

rick@blackbox:/$ cd /sbin
rick@blackbox:/sbin$ sudo rmmod saa7134
rick@blackbox:/sbin$ sudo rmmod tuner
rick@blackbox:/sbin$ sudo modprobe saa7134 tuner=39 card=2 gbuffers=4

---

### Post by stepper on 2005-06-12
Try this [site](http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm)  for help.

---

### Post by rickldavis1 on 2005-06-12
Stepper,

Thanks!

That was the info I needed.

 I appreciate the help.

---

### Post by stepper on 2005-06-13
[QUOTE=rickldavis1]Stepper,

Thanks!

That was the info I needed.

 I appreciate the help.[/QUOTE]
No problem mate!

---

### Post by sksbir on 2005-06-15
i would appreciate some help too,  :grin: 

it seems that i have the same TVtuner : saa7134 + card39, but never get it working : see here : [[UNSOLVED] Flytv Platinium 33 mini : TV Tuner not enabled.](http://www.ubuntuforums.org/showthread.php?t=32598).

@stepper  i know that you already answered me to look at this webpage , but saa7134 card description still stop at 33.

@rickldavis1 : gbuffers=4 : this option seemed to be used by bttv module... I don't understand.
Did you really have the same TVcard has mine ? ( a Flytv platinium 33 mini )
Did you stil use the card=39 option ? (and then, what sort of help brought you the webpage quoted by stepper )

thank's for your attention.

---

### Post by stepper on 2005-06-15
[QUOTE=sksbir]
@stepper  i know that you already answered me to look at this webpage , but saa7134 card description still stop at 33.
[/QUOTE]
Ok, a friend of mine has  a k-world PVR-7134 on knoppix and this is what he does to get tv-time working

```
#rmmod saa7134
#modprobe -v saa7134 card=5
#tvtime-scanner
```
And the damn thing would pickup some tv signals

---

### Post by rickldavis1 on 2005-06-16
sksbir

Hopefully, you have your card running by now.

My card says it is a Flyvideo 2000. I'm not convinced that was the label on the box, but I tossed all that stuff long ago.

I can't remember the origin of  the “gbuffers=4 “ statement. It doesn't cause any problems, but I don't know if it is a benefit.

Here is what I did to get the card running,

	I looked over the info on the URL that stepper suggested.

	I created a file 

		/etc/modprobe.d/saa7134

	it contained the following info

		#flyvideo
		options saa7134 card=2 tuner-39 gbuffers=4

That is it.

---

### Post by sksbir on 2005-06-16
I will try this tonight.

A big thanks for your speedy answers  :)

---

### Post by sksbir on 2005-06-20
althougt i have tried every possibility (each tuner, with each card, with "gbuffers=4" ), i didn't succeed to activate my tuner...

Thank's anyway ;)

---

### Post by peter07 on 2005-06-20
I have got AverTV GO 007 TV/Radio tunner. I'm trying to install this card. Where I can't find some info about it??

---

### Post by stepper on 2005-06-20
peter07, try the instructions in rickldavis1 last post, with the card option changing to 57. 
card=57
[QUOTE=rickldavis1]
I created a file

/etc/modprobe.d/saa7134

it contained the following info

#flyvideo
options saa7134 card=2 tuner-39 gbuffers=4

That is it.[/QUOTE]

---

### Post by peter07 on 2005-06-22
Sorry - it doesn't work

I've done:

sudo gedit /etc/modprobe.d/saa7134

#flyvideo

options saa7134 card=57 tuner-39 gbuffers=4

---

### Post by sksbir on 2005-06-22
I have taken a look yesterday about this card=57.

Just after invoking modprobe with the options you want, just type in **dmesg** and you will get messages about your card model: 57 gives "generic" card, so you have no chance to get something working with this option.
Card definition stops at 47 ( or 46 or 48, i don't remember exactly).

When i use card=39, i get a message in dmesg witch seems to show that this is the good card number for me (flyvideo TV platinium 33 ), but even so, my tuner don't detect any channel.

---

### Post by peter07 on 2005-06-23
XXX@XXX:~ dmsg

...Linux video capture interface: v1.00
saa7134: Unknown parameter `tuner-39'...

When I try turn on tvtime:

XXX@XXX~$ tvtime
Running tvtime 0.9.15.
rtctimer: Cannot set periodic interval: Brak dost&#281;pu

    Failed to get 1024 Hz resolution from your RTC device.  High
    resolution access is necessary for video to be smooth.  Please
    run tvtime as root, set tvtime as SUID root, or change the
    maximum RTC resolution allowed for user processes by running this
    command as root:
        sysctl -w dev.rtc.max-user-freq=1024
    See our support page at [http://tvtime.net/](http://tvtime.net/) for more information.

Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/XXX/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: Nie ma takiego pliku ani katalogu
 

I want also listen radio on my PC. :( I'm searching for software, which allows me to watch TV and listen music.

---

### Post by sksbir on 2005-06-23
[QUOTE=peter07]XXX@XXX:~ dmsg
...Linux video capture interface: v1.00
saa7134: Unknown parameter `tuner-39'...
[/QUOTE]



you must use "tuner=39", not "tuner-39"   ;-)

---

### Post by peter07 on 2005-06-23
XXX@XXX:~ dmesg

...
PCI: Setting latency timer of device 0000:00:07.5 to 64
Linux video capture interface: v1.00
saa7130/34: v4l2 driver version 0.2.12 loaded
PCI: Found IRQ 10 for device 0000:00:09.0
saa7130[0]: found at 0000:00:09.0, rev: 1, irq: 10, latency: 32, mmio: 0xdf011000
saa7130[0]: subsystem: 1461:d109, board: UNKNOWN/GENERIC [card=0,autodetected]
saa7130[0]: board init: gpio is 107a8
saa7130[0]: i2c eeprom 00: 61 14 09 d1 ff ff ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 20: 13 02 ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
tuner: chip found at addr 0xc2 i2c-bus saa7130[0]
tuner: type set to 39 (LG NTSC (newer TAPC series)) by saa7130[0]
tuner: type already set to 39, ignoring request for 37
tuner: The type=<n> insmod option will go away soon.
tuner: Please use the tuner=<n> option provided by
tuner: tv aard core driver (bttv, saa7134, ...) instead.
saa7130[0]: registered device video0 [v4l2]
saa7130[0]: registered device vbi0
...

TVtime, Zapping - didn't work. 

How to install radio ???

---

### Post by abandoned_hussam on 2005-06-23
Hey guys, I have a kworld saa7130 
I added saa7134 card=11 to /etc/modules
Now I get video but no sound in tvtime. ( sound in kmix is setup correctly ) 
I works fine when I reboot to windows, but since I hardly use windows anymore, I really need this to work in Kubuntu as well.

---

### Post by stepper on 2005-06-23
[QUOTE=peter07]XXX@XXX:~ dmesg
..
PCI: Found IRQ 10 for device 0000:00:09.0
saa7130[0]: subsystem: 1461:d109, board: UNKNOWN/GENERIC [card=0,autodetected]
...

[/QUOTE]
Can u do _lspci_ and give the correct name of your card?

---

### Post by peter07 on 2005-06-23
Lspci:

0000:00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

I also have to say, that I've  made some otehr changes. One man's advised me to:

sudo gedit /etc/modprobe.d/aliases 

and enter there:

alias video bttv
options tuner debug=1
options bttv radio=1 pll=1 card=13 bttv_verbose=2 bttv_debug=1  
options tuner type=37 pal=b 

He has also advised me to do something like that:

lsmod | grep bttv 
lspci .TV 
lspci -dotTV 
lsmod -grep bttv 
lsmod grep bttv 

and 

sudo ss... (something, but I don't remember)  

:/

---

### Post by abandoned_hussam on 2005-06-23
peter07, I have a "Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)" as well, if you get it working, please tell me how.

---

### Post by peter07 on 2005-06-24
Mayby somebody know how to install radio from my AVERTV GO 007 ??

---

### Post by heyheyhey on 2006-11-06
Hi all, You may not be monitering this thread anymore but if you are you maybe a more advanced user by now. I'm new to ubuntu after escaping windoze and cannot get my tv tuner working. I have a intel 64bit with ubuntu 6.06lts, and an avertv 303p card. the chipset is a SAA7133 by phillips.

Any help will be most appriciated

---

### Post by sexyback on 2006-11-17
I guess because these 7130 cards suck they apparently  don't have a "booktree" so you have to play with the numbers like crazy.  luckily there is a script somewhere that automatically does it for you, it simply removes one of the variables between card= and tuner=  so you don't have to guess so much...

if you are rediculously new to linux simply open a terminal > type "sudo gedit /usr/bin/tuner.sh" (without the wquotes of course) you will then see am empty text editor where you will paste this exactly:


[FONT="Arial Black"]#/bin/sh
MAXTUNER=69
i=0
while [ $i -lt $MAXTUNER ];
do
rmmod tuner saa7134
modprobe saa7134 card=3 tuner=$i
echo "Actual tuner is:" $i
sleep 1 # this is to make sure /dev/video is registered when tvtime starts
tvtime
i=$(($i+1))
done
[/FONT]

then simply close gedit and in that same terminal type 
sudo chmod +x /usr/bin/tuner.sh

after that just type tuner.sh and it will popup tvtime and do its thing. play with the inputs in tvtime escape the script if it doesn't work with the <ESC> key and it iwll relaunch with a different tuner #... if that still doesn't kind of work then change the card number (sudo gedit /usr/bin/tuner.sh) and edit on the line 
modprobe saa7134 card=3 tuner=$i 
change card=3 to another one, ive tried 38, 39 and 40 but didn't work as well for me as card=3... 
WHEN  you finally find a card that works note the terminal tells you 
""Actual tuner is:" $i"  so just type in the terminal after that  sudo rmmod bttv and again re-enter sudo modprobe saa7134 card=<WHATEVER CARD YOU CHOSE> tuner=<WHATEVER TUNER SAID WORKED>

that is all...I've been up far too long playing with this crap.

---

### Post by yurtk on 2007-01-02
FYI
My Manli saa7130 tv card works fine with /etc/modprobe.d/saa7134 file containing a line:
options saa7134 card=3 tuner=5 oss=1

---

