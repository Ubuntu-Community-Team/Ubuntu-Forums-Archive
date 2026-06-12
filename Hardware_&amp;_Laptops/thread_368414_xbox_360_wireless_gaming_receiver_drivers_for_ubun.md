---
title: "xbox 360 wireless gaming receiver drivers for ubuntu"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by daemonoid on 2007-02-23
Hi,

On the uk release of microsoft's wireless gaming receiver i rushed out and bought one. I've tried to get it up and running in ubuntu, but nothing yet. It pops up in the hardware browser as an attached device, but i can't find any drivers.

Can anyone point me in the direction of the drivers or maybe even an install guide?

---

### Post by daemonoid on 2007-02-27
Anyone?

---

### Post by aberry5555 on 2007-02-27
To be honest I think you may be out of luck :S xbox360 support for Linux is very poor as it is all proprietary hardware and software (both in design and in lack of standards). What exactly does this wireless adapter do, should it not plug in to your router rather than your PC?

---

### Post by daemonoid on 2007-03-02
ah sorry its the usb wireless controller adaptor (for windows). After researching a little more it is possible - there's a way of running it on one of the red hats. Unfortunately adapting the guide to ubutu doesn't work. I have a couple of new ideas and will post back with a full set of results (and maybe even my own how-to) in the next few days.

---

### Post by cdos on 2007-03-07
> **daemonoid said:**
> ah sorry its the usb wireless controller adaptor (for windows). After researching a little more it is possible - there's a way of running it on one of the red hats. Unfortunately adapting the guide to ubutu doesn't work. I have a couple of new ideas and will post back with a full set of results (and maybe even my own how-to) in the next few days.

Would you mind posting the link to the redhat guide?  I was curious about this as well.

---

### Post by daemonoid on 2007-03-08
Cdos,

Here's the driver for the (wired) controller for fedora core 5 [http://www.ps3-hacks.com/file/8](http://www.ps3-hacks.com/file/8)

I can't spot the how to - i'm at work at the moment but i'm pretty sure it wasn't much more than installing the driver and then faffing with the receiver to make it connect. I still haven't got round to trying it as my slug arrived over the weekend ([http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)) and getting linux and the various servers running on that took most of my spare time, plus my missus was insisting on watching reality shows so i couldn't use the tv for my ubuntu media server...

---

### Post by mreams13 on 2007-03-12
This [[COLOR="Red"]guy[/COLOR]]("http://tattiebogle.net/index.php/ProjectRoot/Xbox360Controller/OsxDriver") has written a driver for OSX. He should be posting source code soon (He has the source to the previous versions up that support the wired drivers.) I don't know how much this helps, but he does seem to have it working.

---

### Post by HornedBeast on 2007-03-21
Im really interested in getting my 360 Wireless Receiver working under Linux (Not Ubuntu particulary, but any version of Linux). Any news as of yet?

---

### Post by Halvar on 2007-04-17
I really want to get this xbox 360 wireless adapter working!

I have never written a USB driver before but after taking a look at a lot of posts and the GREAT thread over at, [Howto Setup Xbox350 Controller in Edgy Elft]("http://ubuntuforums.org/showthread.php?t=318382&highlight=xbox+360+edgy") I have hacked up the xpad.c.

I followed that guide with zero problems.  After following it I started to poke around at the xpad.c code and through a lot of trial and error I made the following changes to the code and have BASIC functionality working using two wireless controllers.  I made no attempt to add this into the code at all.  Once we figure out all of the details I can play clean up.  For now I have just replaced the xbox 360 with what was needed for the wireless

However I still have some BIG issues to take care of as well as some problems that I am hoping someone here will see and give me a hand with.

First let me warn you that using these directions will cause you to end up with a module that will freeze on lsusb, modprobe and on reboot.  This is what I REALLY need help fixing ;).  However once you get the module loaded it does work.

