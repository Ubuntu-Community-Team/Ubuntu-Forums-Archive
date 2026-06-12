---
title: "Eraser Bamboo Pen CTL-470L Ubuntu 11.10"
date: 2011-11-30
forum: Hardware
---

### Post by DMKryl on 2011-11-30
Hello i bought today a wacom Bamboo Pen CTL-470L, i downloaded Chris patch from here 
```
http://sourceforge.net/mailarchive/forum.php?thread_name=CAG1eVf398pnsDJ%2Bfm-hzUwyqJqxBCxVt5E1B%2Bi5wyb2LVj8eEg%40mail.gmail.com&forum_name=linuxwacom-discuss
```

and followed the next instructions

```
sudo apt-get update
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev autoconf libtool
sudo apt-get upgrade
gzip -dc wacom-bamboo.tar.gz | tar xvof -
cd wacom
make -C /lib/modules/$(uname -r)/build SUBDIRS=$(pwd) modules
sudo cp ./wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo depmod -a
```

I restarted the pc and the tablet is working :D, but it doesn't recognize the eraser and sometimes when i'm drawing a line in mypaint it stops drawing and i have to lift the pen to draw again

this is the output from xsetwacom list and xinput list

```
ledah@Elizabeth:~$ xsetwacom list
Wacom Bamboo Connect Pen stylus 	id: 10	type: STYLUS    
Wacom Bamboo Connect Finger touch	id: 11	type: TOUCH     
Wacom Bamboo Connect Pen eraser 	id: 15	type: ERASER    
Wacom Bamboo Connect Finger pad 	id: 16	type: PAD       
ledah@Elizabeth:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen stylus         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Finger touch       	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Pen eraser         	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo Connect Finger pad         	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; CNF7017                                 	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
```

---

### Post by Favux on 2011-11-30
Hi DMKryl,

Does your stylus have an eraser?  I was under the impression the Pens didn't have one.
> sometimes when i'm drawing a line in mypaint it stops drawing and i have to lift the pen to draw again
I suppose this could be a couple of things.  If you are in Oneiric there is a bug in Oneiric's X stack that makes Gimp unusable, maybe this is part of it?  Also there was a follow up thread to the one you link where they noticed occasional stylus pointer jumping.  So Chris changed stuff a little and that's in the patches he submitted to the kernel (and backported to input-wacom?).

---

### Post by DMKryl on 2011-12-01
well i don't know, this is my tablet [http://www.wacom.asia/sites/all/themes/wacomasia/images/bamboo-pen-2011.png](http://www.wacom.asia/sites/all/themes/wacomasia/images/bamboo-pen-2011.png), if it doesn't have well there is nothing i can do :D, but the sudden stop is quite bothersome.

i'm not a gimp user so i don't know, i prefer ps cs2 wine, but tablet don't reach that, if you want i can make a screencast to show you, it stops but is totally random and i have to lift the pen,


This is the kernel i have currently
~$ uname -a
Linux Elizabeth 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux

Do i need to get another kernel? or do i have to wait until the next release?

---

### Post by Favux on 2011-12-01
Can't tell if that is suppose to be an eraser.  I don't think there is any technical reason a Pen stylus couldn't have an eraser, they just don't sell them that way.  For eraser to work you have to use it in programs that support it and assign  erase function to it.

No not another kernel.  Just a compile a different wacom.ko and see if that makes a difference.  Instructions for Chris' backport to input-wacom's wacom.ko are on appendix 3 at the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by DMKryl on 2011-12-01
i compiled the driver from the page, and when i restarted the pc stopped to recognize the tablet, I'm going to erase it and replace it with the old one, thank you for time and answers, i'm not going to mark it as solved yet, i'm going to ask to the program developers

---

### Post by Favux on 2011-12-01
My mistake.  My instructions leave out the -b switch.  So you're cloning the master not the bamboo3 branch.  The line should read:
```
git clone git://github.com/cbagwell/input-wacom.git -b bamboo3
```

---

### Post by DMKryl on 2011-12-10
> **Favux said:**
> My mistake.  My instructions leave out the -b switch.  So you're cloning the master not the bamboo3 branch.  The line should read:
```
git clone git://github.com/cbagwell/input-wacom.git -b bamboo3
```

I didn't saw this :P, then the kernel upgrade broke the tablet compatibility from 3.0.0-13 to 3.0.0-14, i come back to see if anyone had the same problem and this one worked like a charm. also it patched the sudden stop i'm marking this as solved thank you very much favux

---

### Post by Scyth on 2012-01-11
Hi!
Got a question. Just received the bamboo ct-470 as a birthday gift. It is working now with the patch. But I am not so sure about that. When I use it, it constantliy is selecting - just as mouse + left mousbutton pressed. Is this a normal behaviour (not sure, never hat a graphic tablet before)? 
Of course, could test it with windos - but Windows not working   xxxxxxxxxxxxx

Can I use it in the Virtual box? Right now the driver installation is at 50% ... but there was something about hid interface found and drivers installed sucessfully...

edit: oh, justsaw the solved in the title. new thread here: ubuntuforums.org/newthread.php?do=newthread&f=332

---

### Post by Favux on 2012-01-11
These are sort of obsolete instructions.  The patch is now included in input-wacom-0.12.1.  See part I. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").
> When I use it, it constantliy is selecting - just as mouse + left mousbutton pressed.
Not quite sure I know what you mean.  Are you able to use it to draw in a program like Gimp etc.?

---

### Post by Scyth on 2012-01-11
Can I draw? Yes... but I don't believe, that it is working correctly.
Because - how can I describe it? Well... you know, that your can select text in your browser by pressing the left mouse button and move the courser? This is the behaviour I expierience constantly with the bamboo pen.
Or: I can draw in gimp - but I can not NOT DRAW. Got me now? 
Actually I am installing windows to analyse the problem: Is it the hardware or is it the driver for linux...

Edit: The correct link to the new thread was [http://ubuntuforums.org/showthread.php?t=1907405](http://ubuntuforums.org/showthread.php?t=1907405)

Edit2: Ok, just realized something - I may not thouch the display to move the mouse. I finally found it out... the producers should rlly print the detailled guide so it can be read... yeah, w/e. Just one question left. I have the patch installed. Should I follow your howto or will it interfere with the allready applied patch?

---

### Post by Favux on 2012-01-11
No it won't.  I was wondering if what you were seeing could possibly be due to a problem with your application of the patch.  And suggesting you redo it.

Now I'm starting to think you're either having a problem with the TabletPCButton parameter or the Threshold level.  Enter man xsetwacom in a terminal.  Also see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)  from:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

