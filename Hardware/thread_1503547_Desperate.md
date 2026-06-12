---
title: "Desperate"
date: 2010-06-06
forum: Hardware
---

### Post by michael80_oz on 2010-06-06
I have recently bought a wacom bamboo pen and touch. I am so desperate to get it going, I will genuinely pay someone for their trouble. I have tried many times and ways to get it going. and every time, I have come to a dead end. I have looked through The Linux Wacom Project site and other various sites. 

I'm still too new to this to understand some of what is being instructed. Any info to steer me in the right direction will be gratefully appreciated.

System specs:
CPU: AMD Athlon XP 3200+
Ram: 1.5g
Ubuntu 10.04 on a 40 Gig Hdd (yes, it's small)
umm....kernel: Linux 2.6.32-22-generic


(please observe I only joined this forum today...so please go easy on me;))

---

### Post by Revolutionary101 on 2010-06-06
Follow this tutorial:

[http://linuxwacom.sourceforge.net/index.php/howto/ubuntu](http://linuxwacom.sourceforge.net/index.php/howto/ubuntu)

Just copy and paste the commands within the quotations into terminal (goto Applications>Accessories>Terminal to open it). For someone that is new to Ubuntu this may seem a bit intimidating but if you do it correct your Bamboo touch should work.

If you have any questions just ask.

---

### Post by CharlesA on 2010-06-06
Linux 2.6.32-22-generic is a Lucid kernel. :)

Checking [here]("https://help.ubuntu.com/community/Wacom"), if you haven't already would be a start. :)

---

### Post by michael80_oz on 2010-06-06
> **Revolutionary101 said:**
> What version of Ubuntu are you running?


10.04? ....is that the answer you were looking for?

---

### Post by Revolutionary101 on 2010-06-06
> **CharlesA said:**
> Linux 2.6.32-22-generic is a Lucid kernel. :))

Oh thanks, I didn't notice that. :)

---

### Post by an0dos on 2010-06-06
It seems like you are not alone in your frustrations with that wacom tablet. :)

Have you tried the steps outlined here: [http://ubuntuforums.org/showpost.php?p=9119518&postcount=782](http://ubuntuforums.org/showpost.php?p=9119518&postcount=782) ?

---

### Post by michael80_oz on 2010-06-06
ok, I followed the link and entered the first command and here is what I get

[COLOR=Black]michael@michael-desktop:~/Desktop$ wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4.tar.bz2)
--2010-06-07 13:47:13--  [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.4.tar.bz2)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-06-07 13:47:14 ERROR 404: Not Found[/COLOR].

---

### Post by michael80_oz on 2010-06-06
> **an0dos said:**
> It seems like you are not alone in your frustrations with that wacom tablet. :)

Have you tried the steps outlined here: [http://ubuntuforums.org/showpost.php?p=9119518&postcount=782](http://ubuntuforums.org/showpost.php?p=9119518&postcount=782) ?


I tried that and there seems to be a file missing when i try to run autogen.sh

edit:

michael@michael-desktop:~/Desktop/xf86-input-wacom$ ./autogen.sh --prefix=/usr
./autogen.sh: 9: autoreconf: not found

---

### Post by michael80_oz on 2010-06-07
> **CharlesA said:**
> Linux 2.6.32-22-generic is a Lucid kernel. :)

Checking [here]("https://help.ubuntu.com/community/Wacom"), if you haven't already would be a start. :)


just tried method 1....nothing.

oh btw, is it ok to have the mouse and tablet plugged in at the same time?

---

### Post by Favux on 2010-06-07
Hi michael80_oz,