The other issue I need to look at but have not yet is setting the lights to off or to identify which /dev/input/js each controller is by lighting the correct light.  Just not taken the time to look at this part yet.

OK...now onto the mess I have made of the code ;)....

Change..

{ 0x045e, 0x028e, 0, "Microsoft Xbox 360 Controller", 1},
to
{ 0x045e, 0x0719, 0, "Microsoft Xbox 360 Controller", 1},

Change..

{ USB_INTERFACE_INFO( 255 ,  93 , 1) },
to
{ USB_INTERFACE_INFO( 255 ,  93 , 129) },

Change..

/* digital pad (button mode) bits (3 2 1 0) (right left down up) */
input_report_key(dev, BTN_0, (data[2] & 0x01));
input_report_key(dev, BTN_1, (data[2] & 0x08) >> 3);
input_report_key(dev, BTN_2, (data[2] & 0x02) >> 1);
input_report_key(dev, BTN_3, (data[2] & 0x04) >> 2);

/* start and back buttons */
input_report_key(dev, BTN_START, (data[2] & 0x10) >> 4);
input_report_key(dev, BTN_BACK, (data[2] & 0x20) >> 5);

/* stick press left/right */
input_report_key(dev, BTN_THUMBL, (data[2] & 0x40) >> 6);
input_report_key(dev, BTN_THUMBR, data[2] >> 7);

to

/* digital pad (button mode) bits (3 2 1 0) (right left down up) */
input_report_key(dev, BTN_0, (data[6] & 0x01));
input_report_key(dev, BTN_1, (data[6] & 0x08) >> 3);
input_report_key(dev, BTN_2, (data[6] & 0x02) >> 1);
input_report_key(dev, BTN_3, (data[6] & 0x04) >> 2);

/* start and back buttons */
input_report_key(dev, BTN_START, (data[6] & 0x10) >> 4);
input_report_key(dev, BTN_BACK, (data[6] & 0x20) >> 5);

/* stick press left/right */
input_report_key(dev, BTN_THUMBL, (data[6] & 0x40) >> 6);
input_report_key(dev, BTN_THUMBR, data[6] >> 7);

Change..

input_report_key(dev, BTN_A, (data[3] & 0x10) >> 4);
input_report_key(dev, BTN_B, (data[3] & 0x20) >> 5);
input_report_key(dev, BTN_X, (data[3] & 0x80) >> 7);
input_report_key(dev, BTN_Y, (data[3] & 0x40) >> 6);
input_report_key(dev, BTN_TL, data[3] & 0x01 );
input_report_key(dev, BTN_TR, (data[3] & 0x02) >> 1);
input_report_key(dev, BTN_MODE, (data[3] & 0x04) >> 2);

to

input_report_key(dev, BTN_A, (data[7] & 0x10) >> 4);
input_report_key(dev, BTN_B, (data[7] & 0x20) >> 5);
input_report_key(dev, BTN_X, (data[7] & 0x80) >> 7);
input_report_key(dev, BTN_Y, (data[7] & 0x40) >> 6);
input_report_key(dev, BTN_TL, data[7] & 0x01 );
input_report_key(dev, BTN_TR, (data[7] & 0x02) >> 1);
input_report_key(dev, BTN_MODE, (data[7] & 0x04) >> 2);

Change..

input_report_abs(dev, ABS_X, (__s16)(((__s16)data[7] << 8) | (__s16)data[6]));
input_report_abs(dev, ABS_Y, ~(__s16)(((__s16)data[9] << 8) | data[8]));

to

input_report_abs(dev, ABS_X, (__s16)(((__s16)data[11] << 8) | (__s16)data[10]));
input_report_abs(dev, ABS_Y, ~(__s16)(((__s16)data[13] << 8) | data[12]));

Change..

input_report_abs(dev, ABS_Z, data[4]);
input_report_abs(dev, ABS_RZ, data[5]);

to

