---
title: "Intermittent unresponsive USB mouse and keyboard"
date: 2012-04-02
forum: Hardware
---

### Post by timjstewart on 2012-04-02
About twice a day, my mouse and keyboard both stop responding to input (e.g. pressed keys, clicked mouse buttons and mouse motions).  My screen continues to update normally (the clock advances, etc.).  When this occurs, I've found that I can take the USB cables for my mouse and keyboard out of the USB ports on the back and put them into the USB ports in the front, and they become responsive again.  If I try to put the USB cables into the back again (after the back USB ports failed), they still do not work.  After some more time (hours sometimes), the front USB ports fail and then I have to hold down the power button until the computer turns off and then I reboot, and the keyboard and mouse work fine.

After installing the proprietary ATI/AMD FGLRX video driver, the problem seems to have decreased in frequency (from failing every 15 minutes, to failing every 3-4 hours).

Computer: HP Compaq 8200 Elite
Keyboard: USB Microsoft Natural Ergonomic Keyboard 4000 v1.0
Mouse: USB Logitech Mx510 Optical Mouse
Video: dual Dell P2411H monitors with a resolution of: 1920x1080@60 Hz 
Proprietary Drivers: ATI/AMD proprietary FGLRX graphics driver

I thought it might be Unity so I installed XFCE and ran that instead for a while but that but it did not help prolong the responsiveness of my mouse and keyboard.

% uname -a
Linux timbuntu 3.0.0-17-generic-pae #30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012 i686 i686 i386 GNU/Linux

% lsusb -vt
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
        |__ Port 3: Dev 3, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 3: Dev 3, If 1, Class=HID, Driver=usbhid, 1.5M
        |__ Port 5: Dev 5, If 0, Class=HID, Driver=usbhid, 1.5M

---

### Post by timjstewart on 2012-04-03
I unistalled the proprietary driver that Ubuntu offered in the "Additional Drivers" dialog, downloaded the most recent version of that driver from the manufacturer's [web site]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English") and have not had a problem since.  That was only a few days ago so time will tell.

---

### Post by timjstewart on 2012-04-10
The driver update did not fix my problem.  My keyboard and mouse both became unresponsive today twice so I had to reboot.

---

### Post by Dreamer Fithp Apprentice on 2012-04-19
I'm having the same problem with my keyboard.  I was having a similar problem with my trackball but in that case I believed the problem to be a hardware problem with the trackball. I still think that was the case with the trackball. I took it apart and found that if I pressed down on a particular spot it would work. I haven't made a practical fix yet so I am using mouse keys for the moment. My keyboard is almost new and it is made by Unicomp which I regard highly as a manufacturer so I am doubtful it is the problem. It conceivably could be worn usb connectors. I am at this moment downloading Dragonfly BSD to install on another partition so as to have an OS with as little in common with Ubuntu as possible. If the problem is the same with it I will regard it as strong evidence, although still not conclusive, that the problem is somewhere in the hardware, probably in the motherboard, defined broadly to include the integrated usb female fittings. I call them female fittings because I refer to the actual physical objects and not to an abstract software entity and the word "port" seems to be used in a confusingly ambiguous way.  I welcome suggestions for more correct nomenclature.

I would also appreciate any diagnostic suggestions. Well, BSD download just finished. Gotta fire up K3B.  Wish me luck, OP. I'll report back.

---

### Post by efflandt on 2012-04-20
I had a similar problem when my video card was failing.  Although, it was a different brand of chip (nvidia GT 430 made by Galaxie).

I initially had problems in Win7 where the screen would freeze or get weird (random color pattern), and then Windows would say that "video driver had become unresponive, but recovered" (with various nvidia drivers).  In Ubuntu 11.10 the keyboard and mouse buttons would occasionally become unresponsive, mouse cursor would still move, but I could not click on anything.  I almost thought it was not happening in Ubuntu 10.10, but eventually it did, just rarely.

I replaced it with a different nvidia card (from EVGA) and have not had a problem since.

---

