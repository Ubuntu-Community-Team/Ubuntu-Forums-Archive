---
title: "[LBP Canon Printer] the printer worked just for one time! Now it crashes!"
date: 2013-01-15
forum: Hardware
---

### Post by acronim on 2013-01-15
Hello everyone,
I've installed Ubuntu 12.10 i386 (updated) on our school lab room computers. there's a canon printer there that is connected to teacher PC via USB.
I installed it following [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)
the printer worked for just one time well and after a reboot I get this error (Plz click on the below image to enlarge it). The teacher is asking me for "printer"!
[[IMG]http://s1.postimage.org/8ce6k6u8r/lbp3100b_crashed.jpg[/IMG]]("http://postimage.org/image/8ce6k6u8r/")

---

### Post by acronim on 2013-01-16
If you know anything to solve this error, please let me to know!

I'm a newbie and I still don't know how should I solve these kind of errors.

kind regards.

---

### Post by acronim on 2013-01-16
Critical issue for me; please help.
Any comments would be valuable.
I would appreciate any comments.

---

### Post by acronim on 2013-01-18
I'm confused! do you need more details? If you need to know more, tell me and I'll gather them around the system!

---

### Post by pdc on 2013-01-18
this must all be very frustrating and disappointing for you; and perhaps very irritating too..

I think we all struggle to know how to help you; I sense you may feel there is a large army of highly seasoned debuggers to sort stuff..not sure that is true.........

......for most of us, we plod along installing things and generally they work....

I wonder if you have googled on the errors eg

> [COLOR="Magenta"]c3pldrv crashed with SIGSEGV[/COLOR]

.......most folks responses to the answers that emerge are: WHAT?

1) I can only check you installed the common driver first and then the specific......

I assume 

> [COLOR="Red"]sudo dpkg -l | grep Canon[/COLOR]

gives you the correct answers; perhaps you copy and paste back what you get;

2) what does > [COLOR="Red"]captstatusui -P LBP[/COLOR]%%%% give..I can't remember which LBP you have and this thread doesn't seem to detail it

........I have an LBP connected via a USB cable to a standalone computer running 32bit Ubuntu ........ I sense your school lab variant may be much more complicated........ maybe you help us by spelling out what it is ..

I can only comment on what worked for me on my 32bit system:

my favoured install is an amalgam of the Ubuntu capt page and sivella's advice:

so from [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

.........having installed the drivers ..........

I like the command to [COLOR="SeaGreen"]register the printer[/COLOR]:

> sudo /usr/sbin/lpadmin -p LBP%%%% -m CNCUPSLBP%%%%CAPTK.ppd -v ccp://localhost:59787 -E 

.......*as you don't need fifo directories*........

and then I like Sivella post #4 for the completeness

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

of proceeding to 

[COLOR="SeaGreen"]Register the printer with ccpd daemon:
[/COLOR]
then [COLOR="SeaGreen"]Start ccpd daemon:[/COLOR]

then [COLOR="SeaGreen"]Test install:[/COLOR]

......then I did the Sivella tweaks to ensure it starts each time ..and it does ..........

---

### Post by ahallubuntu on 2013-01-18
I just setup a couple of Canon printers in 12.04 .  The first printer was automatically detected and I used the default driver.  It worked fine - once - and then was flaky.  Even when I could get it to print, it was very slow - almost like I had set it to "super fine" mode.  I know this printer prints much faster than this and that something was wrong.

So I went back to the driver Canon published for 10.04.  The Debian package did not work, but I was able to install it via the text installer, and now it works well.  Second printer also worked well by installing the same way.  I don't know the model Canon you have but you might look for a driver for it on Canon's Europe site and even if 12.10 isn't officially supported, as in my case you might be able to get the old driver to work.

---

### Post by pdc on 2013-01-18
> [COLOR="Magenta"]I just setup a couple of Canon printers in 12.04 [/COLOR].

.........perhaps you spell out which Canon printers you worked with ..

acronim is talking about the LBP series;

which are laser printers;

...............would you be talking about inkjet printers, of the PIXMA series?

---

### Post by leifwi on 2013-04-18
I have 3 computers runing ubuntu 12.04 and 12.10 and the Canon Capt driver version 2.50 installed.
After some tuning I got the printer to work, all computers show a system error at startup saying 
c3pldrv crashed with SIGSEGV in write ()

It would be nice get rid of this error.

---

