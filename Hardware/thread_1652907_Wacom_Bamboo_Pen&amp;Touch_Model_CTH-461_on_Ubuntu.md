---
title: "Wacom Bamboo Pen&amp;Touch Model CTH-461 on Ubuntu 10.04 or 10.10"
date: 2010-12-25
forum: Hardware
---

### Post by erniejunior on 2010-12-25
Hello Guys,

my girlfriend got the graphic tablet mentioned in the title for christmas. Is there any chance to get it working on Ubuntu 10.04 or 10.10 (she has 10.04 installed but I could do an upgrade)?
I tried nearly everything I found on the net but nothing worked for me.
lsusb shows me the tablet as "Wacom".
xinput list gives me:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; appletouch                              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Apple Computer Apple Internal Keyboard / Trackpad	id=10	[slave  keyboard (3)]
    &#8627; Apple Computer Apple Internal Keyboard / Trackpad	id=12	[slave  keyboard (3)]

```
(I am working with a MacBook)

xsetwacom list dev shows me:
```
appletouch       touch  
```
Maybe the above "touch" is something meaningfull? But I can not get it running neither in MyPaint nor in Gimp.
Please help me. I don't want to install her Windows again!

erniejunior

---

### Post by erniejunior on 2010-12-26
I did a bit further research and I think it does not work because the xorg driver of the default linuxwacom install is only for xorg version 1.7 and below. But I am running version 1.9.
But I do not manage to get the developer versions of wacomlinux installed. Are there any howtos on that issue?

---

### Post by Favux on 2010-12-26
Hi erniejunior,

Please see the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  I don't know if it being a MacBook adds any issues or not.

---

### Post by erniejunior on 2010-12-26
Hello Favux,
Thank you for the hint but I already tried everything in this howto.
But I can't even test the tablet with wacdump because there is no /dev/input/wacom directory. And the other events (0 to 11) don't seem to respond either. I tried a lot of versions of the wacomlinux drivers too. But I can not test whether they are working because of the wacdump issue and because "more /proc/bus/usb/devices" (as they describe it in the howto of wacomlinux) does not work either (no file or directory error).
The only way to find something out about the tablet is lsusb where it shows as
```
Wacom Co., Ltd 
```
I really do not know what to do any more. I think I have to install Windows in the end. I am trying to get it running all day.

---

### Post by Favux on 2010-12-26
Hi erniejunior,

I'd like to get your product ID because I'm wondering if you have one of the new models.  The /K makes it seem likely.  See the model box near the top of the HOW TO and the blue text under it.  If it is one of the new ones you'll have to at least manually patch the wacom_wac.c in linuxwacom to get a wacom.ko that recognizes your model.  You may need to also patch the xf86-input-wacom wcmUSB.c and validate devices.

Edit:  in other words I need to see the complete Wacom lsusb line where it should look something like:

Bus 002 Device 010: ID 056a:00d6 Wacom Co., Ltd

---

### Post by erniejunior on 2010-12-26
It is:
```
Bus 003 Device 003: ID 056a:00da Wacom Co., Ltd 
```
I hope that helps.
I already tried patching something this morning (can't remember what exactly because I tried a lot of options) but I think it did not work. If you had a howto for patching that would be great.

---

### Post by Favux on 2010-12-26
Ok, you're almost there then.  That should be this model then:
```
Bamboo P & T Special Edition Small	stylus, eraser; touch, pad
   (CTH461/L; Product ID = 0xdA)

