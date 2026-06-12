---
title: "canon canoscan D646U"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by ubuntu_demon on 2005-03-13
Hi,

Does anyone have this puppy(canon canoscan D646U) working ?

---

### Post by kleeman on 2005-03-13
According to the sane website

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

this "puppy" is a "dog" (sorry about that ;-)) i.e. unsupported.

---

### Post by ubuntu_demon on 2005-03-13
[QUOTE=kleeman]According to the sane website

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

this "puppy" is a "dog" (sorry about that ;-)) i.e. unsupported.[/QUOTE]
 yeah I know that's why I posted here :)

---

### Post by omiazad on 2005-06-12
I've noticed that this forum is not that helpful for anything. Though there is not solution, other should help, but no one respond to this thread from a long time. As I also have the same Scaner, I need some help for using that.

---

### Post by ubuntu_demon on 2005-06-12
[QUOTE=omiazad]I've noticed that this forum is not that helpful for anything. Though there is not solution, other should help, but no one respond to this thread from a long time. As I also have the same Scaner, I need some help for using that.[/QUOTE]
 the forum is quite helpful but sometimes things get "digged in". Since this is an old thread only people who specifically search for this thread find it. (I am subscribed to all threads I started)

No solution at this point as far as I know. We still have to dual boot (or buy another scanner)

---

### Post by omiazad on 2005-06-29
[QUOTE=demon666_nl]No solution at this point as far as I know. We still have to dual boot (or buy another scanner)[/QUOTE]

