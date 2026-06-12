---
title: "Logitech MX610 Email led"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by haaglin on 2006-04-30
Hi. 

I bought a Logitech mx610 Mouse a few months ago: 
[IMG]http://www.logitech.com./lang/images/0/8119.jpg[/IMG]
and i love this mouse. i got all functions working, except the led for email and msn. a few days ago, i found a program for flashing the email led, but, i'm having problems with permissions with this command:
> 
$mx610hack -f /dev/usb/hiddev0
$hiddev open: Permission denied

How can i make a program like Kgetgmail issue this command? 

This is the links to the mouse and the program i found. 
[http://www.kdedevelopers.org/node/1847](http://www.kdedevelopers.org/node/1847)

The mouse: [http://www.logitech.com./index.cfm/products/details/AU/EN,CRID=2135,CONTENTID=10917](http://www.logitech.com./index.cfm/products/details/AU/EN,CRID=2135,CONTENTID=10917)

Credits to Brad Hards for making this :)

---

### Post by haaglin on 2006-05-03
Anyone? it can't be that hard to get permissions to /dev/usb/hiddev0 ?

---

### Post by clov on 2006-05-09
Hi!
I own a MX610. Can you put the tilt wheel working? How do you do it?
Thkx!

---

### Post by bender unit on 2006-05-13
[QUOTE=clov]Hi!
I own a MX610. Can you put the tilt wheel working? How do you do it?
Thkx![/QUOTE]
I have a MX610, too. I initially got the tilt wheel (and the side buttons, too!) working using [this]("http://ubuntuforums.org/showthread.php?t=65471") forum topic. Even the volume control buttons work, but I didn't test them earlier so I don't know if that has anything to do with it. Alas, since I dist-upgraded to dapper, it's not working so great anymore. The tilt wheel still does work, but always scrolls in the wrong direction (i.e. I press it to the right, and it'll scroll to the left, kinda confusing). The side buttons currently don't work at all, don't know why and so far had no success in getting them back in a working state. But if you use Breezy, the above guide should work fine.

---

### Post by z1ross on 2006-06-16
I have been using the MX610 now for over 2months on both my 12" 1.33Ghz G4 iBook, and Now my 15 MacBookPro both running 10.4.6 (also worked on 10.4.5) with the full version of USB Overdrive V.10.4.5. The sideways scroll works, the volume up, down and Mute all work. Only the Mail and IM buttons and lights do not work here. It would be nice to seeone write a program for just those 2 buttons to work with any IM & Mail clients.

added 6-18-2006
Ok I was playing around with some other device programs and I found another program called "SteerMouse" which actually works better then USB Overdrive on this mouse. It gave me full programability to all the buttons including the email and IM buttons. (but no light support). I'm not a programmer but I have found some people working on making the lights work on the mouse and here is a link to the articale and a down load to compile and you can do different things with both the IM and Email lights. Now if some one could make an installer and some apple scripts to work with this mouse, we could tie in notifacations to the scripts and have the blinking lights for those notifacations we all want in our nosiy offices...lol. 