input_report_abs(dev, ABS_Z, data[8]);
input_report_abs(dev, ABS_RZ, data[9]);

ADD..

if (data[5] == 0x13){

above

/* digital pad (button mode) bits (3 2 1 0) (right left down up) */

ADD..

}

above

/**
 *      xpad_irq_in


Long story short I did three things...

1.  take all of the "data[#]" that affect the 360 and make them #+4.  
2.  Limit which messages to look at.  It appears that that there are a lot of messages being generated by the wireless adapter that have nothing to do with the controllers.  No idea what they are YET!
3.  Change the USB interface info 


I hope someone will see this and sugest some ways to take care of the locking up of the module on load/unload.

---

### Post by EnsignR on 2008-01-05
I've been using the information posted above to try and get my wireless adapter working with Gutsy. As yet without much luck.

I tried modifying the code posted here:
[http://ubuntuforums.org/showpost.php?p=2512158](http://ubuntuforums.org/showpost.php?p=2512158)

Trying to still keep it compatible with a usb connected I've added a new definition

```
#define MAP_DPAD_TO_AXES_X360Wireless	3
```

Added the following to the xpad_device array definition
```
	{ 0x045e, 0x0179, "Microsoft Xbox 360 Cont. Wireless Adapter", MAP_DPAD_TO_AXES_X360Wireless}
```

I've also slightly modified the x360 device mapping of the xpad_process_packet function to accommodate to wireless adapters +4 data offset (compared to a usb connected controller)

```

	int wc_offset = 0;
	if(xpad->dpad_mapping == MAP_DPAD_TO_AXES_X360Wireless) wc_offset = 4;

	if(xpad->dpad_mapping** >= **MAP_DPAD_TO_AXES_X360)
	{
		/* start/back buttons and stick press left/right */
		input_report_key(dev, BTN_START,  data[2** + wc_offset**] & 0x10);
**....**
		/* right stick */
		input_report_abs(dev, ABS_RX, (__s16) (((__s16)data[13** + wc_offset**] << 8) | data[12** + wc_offset]**));
		input_report_abs(dev, ABS_RY, (__s16) (((__s16)data[11** + wc_offset]** << 8) | data[10** + wc_offset]**));
	}
	else

```

There are two changes that Halvar made that I did not implement.
{ USB_INTERFACE_INFO( 255 , 93 , 129) },

and the last part of their post where they enclose some code in an if() statement.

Not sure if they're the reasons it not working or not, but unfortunately it's not.

To be honest I am not really sure what I am doing. It's been a VERY long time since I did any programming or playing around with *nix. I did get my modified module to compile and replaced the xpad.ko located at /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick/xpad.ko

After rebooting modinfo showed that my modified module was loaded, but my 360 controller would not sync with the adapter nor were there any devices present at /dev/input/js0 or /dev/js0.

Next thing I am going to try is track down the Gusty source for xpad.c and see if I can have any luck modifying the code currently compiled on my system.

Any help would be GREATLY appreciated as this is one of the few things left keeping me from formatting my windows partition.



EDIT: I have finally managed to get my WIRELESS controller working under Gutsy by following the instructions (Nicolae's in particular) in this thread: [http://ubuntuforums.org/showthread.php?t=570642](http://ubuntuforums.org/showthread.php?t=570642)

---

### Post by Skoot on 2008-02-16
Yeah, this receiver syncs up with any wireless xbox 360 component, if i remember correctly, Windows has its own driver for the receiver itself, there are only 3(at the time of this post) wireless devices that it syncs up with...:

the wireless controller
the wireless headset
the wireless guitar for guitar hero 3

Not sure if the wireless chatpad that connects to the controller requires a driver or not...but when you sync them up with the receiver....you need the drivers for the device as well..

Support for these devices could be a bit of a problem, but if anyone has the brains to figure these devices out...i'd really only ask for WIRELESS HEADSET support. that'd probably be the most useful in my books...but that's just my two cents worth

---

