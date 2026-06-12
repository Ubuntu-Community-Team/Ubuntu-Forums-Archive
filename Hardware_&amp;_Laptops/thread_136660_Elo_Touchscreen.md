---
title: "Elo Touchscreen"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by mike4263 on 2006-02-26
Hi,  I'm setting up a Point of Sale cash register using Kubuntu 5.10.  I'm having  some problems getting the [Elo Touchscreen]("http://www.elotouch.com/") to work properly.

The device supports both serial and USB adapters.  I am unable to get the serial working at all (the serial port may very well be damaged or dead, this is a used computer I'm working with).  I can cat the USB driver and see that input is being transfered to the screen.

My problem is the USB driver claims to not support kernel 2.6.11 or above.  I attempted to recomplie the kernel but recieved an error message.  Also, my attempts to reinstall the X server hopelessly failed.

I'm at a loss as to what to try next (an older distro maybe?  Is there a version of Ubuntu with XFree86 and a kernel 2.6.10 or below).  If anyone could help out, it would be greatly appreciated.

-mike

---

### Post by Samy_Merchi on 2006-03-22
I am having no luck with the Elo Touchscreen I have. Dead right out of the gate. I have no idea what to do. I've been reading this HOWTO:

[http://tldp.org/HOWTO/XFree86-Touch-Screen-HOWTO-1.html](http://tldp.org/HOWTO/XFree86-Touch-Screen-HOWTO-1.html)

But it stalls right out of the gate, because none of the paths mentioned there exist. My fresh Ubuntu install does not have a

/etc/X11/XF86Config (to conf the X)

or

/usr/X11R6/lib/modules/ (to check that the Elo module is present)

Are those located somewhere else on Ubuntu? Or am I chasing in an entirely wrong direction?

I would appreciate any help.

---

### Post by wermerskoch on 2006-03-22
I THINK that the equivalent file for XF86Config (which is used in Kubuntu) is xorg.conf, which is in the /etc/X11 directory.  At least that's the file that is used in telling it what kind of video card to use, what driver it uses, what kind of monitor you have and things like that.  As far as the modules directory you're looking for, I'd assume that would be either /etc/gnome-vfs-2.0/modules  or /etc/gdm/modules.  Again, I'm not 100% sure about that.  Hope this helps.

---

### Post by Samy_Merchi on 2006-04-13
So would you guess that if I installed Kubuntu instead of Ubuntu, those instructions I linked above should work as-is, without needing to look for "Ubuntu equivalents"?

---

### Post by dukeinid on 2006-11-06
I am having similar problems.  Using 6.10  The driver loads, installs and recognizes that the touch screen device is connected (and also notices when I disconnect it) but it does not actually work.  The ELO setup program (downloaded from the ELO site) complains that the driver isn't installed at all.

Was anybody on this forum able to make the ELO touch screen work with Ubuntu or any variant?

Thank you.

---

### Post by florizs on 2006-11-21
Hello,
I'm turning an epson cash register POS into a music player.
I'm working on the touchscreen myself, I believe its an ELO
If you're still having the problem message me, i'm trying to workout a sollution.
If the case is you've already solved the problem could you send me your xorg.conf?

if i type cat /dev/ttS3 I can see a response from my screen.
hopefully the elo driver will solve it.

---

### Post by jic on 2006-11-28
elo toutchscreen works fine under usb with evtouch driver
but every rebbot I have to edit xorg.conf to set a right event!
then restart X ](*,) 

there's a way to :confused:  set the handler definitly??

 ~$ cat /proc/bus/input/devices 
I: Bus=0003 Vendor=04e7 Product=0020 Version=0107
N: Name="Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB Touchmonitor Interface"
P: Phys=usb-0000:00:0f.4-1/input0
S: Sysfs=/class/input/input2
H: Handlers=event2 js0
B: EV=b
B: KEY=10000 0 0 0 0 0 0 0 0
B: ABS=100 3


---xorg.conf relevant part
Section "InputDevice"
    Identifier "Touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event1
    Option "DeviceName" "Touchscreen"
# Option "Calibrate" "1"
    Option "MinX" "0"
    Option "MinY" "0"
    Option "MaxX" "4000"
    Option "MaxY" "4100"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    Option "SwapY"
EndSection

---

### Post by chuy_max on 2007-10-20
Try my tutorial, it can be found here:

[http://ubuntuforums.org/showthread.php?t=579155](http://ubuntuforums.org/showthread.php?t=579155)

You can find it in the wiki too.

---