```
Which is one of the new models.  It just has /K instead of /L for whatever Wacom reason.  But it is the same product ID.  My patches for it have already been accepted into xf86-input-wacom so cloning the git repository as in step II. should have you set up there.

You need to patch linuxwacom 0.8.8-10 as the instructions and links show you how before you compile it like in step I for the wacom.ko.  If you already have used 0.8.8-10 run 'make clean' before you do the ./configure line.

Ask if you have questions.

---

### Post by erniejunior on 2010-12-26
> **Favux said:**
>  It just has /K instead of /L for whatever Wacom reason.  But it is the same product ID.
On the back of the tablet near to the S/N it says, that it is a CTH-461/L, not /K. But I think it does not matter in the end?

> **Favux said:**
> You need to patch linuxwacom 0.8.8-10 as the instructions and links show you how before you compile it like in step I for the wacom.ko.
Which instructions/links exactly? Are the in the Pen&Touch howto? Maybe I am just blind.

I think I have messed everything up until now. Does that matter or can I just install the new stuff over the old stuff? I found an uninstall script in one of the prebuild folders. Would that help to clean up?

P.S.: Thanks for the effort so far!:)

---

### Post by Favux on 2010-12-26
The uninstall script might help.  I actually haven't figured out how to do it since Karmic.  They introduced a new dependency with xserver-xorg-input-all, which is needed, with Karmic.  Which sort of messed things up.  So we've settled for installing over.  The only problem you might run into is if you've managed to install two xsetwacom's in different locations.  They can conflict.

It's linked in the blue text, see:  [http://ubuntuforums.org/showpost.php?p=10090630&postcount=309](http://ubuntuforums.org/showpost.php?p=10090630&postcount=309)

---

### Post by erniejunior on 2010-12-26
Ok so I will look after the xsetwacom installs. I already read about it.

Unfortunately I could not see any blue text after klicking on your link but I guess it describes how to manually patch the linuxwacom 0.8.8-10 drivers?

Thanks a lot so far. Now I know in theory what to do. I will try it out tomorrow because it's getting a bit late at CEST.
If I run into any errors or if I am successful then I will report back.

---

### Post by erniejunior on 2010-12-27
I just tried it and it worked!:D
Thank you very much Favux! You were my last hope. I was just about to install windows or return the tablet to the store!
The only issue now is the touch thing. It works, even multi-touch. I can scroll with two fingers and zoom by pinching them. But it does all lag a lot and responds so slow, that you can't use it. Even just moving the mouse and doing some klicks is a pain. Is there a solution to that issue?

---

### Post by uyuy on 2010-12-27
All I can tell you is that I tried several version of Wacom products including Bamboo - which works in Kubuntu 9.04 that it will move the mouse cursor and clicks as well. The Wacom products have different hardware versions (4/5/6/), some will not work at all. Some will not be detected at all. Some can appear as a device using the lsusb command -which will show what device had been detected as you plugged / unplug. 

use lsusb command at a shell before you plug the Bamboo and then again after you plug, if you found a new device then that's it.

I had one version of wacom that won't be able to drive the mouse cursor but work inside a VMware virtual machine.

ubuntu 10.10 is quite good with it's hardware supports, laptop touch screens working perfectly in my recent install. There are more than 2400 driver modules amounting 125MB inside /lib/modules/2.6.35-24-generic

I have seen that pen & touch model but had not tried it on any Ubuntu.

What I did to get Bamboo work was some editing to my /etc/X11/xorg.conf file in Kubuntu 9.0.4
;)

---

### Post by uyuy on 2010-12-27
All I can tell you is that I tried several version of Wacom products including Bamboo - which works in Kubuntu 9.04 that it will move the mouse cursor and clicks as well. The Wacom products have different hardware versions (4/5/6/), some will not work at all. Some will not be detected at all. Some can appear as a device using the lsusb command -which will show what device had been detected as you plugged / unplug. 

use lsusb command at a shell before you plug the Bamboo and then again after you plug, if you found a new device then that's it.

I had one version of wacom that won't be able to drive the mouse cursor but work inside a VMware virtual machine.

ubuntu 10.10 is quite good with it's hardware supports, laptop touch screens working perfectly in my recent install. There are more than 2800 driver modules amounting 125MB inside /lib/modules/2.6.35-24-generic

I have seen that pen & touch model but had not tried it on any Ubuntu.

What I did to get Bamboo work was some editing to my /etc/X11/xorg.conf file in Kubuntu 9.0.4
;)

Hope that will be helpful.

---

### Post by Favux on 2010-12-27
Hi erniejunior,

What happened is linuxwacom came up with its gesture code first.  Then Xorg published its MT (multitouch) specification and the linuxwacom code wasn't compliant with the specification.  So the LWP has been changing the code over to Xorg specification compliant code, resulting in gestures being a little hit and miss as the code in the X driver (xf86-input-wacom changes).

Unfortunately MT compliant code also needs to be added to the kernel.  It was accepted into the 2.6.37 kernel.  Which, by the way, is also part of the reason why your model wasn't accepted/added until the 2.6.37 kernel.

Since Natty Narwhal development just switched to the 2.6.37 kernel a lot of this should shake out with the 11.04 release, hopefully.

In the meantime you should get use to the feel of your Bamboo.  If you haven't already, add the .xsetwacom.sh xsetwacom script (IV.).  Then you can slowly adjust the parameters to get a reasonably working tablet in the meantime.  See "Touch & Gesture Tips for the Bamboo in Linux" near the bottom of the HOW TO.


Hi uyuy,

Sounds like you might need a little help getting your Bamboo (MTE?) configured.  With Karmic, if you use the xorg.conf, you can't hot plug.  Can't help you with the VMware virtual machine though.

---

### Post by erniejunior on 2010-12-27
So [this posting of you]("http://ubuntuforums.org/showpost.php?p=10103419&postcount=316") won't work for me? Because I was just about to try it out but could not find the line saying:
```
if ((common->tablet_id >= 0xd0) && (common->tablet_id <= 0xd3))
```
Only:
```
	/* DTF720 and DTF720a don't support eraser */
	if (((common->tablet_id == 0xC0) || (common->tablet_id == 0xC2)) && 
		(ds->device_type == ERASER_ID)) 
	{
		DBG(10, common,
			"DTF 720 doesn't support eraser ");
		return;
	}
