---
title: "Wacom Bamboo Pen CTE-660 Not working"
date: 2011-05-13
forum: Hardware
---

### Post by Louisda16th on 2011-05-13
I have a Wacom Bamboo Pen CTE-660 graphics tablet. I've read around that this should work out of the box on natty but this isn't the case for me. I've tried the wacom-dkms installation but that didn't help either. How do I get my tablet to work?

---

### Post by Favux on 2011-05-13
Hi Louisda16th,

Welcome to Ubuntu forums!

I do not recognize that model.  Do you know if it is a new model that just came out?  I think they're calling it a Bamboo One.

Let's see if we can find out what the Product ID is so we can verify the tablet is in the code.  Enter in a terminal:
```
lsusb
```
Post the line that has Wacom in it.

---

### Post by Louisda16th on 2011-05-13
Hi Favux!

You're right it is a Bamboo One. :) I read about "Bamboo Pen" models everywhere and I totally overlooked. Here is the output of lsusb:

```

Bus 003 Device 002: ID 056a:006b Wacom Co., Ltd 

```

---

### Post by Favux on 2011-05-13
Ok so the Vendor ID = 056a = Wacom which we already knew.  The Product ID = 006b.  Let me check if that model is in the code.

---

### Post by Favux on 2011-05-13
Alright, I am not seeing that model in the code.  So I assume it was recently released by Wacom.  Say in the last several months.

Since it is not in the code that is why it isn't working.  There are two drivers involved.  The usb kernel module/driver wacom.ko and the X driver xf86-input-wacom.  I know how to add your model to the code so it will work.

The xf86-input-wacom X driver isn't a problem.  I can show you how to clone its git repository, add your model to the file wcmUSB.c and , and compile it.  No big deal.

But the usb kernel driver wacom.ko is a problem.  I can show you how to add the model to the code no problem.  But I do not know how to compile the code since the kernel folks took it over.

See after the 2.6.35 kernel they split the Linux Wacom Project package into two parts.  One was the X driver which X.org took over and the other was the kernel driver which the kernel folks at linux-input took over.  That is actually how things are suppose to work and linuxwacom was an anomaly having both in the same package.  I don't know if you have to compile a whole kernel or if you can just get and compile the wacom.ko stuff like you can in Maverick or Lucid.  The file we need to change by the way is called wacom_wac.c.  I just haven't learned how to yet.  Been on my to do list.

So I can help you get your model working in Lucid or Maverick but not Natty.

---

### Post by Louisda16th on 2011-05-13
I don't have a Maverick ISO yet but tell me anyways. And how do you figure out what to change in that file? I'd love to try myself :).

Oh and I don't mind experimenting and messing up my natty installation. Its a fresh install so spending a little time on a reinstall is totally fine with me. If you feel the lucid/maverick fixes have a chance at working here too I can try those as well.

---

### Post by Favux on 2011-05-14
No that's not it.  I'm not worried about messing up Natty.  I'm worried about having to roll an entire custom kernel just to get the wacom.ko module we want.  Not only is that somewhat of an undertaking (downloading and compiling a kernel) but then Ubuntu updates won't work on your custom kernel.  Unless I suppose we follow a Ubuntu HOW TO and use all the same tweaks and customizations they do.

Now I've seen stuff about just compiling the kernel modules and then just copying the module you want.  In our case wacom.ko.  But that seems excessive too.

Also have seen stuff about just compiling a single module against the kernel headers and not needing an entire live kernel, but then you have to write a make script since you can't use the kernel's module make file.  I know nothing about the arcane art of scripting a make file.  I'm pretty dubious the simple examples I see would work for something like wacom.ko.  I could be wrong of course.

So in short I know how to do it with input-wacom which already includes the make file stuff.  But input-wacom only works on Lucid and Maverick.  Follow?

---

### Post by Louisda16th on 2011-05-14
Alright. I understand. So downgrading is the only way. Give me a day or two. I'll download and install maverick and get back to you. Any idea if support for this will be added soon though? Is it on the developers list of devices to add?

---