Follow the directions in this post:  [http://ubuntuforums.org/showpost.php?p=9419773&postcount=1077](http://ubuntuforums.org/showpost.php?p=9419773&postcount=1077)

It's abstracted from the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Ask if you have any more questions.

---

### Post by michael80_oz on 2010-06-07
thanks i'll try it

---

### Post by michael80_oz on 2010-06-07
> **Favux said:**
> Hi michael80_oz,

Follow the directions in this post:  [http://ubuntuforums.org/showpost.php?p=9419773&postcount=1077](http://ubuntuforums.org/showpost.php?p=9419773&postcount=1077)

It's abstracted from the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Ask if you have any more questions.


I get this when checking if it autoloads

michael@michael-desktop:~$ lsmod | grep wacom
wacom                  26872  0

---

### Post by Favux on 2010-06-07
Good, sounds like you did it!  :)

```
wacom 26872 0 
```
Is the wacom.ko, the usb kernel driver.

By the way welcome to Ubuntu forums!

---

### Post by michael80_oz on 2010-06-07
how do i check for that?

thanks :)

---

### Post by Favux on 2010-06-07
I'm sorry, check for what?

Is the tablet working?

---

### Post by michael80_oz on 2010-06-07
> **Favux said:**
> Good, sounds like you did it!  :)

```
wacom 26872 0 
```**Is the wacom.ko, the usb kernel drive**r.

By the way welcome to Ubuntu forums!

how do I check if the usb kernel driver is wacom.ko?

oh...and the tablet isn't working

---

### Post by Favux on 2010-06-07
Hmmm, you did verify the wacom.ko was auto-loading.  All you need to do for the P & T in Lucid is compile a newer wacom.ko than the default wacom.ko.  The default wacom.ko is too old to support the Bamboo P & T's because they are new models.

Was there an error message when you compiled?  You may not have copied all of this line:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

```
Notice it extends far to the right, past the right edge of the box.

Also check if the X driver, xf86-input-wacom is installed.  In Synaptic Package Manager search wacom and you should see that xserver-xorg-input-wacom is installed.

---

### Post by michael80_oz on 2010-06-07
Not sure about compiling a new wacom.ko....

No, there was no error message when I compiled....and yes, I did make sure I had copied the whole line.

Yes, the X driver is installed.

I give up....

---

### Post by Favux on 2010-06-07
Sorry to hear that.  :(

It actually isn't that hard, although it can seem a little overwhelming to a newbie.  Take a few deep breaths and maybe come back to it.

You'll know you had a successful compile if in the unpacked linuxwacom 0.8.6-2 package/tar on your Desktop you look into the /src/2.6.30/ directory and there is now a file called wacom.ko present.  If it is then all you may need to do is repeat the copy (cp) command at the end.

---

### Post by michael80_oz on 2010-06-12
hey Favux, I came back to trying again. Seems that the compile was successful since I checked the /src/2.6.30 directory and yes I can confirm that the wacom.ko is present. I repeated that last command and then to make sure the command was carried out, I navigated to the /lib/modules/2.6.32-22-generic/kernel/drivers/input/tablet folder to confirm that the wacom.ko file did in fact copy to that locaton....and it did.

I have tried having the tablet plugged in as the only usb device and  that failed to work. The strange thing is, that the computer seems to acknowledge it when it's starting up - I see the light of the tablet go off then on.

Do you think if I reformated and installed ubuntu 9.10 would be of great benifit?

---

### Post by Favux on 2010-06-12
Hi michael80_oz,

Welcome back.

You have a mystery on your hands.

Check the dates of the wacom.ko in /src/2.6.30 (right click Properties) and in the /lib/modules/2.6.32-22-generic/kernel/drivers/input/tablet.  They should be the same date and the date when you compiled the wacom.ko.
> Do you think if I reformated and installed ubuntu 9.10 would be of great benifit? 
Well the benefit is you'd be using linuxwacom for the wacom.ko and the wacom_drv.so (the X driver part), rather than Xorg's xf86-input-wacom for the  wacom_drv.so.  They should be functionally equivalent.  Except linuxwacom has wacomcpl (Wacom Control Panel) and the original xsetwacom commands.

What does the output of:
```
xinput --list
```
and
```
xsetwacom list
```
look like?

---

