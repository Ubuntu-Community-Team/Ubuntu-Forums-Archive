---
title: "Kensington VideoCam"
date: 2008-09-01
forum: Hardware
---

### Post by rplantz on 2008-09-01
I have an old Kensington 67014 VideoCam that I am unable to access. It is supposedly supported by the se401 driver, but when I try to access it with camorama I get "Could not connect to video device (/dev/video0). Please check connection."

I get
```

bob@bob-desktop:~$ ls -l /dev/video0
lrwxrwxrwx 1 root root 23 2008-09-01 11:05 /dev/video0 -> /dev/.static/dev/video0
bob@bob-desktop:~$ ls -l /dev/.static/dev/video0
crw-rw---- 1 root video 81, 0 2008-09-01 10:38 /dev/.static/dev/video0
bob@bob-desktop:~$ 

```

and
```

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 047d:5001 Kensington 
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
bob@bob-desktop:~$ 

```

and
```

bob@bob-desktop:~$ lsmod | grep se401
se401                  22276  0 
compat_ioctl32         11136  1 se401
videodev               30720  1 se401
usbcore               170288  5 se401,usbhid,ehci_hcd,ohci_hcd
bob@bob-desktop:~$ 

```

I unplugged the videocam and plugged it back in. dmesg gave
```
[ 5961.377225] usb 2-3: USB disconnect, address 4
[ 5964.757185] usb 2-3: new full speed USB device using ohci_hcd and address 5
[ 5964.860337] usb 2-3: configuration #1 chosen from 1 choice
[ 5964.864406] /build/buildd/linux-2.6.24/drivers/media/video/se401.c: SE401 camera found: Kensington VideoCAM 67014
[ 5964.864411] /build/buildd/linux-2.6.24/drivers/media/video/se401.c: firmware version: 50
[ 5964.867719] /build/buildd/linux-2.6.24/drivers/media/video/se401.c: ExtraFeatures: 0 Sizes: 160x120 200x152 176x144 320x240 352x288 400x300
[ 5964.873048] /build/buildd/linux-2.6.24/drivers/media/video/se401.c: int urb burned down
[ 5964.873059] se401: probe of 2-3:1.0 failed with error -5
bob@bob-desktop:~$ 

```

Any clues as what is causing the error -5?

---

### Post by IntuitiveNipple on 2008-09-01
The problem is caused by the button-handling code in drivers/media/video/se401c::se401_init():
```

	/* Start interrupt transfers for snapshot button */
	if (button) {
		se401->inturb=usb_alloc_urb(0, GFP_KERNEL);
		if (!se401->inturb) {
			info("Allocation of inturb failed");
			return 1;
		}
		usb_fill_int_urb(se401->inturb, se401->dev,
		    usb_rcvintpipe(se401->dev, SE401_BUTTON_ENDPOINT),
		    &se401->button, sizeof(se401->button),
		    se401_button_irq,
		    se401,
		    8
		);
		if (usb_submit_urb(se401->inturb, GFP_KERNEL)) {
			info("int urb burned down");
			return 1;

```
You'll recognise that last-but-one line as the message in the log file. se401_init() returns to the function that called it, se401_probe():
```

	info("firmware version: %02x", le16_to_cpu(dev->descriptor.bcdDevice) & 255);

	if (se401_init(se401, button)) {
		kfree(se401);
		return -EIO;
	}

```
which returns -EIO to the system. EIO is defined  in include/asm-generic/errno-base.h as:
```

#define	EIO		 5	/* I/O error */

```
The final line of the log reports -5 (-EIO):
```

se401: probe of 2-3:1.0 failed with error -5

```
So it seems to suggest the logic for handling the camera's button (does it have one to take photo's or start the camera?) is not working as intended. 

You'd need to contact the driver-maintainer to get some indication of what the error means and if there is a fix or if it indicates a broken device. The kernel MAINTAINERS file shows:
```

USB SE401 DRIVER
P:	Jeroen Vreeken
M:	pe1rxq@amsat.org
L:      linux-usb@vger.kernel.org
W:	http://www.chello.nl/~j.vreeken/se401/
S:	Maintained

```
So to begin with you should email the kernel.org mailing list (L) and CC the maintainer (M).

---

### Post by AdamWill on 2008-10-24
I just noticed the same issue, with the same camera, on (naturally) Mandriva 2009 (so kernel 2.6.27). Before I go and do as Nipple suggested (thanks for that great post, BTW!), rplantz, did you do it, and did you get any reply? Thanks!

---

### Post by AdamWill on 2008-10-24
oh, and yes, the camera does have a button on it. I haven't a clue what it's supposed to do, though.

---

### Post by rbenali on 2008-10-29
Since I'm not using the button, I commented the related code in se401.c provided with the latest kernel source. I recompiled the drivers/media/video modules and updated the se401.ko and now it works perfectly except the button that I don't need.
Racha

---

### Post by bebeto2008 on 2008-10-31
rbenali, can you tell me exactly what you did to make your cam work. i have the same problem with my old kensington videocam. sad to say i am newbie in ubuntu and not a programmer. thnks in advance.

---

### Post by lucio39 on 2008-12-07
> **bebeto2008 said:**
> rbenali, can you tell me exactly what you did to make your cam work. i have the same problem with my old kensington videocam. sad to say i am newbie in ubuntu and not a programmer. thnks in advance.

I'm also interested as my videoCam model #67015 does not work either.
Do I need a driver, such as se401?
Thnx in advance.

---

### Post by bebeto2008 on 2008-12-17
> I'm also interested as my videoCam model #67015 does not work either.
Do I need a driver, such as se401?
Thnx in advance.
yes, you need an se401 driver for this videocam, and it is available at the net, sadly i tried it and it did not work. i got an 'se401: probe of 2-3:1.0 failed with error -5' err mssg. i also tried to contact the driver-maintainer but i guess he is now not using his given e-mail.

---

### Post by TonyFordz on 2009-09-23
> **AdamWill said:**
> oh, and yes, the camera does have a button on it. I haven't a clue what it's supposed to do, though.

It takes pictures like a normal camera in Windows but this cam has not worked for me for a while because Kensington stopped supporting it which is why I never tried to use it again till now & only trying now because my other cam will not work with Ubuntu. If I can get this one to work in Ubuntu that would be awesome it was a very good cam in its time.

---