### Post by timjstewart on 2012-04-20
I switched to a PS/2 keyboard (I'm still using the USB mouse), and I have not had a freeze up in days.

---

### Post by Dreamer Fithp Apprentice on 2012-04-22
I couldn't do the Dragonfly test I was expecting to because Dragonfly doesn't like the VGA monitor I'm using temporarily since I accidentally drowned my more modern monitor. I will do so and report as soon as possible.

> **efflandt said:**
> I had a similar problem when my video card was  failing.  Although, it was a different brand of chip (nvidia GT 430 made  by Galaxie).

I initially had problems in Win7 where the screen would freeze or get  weird (random color pattern), and then Windows would say that "video  driver had become unresponive, but recovered" (with various nvidia  drivers).  In Ubuntu 11.10 the keyboard and mouse buttons would  occasionally become unresponsive, mouse cursor would still move, but I  could not click on anything.  I almost thought it was not happening in  Ubuntu 10.10, but eventually it did, just rarely.

I replaced it with a different nvidia card (from EVGA) and have not had a problem since.

I've been plagued with these exact symptoms in the past. They seemed to  be associated with very high cpu usage as reported by top or system  monitor. It seems to me it went on for a couple of months. I don't  recall doing anything directed at the problem that made any difference.  It was intermittent then so I can't say I noticed when it stopped. I  remember installing a more recent driver for my Nvidia card that I had  to get from the Nvidia site directly hoping that would stop it but it  didn't. Can't say for sure when it was but I'm fairly sure I was using  only Ubuntu at the time although I don't recall what versions I saw it  under.  Presumably some update stopped it. However I think this is a  very different problem from the one OP had and I still have.

> **timjstewart said:**
> I switched to a PS/2 keyboard (I'm still  using the USB mouse), and I have not had a freeze up in days.

When you say PS/2 you are referring to the nature of the connector between the kb and the mobo, not the brand of keyboard, correct? A round job with pins around about 3/4 of the perimeter, right? And if I understand you correctly, you did this by getting another keyboard, not by using a usb-ps/2 adaptor, right? If that is the case, do you have a reason to suspect that the nature of the connector is significant as opposed to it simply being a different keyboard? I would really appreciate it if you are still around if you could clarify this for me when you read this and also let us know if it is still working for you in a week or two because I have exactly the same symptoms. In my case I tend not to suspect my kb, which is a fairly new Unicomp and the best keyboard I've had since my IBM died, as much as either the motherboard, which is not so new, or some software problem.  Worn connectors are a possibility but I've connected an external HD to the same usb sockets (not at the same time obviously) and never seen a problem.  Thanks.

---

### Post by timjstewart on 2012-05-01
I upgraded to 3.2.0-24-generic-pae about four days ago, reconnected the USB keyboard and have not had a freeze-up since.  Perhaps this issue has been fixed.  :)

---

### Post by timjstewart on 2012-05-16
The upgrade to 12.04 did not fix the problem.  Even with my PS/2 keyboard and USB mouse, the mouse still occasionally freezes up.  The first time it freezes, I switch to a different bay of USB ports.  The second time it freezes, I've run out of USB ports and I have to reboot.

---

### Post by phasegen on 2012-05-31
I have a Microsoft Natural usb keyboard, and occaisionally it is _rendered unresponsive by an update, and starts to operate again after another update_. It has only happened running the 64 bit version of Ubuntu. I am trying to figure out what updates do it, and know for sure that kernel updates are sometimes responsible, though once it was caused by an xserver update.
I dual boot. The keyboard always works in GRUB. I have never experienced a problem with my usb mouse.

---

### Post by nodjoim on 2012-06-02
I have a similar situation, using a Toshiba Tecra laptop with Nvidia graphics and Ubuntu 11.10. Especially when I use a second screen, which I do most of the time, my computer takes a long time after logging in to become responsive. It reminds me very much of a Windows system! Starting up any application right after logging in takes ages :-((. On top of that, I also experience the intermittent unresponsiveness of keyboard and mouse. The "remedy" is to simply wait a while (like half a minute) for it to become responsive again. I do suspect the Nvidia driver because it has given me a lot of headaches to recognize my second screen correctly.

---

