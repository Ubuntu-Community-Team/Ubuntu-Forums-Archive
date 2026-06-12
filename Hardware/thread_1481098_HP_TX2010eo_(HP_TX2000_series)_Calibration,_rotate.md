---
title: "HP TX2010eo (HP TX2000 series) Calibration, rotate and anything else..."
date: 2010-05-12
forum: Hardware
---

### Post by Vinddraken on 2010-05-12
I've been using the HP TX 2010eo and linux since 2008, it was preinstalled with Vista and ofcourse everything worked great except for the poor performence and thus i was thinking that what i needed was a stable and more powerful tablet then the one and started to thinking that "hmm, Linux is stable and configurable and also virus free, let's try to install Linux on my machine" i haven't regreted it once since then. Also got my girlfriend to love it as well.

Thanks to ubuntu 10.04 most is working out of the box saving me time to have to activate the wacom driver and making everything work (i'm also using UNE to make the pointing and starting programs a bit easier to start rather then trying to click on icons).

The thing is i've been using Ubuntu since 2008, i know my way around in the terminal and can set up my machine to work with everything i throw on it and also got the touch and stylus to work back in 2008.

But, i've never managed to make the calibration 100% correct with both finger and stylus, and also never got screen rotation and position working (it always gets way off when i'm pointing on the screen in rotation mode).

Here is what terminal say:

drake@drake-laptop:~$ xsetwacom list
Wacom ISDv4 93 eraser ERASER    
Wacom ISDv4 93   STYLUS    
Wacom ISDv4 93   TOUCH     

and also:

drake@drake-laptop:~$ modprobe -l | grep hp-wmi
kernel/drivers/platform/x86/hp-wmi.ko


Specs: 
AMD Turion 64 X2 TL-68
NVIDIA® GeForceTM Go 6150
Wacom tablet, HP calls it "12.1-inch WXGA High-Def HP BrightView-Widescreen with builtin touchscreen"

