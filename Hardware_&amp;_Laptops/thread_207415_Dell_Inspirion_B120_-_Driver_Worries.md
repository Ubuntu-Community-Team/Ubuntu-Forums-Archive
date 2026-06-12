---
title: "Dell Inspirion B120 - Driver Worries"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by Tauhshi on 2006-07-01
I was wondering if anyone has installed Drake on a Dell Inspirion B120 and got everything working. I'm worried that nothing will work because when I install Windows XP, I always have to go install drivers to even get Internet, Wireless Internet, and Sound to work, and install a driver so I can get my full power of the graphics card. I've seen lots of methods for Dells, but I'm not sure if those are for my laptop.

P.S. If you need my hardware specs, please reccomend a program to check all of my hardware.

---

### Post by K.Mandla on 2006-07-01
[QUOTE=Tauhshi]I'm worried that nothing will work because when I install Windows XP, I always have to go install drivers to even get Internet, Wireless Internet, and Sound to work, and install a driver so I can get my full power of the graphics card.[/QUOTE]
You could try the live CD version, which would give you the best idea of what would need attention.

I've put Dapper on an Inspiron 600m, an M170, a number of 8000s and 8100s, and a couple of Optiplex machines. With very few exceptions, everything installs without a hitch.

---

### Post by Tauhshi on 2006-07-01
Well, I'm speaking from the Live CD Experience of Brezzy (5.10). Are the downloadable CD's Live?

---

### Post by K.Mandla on 2006-07-01
Yes, but they don't call it a Live CD any more. It's a "desktop" CD, which sort of makes sense, since you're starting up a "desktop" of Ubuntu. 

The install CD is now the "alternate" disc. ... I haven't quite caught the logic of that name yet.

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

(I would have given you a direct link, but I wasn't sure where you are ... geographically speaking :) )

---

### Post by Tauhshi on 2006-07-01
Hmm, but the site says that you can install from the Desktop CD . . .

Anyway, I downloaded the Desktop CD, so, I'm going to go and make a list of what doesn't work, and report back here.

---

### Post by K.Mandla on 2006-07-01
[QUOTE=Desktop CD]The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use. You will need at least 192MB of RAM to install from this CD.[/QUOTE]
Yes, that's a new feature. If you like the way Ubuntu works, you can install it directly from the live desktop. It's very nifty, and it takes less time to install from the desktop than it does with the installation -- oops, I mean alternate CD.

However, if you want a dual boot or you want to partition your hard drive in a funny way, I don't think the installer on the desktop CD has that option (it's been a while since I used it ... I mostly use the Xubuntu install -- oops, I mean alternate CD).

---

### Post by Tauhshi on 2006-07-01
Ok, tried the "Desktop" CD, and Sound worked. Now, wireless, I couldn't figure out how to view wireless networks or anything, but I bet a pretty penny that it doesn't work. And Video Resolution only went up to 1024 x 768 instead of my preferred 1280 x 800 . . .

So, in short:
Sound - Check
Wireless 'Net - Nope/Can't Tell
Video - Nada

---

### Post by K.Mandla on 2006-07-02
If you know the model of your video card and wireless card, you can be better assured of what success you'll have installing Ubuntu.

Probably the easiest way to see what's inside your machine is to use the service tag on the bottom of your computer on Dell's support site. You can do this from Windows, if you like.

[http://support.dell.com/](http://support.dell.com/)

On the right side of the page enter your service tag and pick "Original System Configuration" from the drop-down menu. The next page will show you all the goodies inside your box.

Try to find the entry for the video card and the wireless card. Or if you like, you can copy and paste the results here and we can help you.

(DON'T list your service tag here. Just paste the system configuration. :) )

---

### Post by dtgolder on 2006-10-31
Well, I'm typing this now on a B120 using Dapper...dual boot to Windows.

Not sure if Edge works (don't want to play with the upgrade--have had some issues on other boxes) but Dapper works fine--BUT:

Wireless will be an issue (you'll need to use the Broadcom fix if you have the same wireless card I have)

Screen resolution too (but there's a fix there too for the IBM drivers (see the 915resolution fix on Package Manager)

Also the microphone (apparently) but there's a fix in this thread:
[http://ubuntuforums.org/showthread.php?t=236381&highlight=b120]("http://ubuntuforums.org/showthread.php?t=236381&highlight=b120")

It'll dual boot to windows, BUT you may need to repartition the hard drive first--I had troubles getting the Linux repartition tool to work (I think because Dell puts all their stuff on the machine). Fixes for that are a full reformat (which I didn't want to do as I wanted to dual-boot) and using a third-party tool (like Partition Magic, which worked great for me).

So good in fact that I'm considering erasing everything on the laptop and doing a full hd reformat and load with Dapper...

---

