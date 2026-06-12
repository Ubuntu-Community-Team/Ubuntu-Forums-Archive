---
title: "Problem with Creative Live! Cam IM"
date: 2008-07-11
forum: Hardware
---

### Post by guleblanc on 2008-07-11
I sent this to the ov51x-jpeg list, but maybe somebody here
knows something.

I am having problems getting this device to work.  I am out of my
depth in kernel programming here.  My system looks like this:

  1.) AMD64 processor, 1Gb memory, etc.
  2.) 64 bit Ubuntu 8.10 (Hardy?), pretty much up to date.
      Kernel 2.6.24-19-generic.
  3.) The output of lsusb tells me it's device number is 041e:4067.
      This is supposed to work according to the driver.  It looks
      like the driver thinks it's a PROD_LIVE_VISTA_VF0350_A, which
      looks like the other VF035O cameras in the .c file.  (I'm
      sort of guessing here.)  The ubuntu forum threads are not
      clear on this.  Or, at least the ones in english are not
      clear.
  4.) I compiled the driver, installed it and ran modprobe.  The
      output of "lsmod | grep ov51x-jpeg" tells me:
        ov51x_jpeg            166552  0
        compat_ioctl32         11136  1 ov51x_jpeg
        videodev               30720  1 ov51x_jpeg
      So, I reckon the driver is in the kernel.
  5.) So, I plug in my camera, and /var/messages says:
	Jul 10 21:21:34 crasher kernel: [135319.486552] usb 3-1.1: new 	
		full speed USB device using ehci_hcd and address 92
	Jul 10 21:21:34 crasher kernel: [135319.580501] usb 3-1.1:
		configuration #1 chosen from 1 choice
	Jul 10 21:21:34 crasher kernel: [135319.580690]
		webcam-driver/ov51x-jpeg-core.c: USB OV519 video device
                    found
	Jul 10 21:21:39 crasher kernel: [135324.597990] ov51x: probe of
	        3-1.1:1.0 failed with error -5
      (Here I've eliminated some long filesystem path names.)
  6.) The output of dmesg is about the same, but it has
	[135324.597958] webcam-driver/ov51x-jpeg-core.c: Can't determine 	
sensor slave IDs
	[135324.597967] webcam-driver/ov51x-jpeg-core.c: OV519 Config 		
		failed
	[135324.597970] webcam-driver/ov51x-jpeg-core.c: Camera
		initialization failed.

It looks from the source that a call to i2c_w is failing, but I can't
tell what i2c_w is.  My google-fu is not working for me.

I do have a few usb devices, mouse, keyboard, midiman fast track 
sound card, and I have two hubs, one chained from the other, and
a memory-card reading device connected to the internal usb header.
This may be relevant because the visor module, for palm devices,
seems to mess up the usb subsystem and require a reboot.  The
visor module is not loaded now, but there may be other conflicts
of which I do not yet know.

The only thing that seems to be working here is the nice blue led on the
camera, which is always on.

Thanks in advance.

---

### Post by guleblanc on 2008-07-11
One more thing.  If I can't solve this by, say, Monday I'm going to return the device for a refund.  So, it there is a time limit on it.

---

### Post by guleblanc on 2008-07-16
FWIW, it turns out that this guy wants to be connected very
closely to the usb headers in the box.  Connecting it through
a hub seems to be a bad idea.  Connecting it through two hubs
is twice as bad.

So, this seems to be working for me, with the most recent version
of ov51x-jpeg.

---

### Post by just_mcateer on 2008-10-22
A big 10-4 on avoiding hubs with this webcam. I was having all sorts of issues and after simply plugging the thing directly into the host machine, all of the problems mysteriously went away.

That's a real pain since the camera is designed for a laptop and only has a two foot cord!

Thanks,
Justin

---

### Post by simohell on 2009-06-19
> **just_mcateer said:**
> A big 10-4 on avoiding hubs with this webcam. I was having all sorts of issues and after simply plugging the thing directly into the host machine, all of the problems mysteriously went away.


Thanks for the idea.
Works also for Creative Webcam Live! Pro Notebook.

(only now I wish I hadn't broken the extra USB-port... should get it fixed)

---