What i would like to work: screen rotation either by pressing a button or like it was in Vista just rotate the screen and presto everything switches to tablet mode with 90-100% accuracy (atleast when i'm using onboard keyboard i can hit the right letter. Also right clickwith stylus would be nice.

I forgot if there is any else i should put in here, just ask!

Ps. I haven't touched anything yet so everything is config. by Ubuntu, not me =)

---

### Post by Favux on 2010-05-12
Hi Vinddraken,

Welcome to Ubuntu forums!

Let's start with automatic rotation.  You're in luck, it looks like the Magick Rotation beta1 for Lucid works.  So go to [Magick Rotation in post #315]("http://ubuntuforums.org/showpost.php?p=8052613&postcount=315") on the Rotation HOW TO thread.  Download v. .3-3 to get the READ ME and icons and also download .4-beta1.  Install the beta1 per the READ ME, but be sure to read Edit4 first

---

### Post by Drycola on 2010-05-12
[B]How to calibrate HP Tx2510us (tx2500 series) Touchscreen and Stylus:
Run terminal
within terminal enter the following commands:[/B]

```

xsetwacom set "12" TopX 225 
xsetwacom set "12" TopY 225 
xsetwacom set "12" BottomX 26300 
xsetwacom set "12" BottomY 16375
 
xsetwacom set "13" TopX 200 
xsetwacom set "13" TopY 225 
xsetwacom set "13" BottomX 4000 
xsetwacom set "13" BottomY 3872

```

Please note that this is strictly for HP TX2500 (the 12 & 13  above specify the device ID for the hardware used in this tablet)

---

### Post by Vinddraken on 2010-05-12
Favux >> Great i'll look into it tomorrow and report back any result i get!

Drycola: a bit risky, how do i restore to default settings if my adventures goes wrong? And what's the terminal command to figure out whats my device ID for the tx2000 series? But if i'm not wrong the TX2500 series should have the same screen size and resolution so if i just know if the numbers are correct the "12" and "13" or something else to put in there then your commands should be the same for my screen.

For anybody: Has somebody figured out how to use the rotate button on the screen? in the past people have found out how to bind rotate scripts for the media launcher that is under the DVD button, would be nice to use the original button for that =)

---

### Post by Favux on 2010-05-12
Hi Vinddraken,

Let me know if you have problems and I'll try to help.
> how do i restore to default settings if my adventures goes wrong?
With xsetwacom commands you just reboot or restart X.  They won't last.  You have to set them up in a script and set it up to auto-start.  And by the way you're right the coordinates are the same for the TX2000.  There might be a slight individual difference that you would have to fine tune.
```
Has somebody figured out how to use the rotate button on the screen?
```
No and we've looked long and hard.  Our best guess is it and the key next to it would need code added to the hp-wmi to enable them.

---

### Post by Vinddraken on 2010-05-13
> 
No and we've looked long and hard. Our best guess is it and the key next to it would need code added to the hp-wmi to enable them. 


Are we talking about the screen brightness button now? i could live with that :P

But the hardware ID or shall i just try random numbers? :P

---

### Post by Drycola on 2010-05-13
> **Vinddraken said:**
> But the hardware ID or shall i just try random numbers? :P

No, you can use the command ```
xinput -list
``` and it will show you the devices with their IDs..
However, you'll probably get two devices with the same name "Wacom ISDv4 93" with the IDs 12 and 13, these are the Stylus and Touchscreen, respectively.

---

### Post by Favux on 2010-05-13
> Are we talking about the screen brightness button now? i could live with that 
Correct.  The two lower right (while in landscape) blue LED bezel buttons don't work.  Rotation and Brightness.

---

### Post by Vinddraken on 2010-05-13
Why hasnt anybody figured out how to make them work, is it hardware or software problems to identify how to make them work? I found a 117 pdf file on an russian site, its a copy of the service manual, if it somehow could help.

[http://www.book-lab.ru/pdf/hp/service-manual-HP-Pavilion-tx2000.pdf](http://www.book-lab.ru/pdf/hp/service-manual-HP-Pavilion-tx2000.pdf)

---

### Post by Favux on 2010-05-13
Basically you have to be able to code in the hp-wmi, which is a acpi bios extension.  Red Lion (who is Russian) was our best hope.  But he wasn't sure he could do it.  He was trying to figure out what was needed.  Apparently the coding is specialized and not something programmers encounter or work with often.  I suppose we could try and get Matthew Garrett to do it.  But I doubt we'd be high on his priority list.  I think we were very lucky he separated out the docking and rotation event for us.

---

### Post by Vinddraken on 2010-05-13
Maybe because it's early morning here but i can't figure out why my .sh won't run

```

#!/bin/sh
xsetwacom set "12" TopX 225 
xsetwacom set "12" TopY 225 
xsetwacom set "12" BottomX 26300 
xsetwacom set "12" BottomY 16375
 
xsetwacom set "13" TopX 200 
xsetwacom set "13" TopY 225 
xsetwacom set "13" BottomX 4000 
xsetwacom set "13" BottomY 3872

```

btw Drycola and the rest of the world: This calibration also works for the tx2000 series like a charm, i'm hitting everything right, fingers and stylus.

Going to try the final piece (rotation) after i finished work.

---

### Post by Vinddraken on 2010-05-14
In terminal when i put in xinput -list, one of the things i found was:

```

&#8627; Wacom ISDv4 93 eraser                   	id=11	[slave  pointer  (2)]

```

I found this topic:

[http://bbs.archlinux.org/viewtopic.php?pid=743123](http://bbs.archlinux.org/viewtopic.php?pid=743123)

```

xsetwacom set 11 bottomy "16441"
xsetwacom set 11 bottomx "26290"
xsetwacom set 11 topy "225"
xsetwacom set 11 topx "225"

```

This is for the eraser. If i change everything to:

```

xsetwacom set 11 bottomy "16375"
xsetwacom set 11 bottomx "26300"
xsetwacom set 11 topy "225"
xsetwacom set 11 topx "225"

```

Then i should also have the eraser working in Xournal if i also add:

```

xsetwacom set 12 TPCButton "on"
xsetwacom set 12 Button3 "Button 3"
xsetwacom set 12 Button2 "Button 3"
xsetwacom set 12 Button1 "Button 1"
xsetwacom set 12 Suppress "2"
xsetwacom set 12 RawSample "4"
xsetwacom set 12 ClickForce "6"
xsetwacom set 12 PressCurve "0 0 100 100"

```

Right?

Edit: I had  time to try out

```

xsetwacom set 12 TPCButton "on"
xsetwacom set 12 Button3 "Button 3"
xsetwacom set 12 Button2 "Button 3"
xsetwacom set 12 Button1 "Button 1"
xsetwacom set 12 Suppress "2"
xsetwacom set 12 RawSample "4"
xsetwacom set 12 ClickForce "6"
xsetwacom set 12 PressCurve "0 0 100 100"

```

And right click with the stylus works now :-D Haven't tried the rest, report back later!

---

### Post by Favux on 2010-05-14
Did you make it executable?  Right click on it and Properties, Permissions tab, check Allow executing file as program.  Or in a terminal:
```
chmod +x ~/.yournameforit.sh
```

---

### Post by Vinddraken on 2010-05-14
> **Favux said:**
> Did you make it executable?  Right click on it and Properties, Permissions tab, check Allow executing file as program.  Or in a terminal:
```
chmod +x ~/.yournameforit.sh
```

Riiight and that is why you should never do anything without coffee! But the rest of the stuff i wrote should work? That would enable the eraser if i'm not wrong. I cant wait to mess around with magick and hope it will work with the calibration working right. 

First time i want to go home right now from work! :P

---

### Post by Favux on 2010-05-14
Hi Vinddraken,

It's looking close.  Remember stylus and eraser have the same coordinates as they are on the same device.  Here's my .xinitrc to show you the xsetwacom commands and values for the TX2000:
```
xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 10 90 100"
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
xsetwacom set touch bottomy "3969"
xsetwacom set touch bottomx "4028"
xsetwacom set touch topy "215"
xsetwacom set touch topx "140"
xsetwacom set touch Capacity "1"
xsetwacom set eraser bottomy "16630"
xsetwacom set eraser bottomx "26416"
xsetwacom set eraser topy "-101"
xsetwacom set eraser topx "66"
xsetwacom set stylus bottomy "16630"
xsetwacom set stylus bottomx "26416"
xsetwacom set stylus topy "-101"
xsetwacom set stylus topx "66"
```
Notice the top coordinate can be negative.

Edit:  Capacity may have been removed since it never worked right.

---

### Post by Vinddraken on 2010-05-14
> **Favux said:**
> 

Edit:  Capacity may have been removed since it never worked right.

So this is your tx2000 config? Looks like you have an older ubuntu, but will it work on lucid?

----------------------------------------
Few minutes later: 

I didn't want to wait to see what your answer was so i ran everything on the terminal, only error i noticed was: Cannot find device 'stylus'.

I'm not sure if i noticed anything different. If i rotate the screen then the pointer gets "mirrored" everything gets on the opposite sid, i'm pointing on top and the cursor gets to the bottom. When i'm in rootate should i somehow revert bottomy and bottomx or something?

Haven't had time to try rotate magick, got too much things to do atm :-( i've waited 2 years to get everything right, so i can wait a bit longer :P During my trial and error time with the TX2000 i have had to reinstall ubuntu, use my mobile to look answers on the net to make gnome work again and so on. So i wan't to be a bit careful and take my time to try out rotate magick thats why i haven't done it yet ;-)

---

### Post by Favux on 2010-05-14
It should, or something close.  I'd remove the RawSample and Capacity lines, and then you should be good to go.  Obviously you have to substitute the the device name or ID number for stylus etc.

---

### Post by Vinddraken on 2010-05-14
> **Favux said:**
> Hi Vinddraken,

Welcome to Ubuntu forums!

Let's start with automatic rotation.  You're in luck, it looks like the Magick Rotation beta1 for Lucid works.  So go to [Magick Rotation in post #315]("http://ubuntuforums.org/showpost.php?p=8052613&postcount=315") on the Rotation HOW TO thread.  Download v. .3-3 to get the READ ME and icons and also download .4-beta1.  Install the beta1 per the READ ME, but be sure to read Edit4 first

Ah, time to give you a headache perhaps? The Magick doesn't do anything, of course i followed everything and also did copy the readme and the icons. The only thing happens is that it runs and also tells me that hp_wmi isn't found, of course, i don't have anything on my system called hp_wmi (hp-wmi.ko but why hasn't The Magick found that and call it HP_WMI?) i saw in the readme that it's called hp-wmi. 

Also i didn't configure my videocard for rotation becuase when i go to 
System>Settings>Screens i can rotate the screen (with the mirror effect of course).

---

### Post by Favux on 2010-05-14
Did you check in lsmod that hp-wmi is auto-loading?  See:  [http://ubuntuforums.org/showpost.php?p=7738673&postcount=225](http://ubuntuforums.org/showpost.php?p=7738673&postcount=225) (linked in the read me).  You may have to add hp-wmi to /etc/modules as described.

By mirror effect do you mean the stylus etc are moving at right angles.  That just means they haven't rotated.  Did you put the appropriate device names or ID numbers in Advanced Setup?

---

### Post by Vinddraken on 2010-05-15
```

drake@drake-laptop:~$ modprobe -l | grep hp-wmi
kernel/drivers/platform/x86/hp-wmi.ko

```

lsmod
Gave me no wmi or hp-wmi

Because i have Lucid and it's says that starting with Jaunty the ubuntu kernel team started adding wmi to the kernel i skipped that part because what i understood it should already be there.

Looking in to /lib/modules/`uname -r`/extra/ (where uname -r is 2.6.32-22-generic for me) i couldn't find /extra/ or hp-wmi.ko

I did the next step trying to make hp-wmi active, and thought that maybe it will still work even without in /lib/modules/`uname -r`/extra/ (i think that if i did the compile in intrepid step i might find /extra/.

Wow! i did the next part:

```

gksudo gedit /etc/modules

```

And i must say... well... have a look:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

```

But still i added hp-wmi at the end (i.e after lp).

I also created the script.

Followed all the steps and added it to Startup Applications

And also rebooted the computer.

After reboot i finally got further then i ever have since i got linux installed on the machine! The rotation works!!!

But with the mirror effect as i call it is simply that when i point on the screen it gets way off from when i'm pointing (before i followed the steps it also pointed on the opposite direction) The arrow does rotate but as it seems now when in rotated state it gets way off, like 10cm or something like that.

Another thing for me is that when i'm rotated the taskbar shrinks to the right size but because i'm using UNE (earlier called UNR=Ubuntu Netbook Remix) i'm losing part of the screen so that the icons to the right isn't there.

Firefox does resize so that i have everything without loosing anything.

Same thing goes with nautilus everything resizes so i don't loose anything.

So whats left: Way off in tablet mode, somehow figure out why everything resizes but not UNE part (but i could live without fixing it). 

I also made a discovery: The default Magick setting is rotation to the right. When i switch to the left setting and point somewhere on top of the screen the arrow points kind off at the bottom (if i point at furthes top the arrow doesn't go all the way furthes down). And when i move my finger further down almost in the middle the arrow meets me there and if i continue further down the arrow goes up.

I suspect that i need to have several scripts coming to live depending on rotation state. I need to add that i'm only using the input that Drycola wrote here. I'm going to try out Favux config...

Btw Magick doesn't whine that i'm missing hp_wmi anymore!

---

### Post by Vinddraken on 2010-05-15
I also tried out Favux settings to see if that could work. 

```

xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 10 90 100"
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
xsetwacom set touch bottomy "3969"
xsetwacom set touch bottomx "4028"
xsetwacom set touch topy "215"
xsetwacom set touch topx "140"
xsetwacom set touch Capacity "1"
xsetwacom set eraser bottomy "16630"
xsetwacom set eraser bottomx "26416"
xsetwacom set eraser topy "-101"
xsetwacom set eraser topx "66"
xsetwacom set stylus bottomy "16630"
xsetwacom set stylus bottomx "26416"
xsetwacom set stylus topy "-101"
xsetwacom set stylus topx "66"

```

In laptop mode i just need to make some adjustments because i can't hit the corners. But in Tablet mode it's still terrible, i don't now exactly whats wrong in the X and Y axis, With the settings above it's less mirror effect and just more the arrow going a bit off. I suspect that the settings in laptop mode applies to the tablet mode but not really know how. If i point near the HP logo in Laptop mode then in tablet pointing at the same place the arrow gets closer to the fingerprint reader (left side in laptop mode) If i move the finger on the opposite direction to the HP logo (where the cam is) the arrow goes a bit above the DVD button.

I hope somebody can figure this one out, because i can't!

---

### Post by Vinddraken on 2010-05-15
> **Favux said:**
> Did you put the appropriate device names or ID numbers in Advanced Setup?

Touch: id=13 
Stylus: id=12 
Eraser: id=11

I think you wrote somewhere that Touch has i higher value number then the stylus.

I wrote in the boxes id=13 or should i have wrote: 13?

---

### Post by Vinddraken on 2010-05-15
The stylus works in rotate mode, why didn't i think of that when i was doing my "report". Also now the touch is sort of working. The arrow goes where i point, but it doesn't click on links, applications and so on. And when i release the arrow ends up in a random location (but it doesn't move if i point on the same place on the screen). But i'm happy that atleast the stylus work!

Edit: I'm starting to think that there is no hardware or software error with my computer, just the typical ghost in the shell. Because when i tried to see if stylus worked then the right click on the stylus stopped working, and instead just paste anything i've copied. Very frustrating and it feels like no one out there can help me or other forum posts. I got further with LL then with any other ubuntu and also thanks to Favux, but this one last thing frustrates me!!!

---

### Post by Vinddraken on 2010-05-16
> **Vinddraken said:**
> Touch: id=13 
Stylus: id=12 
Eraser: id=11

I think you wrote somewhere that Touch has i higher value number then the stylus.

I wrote in the boxes id=13 or should i have wrote: 13?

Also when writing in advance setting on Magick for the right-click option to work with the stylus you have to put in id=12 writing just 12 disables it or isn't recognized by Magick.

It feels like this is starting to become a trial and error log instead of somebody to help me out or point me to the right direction, seriously no one here to help me with the last step(s)?

---

### Post by Favux on 2010-05-18
Hi Vinddraken,

Let me try to summarize.  You are using the Magick Rotation beta1 for Lucid.
wmi and hp-wmi are two different things.  wmi was added into the kernel.  You discovered that hp-wmi wasn't auto-loading and that was why Magick wasn't working.  You added 'hp-wmi' without the quotes and then it loaded and Magick worked.  Right now the stylus and eraser rotate when the screen rotates, but not touch?

You've run into the device naming bug in linuxwacom 0.8.4-4's wacom.ko.  This has been fixed.  Basically it calls the stylus and touch the same name.  To distinguish them we've been adding the ID number from 'xinput --list' to Advanced Settings in Magick.  Just the number, not anything else.  It's not clear to me where your problem is:  adding the other stuff instead of just the number or you are using the wrong number.

Have I caught up?

You've also been investigating the xsetwacom commands and a start up script with them.

---

### Post by Vinddraken on 2010-05-23
> **Favux said:**
> Hi Vinddraken,

Let me try to summarize.  You are using the Magick Rotation beta1 for Lucid.
wmi and hp-wmi are two different things.  wmi was added into the kernel.  You discovered that hp-wmi wasn't auto-loading and that was why Magick wasn't working.  You added 'hp-wmi' without the quotes and then it loaded and Magick worked.  Right now the stylus and eraser rotate when the screen rotates, but not touch?

You've run into the device naming bug in linuxwacom 0.8.4-4's wacom.ko.  This has been fixed.  Basically it calls the stylus and touch the same name.  To distinguish them we've been adding the ID number from 'xinput --list' to Advanced Settings in Magick.  Just the number, not anything else.  It's not clear to me where your problem is:  adding the other stuff instead of just the number or you are using the wrong number.

Have I caught up?

You've also been investigating the xsetwacom commands and a start up script with them.

Hi Favux!

Yeah thats about it! I used the script that Drycola posted because it worked better for me.

What i need now is touch rotating with the screen.

---

### Post by Favux on 2010-05-23
```
I used the script that Drycola posted because it worked better for me.
```
Could you remind me of where that is?

How is it better than Magick?  With either one you're not getting touch to rotate.  Frankly since all you should need to do is vary the ID numbers until you figure which one is touch and which is stylus this makes no sense to me.  Does touch work in Windows?  To get around the naming bug you could just compile linuxwacom 0.8.6-2 for a wacom.ko where the naming bug is fixed.

---

### Post by Vinddraken on 2010-05-23
> **Favux said:**
> ```
I used the script that Drycola posted because it worked better for me.
```
Could you remind me of where that is?

How is it better than Magick?  With either one you're not getting touch to rotate.  Frankly since all you should need to do is vary the ID numbers until you figure which one is touch and which is stylus this makes no sense to me.  Does touch work in Windows?  To get around the naming bug you could just compile linuxwacom 0.8.6-2 for a wacom.ko where the naming bug is fixed.

Its on the first page on this thread. I thought that magick did the rotation bit, but i guess it does more?

---

### Post by Favux on 2010-05-23
Oh I see.  You meant Drycola's calibration's not a rotation script.  That's why I drew a blank.

---

### Post by Vinddraken on 2010-05-23
> **Favux said:**
> 
Frankly since all you should need to do is vary the ID numbers until you figure which one is touch and which is stylus this makes no sense to me.  1. Does touch work in Windows?  

2.To get around the naming bug you could just compile linuxwacom 0.8.6-2 for a wacom.ko where the naming bug is fixed.

Hello again! 

I added numbers to your questions so it's easier to understand (look at the quote box)

1. Yes it did work in Vista (didn't it for you, i thought you also had the tx2000-series)

2. Done and xinput -list gives me this now:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 Pen                      	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 Finger                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=16	[slave  keyboard (3)]

```

As in earlier posts if you remember it was:
```

Touch: id=13
Stylus: id=12
Eraser: id=11

```

Added the new values to Magick:
for pen: 11
for finger: 12

Also changed Drycolas values from:
```

xsetwacom set "12" TopX 225 
xsetwacom set "12" TopY 225 
xsetwacom set "12" BottomX 26300 
xsetwacom set "12" BottomY 16375
 
xsetwacom set "13" TopX 200 
xsetwacom set "13" TopY 225 
xsetwacom set "13" BottomX 4000 
xsetwacom set "13" BottomY 3872

```

To:
```

xsetwacom set "11" TopX 225 
xsetwacom set "11" TopY 225 
xsetwacom set "11" BottomX 26300 
xsetwacom set "11" BottomY 16375
 
xsetwacom set "12" TopX 200 
xsetwacom set "12" TopY 225 
xsetwacom set "12" BottomX 4000 
xsetwacom set "12" BottomY 3872

xsetwacom set 11 TPCButton "on"
xsetwacom set 11 Button3 "Button 3"
xsetwacom set 11 Button2 "Button 3"
xsetwacom set 11 Button1 "Button 1"
xsetwacom set 11 Suppress "2"
xsetwacom set 11 RawSample "4"
xsetwacom set 11 ClickForce "6"
xsetwacom set 11 PressCurve "0 0 100 100"

```

I noticed that it didn't work in rotate as usual so i changed it to that, still nothing.

---

### Post by Favux on 2010-05-23
Hi,

With re to 1) that's a standard way to check if the hardware works, ie try it in another OS.

With re to 2) I assume you compiled linuxwacom 0.8.6-2's wacom.ko and that's why touch and stylus are distinguished now?  If so good job.
> I noticed that it didn't work in rotate as usual so i changed it to that, still nothing. 
I don't understand what that means.  If you are saying touch still doesn't rotate we need to look at your Xorg.0.log.  It's in /var/log.  Right click on it and compress it with Create Archive and attach it to your next post using Manage Attachments below.

---

### Post by Vinddraken on 2010-05-23
> **Favux said:**
> 

I don't understand what that means.  If you are saying touch still doesn't rotate we need to look at your Xorg.0.log.  It's in /var/log.  Right click on it and compress it with Create Archive and attach it to your next post using Manage Attachments below.

Yup it still doesn't rotate, so here is the Xorg.0.log file:

---

### Post by Favux on 2010-05-23
Hi Vinddraken,

Alright, the Xorg.0.log was revealing.  As far as your system is concerned there is no Wacom driver being initialized for your wacom devices.  Both stylus/pen and touch are being picked up by the evdev driver.  Evdev will pick up input devices if nothing else has grabbed them.

So I don't know if you don't have the wacom drivers installed or your configuration file, whichever it is, is missing or has some error so it isn't invoking the wacom drivers.

---

### Post by Vinddraken on 2010-05-23
> **Favux said:**
> Hi Vinddraken,

Alright, the Xorg.0.log was revealing.  As far as your system is concerned there is no Wacom driver being initialized for your wacom devices.  Both stylus/pen and touch are being picked up by the evdev driver.  Evdev will pick up input devices if nothing else has grabbed them.

So I don't know if you don't have the wacom drivers installed or your configuration file, whichever it is, is missing or has some error so it isn't invoking the wacom drivers.

Ok, so where to begin? what other system files do you need? i noticed that i don't have the nvidia drivers installed. Because when i'm running on battery the screen is black until i reboot with power plugged in. But then the Magick script doesn't activate any rotation just starts Cellwriter.

---

### Post by Vinddraken on 2010-05-23
Ok i've done some research before going to bed.

10-wacom.conf is empty Edit: I downloaded xf86-input-wacom-0.10.3.tar.gz and compiled. Now 10-wacom.conf gives me this:

```

Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

```

/etc/hal/fdi/policy/custom_wacom.fdi is also empty

/etc/X11/xorg.conf also empty

```

xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 Pen                      	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 Finger                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=16	[slave  keyboard (3)]

```

```

lsusb | grep '[w|W]acom'
Bus 001 Device 006: ID 056a:0093 Wacom Co., Ltd 

```

---

### Post by Vinddraken on 2010-05-23
I tried to recompile again don't know if it did do anything but here is my xorg.0.log again

---

### Post by Favux on 2010-05-24
Nice job!  It now looks like wacom has it!  :)

Quick way to tell.  If the wacom devices show up in:
```
xinput --list
```
then run:
```
xsetwacom list
```
and your 3 devices should show up in it too.  If it's blank you know the wacom drivers aren't active.

Now Magick should work for you.

> I downloaded xf86-input-wacom-0.10.3.tar.gz and compiled.
I hope you mean at least 10.5, because that's the Lucid default.  10.6 would be OK too of course.  But if you mean 10.3 and things are working don't mess with it.  Either way it looks like you got your missing configuration file 10-wacom.conf by doing that.

You don't need a .fdi, that's gone with Lucid.  You don't need wacom sections in xorg.conf, the 10-wacom.conf in xorg.conf.d will take care of the configuration.

---

### Post by Vinddraken on 2010-05-24
> **Favux said:**
> Nice job!  It now looks like wacom has it!  :)

