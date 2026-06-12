---
title: "Xbox 360 Controller Problems in 8.10"
date: 2008-11-14
forum: General Help
---

### Post by eleniontolto on 2008-11-14
Seeing that original xbox controller support seems to be broken at the moment in 8.10, I decided to try to get my xbox 360 controller working in ubuntu using this tutorial:  [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)


However, when I do the "make"  command, I get this:

```
thetrap@XBMC:~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.27-7-generic SUBDIRS=/home/thetrap/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/thetrap/xpad/xpad.o
/home/thetrap/xpad/xpad.c: In function ‘xpad_open’:
/home/thetrap/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/thetrap/xpad/xpad.c: In function ‘xpad_close’:
/home/thetrap/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/thetrap/xpad/xpad.c: In function ‘xpad_probe’:
/home/thetrap/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/thetrap/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/thetrap/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/thetrap/xpad] Error 2
make[1]: Leaving direct
```

Am I doing something wrong here or is this a bug?  I couldn't find anybody else with these problems in 8.10 doing a google a search.

---

### Post by cainram on 2008-11-22
I'm having this same error.

---

### Post by ZERO16LIVES on 2008-11-26
me too :(

---

### Post by renato83 on 2008-11-28
Hi All!

Ubuntu 8.10 already support the xpad driver.
If you try
**locate xpad**

you'll find
[B]/lib/modules/2.6.27-7-generic/kernel/drivers/input/joystick/xpad.ko
/lib/modules/2.6.27-9-generic/kernel/drivers/input/joystick/xpad.ko
[/B]

The problem is not in the driver, but in the X11 server as described there
[http://ubuntuforums.org/showthread.php?t=953639]("http://ubuntuforums.org/showthread.php?t=953639")

If you are in a hurry, you can try the instruction in the previous link, otherwise, you can wait to the FDI file that soon will be present there
[https://help.ubuntu.com/community/Joystick_lshal_outputs_done]("https://help.ubuntu.com/community/Joystick_lshal_outputs_done")

I tried the methods to use a joystick and I found that all the guitar's keys works but the direction keys. This is because I didn't map them correctly whit the FDI file.

I hope to be helpful to you all fun of frets on fire! :guitar:

**EDIT:**
Adding to the /etc/X11/xorg.conf **_only_** the following code

[B]Section "ServerFlags"
	Option "AutoAddDevices" "False"
EndSection[/B]

will make the guitar work perfectly.
The only problem is that now the keyboard is recognized as american and not spanish...
I think that I'll have to add the lines manually, but not the guitar works! ;)

**EDIT Nº 2:**
If your keyboard are not american add the following text to your xorg.conf:

[B]Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
EndSection[/B]

modifying the "es" with the code of your language.
If there are others devices that don't work, do as usual modifying the xorg.conf file.

That's all waiting for the FDI file to come out.

---

### Post by NoThanksM$ on 2008-11-29
I don't think that page is being updated anymore, if you look at the top it says

> With xserver-xorg-input-evdev 1:2.0.99+git20080912-0ubuntu6 now in intrepid-updates, all you need to do is update your system (just check the version of xserver-xorg-input-evdev if you joypad still doesn't work in Ubuntu 8.10 (Intrepid) amd64, and make sure you're not using joystick-calibrator, jscal or another program like that).

The following is kept for reference. 

However, I have the verion of xserver-xorg-input-evdev mentioned on that page and still can't get the Xplorer guitar to work.  Adding those first three lines to xorg.conf that renato83 break input hotplug support, from what I've read.

---

### Post by renato83 on 2008-11-29
> **NoThanksM$ said:**
> However, I have the verion of xserver-xorg-input-evdev mentioned on that page and still can't get the Xplorer guitar to work.  Adding those first three lines to xorg.conf that renato83 break input hotplug support, from what I've read.

Yes, that code break the support to the hotplug support, but it can be removed when the FDI file will come out. Until now I have experimented no problems at all with the hardware. All the USB hard disk are recognized and mounted automatically when plugged in and even the guitar can be plugged and unplugged as needed without any problems.

---

### Post by NoThanksM$ on 2008-11-29
Okay, I tried adding those three lines and it did help somewhat, thanks.  The five frets and the Back and Start buttons work, but the pick and the d-pad still aren't detected.  They don't seem to do anything in jscalibrator either.  Do you know if there's anytyhing I can do to get the rest of the buttons working?

---

### Post by eleniontolto on 2008-12-01
> **NoThanksM$ said:**
> With xserver-xorg-input-evdev 1:2.0.99+git20080912-0ubuntu6 now in intrepid-updates, all you need to do is update your system (just check the version of xserver-xorg-input-evdev if you joypad still doesn't work in Ubuntu 8.10 (Intrepid) amd64, and make sure you're not using joystick-calibrator, jscal or another program like that).

The following is kept for reference. 


Does anyone know why we shouldn't use joystick-calibrator?  I'm using it at the moment.

By the way, for anyone interested, it appears original xbox controller problems have been solved. Here's a fix:  [http://ubuntuforums.org/showthread.php?t=981623](http://ubuntuforums.org/showthread.php?t=981623)

---

### Post by Grumbel on 2009-01-20
> **renato83 said:**
> That's all waiting for the FDI file to come out.
Creating a .fdi file that just disables Xorg grabbing the device is very easy and document at:

[http://github.com/Grumbel/xboxdrv/blob/85a72e7e1981c3129764639ff900484ccc00376d/README](http://github.com/Grumbel/xboxdrv/blob/85a72e7e1981c3129764639ff900484ccc00376d/README)

Result should look something like:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.product" string="Microsoft X-Box 360 pad">     
     <remove key="input.x11_driver" />
    </match>
  </device>
</deviceinfo>
```

The "Option "AutoAddDevices" "False"" workaround is pretty drastic and will likely break more stuff then fix.

---

### Post by Prof_NARF on 2009-10-06
> **eleniontolto said:**
> 
```
thetrap@XBMC:~/xpad$ make
make modules -C /usr/src/linux-headers-2.6.27-7-generic SUBDIRS=/home/thetrap/xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/thetrap/xpad/xpad.o
/home/thetrap/xpad/xpad.c: In function ‘xpad_open’:
/home/thetrap/xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/thetrap/xpad/xpad.c: In function ‘xpad_close’:
/home/thetrap/xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/thetrap/xpad/xpad.c: In function ‘xpad_probe’:
/home/thetrap/xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/thetrap/xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/thetrap/xpad/xpad.o] Error 1
make[1]: *** [_module_/home/thetrap/xpad] Error 2
make[1]: Leaving direct
```


To make the code compile I did this:

Changed lines 382 and 408 in xpad.c from
```
struct usb_xpad *xpad = dev->private;
```
to
```
struct usb_xpad *xpad = input_get_drvdata(dev);
```


line 496 from
```
input_dev->cdev.dev = &intf->dev;
```
to
```
input_dev->dev.parent = &intf->dev;
```


and line 497 from
```
input_dev->private = xpad;
```
to
```
input_set_drvdata(input_dev, xpad);
```

I hope this works for you.

This way I made the Microsoft XBox360 Gamepad work under Ubuntu 9.04 - Jaunty Jackalope x64. I am not sure if I needed to do that since I read the controller works out of the box in Jaunty. Maybe all you need to do is start jscalibrator. This will initialize the controller and you can use it to test and calibrate the gamepad.

---