### Post by Favux on 2011-05-14
Nope.  Wacom doesn't tell the Linux Wacom Project about new products.  It is likely I'll be the one adding support for your model.  After you test and verify it works.  All of this adding a model stuff was in the [Bamboo Pen & Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") because we had to add the 5 new models that came out in October of 2010.  But since my patches (and from other folks) were accepted into xf86-input-wacom and linux-input I removed that stuff a few weeks ago.  It is still in posts scattered through the thread and also on the Axiotron Modbook thread.

They're on kenrel 2.6.39 now.  I don't know if linux-input feeds into that.  I suspect patches submitted won't show up until 2.6.40 though.

I really hate the thought you have to downgrade.  But until I figure out how to deal with the new situation regarding the kernel driver...

---

### Post by Louisda16th on 2011-05-14
Awesome! After a bit of searching I realized I do have a Maverick CD. I have enough space on my hard disk so I'll install it alongside natty in the evening.

This is actually for my mom's laptop. Her laptop slows down so often and I've to put so much effort in speeding it up again. So I've asked her to ditch windows and try out Ubuntu. She really liked the natty interface but I'll do something about that even if its maverick (or is it possible to install Unity in maverick?) :)

---

### Post by Louisda16th on 2011-05-14
Maverick installed :). I haven't updated to the latest packages however. It'll take a long time. Is this necessary or can we continue with just a fresh installation?

---

### Post by Favux on 2011-05-14
Although the updates probably won't affect the Wacom X driver I'd rather you did in case there is a kernel update in there.  That would "break" our compile and install of the wacom.ko from input-wacom.  What happens is the new kernel has a new modules directory and the default (non-working as far as you are concerned) wacom.ko is installed in it.

---

### Post by Louisda16th on 2011-05-14
Ok. Well I'll try it anyways. If an update does break the driver, just following the instructions again should work right?

---

### Post by Favux on 2011-05-14
Sure, and if we get it working you could always add the modified wacom.ko as a DKMS (dynamic kernel module support).  That way the modified module is automatically compiled for a new kernel, rather than requiring you to manually do it.

Alright we'll start with wacom.ko.  You'll use the instructions in the Bamboo P&T HOW TO I linked above to compile input-wacom.  But you'll stop after you untar the download:
```
tar xjvf input-wacom-0.11.0.tar.bz2

```
to modify the wacom_wac.c file.

---

### Post by Louisda16th on 2011-05-14
Done. I did obviously skip the "apt-get upgrade" step. What do I do next?

---

### Post by Favux on 2011-05-14
I assume you mean you now have the unpacked source code for input-wacom and are ready to make the changes in the code?  The upgrade step refers to the libraries/dependencies.  It wouldn't upgrade your distribution.  :)

Input-wacom should work for either Lucid or Maverick.

Use Part I to compile input-wacom-0.11.0 in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  After you've unpacked the downloaded tar stop and do the following.

Go into the input-wacom-0.10.11/2.6.30 folder and open the wacom_wac.c file and at line 1438 add/enter these two lines:
```

static const struct wacom_features wacom_features_0x6B =
	{ "Wacom Bamboo One 6x8", WACOM_PKGLEN_BBFUN,   21648, 13530, 1023, 63, BAMBOO_PT };


```
Make sure your identation is the same as the code's, that's important.  You're inserting at the end so the finish product looks like:
```

static const struct wacom_features wacom_features_0x47 =
	{ "Wacom Intuos2 6x8",    WACOM_PKGLEN_INTUOS,    20320, 16240, 1023, 31, INTUOS };
static const struct wacom_features wacom_features_0x6004 =
	{ "ISD-V4",               WACOM_PKGLEN_GRAPHIRE,  12800, 8000, 255, 0, TABLETPC };
static const struct wacom_features wacom_features_0x6B =
	{ "Wacom Bamboo One 6x8", WACOM_PKGLEN_BBFUN,   21648, 13530, 1023, 63, BAMBOO_PT };

#define USB_DEVICE_WACOM(prod)

```
With gedit to enable the line numbers go to Edit > Preferences > and check the box in front of 'Display line numbers' in the View tab.

