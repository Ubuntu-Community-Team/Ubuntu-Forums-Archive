---
title: "tx2000 touchscreen"
date: 2009-04-19
forum: Hardware
---

### Post by FracOMac on 2009-04-19
Hey everyone.  I've been trying to get the touchscreen on my friends tablet pc working and I've tried all sorts of instructions to do so on the internet with no luck.  I was wondering if anyone could help us out?  I'd post more info but I really don't even know where to begin.

---

### Post by Favux on 2009-04-19
Hi FracOMac,

Could you post the model you have?  It should be on the plate on the bottom of the laptop.  Also which version of Ubuntu are you running on?

What instructions have you tried?  I'm trying to get an idea if you've made changes to your system.

---

### Post by ddrichardson on 2009-04-19
I had the touchscreen working on a TX1000 series tablet (TX1250ea) but the evtouch driver is no longer on the site I got it from.

My experiences are here FWIW, I had to disable some modules too: [http://wiki.lynxworks.eu/ubuntu/tx1250ea#touchscreen](http://wiki.lynxworks.eu/ubuntu/tx1250ea#touchscreen)

---

### Post by FracOMac on 2009-04-19
Its a tx2000z I believe (I'll have confirmation on that soon) and its running the 9.10 rc (we read somewhere that it had better tablet support).  The instructions we've been trying are from the linux wacom site.

---

### Post by ddrichardson on 2009-04-19
It won't be wacom, it'll be evtouch if its an HP.

---

### Post by FracOMac on 2009-04-19
Pretty sure its wacom, various commands listed it as wacom and this thread: [http://ubuntuforums.org/showthread.php?t=708726](http://ubuntuforums.org/showthread.php?t=708726) did too.

---

### Post by Favux on 2009-04-19
Hi FracOMac,

If it is one of the HP Pavillion TX2000 series it has a Wacom digitizer and touch screen.  You should have a stylus with an eraser and one button.  In addition you will also have touch capability (use of a finger).

If so you are correct and you need the linuxwacom drivers.

---

### Post by FracOMac on 2009-04-19
yup, its got all that but the linux wacom instructions did not work.

---

### Post by Favux on 2009-04-19
OK, but you still haven't answered my question on the model number.  I can help you get it working, no problem.  But I need to know the equipment you have.  As I said it should be on the plate on the bottom.  As an example TX2110us or whatever.  A TX2000 has the nVidia video chipset and a TX2500 has the ATI version.  The new TX2z (although it may not use the z in the model number anymore) touchsmarts have an N-trig digitizer.  But they don't have an eraser.

---

### Post by FracOMac on 2009-04-19
On the bottom it just says tx2000 and he says that he is pretty sure it said tx2000z on his receipt when he bought it.

---

### Post by Favux on 2009-04-19
Dead end there.  Let's try another way.  How old is it?  When did he buy it?  Is there an eraser?  It is a button on the end of stylus that when depressed slides into the barrel of the stylus.  Which video chipset does it have.  If you look in System do you have anything about NVIDIA or ATI?  How about in Hardware Drivers?

I should have mentioned that touchsmart=muti-touch which means a N-trig.

You could also try "lsusb" in a terminal and see if you see Wacom or N-trig.

---

### Post by GoneZombie on 2009-04-19
Hi all, this is my tablet under discussion, so thanks.

So yeah, I bought it May 08, it's definitely wacom and has an active digitizer and touchscreen, the pen has a side button and eraser, and it has an NVIDIA chipset (GeForce Go 6150, I believe)
Thanks,
-GoneZombie

---

### Post by Favux on 2009-04-19
Hi GoneZombie,

Great, you are in luck.  In the last day or two we developed another way to get Wacom working on Jaunty.  As you'll see on this thread:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  You want to read the Jaunty users part near the top.

It may look a little daunting but if you read through you'll see things have actually been broken down pretty well.  Just be patient and read through the HOW TO's before you start.

---

### Post by GoneZombie on 2009-04-20
Woo! It works! Thanks, I feel as exited as that guy in the finallyfast.com commercial, only I didn't just brick my computer!

---

### Post by Favux on 2009-04-20
Congratulations!  Which method did you use?

---

### Post by swarup on 2009-05-04
I have an HP Touchsmart PC IQ524, which I've just purchased. It came with Vista, and I just set up a dual boot with Jaunty 9.04. Most features are working quite well, but the touchscreen does not work. (Also, no sound, and some desktop icons are not taking the proper shape which I take to mean that the video drivers may not be totally functional yet).

My main question for this thread is: what do I have to do to get the touchscreen working for this model?

---

### Post by Favux on 2009-05-04
Hi swarup,

Do you know what the video chipset is?  Do you know what kind of digitizer/touchscreen it has?

The TX2 (was TX2z) touchsmart, is also called the multi-touch.  The multi-touch means it has the N-trig digitizer which supports a stylus and touch (your finger).  Most digitizers in tablet pc's are Wacom.  The N-trig is in the TX2z and Dell Latitude XT (and new XT2).

---

