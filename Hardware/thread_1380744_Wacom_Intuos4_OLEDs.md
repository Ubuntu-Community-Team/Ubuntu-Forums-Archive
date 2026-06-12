---
title: "Wacom Intuos4 OLEDs"
date: 2010-01-14
forum: Hardware
---

### Post by RedDirt6722 on 2010-01-14
Hi all,

Thanks to all the amazingly helpful folk who have taken the time to work it all out, I have been through the threads on here and managed to get my Wacom Intuos4 Medium tablet working in 9.10.

I am still stuck in one last area, though.  I can't work out how to get the little OLED displays working.  I've seen the patches that are available, but the instructions included are, unfortunately, going straight over my head.

Is anyone able to help me with a step-by-step on how to get the OLEDs up and running?  

I am using 9.10 (2.6.31-17).

Thanks.

---

### Post by Favux on 2010-01-14
Hi RedDirt6722,

Welcome to Ubuntu forums!

You don't have to use the patches anymore.  The patches were included in linuxwacom 0.8.5-8.  So you can go to the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") and compile and install 0.8.5-9.  Just remember to replace 0.8.4-4 with 0.8.5-9.

Hope this helps.

---

### Post by RedDirt6722 on 2010-01-14
Favux,

Thank you so much for the quick reply.

I went through that how-to, but unfortunately I had no joy.  For some reason, I now don't have an option in "wacomcpl" to configure the buttons on the tablet (which I did have previously), and the OLEDs still don't work.

Do you have any idea what I might have done wrong?  Any suggestions would be gratefully appreciated.

Cheers.

---

### Post by Favux on 2010-01-14
Hi RedDirt6722,

Ouch!  Even less functionality?

Check in Synaptic Package Manager if xserver-xorg-input-all is installed.  Did you reinstall the new-generic rc2 .fdi?  Were there any errors you noticed when you configured and ran make?  Maybe there's a new dependency needed.

---

### Post by RedDirt6722 on 2010-01-14
Favux,

I've checked, and xserver-xorg-input-all is still installed.  As far as I noticed, there were no errors when I followed the how-to, and yes, I used the generic-rc fdi.

One thing I was thinking is that perhaps when I was trying to get it working myself (prior to creating this thread) I installed a different version of linuxwacom that is conflicting with the new one.  Would I be best served removing everything and starting again?  And if so, how would I go about doing that?

Thanks again for your assistance.

---

### Post by Favux on 2010-01-15
Hi RedDirt6722,

That's a good thought.  Why don't you go through the purge routine with only wacom-tools, skipping xserver-xorg-input-wacom so you don't run into the xserver-xorg-input-all problem.  Then recompile 0.8.5-9 first doing a 'make clean' and probably a 'make distclean' before doing the configure.

Let me know how it goes and what steps you used.

---

### Post by RedDirt6722 on 2010-01-15
Favux,

I went through the purge process listed at the bottom of the how-to, without purging xserver-xorg-input-wacom.

Could you give me a little more detail on the "make clean" and "make distclean" bit?  That part went over my head a bit.  

At what point to I do this, and what do I need to enter in order to do it?  

My apologies if I am being a bit dense here, and thanks again for the help.

Cheers.

---

### Post by Favux on 2010-01-16
Hi RedDirt6722,

Just to clean out your previous compile.  You could also just delete it and download a new linuxwacom source tar.  If you use the previous unpacked source code you compiled in before you'd do the lines right before:
```
./configure --enable-wacom --prefix=/usr
```
So it becomes:
```
make clean
make distclean
./configure --enable-wacom --prefix=/usr
etc.

```

---

### Post by RedDirt6722 on 2010-01-16
Favux,

No luck, unfortunately.  I did as you said, but nothing has changed.  Wacomcpl still doesn't list the pad, and the OLEDs aren't doing anything.

Is there anything else I could try?

Cheers.

---

### Post by Favux on 2010-01-16
Hi RedDirt6722,

Darn.

OK, so a clean compile of 0.8.5-9 on Karmic gives you a working stylus, stylus buttons, and eraser but the pad doesn't work(?) or doesn't show up in wacomcpl(?).  Everying else shows up in wacomcpl and no errors jumping out at you during the compile?

If the pad isn't working does it work in Windows?

If so let's look at your lshal and Xorg.0.log.  For the lshal:
```
lshal>RedDirt6722_lshal.txt
```
And the Xorg.0.log is in /var/log/.  Since both will exceed the upload limit compress them by right clicking and using Create Archive.  Then you can use Manage Attachments to attach them to your next post.

---

### Post by RedDirt6722 on 2010-01-16
Yes.  The stylus and eraser work perfectly and both appear in Wacomcpl, but the pad buttons don't work, the OLEDs don't work and the pad doesn't appear in the Wacomcpl panel.  I also use an XP partition for just such emergencies, and every feature of the tablet works perfectly in XP.

I didn't notice any errors when I was going through the how-to.

I've compressed and attached those files.  Thanks again for your help on this.

---

### Post by Favux on 2010-01-17
Hi RedDirt6722,

There's no indication of your tablet in either file.  I'm puzzled as to how the stylus could be working.

