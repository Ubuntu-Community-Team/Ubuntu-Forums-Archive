---
title: "Alps Touchpad Scrolling Issue"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by GoodPanos on 2005-10-16
Does any one have **A to Z** instructions on how to get the vertical scrolling working on an Alps Touchpad.

The touchpad as it is now works fine but I can't do any scrolling.  I've read numerous postings on this issue here and else where and I still can't get it to work.

My Specs are as follows:
[LIST]
[*]Dell Inspiron 6000
[*]Ubuntu 5.10
[*]Package: linux-386 Ver. 2.6.12.16
[*]Package: linux-image-2.6.12-9-686 (I don't have the linux-686 package installed; could that make a difference?) 
[*]Alps touchpad
[/LIST]

Any help is appreciated :smile:

---

### Post by John.Michael.Kane on 2005-10-17
heres a working alps config [http://bugzilla.ubuntu.com/attachment.cgi?id=3525](http://bugzilla.ubuntu.com/attachment.cgi?id=3525)
[http://bugzilla.ubuntu.com/show_bug.cgi?id=14480](http://bugzilla.ubuntu.com/show_bug.cgi?id=14480)

here is the info on the issue..```
 Re: synaptics driver does not work right  Posted by Trent Lloyd  at 2005-10-17 13:17:33 UTC

This was intended to be fixed, unfortunately the new synaptics driver caused worse issues with other people, such as horridly slow mouse speed, and the mouse running off randomly in the wrong direction.

Perhaps this may be fixed for dapper?
```

so from the looks of it. they may get it fixed in dapper.

---

### Post by kooshball on 2005-10-17
[QUOTE=SD-Plissken]heres a working alps config [http://bugzilla.ubuntu.com/attachment.cgi?id=3525](http://bugzilla.ubuntu.com/attachment.cgi?id=3525)
[http://bugzilla.ubuntu.com/show_bug.cgi?id=14480](http://bugzilla.ubuntu.com/show_bug.cgi?id=14480)

here is the info on the issue..```
 Re: synaptics driver does not work right  Posted by Trent Lloyd  at 2005-10-17 13:17:33 UTC

This was intended to be fixed, unfortunately the new synaptics driver caused worse issues with other people, such as horridly slow mouse speed, and the mouse running off randomly in the wrong direction.

Perhaps this may be fixed for dapper?
```

so from the looks of it. they may get it fixed in dapper.[/QUOTE]

I just tried this and it make the cursors more sensitive but it doesnt seem to do anything about the scrolling. I still can't use the vert or horiz scroll. help?

---

### Post by GoodPanos on 2005-10-17
Yep, same here.  I set up my  xorg.conf file to the one recommended here and it didn't make no difference.  I'm still not able to scroll up or down and now it's super sensitive. 

Any other ideas?

---

### Post by Jason King on 2005-12-01
Hi,

this is how I got my alps touchpad on a sony vaio pcg-tr1mp to finally scroll:

observe the output of "cat /proc/bus/input/devices". In my case that's:

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd event0
B: EV=120013
B: KEY=1 80000004 2000000 3002078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=104d Product=0000 Version=0000
N: Name="Sony Vaio Jogdial"
P: Phys=
H: Handlers=mouse0 event1
B: EV=7
B: KEY=40000 0 0 0 0 0 0 0 0
B: REL=100

I: Bus=0010 Vendor=104d Product=0000 Version=0000
N: Name="Sony Vaio Keys"
P: Phys=
H: Handlers=kbd event2
B: EV=3
B: KEY=1f ffff0000 0 20000 100000 0 2 0 0 100400 0 40300400 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
H: Handlers=mouse1 event3 ts0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse2 event4 ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003


Note that the event name for the touchpad is "event4". Set the device name in xorg.conf to "/dev/event/event4" (or whatever the number is on your machine) instead of "/dev/psaux". Moreover, set the protocol to "event" instead of "auto-dev".

Restart X and scroll happily...

---

### Post by postb99 on 2005-12-05
Hi,

I own a Sony Vaio too (PCG-SR11K, a version that seemed to have been sold only in Europe, and not many ones, although I have luck with this laptop for now), but don't have the same output.

```


:~$ cat /proc/bus/input/devices
I: Bus=0003 Vendor=046d Product=c501 Version=0910
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:07.2-1/input0
H: Handlers=mouse0 
B: EV=17 
B: KEY=1f0000 0 0 0 0 0 0 0 0 
B: REL=103 
B: MSC=10 

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
H: Handlers=kbd 
B: EV=120013 
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe 
B: MSC=10 
B: LED=7 

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="AlpsPS/2 ALPS TouchPad"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse1 
B: EV=f 
B: KEY=420 30000 670000 0 0 0 0 0 0 0 0 
B: REL=3 
B: ABS=1000003 

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
H: Handlers=kbd 
B: EV=40001 
B: SND=6 

```

Why don't I have an "event" handler for the touchpad ? I right now have an USB Logitech mouse connected in addition. Anyway this is not the same configuration, I don't have a "glidepoint" alps device, just a "touchpad" one.

I remember it fully scrolled under Windows.

Btw : I run Debian on this, almost switched to Ubuntu but finally did not (had keyboard latency issues with another Dell laptop and XFCE4, not Gnoem, but Gnome is too heavy for this machine...). Guess I should switch to a 2.12-some kernel instead of the 2.11.7 I am running now.

---

### Post by ewinslow on 2005-12-05
GoodPanos,

I know you were on this thread started by ScubaJeff:
[http://ubuntuforums.org/showthread.php?t=78904](http://ubuntuforums.org/showthread.php?t=78904)

Without rereading I suppose it did not work for you. 

I do have the same machine as you and followed ScubaJeff's posted instructions and finally the touchpad is doing all it should. Sensitivity is cured and the scrolling works.

I do have the 686 kernel (2.6.12-10) along with its image and the 386 image is also still on my system, too. I don't think that should have anything to do with your issue, but then again, I am no expert.

Good luck.

---

### Post by Unicast on 2005-12-06
Wa-hoo!

I've just re-read the ScubaJeff thread and finally got the scrolling to work on my Dell Latitude D400. Yay, get in there!

I couldn't get mine to work even after adding all the extra lines into the xorg.conf, but finally got there when I realised I'd got the wrong event# - changed it to that reported by *cat /proc/bus/input/devices* and bingo!

This forum rocks!

EDIT: Also had a nasty introduction to *vim* when I mis-matched the InputDevice name in the ServerLayout section and X didn't load up!

---

