---
title: "HP TouchSmart, does the touch screen work with ubuntu?"
date: 2008-11-21
forum: Hardware
---

### Post by Durham on 2008-11-21
I'm working as a teacher, and my school wants to buy tablet-PC's. Are there software in Ubuntu to support the funtionality in these? 

Thanks :)

---

### Post by brunom9 on 2009-08-27
Hi,

You can get the Touchsmart working with ubuntu but a little tweaking will be necesary, so if you're not comfortable with typing code, get someone to help you.

I've followed all of these guides:

[http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)
[http://rkvsraman.blogspot.com/2008/10/gotcha-for-hp-touchsmart-pc.html](http://rkvsraman.blogspot.com/2008/10/gotcha-for-hp-touchsmart-pc.html)
[https://wiki.cse.unsw.edu.au/~jlennox/cgi-bin/moin.cgi/powmri/touchsmart](https://wiki.cse.unsw.edu.au/~jlennox/cgi-bin/moin.cgi/powmri/touchsmart)

Everything is working except for the right click, haven't gotten into it yet. I'm replying from an IQ810 running Jaunty 9.04 amd64

Cheers,

---

### Post by Favux on 2009-08-27
Hi Durham and brunom9,

The answer is yes.  You can get the stylus and touch working.  However as yet there is no multi-touch.  Several people are looking into it.

If you want to get the TX2z working in Jaunty see Appendix 2 here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  It gives you the links to Ayuthia's kernel patching HOW TO and his kernel deb.s.  The xorg.conf is attached below it.

Also Method 4 on the same link shows you how to get automatic screen rotation.

---

### Post by brunom9 on 2009-08-27
Favux,

Great news, thanks. Right now I'm working with a HP Touchsmart desktop, next buy will be a tx2 for sure. Will get to work on getting everynthig done then.

Cheers.

---

### Post by Favux on 2009-08-27
Hi brunom9,

It would be interesting to know what digitizer HP uses for the desktop touchsmart.  Do you know?

With:
```
more /proc/bus/input/devices
```
The N-trig digitizer with Vista firmware identifies as:
```
I: Bus=0003 Vendor=1b96 Product=0001 Version=0110
N: Name="HID 1b96:0001"
P: Phys=usb-0000:00:14.5-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.0/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=1b
B: KEY=2401 0 0 0 0 0
B: ABS=73000001000003
B: MSC=10

```
and with Win 7 firmware:
```
I: Bus=0003 Vendor=1b96 Product=0001 Version=0110
N: Name="HID 1b96:0001"
P: Phys=usb-0000:00:14.5-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input9
U: Uniq=
H: Handlers=mouse2 event9
B: EV=1b
B: KEY=2c03 1 0 0 0 0
B: ABS=73000001000003
B: MSC=10
```
The Dell XT's also have the same Vendor, Product, and Version id's.

---

### Post by brunom9 on 2009-09-02
Hi Favux,

Found another thread and combined couple of other posts, so finally what I changed was my X11, the Option pointing to the event:

 ```
Option "Device" "/dev/input/event4"

```

For a path:
```

 Option "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.2-event-mouse"


```The pci-0000:00:1d.0-usb-0:1:1.2-event-mouse being the result of a ```
ls -l /dev/input/by-path
```:

```
total 0
lrwxrwxrwx 1 root root 9 2009-09-01 11:33 pci-0000:00:1d.0-usb-0:1:1.0-event-kbd -> ../event3
lrwxrwxrwx 1 root root 9 2009-09-01 11:33 pci-0000:00:1d.0-usb-0:1:1.2-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2009-09-01 11:33 pci-0000:00:1d.0-usb-0:1:1.2-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2009-09-01 11:33 pci-0000:00:1d.1-usb-0:2:1.0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 9 2009-09-01 11:33 pci-0000:00:1d.1-usb-0:2:1.1-event-mouse -> ../event6
lrwxrwxrwx 1 root root 9 2009-09-01 11:33 pci-0000:00:1d.1-usb-0:2:1.1-mouse -> ../mouse2
lrwxrwxrwx 1 root root 9 2009-09-01 11:33 platform-pcspkr-event-spkr -> ../event7
```


Just matched the events, found the path.

Now it works like a charm.

Here's the listing of ```
more /proc/bus/input/devices
```

```
I: Bus=0003 Vendor=1926 Product=0003 Version=0100
N: Name="NextWindow Touchscreen"
P: Phys=usb-0000:00:1d.0-1/input2
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.2/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=1f
B: KEY=401 70000 0 0 0 0
B: REL=100
B: ABS=f
B: MSC=10

```

---

### Post by Favux on 2009-09-02
Hi brunom9,

Wow, great job!  Thanks for the information.

I found a couple post, one with the TouchSmart (NextWindow Touchscreen) in Hardy and the other in Intrepid.  Sounds like you already have them.

---

### Post by costolleumus on 2009-09-02
PLEASE people, can any one help me? Im trying to make this to work all day and I get nothing! I have HP Touchsmart IQ 515, can anyone tell me what I need to type in xorg???
BDW sorry for my english.

---

### Post by Favux on 2009-09-02
Hi costolleumus,

Welcome to Ubuntu Forums!

Hopefully brunom9 can help you.

In the meantime here are two links that may help.

First one uses Hardy and xorg.conf:  [http://rkvsraman.blogspot.com/2008/10/gotcha-for-hp-touchsmart-pc.html](http://rkvsraman.blogspot.com/2008/10/gotcha-for-hp-touchsmart-pc.html)  Notice brunom9 shows you how to get the usb pci by-path you can use in xorg.conf

Second one is for Intrepid and uses a .fdi:  [https://wiki.cse.unsw.edu.au/~jlennox/cgi-bin/moin.cgi/powmri/touchsmart](https://wiki.cse.unsw.edu.au/~jlennox/cgi-bin/moin.cgi/powmri/touchsmart)  But links to NextWindow's sample xorg.conf.

I hope this helps.

---

### Post by iboot on 2009-09-03
When I installed Ubuntu 9.04, on the HP tx2z, touchscreen started working with the pen right out-of-the-box. So as long as I use the pen provided, I can do everything a mouse does except right-click. So drag and drop, select and click are all working well.

After changing the driver to the ATI (selected under system..hardware) I also got default compiz effects to work, although I don't see the fancy options for desktop cube etc., I can minimize and maximize with the bouncy effects.

I have seen many posts on how to get the touch with finger and the rotation to work, but there are so many settings that it is a bit overwhelming for a beginner like me. I plan to roll up my sleeves and get into it one of these days, but I was just wondering if some of the gurus out there can compile one package or script that I can simply run and get the touch and rotation to work?

Thanks in advance!

---

### Post by Favux on 2009-09-03
Hi iboot,

Closest to what you want is this HOW TO:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)

The bad news is that with the ATI proprietary drivers and Compiz rotation doesn't work right.  You can still use Compiz in landscape if you turn it off before rotating.

---

### Post by iboot on 2009-09-03
> **Favux said:**
> Hi iboot,

Closest to what you want is this HOW TO:  [http://ubuntuforums.org/showthread.php?t=1252492](http://ubuntuforums.org/showthread.php?t=1252492)

The bad news is that with the ATI proprietary drivers and Compiz rotation doesn't work right.  You can still use Compiz in landscape if you turn it off before rotating.


Hi Favux,

Can I just follow the steps 5 and 6 to get touch and rotation to work, or do I need to do the n-trig and xconf changes as well? I already have the stylus working well, but just need the screen to start recognizing the touch by finger and change orientation to Potrait when rotated.

Will rotation work if I just follow step 5? The referenced HOW-TO presents many methods of doing it. Which one is the simplest?

Thanks!

---

### Post by Favux on 2009-09-03
Hi iboot,

If you want touch you have to either patch the kernel or use the kernel deb.s and the xorg.conf.  If you are happy with just the stylus we can add a line to the .fdi to give you the button click.

Well like it says in 5) Methods 1 and 3 will work.  If you want Compiz you can use the Compiz off Rotation script attached to the bottom.  Just read things through before deciding.  Actually they are all pretty simple once you wrap your head around them.

If you want automatic rotation then either the script or the applet.  You should be able to integrate Compiz off into either.

---

### Post by iboot on 2009-09-04
I see. So I made the xconf changes as documented and my button click is working, but the touch is not. I tried to turn on touch using the command line, but no effect. any troubleshooting tips?

```
Section "InputDevice"
    Identifier    "stylus"
    Driver        "wacom"
#   The by-path below is for the HP TX2z with Vista firmware
    Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
    Option        "Type"        "stylus"
    Option        "USB"        "on"
    Option        "Button2"    "3"    # make stylus button R mouse click
EndSection
Section "InputDevice"
    Identifier    "touch"
    Driver        "wacom"
#   The by-path below is for the HP TX2z with Vista firmware
    Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
    Option        "Type"        "touch"
    Option        "USB"        "on"
    Option        "Touch"        "on"
    Option        "TopX"        "0"
    Option        "TopY"        "0"
    Option        "BottomX"    "9600"
    Option        "BottomY"    "7200"
EndSection
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
#    Identifier    "X.org Configured"    # New for Jaunty?
    InputDevice    "stylus"    "SendCoreEvents"
#   Remove the comment below if you have an eraser.
#    InputDevice    "eraser"    "SendCoreEvents"
    InputDevice    "touch"        "SendCoreEvents"
EndSection
```

---

### Post by Favux on 2009-09-04
Hi iboot,

I'd like to point out we are "hijacking" this thread.  This is for the TouchSmart desktop pc not the tablet.

Good, at least you've got the stylus button along with the stylus.  Well did you comment out the n-trig section in 10-wacom.fdi?  Did you do the kernel patches or deb.s?

---

### Post by anikilol on 2009-09-04
I have an hp touchsmart iq775, and it worked out of the box for me O_O

---