Next go to line 1528 (was 1526 ) and add this line:
```
	{ USB_DEVICE_WACOM(0x6B) },
```
so it looks like:
```

	{ USB_DEVICE_WACOM(0x47) },
	{ USB_DEVICE_LENOVO(0x6004) },
	{ USB_DEVICE_WACOM(0x6B) },
	{ }

```
Save your changes.  That should take care of the wacom.ko.  Go ahead and finish compiling and installing it.  That just leaves the X driver.

The active area for a Bamboo One medium is a little smaller than a Bamboo Pen & Touch medium.  I'm using those dimensions rather than trying to figure out the new dimensions.  We can do that later if it seems needed.  Might have to change a couple of other things.  The BambooPT's just look like the best match.

---

### Post by Louisda16th on 2011-05-14
Thats line 1438 for me. Line 1450 reads:

```

	{ USB_DEVICE_WACOM(0x11) },

```
for me. The lines before 1438 are the structures you mentioned.

---

### Post by Favux on 2011-05-14
Concentrate on context and making it look the same not line number.  Maybe I'm not looking at input-wacom-0.11.0 like I think I am.


Edit: right you are it's 1438 for 0.11.0.  I guess I was looking at 0.10.11.

---

### Post by Favux on 2011-05-14
By the way I'd guess the new Bamboo One small (CTE-460) Wacom talks about has the Product ID = 006a

