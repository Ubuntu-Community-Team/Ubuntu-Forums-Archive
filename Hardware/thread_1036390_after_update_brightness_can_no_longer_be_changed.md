---
title: "after update brightness can no longer be changed"
date: 2009-01-10
forum: Hardware
---

### Post by jasonpeinko on 2009-01-10
I updated my ubuntu laptop, (dv6000) and after the update I can no longer change screen brightness with fn+f7 or fn+f8 nor can i use the brightness applet.

---

### Post by crazyness003 on 2009-01-10
what does your brightness applet look like? 
Is it like the attachment below? If so, then you and I have the exact same problem and I was about to post the exact type of thread!

My first guess is bug. But i wanted to ask first.

EDIT: Forgot to add that I too have an HP TX1308nr (See [My Specs]("http://ubuntuforums.org/showthread.php?p=5625571#post5625571"))
also, if anyone can tell us how we can get a log of recent updates thru apt. Maybe the culprit can be pin-pointed I'd appreciate it

I also have an lshal output txt file, biut its massive (went over the forum's limit. If you need a specfic section, i can post it)

---

### Post by jasonpeinko on 2009-01-10
Yes! Exact same thing.

---

### Post by pp. on 2009-01-11
I have another laptop (Compaq nc6220) and I haven't used the brightness applet. However:

I now have added the applet to the task bar, and it doesn't work, either. It shows the same error message as shown in the post above.

The brightness buttons on the keyboard (in my case fn+f9 and fn+f10) do work albeit slowly. Holding fn+f9 or fn+f10 for a longer time will indeed alter the brightness and will keep on doing so for a while after I let go of the button. 

It appears that the increment or decrement for the brightness is set to a very low value, and that there's a rather long delay involved when the buttons are being held for some time. 

Still, brightness does work on my laptop, after a fashion. I can not say if there has been any kind of change recently, as I don't normally use the brightness control.

---

### Post by blackened on 2009-01-11
I know many dell laptops are having issues with some recent updates. These could be related.

---

### Post by minisori on 2009-01-11
My asus laptop has the same problem since i updated a couple of hours ago. Well the brightness change but when i restart the computer, also i don't see the gnome dialog changing it...

I also noticed there is no longer the option to down the brightness under inactivitid, in the energy manager dialog.

This is the list of updated packages if it helps:

bind9-host (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
dnsutils (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libbind9-40 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libc6 (2.8~20080505-0ubuntu7) to 2.8~20080505-0ubuntu8
libc6-dev (2.8~20080505-0ubuntu7) to 2.8~20080505-0ubuntu8
libc6-i386 (2.8~20080505-0ubuntu7) to 2.8~20080505-0ubuntu8
libdns43 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libisc44 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libisccc40 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
libisccfg40 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
liblwres40 (1:9.5.0.dfsg.P2-1ubuntu3) to 1:9.5.0.dfsg.P2-1ubuntu3.1
linux-headers-2.6.27-11 (2.6.27-11.22) to 2.6.27-11.23
linux-headers-2.6.27-11-generic (2.6.27-11.22) to 2.6.27-11.23
linux-image-2.6.27-11-generic (2.6.27-11.22) to 2.6.27-11.23
linux-libc-dev (2.6.27-11.22) to 2.6.27-11.23
ntpdate (1:4.2.4p4+dfsg-6ubuntu2.1) to 1:4.2.4p4+dfsg-6ubuntu2.2

---

### Post by crazyness003 on 2009-01-11
well, it seems we all have related problems, but unlike pp. , my brightness controll is completely busted. I have no keyboard-softkey control, nor applet control. Not even in the power management. I do believe this is cause by a recent update. Its not extrememly important, butenough to annoy me.

If anyone can tell me how i can access recently a list of recently downloaded updtes, I may be able to pin-point the cause. Or if you need a specfic section of lshal, i made an output file.

hopefully someone can at leased tell us where to report this as a bug (if it is one)

---

### Post by moeFinley on 2009-01-11
I had no softkeys before but now also have no aplet control or power management control. I makes it almost impossible to seem my screen in bright light :(

I have an Advent 8212

---

### Post by crazyness003 on 2009-01-11
I submitted this as a bug on lanuchpad.net.
[https://bugs.launchpad.net/ubuntu/+bug/316145](https://bugs.launchpad.net/ubuntu/+bug/316145)

So if anyone wants to add info there, it will be addressed quicker.
If anyone asks for your lshal, make sure you run this command
```
lshal > hal_output.txt
```
The lshal output is HUGE, so containing it in a text file and then attaching it is the best way of doing it. this will save all your output on a file called "hal_output.txt" in your /home/<your user name>

I also gave IRC a shot, but no dice. That place is chaotic. They all basically screamed at me when I asked where i should post the bug :P

Hopefully someone will help.

---

### Post by minisori on 2009-01-12
> **crazyness003 said:**
> If anyone can tell me how i can access recently a list of recently downloaded updtes, I may be able to pin-point the cause. Or if you need a specfic section of lshal, i made an output file.


In synaptic, go to file and history. If you used update manager to update your packages it must be there.
I also replied your bug in launchpad.

---

### Post by priegog on 2009-01-13
Same problem here. 
I'm using a (quite old) motion computing m1300.
Already subscribed to and replyed to your bug, crazyness. I urge everyone here to do the same, since the ubuntu devs check launchpad and only ocassionally the forums, so there's no use in complaining here.

---

### Post by crazyness003 on 2009-01-13
thanks dude. I set the bug as confirmed. Now the more people that give input, the better chance of getting someone on the ball. Unfortunately, so far it looks like its a kernel problem. We'll see what happens

---

### Post by minisori on 2009-01-14
Yes is a kernel problem, i upgraded to jaunty the other day, and it was not there, unfortunately after a kernel update yesterday the bug comes with it too.

---

### Post by cybergrunt on 2009-01-14
Not sure if this is related but I lowered the brightness using the Fn keys on my Latitude running Intrepid and it wouldn't go back up again until I rebooted. I'm just not going to bother touching it any more.

---

### Post by HunterThomson on 2009-01-14
Same problem with the Lenovo Ideapad ever sents Hardy..... We Fixed it by fixing  problems with the DSDT. There is a vary good chance it is the same problem with your computers. Why can I say that ? The DSDT is a BIOS file that tels the ACPI kernel module how to handle the hardware.


Read This...

  Bill Gates on Making ACPI Not Work with Linux

[http://www.osnews.com/story/17689/Bill-Gates-on-Making-ACPI-Not-Work-with-Linux/](http://www.osnews.com/story/17689/Bill-Gates-on-Making-ACPI-Not-Work-with-Linux/)

---

### Post by minisori on 2009-01-14
> **cybergrunt said:**
> Not sure if this is related but I lowered the brightness using the Fn keys on my Latitude running Intrepid and it wouldn't go back up again until I rebooted. I'm just not going to bother touching it any more.

Yes is related to this bug.

---

### Post by HA4ever on 2009-01-14
same problem HP dv6799

[http://ubuntuforums.org/showthread.php?t=1036041](http://ubuntuforums.org/showthread.php?t=1036041)

---

### Post by crazyness003 on 2009-01-16
**FIXED**
Latest intrepid-propoesd updates of the kernel fix this (2.6.27-11.24)
Hooray Devs!

---