Quick way to tell.  If the wacom devices show up in:
```
xinput --list
```
then run:
```
xsetwacom list
```
and your 3 devices should show up in it too.  If it's blank you know the wacom drivers aren't active.

Now Magick should work for you.


I hope you mean at least 10.5, because that's the Lucid default.  10.6 would be OK too of course.  But if you mean 10.3 and things are working don't mess with it.  Either way it looks like you got your missing configuration file 10-wacom.conf by doing that.

You don't need a .fdi, that's gone with Lucid.  You don't need wacom sections in xorg.conf, the 10-wacom.conf in xorg.conf.d will take care of the configuration.

```

drake@drake-laptop:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 Pen eraser               	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 Pen                      	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 Finger                   	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam                               	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=17	[slave  keyboard (3)]
drake@drake-laptop:~$ 

```

```

drake@drake-laptop:~$ xsetwacom list
Wacom ISDv4 93 Pen eraser ERASER    
Wacom ISDv4 93 Pen STYLUS    
Wacom ISDv4 93 Finger TOUCH     
drake@drake-laptop:~$ 

```

But the last thing is that while pointing with finger (touch) will happen as expected but when you lift the finger the arrow (mouse pointer) goes away from where i pressed.

"I hope you mean at least 10.5, because that's the Lucid default.  10.6 would be OK too of course.  But if you mean 10.3 and things are working don't mess with it.  Either way it looks like you got your missing configuration file 10-wacom.conf by doing that."

No i installed 10.3 i missed that there was a 10.5 file...

---

### Post by m3n7al.piracy on 2010-10-08
This code:

xsetwacom set "12" TopX 225 
xsetwacom set "12" TopY 225 
xsetwacom set "12" BottomX 26300 
xsetwacom set "12" BottomY 16375
 
xsetwacom set "13" TopX 200 
xsetwacom set "13" TopY 225 
xsetwacom set "13" BottomX 4000 
xsetwacom set "13" BottomY 3872

works perfectly for the plain tx2000 too!

---