Now use part II. c) of the [Bamboo Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") to clone xf86-input-wacom (the X driver).  Before you run the line:
```
./autogen.sh --prefix=/usr
```
go into the xf86-input-wacom folder into the /src directory.  Open the wcmUSB.c file in a text editor and after line #244 add this line:
```

	{ WACOM_VENDOR_ID, 0x6B, 100000, 100000, &usbBamboo     }, /* Bamboo One 6x8 */

```
so it looks like:
```

	{ WACOM_VENDOR_ID, 0x65, 100000, 100000, &usbBamboo     }, /* Bamboo */
	{ WACOM_VENDOR_ID, 0x69,  39842,  39842, &usbBamboo1    }, /* Bamboo1 */
	{ WACOM_VENDOR_ID, 0x6B, 100000, 100000, &usbBamboo     }, /* Bamboo One 6x8 */

	{ WACOM_VENDOR_ID, 0xB0, 200000, 200000, &usbIntuos3    }, /* Intuos3 4x5 */

```
Save and close that file.  I don't think we need to make any changes to the wcmValidateDevice.c file.  So finish compling by running the autogen line etc. and rebooting.

With luck it should be working.

Diagnostics I need would be the output of *xinput list* and *xsetwacom list* entered in a terminal.

It would also help to have the Xorg.0.log.  That's in /var/log.  It might be pretty big so you can compress it by right clicking on it and using Create Archive.  Then you can attach it to your post using Manage Attachments below.

---

### Post by Louisda16th on 2011-05-14
I don't have a 
/usr/share/aclocal/xorg-macros.m4

But I have this
/usr/share/aclocal/xorg-server.m4

How do I proceed?

---

### Post by Favux on 2011-05-14
The update from macro 1.5 to 1.8 only applies to Lucid.  Maverick already has the newer one so you don't have to worry about it.  :)

---

### Post by Louisda16th on 2011-05-14
Ah. Didn't see the "Lucid only". Thanks :)

---

### Post by Favux on 2011-05-14
By the way there was a Maverick Unity for netbooks I think.  I believe some folks installed it on their Maverick Desktops.  But I'd consider that sort of an alpha of Unity.  Making the Natty Unity a Beta 1.  So there's a way to go before Unity is there in my opinion.  Unity in Natty is basically a plug in to Compiz.

I think the way to go would be to install cairo dock (also called glx dock) for your mom.  It's pretty fun.

---

### Post by Louisda16th on 2011-05-14
I've completed instructions till the end of Part II. The tablet still doesn't respond when I move the stylus. Should at this point or will it only after part III and IV?

Just asking in case I've missed something till now.

---

### Post by Favux on 2011-05-14
Nope should be working after you rebooted.  What's the output of *xinput list* in a terminal?

---

### Post by Louisda16th on 2011-05-14
Here you go:

```

Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo One 6x8 Pen stylus         	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo One 6x8 Pen eraser         	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=12	[slave  keyboard (3)]


```

Why does it list an "eraser"?

---

### Post by Favux on 2011-05-14
The xinput list looks good.  It appears our wacom.ko changes are recognized.  But no reaction to the stylus?  Could you boot into Natty and post *xinput list* from Natty?

I assumed the stylus had an eraser and two side buttons.  Is there an eraser on the back of the stylus opposite the stylus tip?

Back in Maverick could you attach your Xorg.0.log?  Maybe we are having touble with the wcmValidateDevice.c file after all.


Edit:  Ok, looking at the pictures I see the two side buttons, the rocker switch.  I don't think I see an eraser but it is hard to tell in the pictures and the details of the stylus aren't listed.  Having a spurious eraser entry shouldn't hurt anything.  My guess is if you got a Bamboo P&T stylus with an eraser it might work.

---

### Post by Louisda16th on 2011-05-14
There are two side buttons but no eraser. I've attached Xorg.0.log. Will give you natty's xinput list in a moment.

---

### Post by Favux on 2011-05-14
Something went wrong with your Xorg.0.log upload.  Gedit can't open it.

---

### Post by Louisda16th on 2011-05-14
Here is the output from natty:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImExPS/2 Logitech Explorer Mouse        	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=8	[slave  keyboard (3)]


```

The file wouldn't open in gedit for me before I uploaded it either. So I checked in gvim and it worked. Not sure how.

---

### Post by Louisda16th on 2011-05-14
> 
if you got a Bamboo P&T stylus with an eraser it might work

I didn't understand. Does P&T refer to pen and touch? My tablet only works with the stylus. By touch you mean using your fingers directly right?

---

### Post by Favux on 2011-05-14
So in Natty the X server doesn't see the tablet because it isn't in the kernel (wacom.ko).  It seems like we're halfway there.

There is apparently something wrong with the Xorg.0.log's character encoding which doesn't make sense to me.  It should be and open as a straight text file.

Right they have touch which yours doesn't.  But the Bamboo Pen is one of them and also lacks touch and an eraser.  It shows with the spurious eraser though.

---

### Post by Favux on 2011-05-14
In lieu of the Xorg.0.log nothing is jumping out at me as a show stopper.  My guess is the problem lies with xf86-input-wacom.  Either something went wrong with the compile/cloning (did you see any errors?) or with the code change.  For example a typo on the 0x6B product ID.  You might just want to repeat that X driver part again.  You could start by checking the wcmUSB.c file and making sure it looks good.

I'm assuming *xsetwacom list* in a terminal returns nothing?

---

### Post by Louisda16th on 2011-05-14
I get this output:
```

Wacom Bamboo One 6x8 Pen stylus 	id: 9	type: STYLUS    
Wacom Bamboo One 6x8 Pen eraser 	id: 14	type: ERASER 

```

I'll redo those steps and check.

---

### Post by Louisda16th on 2011-05-14
Nothing happened :(

---

### Post by Favux on 2011-05-14
Well shoot.  Everything looks right.  The fact that the tablet and its input devices are showing up in xsetwacom list should indicate it is actually working!  It appears the X server recognizes it and it is on the Wacom X driver.  What is the output of:
```
xinput list-props "Wacom Bamboo One 6x8 Pen stylus"
```
in a terminal?

Any luck with Xorg.0.log?  When you navigate to it in Nautilus/Places you should just be able to right click on it and chose 'Open with Text Editor' and it should open in gedit.

---

### Post by Louisda16th on 2011-05-14
I noticed that my device isn't listed in wcmUSB.c

---

### Post by Favux on 2011-05-14
I guess...What?

---

### Post by Louisda16th on 2011-05-14
Xorg.0.log doesn't open in gedit even when I use Nautilus. I'm not sure why. I opened it in gvim, selected and middle-clicked it in a new file. That seems to have worked. I've attached it.

Here is the output for xinput list-props "Wacom Bamboo One 6x8 Pen stylus"

```

Device 'Wacom Bamboo One 6x8 Pen stylus':
	Device Enabled (154):	1
	Coordinate Transformation Matrix (156):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (273):	0
	Device Accel Constant Deceleration (274):	1.000000
	Device Accel Adaptive Deceleration (275):	1.000000
	Device Accel Velocity Scaling (276):	10.000000
	Wacom Tablet Area (283):	0, 0, 21648, 13530
	Wacom Rotation (284):	0
	Wacom Pressurecurve (285):	0, 0, 100, 100
	Wacom Serial IDs (286):	107, 0, 2, 0
	Wacom Capacity (287):	-1
	Wacom Pressure Threshold (288):	27
	Wacom Sample and Suppress (289):	2, 4
	Wacom Enable Touch (290):	0
	Wacom Hover Click (291):	1
	Wacom Enable Touch Gesture (292):	0
	Wacom Touch Gesture Parameters (293):	50, 20, 250
	Wacom Tool Type (294):	"STYLUS" (272)
	Wacom Button Actions (295):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (296):	0, 0

```


You asked me to have a look at wcmUSB.c I saw the following section:

```

 WacomModelDesc [] =
{
	{ WACOM_VENDOR_ID, 0x00,  39370,  39370, &usbPenPartner }, /* PenPartner */
	{ WACOM_VENDOR_ID, 0x10,  80000,  80000, &usbGraphire   }, /* Graphire */
	{ WACOM_VENDOR_ID, 0x11,  80000,  80000, &usbGraphire2  }, /* Graphire2 4x5 */
	{ WACOM_VENDOR_ID, 0x12,  80000,  80000, &usbGraphire2  }, /* Graphire2 5x7 */
	{ WACOM_VENDOR_ID, 0x13,  80000,  80000, &usbGraphire3  }, /* Graphire3 4x5 */
	{ WACOM_VENDOR_ID, 0x14,  80000,  80000, &usbGraphire3  }, /* Graphire3 6x8 */
	{ WACOM_VENDOR_ID, 0x15,  80000,  80000, &usbGraphire4  }, /* Graphire4 4x5 */
	{ WACOM_VENDOR_ID, 0x16,  80000,  80000, &usbGraphire4  }, /* Graphire4 6x8 */
	{ WACOM_VENDOR_ID, 0x17, 100000, 100000, &usbBambooFun  }, /* BambooFun 4x5 */
	{ WACOM_VENDOR_ID, 0x18, 100000, 100000, &usbBambooFun  }, /* BambooFun 6x8 */
	{ WACOM_VENDOR_ID, 0x19,  80000,  80000, &usbBamboo1    }, /* Bamboo1 Medium*/
	{ WACOM_VENDOR_ID, 0x81,  80000,  80000, &usbGraphire4  }, /* Graphire4 6x8 BlueTooth */

```


Its a much bigger list but my tablet's model number is not there.

---

### Post by Favux on 2011-05-14
The xinput list-props output looks good.  It is showing the tablet on the wacom driver, not evdev for example.

OK, I think you're looking in the wrong section.  The line for your model should be a little lower.  Below the Bamboo1 entry:
```
	{ WACOM_VENDOR_ID, 0x64,  50000,  50000, &usbVolito2    }, /* PenPartner2 */

	{ WACOM_VENDOR_ID, 0x65, 100000, 100000, &usbBamboo     }, /* Bamboo */
	{ WACOM_VENDOR_ID, 0x69,  39842,  39842, &usbBamboo1    }, /* Bamboo1 */

	{ WACOM_VENDOR_ID, 0xB0, 200000, 200000, &usbIntuos3    }, /* Intuos3 4x5 */
```

Nice work on the Xorg.0.log.  I still don't understand the problem.  But anyway it looks good:
```
[    19.356] (II) config/udev: Adding input device Wacom Bamboo One 6x8 Pen (/dev/input/event4)
[    19.356] (**) Wacom Bamboo One 6x8 Pen: Applying InputClass "evdev tablet catchall"
[    19.356] (**) Wacom Bamboo One 6x8 Pen: Applying InputClass "Wacom class"
[    19.356] (II) LoadModule: "wacom"
[    19.357] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    19.374] (II) Module wacom: vendor="X.Org Foundation"
[    19.374] 	compiled for 1.9.0, module version = 0.11.0
[    19.374] 	Module class: X.Org XInput Driver
[    19.374] 	ABI class: X.Org XInput driver, version 11.0
[    19.374] (**) Wacom Bamboo One 6x8 Pen: always reports core events
[    19.374] (**) Option "Device" "/dev/input/event4"
[    19.384] (II) Wacom Bamboo One 6x8 Pen: type not specified, assuming 'stylus'.
[    19.384] (II) Wacom Bamboo One 6x8 Pen: other types will be automatically added.
[    19.384] (--) Wacom Bamboo One 6x8 Pen stylus: using pressure threshold of 27 for button 1
[    19.384] (--) Wacom Bamboo One 6x8 Pen stylus: Wacom Unknown USB tablet maxX=21648 maxY=13530 maxZ=1023 resX=1016 resY=1016  tilt=enabled
[    19.384] (II) Wacom Bamboo One 6x8 Pen stylus: hotplugging dependent devices.
[    19.384] (II) Wacom Bamboo One 6x8 Pen stylus: hotplugging completed.
[    19.404] (II) XINPUT: Adding extended input device "Wacom Bamboo One 6x8 Pen stylus" (type: STYLUS)
......
[    19.636] (**) Wacom Bamboo One 6x8 Pen eraser: Applying InputClass "evdev tablet catchall"
[    19.636] (**) Wacom Bamboo One 6x8 Pen eraser: Applying InputClass "Wacom class"
[    19.636] (**) Wacom Bamboo One 6x8 Pen eraser: always reports core events
[    19.636] (**) Option "Device" "/dev/input/event4"
[    19.645] (--) Wacom Bamboo One 6x8 Pen eraser: Wacom Unknown USB tablet maxX=21648 maxY=13530 maxZ=1023 resX=1016 resY=1016  tilt=enabled
[    19.645] (II) XINPUT: Adding extended input device "Wacom Bamboo One 6x8 Pen eraser" (type: ERASER)

```
It sure seems like it should be working.  And it shows the cloning worked because the version of xf86-input-wacom is 0.11.0.

Although it would be a big coincidence are you sure the hardware works, i.e. the stylus?  Does it work in Windows?

---

### Post by Louisda16th on 2011-05-14
I couldn't find it anywhere. I was actually looking for the 0x6B. Also the stylus does work on windows.

---

### Post by Favux on 2011-05-14
So it's not a hardware problem.

Interesting.  Alright.  Let's make sure you add your model to wcmUSB.c this time as described in [post #19]("http://ubuntuforums.org/showpost.php?p=10815337&postcount=19").  You may have forgotten to save the changes before you went ahead and did the compile.

---

### Post by Louisda16th on 2011-05-14
Argh! I overlooked post 19 :-|. Sorry about it. I guess we posting at the same time. *crosses fingers*.

---

### Post by Favux on 2011-05-14
lol  Don't worry about it.  I've thrown a lot of stuff at you in a short time.  :)

---

### Post by Louisda16th on 2011-05-14
Still no luck :(. Its 2:30 AM over here so I'll pause for now. I'll give this a fresh start after I wake up. :)

---

### Post by Favux on 2011-05-25
Ok, let's try again.  I changed from the BambooPT stuff to the graphire and calculated the max X & Y and resolution.  So hopefully we're now good to go.

It turns out input-wacom should work for Lucid, Maverick, and Natty.  So you can get your mom back to Natty.  I've also included the other Bamboo One.  Use the lines for your model (from lsusb), or just insert both models.

Use Part I to compile input-wacom-0.11.0 in the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  After you've unpacked the downloaded tar stop and do the following.

Go into the input-wacom-0.10.11/2.6.30 folder and open the wacom_wac.c file and at line 1288 add/enter these two lines:
```

static const struct wacom_features wacom_features_0x6A =
	{ "Wacom Bamboo1 4x6", WACOM_PKGLEN_GRAPHIRE,  14760,  9225,  1023, 63, GRAPHIRE };
or
static const struct wacom_features wacom_features_0x6B =
	{ "Wacom Bamboo1 6x8", WACOM_PKGLEN_GRAPHIRE,  21648, 13530,  1023, 63, GRAPHIRE };

```
Make sure your identation is the same as the code's, that's important.  You're inserting at the end so the finish product looks like:
```

static const struct wacom_features wacom_features_0x69 =
	{ "Wacom Bamboo1",        WACOM_PKGLEN_GRAPHIRE,   5104,  3712,  511, 63, GRAPHIRE };

static const struct wacom_features wacom_features_0x6A =
	{ "Wacom Bamboo1 4x6",    WACOM_PKGLEN_GRAPHIRE,  14760,  9225, 1023, 63, GRAPHIRE };
or
static const struct wacom_features wacom_features_0x6B =
	{ "Wacom Bamboo1 5x8",    WACOM_PKGLEN_GRAPHIRE,  21648, 13530, 1023, 63, GRAPHIRE };
static const struct wacom_features wacom_features_0x20 =
	{ "Wacom Intuos 4x5",     WACOM_PKGLEN_INTUOS,    12700, 10600, 1023, 31, INTUOS };

```
With gedit to enable the line numbers go to Edit > Preferences > and check the box in front of 'Display line numbers' in the View tab.

Next go to line 1440 (was 1438 ) and add this line:
```

	{ USB_DEVICE_WACOM(0x6A) },
or
	{ USB_DEVICE_WACOM(0x6B) },
```
so it looks like:
```

	{ USB_DEVICE_WACOM(0x69) },
	{ USB_DEVICE_WACOM(0x6A) },
or
	{ USB_DEVICE_WACOM(0x6B) },
	{ USB_DEVICE_WACOM(0x20) },

```
Save your changes.  That should take care of the wacom.ko.  Go ahead and finish compiling and installing it.  That just leaves the X driver.


Now use part II. c) of the [Bamboo Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") to clone xf86-input-wacom (the X driver).  Before you run the line:
```
./autogen.sh --prefix=/usr
```
go into the xf86-input-wacom folder into the /src directory.  Open the wcmUSB.c file in a text editor and after line #244 add this line:
```

	{ WACOM_VENDOR_ID, 0x6B, 100000, 100000, &usbBamboo     }, /* Bamboo1 4x5 */
or
	{ WACOM_VENDOR_ID, 0x6B, 100000, 100000, &usbBamboo     }, /* Bamboo1 6x8 */

```
so it looks like:
```

	{ WACOM_VENDOR_ID, 0x65, 100000, 100000, &usbBamboo     }, /* Bamboo */
	{ WACOM_VENDOR_ID, 0x69,  39842,  39842, &usbBamboo1    }, /* Bamboo1 */
	{ WACOM_VENDOR_ID, 0x6A, 100000, 100000, &usbBamboo     }, /* Bamboo1 4x5 */
or
	{ WACOM_VENDOR_ID, 0x6B, 100000, 100000, &usbBamboo     }, /* Bamboo1 6x8 */

	{ WACOM_VENDOR_ID, 0xB0, 200000, 200000, &usbIntuos3    }, /* Intuos3 4x5 */

```
Save and close that file.  I don't think we need to make any changes to the wcmValidateDevice.c file.  So finish compling by running the autogen line etc. and rebooting.

With luck it should be working.

Diagnostics I need would be the output of *xinput list* and *xsetwacom list* entered in a terminal.

It would also help to have the Xorg.0.log.  That's in /var/log.  It might be pretty big so you can compress it by right clicking on it and using Create Archive.  Then you can attach it to your post using Manage Attachments below.


**Edit** (5-28-11):  Alright, a Bamboo One small (006a) is working using the above instructions!  Although he says I got some line numbers wrong.  So watch out for that.

---