Make sure the new-generic .fdi is in place.  Read Section 1 steps 6) and 7) again in the [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Your trying to make sure the compiled wacom.ko is in place and auto-loading.

---

### Post by RedDirt6722 on 2010-01-17
Favux,

Forgive me if I've got this wrong...

As per the how-to, I'm under the assumption that the way to check if the wacom.ko is in place is to enter: 

```
modinfo -n wacom
```

The output from that is:

```
/lib/modules/2.6.31-17-generic/kernel/drivers/input/tablet/wacom.ko
```

And to check to see if it is auto-loading, the how-to tells me to enter:

```
lsmod | grep wacom
```

The output from that is:

```
wacom                  29124  0 
```

Do I have that right?  Do these indicate that the wacom.ko is there?

---

### Post by Favux on 2010-01-20
Hi RedDirt6722,

Yes, that shows the wacom.ko is there.  Assuming it is the correct wacom.ko it should be working since you have the new-generic .fdi in place.

What could be wrong?  Since the tablet isn't appearing in either lshal and Xorg.0.log it appears usb communication with your tablet isn't being established.  That leads us back to the wacom.ko I guess.  I'm stumped.

Despite everything a conflict between different linuxwacom versions?

---

### Post by Jack005 on 2010-02-02
Hi Favux,

First I am running Intreprid and I did every steps in the post to install the 0.8.5-9 (I had 0.8.4-4 before). Everything is working besides the OLEDs label. The sylus, all the button on the strip are working. I just can't figure out what is missing.

 
Thanks for all the time you put in this. The info is just amazing.

---

### Post by Favux on 2010-02-02
Hi Jack005,

Thank you.

Thanks for confirming 0.8.5-9 is working for you in Intrepid.  It works fine for me in Intrepid also.

As far as the OLED stuff that is suppose to be in there goes, either it doesn't work or maybe there is a new dependency/library required.  Did you see any error/complaint in your configure or make output?

If not I think it's time for Intuos4 users to start making bug reports, either in:

linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

or the bug-tracker:  [https://sourceforge.net/projects/linuxwacom/support](https://sourceforge.net/projects/linuxwacom/support)

This is sort of Urgent because linuxwacom is due out in about a week and the next production version the week after.  And they are under the impression it works!

---

### Post by amicable on 2010-02-04
I've submitted this [to the bug tracker; please add comments]("http://sourceforge.net/tracker/?func=detail&aid=2945959&group_id=69596&atid=525124") if you think they would be helpful:

---

### Post by Favux on 2010-02-05
Hi amicable, Jack005, and RedDirt6722,

I posted on linuxwacom-discuss and got some great responses.  So I've got a handle on what's going on.  The OLED support added to linuxwacom is Nicholas Hirsch's OLED patch for the kernel part of the driver.  To get it working you have to do the rest of the userspace stuff he tells you to do.  Ping Cheng says the code that would needed to be added to the linuxwacom X driver, xsetwacom, and wacomcpl hasn't been done yet.  Although Peter Hutterer may have had an idea to simplify doing it.

First you need to go to Nicholas Hirsch's post on the tracker:  [https://sourceforge.net/tracker/?func=detail&aid=2878608&group_id=69596&atid=525126](https://sourceforge.net/tracker/?func=detail&aid=2878608&group_id=69596&atid=525126)  Then download the "OLED_wacom_patch.tar.gz".  In it you'll find a README and PDF that explain what you need to do.  Of course you don't have to apply the patch to linuxwacom and compile it since it should already be 0.8.5-9.

Jim Henderson pointed out the trick is mounting usbfs and apparently you have to access it through  root.  For some information on usbfs and mounting it see:  [https://wiki.ubuntu.com/KernelTeam/Debugging/USB?](https://wiki.ubuntu.com/KernelTeam/Debugging/USB?)  And it's described in the tar's instructions.

Sanette has been active on the Intuos4 thread and he used the patch and so on and got things working with some changes:  [http://ubuntuforums.org/showpost.php?p=8181190&postcount=169](http://ubuntuforums.org/showpost.php?p=8181190&postcount=169)  I'll quote his post on linuxwacom-discuss:  [https://sourceforge.net/mailarchive/message.php?msg_id=200910282150.07784.san.vu-ngoc%40laposte.net](https://sourceforge.net/mailarchive/message.php?msg_id=200910282150.07784.san.vu-ngoc%40laposte.net)
> Thanks a lot for this patch: I've just compiled and it works !
(I'm on kubuntu 9.04) Wow this is cool.

Some remarks:

the python things did not work well for me, but I found out that using

convert image.png image.gray

and then sending directly image.gray as a raw image works very well - and is
much faster.

Also to make it faster I removed the hardware detection magic. So finally my
rawToWacom.sh script (after initialisation) is just

#!/bin/bash

IMG=$1
BTN=$2

if [ $# -ne 2 ]; then
echo "Usage: ./rayToWacom.sh img.gray button"
exit -1
fi

# Now put it on the device
BUS=002
DEV=009

sudo ./imageToLed $1 /proc/bus/usb/$BUS/$DEV $BTN

############

To sum up: this patch is really nice, and if you save your 8 images in raw
format, then you can easily update all of them in less than one second.
Here's some more links to linuxwacom-discuss posts about it.  If you scan through them you'll see the relevant posts:

[https://sourceforge.net/mailarchive/message.php?msg_id=hc0d7n%244do%241%40ger.gmane.org](https://sourceforge.net/mailarchive/message.php?msg_id=hc0d7n%244do%241%40ger.gmane.org)

[https://sourceforge.net/mailarchive/message.php?msg_id=hc5mcd%243c5%241%40ger.gmane.org](https://sourceforge.net/mailarchive/message.php?msg_id=hc5mcd%243c5%241%40ger.gmane.org)

[https://sourceforge.net/mailarchive/message.php?msg_id=hc5mcd%243c5%241%40ger.gmane.org](https://sourceforge.net/mailarchive/message.php?msg_id=hc5mcd%243c5%241%40ger.gmane.org)

I've just skimmed through this stuff.  If we can't figure this out maybe we can ask Sanette to help us.  Especially if he has tried it out in 0.8.5-8 or 0.8.5-9 and in Karmic.

---

### Post by amicable on 2010-02-05
> **Favux said:**
> Of course you don't have to apply the patch to linuxwacom and compile it since it should already be 0.8.5-9.


I've had a kernel update since I tried this last week. How do I check which linuxwacom version I have running? The applet doesn't have an "about" function and flags like -v or -r don't do anything to wacomcpl.

---

### Post by Favux on 2010-02-05
Hi amicable,

As you know to see the kernel you have you enter:
```
uname -r
```
in a terminal.  A kernel update knocks out a compiled linuxwacom because it creates a new directory without your compiled wacom.ko which means you have to copy the compiled wacom.ko to it.

Linuxwacom (or wacomcpl) won't give a version number.  Apparently because it's really 3 separate packages merged together.  If you have the default Karmic packages they would 0.8.4-1 which you can confirm by searching Synaptic Package Manager with 'wacom'.

If you've compiled linuxwacom (which I think you did) you have to go by the label of the downloaded tar.  Although sometimes Xorg.0.log in /var/log/ will have a version number in it's output.  Not for sure if that's valid though, even if there.

---

### Post by amicable on 2010-02-07
OK, Thanks Favux - using Synaptic was the easiest way to find out. I have the headers, I've done the make etc.  I was confused about which asterisked bit applies to my suituation (karmic, 2.6.31-17-generic-pae) when trying to do [section 6 of the install routine]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1"). 

The only option that works is the one for 2.6.27 since the src file in the dev folder only goes up to 2.6.27.

Now I'm trying to get the scripts in the patch working. If I call the texToWacom.sh I get a series of errors and it wasn't clear (to a non-programmer like me) what to do. The pdf simply says:

> inspect the scripts textToWacom.sh and imgToWacom.sh to see how convert is used

If I try to do a make in the patch directory to compile the c stuff, I get:

> gcc -o imageToLed imageToLed.c
imageToLed.c:15:25: error: wacom_ioctl.h: No such file or directory
imageToLed.c: In function &#8216;set_led&#8217;:
imageToLed.c:27: error: storage size of &#8216;led_img&#8217; isn&#8217;t known
imageToLed.c:42: error: &#8216;WACOM_SET_LED_IMG&#8217; undeclared (first use in this function)
imageToLed.c:42: error: (Each undeclared identifier is reported only once
imageToLed.c:42: error: for each function it appears in.)
make: *** [imageToLed] Error 1

BUT, all you need to do is move the wacom_ioctl.h file into the apps directory before doing the make

I now successfully get text to the tablet - wooo :D

Next to try getting an image across

---

### Post by Favux on 2010-02-07
Hi amicable,

Wow!  Progress!  Great work.

> The only option that works is the one for 2.6.27 since the src file in the dev folder only goes up to 2.6.27.
Right.  Ping Cheng at the LWP removed the 2.6.31 folder with 0.8.5 and the 2.6.28 folder with 0.8.5-6.  That was to simplify things since apparently those folders were there for the bluetooth module not the wacom.ko.

I'm hoping you can put together a HOW TO for others.  Keep it up!

---

### Post by amicable on 2010-02-07
> **Favux said:**
> That was to simplify things since apparently those folders were there for the bluetooth module not the wacom.ko.

I'm hoping you can put together a HOW TO for others.  Keep it up!

I could. But it would probably be full of unnecessary steps given what you say about the ko. I don't know enough to know what to drop - kind of Pavlov's dog.

---

### Post by Favux on 2010-02-07
Maybe we can figure something out together?  Especially if some others drop in to help.  As you can tell my big "adventage" is not being too afraid to look like an idiot.  If you're "shy" just PM me with what you end up with.

---

### Post by amicable on 2010-02-08
Favux, Have no problem sharing whatever the errors :D

I haven't tested this, I just trawled through my bash history and it seems to go like this:

Running mostly as sudo:

[LIST=1]
[*]apt-get install linux-headers-generic
[*]wget -O /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h [http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h](http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h)
[*]make
[*]make install
[*]cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
[*]apt-get install msttcorefonts
[*]mount -t usbfs usbfs /proc/bus/usb
[*]Now d/l and open [the OLED wacom patch]("http://sourceforge.net/tracker/?func=detail&aid=2878608&group_id=69596&atid=525126"). We're using this purely to access the scripts, not the patch itself. Make sure you copy the wacom_ioctl.h from the patches directory into the apps directory. You need to run a make so the c for the ImageToLed (and the left handed script if required) compiles for your machine.
[*]make
[*]./textToWacom.sh hello 8 2 0

The script will write "hello" to the 3rd button down in 8pt using the font specified in the textToWacom script. The 0 at the end is a switch for left hand / right hand afaik.
[/LIST]

It doesn't persist between boots but it does work very well.

I now need to make the OLEDs persist and play with images. Then I need to work out how to get different profiles for different apps - one for Gimp, one for Inkscape etc

---

### Post by amicable on 2010-02-08
.

---

### Post by amicable on 2010-02-08
Using the imgToWacom.sh script I'm able to send a png to the tablet and it works, kind of. I managed to get a grayscale version of the Ubuntu logo appearing on the board. Well, half of the logo, anyway ;) 

> ./imgToWacom.sh a.png 1 0

will send an image called a.png to the second button down in right hand mode

The image should be the right size else it will be scrambled.

Looking at the source code for imageToLed (which imgToWacom invokes), it appears that the OLED buttons are 64 x 32 pixels in size. 

The main problem I have is alignment. Whether using ImgToWacom or textToWacom, alignment/offset seems pretty random; I can't work out the rules from the code.

Still, we're getting somewhere :)

---

### Post by Favux on 2010-02-08
Hi amicable,

Totally sweet!  You're almost there.

Alignment was something others ran into.  See:  [https://sourceforge.net/mailarchive/message.php?msg_id=hc0d7n%244do%241%40ger.gmane.org](https://sourceforge.net/mailarchive/message.php?msg_id=hc0d7n%244do%241%40ger.gmane.org)  Start with this post:
>   	
Re: [Linuxwacom-discuss] OLED/Express Keys Support Patch: Please try it!
From: Jim Henderson <hendersj@gm...> - 2009-10-25 04:27
On Sun, 25 Oct 2009 04:10:30 +0000, Jim Henderson wrote:

> One thing that I'm having a little trouble with, though, is resetting
> the values to just black - it seems that if I pass a plain black image
> in, I get garbage on the OLED display. I think it's an artifact of the
> imgToRaw.py script, will try converting something else. What format is
> the tmp.out file in? Is it just an RLE-encoded bmp, or something else?

I found that if I removed the manipulation of the image to center the
text (since I'm using Gimp to create the buttons, the centering logic
isn't necessary for me), that solved this issue.

Jim

Then a couple posts down Jim gives three scripts and a perl script and says: 
```
I've also modified Nick's scripts to include absolute paths to each other
in the ~/bin directory on my system, and removed from imgToRaw.py to
remove the code that tries to center the images; my pngs are all just
64x32 with no comssion.
```
So you could ask him for help.  I think the centering code he's talking about starts under:
> # we want to preprocess some data to center the text

---

### Post by amicable on 2010-02-08
OK, so it seems from that thread that the Python script attempts to centre text and doesn't do it consistently for some reason.

If you're building your own 64 x 32 image then there's no need for any centring. I'm sure most of us using these tablets will be geeky enough to want to use a nice 64 x 32 icon. Soon enough nice ones will be shared for the Intuos4.

Meantime, I have no idea how to circumvent the python script to avoid the centring - the code is beyond me. I can see what this is doing. It is another matter to meddle with it ;)

Here it is in case anyone knows a little Python and can help:

> #!/usr/bin/python

import sys
import Image
import struct
import numpy
import matplotlib
import pylab

def bufToImage(buf, w, h):
	buf3 = []
	for i in range(h):
		buf3.append([])
		for j in range(w):
			buf3[i].append([])
			buf3[i][j] = buf[i*w + j]
	
	pylab.imshow(buf3)
	pylab.show()

def getPixelCenter(buf, w, h, maxval, chunks):
	vert = []
	for j in range(h):
		tot = 0.0
		vert.append([])
		for i in range(w):
			val = buf[j*w + i]
			for k in range(int(val/maxval / (1.0/chunks))):
				tot += 1
				vert[j].append(i)
		vert[j] = int(numpy.sum(vert[j]))
		if tot == 0:
			vert[j] = -1
		else:
			vert[j] = int(vert[j]/float(tot))
	tmp = []
	for j in range(h):
		if vert[j] == -1:
			pass
		else:
			tmp.append( vert[j] )
	return int(numpy.average(tmp))

MAXVAL = 15
CHUNKS = 10 
def getXAverage(buf, w, h):
	return getPixelCenter(buf, w, h, MAXVAL, CHUNKS)

def transposeBuf(buf, w, h):
	buf2 = []
	for i in range(w*h):
		buf2.append(0)
	for i in range(w):
		for j in range(h):
			buf2[i*h + j] = buf[j*w + i]
	return buf2

def getYAverage(buf, w, h):
	buf2 = transposeBuf(buf, w, h)
	return getPixelCenter(buf2, h, w, MAXVAL, CHUNKS)

def process(rgb):
	return int((rgb[0] + rgb[1] + rgb[2])/3 >> 4)

def offsetImg(buf, w, h, xOffset, yOffset):
	buf2 = []
	for i in range(w*h):
		buf2.append(0)

	for i in range(h):
		for j in range(w):
			val = buf[i*w + j]
			if (j + xOffset < 0 or j + xOffset >= w):
				pass
			else:
				buf2[i*w + j+xOffset] = val
	buf3 = []
	for i in range(h*w):
		buf3.append(0)
	for i in range(h):
		for j in range(w):
			val = buf2[i*w + j]
			if (i + yOffset < 0 or i + yOffset >= h):
				pass
			else:
				buf3[(i+yOffset)*w + j] = val
	return buf3


#################### Main ####################

filename = sys.argv[1]

#f = open(filename, "rb")
im = Image.open(filename)

outfile = open("tmp.out", "wb")

width = im.size[0]
height = im.size[1]

# we want to preprocess some data to center the text

buf = []
for j in range(height):
	for i in range(width):
		val = im.getpixel((i,j))
		val = process(val)
		buf.append(val)


xAvg = getXAverage(buf, width, height)
xOffset = ((int(width/2.0)) - xAvg)

yAvg = getYAverage(buf, width, height)
yOffset = ((int(height/2.0)) - yAvg)

buf2 = offsetImg(buf, width, height, xOffset, yOffset)

for i in range(height):
	for j in range(width):
		val = buf2[i*width + j]
		s = struct.pack("@B", val)
		outfile.write(s)

outfile.close()

Just to clarify, this Python is called by imgToWacom; it produces a file called tmp.out which is processed by imageToLed and sent to the Intuos4.

---

### Post by Favux on 2010-02-08
Hi amicable,

We can apply the BFMI principle.

I'm pretty sure this is what we want to get rid of:
```
xAvg = getXAverage(buf, width, height)
xOffset = ((int(width/2.0)) - xAvg)

yAvg = getYAverage(buf, width, height)
yOffset = ((int(height/2.0)) - yAvg)

```
Looking at the rest of it my guess is you can get rid of:
```
# we want to preprocess some data to center the text

buf = []
for j in range(height):
	for i in range(width):
		val = im.getpixel((i,j))
		val = process(val)
		buf.append(val)


xAvg = getXAverage(buf, width, height)
xOffset = ((int(width/2.0)) - xAvg)

yAvg = getYAverage(buf, width, height)
yOffset = ((int(height/2.0)) - yAvg)

buf2 = offsetImg(buf, width, height, xOffset, yOffset)

for i in range(height):
	for j in range(width):
		val = buf2[i*width + j]
		s = struct.pack("@B", val)
		outfile.write(s)
```
You could try that and see if it breaks it.  Which should be the worst that can happen.

---

### Post by amicable on 2010-02-08
It goes through but delivers a scrambled button, looking similar to what happens when the image isn't the right size.

---

### Post by amicable on 2010-02-08
But this change works a treat:

> xAvg = 64
xOffset = 0

yAvg = 32
yOffset = 0

:D

---

### Post by Favux on 2010-02-08
Dooooh!

Sure, and if the other models are different sizes easy to change.  Clever!  :D

---

### Post by amicable on 2010-02-09
> **Favux said:**
> Dooooh!

Sure, and if the other models are different sizes easy to change.  Clever!  :D

I now have 8 tiny grayscale images as my OLED buttons :cool:

Of course, hacking this mucks up the texttoimage script but you could easily rename them so you have two different sets. I'm not going to bother until I can work out a way of getting these things onto the tablet each time I boot. 

It'd be really nice to have a simple loop script that fires off the right commands. You'd put it in the System->Prefs->Startup Apps menu for boot time. You could have a default set for Gimp in there and then another script to set up buttons for Inkscape,  OpenOffice, Ardour etc. I know it'd be a really simple thing to do but I can't programme that sort of stuff. I could definitely hack it once seen but writing the initial thing is beyond me.

By the way, some of the steps I wrote earlier are redundant. The scripts already contain a line to mount the USB, so you don't need to do that. Installing MS core fonts isn't mandatory - just open the relevant text script and make sure it's pointing to a ttf font somewhere on your system.

So here's a simplified routine (again, I'm not 100% sure all the steps are written out accurately, I just flicked through my bash history and copied what I thought was relevant)

[LIST=1]
[*]apt-get install linux-headers-generic
[*]wget -O /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h [http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h](http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h)
[*]make
[*]make install
[*]cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
[*]d/l and open [the OLED wacom patch]("http://sourceforge.net/tracker/?func=detail&aid=2878608&group_id=69596&atid=525126"). We're using this purely to access the scripts (in the apps folder), not the patch itself.
[*]Copy the wacom_ioctl.h from the patches folder into the apps folder 
[*]make (this complies the ImageToLed.c (and the left handed script if required))
[*]Ensure that line under ##### Render font ##### in the textToWacom.sh script points to a valid ttf font on your system.
[*]./textToWacom.sh hello 8 2 0
[/list]

"hello" is your text. Don't use spaces; it'll mess up the code.
"8" is your font size (depending on your label length, 8-22pt work well; some fonts are pretty unreadable at 8. I'd advise choosing a good system ttf font that resolves well at low pixel sizes)
"2" is button #3 (they go from 0-7)
"0" is right handed ("1" gives you left handed)

---

### Post by Favux on 2010-02-09
Outstanding amicable!

Now you can just keep adding to this post as you learn more and others contribute and you have your HOW TO!

---

### Post by sanette on 2010-02-10
Hi everybody, I'm back...

so it seems that other people are trying the LED stuff
very good !

I have tried to compile the lastest linuxwacom-0.8.5-9
and it works very well.

(I have my small animation of Tux walking ;) )

It would be great to remove the python dependency
and make it more user friendly

---

### Post by sanette on 2010-02-10
In case anybody wants to try, I share my small Tux images.
(see the attachment)


If you are lucky just untar, go in the walking-tux directory run
```
./walking-tux.sh
```
and it works.
(I include the **imageToLed** program, compiled under karmik 64bit)

---

### Post by Favux on 2010-02-10
Hi sanette,

Welcome back!

Do you have any suggestions for amicable to streamline or simplify his steps?  Or make them clearer if they need amplifying?  Any changes he/we could make to the scripts?

Could you post your Tux image samples?

> It would be great to remove the python dependency
and make it more user friendly 
It's still the case that no one has found time to do that.  Between my post on linuxwacom-discuss and amicable's bug report on the bug tracker they have been reminded of the OLED's.

Right now the dev.s are considering/planning on splitting wacomcpl out from linuxwacom so it is stand alone.  That's so folks with Xserver 1.7 (Lucid etc.) and xf86-input-wacom will have it available to them also.  They are looking for someone to take on the project and then maintain wacomcpl.  If someone steps forward that would be an opportunity to lobby them for OLED inclusion.

Edit:  Oops, you beat me with Tux!  :)

---

### Post by sanette on 2010-02-10
Hi Favux

I'm not sure I can help. The crucial steps for me were to copy
the file **hid-ids.h** at the proper place (as indicated in point 2. of amicable)
then

```
./configure --enable-wacom
make
```

and copy wacom.ko at the proper place.

The **imageToLed** was compiled in my first attempt with 8.4-3 so I don't
remember exactly, but it was probably just a **make**.

Then I do remember I had to change the **textToWacom.sh** and **imgToRaw.py** to remove centering.

Then, for gimp I use the script:
```
#!/bin/bash

cd $HOME/systeme/wacom/apps


./textToWacom.sh "Switch" 20 0 1
./textToWacom.sh "Quit" 24 1 1
./textToWacom.sh "Outils Gimp" 10 4 1
./textToWacom.sh "MAJ" 24 5 1
./textToWacom.sh "CTRL" 24 6 1
./textToWacom.sh "ALT" 24 7 1

```

I am attaching my **textToWacom.sh** and **imgToRaw.py**

---

### Post by Favux on 2010-02-10
Hi sanette,

That's big help.  Now we know how to "properly" fix imgToRaw.py to remove centering!  Thanks!

And textToWacom.sh and the script are also quite helpful.

Getting closer to a HOW TO more folks can follow.

---

### Post by sanette on 2010-02-12
following the idea of amicable, I'm hacking some scripts to save the button images so that you can restore them quickly when you restart the computer (or simply when you unplug/plug the USB cable)

---

### Post by Favux on 2010-02-12
Hi sanette,

That would be slick!

---

### Post by amicable on 2010-02-12
> **sanette said:**
> I'm hacking some scripts to save the button images

Would love to see that sanette

---

### Post by sanette on 2010-02-14
Aah, I have worked hard ! :popcorn:

Here is a "package" with scripts to set LEDs, save profiles, restore profiles.

Untar in $HOME/bin

(it should put everything under $HOME/bin/intuos)

Please test if it works for you. Give me your ideas and suggestions !


PS: here is the (long) README:

[SIZE="1"]
[COLOR="Red"]*VERSION 2010-03-08*[/COLOR]
------------------



Depends on imagemagick
(a recent version is better for proper text adjustment)

Needs xterm too

python-matplotlib is *not* needed anymore


INSTALLATION

1. make binaries
----------------

make

2. the xinput name of the pad is assumed to be the last entry in
`xinput list --short` containing the letters "pad". If not, you should
modify the scripts (each occurence of an "xsetwacom" invocation)...

3. the scripts have to be in the same directory. This directory is
assumed to be $HOME/bin/intuos. But it can be put anywhere else if you
wish ! You only need to modify following line in the scripts
"wacom-intuos" and "intuos-select-profile.sh":

oled_dir=$HOME/bin/intuos



USE


1. setup you buttons:
---------------------

* for keybindings: use wacomcpl or

xsetwacom set pad Buttoni "key code"

The buttons corresponding to the 8 LEDS are
Buttoni = "Button2", "Button3", ..., "Button9"

* put text on LEDs using

./textToWacom.sh text fontsize button [left_handed]

(Use "fontsize" 0 for automatic fit. "left_handed" is optional --
should be automatically detected)

The "button" parameter corresponding to the 8 LEDS are
0, 1, 2, ..., 7
"left_handed" is 0 or 1

* put images on LEDs using

./imgToWacom.sh image button left_handed

"image" can be any image in any format. Of course best if already of size 64x32.
Otherwise it will be scaled, without keeping aspect ratio, to fit in 64x32.


2. save your setup:
-------------------

Once you're satisfied, save your setup with

./intuos-save-buttons.sh default

(You can use any identifier instead of "default". For instance,
"gimp", "inkscape", etc.)

3. restore your setup:
----------------------

You restore everything (images+keybindings) using

./intuos-restore-buttons.sh default

(Replace "default" with the profile identifier you want to restore)

You can also use a very basic GUI for this !

./intuos-select-profile.sh

(should work both with KDE -- using kdialog -- or GNOME -- using zenity)
Suggestion: bind this program to the central round button of the tablet !
You can do this like this:
xsetwacom set pad Button1 "CORE KEY CTRL SHIFT print"
and then use your system settings to bind "Ctrl Shift Print" to $HOME/bin/intuos/intuos-select-profile.sh

Remark
------

Step 2. is in fact optional ! By default, everything is automatically
saved under the profile "last". Then you can use

./intuos-restore-buttons.sh

(without any argument) to restore this.

Automatic restore
-----------------

the script "wacom-intuos" is (hopefully) appropriate to be launched at
session start-up to restore the previous settings. It uses xterm for asking "sudo" because I could not get it working properly with kdesudo...


Images
------

You can use the image "tux.png" for testing.

The image "black.png" is useful for erasing an image !



[/SIZE]

---

### Post by sanette on 2010-02-14
PPS:

minimal example of use:

```
cd $HOME/bin/intuos
```

```
./imgToWacom.sh tux.png 0
```

The small tux should appear on the first button !

Then plug out the USB cable, plug it in again, and

```
./intuos-restore-buttons.sh
```

Small tux should be here again !


Have fun

---

### Post by Favux on 2010-02-14
Hi sanette,

**[SIZE="3"]Awesome!!![/SIZE]**  :D

Thank you for all the hard work!

---

### Post by amicable on 2010-02-15
> **sanette said:**
> 2. the xinput name of the pad is assumed to be "pad". If not, you should modify the scripts (each occurence of an "xsetwacom" invocation)...


My pad seems to be called "stylus pad"

> xinput list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"stylus"	id=3	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 44704
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 27940
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
"stylus pad"	id=4	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 9
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 44704
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 27940
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 4 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 5 :
		Min_value is 0
		Max_value is 71
		Resolution is 1
"stylus cursor"	id=5	[XExtensionKeyboard]
	Type is Wacom Cursor
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 44704
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 27940
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
	Axis 4 :
		Min_value is -1023
		Max_value is 1023
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"eraser"	id=6	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 44704
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 27940
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Power Button"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=9	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Dell Dell USB Optical Mouse"	id=10	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1


How do I put that in imgToWacom.sh ?
> rotate=$(xsetwacom get pad rotate)

The command can't take a name with spaces and I don't know how to deal with it.

Also, for me wacomcpl doesn't give me access to the keybindings - I just have stylus and eraser appearing.

---

### Post by Favux on 2010-02-15
Hi amicable,

You could try:
```
"stylus pad"
```
with the quotes instead of pad.

You're in Karmic with the default 0.8.4-1 linuxwacom, correct?  Which .fdi are you using?

---

### Post by sanette on 2010-02-16
yes, "stylus pad" with quotes should do it.

Favux, do you know a way to detect this automatically ?

---

### Post by sanette on 2010-02-16
**amicable**, I think that your wacomcpl does not show you the pad for the same reason: it does not like the name "stylus pad" !

You should try change your 10-linuxwacom.fdi to get a "pad" instead of "stylus pad".

Probably Favux knows how to do this

---

### Post by Favux on 2010-02-16
Hi sanette,

I was hoping the wacomcpl in the new 0.8.5-10 would do that.  At least the device names now show up in the wacomcpl list but if you click on them none of the feature options for the device show up.  So I don't think it works yet, although maybe we're just missing something.


Hi amicable,

Like sanette suggests if you want to see if a modified .fdi will help you, you could take a look at [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").  There is a link in there to configure the Intuos4 pad.

---

### Post by sanette on 2010-02-16
**Favux**,

do you think a sed magic like this below is OK for detecting the name of the pad device ?

It assumes there is only one entry in xinput with the name "pad" in it
(without capitals). (if there are more than one, it takes the last one)
 Does this sound reasonable to you ?


```
pad=$(xinput list --short | sed -n 's|\(\"*.pad*.\"\).*|\1|p' | tail -1)
rotate=$(xsetwacom get $pad rotate)
```

---

### Post by Favux on 2010-02-16
Hi sanette,

That should work for the Intuos4 using the usb .fdi (Jaunty ext graphics).  I think it will work for the new-generic .fdi too.  I don't think the info.callout to hal-setup-wacom on 'if1' will generate a spurious pad for the Intuos4 because IIRC it is only on 'if0'.  That's in there for the new Bamboo P & T's, which have (had?) their pad on 'if1'.

It may not work for the default .fdi's linuxwacom is putting out.

---

### Post by amicable on 2010-02-16
Hi Favux, Sanette

OK, I'm a little confused; there are too many posts to follow, some referring back to older situations and kernel versions.

My 10-linuxwacom.fdi has no mention of "stylus pad" (it is the one from 	Favux_new-generic_rc2_10-linuxwacom.fdi.txt)

My xsetwacom --version is 0.2.3

I'm using Karmic 2.6.31-17-generic-pae

My /etc/X11/xinit/xinitrc is fully commented out

Where / how should I replace the words "stylus pad" which appear in my xinput list?

---

### Post by Favux on 2010-02-16
Hi amicable,

Could you try the first .fdi in post #176?  The one that has Jaunty in the name?  Then let's see your 'xinput --list' output again.  Hopefully it will just say pad.  And if you have a Wacom mouse for your Intuos4 it should just say cursor, not "stylus cursor".  By the way which version of linuxwacom do you have installed?

---

### Post by amicable on 2010-02-16
Using your first fdi xml ([Favux_Jaunty ext graphics_test 2_10-wacom.fdi.txt]("http://ubuntuforums.org/attachment.php?attachmentid=112835&d=1241728139")), my xinput seems fixed. I now get stylus, pad, cursor and eraser to play around with :)

Sanette's version of the text and image send scripts are working well

Next I'll try Sanette's save and restore scripts and then try and do a couple of configurations for different apps and see if I can switch easily.

Thanks to both of you; it's progressing really well =D>

btw I think I'm using the linuxwacom default. How do I check?

---

### Post by Favux on 2010-02-16
Hi amicable,

Sounding good!  :)

I think the only way is to look in Synaptic Package Manager.  Or if you've compiled one look at the tar label.  There's no commmand to get linuxwacom to identify it's version.  Sometimes you'll see a version in Xorg.0.log in /var/log but I'm not sure how accurate that is.

---

### Post by amicable on 2010-02-16
wacom-tools is showing in Synaptic as 1.0.8.4.1-0ubuntu4 and so is xserver-xorg-input-wacom. I guess these are the distro defaults for Karmic. I remember I only d/l'd the patch to get at the scripts.

---

### Post by sanette on 2010-02-17
I just updated my post #44 to include the 'sed detection' and
corrected a bug in wacom-intuos.

I can't test right now since I am away from my tablet...

---

### Post by amicable on 2010-02-17
Sanette, I installed the new set of scripts & did a make

Both text and image work but they also write out an error to the terminal:

> Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '"pad"'

---

### Post by sanette on 2010-02-17
Hi amicable

mmm. I think I know what causes this. There are too many quotes. I suppose if you try

```
xsetwacom get "pad" rotate
```

it works ?

---

### Post by sanette on 2010-02-17
Hi amicable

I have updated intuos_2010-02-17.tar.gz  in my post [#44]("http://ubuntuforums.org/showpost.php?p=8826476&postcount=44")

Does it work now ?

---

### Post by amicable on 2010-02-17
> **sanette said:**
> Hi amicable

mmm. I think I know what causes this. There are too many quotes. I suppose if you try

```
xsetwacom get "pad" rotate
```

it works ?

I don't know what the command is supposed to do, but terminal just shows up 

> 0

---

### Post by amicable on 2010-02-17
> **sanette said:**
> Hi amicable

I have updated intuos_2010-02-17.tar.gz  in my post #44

Does it work now ?

Maybe I messed sthg up but I can't make the new package. I get

> make: Nothing to be done for `all'.

and then I get

> ./imgToWacom.sh tux.png 8 0
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device '"pad"'
Couldn't update LEDs


but probably it's because make didn't work.

---

### Post by sanette on 2010-02-18
Hi amicable

be sure you remove the old intuos directory before unpacking a new archive.

Btw I posted yet again another version...

---

### Post by amicable on 2010-02-18
> **sanette said:**
> Hi amicable

be sure you remove the old intuos directory before unpacking a new archive.

Btw I posted yet again another version...

ok, this one make's. 

and it works with both text and images :)

I haven't tested the save functions yet...

---

### Post by sanette on 2010-02-19
Hi amicable

very good !

for the save/restore, could you just test the following:
(after setting some text/images to the tablet LEDs)

*unplug the tablet

*plug it again

*then issue the command (in the "intuos" directory)

```
./intuos-restore-buttons.sh
```

then the images you had on the LEDs should be restored

---

### Post by amicable on 2010-02-19
interesting

It didn't restore the setup I just created 2 mins ago but restored what I had before I shut down last night 

Nice :)

---

### Post by sanette on 2010-02-19
interesting indeed ;)

when you created your setup 2min before unplugging, did
you only use the scripts

imgToWacom.sh and textToWacom.sh ?

(the program imageToLed should not be used directly)

Did you have any error message ?

---

### Post by amicable on 2010-02-19
Here's the output in full fyi. I didn't try the text:

> paul@paul-desktop:~/bin/intuos$ ./imgToWacom.sh tux.png 1 0
paul@paul-desktop:~/bin/intuos$ ./intuos-restore-buttons.sh
Profile: last
Updating image for button 0... done. xf86WcmDecodeAction No action defined
Code for button 0 is: ""
Updating image for button 1... done. xf86WcmDecodeAction No action defined
Code for button 1 is: ""
Updating image for button 2... done. xf86WcmDecodeAction No action defined
Code for button 2 is: ""
Updating image for button 3... done. xf86WcmDecodeAction No action defined
Code for button 3 is: ""
Updating image for button 4... done. xf86WcmDecodeAction No action defined
Code for button 4 is: ""
Updating image for button 5... done. xf86WcmDecodeAction No action defined
Code for button 5 is: ""
Updating image for button 6... done. xf86WcmDecodeAction No action defined
Code for button 6 is: ""
Updating image for button 7... done. xf86WcmDecodeAction No action defined
Code for button 7 is: ""


---

### Post by sanette on 2010-02-19
mmm. this output looks normal to me.

and then the tux image was not restored ?

This is weird.

You did not change user by any chance (no sudo ?)

---

### Post by amicable on 2010-02-19
I ran as the same user. If I sudo the script, I get the same result:

> paul@paul-desktop:~/bin/intuos$ sudo ./intuos-restore-buttons.sh
[sudo] password for paul: 
Profile: last
Updating image for button 0... done. xf86WcmDecodeAction No action defined
Code for button 0 is: ""
Updating image for button 1... done. xf86WcmDecodeAction No action defined
Code for button 1 is: ""
Updating image for button 2... done. xf86WcmDecodeAction No action defined
Code for button 2 is: ""
Updating image for button 3... done. xf86WcmDecodeAction No action defined
Code for button 3 is: ""
Updating image for button 4... done. xf86WcmDecodeAction No action defined
Code for button 4 is: ""
Updating image for button 5... done. xf86WcmDecodeAction No action defined
Code for button 5 is: ""
Updating image for button 6... done. xf86WcmDecodeAction No action defined
Code for button 6 is: ""
Updating image for button 7... done. xf86WcmDecodeAction No action defined
Code for button 7 is: ""
 

Now I just made a change and unplugged for 5 seconds.

When I plug back in and restore, I get my recent changes.

So the behaviour appears unpredictable. I will try and work out what the pattern is.

---

### Post by sanette on 2010-02-19
in principle these scripts should **not** be run with sudo,
because the backups are stored in the HOME directory, and this would
be the "root" directory if run with sudo !

---

### Post by amicable on 2010-02-19
> **sanette said:**
> in principle these scripts should **not** be run with sudo,
because the backups are stored in the HOME directory, and this would
be the "root" directory if run with sudo !

Indeed, this is what I thought. I had no need or intention to sudo. Anyhow, let me know if you want me to test anything else. 

I haven't got round to getting the button functions doing something purposeful yet. Has anyone done a set for eg Gimp?

---

### Post by sanette on 2010-02-19
Hi amicable

sure, for Gimp the buttons can be very useful. 

For instance here is my .wacom/gimp/bindings:

# Button bindings for gimp
key0="CORE KEY  ALT"
key1="CORE KEY  CTRL"
key2="CORE KEY  SHIFT"
key3="CORE KEY  CTRL b"
key4="6"
key5="7"
key6="CORE KEY  CTRL q"
key7="CORE KEY  ALT  Tab"


As mentioned in one of my previous posts, I used this to set up the LED for the first time:

./textToWacom.sh "Switch" 0 0
./textToWacom.sh "Quit" 0 1
./textToWacom.sh "Gimp tools" 0 4
./textToWacom.sh "SHIFT" 24 5
./textToWacom.sh "CTRL" 24 6
./textToWacom.sh "ALT" 24 7



If you want to try this, you can just issue the textToWacom commands above, then copy the "bindings" files to $HOME/.wacom/last/bindings
and then
```
./intuos-restore-buttons.sh
```

---

### Post by irah.000 on 2010-02-20
Should this work with xf86-input-wacom?

---

### Post by amicable on 2010-02-21
@ Sanette Great, this is working well. I noticed I have Wacom Tablet Calibration Settings which is calling .xinitrc from my home directory on startup (maybe this is from an old attempt at getting the tablet going). Do I need to adjust this to get the whole thing to load on boot?

---

### Post by sanette on 2010-02-22
Hi amicable

I'm glad you can make it work too !

Concerning .xinitrc, if it contains only calibration data (and not keybindings), then you can safely load it at boot time (together with $HOME/bin/intuos/wacom-intuos for the button stuff).

If it contains keydindings, then I think you should either remove them from this file or at least make sure the file with the keybindings you want is loaded last at boot time.

Tell me how it goes

---

### Post by sanette on 2010-02-22
oh, maybe I did not answer your question. To make it clear

if you want the OLED button scripts to be loaded at boottime, then

* either you go to your system preferences and add the script
$HOME/bin/intuos/wacom-intuos
to be loaded on startup

* or (I haven't tested this one) you add the line

```
$HOME/bin/intuos/wacom-intuos
```

at the end of your .xinitrc file (assuming you trust the fact that this file is loaded on startup.)

---

### Post by sanette on 2010-03-07
:o

after upgrading to 2.6.31-20 kernel, it's impossible to set LEDs !

(something broken with usbfs)

any idea ?

for the moment I have to downgrade to 2.6.31-19...

---

### Post by amicable on 2010-03-10
It's broken for me, too, since upgrading the kernel last night :(

---

### Post by ollinwing on 2010-03-13
Favux, amicable, and sanette, 

I'm a linux noob. I just did away with windows7 and installed ubuntu two days ago and I love the system so much that I changed my laptop over as well. I'm an art student. Long story short, I absolutely need my intuos4 to work but I have no clue what you guys are talking about. I've learned a lot just wading through the forum so far and I'm not trying to get in the discussions way at all but I do have a question. 

Is it necessary for me to switch from Karmic Koala down to Jaunty so I can follow along more completely? If so I think I can manage that part well enough on my own. Also I'm having the same problems with Karmic in that the tablet isn't reading like it should in gimp (in other words I have no LEDs except for the single turntable which represents the zoom function).

Anyway, don't give in to the stress of it guys! *I almost threw the tablet because my brain was on fire trying to speed learn all of this* Anywhosit! My art career depends upon your knowledge! Keep up the good work and I'll follow along quietly from now on and try not to get in your way.

~ollin~

---

### Post by amicable on 2010-03-13
ollinwing, the tablet should work fine without the oleds - they're just eye candy for me. Despite the oled stuff breaking, the rest of the functions work perfectly.

---

### Post by ollinwing on 2010-03-13
yeah everything's fine but the oleds and except that I can't tell what the turntable functions are because they're not registering in gimp. I'll go back through the discussion right quick in case I missed something crucial. I prolly did because I was reading other forum material along with this in order to understand a lot of what was going on with ubuntu. Multi-task reading leads to muchos confusion. 

~ollin~

---

### Post by ollinwing on 2010-03-13
nevermind. lemme try this out. There are a lot of threads for this conversation lol.

---

### Post by sanette on 2010-03-14
ollinwing, I'm not sure exactly what you mean.

There are 2 things: the buttons and the OLEDS.

even if the oleds show nothing, you can still use the buttons.

you set them to any key combination you want, for instance one that is recognized by gimp !

(Personally, I use "ALT", "CTRL", "SHIFT", "CTRL b" quite often in gimp, so I have bound them to some of the Intuos buttons)

---

### Post by elefantcrossing on 2010-03-18
Hi! I'm trying to get this to work on lucid but there is no /proc/bus/usb
so usbfs can't be mounted

any ideas how to fix this?

and what happened to usbfs?

---

### Post by vitku on 2010-03-18
From another thread ([http://ubuntuforums.org/showthread.php?t=1383457](http://ubuntuforums.org/showthread.php?t=1383457))
> **GameManK said:**
> Looks like it's not supposed to work:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507824)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274)

Apparently usbfs mounts are broken for now. Reading the comments - it seems booting to kernel <.17 could do the trick.

---

### Post by Favux on 2010-06-11
Hi everyone,

Discouraging news about usbfs.  According to this launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274)  there is a "workaround".  Something on the order of:

  mkdir /dev/bus/input /dev/bus/pccard /dev/bus/pci
  (basically anything you see under /proc/bus)

  mount --bind /proc/bus/input /dev/bus/input
  mount --bind /proc/bus/pccard /dev/bus/pccard
  mount --bind /proc/bus/pci /dev/bus/pci

  mount --bind /dev/bus /proc/bus

  ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices

Mileage will for sure vary.

---

### Post by sanette on 2010-06-12
Hi Favux

unfortunately this workaround doesn't work for me :(

---

### Post by -Zeus- on 2010-06-17
> **Favux said:**
> Hi everyone,

Discouraging news about usbfs.  According to this launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274)  there is a "workaround".  Something on the order of:

  mkdir /dev/bus/input /dev/bus/pccard /dev/bus/pci
  (basically anything you see under /proc/bus)

  mount --bind /proc/bus/input /dev/bus/input
  mount --bind /proc/bus/pccard /dev/bus/pccard
  mount --bind /proc/bus/pci /dev/bus/pci

  mount --bind /dev/bus /proc/bus

  ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices

Mileage will for sure vary.

I'm also having the usbfs problem, any workarounds?  I tried your commands.

---

### Post by Favux on 2010-08-22
Hi everyone,

Good news!

Christoph Karg has written a new OLED applet in C using libusb to communicate with the tablet and Magick++ to deal with the images/icons.  It's for the Intuos4 M, Product ID 0x00b9.  But if you have another Intuous4 with a different product number it looks like all you need to do is add it to the defines in WacomIntuous4LED.cpp under line 19, basically copying it.  And substitute the Product ID for yours at line 16 in intous4-led-check.cpp.

See his post at linuxwacom-devel:  [https://sourceforge.net/mailarchive/forum.php?thread_name=201008211203.59754.wacom%40kargulus.de&forum_name=linuxwacom-devel](https://sourceforge.net/mailarchive/forum.php?thread_name=201008211203.59754.wacom%40kargulus.de&forum_name=linuxwacom-devel)  The applet is in the attachment.  Icons are included.

---

### Post by amicable on 2010-08-23
I'm sure I can make this work with a little help. After installing the libs and doing a make, I try the tablet check and get:

> intuos4-led-check: command not found


The file is there, though... here are all the files I have in the src directory

> icon-library.cpp        intuos4-led-check.o     set-intuos4-leds.sh
icon-library.o          intuos4-led-config      WacomIntuos4LED.cpp
init-intuos4-tablet.sh  intuos4-led-config.cpp  WacomIntuos4LED.h
intuos4-led-check       intuos4-led-config.o    WacomIntuos4LED.o
intuos4-led-check.cpp   Makefile


I do now have labels for the buttons on my pad: *Button1, Button 2,....* So that's cool. 

Any ideas? I'm using the Intuos4 M, by the way.

Thanks

> **Favux said:**
> Hi everyone,

Good news!

Christoph Karg has written a new OLED applet in C using libusb to communicate with the tablet and Magick++ to deal with the images/icons.  It's for the Intuos4 M, Product ID 0x00b9.  But if you have another Intuous4 with a different product number it looks like all you need to do is add it to the defines in WacomIntuous4LED.cpp under line 19, basically copying it.  And substitute the Product ID for yours at line 16 in intous4-led-check.cpp.

See his post at linuxwacom-devel:  [https://sourceforge.net/mailarchive/forum.php?thread_name=201008211203.59754.wacom%40kargulus.de&forum_name=linuxwacom-devel](https://sourceforge.net/mailarchive/forum.php?thread_name=201008211203.59754.wacom%40kargulus.de&forum_name=linuxwacom-devel)  The applet is in the attachment.  Icons are included.

---

### Post by amicable on 2010-08-23
Update: I hadn't noticed, but the *Button 1, Button 2...* labels changed to *Undo, Redo, Zoom In, Zoom Out, Save, Alt, Ctrl & Up Arrow*.

I don't know how to get the config going; the *Zoom In, Zoom Out, Save, Alt* buttons are running the scroll bars in my apps.

---

### Post by Favux on 2010-08-23
Hi amicable,

As I understand it you "must be root to execute the software".  So it would be:
```
sudo intuos4-led-check
```
as in the READ ME.  I can't tell from what you've posted if that's what you're doing.

And init-intuos4-table.sh shows how you combine that with a .xsetwacom.sh script to configure the buttons.  It looks like he's modprobing wacom to remove it, and then the icons, and then restarting wacom.ko.  Not sure what that's about.  Maybe you can't get or change the icons on the OLED's without stopping wacom.ko?

Yep, that must be it because he also says in the READ ME "the wacom driver must be reloaded after usage of the software".  So I think that means 'the wacom usb driver (wacom.ko) must be unloaded before usage of the software and then reloaded'.

So then it becomes:
```
sudo modprobe -r wacom
```
Then use the software:
```
sudo intuos4-led-config --button 2 --icon WacomLogo
```
or whatever.  And then to get the tablet working again when you are finished:
```
sudo modprobe wacom
```

---

### Post by amicable on 2010-08-25
I still get

> sudo: intuos4-led-check: command not found

Is this something very basic -does it need to be in a path or sthg?

---

### Post by Favux on 2010-08-25
> Is this something very basic...?
Probably.  Do any of the other commands, aside from intuos4-led-check, work?

---

### Post by amicable on 2010-08-25
> **Favux said:**
> Probably.  Do any of the other commands, aside from intuos4-led-check, work?

Good point. No, nothing works, not even the shell scripts. I am running as sudo. The folders are in my /home/ 

:?

---

### Post by Favux on 2010-08-25
OK, I'm assuming you installed:
```
apt-get install g++
apt-get install libusb-1.0-0-dev
apt-get install libmagick++-dev

```
He tells you to "To compile the sources, change to the src directory and invoke make."  So apparently no:
```
./configure --prefix=/usr
```
needed.  Did you do a?:
```
sudo make install
```

---

### Post by amicable on 2010-08-25
Yes, I did the make. It went through without errors and I had all the dependencies. The Intuos4-LED/src directory contains the following files:

```
icon-library.cpp        intuos4-led-check.o     set-intuos4-leds.sh
icon-library.o          intuos4-led-config      WacomIntuos4LED.cpp
init-intuos4-tablet.sh  intuos4-led-config.cpp  WacomIntuos4LED.h
intuos4-led-check       intuos4-led-config.o    WacomIntuos4LED.o
intuos4-led-check.cpp   Makefile
```

---

### Post by Favux on 2010-08-25
Alright, if you didn't do the make install and the compiled files aren't in /usr/bin then I suppose you have to use the full path to the file in the /src directory of the unpacked source code tar.

---

### Post by amicable on 2010-08-25
> **Favux said:**
> if you didn't do the make install

Weird. I did the make install. Anyhow, using the full path got the tablet LED's going with the default set. 

Now I have to enter a whole bunch of parameters as intuos4-led-config tells me:

```
intuos4-led-config

Usage: 

/home/[user]/Intuos4-LED/src/intuos4-led-config [--lefthanded] [--vendorid <vid> --productid <pid>]  --button <id> --icon <name> --> Set library icon <name> to button <id>

/home/[user]/Intuos4-LED/src/intuos4-led-config [--lefthanded] [--vendorid <vid> --productid <pid>] --button <id> --image <filename> --> Set image <filename> to button <id>

/home/[user]/Intuos4-LED/src/intuos4-led-config --dump <filename> --> Dump image <filename> as C static array

/home/[user]/Intuos4-LED/src/intuos4-led-config --list -> List library icon names

/home/[user]/Intuos4-LED/src/intuos4-led-config --help -> Display this help text

```

I'll try and install make again as it's tedious to punch out the full path each time.

It'd be good to work out how to make a script so that I can do a one click set up for often used apps (for me Gimp & Inkscape)

I'd also like to know how to get this to persist between boots.

---

### Post by Favux on 2010-08-25
Good so you've confirmed it works.  Just a little bit to go.

OK, I think I see what's going on.  The compile made 4 files:
```
icon-library.o
intuos4-led-check.o
intuos4-led-config.o
WacomIntuos4LED.o
```
The makefile doesn't make any directories or give paths which is why make install isn't doing anything.  So given what he's doing in init-intous4-tablet.sh, it looks like you just copy those four files to /home/username.  Then his ./intuos4-led-config should work.  By the way that's what the init-intous4-tablet.sh if for.  He's pre-made a set up for you.  If you set it up in auto-start it will be applied everytime you boot.  Just remember to make it executable.

Edit:  Otherwise there should be lines something like:
```
install:
	cp -v intuos4-led-check.o ${DESTDIR}/usr/bin/
```
(or wherever he wants to put the compiled objects) in the Makefile.

---

### Post by sanette on 2010-09-22
amicable: 

if you are in the src/ directory just type
```
sudo ./intuos4-led-check
```

(so you don't need make install at this point)

---

### Post by sanette on 2010-09-22
So... finally I have tried this new OLED applet
on my kubuntu 10.04 
(2.6.32-24-generic with hand-compiled xf86-input-wacom-0.10.8)

and it works very well !
Thanks to Christoph Karg!

I need some time to adapt the tools I made for managing profiles, but
it should be ok.

Too bad one has to unload the wacom driver each time... it means I won't have my little animations ;)

---

### Post by amicable on 2010-09-23
> **sanette said:**
> amicable: 

if you are in the src/ directory just type
```
sudo ./intuos4-led-check
```

(so you don't need make install at this point)

Just back from a holiday. Great, this works; I get various tones filling the buttons and then a tux & wacom logo alternating the buttons, finally text saying Button 1, 2..8 appear. :cool:

Now I need to set up profiles for Gimp & Inkscape

---

### Post by sanette on 2010-09-25
Ah ! Here is a modified version of Christoph Karg's program that includes
profiles managing.

So you can have a profile for gimp and one for inkscape...

You switch by

```
intuos-restore-buttons.sh gimp
```

Or with a GUI

```
intuos-select-profile.sh
```

Please read 'README'

---

### Post by amicable on 2010-11-26
I've been away for a while (got married etc) but am back on the Intuous and have just installed Christoph's package. Great, it generally works - I have labels and some of them do things. 

How do I programme the actions for the keys? The one in the package works for Gimp for the save, alt, ctrl, shift, undo, redo buttons but not the zoom in or out. At the same time, I am trying to work out how to generate profiles.

Then I need to work out how to create a start up script - know it should have $HOME/bin/intuos/wacom-intuos but where do I put this?

---

### Post by sanette on 2010-11-28
Hi amicable

congratulations for your wedding !! :p

Are you asking where to put start-up scripts ?

This depends on your distrib.

In kubuntu <= 10.04 : system settings -> advanced -> automatic startup
then select "add script".
(in kubuntu 10.10, same, but there is no "advanced" tab)

In ubuntu 
System -> preferences -> startup applications

(I'm translating from french, maybe that's not the accurate menu names)

---

### Post by amicable on 2010-11-28
> **sanette said:**
> Are you asking where to put start-up scripts ?

Thanks Sannette; sorry I should be clearer. There are three things I want to learn how to do now:

1. Understand how to assign buttons to actions/keys
2. Understand how to collect these into a profile
3. Understand how to automatically start the script on each boot

As far as I know, 3. is tricky as it needs root access. So I'm happy to sudo this through terminal each time although if there's a simpler automatic way I'd love to know.

Paul

---

### Post by sanette on 2010-11-28
> **amicable said:**
> Thanks Sannette; sorry I should be clearer. There are three things I want to learn how to do now:

1. Understand how to assign buttons to actions/keys
2. Understand how to collect these into a profile
3. Understand how to automatically start the script on each boot

As far as I know, 3. is tricky as it needs root access. So I'm happy to sudo this through terminal each time although if there's a simpler automatic way I'd love to know.

Paul

For 1, use xsetwacom
example:

```
xsetwacom set "Wacom Intuos4 6x9 pad" Button1 "key a"
```

this assigns "a" to the central button.

you can also use the scripts I wrote.

for 2-3, this is exactly what I wrote the scripts for (see attachment). It's not optimal, but ok. At startup, a window pops up where you have to enter your password.

for 3: use the script $HOME/bin/intuos/wacom-intuos

to assign an action to a button, first assign a rare key combination, like

xsetwacom set "Wacom Intuos4 6x9 pad" Button1 "KEY CTRL SHIFT f12"

and then use KDE hotkeys to assign to "CTRL SHIFT f12" the script you want. for instance: $HOME/bin/intuos/intuos-select-profile.sh

for changing key bindings, you can also edit the bindings files in $HOME/wacom
(for instance  my $HOME/.wacom/last/bindings:
```

rotate=HALF

key8="KEY CTRL z"
key7="KEY CTRL y"
key6="KEY CTRL l"
key5="KEY CTRL b"
key4="KEY CTRL s"
key3="KEY ALT"
key2="KEY CTRL"
key1="KEY SHIFT"

#central button:
key0="KEY CTRL SHIFT f12"

```

[COLOR="DarkSlateBlue"]* There are more explanations in the README file[/COLOR]

---

### Post by amicable on 2010-11-29
Sanette,

Does this mean I edit init-intuos4-tablet.sh to create my own profile for eg Inkscape by changing the bindings here:

```
echo "rotate=$rotate" > $bindings
echo "key$(( $formula 0 ))=\"key ctrl z\"" >> $bindings
echo "key$(( $formula 1 ))=\"key ctrl y\"" >> $bindings
echo "key$(( $formula 2 ))=\"key bracketright\"" >> $bindings
echo "key$(( $formula 3 ))=\"key slash\"" >> $bindings
echo "key$(( $formula 4 ))=\"key ctrl s\"" >> $bindings
echo "key$(( $formula 5 ))=\"key alt\"" >> $bindings
echo "key$(( $formula 6 ))=\"key ctrl\"" >> $bindings
echo "key$(( $formula 7 ))=\"key shift\"" >> $bindings
```

and for the LEDs here:

```
sudo modprobe -r wacom
sudo $LEDCMD $lefthanded --button 1 --icon Undo
sudo $LEDCMD $lefthanded --button 2 --icon Redo
sudo $LEDCMD $lefthanded --button 3 --icon ZoomIn
sudo $LEDCMD $lefthanded --button 4 --icon ZoomOut
sudo $LEDCMD $lefthanded --button 5 --icon Save
sudo $LEDCMD $lefthanded --button 6 --icon Alt
sudo $LEDCMD $lefthanded --button 7 --icon Ctrl
sudo $LEDCMD $lefthanded --button 8 --icon ArrowUp
sudo modprobe wacom
```

and then saving the resulting file under a new name?

Forgive my ignorance - my scripting abilities are limited

---

### Post by djwkd on 2010-12-05
> **sanette said:**
> 


you can also use the scripts I wrote.




Hi,

I've downloaded the scripts, but I'm not sure how to create  a profile - could you explain it, please?

Cheers,

Dom.

---

### Post by sanette on 2010-12-05
Hi Dom

sorry amicable, I forgot to answer your question

the idea is simply to set up the tablet manually and then save the current state to a "profile", so that next time it can be automatically reloaded.

Instead of setting by hand the first time, you can indeed use 
**init-intuos4-tablet.sh**

and first edit it to suit your needs.

Do you need help for this ?
(there is some in the README file, but I agree it's not a tutorial...)

---

### Post by amicable on 2010-12-05
Hi Sanette

I'll give it a go, 

```
key bracketright
```

is self explanatory

but I'll need to know where to find a full list of keybindings. Or how to generate the right things from keystrokes.

---

### Post by sanette on 2010-12-05
Dom and amicable: you can also try my gimp setup:


1. download the attached file **wacom-gimp.tar.gz** to your HOME dir.

2. open a terminal, and type

```
tar xvfz wacom-gimp.tar.gz
cd bin/intuos
./intuos-restore-buttons.sh gimp

```

(this assumes you have already download and installed the scripts in Intuos4-LED-100930.tar.gz)

---

### Post by sanette on 2010-12-05
amicable:
 I think you can take it that you can use the terminology of this file:

```
/usr/include/X11/keysymdef.h
```

---

### Post by amicable on 2010-12-05
> **sanette said:**
> amicable:
 I think you can take it that you can use the terminology of this file:

```
/usr/include/X11/keysymdef.h
```

Had a look at that but if if I eg search for "bracketright" in that I get a line which says:

```
#define XK_bracketright                  0x005d  /* U+005D RIGHT SQUARE BRACKET */
```

Am a bit lost as to what I do with this... :confused:

---

### Post by Favux on 2010-12-05
Hi amicable,

If you have xf86-input-wacom 0.10.8 or better you should be able to enter 'man xsetwacom' in a terminal.  Try these commands in a terminal:
```
xsetwacom
```
lists available commands and switches.
```
xsetwacom list param
```
Lists available parameters.
```
xsetwacom list mod
```
Lists modifiers and special keys available.

---

### Post by sanette on 2010-12-05
Hi Favux

unfortunately, "xsetwacom list mod" does not list all the available keys.

for instance

xsetwacom set 19 Button1 "key +"

does not work, you need

xsetwacom set 19 Button1 "key plus"

---

### Post by sanette on 2010-12-05
Amicable:

I think that if you find something like

```
#define XK_bracketleft
```

in **/usr/include/X11/keysymdef.h**

it means that you can use the keyword "bracketleft"
(either in **init-intuos4-tablet.sh** or directly when you use **xsetwacom**)

---

### Post by djwkd on 2010-12-13
> **sanette said:**
> 

for 3: use the script $HOME/bin/intuos/wacom-intuos


My tablet hasn't arrived yet, but I (think) I have all the drivers installed, and yet, I don't have a /home/user/bin/intuos folder. In fact, I don't have a /home/user/bin folder... Is there some kind of autodetection that Linux does that then creates this folder?


Cheers,
Dom.

---

### Post by azurehoney on 2010-12-18
This is great news.
[[IMG]http://i.imgur.com/7tZIis.jpg[/IMG]](http://imgur.com/7tZIi)
[[IMG]http://i.imgur.com/AIzY7s.jpg[/IMG]](http://imgur.com/AIzY7)
Does anyone know how to create custom images?

---

### Post by djwkd on 2010-12-19
Hi,

I still don't have a $HOME/bin/wacom directory.
I also can't use the oLEDs - I get this message when running intuos4-led-config - 

```
/home/dominic/Intuos-Stuff/Intuos4-LED-100930/src/intuos4-led-config: error while loading shared libraries: libMagick++.so.2: cannot open shared object file: No such file or directory
```

Can anyone help?

Cheers in advance,

Dom

---

### Post by djwkd on 2010-12-19
Ok, just cd'd to the src dir and ran make install...Here are the results...

```
dominic@dominic-desktop:~/.wacom/src$ make install
mkdir -p /home/dominic/bin/intuos
mkdir -p /home/dominic/.wacom/last
cp intuos4-led-config intuos4-led-check init-intuos4-tablet.sh \
    intuos-restore-buttons.sh intuos-save-buttons.sh \
    set-intuos4-leds.sh text-icon.sh /home/dominic/bin/intuos
cp: cannot stat `intuos4-led-config': No such file or directory
cp: cannot stat `intuos4-led-check': No such file or directory
make: *** [install] Error 1

```

EDIT - I re-downloaded the file and re-installed. It has installed fine, but I still get this: /home/dominic/bin/intuos/intuos4-led-check: error while loading shared libraries: libMagick++.so.2: cannot open shared object file: No such file or directory

I DO have libmagick++ installed (as per the README file)

---

### Post by sanette on 2010-12-20
djwkd: did you run "make" before "make install" ?

---

### Post by sanette on 2010-12-20
azurehoney:  sure, you can create any image you want. It should be a 64x32 PNG image. (you can use gimp for instance)
For instance, I use this for "undo" and "redo" in my "gimp" profile:

[IMG]http://imgur.com/h4VVn.png[/IMG] and [IMG]http://imgur.com/B0ZTc.png[/IMG]

You can also directly create an image from text with the script text-icon.sh


```
       ./text-icon.sh "Hello world"
```

[IMG]http://imgur.com/IaXzV.png[/IMG]

Then you send the image to the tablet with, for button 5:

```
       sudo ./intuos4-led-config --button 5 --image sheep.png
```

(here sheep.png is my image: a small sheep that my daughter likes very much ;) )
[IMG]http://imgur.com/g42dy.png[/IMG]

---

### Post by djwkd on 2010-12-20
Hi Sanette - thanks for the quick response!

> **sanette said:**
> djwkd: did you run "make" before "make install" ?

No. Just done that, and I get this:

```
 make
make: Nothing to be done for `all'.

```

I expect this means I should build each file individually - is there a certain order in which I should build them?

Cheers again,

Dom

---

### Post by sanette on 2010-12-20
just to be sure, you can try, in the src dir:

```
make clean
make 
make install

```

---

### Post by djwkd on 2010-12-20
> **sanette said:**
> just to be sure, you can try, in the src dir:

```
make clean
make 
make install

```

Ok, so the oLEDs are working now, but the keys don't do what the leds say, if that makes sense...For example, (I used the GIMP profile that was up here) the undo button middle-clicks, the redo button right clicks, the middle button (in the middle of the scroll wheel) still left-clicks...I know I can do xsetwacom and everything, but aren't the profiles supposed to set the keys, too (or have I got this wrong?)

Cheers,
Dom

---

### Post by azurehoney on 2010-12-20
> **sanette said:**
> azurehoney:  sure, you can create any image you want. It should be a 64x32 PNG image.
I tried that, but nothing happened.

The test image I used:

[[IMG]http://i.imgur.com/1pQvE.png[/IMG]](http://imgur.com/1pQvE)

---

### Post by sanette on 2010-12-20
your image is very dim, and the LEDS have only 16 levels of gray, so
it might happen that your image becomes completely black.

Can you try with a more contrasted image ?

---

### Post by sanette on 2010-12-20
djwkd: have you selected the gimp profile ?


```
$HOME/bin/intuos/intuos-restore-buttons.sh gimp
```

---

### Post by djwkd on 2010-12-20
> **sanette said:**
> djwkd: have you selected the gimp profile ?


```
$HOME/bin/intuos/intuos-restore-buttons.sh gimp
```


I used the switch profile script, and selected the gimp profile. Does the above need to be done in addition to that?

---

### Post by djwkd on 2010-12-20
After a reboot, all is fine.


Thanks so much! Just gonna set up profiles and stuff now. Would it, in theory, be possible to code a plugin for gimp/inkscape etc for when the program is the active window to switch to the respective profile? Would this be a mouse_enter event or similar? (if its possible, I will look into it, but my coding abilities are limited, to say the least!)

---

### Post by sanette on 2010-12-20
> **djwkd said:**
> After a reboot, all is fine.

Great !



> **djwkd said:**
> Thanks so much! Just gonna set up profiles and stuff now. Would it, in theory, be possible to code a plugin for gimp/inkscape etc for when the program is the active window to switch to the respective profile? Would this be a mouse_enter event or similar? (if its possible, I will look into it, but my coding abilities are limited, to say the least!)

Well, that's a very good idea. Unfortunately, I don't know how to do it either...  I see 2 possibilities:

* a global X11 daemon which triggers the profile corresponding to the active window.

* as you suggest, a specific plugin for gimp, and another for inkscape.

Anyone knows how to program this ?

---

### Post by djwkd on 2010-12-20
> **sanette said:**
> Great !





Well, that's a very good idea. Unfortunately, I don't know how to do it either...  I see 2 possibilities:

* a global X11 daemon which triggers the profile corresponding to the active window.

* as you suggest, a specific plugin for gimp, and another for inkscape.

Anyone knows how to program this ?

Just checked docs for gimp plugin development, and its bad news - it seems to say that you can only use plugs to modify an image. However, i've looked into doing it on java (only linux-friendly language that I have a clue about) and there is something which returns the current active window - keyboardFocusManager.getGlobalActiveWindow.

I am, however, having problems with it. If it means anything to anyone, It says "getGlobalActiveWindow has protected access in..."

And I don't know how to solve it...I'll try though :)

If anyone else wants to have a go, then please do!

---

### Post by azurehoney on 2010-12-20
> **sanette said:**
> your image is very dim, and the LEDS have only 16 levels of gray, so
it might happen that your image becomes completely black.

Can you try with a more contrasted image ?

What happened is that I confused commands and instead of [FONT="Courier New"]intuos4-led-config --button 5 --image[/FONT] I used [FONT="Courier New"]intuos4-led-config --button 5 --icon[/FONT]

Now it's ok.

[[IMG]http://i.imgur.com/MdCW1s.jpg[/IMG]](http://imgur.com/MdCW1)

---

### Post by sanette on 2010-12-20
very nice dragonfly ;)

---

### Post by djwkd on 2010-12-20
> **sanette said:**
> Amicable:

I think that if you find something like

```
#define XK_bracketleft
```in **/usr/include/X11/keysymdef.h**

it means that you can use the keyword "bracketleft"
(either in **init-intuos4-tablet.sh** or directly when you use **xsetwacom**)

This is in my keysymdef.h, too, yet if I add bracketleft to the bindings file, it just doesn't work...

---

### Post by djwkd on 2010-12-20
Hmm...it seems that sometimes, the script restarts X, whilst it doesn't at other times...is this normal?

---

### Post by sanette on 2010-12-20
> **djwkd said:**
> This is in my keysymdef.h, too, yet if I add bracketleft to the bindings file, it just doesn't work...

what do you do exactly ?

If I edit .wacom/last/bindings as follows:

```
rotate=HALF

key8="KEY CTRL z"
key7="KEY CTRL y"
key6="KEY CTRL l"
key5="KEY CTRL b"
key4="KEY CTRL s"
key3="KEY ALT"
key2="KEY CTRL"
key1="KEY bracketleft"

#central button:
key0="KEY CTRL SHIFT f12"
```

and then ```


cd $HOME/bin/intuos
./intuos-restore-buttons.sh
```

(the intuos-select-profile.sh script should work too)

then for me it works "as expected".

"as expected" means that when I press the button I get "(", which is on
the same key as "[" on my keyboard (I think this is a bug in xsetwacom)

---

### Post by sanette on 2010-12-20
> **djwkd said:**
> Hmm...it seems that sometimes, the script restarts X, whilst it doesn't at other times...is this normal?

what script ??

---

### Post by djwkd on 2010-12-20
> **sanette said:**
> what do you do exactly ?

If I edit .wacom/last/bindings as follows:

```
rotate=HALF

key8="KEY CTRL z"
key7="KEY CTRL y"
key6="KEY CTRL l"
key5="KEY CTRL b"
key4="KEY CTRL s"
key3="KEY ALT"
key2="KEY CTRL"
key1="KEY bracketleft"

#central button:
key0="KEY CTRL SHIFT f12"
```and then ```


cd $HOME/bin/intuos
./intuos-restore-buttons.sh
```(the intuos-select-profile.sh script should work too)


Just the same as you've done there, except on key5, and running the select-profile.sh script isntead of restore-buttons.sh. It gives the output '8' (without quotes)...
[QUOTE=sanette]
what script ?? 
[/QUOTE]

I think its ...restore-buttons.sh, as it happens on both select-profile and the wacom-intuos command. I never directly call ...restore-buttons.sh

---

### Post by sanette on 2010-12-20
you probably have a different keyboard as mine...

And I have the impression that xsetwacom is unstable when setting "non-standard" keys...

try a plain letter "key a" or "key ctrl a", etc.
to see if it works...

---

### Post by djwkd on 2010-12-20
> **sanette said:**
> you probably have a different keyboard as mine...

And I have the impression that xsetwacom is unstable when setting "non-standard" keys...

try a plain letter "key a" or "key ctrl a", etc.
to see if it works...

Already have - that all works fine. Just wanted to see if I could set a key as a bracket so that I could have something to adjust the brush size. Then again, its not one of the main things - its easily done with the keyboard...

---

### Post by djwkd on 2010-12-23
Another problem...it doesn't always restore the buttons...sometimes it does, but, like...no matter how many times I run this at the moment, it won't use the bindings from the GIMP profile - it just uses the default bindings...same with other profiles, I think, too...

EDIT: the times it doesn't work seem to be the times it restarts X.

---

### Post by sanette on 2010-12-23
> **djwkd said:**
> Another problem...it doesn't always restore the buttons...sometimes it does, but, like...no matter how many times I run this at the moment, it won't use the bindings from the GIMP profile - it just uses the default bindings...same with other profiles, I think, too...

what exactly is not restored: images / key bindings / both ?

any error message when you do this in a terminal ?

> **djwkd said:**
> EDIT: the times it doesn't work seem to be the times it restarts X.

I never had X restart with these scripts, so I don't know what happens here.
Which version of the wacom driver are you using ?

---

### Post by djwkd on 2010-12-23
Its the bindings that don't restore - images seem to have restored fine.

I'm using 0.10.10, built from git...

---

### Post by sanette on 2010-12-23
can you check if the binding files in the various .wacom/* directories
contain wnat they are supposed to ?

---

### Post by djwkd on 2010-12-24
By 'supposed to', you mean the keys that I want?

Here is the contents of the bindings file for the GIMP profile: (This is the one I pretty much always use, and is the one that will have been in the last directory when X has restarted, and, equally, on the times it didn't.)
```

#CTRL ALT SHIFT P - GIMP BRUSH UP
#CTRL ALT SHIFT O - GIMP BRUSH DOWN


key1="KEY CTRL z"
key2="KEY CTRL y"
key3="KEY CTRL l"
key4="KEY CTRL s"
key5="KEY CTRL ALT SHIFT P"
key6="KEY CTRL ALT SHIFT O"
key7="KEY CTRL"
key8="KEY SHIFT"

#central button:
key0="KEY CTRL SHIFT f12"


```

NB: My scripting abilities are (really) limited, but from the scripts I gathered that # is a comment, right? Otherwise, the first two lines there are messed up...

---

### Post by djwkd on 2010-12-25
Actually, if the restore_buttons script calls the wacom-intuos executable, then it might be that - it is either when I switch profiles or when I open wacom-intuos...

PS: Merry Christmas!

---

### Post by 3soli on 2010-12-28
Hi, I have some problem with this script. Could anybody help me understanding why?

```
sudo ./init-intuos4-tablet.sh
NONE
ERROR: tablet could not be initialized.
ERROR: tablet could not be initialized.
ERROR: tablet could not be initialized.
ERROR: tablet could not be initialized.
ERROR: tablet could not be initialized.
ERROR: tablet could not be initialized.
ERROR: tablet could not be initialized.
ERROR: tablet could not be initialized.
Profile: last
ERROR: tablet could not be initialized.
Code for button 0 is: "key ctrl z"
Code for button 1 is: "key ctrl y"
Code for button 2 is: "key bracketright"
Code for button 3 is: "key slash"
Code for button 4 is: "key ctrl s"
Code for button 5 is: "key alt"
Code for button 6 is: "key ctrl"
Code for button 7 is: "key shift"
Code for button 8 is: ""
```

I'm using Archlinux, but i hope it is not a problem for you :)

Thank you

Merry christmas

---

### Post by sanette on 2011-01-07
3soli:

apart from this, is your Intuos working OK, and do you know which version of the wacom driver you are using ?

xsetwacom -V

---

### Post by sanette on 2011-01-09
> **djwkd said:**
> Hmm...it seems that sometimes, the script restarts X, whilst it doesn't at other times...is this normal?

good news and bad news:

_bad news:_ after intensive testing, I have indeed experienced some X crashes, I believe this is due to the fact that the OLED driver by Christoph Karg requires unloading the wacom driver (**rmmod wacom**), 
which seems to be dangerous to do when you are using the stylus at the same time.

one (not very nice) solution would be to only use the mouse or keyboard to switch profiles.

_good news:_ during the holidays, I have tried to learn X11 programming and wrote a small daemon that does what [djwkd]("http://ubuntuforums.org/showpost.php?p=10260362&postcount=135") wanted: automatically switch profiles when you change application !

---

### Post by amicable on 2011-01-10
> **sanette said:**
> _good news:_ during the holidays, I have tried to learn X11 programming and wrote a small daemon that does what [djwkd]("http://ubuntuforums.org/showpost.php?p=10260362&postcount=135") wanted: automatically switch profiles when you change application !

Sannette, that would be amazing. Currently I use my tablet in a default mode without OLEDs etc because right now I just don't have the time to fiddle around. Automation would be awesome. :)

---

### Post by ManDay on 2011-01-11
Hello, I've been pointed to this thread to get LEDs working. Great work guys. First I'd like to contribute a little nonetheless useful script I've written (bash). Right now it only does a very limited job, that is switching the behaviour of the TouchRing, but the modifications to make it change the behaviour of another key should be minor. Just in case someone is interested:

```
#!/bin/bash
####################################
# Usage: ./switchwacom
# Will cycle through button mappings
# for the touchring
####################################
# Message to show for each mode
message_up=( "Hue" "Luminosity" )
# Options to use for osd_cat
options_up=( "-c red" "-c white" )
# Keybindings for each mode
keycycle_up=( 'key +Control_L +Alt_L +d -d' "key +Control_L +Alt_L +l -l" )
keycycle_down=( 'key +Control_L +Shift_L +Alt_L +d -d' "key +Control_L +Shift_L +Alt_L +l -l" )
####################################

bind_up="AbsWUp"
bind_down="AbsWDn"
devicename="Wacom Intuos4 6x9 pad"
statefile="/tmp/switchwcm"
# If osd_cat is not in PATH
localdir=""
# osd_cat command. If you don't have osd_cat you can replace this with notify-send
osdpipe="'${localdir}osd_cat' --font='-*-*-bold-r-*-*-30' -p bottom -l 1 -o 4"

# **
if [[ -f "$statefile" ]] ; then
	currentkey_up=$(cat "$statefile")
else
	currentkey_up=$(xsetwacom --get "$devicename" "$bind_up")
fi
# /**
# *
trailingletter="${currentkey_up: -1}"
if [[ "$trailingletter" == " " ]] ; then
	currentkey_up=${currentkey_up% }
fi
# /*
i=1
for testkey_up in "$keycycle_up" ; do
	if [[ "$currentkey_up" == "$testkey_up" ]] ; then
		break
	fi
	i=$(( i + 1 ))
done
if (( $i >= ${#keycycle_up[@]} )) ; then
	i=0
fi
echo "${keycycle_up[$i]}" > "$statefile"
xsetwacom --set "$devicename" "$bind_up" "${keycycle_up[$i]}"
xsetwacom --set "$devicename" "$bind_down" "${keycycle_down[$i]}"

eval "echo '${message_up[$i]}' | $osdpipe ${options_up[$i]}" &
```

I use it with the GIT version which might have some bugs which are not in stable, for example the current bindings are not reported back correctly, so I use a statefile for saving the current binding (** lines). That part might be removed if that bug is fixed. Also the * lines are needed for strict comparsion of the keys in case for there is an additional " " at the end of the --get result.


**Question:**

Does anyone know what exactly the problem with the OLED program that makes it require to reload the kernel module?

---

### Post by sanette on 2011-01-12
> **amicable said:**
> Sannette, that would be amazing. Currently I use my tablet in a default mode without OLEDs etc because right now I just don't have the time to fiddle around. Automation would be awesome. :)

yeah, but I'm hesitating to release it because, due to the unloading/reloading of the kernel drivers, it crashed frequently if you happen to move the stylus while switching (which happens naturally, of course...)

---

### Post by sanette on 2011-01-12
> **ManDay said:**
> 
**Question:**

Does anyone know what exactly the problem with the OLED program that makes it require to reload the kernel module?



thanks for this nice script ! we will have a lot of nifty thinkg to package together ;)

the kernel problem is that the OLED program used the libusb library, which won't let you access a device if it's claimed by a kernel driver...

The only possibility I see is to program a switch in the kernel driver which lets you send data to the tablet without interfering with the rest...

---

### Post by djwkd on 2011-01-13
> **sanette said:**
> good news and bad news:

_bad news:_ after intensive testing, I have indeed experienced some X crashes, I believe this is due to the fact that the OLED driver by Christoph Karg requires unloading the wacom driver (**rmmod wacom**), 
which seems to be dangerous to do when you are using the stylus at the same time.

one (not very nice) solution would be to only use the mouse or keyboard to switch profiles.

_good news:_ during the holidays, I have tried to learn X11 programming and wrote a small daemon that does what djwkd wanted: automatically switch profiles when you change application !

Yay! Three cheers for Sanette! That sounds really awesome! Shame that a kernel switch might need to be implemented though! Does anyone know how to code *that*?

---

### Post by djwkd on 2011-02-10
Sorry to be a pest, but have you had any more progress?

---

### Post by Favux on 2011-02-10
Hi djwkd & sanette & everyone,

I'm thinking Peter just figured out the problem and submitted a patch for it a few days ago.  Apparently if the master device is accessed for a brief period during the hotplug after the dependent devices are added (which are first?), that's what's crashing X.  His patch is more a temporary work around until a real fix is found.  Then Ping chimed in saying she was doing automated testing of some new usb hot plug code.  So there may be a solution in a short time.

---

### Post by sanette on 2011-02-10
> **djwkd said:**
> Sorry to be a pest, but have you had any more progress?

Hi djwkd

no problem. my program is already fully fonctional, but it crashes so often
that I did not want to publish it. Do you want to try ?

(I think the crash is due to the rmmod problem, not mine, but I can't be sure of course)

Then I found a much simpler solution using xprop instead of X programming in C, but that does not solve the crash problem.

---

### Post by sanette on 2011-02-11
> **Favux said:**
> Hi djwkd & sanette & everyone,

I'm thinking Peter just figured out the problem and submitted a patch for it a few days ago.  Apparently if the master device is accessed for a brief period during the hotplug after the dependent devices are added (which are first?), that's what's crashing X.  His patch is more a temporary work around until a real fix is found.  Then Ping chimed in saying she was doing automated testing of some new usb hot plug code.  So there may be a solution in a short time.

Hi Favux

thanks for the information.
I'm going to try again then
(not before next wednesday, I'm too busy right now)

---

### Post by amicable on 2011-02-11
Hi Favux, Sanette

I'm happy to test once again when sthg is out - I've been using the tablet without OLEDs for the past months.

---

### Post by djwkd on 2011-02-11
I'm happy to test out your program, too, Sanette! It will be great to have it with the same functionality as it has in Windoze.

---

### Post by sanette on 2011-02-11
> **djwkd said:**
> I'm happy to test out your program, too, Sanette! It will be great to have it with the same functionality as it has in Windoze.

OK I'll package it for you next week.

but in windows it does not change the OLEDS when you switch application, does it ?

---

### Post by djwkd on 2011-02-11
> **sanette said:**
> OK I'll package it for you next week.

but in windows it does not change the OLEDS when you switch application, does it ?

You have the option of creating profiles, and they switch automatically when you go to the programme that that profile belongs to (but you can't use the same profile for more than one programme, as far as I know)

---

### Post by sanette on 2011-02-16
Ok, it was much fun for me learning C programming, X11, and debian packaging...

so for the adventurous who want to try automatic profile switching:

```
sudo apt-get install xosd-bin
```

(this is for displaying notifications on screen)

get **Intuos4-LED-110216.tar.gz** (attached below) and install it as before:

```
tar xvfz Intuos4-LED-110216.tar.gz
cd Intuos4-LED-110216/src/
make
make install
```

This installs the OLED things in your $HOME/bin/intuos.

Now the X11 daemon: get the debian package '**follow-focus**'
 at [launchpad]("https://launchpad.net/~sanette-linux/+archive/wacom/+packages").

Install it:

```
sudo dpkg -i follow-focus_0.2.1_amd64.deb
```

(replace with the version you have downloaded)

You can try it now ! I advise first to try it **without** the Wacom Intuos (unplug it). Then

```
follow-focus -f
```

(the -f option will show some information on the terminal and gives you the possibility to stop with CTRL-C)

Now open firefox, gimp, and try to switch from each other: it should be detected and displayed onscreen !

Now to test it with Intuos: the important config file is **/etc/follow-focus.conf**. Modify it to suit your needs.
(You will see that you can use the same profile for several programmes)
You can put the config file in $HOME/.follow-focus if you prefer. Now run follow-focus as sudo

```
sudo follow-focus -f
```


WARNING: each time you change Intuos profile, it unloads/reloads the wacom module, which is prone to crashing X...
If you want to test it safely first,** use the mouse** to swich programme, instead of the stylus.

---

### Post by Favux on 2011-02-16
Hi sanette,

Great work as usual.

Just to let you know the "fix" should be in 0.10.11 according to the latest.  And that should be out later today or tomorrow with luck.

By the way Peter Hutterer wanted to look at Karg's & your code so I gave him your second version.  No idea when he'll actually get around to it.

---

### Post by sanette on 2011-02-17
> **Favux said:**
> Hi sanette,

Great work as usual.

Just to let you know the "fix" should be in 0.10.11 according to the latest.  And that should be out later today or tomorrow with luck.

By the way Peter Hutterer wanted to look at Karg's & your code so I gave him your second version.  No idea when he'll actually get around to it.


Hi Favux

I installed the latest GIT, but I get xsetwacom errors like this

```
Paramater 'Button1' is no longer in use. It was replaced with 'Button'.
```

despite that *paramater* should be *parameter* ;) it means that xsetwacom syntax is changing ? Do you know the new one ? Will it be in 0.10.11 ?

---

### Post by Favux on 2011-02-17
Hi sanette,

You are correct.  For 0.10.11, which is now out, a bunch of parameter names have changed.  Button1 is now Button 1 for example, and so on for all the buttons, new whitespace.  Got rid of a lot of redundant code in xsetwacom by doing that.  Use 'xsetwacom list parameter' or 'xsetwacom get "device name' "old parameter name' to get them.  Or there is a table I put up on the mediawiki:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)  Looks like I forgot to put the param to parameter change into the table!

I think those commands are right or close anyway.  I've been in Linux the past few days on the Desktop working on the mediawiki so I need to spend some time in Windows catching up.  So it'll be later today before I can check everything out.  I'll send a patch to correct the spelling error if someone doesn't beat me to it.  :)

---

### Post by djwkd on 2011-03-01
Hello.

Any chance of the new version with the new button commands in etc (I know I can just modify the scripts otherwise)?

Cheers,
Dom.

---

### Post by sanette on 2011-03-06
> **djwkd said:**
> Hello.

Any chance of the new version with the new button commands in etc (I know I can just modify the scripts otherwise)?

Cheers,
Dom.


Sure: here it is !

Now I am quite happy: with the new wacom driver 0.10.11, it seems very stable: no more crash !

As usual, to upgrade, untar the [_archive below_]("http://ubuntuforums.org/attachment.php?attachmentid=185239&stc=1&d=1299403655"), change to the **Intuos4-LED-110305/src** directory and type
```
make
make install
```
If you want to do it again, type before:
```
make clean
```

At this point,  you can set up your icons and keybindings, save profiles, and run the **follow-focus** daemon, as described in my previous post. I find it quite convenient, hope it works for you too !

**_Warning:_** due to changes in xsetwacom, I had to modify several things. In particular the tablet buttons are now recognized by X11 as buttons 1 2 3 8 9 10 11 12 13 (weird !)
"1" is the central round button, and the rest are the 8 rectangular buttons.

Because of this, the labelling scheme has changed, and you should recreate your profiles in **$HOME/.wacom**
I give you a [_sample dir below_]("http://ubuntuforums.org/attachment.php?attachmentid=185238&stc=1&d=1299403770") if you want to try quickly. Just untar it in your **$HOME** dir.

**_Warning 2:_** Again, I have tested only with **xf86-input-wacom-0.10.11**. I, like me, you use ubuntu 10.04, then this version needs a patch (otherwise it crashed immediately). It is very simple: edit the file
**xf86-input-wacom-0.10.11/src/wcmCommon.c**, go to line 41, where you should find the line:
```
	static int v[MAX_VALUATORS];
```
Delete this line and copy it just after line 38, so that the new lines 38-44 should be:
```
#if GET_ABI_MAJOR(ABI_XINPUT_VERSION) < 11
static int v[MAX_VALUATORS];
static int *VCOPY(const int *valuators, int nvals)
{
	memcpy(v, valuators, nvals * sizeof(int));
	return v;
}
```

You can now go on as usual:
```
cd xf86-input-wacom-0.10.11
./configure --prefix=/usr
make
sudo make install
```

---

### Post by djwkd on 2011-04-12
Surprised I didn't post here earlier!

Thanks again, Sanette - great work!

Only one thing: did you say you had implemented a way for it to automatically switch profiles with the windows? How do I use it?

Thanks again,

Dom.

---

### Post by sanette on 2011-04-14
> **djwkd said:**
> 
Only one thing: did you say you had implemented a way for it to automatically switch profiles with the windows? How do I use it?


Hi Dom, yes I have implemented such a thing. See my previous post  [#169]("http://ubuntuforums.org/showpost.php?p=10465371&postcount=169"). In your case, if you already have installed Intuos4-LED-110305, you just need to install the ubuntu package **xosd-bin** and the **follow-focus** package from my [ppa]("https://launchpad.net/~sanette-linux/+archive/wacom/+packages").

---

### Post by sanette on 2011-05-11
Some good news:

I've just installed kubuntu 11.04 (Natty)
(it should be the same with ubuntu)

and the wacom package shipped with it (0.10.11) works quite well: no more need to compile a newer version by hand.

* the Intuos is recognized and works out of the box (without OLEDs)

* the OLED bundle works. (Install **libmagick++-dev** and **libusb-1.0-0-dev** for the compilation. See previous messages)

* the **follow-focus** package works. (I uploaded a Natty version on the PPA page)


When the OLED will be integrated in the wacom driver (when ??) it will be smoother, and there will be no need to run follow-focus as sudo. But still, it's not so bad so far !

EDIT: if anybody is interested, I can try to package the OLED utilities+ the follow-focus app in one ubuntu package

---

### Post by DementedSnake on 2011-05-12
Yes please. Also, a simple GUI would be great, but this is wonderful as-is.
Also, here's an idea for anyone interested. Stylish icons. [http://fav.me/d3g596m](http://fav.me/d3g596m)

---

### Post by theOGRE on 2011-05-22
Hey guys! This is my first wacom related post, but I've been reading a lot of these post. Kudos to you guys for all the work you're doing and the grade A help.:D I used my Intuos4 back in the day on Hardy Heron, but kind of pushed it on the back burner till now (Natty). You have done a lot of work! I have 99% functionality now without even building any drivers! Excellent. 

Ok, as far as that last 1%, which I really want,   maybe you can help me. I see a lot of talk here and there about the OLEDs, which only makes me jealous I didn't get one of those fancy suckers. I have an Intuos4 model PTK-440 ( no OLEDs). I just want to be able to turn the 4 little LEDs that are next to the ring on and off. Don't know if I missed something, but is it possible?

Kubuntu 11.04 with xf86-input-wacom and xsetwacom -V says 0.10.11
any help would be great.

oh yeah, I do have something else that doesn't work, but I forgot 'cause I was working around it. If I try to map the Super mod, no matter which version I try, I can't get the Super or Hyper to stick. The output of xsetwacom -s get $id Button $btn_num   says  ' +(null) -(null)' instead of '+lsuper -lsuper'.

Thanks again for all the hard work everyone.

---

### Post by theOGRE on 2011-05-22
I was going about trying to make a gui for my Intuos settings, and I have come across a little problem. This may be already addressed in new version, but xsetwacom should return something other than 0 if it bailed due to a bad argument. I would like to have the gui let you know it is a bad setting, by using '--shell get' to get the current setting, and then apply the user defined setting, see if it returned 0, then put it back if it did not. I can work around it by redirecting the error stream to std out, catch that and test if it is empty, but generally I would expect an error number or at least non 0.

---

### Post by sanette on 2011-05-31
> **theOGRE said:**
> 
Ok, as far as that last 1%, which I really want,   maybe you can help me. I see a lot of talk here and there about the OLEDs, which only makes me jealous I didn't get one of those fancy suckers. I have an Intuos4 model PTK-440 ( no OLEDs). I just want to be able to turn the 4 little LEDs that are next to the ring on and off. Don't know if I missed something, but is it possible?


I remember reading in the linuxwacom mailings that this was not possible for the moment.

Btw, Favux (if you read this), you said at some point that there were works on the way to include OLEDs into the drivers. Where is this happening ? I'd be interested to see the code.

---

### Post by sanette on 2011-05-31
> **DementedSnake said:**
> Yes please. Also, a simple GUI would be great, but this is wonderful as-is.
Also, here's an idea for anyone interested. Stylish icons. [http://fav.me/d3g596m](http://fav.me/d3g596m)

The link doesn't work. Could you update it ?

---

### Post by Favux on 2011-05-31
Hi sanette,

Eduard Hasenleithner is submitting the patches to the linux-input mailing list:  [https://patchwork.kernel.org/project/linux-input/list/](https://patchwork.kernel.org/project/linux-input/list/)

March 27, 2011 - Wacom Intuos4 LED and OLED support:  [https://patchwork.kernel.org/patch/666511/](https://patchwork.kernel.org/patch/666511/)
His first patch using IOCTL interface which I'm pretty sure he discussed with Ping and Peter.

April 3, 2011 - [v2] Wacom Intuos4 LED and OLED support:  [https://patchwork.kernel.org/patch/683991/](https://patchwork.kernel.org/patch/683991/)
Cleaned up version.  Dmitry Torokhov (the maintainer) finally responds.  Discussion ensues and they decide that binary sysfs attributes would be a better way to go than IOCTL.

April 8, 2011 - Wacom Intuos4 LED and OLED control:  [https://patchwork.kernel.org/patch/695611/](https://patchwork.kernel.org/patch/695611/)
First sysfs version which by the way also supports the LEDs.  Dmitry wants some changes.

May 8, 2011 - [PATCHv2] Wacom Intuos4 LED and OLED control:  [https://patchwork.kernel.org/patch/765792/](https://patchwork.kernel.org/patch/765792/)
No response from Dmitry as of yet.

---

### Post by theOGRE on 2011-05-31
Thanks for the response. So how hard is it to apply one of these patches?

---

### Post by sanette on 2011-06-01
Thanks Favux, I'll have a look

---

### Post by Favux on 2011-06-01
Sure sanette.  Let me know what you think.


Hi theOGRE,
> So how hard is it to apply one of these patches? 
Probably not too bad.  You'd want to use the last patch of course.  In appendix 1 of the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") I show how to patch the Ubuntu kernel source code for the wacom.ko and compile it.

---

### Post by sanette on 2011-06-01
I have tested the last patch, it works !!

You can

* choose which one of the 4 small leds you want to light on
* make the intensity of the led change when the stylus is touching the table
* send images to the OLEDS

Wow !! great !

---

### Post by Favux on 2011-06-02
Hi sanette,

Excellent!!!  :)  Real progress then.

You might want to consider posting on linux-input and giving Eduard a tested-by: for the patch, if possible.  Or at least contact him through his posting on linuxwacom-discuss or -devel, I forget which he posted on.

---

### Post by sanette on 2011-06-02
> **Favux said:**
> Hi sanette,

Excellent!!!  :)  Real progress then.

You might want to consider posting on linux-input and giving Eduard a tested-by: for the patch, if possible.  Or at least contact him through his posting on linuxwacom-discuss or -devel, I forget which he posted on.

Right, so I posted to linux-input. I'm not sure it worked, though.

Here is part of my message: maybe you can answer:

"A beginners' question: the device can be accessed by, for instance through

/sys/class/input/input13

What is the best way to find out which number it is (here 13) ?"

EDIT:

Ah ! I found this

```
readlink /dev/input/wacom 
```

---

### Post by sanette on 2011-06-03
Eduard Hasenleithner told me this will be included in xsetwacom.

In the meantime I have adapted Christoph Karg's tools: this is great, now we don't need sudo and we don't need to reset the wacom module every time we change the OLED.

It is not very polished to release it now, especially having in mind that the (o)leds features should eventually go into xsetwacom, but I can post it if anybody is impatient and interested.

---

### Post by sanette on 2011-06-05
Mmm I've just noticed that each time I press a button, or the ring, the cursor jumps to top corner of the screen.

I'm using the driver that comes with Natty, but I'm not sure if this happened already when I installed natty, or if it is due to some changes I made.

Does anyone experience this too ?

---

### Post by sanette on 2011-06-05
A user reported the same bug last year:

[https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/560180](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/560180)

unfortunately it seems that the bug is back

(and the patch doesn't apply anymore as is)

---

### Post by Favux on 2011-06-05
Hi sanette,

It seems to be a new bug with the Intuos4:  [http://ubuntuforums.org/showthread.php?t=1767607](http://ubuntuforums.org/showthread.php?t=1767607)  especially since you are seeing it too.

---

### Post by theOGRE on 2011-06-08
Ok, so I tried the patch, and it doesn't help me, because it does not cover the Intuos4 Small. So I guess it's a no go on the leds. However, I have just started having the cursor jump problem above. Reverting the wacom.ko did not help, so I'm not sure what made this start happening. I know for sure that a week and a half ago I was using the pad buttons and wheel in Inkscape with no problem. Also I could scroll in firefox just fine. Now the pad cannot perform these tasks because of the cursor move. Please Help Me! [-o<

---

### Post by Favux on 2011-06-08
Hi theOGRE,

Shoot, I thought the LEDs would cover the small's LEDs.  I'm interested in sanette's take.

Sanette posted a fix for the jump on linuxwacom-discuss:  [http://sourceforge.net/mailarchive/forum.php?thread_name=BANLkTimZUkGELM8mHxdCgRtLgt-QJSAcVQ%40mail.gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=BANLkTimZUkGELM8mHxdCgRtLgt-QJSAcVQ%40mail.gmail.com&forum_name=linuxwacom-discuss)

---

### Post by theOGRE on 2011-06-08
oh yippy, I'll try that now. I can't help but wonder what caused it to start though, because I know it was not doing this before. By the way Favux, your a lot of help. Thanks for replying to peoples questions.  =D>

---

### Post by theOGRE on 2011-06-08
Oh, and about the led thing, the patch description says this:

[COLOR=Blue]This commit enables control of the LEDs and OLED displays found on the Wacom Intuos4 M, L, and XL. For this purpose, a new "led" attribute group is added to the sysfs entry of the input device.  This "led" group only shows up when the correct device (M, L, or XL) is detected. The attributes are described in Documentation/ABI/testing/sysfs-wacom[/COLOR]
So it's an 'all or none' deal with the OLEDs and the ring LEDs. Maybe this should be seperated, so that all the Intuos get the little leds, and if Size >=Medium then it gets OLED functionality.

---

### Post by theOGRE on 2011-06-08
I'm no good at this stuff. So when I try to apply the patch, I get this:
[COLOR=Purple]patching file src/wcmCommon.c
patch: **** malformed patch at line 6: WacomDeviceState* ds,[/COLOR]

I don't know what to try. I copied the patch part from the post you mentioned, and saved it in a file called patch-fix-jump.patch, then in the top dir of the kernel source, I put :
[COLOR=DarkGreen]patch --dry-run -p1 < ../patch-fix-jump.patch[/COLOR]

---

### Post by sanette on 2011-06-08
Hi theOGRE

I don't know what happened with your patch. You can try to download it directly:

```
wget https://patchwork.kernel.org/patch/765792/raw/
```

And then

patch -p1 < index.html

EDIT: sorry, I was talking about the other patch... mixing things up

another possibility is to do the changes manually; for the "fix-jump" patch, there are very few of them

---

### Post by sanette on 2011-06-08
Concerning the led kernel patch, I don't know...

One could try to modify line 695 of wacom_sys.c:
replace **>= INTUOS4** by **>= INTUOS4S**
and see what happens...

I don't have an Intuos 4S to test...

---

### Post by sanette on 2011-06-08
oops, see below

---

### Post by sanette on 2011-06-08
Hi theOGRE

concerning the 'fix-jump' patch, here is what you can do:

go to a fresh directory,

```
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
cd xf86-input-wacom
./autogen.sh --prefix=/usr
```

now copy here the file jump-patch.txt (post attachment)
```

patch -p1 < jump-patch.txt 
make
sudo make install
```

---

### Post by theOGRE on 2011-06-08
O.K. thanks, I'll try that in a bit. should the led patch be applied to the wacom.ko first, or this one, or does it even matter? I also wanted to be sure it won't be hard to get be back to the start if I screw up. Tanks again.

---

### Post by theOGRE on 2011-06-08
Thank you very much! Leds working after the suggested change, except mine was on line 689. I just changed the permission  on the files, and now I can change the lights. Yeah! So is this persistant, or will the input* change around.

As far as the jump problem, I get this error when trying to run autogen.sh:

[COLOR=Purple]configure.ac:43: error: must install xorg-macros 1.8 or later before running autoconf/autogen
configure.ac:43: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: /usr/bin/autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1[/COLOR]

I can't find [COLOR=Purple]xorg-macros[/COLOR]. any suggestions?  Thank you again! I'm very happy about the leds. Is there somewhere I should post this, so that maybe the change can happen upstream?

---

### Post by Favux on 2011-06-08
See part II. of the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  In a) Lucid only it shows you how to update the xorg-macros for Lucid.

---

### Post by theOGRE on 2011-06-08
Thank you.

---

### Post by theOGRE on 2011-06-08
Ok... Thank you both for the excellent help. I am pleased to say that it all worked out, and i got led support plus got rid of the jump problem. 
:biggrin:AWESOME!

So now I have one last question if it's not too much to ask.
How can I make the led/status* files writeable to all at boot ? (I know, I should know this) I would like to include light switching in my scripts without being root.

---

### Post by sanette on 2011-06-09
Hi theOGRE

I'm glad it works for the INTUOS4S too !

for the perms, you should modify every line in wacom_sys.c that starts with

```
static DEVICE_ATTR
```

I did this too for me ! See the attached file (which should be all set for you).

---

### Post by sanette on 2011-06-09
and yes, the input* may change around.
You can use ```
readlink /dev/input/wacom
``` to find out

see the sample script I write below:

```
#!/bin/bash -e

event=$(readlink /dev/input/wacom) # exits if does not exist
leddir=/sys/class/input/$event/device/led

echo "Intuos sysfs detected at $leddir"

case "$1" in
    "-active-led") # 0-127
        echo "$2" > $leddir/status1_luminance
        exit
        ;;
    "-passive-led") # 0-127
        echo "$2" > $leddir/status0_luminance
        exit
        ;;
    "-button") # 0-7
        button=$2
        raw_image=$3
        cat $raw_image > $leddir/button${button}_rawimg
        exit
        ;;
    "-select-led") # 0-3
        echo "$2" > $leddir/status_led_select
        exit
        ;;
    "-luminance") # 0-15
        echo "$2" > $leddir/buttons_luminance
        exit
        ;;
    *)

esac

```

---

### Post by sanette on 2011-06-09
OGRE: I'm just curious: in the led sysfs directory, do the files
"button*_rawimg" get created for your INTUOS4S too ?

---

### Post by jon.k on 2011-06-09
> **sanette said:**
> …for the perms, you should modify every line in wacom_sys.c that starts with…
I would advise against setting "S_IRUSR | S_IROTH" though, as reading is unimplemented.
I did something for a profile manager I started to work on and only used "S_IWUSR | S_IWOTH".

I suppose a more permanent solution once this gets integrated to xsetwacom would be a separate setuid executable that allows to change these values as policy seems to be root-only for /sys.

---

### Post by sanette on 2011-06-09
I see, thanks for pointing this out.

---

### Post by theOGRE on 2011-06-09
Yes, the files are there, but I haven't dared to mess with them.

Ah, nice script. I have one that does this pretty much, but I missed the readlink part(thank you), and I skipped the button pics because I don't have those. I also have a few little animations such as pulse and cycle.

 Is there a reason the files are made with root permissions? I see that I can change the source to make them not do that, but I want my GUI to work for other people too. Is there another easy way to change the files, because I don't want to depend on having an altered xf86-input-wacom for it to work. If not then that will work. Maybe the wacom stuff that needs root can be created with the group "wacom", and then add yourself to the wacom group for access? Just a thought. If nothing else then I will probably have my gui launcher first run 'kde/gksudo chmod a+w ${led_dir}/*', rather than hacking the source.

 Is there a way of getting the "S,M,L, or XL" from a shell script so that I can avoid the button LEDs if it is Intuos4S, but still include it for others? Or better yet, what is the proper way to get all the info on the wacom tablet. 'xsetwacom list' does not produce the 'S' that I need. 

Is there any harm in writing to the button led files if I don't have the leds?
In my case I only use the status0, status1, and select files.

Thanks again for helping me out here, and especially for the jump patch. Sorry 'bout the million questions! You can tell me to scram at any time. :D

---

### Post by sanette on 2011-06-09
since you mention profile manager, here is the one I started to work on too.

It is fully functional for OLEDS, buttons and automatic switching, but I didn't do anything with the 4 small leds for now, and I won't have the time to work on it for a while.

```
tar xvfz intuos-utils.tar.gz 
cd intuos-utils-current/
./configure --prefix=/usr
make
sudo make install

```

There are 3 subdirs here, and the makefiles are a mess, sorry for this. Maybe it can still be useful to some real programmer out there.

---

### Post by jon.k on 2011-06-09
I have some kind of state-machine-ish profile manager that allows you to switch through several mappings by context. I used symlinks and directories to represent state. I quite like how it turned out. I'll polish it up a bit and post it this weekend.

For example for inkscape:

[LIST]
[*]Select (1. icon) will press F1 then switch to new set of buttons: (1st status led is lit)
[LIST]
[*]Home (1. icon) will return to previous screen of buttons
[*]Duplicate will press Ctrl+D
[*]…
[*]Center ring will move to second page: (2nd status led is lit)
[LIST]
[*]move selection to top
[*]move selection up
[*]…
[*]Center ring _could_ move to even another page but goes back to 1st page in my case (there I could click on the home icon to return to the main set of buttons)
[/LIST]
[/LIST]
[*]Select Nodes (2. icon)
[/LIST]

---

### Post by sanette on 2011-06-10
Hi jon.k

that sounds great !

I was wondering whether it would be more practical (or not) that the led only indicates the behaviour of the touch ring (and does not change the buttons).
For instance in gimp: you would press the central button to change the effect of the touch ring: zoom in/out -- change brush size -- change opacity -- etc..

Now I'm thinking: with your profile manager, with my tentative (which is application-based and also uses directories for profiles), with Karg's set of ready-to use icons, with OGRE apparently writing a GUI for his intuos3... and probably others...
Why not try to unite efforts and make a killer app ?

---

### Post by jon.k on 2011-06-10
I thought now would be a good moment to share my take on things be they polished or not. I implemented this first version as a (zsh) shell script but found it to be a good match as it does quite well in handling symlinks and the like and keeps the code simple to digest. In fact, go ahead and [take a look at it now]("https://github.com/kljohann/pintxuos/blob/master/pintxuos.zsh"), I tried to explain how it is supposed to work in the comments.

Basically you have a "current" state (that is, a directory with icons and key bindings) pointed to by "~/.pintxuos/this". When pressing a button on your tablet you have to set it up to call "pintxuos press #" where # is the number of the button on your tablet counted from 1-8 (from the top). Pintxuos won't change this keybinding but instead use a seperate tool for the job (kind of unix philosophy) namely xdotool to send keys to the focused window.

[What happens when you press a button]("https://github.com/kljohann/pintxuos/blob/867a99511ce08c3ab387d9a55d0f4113a7d79ef8/pintxuos.zsh#L182") (ie. change status, push keys)
[What happens when you change to a new state]("https://github.com/kljohann/pintxuos/blob/867a99511ce08c3ab387d9a55d0f4113a7d79ef8/pintxuos.zsh#L70") (ie. set status led, display icons)

See the source here: [https://github.com/kljohann/pintxuos/blob/master/pintxuos.zsh](https://github.com/kljohann/pintxuos/blob/master/pintxuos.zsh)
And a sample profile here: [https://github.com/kljohann/pintxuos-profiles](https://github.com/kljohann/pintxuos-profiles)

This needs zsh, xdotool and some tool to convert the images to raw icons. I will post this in a bit. _Is there a way to do this with image magick's command line tools?_

EDIT: [Here]("http://www.youtube.com/watch?v=Yc7N8NwYgrE") is a vidoo of it in action. I used the keyboard to switch states as my keybindings are currently messed up.

> **sanette said:**
> I was wondering whether it would be more practical (or not) that the led only indicates the behaviour of the touch ring (and does not change the buttons).
For instance in gimp: you would press the central button to change the effect of the touch ring: zoom in/out -- change brush size -- change opacity -- etc..
Indeed that behaviour could be useful, too. In my current implementation you could get this behaviour by changing what the touch strip does in the "_init" file in a state directory. The status led will always be what is inside "_status". This will perhaps be clearer, when you take a look at my sample profile.

> **sanette said:**
> Now I'm thinking: with your profile manager, with my tentative (which is application-based and also uses directories for profiles), with Karg's set of ready-to use icons, with OGRE apparently writing a GUI for his intuos3... and probably others... Why not try to unite efforts and make a killer app ?
Although I may not have that much time to put into this, count me in!
I would prever a solution that is simple and does not depend on certain window managers, but otherwise I could just keep using my simple version for that.

---

### Post by theOGRE on 2011-06-10
I saw your video, and it's cool. I sure wish I had those  button LEDs man! That is so slick. I was going to change what all the buttons do, but having them always the same so that your script can keep up with what to do is a neat way to get the job done. This is probably better than changing the actual bindings, yeah? 

Ok, I might try to see what happens if I  write to the raw image files without having the LEDs. As far as the me trying to find out if the pad is 'S' for small... I cannot believe how ridiculous I am sometimes! I just need to ( xsetwacom list | grep 'Intuos4 4x6' )... duh!

Edit:  I don't know how to try the raw image thing. Where do you get the [FONT=monospace]'[/FONT]intuos4led-img2raw' ?  I know it won't do anything, but I just want to see if it will break anything.

---

### Post by jon.k on 2011-06-10
I guess it won't do any good. In the end, the small version does not have any OLEDs, so I guess there would be no reason to try it? :-)
intuos4led-img2raw however is a converting program I assembled out of bits from Christoph Karg's initial toolset (WacomIntuos4LED.cpp).
You can get it here: [https://gist.github.com/1019617](https://gist.github.com/1019617)

Then use
```
g++ -o intuos4led-img2raw -I/usr/include/ImageMagick -lMagick++ intuos4led-img2raw.cpp
``` to compile it.

---

### Post by eyes on 2011-06-10
Hi,

I've just patched my kernel to display my Intuos 4M OLEDs
What can I try to see if it worked ?

@ jon.k : I watched your video, I want these icons too !
__

---

### Post by theOGRE on 2011-06-11
@ jon.k: I only was wondering if there should be a different patch for the small Intuos. Like can I use your state style script, or other things people make? Or will it be a bad thing if one of these programs tries to draw to my led that isn't there? 

 I really don't know jack about patches, but should I not have these files? Should the oled implementation that makes it in to the module(I'm assuming this won't be a patch in the future) be made to ignore those files for an Intous4S ? 

My main concern is that I don't know if there is anything problematic about using this altered patch that was made for other models just to get the indicator leds on my model to work. Does the driver use any extra checks on those files, to see that there's nothing there? Or does it only look if the file is written to? should the driver be changed to only make the 3 needed files for my model, and make them all for others?  

I have too many questions here that probably only effect me,  because any sensible person would get the other models. That video makes me jealous! :)

---

### Post by sanette on 2011-06-11
Hi Jon.k

I didn't know zsh, it seems very powerful, and your programming style is very nice !
Your idea to have fixed bindings for the buttons is interesting, but I don't quite understand why it is better than direclty binding the buttons to the keys we want.

If I understand your strategy involves 2 intermediate layers: the window manager (to call a script) and then the script calls xtodool to emulate keys.

But the guys at linuxwacom worked hard to include key event directly in xsetwacom: no intermediate level. Why not use it ?

I know this is not very important, I'm just curious.

Btw, I didn't know xdotool, it seems more powerful than xte. Thanks for sharing this

---

### Post by theOGRE on 2011-06-11
In Jon.k's script he is doing key events with xdotool based on file name. Button 1 might  change the state, which changes all the icons and what all the buttons do or something. After thinking about his state method, I think I will use something similar.

 It could be slightly modified to do more with xdotool than the wacom keys can do though. xdotool can chain events together that can be complex. (Activate a window, clear all modifiers then click here, and type "hello world", and hit enter) Or something simple like a 'Control' keydown and 'mouse 3' and  'Control' keyup.

 Besides that, having it bound to the same keys is still using the linuxwacom key event, but depending on the state it could do pretty much anything. I might make button 1 cycle through Gimp windows. All this would be too much to ask of the wacom team, and too much bloat for someone who doesn't want the features. 

here is an example that could be put in a script that is launched on key event:

```
query=`xclip -o`;[ -n "${query}" ] && xdotool search --class "firefox" windowactivate %1 key --clearmodifiers "Control+t" key "Tab" type "${query}" && xdotool key Return
```That will switch to an open firefox window, make a new tab, tab over to the google bar, and search for what is on the clipboard.

---

### Post by sanette on 2011-06-11
Thanks OGRE for the explanation. Indeed, I agree now it sounds like a good idea.

Some more comments:

* I find it unsafe to encode information in the filenames themselves.
Maybe that's just because I had bad experiences syncing files from/to linux/windows/mac...

* writing raw files instead of png files is interesting because the images get converted only once, and then no image manipulation via magick is necessary.

The directory structure that I use for the moment is the following: (example)

```
ls ~/.wacom/inkscape/
bindings      button11.raw  button13.raw  button3.raw  button9.raw
button10.raw  button12.raw  button2.raw   button8.raw
```

and the bindings file is like this:

```
rotate=half
key1="key +Control_L +Shift_L +F12 -F12 "
key2="key +Shift_L "
key3="key +Control_L "
key4=""
key5=""
key6=""
key7=""
key8="key +Alt_L "
key9="key +Control_L +s -s "
key10="key +Control_L +b -b "
key11="key +Shift_L +Control_L +l -l "
key12="key +Control_L +y -y "
key13="key +Control_L +z -z "

```

this one is automatically generated, but writing it manually works too.

---

### Post by jon.k on 2011-06-11
@all: Thanks for your feedback! :)

> **eyes said:**
> I've just patched my kernel to display my Intuos 4M OLEDs
What can I try to see if it worked ?

@ jon.k : I watched your video, I want these icons too !
To test if it worked you try to cat a raw icon to one of the /sys/class/input/input*/led/buttonN_rawimg files:

[LIST=1]
[*]locate the /sys/class/input directory for your tablet (this will be the only one with a 'led' subdirectory). Try something like "echo /sys/class/input/input*/led" in bash/zsh
[*]Get some icon in the correct format. You can use the tool I posted earlier to convert a 64x32 image or just use the sample one I attached (gunzip it first!).
[*]Type "cat icon.raw > /sys/class/input/input*/led/button0_rawimg" into your shell. Either it will work with the wildcard or you will have to substitute the directory you found above.
[/LIST]
I took those icons out of Inkscape's icons.svg and some of them from the icon sheme HighContrast. For now I pushed my [pintxuos-profiles]("https://github.com/kljohann/pintxuos-profiles") to github, they are included there.

> **theOGRE said:**
> @ jon.k: I only was wondering if there should be a different patch for the small Intuos. Like can I use your state style script, or other things people make? Or will it be a bad thing if one of these programs tries to draw to my led that isn't there?
I think as a temporary solution removing the corresponding parts from the patch besides removing the check for M/L (what you already did) will work.

> **theOGRE said:**
> Besides that, having it bound to the same keys is still using the  linuxwacom key event, but depending on the state it could do pretty much  anything. I might make button 1 cycle through Gimp windows. All this  would be too much to ask of the wacom team, and too much bloat for  someone who doesn't want the features. 
Exactly. I found xdotool to be doing a great job and tried to keep it simple by using tools that already work.

> **theOGRE said:**
> It could be slightly modified to do more with xdotool than the wacom  keys can do though. xdotool can chain events together that can be  complex. (Activate a window, clear all modifiers then click here, and  type "hello world", and hit enter) Or something simple like a 'Control'  keydown and 'mouse 3' and  'Control' keyup.
That's possible by making the button file executable and including it as a script. For example put this in "3-whatever" and "chmod +x 3-whatever":

```

# your code
query=`xclip -o`;[ -n "${query}" ] && xdotool search --class  "firefox" windowactivate %1 key --clearmodifiers "Control+t" key "Tab"  type "${query}" && xdotool key Return
# $1 is the path to the pintxuos executable, so it's still possible to switch to a different state although this is not a symlink!
# will switch to directory "node" in the current state
$1 go node

```> **sanette said:**
> I find it unsafe to encode information in the filenames themselves.
Maybe you are right, but I found this to be the simplest solution for me because you can easily see what this button is bound to without opening the file and it's the only way for a symlink to include this information.

---

### Post by azurehoney on 2011-06-11
> **jon.k said:**
> 
EDIT: [Here]("http://www.youtube.com/watch?v=Yc7N8NwYgrE") is a video of it in action. I used the keyboard to switch states as my keybindings are currently messed up.

Neat. Icons look surprisingly sharp. "Expresskey" OLEDs and status LEDs will be available in a driver soon, correct? Now we need a [graphical tool to configure the tablet](https://live.gnome.org/Design/SystemSettings/Tablet) and Linux Intuos4 driver will reach feature parity (and surpass with complete! freedom to customize OLEDs) with Windows/Mac...well, minus some special things like "[Precision Mode](http://i.imgur.com/OwcMP.png)" and "[Radial Menu](http://i.imgur.com/R3B5a.png), although the last one is more like gimmick in my humble opinion.

Also I wonder what is the exact dpi of Intuos4 OLED display? I did some rough measurements with a ruler and got around 1.75cm per 64 dots. That is (inaccurately) around 92...93 dpi.

---

### Post by theOGRE on 2011-06-11
I tried the 1.raw image to see if it would upset my driver or break something. It did not. It didn't seem to do anything, which is what I was hoping for. Is there one of those magic commands or log files that will tell me that there was a problem? I think it is non issue. 

I have a buddy that inherited my old bamboo fun (old model no touch) when I  got the Intuos4. Is there a way to use the led ring on that model?

Also, when one has multiple pens, like the airbrush pen, would they show up with their own id# in 'xsetwacom list' ? I need to know that, but I don't own another pen.

---

### Post by Favux on 2011-06-11
Hi theOGRE,

Identifying styli and airbrushes by their serial numbers is a new feature added to xf86-input-wacom in the 0.11.0+ tree by Alexia Death (a Gimp developer) and Peter Hutterer.  You set the serial Option in the wacom.conf and then use a new xsetwacom command:
```
xsetwacom parameter BindToSerial
```
I don't actually know how to use it in practice because I haven't seen anyone try it yet.

---

### Post by theOGRE on 2011-06-11
Hey Favux, I'm curious about that, as it may effect what I'm doing, and I may want one also. I wonder if they show up as a another input in gimp, get their own button settings with xsetwacom, etc.

---

### Post by Favux on 2011-06-11
I don't know.  If you clone the 0.11.0+ git repository there is a new entry in *man wacom* describing the new Option.  I don't know if there is anything in *man xsetwacom* yet.

---

### Post by theOGRE on 2011-06-11
Yeah, I ended up with 0.11.1.  I don't see anything in xsetwacom,  but the man for wacom says that I can see it by running xsetwacom, so I guess it will show up. I didn't realise I had a new man page! I might just need to get one of those and try it out.

Edit: Nevermind... those suckers are expensive!

---

### Post by eyes on 2011-06-11
Hi everyone,

I just realized that I was also concerned by the jump bug with my intuos 4 m.
I've cloned the  xf86-input-wacom git repository and I would like to know which patch I have to apply ?
The jump-patch.txt that sanette has committed for theOGRE or this [one]("http://sourceforge.net/mailarchive/forum.php?thread_name=BANLkTimZUkGELM8mHxdCgRtLgt-QJSAcVQ%40mail.gmail.com&forum_name=linuxwacom-discuss") from the sourceforge.net mail archive ?

---

### Post by sanette on 2011-06-12
Hi eyes

both should do it. But the patch in #202, in addition, corrects the orientation of the touch strips (you have them in Intuos3 or Cintiq). In your case (intuos4) , there is no difference.

---

### Post by eyes on 2011-06-12
Hi sanette,

thank you for your reply. The jump bug is fixed now.
I can now try to understand how I can display icons on my tablet.

---

### Post by theOGRE on 2011-06-13
Are any of you able to map the Super or Hyper keys? I still cannot map them, but I can use them in system hotkeys.


Edit:  I can use Super_R.

---

### Post by sanette on 2011-06-20
> **jon.k said:**
> 
This needs zsh, xdotool and some tool to convert the images to raw icons. I will post this in a bit. _Is there a way to do this with image magick's command line tools?_


Hi Jon.k

AFAIK it is not possible with a simple magick's command line, but I came up with a small bash script that does it:

```

#!/bin/bash -e

# convert a 64x23 image to raw 4bit grayscale data suitable for
# sending to the Intuos4 tablet.

# Remark: 
# convert -depth 4 $image gray:$output
# does not work. For the intuos one byte should encode 2 pixels: one
# on top of the other.

tmpfile=/tmp/abcdefg_tmp
rm -f $tmpfile.raw
image=$@

# first we convert into 8 bit linear grayscale raw data
convert -depth 8 "$image" gray:$tmpfile.gray

declare -a data=($(hexdump -v -e '1/1 "%02X "' $tmpfile.gray))

for y in {0..15}; do
    for x in {0..63}; do
	
	up=${data[$(( y*128 + 63 - x ))]}
	down=${data[$(( (2*y+1)*64 + 63 - x ))]}
	echo -ne \\x${down:0:1}${up:0:1} >> $tmpfile.raw
	
    done
done

cp $tmpfile.raw $image.raw

```

EDIT: the script I first posted was not the last version, sorry. Now it should be ok

---

### Post by Favux on 2011-06-20
Hi sanette,

Ping, over on linuxwacom-discuss, has tested your reverse strip orientation patch and wants to submit it.

---

### Post by sanette on 2011-06-20
> **Favux said:**
> Hi sanette,

Ping, over on linuxwacom-discuss, has tested your reverse strip orientation patch and wants to submit it.


thanks. I'll see this with Ping, then.

---

### Post by Favux on 2011-09-24
Hi everyone,

Good news!

Eduard Hasenleithner's fourth patch set "Input: wacom - add Intuos4 LED and OLED control" has been added to the 3.1 kernel:  [https://github.com/dtor/input/commit/5d7e7d479856f23eebc272128905a7ecada367fb](https://github.com/dtor/input/commit/5d7e7d479856f23eebc272128905a7ecada367fb)

He's started on the xsetwacom implementation for the xf86-input-wacom side of things.

---

### Post by amicable on 2011-09-26
That's really great news Favux.

It's going to be a while before I pick that kernel up; I'm on 2.6.38-10-generic-pae.

Can you point me to instructions for patching Eduard's code into my kernel?

Many thanks

---

### Post by Favux on 2011-09-26
Hi amicable,

It would likely be better if sannette or theOGRE etc. gave you the instructions.  After all they've actually done it.

Appendix 1 on the [Linux Wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") shows you how to download the Ubuntu kernel source code and patch the wacom_wac.c.  That should at least get you started since I doubt you want to role a generic kernel.  Appendix 2 shows you how to implement a DKMS for wacom.ko.  There are Ubuntu wiki's on compiling the kernel and DKMS of course.

You could get some hints starting with post #183 on the thread and on:  [http://ubuntuforums.org/showpost.php?p=10885415&postcount=183](http://ubuntuforums.org/showpost.php?p=10885415&postcount=183)

BTW Eduard has already submitted the first xsetwacom patch set to xf86-input-wacom's linuxwacom-devel mailing list:  [http://sourceforge.net/mailarchive/forum.php?thread_name=1316982193-27527-1-git-send-email-eduard%40hasenleithner.at&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=1316982193-27527-1-git-send-email-eduard%40hasenleithner.at&forum_name=linuxwacom-devel)  He's waiting for Peter to review it.  Notice he says the OLED's are coming in kernel 3.2 not 3.1.

---

### Post by Favux on 2011-09-26
Hi again everyone,

Eduard just posted a backport for the OLED's.  It looks like it's for Natty (and maybe Oneiric?):  [http://sourceforge.net/mailarchive/forum.php?thread_name=1317065693-30605-1-git-send-email-eduard%40hasenleithner.at&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=1317065693-30605-1-git-send-email-eduard%40hasenleithner.at&forum_name=linuxwacom-devel)

Edit:  It's now in the input-wacom repository.  To clone the input-wacom repository see appendix 2 in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by a.nvlkv on 2011-10-15
> **Favux said:**
> Hi again everyone,

Eduard just posted a backport for the OLED's.  It looks like it's for Natty (and maybe Oneiric?):  [http://sourceforge.net/mailarchive/forum.php?thread_name=1317065693-30605-1-git-send-email-eduard%40hasenleithner.at&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=1317065693-30605-1-git-send-email-eduard%40hasenleithner.at&forum_name=linuxwacom-devel)

Edit:  It's now in the input-wacom repository.  To clone the input-wacom repository see appendix 2 in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").
Hi Favux,

I have problem with Oneiric.
I follow appendix 2 in [HOWTO]("http://ubuntuforums.org/showthread.php?t=1515562") above, and it stops on cp. There is no wacom.ko in input-wacom/2.6.36. And of course no folder for 3.0.0. Please advise what to do now.

---

### Post by Favux on 2011-10-16
Hi a.nvlkv,

Welcome to Ubuntu forums!

It is telling me:
```
configure: WARNING: kernel version 3.0.0-12-generic not supported
```
It doesn't seem to be throwing up any errors so perhaps the make files just need to be modified to build.  But looking through them they are very complicated and I don't see an obvious place yet to make the modification.  So we may have to wait until input-wacom is updated to support the 3.0 kernel (if ever) if we want to use input-wacom.

The other option is to apply the patch to the 3.0 kernel as described in appendix 1 from the [LinuxWacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  It looks fairly straightforward involving just the wacom.ko if you ignore the documentation stuff:  [https://github.com/dtor/input/commit/5d7e7d479856f23eebc272128905a7ecada367fb](https://github.com/dtor/input/commit/5d7e7d479856f23eebc272128905a7ecada367fb)

But I have to say with the bug currently affecting Wacom tablets in Oneiric using Gimp etc. is it worth putting time into Oneiric until the bug is fixed?  Or are you not getting the extra lines being thrown off and the pressure and left click problems?

---

### Post by Favux on 2011-10-16
Looks like amonpaike has come up with a work around for compiling input-wacom on the 3.0 kernel:  [http://ubuntuforums.org/showpost.php?p=11353751&postcount=816](http://ubuntuforums.org/showpost.php?p=11353751&postcount=816)

After he cloned the git repository:
```
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/input-wacom

```
He changed directory into the 2.6.36 folder:
```
cd /imput-wacom/2.6.36/
```
Then he manually compiled the input-wacom wacom.ko with:
```
make -C /lib/modules/$(uname -r)/build SUBDIRS=$(pwd) modules
```
Copied it into place:
```
sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/

```
Then removed the old wacom.ko and replaced it with the new one:
```
sudo rmmod wacom

sudo modprobe wacom
```
Rather than doing the last bit I'd suggest:
```
sudo depmod -a
```
and rebooting.

---

### Post by sanette on 2011-12-04
* just a remark: I switched to Oneiric, and I was too lazy to
reinstall the git.

But I was happy to notice that my old tarball in post #214 still works  ! (it contains the patched wacom.h for OLED support, and various oled utilities) --> I still have my nice little OLED images ;)

* Favux, you mention the Gimp bug where bad lines pop up. I noticed this too. Could you direct me to a thread where this is discussed ?

---

### Post by Favux on 2011-12-04
Hi sanette,

That's good to hear.  Eduard's xsetwacom support for OLEDs seems to have stalled.  Then Peter said some cryptic things that worried me a little.

The bug report:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)

The work around is to update Gimp from 2.6 to 2.7 if you can.  Because 2.7 has the history buffer removed.  Presumably the bug is in Oneiric's X stack and the history buffer makes it painfully obvious in the default Gimp.

---

### Post by sanette on 2011-12-05
Mmm I see, this is quite a serious bug, making
gimp really unusable.

I thought it could be similar to the bug I had on the Toshiba Portege M750 tablet PC, but not at all. This one was easy to patch.

By the way I noticed something strange in Xournal: if you draw near the bottom-right corner of the screen, cursor motion is very slow and lags behind the cursor.

This doesn't happen in Gimp or Inkscape.

Anyone has this too ?

---

### Post by Favux on 2011-12-05
Haven't noticed it.  I was getting a lag in Gimp in addition to the lines until I used Ingo's PPA with Alexia's history buffer disabling patch.  That's made Gimp usable for me.

---

### Post by Teacher Lion on 2011-12-08
Hi folks,

I've been posting on [http://ubuntuforums.org/showthread.php?t=1120029&page=30](http://ubuntuforums.org/showthread.php?t=1120029&page=30) for the past while but Favux reckons I should post here. So that is what I am doing!

I have been trying to get the LEDs working on my Intuos4 Small.

I found this bit of info ealier...

> Concerning the led kernel patch, I don't know...

One could try to modify line 695 of wacom_sys.c:
replace >= INTUOS4 by >= INTUOS4S
and see what happens...

I don't have an Intuos 4S to test...

Incidentally, there isn't a single instance of INTUOS4 in any of the script. So I don't think the above is going to work. Line 695 in wacom_sys.c is different in all the different folders. I don't think any of it is what the above post was getting at!

I have no idea where to go from here! Could anyone kindly point me in the right direction?!

Many thanks in advance!

---

### Post by Teacher Lion on 2011-12-08
OK, I've just been in GIMP messing around with my currently LED-flawed Intuos. The various Wacom parts were recognised in the extended input devices area. That is good.

Most of the forums I've been on seem very techie. It has taken me hours to trawl through stuff and I'm not much the wiser. So... I hope noone minds me asking this...

Is there any chance that I will... at any point in the future... be able to use GIMP with my Wacom Intuos4 Small and change colours, zoom in, zoom out, change brush sizes, change brush types, etc. all with the help of my trusty pad wheel?

I just want to know if this is going to end up being a massive waste of time! I'll do my best to get it sorted but I'm just not sure if this is even possible!

---

### Post by sanette on 2011-12-09
Hi Teacher Lion

you have 2 issues

(1). having your four leds light on and off
(2). using your wheel for different actions

I remember vaguely someone doing (1) with success. I can try to search

(2) is "easy". Here is how you can do

- in **gimp**, assign shortcuts to actions you like (zoom, etc.)
(some are assigned by default, but you can add almost anything you like in Edit-> Keyboard shortcuts)

- map your Intuos wheel to these shortcuts using **xsetwacom**

- better: write a shell script to do this, and which allows several "profiles" (I wrote one below)

- with you window manager kde/gnome, assign a global shortcut that will trigger this script. (Choose a rare key combination)

- with **xsetwacom**, map your central wheel button to this shortcut.

Are you still with me ?

Here is the script that I propose for this
(I haven't tested it, I don't have my intuos now)

```

#!/bin/bash

# launch this script to switch to the next "state" for Intuos4 wheel action

# GIMP remark: you need to configure gimp shortcuts. 
# Go to Edit-> Keyboard shortcuts
# Here are the defaults used in this script:
# "Decrease brush scale" -> "CTRL -"
# "Increase brush scale" -> "CTRL +"
# "Zoom in" -> "+"
# "Zoom out" -> "-"
# "Foreground Swatch Color Next" -> "0"
# "Foreground Swatch Color Previous" -> "9"


# detect device
id=$(xsetwacom list | sed -n 's|Wacom.* pad.*id: \([0-9]*\).*|\1|p')
if [ "A${id}B" == "AB" ]
then 
    echo "No Wacom pad device detected ! Aborting."
    exit
else echo "Using pad device number $id"
fi

# read current state number
tmpfile=/tmp/wacom_wheel_state
touch $tmpfile
state=$(cat $tmpfile)
if [ "A${state}B" == "AB" ]; then state=0; fi

# increase to next state
state=$(( $state + 1 ))
if [ $state = 5 ]; then state=1; fi

# set keys
case $state in
    1)
	echo "Setting ZOOM"
	xsetwacom set $id RelWheelUp "key Shift plus"
# WARNING: if you don't need to hold SHIFT to get a "+", 
# then replace "keyShift plus" by "key plus"
# (same applies below...)
	xsetwacom set $id RelWheelDown "key minus"
	;;
    2)
	echo "Setting BRUSH SCALE"
	xsetwacom set $id RelWheelUp "key Ctrl Shift plus"
	xsetwacom set $id RelWheelDown "key Ctrl minus"
	;;
    3)
	echo "Setting COLOR SWATCH"
	xsetwacom set $id RelWheelUp "key Shift 0"
	xsetwacom set $id RelWheelDown "key Shift 9"
	;;
    4)
	echo "Setting ???"
	;;
    *)
	echo "This should NOT happen !"
	state=0
esac

# save new state number
echo $state > $tmpfile

exit

```

Beware, there is a caveat in xsetwacom (at least the version I have in 11.10): for instance the keywork "key plus"
refers to the key that has "+" on it, but on my keyboard in fact it will give me what I get if I press the key, which is "=" not "+" !!  (since "+" needs a "SHIFT")

same for "key 0" which gives me "à" :(

---

### Post by Teacher Lion on 2011-12-09
Hi sanette,

What you have written makes sense to me! I'll give it a shot! It'll probably take me ages (everything does) but I should be able to report back in the next day or so!

Thank you for your help.

---

### Post by sanette on 2011-12-09
ok, let me know

for the leds, it should work (theOgre did it in this thread)

It is maybe more tricky since you have to patch and recompile the kernel driver wacom.ko

(I don't remember the best "official" procedure to do this
but I have a personal package which does it for me.)

---

### Post by sanette on 2011-12-09
@Teacher Lion

I didn't notice that you have Ubuntu 9.10

If this is still the case, then xsetwacom syntax is probably different, beware.

---

### Post by Teacher Lion on 2011-12-09
Hi sanette!

I don't! I'm using 10.04 and I don't live in Bangkok anymore!! I'm not allowed to change my details because I don't have permission!!

Bit of a mad system if you ask me!!

---

### Post by Teacher Lion on 2011-12-09
Hi sanette,

No luck this end. The keys on my Intuos4 still don't do anything. I went into system-->prefences-->keyboard shortcuts and just assigned a simple gedit command to test the buttons. None of them are working.

I have been jumping between one file and the next. The first thing I noticed was that the shell script I was using at startup referred to a Wacom Intuos4 6x9. Or some size similar. So I changed that to 4x6 then I restarted. Still no luck. It was a shell script for Intuos4 that Favux uploaded some time back. I think.

Now apparently I need to recompile to get the LEDs working. Which is the Step 1 bit in this thread [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
It won't help. Ogre was using a different sys file to me. I went into the wacom_sys.c file to have a look around but nothing resembled what he was talking about. Line 695 was different.

After hours of messing around for the past few days, I have managed to get the wheel working. I can use it to scroll up and down in Chrome. Just like the trusty scroll wheel on my mouse. My computer... it now seems... is mocking me.

I'm giving up for the time being. Will try again from scratch later.

---

### Post by sanette on 2011-12-09
Teacher Lion

I'm not sure exactly whay you tried.

Can you do the following, in a terminal:

```
xsetwacom list
```

it should give you a list of recognized wacom devices.

```
id=$(xsetwacom list | sed -n 's|Wacom.* pad.*id: \([0-9]*\).*|\1|p')
echo $id
```

It should print the number of the "pad" device

```
xsetwacom set $id RelWheelUp "key a"
xsetwacom set $id RelWheelDown "key b"
```

Then play with your scroll wheel in both directions--> it should print a's and b's like this
aaaaaabbbbbababaaaabbb

If all of this works, you are in a very good shape !

---

### Post by Favux on 2011-12-09
Hi Teacher Lion,

I discovered the reason for the permission problem.  They made a change a little while ago to cut down on spam or something.  I didn't know that!  You have to have at least 50 posts to be able to edit your User CP.  So the change must have happened after you signed up and went on the forums the first time.  But at 34 you're rapidly closing in on the required number.  See:  [http://ubuntuforums.org/showthread.php?t=1847191](http://ubuntuforums.org/showthread.php?t=1847191)

---

### Post by Teacher Lion on 2011-12-09
@ Favux

Thank you for checking that out! I've never had a problem being verbose! Should be able to get that fixed in no time!

@ sanette

I'm giving that a try now!

---

### Post by Teacher Lion on 2011-12-09
Hi sanette,

That last bit didn't work. I did find out the ID number. It is 19.

> adam@mixbreed-a8dc:~$ xsetwacom list
Wacom Intuos4 4x6 stylus        	id: 12	type: STYLUS    
Wacom Intuos4 4x6 eraser        	id: 17	type: ERASER    
Wacom Intuos4 4x6 cursor        	id: 18	type: CURSOR    
Wacom Intuos4 4x6 pad           	id: 19	type: PAD       
adam@mixbreed-a8dc:~$ id=$(xsetwacom list | sed -n 's|Wacom.* pad.*id: \([0-9]*\).*|\1|p')
adam@mixbreed-a8dc:~$ echo $id
19
adam@mixbreed-a8dc:~$ xsetwacom set $id RelWheelUp "key a"
adam@mixbreed-a8dc:~$ xsetwacom set $id RelWheelDown "key b"
adam@mixbreed-a8dc:~$ 

---

### Post by Teacher Lion on 2011-12-09
I then tried replacing $id with 19. That didn't work either. Now I'm just taking stabs in the dark!!

---

### Post by Favux on 2011-12-09
Hi Teacher Lion,

Did you update your xf86-input-wacom along with input-wacom?  I recall you were having trouble with the macro update.  If you still have the Lucid default xf86-input-wacom-0.10.5 that could be part of the problem.  You should be able to determine your version by entering in a terminal:
```
xsetwacom -V
```

Also for the script you downloaded from the BambooPT HOW TO to work correctly you have to use the current "device name" *xinput list* returns for you.  So in the script not just change the size unless that made the entire name identical to the one from *xinput list*.  For example for pad you have:
```
"Wacom Intuos4 4x6 pad"
```
for the "device name" and that's what should be used in the script.  The ID# can change which is why you use the "device name" in a script.  Sanette's line finds the current ID number in use, so it doesn't matter if it changed during a hotplug or startup, which is why it works for his stuff.

---

### Post by Teacher Lion on 2011-12-09
This is what xsetwacom -V does...

> adam@mixbreed-a8dc:~$ xsetwacom -V
0.12.0
adam@mixbreed-a8dc:~$ 

As far as keeping everything identical to the device name, I think I've done that. The trouble is that I've been going round in circles for a long time.

How might I go about trying to diagnose the problem? I could conceivably upload different bits and pieces.

I'm going to have another stab at it now from scratch.

---

### Post by Teacher Lion on 2011-12-09
Ignore.

---

### Post by Teacher Lion on 2011-12-09
OK, whilst I do feel like a complete idiot I also feel like I'm learning.

I now appreciate the value of going through the shell script and changing everything. If you run them in the terminal it gives you a readout of all the stuff that isn't working. I replaced all the device name parts, AbsWheelUp, AbsWheelDown, all the obvious stuff. Here is what I get now...

> adam@mixbreed-a8dc:~$ sh xsetwacom.sh
Cannot parse keyword '+' at position 1
Note: The "core" keyword is not supported anymore and will be ignored.
Cannot parse keyword '-' at position 1


Now... how do I make it love me?!

Thanks for all your help! I imagine this might be very irritating reading for you but at least I'll be less of a noob once I've got it all working!

---

### Post by Favux on 2011-12-09
The parameter name syntax was changed from Buttonx to Button x, so:
    Button1
becomes
    Button 1
and so on.  Just adding the space fixes it.

---

### Post by Teacher Lion on 2011-12-09
@ sanette

This is what your script does! It only seems to cycle through different sorts of errors but I have read through the script and tomorrow morning I think I might be able to have a go at fixing it up. The wheel has been misbehaving but I can now perform the 'aaabbbaabbaa' trick!

> adam@mixbreed-a8dc:~$ sh modes.sh
[: 23: A19B: unexpected operator
Using pad device number 19
[: 29: A1B: unexpected operator
Setting BRUSH SCALE
adam@mixbreed-a8dc:~$ sh modes.sh
[: 23: A19B: unexpected operator
Using pad device number 19
[: 29: A2B: unexpected operator
Setting COLOR SWATCH
adam@mixbreed-a8dc:~$ sh modes.sh
[: 23: A19B: unexpected operator
Using pad device number 19
[: 29: A3B: unexpected operator
Setting ???
adam@mixbreed-a8dc:~$ sh modes.sh
[: 23: A19B: unexpected operator
Using pad device number 19
[: 29: A4B: unexpected operator
Setting ZOOM


> for the leds, it should work (theOgre did it in this thread)

I'm still completely lost on this! I have been through wacom_sys.c many times. Alas... to no avail.

It has felt like I've been banging my head against a brick wall all day but I'm really pleased things have started to work. I don't feel like anywhere near as much of a retard as I did 24 hours ago!

Thank you, everyone!

---

### Post by sanette on 2011-12-10
Hi Teacher Lion

it seems that you are executing a bash script with sh.
Instead, try

```
chmod 755 modes.sh
```

and then execute with

```
./modes.sh
```

(and don't forget the magic #!/bin/bash line in the script)

---

### Post by sanette on 2011-12-10
Teacher Lion:

I have finally tested my script with my intuos 4 (M),
indeed there was a mistake:
you should not use RelWheelUp/RelWheelDown, but instead
**AbsWheelUp/AbsWheelDown** (don't ask me why)

Apart from this, it works well.

---

### Post by sanette on 2011-12-10
> **Teacher Lion said:**
> @ sanette

I'm still completely lost on this! I have been through wacom_sys.c many times. Alas... to no avail.

It has felt like I've been banging my head against a brick wall all day but I'm really pleased things have started to work. I don't feel like anywhere near as much of a retard as I did 24 hours ago!

Thank you, everyone!

this part is more difficult. You can try this:
(I'm not sure it works for ubuntu 10.04. It should work for 11.04 and 11.10, but one never knows)

download the archive I posted in #214

[http://ubuntuforums.org/showpost.php?p=10921962&postcount=214](http://ubuntuforums.org/showpost.php?p=10921962&postcount=214)

extract it:

```
tar xvf intuos-utils.tar.gz
```

go in the kernel directory:

```
cd intuos-utils-current/kernel-2.6.38/
```

(don't be afraid of the number 2.6.38. I have kernel 3.0.0-13 and it still works perfectly)

then

```
make
sudo ./install
```

(don't worry, it backups the original wacom.ko -> wacom.ko.orig)

If it works, your small led should change luminance when you press the stylus.

(you might try to reboot at that point -- but not necessary in principle)

Then you switch on the second led by

```
./intuos-led -select-led 1
```

(of course you can replace "1" by 0,1,2,3)

It works for my Intuos.

---

### Post by sanette on 2011-12-10
wow ! I didn't notice this annoucement:

> Wacom Control Panel
   1.20  
[http://gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309](http://gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309)

UPDATE New version is currently underway. I so far have better tablet detection, the new features of xsetwacom implemented, Intuos4 OLEDs working with both images, text and animations and application profiles that automatically switch the button configuration. Please hang in there everyone, I know the current version up here sucks and this overhaul is long overdue. Check back in a month or two.

finally! this sounds great !

---

### Post by Favux on 2011-12-10
Maybe I'm completely missing something Teacher Lion but you shouldn't need to do anything to wacom_sys.c anymore.  Adding the Intuos4 small has already been done, see this commit:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/input-wacom;a=commit;h=60ed79f71119e0e0a7c2cc1fec6146ef53a4d706](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/input-wacom;a=commit;h=60ed79f71119e0e0a7c2cc1fec6146ef53a4d706)  If you look at the wacom_sys.c diff you'll see:
```
+       /* Initialize default values */
+       switch (wacom->wacom_wac.features.type) {
+       case INTUOS4S...INTUOS4L:
+               wacom->led.select[0] = 0;
+               wacom->led.select[1] = 0;
+               wacom->led.llv = 10;
+               wacom->led.hlv = 20;
+               error = sysfs_create_group(&wacom->intf->dev.kobj,
+                                          &intuos4_led_attr_group);
+               break;
```
So as long as you've compiled input-wacom-0.12.0 you should have it.

As far as I can tell you just need sanette to show you how to manipulate the LEDs since the xsetwacom part of it hasn't been finished yet.


Hi sanette,

That would really be excellent if that thing finally started working.  It's always been busted the couple times I've tried it and just messed things up.  But it seems like it may take forever for the Gnome Wacom tablet applet to get anywhere.

---

### Post by sanette on 2011-12-11
> **Favux said:**
> 
So as long as you've compiled input-wacom-0.12.0 you should have it.

Ah, I did not realize this. Good. (I'm still using the ubuntu "official" xf86-input-wacom-0.11.0)

> **Favux said:**
> 
As far as I can tell you just need sanette to show you how to manipulate the LEDs since the xsetwacom part of it hasn't been finished yet.


If this hasn't changed, this is just something like this:


```
event=$(readlink /dev/input/wacom)
leddir=/sys/class/input/$event/device/led
echo "1" > $leddir/buttons_luminance
```

The first 2 lines are just for guessing the right /sys/class/input/event??/device/led directory.

In the last line you may replace "1" by "0", "1", "2", "3", to select the desired led.




> **Favux said:**
> 
Hi sanette,

That would really be excellent if that thing finally started working.  It's always been busted the couple times I've tried it and just messed things up.  But it seems like it may take forever for the Gnome Wacom tablet applet to get anywhere.

I see. That's too bad.

---

### Post by Teacher Lion on 2011-12-11
Wow! I just got back home after a massive two day Christmas shopping spree and am overwhelmed with the amount of info I have to process! I'll do my best to do justice to it, though! Promise!

Thank you both enormously.

I desperately need rest. However, I'll have a few hours tomorrow morning to try and get a proper grasp of all this.

Good night!

---

### Post by Favux on 2012-02-17
**[SIZE="3"]FYI Update:[/SIZE]**

Hi everyone,

Some not so good news.  It looks like the xsetwacom support for the OLEDs and LEDs we have been waiting for will not be coming anytime soon.  If I am tracking the argument correctly Peter has vetoed adding it to xf86-input-wacom:  [http://sourceforge.net/mailarchive/message.php?msg_id=28814445](http://sourceforge.net/mailarchive/message.php?msg_id=28814445)  I have no idea when XI 2.3 is due out.  Could be quite a while.  That's from this linuxwacom-devel thread:  [http://sourceforge.net/mailarchive/forum.php?thread_name=CAF8JNhK6%3DvdFtXAYK6iX7UJo6%3DxSduaaUK63d94pGkg5V15s0Q%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=CAF8JNhK6%3DvdFtXAYK6iX7UJo6%3DxSduaaUK63d94pGkg5V15s0Q%40mail.gmail.com&forum_name=linuxwacom-devel)  That's unfortunate because it seems Eduard Hasenleithner's (got the sysfs for Intuos4 OLED and LED added to the 3.2 kernel) xsetwacom efforts picked up by Ping Cheng and now by Jason Gerecke are for naught.

It appears we're suppose to continue using an applet.  Bastien Nocera, who is working on the Gnome Wacom tablet applet for System Settings, was asking about the OLEDs and LEDs.  Since he is also working on [libwacom]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Libwacom") as part of that it is possible something may happen there.  But maybe we should assume we're going with the Karg/sanette applet for the foreseeable future.


Edit:  The latest (the third version?) of the applet posted by sanette is here:  [http://ubuntuforums.org/showpost.php?p=10921962&postcount=214](http://ubuntuforums.org/showpost.php?p=10921962&postcount=214)

---

### Post by gamamoto on 2012-04-23
Are there new updates about this project ?

I followed this tutorial : [http://www.davidrevoy.com/index.php?article70/set-the-led-display-of-the-wacom-intuos4-tablet-on-ubuntu-linuxmint](http://www.davidrevoy.com/index.php?article70/set-the-led-display-of-the-wacom-intuos4-tablet-on-ubuntu-linuxmint)

but i'm having some issues with my intuos4L :

[LIST]
[*]when i launch the sript found in this tutorial the icons display well but the key bindings are not working.
[/LIST]
I get this error message :

```
Cannot find device '11'.
```Where 11 is my pad.
I guess my script disconnects the tablet as xinput --list |  grep '[w|W]acom' returns nothing and i can't click with the stylus.

[LIST]
[*]My second issue is that if i set the key bindings 'correctly' (the icon parts are commented), if i get my stylus close to the tablet so it will move the mouse pointer the bindings won't work and when i get my stylus out the bindings work well.
[*]Third, the touch ring is fully functionnal when pluging in the tablet at first but deactivates when running the script. It also deactivates my mouse in gimp drawing area -.-"
[/LIST]
Here is my script :
```

#! /bin/bash
###############
# LED Display :
###############

# path :
LEDPROGRAMPATH=~/Script/Intuos4-LED/src/intuos4-led-config
ICONPATH=~/Script/Intuos4-LED/icons

echo "Wacom Intuos4 LED icon and configuration"
sudo modprobe -r wacom
sudo $LEDPROGRAMPATH --button 1 --image $ICONPATH/icon-Sélection.png
sudo $LEDPROGRAMPATH --button 2 --image $ICONPATH/icon-Bucket.png
sudo $LEDPROGRAMPATH --button 3 --image $ICONPATH/icon-Pinceau.png
sudo $LEDPROGRAMPATH --button 4 --image $ICONPATH/icon-Crayon.png
sudo $LEDPROGRAMPATH --button 5 --image $ICONPATH/icon-ctrl.png
sudo $LEDPROGRAMPATH --button 6 --image $ICONPATH/icon-shift.png
sudo $LEDPROGRAMPATH --button 7 --image $ICONPATH/icon-redo-arrow.png
sudo $LEDPROGRAMPATH --button 8 --image $ICONPATH/icon-undo-arrow.png
sudo modprobe wacom
sleep 1

#################
# Wacom buttons :
#################
# tablet identificators :
# xinput --list | grep '[w|W]acom'

#DEVICE="Wacom Intuos4 6x9 pad"
#STYLUS="Wacom Intuos4 6x9 stylus"
ERASER=10
CURSOR=11
STYLUS=12


# Buttons
#  _________
# | Button2 |
# |_________|
# | Button3 |
# |_________|
# | Button4 |
# |_________|
# | Button5 |
# |_________|
#    _________
#   /         \ <-- Touchring 
#  /    ___    \
# |    /   \    |
# |   |   <-|---|-- Button1
# |    \___/    |
#  \           /
#   \_________/
#  _________
# | Button6 |
# |_________|
# | Button7 |
# |_________|
# | Button8 |
# |_________|
# | Button9 |
# |_________|

# /!\ WARNING /!\
# The keyboard is in qwerty mode for the tablet ! 
xsetwacom --set "$CURSOR" Button2 "key r"
xsetwacom --set "$CURSOR" Button3 "key shift b"
xsetwacom --set "$CURSOR" Button4 "key p"
xsetwacom --set "$CURSOR" Button5 "key n"
# ---
xsetwacom --set "$CURSOR" Button1 "key x" 
# ---
xsetwacom --set "$CURSOR" Button6 "key ctrl"
xsetwacom --set "$CURSOR" Button7 "key shift"
xsetwacom --set "$CURSOR" Button8 "key ctrl y"
xsetwacom --set "$CURSOR" Button9 "key ctrl w"

#-- Stylus
#xsetwacom --set "$STYLUS" Button1 "key t" # Pointe stylet
xsetwacom --set "$STYLUS" Button2 "key ctrl" # Bouton 1

```

Note : hope my post isn't too long and my english not too bad.
best regards

---

### Post by Favux on 2012-04-23
Hi gamamoto,

Welcome to Ubuntu forums!

Hopefully sanette or one of the other experts will jump in.

In the meantime what is the output of *xinput list* when things are working?  And when things aren't working?

My first thought is the ID # is changing since you seem to have 11 hardcoded as the pad:
```
CURSOR=11
```
or maybe the wacom.ko isn't being reloaded after the modprobe removes it.  If that was happening you would see **wacom** in *lsmod* when working and it would be missing when things weren't working.

By the way cursor refers to the Wacom puck or tablet mouse.  Pad is for the ExpressKeys.  So it would be less confusing if you used:
```
PAD=11
```
and
```
xsetwacom --set "$PAD" Button2 "key r"

etc.
```

Edit:  I just noticed the syntax for button is wrong in your script if you have a relatively recent xf86-input-wacom.  Starting with I believe xf86-input-wacom-0.10.11 a space was added between Button and the button number.  So the above xsetwacom command should read:
```
xsetwacom --set "$PAD" Button 2 "key r"
```
and the same for all of the other pad xsetwacom commands.  That may be your problem.  You can determine your xf86-input-wacom version by running the command:
```
xsetwacom -V
```

---

### Post by gamamoto on 2012-04-29
Thanks for your quick answer, as I didn't have my tablet with me i only answer you now.
I did change my Button2 by Button 2 but those aren't recognised. When I type** xsetwacom --list param** I get this :
```

Button1          - X11 event to which button 1 should be mapped. 
Button2          - X11 event to which button 2 should be mapped. 
Button3          - X11 event to which button 3 should be mapped.
etc...

```So the bindings don't work.

My xsetwacom version is :
```
0.10.5
```

Also pressing the keys on the pad make my mouse pointer go to the top-left corner of the screen.

---

### Post by Favux on 2012-04-29
Hi gamamoto,

OK, we're getting somewhere.  From your xf86-input-wacom-0.10.5 I infer you are using Ubuntu Lucid (10.04).  That's the problem.  You need to update both your wacom.ko (the kernel driver/module) and xf86-input-wacom (the X driver).

The cursor going to the top left corner is an old bug that is fixed in the newer drivers.

So install input-wacom-0.13.0 for the wacom.ko and xf86-input-wacom0.14.0.  You can use part I. and II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or sections 1 and 2 of the [Linux Wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") to do that.  Although section 2 actually clones xf86-input-wacom rather than using the 0.14.0 tar.

After doing that then the OLED applet should start working for you.

---

### Post by gamamoto on 2012-04-29
After following your advices and making some modifications to my script so it corresponds to the new parameters I end up having this output after launching my script :
```

Wacom Intuos4 LED icon and configuration
Cannot find device 'Wacom Intuos4 8x13 pad'.

```

Seems that my tablet is disconnected. When i do xsetwacom --list devices it returns nothing.

---

### Post by Favux on 2012-04-29
You updated both the wacom.ko and xf86-input-wacom?

What does the output of:
```
xinput list
```
look like?

---

### Post by gamamoto on 2012-04-29
Yes I updated both !
Here is what i have before using my script :
```

**xinput --list | grep '[w|W]acom'**
&#9116;   &#8627; Wacom Intuos4 8x13 stylus                   id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 eraser                   id=16    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 cursor                   id=17    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 pad                      id=18    [slave  pointer  (2)]

```And after :
```
**xinput --list | grep '[w|W]acom'**
```nothing...

---

### Post by Favux on 2012-04-29
OK it sounds like the modprobe is failing.  You want to check if the wacom.ko is loaded before you run the script, when you see the Wacom entries in *xinput list*.  So see if:
```
lsmod
```
shows **wacom** in it.  After you run the script and it isn't working is **wacom** still in?
```
lsmod
```

---

### Post by gamamoto on 2012-04-30
Well i got this before AND after launching the script :
```
lsmod | grep wacom
wacom                  37277  0 

```

It's quite strange, if I understand what you said wacom.ko is loaded even after I ran my script which means it does not come  from the modprobe.
Perhaps i should try another way of displaying those icons.

While i'm here I noticed that now when the icons display my stylus and my keys won't work.

---

### Post by Favux on 2012-05-07
Alright since **wacom** (the wacom.ko) is in *lsmod* that would imply that the problem is with the Wacom X driver.  Perhaps the Intuos4 is not being re-associated with the Wacom X driver after what I guess is a hot plug event when you run the script.  You should be able to determine if that is what is happening by looking at your Xorg.0.log in /var/log.  Search **wacom** when you open it up in gedit.  It may also give you a clue as to what is going wrong.

When you see your tablet's input devices after an ***xsetwacom list*** it means both the Wacom kernel and X driver are working just as with ***xinput list***.  And by the way you can use that instead of ***xinput --list | grep '[w|W]acom'***.  With ***xinput list*** you have to use the fact that stylus, eraser, pad, and cursor are appended to the parent <device name> to verify the tablet is on the Wacom X driver.

---

### Post by gamamoto on 2012-05-11
The Xorg.0.log wacom section :
```

(II) config/udev: Adding input device Wacom Intuos4 8x13 (/dev/input/event14)
(**) Wacom Intuos4 8x13: Applying InputClass "evdev tablet catchall"
(**) Wacom Intuos4 8x13: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.14.99
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Wacom Intuos4 8x13: always reports core events
(**) Option "Device" "/dev/input/event14"
(II) Wacom Intuos4 8x13: type not specified, assuming 'stylus'.
(II) Wacom Intuos4 8x13: other types will be automatically added.
(--) Wacom Intuos4 8x13 stylus: using pressure threshold of 27 for button 1
(--) Wacom Intuos4 8x13 stylus: Wacom USB Intuos4 tablet maxX=65024 maxY=40640 maxZ=2047 resX=200000 resY=200000  tilt=enabled
(II) Wacom Intuos4 8x13 stylus: hotplugging dependent devices.
(EE) Wacom Intuos4 8x13 stylus: Invalid type 'touch' for this device.
(II) Wacom Intuos4 8x13 stylus: hotplugging completed.
(II) XINPUT: Adding extended input device "Wacom Intuos4 8x13 stylus" (type: STYLUS)
(**) Wacom Intuos4 8x13 eraser: always reports core events
(**) Option "Device" "/dev/input/event14"
(**) Option "Type" "eraser"
(--) Wacom Intuos4 8x13 eraser: Wacom USB Intuos4 tablet maxX=65024 maxY=40640 maxZ=2047 resX=200000 resY=200000  tilt=enabled
(II) XINPUT: Adding extended input device "Wacom Intuos4 8x13 eraser" (type: ERASER)
(**) Wacom Intuos4 8x13 cursor: always reports core events
(**) Option "Device" "/dev/input/event14"
(**) Option "Type" "cursor"
(--) Wacom Intuos4 8x13 cursor: Wacom USB Intuos4 tablet maxX=65024 maxY=40640 maxZ=2047 resX=200000 resY=200000  tilt=enabled
(II) XINPUT: Adding extended input device "Wacom Intuos4 8x13 cursor" (type: CURSOR)
(**) Wacom Intuos4 8x13 pad: always reports core events
(**) Option "Device" "/dev/input/event14"
(**) Option "Type" "pad"
(--) Wacom Intuos4 8x13 pad: Wacom USB Intuos4 tablet maxX=65024 maxY=40640 maxZ=2047 resX=200000 resY=200000  tilt=enabled
(II) XINPUT: Adding extended input device "Wacom Intuos4 8x13 pad" (type: PAD)
(II) config/udev: Adding input device Wacom Intuos4 8x13 (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)

```Here is what i get with xinput list before launching script :
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Laser Mouse                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 stylus                   id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 eraser                   id=16    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 cursor                   id=17    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 pad                      id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```And this what i get after :
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Laser Mouse                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```So as you can see the tablet disappears. I do not see any bug there but perhaps with your lynx eyes you'll catch the error.

May I suggest that my script to lit up oleds is depreciated and i should try and catch a new version ?

Thanks for your answers. :)

Ps : i do not have my tablet with me during the week that's why only naswer you now.

---

### Post by Deevad on 2012-07-01
> **gamamoto said:**
> 
May I suggest that my script to lit up oleds is depreciated and i should try and catch a new version ?

Yes, on your previous message you quote my website for a OLED wacom tutorial ( [http://www.davidrevoy.com/article70/set-the-led-display-of-the-wacom-intuos4-tablet-on-ubuntu-linuxmint](http://www.davidrevoy.com/article70/set-the-led-display-of-the-wacom-intuos4-tablet-on-ubuntu-linuxmint) ). It's written in red it's only for Ubuntu 10.10 ; so depreciated is a right terms if you try to make it run on a 12.04.

I also wait solution for making them works again. Almost 1 years without OLED for the moment.

---

### Post by gamamoto on 2012-07-02
As said by Favux i'm running ubuntu 10.04. Now that i'm on vacations i'll have plenty of time to spend on this. I wonder if upgrading my lucid to the new lts 12.04 will change something. Or perhaps changing distibution will do the trick.

As you know there's a tool included in ubuntu to set wacom tablet's buttons and pressure sensivity, i went to the website and the author asewered me that he will not continue the developpement which disapointed mebecause it was really easy to use.

---

### Post by shaun79 on 2012-07-08
It is unfortunate that Ubuntu doesn't have a way to set the tablet pressure curve from the new Gnome Wacom settings in System Settings... Kubuntu lets you do this. Hopefully it won't be too long before you can set the OLEDs from the Gnome settings app, but I read that the work that was done to enable this was blocked by one of the linux wacom people and this is preventing KDE and Gnome from integrating OLED configuration stuff in their applets?

At least you can map the buttons in both Kubuntu/Ubuntu without learning to write or edit scripts (good for new linux users).

> **Deevad said:**
> I also wait solution for making them works again. Almost 1 years without OLED for the moment.

Deevad, you'll be happy to know Christoph (Kargulus) updated his code for Ubuntu 12.04 and xsetwacom 0.14.0 and I can confirm I've got the OLEDs working. :p

[http://braindump.kargulus.de/?p=432](http://braindump.kargulus.de/?p=432)

I've had a few problems with it though. I'm sure that in Oneiric I was able to set the lights and buttons with different scripts as often as I needed for switching between apps with different keyboard shortcuts. But now I can't do that - if I try to change the OLED/button mapping after they've already been set the tablet freezes and I have to restart the computer to use it again. I guess I'll just have to change all the shortcuts to be the same in mypaint/gimp/etc :|

---

### Post by Favux on 2012-07-08
Hi shaun79,

Welcome to the Ubuntu forums!


Thanks for the heads up on the new Precise version of Christoph Karg's OLED applet.  The Gnome Wacom tablet applet does allow you to set stylus and eraser pressure levels.

The freeze things sounds wrong, like you are back to modprobing wacom.ko.  That can't be right, can it?

---

### Post by shaun79 on 2012-07-09
Hi Favux, thanks! I've been lurking around here for a while :p

Of course you're right that you can use the Gnome applet to change the pressure, I just meant you can't edit the pressure curve graphically like you can in KDE: [http://kde-apps.org/content/show.php?content=114856](http://kde-apps.org/content/show.php?content=114856)

> The freeze things sounds wrong, like you are back to modprobing wacom.ko.  That can't be right, can it?
The script does a modprobe -r wacom to set the OLEDS then a modprobe wacom before the xsetwacom commands. Is that what you mean?

Here's a script I use

```
#! /bin/bash

# Device name of the tablet retrieved from xsetwacom
DEVICE="Wacom Intuos4 8x13 pad"
# Path to the tablet config application
LEDCMD=./intuos4-led-config
ICONPATH=/home/shaun/wacom/kargulus/intuos4-led-0.002/icons

sudo modprobe -r wacom
sudo $LEDCMD --button 1 --image $ICONPATH/icon-undo.png
sudo $LEDCMD --button 2 --image $ICONPATH/icon-redo.png
sudo $LEDCMD --button 3 --image $ICONPATH/icon-darker.png
sudo $LEDCMD --button 4 --image $ICONPATH/icon-lighter.png
sudo $LEDCMD --button 5 --image $ICONPATH/icon-increase.png
sudo $LEDCMD --button 6 --image $ICONPATH/icon-decrease.png
sudo $LEDCMD --button 7 --image $ICONPATH/icon-mirror.png
sudo $LEDCMD --button 8 --image $ICONPATH/icon-arrow-up.png
sudo modprobe wacom

sleep 1

xsetwacom --set "$DEVICE" Button 2 "key ctrl z"
xsetwacom --set "$DEVICE" Button 3 "key shift ctrl z"
xsetwacom --set "$DEVICE" Button 8 "key K"
xsetwacom --set "$DEVICE" Button 9 "key L"

xsetwacom --set "$DEVICE" Button 1 "key ctrl"

xsetwacom --set "$DEVICE" Button 10  "key period"
xsetwacom --set "$DEVICE" Button 11 "key comma"
xsetwacom --set "$DEVICE" Button 12 "key ctrl I"
xsetwacom --set "$DEVICE" Button 13 "key ctrl shift F"

xsetwacom --set "$DEVICE" AbsWheelUp "key ctrl minus"
xsetwacom --set "$DEVICE" AbsWheelDown "key ctrl plus"
```I've left a message for Christoph on his blog and he'll probably reply, eventually.

As a kind of workaround at the moment, I'll just split the script in two, and run the oled changer bit once and just change the button mappings as I need to - if that makes sense.

---

### Post by Favux on 2012-07-09
Hi shaun79,

> I just meant you can't edit the pressure curve graphically like you can in KDE
Now I gotcha.  Right plus it is in 25% increments, or was last time I checked, which is a bit ridiculous.
> The script does a modprobe -r wacom to set the OLEDS then a modprobe wacom before the xsetwacom commands. Is that what you mean?
Yep.  I'm thinking that isn't needed anymore with the new sysfs bindings.  Didn't sanette and myself talk about that a few pages back when helping that other Intuos4 user setup?  I can't remember for sure.
> As a kind of workaround at the moment, I'll just split the script in two, and run the oled changer bit once and just change the button mappings as I need to - if that makes sense. 
Sure.  Would like to get rid of the modprobe if it isn't necessary.  Did sanette do that with his last version?  Can't remember that either.  Been too long and since I don't have an Intuos4 all this is theoretical to me.

---

### Post by hissingshark on 2012-07-10
Hi all,

I've been very impressed with the longevity of this thread and the work that has been put in.
It's certainly taken me places I never expected (who would have thought I'd be compiling anything from source?) and looks promising.

I'm trying to get an Intuos4 L working under Ubuntu 12.04 for use with Blender and Gimp.

So far I have managed to get the OLED icon test working after changing the source to accept the Large tablet.  But I too have experienced the total lockup after using modrobe / modprobe -r too many times...

I'm curious about the idea of splitting the script into two parts.  I would have assumed that you'd want to change the icons just as often as the key mappings as the icons describe the purpose of those keymappings!  Unless I suppose you want the same functions available (so same icons) but in different applications (so different short-cut key bindings).  In my case I'd need to change both.

Thanks again for the work everyone and keep it up. Unless I'm missing something this still isn't cracked yet!  Particularly with regard to having switchable profiles as with the Wacom supplied Windows utilities...

Ah, just saw:
[INDENT]Deevad, you'll be happy to know Christoph (Kargulus) updated his code for Ubuntu 12.04 and xsetwacom 0.14.0 and I can confirm I've got the OLEDs working.

[http://braindump.kargulus.de/?p=432](http://braindump.kargulus.de/?p=432)[/INDENT]

Heading over there now to see if this is the holy grail...

---

### Post by hissingshark on 2012-07-10
Oh dear,

Well I,ve tried compiling the latest and greatest from Kargulus.

Similar issues.

The OLED test program works - hurrah.

The profile changing utility does indeed set a profile - hurrah.

But if I try to set the profile a second time (one assumes instigating *rmmod wacom* or *modprobe wacom* internally?) then the terminal just hangs with eternal flashing cursor.
At this point the stylus has no effect on screen and using the ring button no longer cycles its little LEDs.
Disconnecting and reconnecting the tablet does not work.  In fact the tablet doesn't even seem to be powered when reconnected as none of the the ring LEDs even light.
A system reboot is then in order.

Does this describe others' experience?  And what is at fault here?

Regards,

---

### Post by shaun79 on 2012-07-10
Hi hissingshark, yes this is what's happening to me - exactly as you described. 

I've tried changing the OLEDs by commenting out the modprobe lines in the script and while it does work and I can change the OLEDs  - multiple times (yay), you can't actually use the tablet anymore. 

Trying to map a button on the tablet gives this-
```
Cannot find device 'Wacom Intuos4 8x13 pad'.
```I've spent the last couple of hours trawling through the posts here in this thread... and I've been looking at Sanette's stuff [http://ubuntuforums.org/showpost.php?p=10921962&postcount=214](http://ubuntuforums.org/showpost.php?p=10921962&postcount=214)

I haven't tried it out yet but looking through the files it seems it uses 'modprobe wacom' too - I'm going to take a break from it tonight and have another go tomorrow. It's a shame Sanette hasn't posted here since last December as he/she might be able to help. I'm not a programmer and I've only got a basic knowledge of all this :confused:

---

### Post by shaun79 on 2012-07-11
I've been too busy to try Sanette's code today but I've discovered something interesting; My scripts using Christoph's code work flawlessly in Kubuntu, it's under Unity that they fail. 

I have both Unity and KDE desktops installed and as I said in an earlier post I was sure I changed OLEDs often without a problem so I'm guessing I must have been logged into the Kubuntu desktop at the time. It's only recently I've been using Unity regularly. 

So I suspect it might be the Gnome Wacom applet (gnome settings daemon?) causing the failure? Because by default in Kubuntu pressing the round 'mode selector' button on the tablet doesn't effect the small LEDs around it, which is what happens in Unity.

---

### Post by Favux on 2012-07-11
You may be on to something shaun79.  The gnome-settings-daeomon does indeed have "new" hooks added into it for the Wacom Tablet applet.  We should look at those in gconf.  Maybe it is just a question of adding a key(s) for the the OLED's allowing setting of a sysfs key value that way?  I know how to use gsettings/Python to to change key values.

---

### Post by hissingshark on 2012-07-13
Again, I can only confirm *shaun79*'s findings.
After reading about his KDE experience I just built the Christoph downloads of 

[INDENT]intuo4-led-config[/INDENT]

and

[INDENT]setup.py[/INDENT]

on my Kubuntu 12.04 install.

They work great!  No more crashes.
And no, the button in the centre of the scroll wheel no longer works.


Shame that I really don't like the KDE/Kubuntu desktop...

I've some self taught experience of C/C++ so I can play with what others have done, particularly scripts.  But *favux* is way ahead here with talk of gconf, sysfs keys and the like.  Not sure I have much more to contribute here and can only watch with interest.  If I do stumble across anything I'll be sure to post back, although I'm sure I'd be reading about it here first.

---

### Post by Favux on 2012-07-13
Hi hissingshark,

Actually it sounds like we're at about the same place with C.  If it is simple maybe I can do it especially if I can test it and revise it.

So what's really need is for me to bring you guys up to speed on some definitions and so forth and maybe we can figure it out.

First I did not mean the gconf-editor I meant the dconf-editor.  You can use gsettings to update the key values, that's not hard.

dconf-editor isn't installed by default so:  sudo apt-get install deconf-editor
and then run it from a terminal.

You'll see the gnome-settings-daemon's available keys and their values at:
org > gnome > settings-daemon > peripherals > wacom

I'll try to find the stuff on sysfs, although I think I linked to Eduard Hasenleithner's kernel patches a few pages back.

If you do have to remove and then restore the wacom.ko module then oh well.  In that case what we'd probably want to figure out is it enough to  disable the Wacom tablet app or do we need to disable the gnome-settings-daemon's wacom hooks.  In which case we'd probably need to talk to the developers on how to handle all of this.

As soon as I get done with my likely futile efforts to get them to rescind the 1 week post edit limit (so I can update my HOW TO's and continue to maintain them) I can start assembling all my notes on this and try to get back up to speed.  I've kind of been relying on sanette to come back and sort this all out or maybe one of the LWP developers.  Because for e.g. Przemo was working on the Intuos4 wireless and was interested.  I sent him the icon .pngs.  And I think Chris took a look too, maybe.  Anyway that's one of the threads I should dig up.

---

### Post by shaun79 on 2012-07-13
I can now change the OLEDs using the Christoph script under Unity. Thanks Favux for the hint with dconf-editor! Using that I've just had a look at **org > gnome > settings-daemon > plugins > gsdwacom** and unticked "active". Now the tablet doesn't freeze when I change OLEDs more than once. It just means I can't change any tablet setting with the Gnome wacom applet (at least that seems to be the case while experimenting) but I guess that's OK if I'm using scripts anyway.

> Maybe it is just a question of adding a key(s) for the the OLED's allowing setting of a sysfs key value that way?This would be good - it would simplify things a lot :).  I think it's beyond my expertise though as I've read quite a bit over the last couple of days, about sysfs/OLEDs, here and on the linuxwacom mailing list archives but I'm none the wiser what to do sorry.

I'm a lot less confused why things weren't working before though so thanks again Favux, and I hope this helps you too Hissingshark, to get your OLEDs useable in Unity/Gnome.

If ever Sanette comes back here, or Christoph, or one of the linuxwacom developers has a go at this then that'd be really amazing [-o<

---

### Post by Favux on 2012-08-09
Hi everyone,

**[SIZE="3"]FYI Update:[/SIZE]**

Przemo Firszt has just submitted patches to the Linux Wacom Project to enable OLEDs for the Intuos4 wireless model on [linuxwacom-devel]("http://sourceforge.net/mailarchive/forum.php?thread_name=1344534404-22347-2-git-send-email-przemo%40firszt.eu&forum_name=linuxwacom-devel").

He describes how to use the new feature on his blog in two parts:
[http://blog.firszt.eu/index.php?post/2012/07/29/OLED-icons-on-Wacom-Intuos4-Wireless-PTK-540WL](http://blog.firszt.eu/index.php?post/2012/07/29/OLED-icons-on-Wacom-Intuos4-Wireless-PTK-540WL)
[http://blog.firszt.eu/index.php?post/2012/08/02/OLED-icons-on-Wacom-Intuos4-Wireless-PTK-540WL-part-2](http://blog.firszt.eu/index.php?post/2012/08/02/OLED-icons-on-Wacom-Intuos4-Wireless-PTK-540WL-part-2)

---

### Post by Deevad on 2012-08-22
Just a little message here to report that the method described on the "Christoph's Braindump" blog ( [http://braindump.kargulus.de/?p=432](http://braindump.kargulus.de/?p=432) )  **worked great to get custom OLED** labels and goodies. I'm on a Kubuntu 12.04 and Intuos 4 Medium wired. Many thanks Christoph if he is around !

[IMG]http://wstaw.org/m/2012/08/22/20120822_151321_net.jpg[/IMG]

---

### Post by gamamoto on 2012-09-01
Wow that 's looking great ! I think you guys got something interesting, unfortunately I don't have my intuos4 with me so I can't tell if it works better with you findings.

Keep it up !

---

### Post by PrzemoF on 2012-09-24
I'm looking for testers of Wacom Intuos4 OLED helper. The helper is here:

[https://github.com/PrzemoF/i4oled](https://github.com/PrzemoF/i4oled)

or you ca get it using:

git clone git://github.com/PrzemoF/i4oled.git

It has to be compiled from the source and it needs kernel 3.2 (precise pangolin is OK, older kernels won't work). The compilation is very easy (./autogen && ./configure && make) and I'm offering full support is something goes wrong.

The helper allows to send text-to-OLED, PNG-to-OLED, tex-to-PNG and should work on any Intuos4 tablet equpped with OLED displays. 

Intuos4 _Wireless_ tablets have to be connected with USB cable.

---

### Post by maarts on 2012-09-28
Hi PrzemoF,

the OLED helper works fine for me!

Thanks,
maarts

---

### Post by Deevad on 2012-10-01
> **PrzemoF said:**
> I'm looking for testers of Wacom Intuos4 OLED helper. The helper is here [...] 
I would really like to test, but at the same time, I have a setup who works now. So I'm affraid testing something else could break my setup. 

Note : I found that my **.sh* script could be added with a text editor to **/etc/rc.local ** ( to edit as root ) with a line similar to this  before 'exit 0' :
**sh /home/<yourname>/path/to/script.sh**
And it makes the OLED load automatically at login without asking password. :KS

---

### Post by Favux on 2012-10-01
Understandable Deevad.


**[SIZE="3"]FYI Update[/SIZE]**:
Przemo is now onto integrating it into the gnome-settings-daemon and the gnome-control-center Wacom applet.:  [http://sourceforge.net/mailarchive/forum.php?thread_name=271ec2fd6f227188c9f242287ef65309.squirrel%40webmail.firszt.eu&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=271ec2fd6f227188c9f242287ef65309.squirrel%40webmail.firszt.eu&forum_name=linuxwacom-devel)

But I am sure he would appreciate more testers.

---

### Post by tatoknight on 2012-10-20
Hi,

I was just wondering if you still need testers. I'm kind of new at Ubuntu but I'm a developer and own an Wacom Intuos4 Medium, and will be more than glad to help :)

---

### Post by gamamoto on 2012-10-22
Will there be further support for old kernel users or do you recommend to update to 12.10 for a better tablet use ?

---

### Post by Favux on 2013-03-08
zorbama (with an Intuos5) on Mint forums pointed out that my sample xsetwacom.sh script for the Intuos4 only had one function for the touch ring and Button 1 (in the center of the touch ring) was assigned to a key and not acting as a toggle switch.
```
xsetwacom set "Wacom Intuos4 6x9 pad" Button 2 key ctrl
xsetwacom set "Wacom Intuos4 6x9 pad" Button 3 key alt
xsetwacom set "Wacom Intuos4 6x9 pad" Button 8 key shift
xsetwacom set "Wacom Intuos4 6x9 pad" Button 9 key tab

xsetwacom set "Wacom Intuos4 6x9 pad" AbsWheelDown +
xsetwacom set "Wacom Intuos4 6x9 pad" Button 1 key A  # button inside touchring
xsetwacom set "Wacom Intuos4 6x9 pad" AbsWheelUp -

xsetwacom set "Wacom Intuos4 6x9 pad" Button 10 key apostrophe
xsetwacom set "Wacom Intuos4 6x9 pad" Button 11 key backspace
xsetwacom set "Wacom Intuos4 6x9 pad" Button 12 key backslash
xsetwacom set "Wacom Intuos4 6x9 pad" Button 13 key ctrl z
```
He had a point.  So we had some fun looking into it and each came up with a script to toggle between the 4 possible touch ring modes, plus it changes the status LEDs to reflect what mode is in use.  See:  [http://forums.linuxmint.com/viewtopic.php?f=213&t=127358](http://forums.linuxmint.com/viewtopic.php?f=213&t=127358)

The touchring-toggle script should work for a Intuos4, Intuos5, and even Cintiq touch ring.  With the Cintiq there are two touch rings so we'd need the second bank of status LEDs name.  You'll need to bind Button 1 to the script using a key combination in your xsetwacom.sh script:
```
# Button 1 toggles the 4 touch ring modes using touchring-toggle.sh.
xsetwacom set "Wacom Intuos4 6x9 pad" Button 1 key ctrl alt r  # key combination for script binding
```
And also install a command in rc.local as mentioned in the script comments.
```
#!/bin/bash

## Touch ring toggle script
##
## Bind Button 1 (button center of touch ring) to the script.
##
## To allow script to select mode status LEDs edit rc.local to change root
## only permissions on the sysfs status_led0_select file:
##   gksudo gedit /etc/rc.local
## Add the following comment and command (before 'exit 0'):
##   # Change permissions on status_led0_select file so being root isn't
##   # required to switch Wacom touch ring mode status LEDs.
##   /bin/chmod 666 /sys/bus/usb/devices/*/wacom_led/status_led0_select
##
## Intuos - status_led0_select file = the left (only) ring status LEDs.
## Cintiq - status_led1_select = the left ring; status_led0_select =
## the right ring status LEDs.  Same for the touchstrips.
##
## For mode state notification use:
##   sudo apt-get install libnotify-bin
## Otherwise comment (#) out the notify-send lines.  If libnotify-bin
## installed see 'man notify-send' for details.

# check if mode_state file exists, if not create it and set to 0
if [ ! -f /tmp/mode_state ]; then
        echo 0 > /tmp/mode_state
fi

# read mode state value from temporary file
MODE=`cat /tmp/mode_state`

# select touch ring mode status LED for current mode state
echo $MODE > /sys/bus/usb/devices/*/wacom_led/status_led0_select

# for DEVICE use the pad "device name" from 'xinput list'
DEVICE="Wacom Intuos4 6x9 pad"
#DEVICE="Wacom Intuos5 touch M Pen pad"

# set touch ring function option and notification for the 4 toggled modes
if [ "$MODE" == 0 ]; then
        xsetwacom set  "$DEVICE" AbsWheelUp 4  # scroll up
        xsetwacom set  "$DEVICE" AbsWheelDown 5  # scroll down
        notify-send -t 1500 "Mode 1:  Scroll up or down."
elif [ "$MODE" == 1 ]; then
        xsetwacom set  "$DEVICE" AbsWheelUp key alt up  # increase brush radius (must be mapped in GIMP)
        xsetwacom set  "$DEVICE" AbsWheelDown key alt down  # decrease brush radius (must be mapped in GIMP)
        notify-send -t 1500 "Mode 2:  Increase or decrease brush size in Gimp"
elif [ "$MODE" == 2 ]; then
        xsetwacom set  "$DEVICE" AbsWheelUp key shift plus  # zoom in
        xsetwacom set  "$DEVICE" AbsWheelDown key minus  # zoom out
        notify-send -t 1500 "Mode 3:  Zoom in or out in Gimp."
elif [ "$MODE" == 3 ]; then
        xsetwacom set  "$DEVICE" AbsWheelUp key PgUp  # select previous layer
        xsetwacom set  "$DEVICE" AbsWheelDown key PgDn  # select next layer
        notify-send -t 1500 "Mode 4:  Select previous or next layer in Gimp"
fi

# toggle button increment counter
MODE=$((MODE += 1))

# set next mode state
if (( "$MODE" > 3 )); then  # roll over to 0, only 4 mode states available
        echo 0 > /tmp/mode_state
else
        echo $MODE > /tmp/mode_state
fi
```
The script works for me but zorbama says it doesn't for him so you'll probably want to run it in a terminal first to see if it throws an error.  He uses his script instead.  Once you learn which function goes with which LED you might want to comment out the notification line for that function.

---

### Post by hissingshark on 2013-03-29
Well I've been away a while.  Excited to see there have been developments.

Downloaded "i4oled-master".

Tried as mentioned in the thread:

./autogen && ./configure && make

Configure fell over, unable to find "pangocairo".
I can't seen to find this and get it installed to get things built and have a test.

Any suggestions?  I see some have clearly managed to get this to compile already...

EDIT:

Ok, finally got it to go after going way overboard with:

sudo apt-get install build-essential automake autoconf libtool pkg-config libcurl4-openssl-dev intltool libxml2-dev libgtk2.0-dev libnotify-dev libglib2.0-dev libevent-dev checkinstall

I'm probably good to go now compiling Deep Thought from source now...

---

### Post by PrzemoF on 2013-05-24
The "brain & heart" of i4oled is now included in gnome, so it might eventually get ported to ubuntu as well. If you hit any problems with i4oled please let me know (on github...) - I'll try to fix them.

---

### Post by shaun79 on 2013-06-09
WOW. I just saw this [http://blog.firszt.eu/public/wacom/wacom_oleds_in_action.webm](http://blog.firszt.eu/public/wacom/wacom_oleds_in_action.webm)
It's looking really good! I hope this lands in Saucy Salamander. That's IF Ubuntu goes with 3.10.x gnome-settings-daemon/control-centre? (AFAIK they are stuck on 3.6.3)

---

### Post by sigmagammapi on 2014-02-09
So I finally got to try out the Gnome 3.10 Wacom plugin in Ubuntu 13.10 with the Gnome3 ppa and I really like it. I'm now trying out the development Trusty release with Unity. From what I've been reading it looks like this Wacom plugin is not going to be included in 14.04 which is a LTS release, because Ubuntu will be using a patched gnome-settings-daemon 3.8.x and they've forked Gnome Control Centre 3.6 for the Unity Control Centre. Most other Gnome stuff is being bumped to 3.10.

I've created a bug report about the lack of an up-to-date Wacom plugin in the next LTS. Please, if this also matters to anyone else, comment on the bug and click on the link "Does this bug affect you?" near the top of the bug page. Thank you.

Here's the link: [https://bugs.launchpad.net/unity-control-center/+bug/1277733](https://bugs.launchpad.net/unity-control-center/+bug/1277733)

---

### Post by PrzemoF on 2014-04-19
[FONT=verdana][SIZE=3]I made a gui version of i4oled.
Short demo of what to expect: [http://firszt.eu/wacom-icons/i4oled_gui_demo.webm](http://firszt.eu/wacom-icons/i4oled_gui_demo.webm)
Source code: [https://github.com/PrzemoF/i4oled-gui/](https://github.com/PrzemoF/i4oled-gui/)

It's a graphical user interface for setting OLEDs on Wacom Intuos4 tablets.
[/SIZE][/FONT][FONT=verdana][SIZE=3][/SIZE][SIZE=1][/SIZE][SIZE=3]It requires gnome & dconf, but it doesn't require root access rights. I hope that some of the ideas tested in i4oled-gui
will be used in gnome.

Please test, send feedback, report bugs, ideas and new icons. [/SIZE][/FONT]

---

