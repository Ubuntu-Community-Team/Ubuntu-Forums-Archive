---
title: "unable to get webcam to work"
date: 2008-08-25
forum: Hardware
---

### Post by mattyrigby00 on 2008-08-25
Hi,
I cannot get my webcam to work and am wondering if it is incompatible, or simply needs extra drivers. It is a Mikomi webcam from Argos, and the outcome from lsusb is "Bus 006 Device 004: ID 093a:2620 Pixart Imaging, Inc."
Thanks

---

### Post by Crafty Kisses on 2008-08-25
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by mattyrigby00 on 2008-08-25
just tried that now, no luck :(

---

### Post by IntuitiveNipple on 2008-08-25
It may be worth testing the [gspca/spca driver](http://mxhaard.free.fr/spca5xx.html) that Michel Xhaard maintains.

According to the supported devices list 093a:2620 isn't currently supported but it would be worth adding that PCI ID to the driver and re-compiling it. I suggest that because many other Pixart cameras are supported and is possible the model you have contains the same/a similar chipset.

The module exists in the Ubuntu Hardy kernel already (v1.00.18 ) but v1.00.20 is available [from the Intrepid repository](http://packages.ubuntu.com/intrepid/gspca-source). It can be built for Hardy, too. You will need to edit, build, and re-install it from that source package.

I've created a patch for what I think are the changes necessary to add detection of the camera to the driver... as to whether it will work, well, you'd have to keep a close eye on the messages in /var/log/kern.log when loading the driver and camera.



I've uploaded the example patched package for Hardy to my PPA (see link in my signature) so you get the idea. You can get that and install it manually:
```

wget http://launchpadlibrarian.net/17060689/gspca-source_01.00.20-1ubuntu1%7Eppa2h_all.deb

sudo dpkg -i gspca-source_01.00.20-1ubuntu1~ppa2h_all.deb

mkdir gspca-01.00.20
cd gspca-01.00.20
tar -xjf /usr/src/gspca.tar.bz2
mv modules/gspca/* .
rm -rf modules

```

The patch is debian/patches/01_add_mixomi_M6607m.patch:
```

diff -rNu gspca-01.00.20.virgin/gspca_core.c gspca-01.00.20/gspca_core.c
--- gspca-01.00.20.virgin/gspca_core.c	2008-01-09 10:44:54.000000000 +0000
+++ gspca-01.00.20/gspca_core.c	2008-08-25 13:39:40.000000000 +0100
@@ -422,6 +422,7 @@
 	Lenovo,
 	LogitechQC4Notebooks,
 	PhilipsSPC220NC,
+	MikomiM6607M,
 	LastCamera
 };
 static struct cam_list clist[] = {
@@ -620,6 +621,8 @@
 	{Lenovo,"lenovo MI1310_SOC"},
 	{LogitechQC4Notebooks,"Logitech QuickCam for Notebooks"},
 	{PhilipsSPC220NC,"Philips SPC220NC PAC207"},
+	{MikomiM6607M,"Mikomi M6607M"},
+
 	{-1, NULL}
 };
 static __devinitdata struct usb_device_id device_table[] = {
@@ -834,6 +837,7 @@
 	{USB_DEVICE(0x046d, 0x08af)},	/* Logitech QuickCam Cool */
 	{USB_DEVICE(0x093a, 0x2472)},	/* PAC207 Genius VideoCam ge110 */
 	{USB_DEVICE(0x093a, 0x2463)},	/* Philips spc200nc pac207 */
+	{USB_DEVICE(0x093a, 0x2620)},	/* Mikomi M6607M */
 	{USB_DEVICE(0x0000, 0x0000)},	/* MystFromOri Unknow Camera */
 	{}			/* Terminating entry */
 };
@@ -4136,6 +4140,7 @@
 		case 0x2608:
 		case 0x260e:
 		case 0x260f:
+		case 0x2620:
 			spca50x->desc = PAC7311;
 			spca50x->bridge = BRIDGE_PAC7311;
 			spca50x->sensor = SENSOR_PAC7311;

```
It should give you the idea. To apply it manually do:
```

patch -p1 <debian/patches/01_add_mixomi_M6607m.patch

```
Crucially, it adds a case for the PID (Product ID) 0x2620 to the range of Pixart PIDs 0x2608,0x260e,0x260f in spcaDetectCamera() in the file gspca_core.c:
```

	case 0x093a:		/* Mars-semi ~ Pixart */
		switch (product) {

```
...
```

		case 0x2600:
		case 0x2601:
		case 0x2608:
		case 0x260e:
		case 0x260f:
		case 0x2620:
			spca50x->desc = PAC7311;
			spca50x->bridge = BRIDGE_PAC7311;
			spca50x->sensor = SENSOR_PAC7311;
			break;

```
If that doesn't work move the new "case 0x2620:" to one of the other Pixart PID ranges in case the camera shares the same chips as one of those.

After each source change, from the source directory, rebuild and reinstall the driver with:

```

sudo modprobe -r gspca

make
sudo mv gspca.ko /lib/modules/$(uname -r)/ubuntu/media/gspcav1/gspca.ko
sudo /sbin/depmod -ae

sudo modprobe gspca

```

---

### Post by mattyrigby00 on 2008-08-25
Thanks, it's now detected but I get a black screen when testing it in kopete - I'll try moving the case 0x2620: to another section.

---

### Post by mattyrigby00 on 2008-08-25
Tried a few other areas, none work, all either show nothing or the black screen - I guess my camera is incompatible with current drivers...

---

### Post by IntuitiveNipple on 2008-08-25
What is reported to /var/log/kern.log when the driver loads/camera is detected, when the case statement is as in my original patch?

Most drivers, when they log a new device, will give some indication of whether they completely understand the device when communicating with it. If that logging indicates that the camera is understood then, as I said, it may be necessary to add additional logic to completely support the camera in the driver - there might be other locations in the source-code where it has to do the same kind of switch/case or if (...) logic.

---

### Post by IntuitiveNipple on 2008-08-25
An idea to identify the chip-set.

Do you have Windows drivers that came with the camera? If they are not compressed into a self-extracting executable can you pull the .inf file and attach it - it could give some clues?

Alternatively, gzip the driver installer and attach that - I can *install* it using WINE in order to get to the .inf file.

---

### Post by mattyrigby00 on 2008-08-25
I tried to find the .inf file by installing the software in wine - and I couldn't find the .inf, but did find a folder called PAC7302.

Here is a log of what happens in /var/log/kern.log when the camera is plugged in on the original patch:
```
Aug 25 21:00:45 matthew-desktop kernel: [  143.020744] Linux video capture interface: v2.00
Aug 25 21:00:45 matthew-desktop kernel: [  143.094118] usbcore: registered new interface driver gspca
Aug 25 21:00:45 matthew-desktop kernel: [  143.094124] /usr/src/gspca-01.00.20/modules/gspca/gspca_core.c: gspca driver 01.00.20 registered
Aug 25 21:00:54 matthew-desktop kernel: [  151.604017] usb 4-1: new full speed USB device using uhci_hcd and address 2
Aug 25 21:00:54 matthew-desktop kernel: [  151.837546] usb 4-1: configuration #1 chosen from 1 choice
Aug 25 21:00:54 matthew-desktop kernel: [  151.840471] /usr/src/gspca-01.00.20/modules/gspca/gspca_core.c: USB SPCA5XX camera found. (PAC7311)
Aug 25 21:00:54 matthew-desktop kernel: [  151.840475] /usr/src/gspca-01.00.20/modules/gspca/gspca_core.c: [spca5xx_probe:4301] Camera type JPEG 
Aug 25 21:00:54 matthew-desktop kernel: [  151.852528] /usr/src/gspca-01.00.20/modules/gspca/gspca_core.c: [spca5xx_getcapability:1253] maxw 640 maxh 480 minw 160 minh 120
Aug 25 21:00:54 matthew-desktop kernel: [  151.863396] /usr/src/gspca-01.00.20/modules/gspca/gspca_core.c: [spca5xx_set_light_freq:1936] Sensor currently not support light frequency banding filters.
Aug 25 21:00:54 matthew-desktop kernel: [  151.863429] /usr/src/gspca-01.00.20/modules/gspca/gspca_core.c: [gspca_set_isoc_ep:949] ISO EndPoint found 0x85 AlternateSet 8
Aug 25 21:00:54 matthew-desktop kernel: [  151.907508] usbcore: registered new interface driver snd-usb-audio
```

---

### Post by IntuitiveNipple on 2008-08-25
That log looks promising if, as it seems to suggest, the driver actually did communicate and understand the camera.

Back to the Windows driver, since that can quickly confirm the chip-set in device.

I did a similar WINE install with an HP web-cam driver self-installing executable (that also happens to be Pixart-based) a couple of hours ago. The .inf  is always installed to C:\Windows\inf\ and is usually identified by the last-accessed date being the most recent.

Usually that translates to: /home/$USER/.wine/drive_c/windows/inf/

Another trick is to leave the installer waiting for user input and then look in C:\Windows\temp\ since the installer will usually unpack the contained files to a temporary directory. Again, the most recent date should be the one. Sometimes the files in ...\temp\ itself, too.

---

### Post by mattyrigby00 on 2008-08-25
Managed to find the .inf now, attached to the post. (placed inside a .tar.gz file because the forum wouldn't let me upload the .inf)

---

### Post by IntuitiveNipple on 2008-08-25
Nice one, that has helped a lot.

The chip-set is the PAC7302. It is not currently supported in the gspca driver **but** [this thread on the spca50x.devel mailing-list](http://sourceforge.net/mailarchive/forum.php?thread_name=75d9d9b90711262203t38b126aagaa69b2514dc5f72%40mail.gmail.com&forum_name=spca50x-devs) from November 2007 offers some hope:
> 
The video stream uses the same "Pixart" JPEG compression as the PAC7311 I am working on. I am able to extract and decode pictures from the usbsnoop I god from Guillermo :-) But the picture is 90 degree rotated. Instead of 640x480 I have to add 480x640 in the JPEG header to get the whole picture. And I see the same pixel problem as with the PAC7311. (I found a JPEG Guru who is willing to help me on this, I hope we can find the problem)

Register 0x78 seems to turn on the stream. That's the same register like
PAC7311. Register 0xff seems to be a kind of bank switching as it is on the PAC7311. But here it uses values from 0 to 3 and on the PAC7311 only the value 1 and 4. Register 0x11 seems to have the same function, too (load settings to sensor or strobe).


I'm emailing the person that was hacking the code to see if any progress has been made. I'll let you know if/when there is a reply. I'll point them to this thread, too, so they can ask you questions directly if they want to.

---

### Post by IntuitiveNipple on 2008-08-25
Even more encouraging news. I did some more cross-referencing of the chip-set number and found that there are some very recent commits to the [linuxtv](http://www.linuxtv.org) project's [v4l-dvb repository](http://linuxtv.org/hg/v4l-dvb) which suggest it has emerging support for the PAC7302.

Tomorrow I'll clone the repository (it looks to have a lot of recent work on a multitude of camera drivers I'm interested in) and see how to split out the driver and bundle it for you to test (unless you want to work it out for yourself?).

---

### Post by IntuitiveNipple on 2008-08-25
I decided to clone the v4l-dvb repository now so I could scan the commit log and see what is going on.
The good news is that the 093a:2621, which uses the PAC7302, is already supported by gspca. I'm guessing there'll be little difference between that and the 093a:2620.
Adding code similar to what I did for the gspca-1.00.20 driver from Michel Xhard is possibly all it needs.

**linux/drivers/media/video/gspca/pac7311.c:853**
```

/* -- module initialisation -- */
static __devinitdata struct usb_device_id device_table[] = {
	{USB_DEVICE(0x093a, 0x2600), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x2601), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x2603), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x2608), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x260e), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x260f), .driver_info = SENSOR_PAC7311},
	{USB_DEVICE(0x093a, 0x2621), .driver_info = SENSOR_PAC7302},
	{}
};
MODULE_DEVICE_TABLE(usb, device_table);

```

I just need to figure out why there are two apparently separately maintained drivers with the same name (gspca) and if there is any common relationship between them.

---

### Post by mattyrigby00 on 2008-08-26
I just tried installing v4l-dvb with the pac7311.c file edited to detect the 093a:2620 as PAC7302, and now rather than showing a black square with white dots, it shows a solid black box - this is all it says in kern.log when I plug the camera in:
```
Aug 26 10:19:14 matthew-desktop kernel: [  820.516686] usb 4-1: new full speed USB device using uhci_hcd and address 3
Aug 26 10:19:14 matthew-desktop kernel: [  820.749547] usb 4-1: configuration #1 chosen from 1 choice
Aug 26 10:19:14 matthew-desktop kernel: [  820.752560] gspca: probing 093a:2620
Aug 26 10:19:14 matthew-desktop kernel: [  820.762529] gspca: probe ok
Aug 26 10:19:14 matthew-desktop kernel: [  820.762549] gspca: probing 093a:2620
```

---

### Post by IntuitiveNipple on 2008-08-26
I suspect it is worth emailing the guy making the PAC7302 commits so that whilst he's focused on it he can investigate the device you have. I'd suggest, if you can, running Windows and capturing the USB packets for later analysis [using USBsnoop or similar](http://mxhaard.free.fr/snoopy.html). I think there are instructions I saw on the linuxtv.org Wiki for the precise steps.

Also, it is worth investigating the gspca module's command-line parameters since one of those might help.

For example I recently found that using the ov51x-jpeg driver it needed "force_palette=x" to set the palette (in that case YUV420) so that applications could work correctly.

---

### Post by Olyander on 2009-02-15
wow 2006 been along time since this issue was revisted. 

IntuitiveNipple, I need your patch assistance.

I looked at your coding, cool, good job!

Can you do the same for me, but this time using the gspca for Pixart Webcam registering on lsusb:

Bus 002 Device 004: ID 093a:2620 Pixart Imaging, Inc

I can try the case cmd to move the 2620.

Can I do this already? I'm a little hesitant, new territory for me.

Any help is needed. thanks!!

OlyAnder 

ps the same issue, webcam not working yadda, I can simply try your new patch - and post link if you please. Mucho appreciato!!

I'll check back in a few dayz..

---

### Post by Kangarooo on 2010-05-05
heres also this cam [http://ubuntuforums.org/showthread.php?t=1442626](http://ubuntuforums.org/showthread.php?t=1442626)

---