```
Starting from line #1318 (maybe that should  be changed for other users that are reading your post because your post is mentioned in the head of the thread).

But if you say that it will definitively work in 11.04 that is ok too (of course earlier it would be better). I assume 11.04 will be released in April?

---

### Post by erniejunior on 2010-12-28
Maybe upgrading just the kernel to 2.6.37 would be enough?

---

### Post by Favux on 2010-12-28
Hi erniejunior,

Looks like that line got dropped in the last few commits.  I guess my clone in Maverick is old enough to still have it.  I talked to Chris and he will submit a patch to detect WCM_2FG based on MT slots instead of USB ID to linux-input for the 2.6.37 kernel.  You're right, I should update the "HOW TO's" since there are yet two more models.

Don't know what problems you'd run into importing the 2.6.37 kernel into Maverick.  I know some folks do that.  Seems like you'd need to compile the kernel with the Ubuntu tweaks which might get involved.  I think there's a Ubuntu tutorial on that.

---

### Post by erniejunior on 2010-12-29
> **Favux said:**
> I talked to Chris and he will submit a patch to detect WCM_2FG based on MT slots instead of USB ID to linux-input for the 2.6.37 kernel.
Sorry, I don't understand what you mean. What are MT slots? What is WCM_2FG based?

I will have a look at the HowTos for upgrading the kernel but it sounds like it is not worth the effort.

---

### Post by Favux on 2010-12-29
That's kind of my feeling.  I don't mind compiling some kernel modules, but the whole kernel?

Don't worry about the jargon.  It just means Chris thinks he's found a way to identify tablets using their capabilities rather than explicitly identifying them.  The lingo is the from the new MT (multitouch) specification from Xorg.

---

### Post by wacomuser on 2011-01-22
Is there already a solution for this problem, I am waiting till I can use my Wacom.... ;)

---

### Post by Favux on 2011-01-22
Hi wacomuser,

Welcome to Ubuntu forums!

Yes, everything has been straightened out in the X driver xf86-input-wacom and all of the new Bamboo P&T models are now in it as of a couple of days ago.

Depending on your model you may need to add it into the wacom.ko of linuxwacom 0.8.8-10.  The input-wacom 0.10.10-1's wacom.ko already has the new models.  You'll have to decide which you want to use.

See the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  See post #2 for adding new models.

Hope this helps.

---