Okey. But what about [http://canonscanner.sourceforge.net/](http://canonscanner.sourceforge.net/) I'm very new in Linux, but perhaps you can find a way to compile them and make this Puppy work. ](*,)

---

### Post by ubuntu_demon on 2005-06-29
[QUOTE=omiazad]Okey. But what about [http://canonscanner.sourceforge.net/](http://canonscanner.sourceforge.net/) I'm very new in Linux, but perhaps you can find a way to compile them and make this Puppy work. ](*,)[/QUOTE]
 great work!
at first I couldn't find anything about the D646U there but when I browsed the CVS I found 

(file) ct_D646U.c at :

[http://cvs.sourceforge.net/viewcvs.py/canonscanner/canon/](http://cvs.sourceforge.net/viewcvs.py/canonscanner/canon/)

I will look into this. Maybe we'll get this working!!!

---

### Post by ubuntu_demon on 2005-06-29
[http://www.sane-project.org/unsupported/canon-d646u.html](http://www.sane-project.org/unsupported/canon-d646u.html)

So this was the testprogram. I couldn't get this testprogram to work because it wants to read from /dev/usb/scanner (this is a file)

while my scanner hangs is at : libusb:0 02:002 (this is not a file)

But since it's a testprogram. I don't think it will work nicely anyway. I'm going to mail him about how to get the program to work with libusb.

> 
This is a test program for CanoScan D646U USB scanner.

In order to get your scanner be recognized, you need to
add the following line to modules.conf or conf.modules:

options scanner vendor=0x04a9 product=0x220b


This program comes WITHOUT warranty.

Francesco Salvestrini (salvestrini@users.sourceforge.net)


I sent him this mail :

> 
Hi,

I am a moderator of ubuntuforums.org. I have a canon D646U. And I want to run your testprogram.

Your testprogram looks at the wrong place for my scanner :

Unable to open scanner device ('/.dev/usb/scanner0'): No such device

How do I get your testprogram to work with libusb ?

sane-find-scanner :

found USB scanner (vendor=0x04a9 [Canon], product=0x220b [CanoScan]) at libusb:0 02:002

I run Ubuntu hoary. 

/proc/version :

Linux version 2.6.10-5-686-smp (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 SMP Fri Jun 24 18:12:58 UTC 2005

Here's a thread about trying to get the D646U getting to work in Ubuntu: 

[http://www.ubuntuforums.org/showthread.php?p=233783](http://www.ubuntuforums.org/showthread.php?p=233783)

Thank you very much.


I also sent him the results of :
$sane-find-scanner -v -v

and the interesting part of :
$cat /proc/bus/usb/devices

---

### Post by omiazad on 2005-06-29
But my Puppy's name is **D646U ex**

---

### Post by ubuntu_demon on 2005-06-29
[QUOTE=omiazad]But my Puppy's name is **D646U ex**[/QUOTE]
 I didn't know but it doesn't matter much since this page : [http://www.sane-project.org/unsupported/canon-d646u.html](http://www.sane-project.org/unsupported/canon-d646u.html)

Is about both :

> 
Scanners not supported by SANE
Manufacturer and model

Canon Canoscan D646U
Canon Canoscan D646U ex
Bus type

USB
Vendor ID

0x04a9
Product ID

0x220b 


---

### Post by omiazad on 2005-06-29
Let's see what's written in out fate. :)

---

### Post by oenggun on 2006-08-26
This thread has been 1 year old since the last post,... is there any solution for this scanner problem?

I'm not a programmer, I'm totally blind to coding any lines of code for computer. Any help would be much appreciated.

thanks,
~un~

---

### Post by omiazad on 2006-08-27
No

---

### Post by ubuntu_demon on 2006-08-30
> **omiazad said:**
> Yes!

Canon Japan sent me some drivers and they worked fine. But I don't have that right now as I changed my printer.

Can you attach these drivers to a new post ? It would be great if I could get my scanner to work :-D

thanks

---

### Post by capsel on 2006-10-03
I'm owner of D646U, too.
Omi Azad, could you share your drivers with us (or me)? If it is possible I can put them on on my http server to give them to others searching it.:-D

---

### Post by omiazad on 2006-10-03
I don't have the drivers. It was a miss understanding.

Sorry!

---

### Post by ubuntu_demon on 2006-10-07
DoctorMo gave me this suggestion :

[quote=DoctorMo]
Ah it might be worth revisiting the SANE drivers for canon scanners, I've found that even if your scanner isn't listed explicitly adding a definition in the right driver for your scanner will work (remember to send the patch back to developers)

download sane 1.0.18 from sane website
edit the backend/plustek-usbdevs.c file, this contains the canoscan D660U driver, you need to find somewhere neer the bottom of the file is a list of definitions, create a new definition containing the USB hex numbers you get from `lsusb` and you'll need a colour profile too but you might get away with the same profile as the D660U.
[/quote]

You will have to compile it ofcourse. I have never used a scanner in Linux so it will cost me a bit of time to figure it out. I haven't tried it yet because I'm quite busy.

---

### Post by DoctorMO on 2006-10-07
It's worth it because it gives you a nice warm glow that you've enabled that scanner for everyone else in the linux world :-)

I did this for the Canon MP360 multifunction device. printer worked, scanner didn't. used the same driver as the MP730 thus reconfigured witht he help of the sane developer and everythings great.

---

### Post by ubuntu_demon on 2006-10-08
> **DoctorMO said:**
> It's worth it because it gives you a nice warm glow that you've enabled that scanner for everyone else in the linux world :-)

I did this for the Canon MP360 multifunction device. printer worked, scanner didn't. used the same driver as the MP730 thus reconfigured witht he help of the sane developer and everythings great.
I totally agree.

It's just that my scanner lives with my mum (with most of my stuff) while I live with my girlfriend (she doesn't have much space). When I'm at my mum's place there's lots of other stuff to do. Last weekend for example I reconfigured my server and moved it by train to my girlfriend's place.

I will definetely spend time on the scanner. I just don't know when. I'm quite busy these days :).

---

### Post by Gardon on 2006-12-09
I tried to edit the plustek file, but it didn't make any difference. Here is the lsusb:

> Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0458:000e KYE Systems Corp. (Mouse Systems) VideoCAM Web
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 04a9:220b Canon, Inc. CanoScan D646U
Bus 001 Device 001: ID 0000:0000


sane-find-scanner:

> # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04a9 [Canon], product=0x220b [CanoScan]) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


scanimage -L :
> 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


Can anyone help, or have information on how to write a backend for sane?
I really want my scanner to work, cause I don't have dual boot,

Thanks!!

---

### Post by HuwSy on 2007-03-06
Anyone managed a solution yet? Or is this a doomed feature.

---

### Post by HuwSy on 2007-03-07
Is it possible to get this device running through Wine somehow, as iv seen ppl elsewhere say theyv done it with other scanners that arent supported by sane in order to capture the device signals. But nothing recent to ask anyone about.

---

### Post by ubuntu_demon on 2007-03-26
> **ubuntu_demon said:**
> DoctorMo gave me this suggestion :

[quote=DoctorMo]
Ah it might be worth revisiting the SANE drivers for canon scanners, I've found that even if your scanner isn't listed explicitly adding a definition in the right driver for your scanner will work (remember to send the patch back to developers)

download sane 1.0.18 from sane website
edit the backend/plustek-usbdevs.c file, this contains the canoscan D660U driver, you need to find somewhere neer the bottom of the file is a list of definitions, create a new definition containing the USB hex numbers you get from `lsusb` and you'll need a colour profile too but you might get away with the same profile as the D660U.


You will have to compile it ofcourse. I have never used a scanner in Linux so it will cost me a bit of time to figure it out. I haven't tried it yet because I'm quite busy.[/QUOTE]
I haven't been able to follow up on it. Feel free to try it out :).

---

### Post by HuwSy on 2007-03-28
Iv had a few goes, but its a non worker, without a lot of code changes beyond my ability.  Any other ideas anyone.

---

### Post by HuwSy on 2007-04-26
Iv noticed this here [http://www.kegel.com/linux/sq4800.html](http://www.kegel.com/linux/sq4800.html) and wondering if anyone can get somethig like this to give access for windows apps in wine to the scanner atleast.  Or wont it pass on the windows commands directly to the device.  The problem Im having 1st off is that wine no longer uses a .winerc file so im not sure where to add the device. Any ideas?

---

### Post by hyperair on 2007-05-28
Hey I just discovered that it's possible to connect the scanner to VirtualBox, even without support :P I'm going to try it now. I'll post back later if it works.

---

### Post by HuwSy on 2007-05-28
I have tried some virtualisation methods to varying success, Iv not had a chance to try with virtual box, and couldnt get qemu to connect the usb interface correctly. But VMware allows, so its possible to have a 'lite' windows 98 image with scanner support and network bridge taking like 50mb to use soly for scanning but this does defeat the object a little imo.  Theres ways of traceing all the usb data passed bothways in these solutions and somehow using this to make a backend for sane but iv not had the chance or understanding to do ths myself.

---

### Post by hyperair on 2007-05-28
It worked! Just connect it and install the software as you normally would. :P

EDIT: I reckon VirtualBox allows direct access to the raw interface of the scanner, and so it worked perfectly, just like it should :P

---

### Post by ubuntu_demon on 2007-05-28
> **hyperair said:**
> It worked! Just connect it and install the software as you normally would. :P

EDIT: I reckon VirtualBox allows direct access to the raw interface of the scanner, and so it worked perfectly, just like it should :P
I'm not familiar with VirtualBox. Is it to run windows in a virtual machine ?

---

### Post by hyperair on 2007-05-28
Yeah that's right.

---

### Post by Skerit on 2007-11-10
Emulating windows IS NOT an option, come on!

It can't be impossible to get this thing to work, right?

---

### Post by hyperair on 2007-11-10
It's actually good enough for most of us. Earlier in this thread there was a link which pointed to the source code of a prototype driver for the D646U. Unfortunately I can't get it to run.

---

### Post by omiazad on 2007-11-10
It's actually Canon's fault that they didn't make the compatible driver. I strongly recommend Linux users not to buy any Canon Imaging products, except Digital Cameras.

---