[http://www.kdedevelopers.org/node/2029](http://www.kdedevelopers.org/node/2029)

---

### Post by haaglin on 2006-06-22
Great!

---

### Post by Udziuolo on 2006-08-21
I'm using Dapper, but I think that's not a problem. I've found the solution for manipulating notification LEDs here: [http://www.kdedevelopers.org/node/1847]("http://www.kdedevelopers.org/node/1847")
```
1. Download and compile

2. Change permissions (potential security hole here?)
In /etc/udev/rules.d/50-udev.rules, add this line:
KERNEL=="hiddev*", NAME="%k", GROUP="root", MODE="666"

3. Write a script for KMail to execute. A sample one looks like this:
#!/bin/bash
# Turn on the light. -e is on, -f is flash, and -p is pulse
~/.mx610hack/mx610hack -p /dev/hiddev0
# Set how long you want the notification to last
sleep 1m
# Turn off the light after the specified amount of time
~/.mx610hack/mx610hack -o /dev/hiddev0

4. In KMail, configure the notifications such that it will execute the script.


```

If you'd like to use Thunderbird, have a look at [http://globs.chez.tiscali.fr/moz_extensions/yamb.html]("http://globs.chez.tiscali.fr/moz_extensions/yamb.html")

I've added mx610hack as an attachment.

---

### Post by jannol on 2006-10-13
About gaim notify...

KERNEL=="hiddev*", NAME="%k", GROUP="root", MODE="666"

is also needed for the [gaim mx610 notification](http://koti.mbnet.fi/simom/gaim_en/mx610-notification.php).

**Quick Install Guide**

* Install Gaim MX610-notification and enable it in gaim, close gaim

* Add the kernel rule in /etc/udev/rules.d/50-udev.rules, in case you don't have the /etc/udev/rules.d/50-udev.rules file, simply create it.

* Restart udev
```
~$ sudo /etc/init.d/udev restart
```

* Start gaim

I suppose you must have your mouse configured to use evdev in xorg.conf for all this to work.



I also set my mail-notification up with the mx610hack to pulse until all my mail is read. If you use mail-notification just install the mx610hack and set the commands in mail-notification.

I like this, I wouldn't belive I'll get all my buttons working when I bought this mouse. :-)

I also used xbindkeys and xautomation to bind sidescroll and thumb buttons.

**Quick Install Guide**

* Install xautomation and xbindkeys
```
~$ sudo apt-get install xautomation xbindkeys
```

* Create a default .xbindkeysrc.scm
```
~$ xbindkeys --defaults-guile > .xbindkeysrc.scm
```

* Open .xbindkeysrc.scm with your preferred text editor and add this
```
; Bind Alt+Left and Alt + Right to side scroll click on MX610
(xbindkey '("b:7") "xte 'keydown Alt_L' 'key Left' 'keyup Alt_L'")
(xbindkey '("b:6") "xte 'keydown Alt_L' 'key Right' 'keyup Alt_L'")
```

or if you have the old syntax (older xbindkeys I guess)
```
; Bind Alt+Left and Alt + Right to side scroll click on MX610
"xte 'keydown Alt_L' 'key Left' 'keyup Alt_L'"
b:7
"xte 'keydown Alt_L' 'key Right' 'keyup Alt_L'"
b:6
```

* Now run xbindkeys and try if it works in ex nautilus ```
~$ xbindkeys -n
``` If it does press ctrl+c to exit xbindkeys in the terminal.

* Edit .xbindkeysrc.scm with commands for your thumbbuttons, when you're done and tested, put xbindkeys in start up programs in sessions properties to have it autostart when you log in.

Oops, I forgot, this thread was about the email led, hmm well then I'll go hide until you're done screaming :oops:

---

### Post by tronica on 2006-10-28
i found this on the net, works great.

[http://97k.eu/blog/comments.php?y=06&m=10&entry=entry061015-170138](http://97k.eu/blog/comments.php?y=06&m=10&entry=entry061015-170138)

---

### Post by kogber on 2007-01-19
I have create a guide that includes info on getting the LED's to work, based on Dankoozy's blog as linked above.

[http://ubuntuforums.org/showthread.php?t=332256](http://ubuntuforums.org/showthread.php?t=332256)

---

### Post by melenor on 2007-11-18
[Sorry for double post internet problem]

---

### Post by melenor on 2007-11-18
Hi yah i have a logitech MX610 all i have working is right, left, wheel, wheel click and the e-mail button working how can i get any of the other buttons working or gettting the lights to light up? thanks for the help i have ubuntu 7.10

---

### Post by melenor on 2007-12-21
Just wondering if anyone has found a way to get the scroll wheel tilt to work, that is the only thing not working on mine thanks.

---

### Post by haaglin on 2008-03-02
It has been a while since the last post, but i just wanted to give an update. To get everything working, follow this guide: [https://help.ubuntu.com/community/Logitech_MX610 ]("https://help.ubuntu.com/community/Logitech_MX610")
**if you have followed any other guides, it might not work. **
This guide also makes the tilt wheel work. 

To get the tilt-wheel to work correctly in firefox too, do this:

1. enter about:config in the address bar. 
2. set mousewheel.horizscroll.withnokey.action to 0
3. set mousewheel.withnokey.sysnumlines to true

If anyone has found a way to use the im button other than with the pidgin plugin, please let me know.

---

