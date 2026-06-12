---
title: "Mixeosoft Wireless Entertainment Desktop 7000 Works in Feisty"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by Gestalt73 on 2007-04-14
The Short Version:
This keyboard and mouse combo works out of the box in ubunty feisty, no configuration is necessary, and most major features are supported.  It "just works."

The Longer Version:
I've been looking around for a good HTPC keyboard for my set-up, and wasn't really satisfied with the RF Versapoint.  This keyboard was recieving good reviews, but I couldn't find any posts or reviews that indicated that it would be supported in Linux.  There was a posting here about success with the Microsoft Optical bluetooth Keyboard here:
[http://ubuntuforums.org/showthread.php?t=227057&highlight=microsoft+keyboard]("http://ubuntuforums.org/showthread.php?t=227057&highlight=microsoft+keyboard")

Link to Keyboard description
[http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=081]("http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=081")

Highlights:
[LIST]
[*]The bluetooth dongle is recognized
[*]The keyboard is recognized and works with no configuration
[*]The mouse is recognized and works with no configuration
[*]The mouse scroll wheel works
[*]The keyboard touch pad and mouse buttons are supported, but the touchpad is "different"
[*]The function keys are supported (but they're not really keys, more like touch sensitive areas)
[*]The mute and volume buttons are supported
[*]The rest of the media keys may or may not be supported, I know they don't do anything on my setup
[*]The keyboard layout has a curve to it that takes a few minutes to get used to
[/LIST]

So far I can't recommend this enough.  And if you can wait a few months, they'll have a new version out with a backlit keyboard.  That should be coming out in September.

Alan

---

### Post by phish108 on 2007-11-29
Hi,

I found Alan's post helpful in Getting myself a "Microsoft Wireless Entertainment Desktop 7000".

The bluetooth keyboard and mouse run smoothly with ubuntu 7.10 out of the box.

The keyboard comes with a touchpad build in, which works as a second mouse. As Alan reported there are no problems with the basic functions. 

Furthermore, the keyboard has a Fn-key (like many laptops have) and a couple additional function keys (a communication button, a 'gadets' button, a zoom button, and two channel buttons for up and down), and some multimedia keys. 

There are no problems with the multimedia keys

The Fn-key does not always send a key code if it is used with another key. The keyboard has a bunch of labels printed on that indicate where key codes should be expected. However, only a few of them work (about a third of the labeled keys, mostly the Num pad emulation). 

I am wondering whether I missed something in making the Fn-key work properly.

The additional function keys which I listed above do not send key codes.

I tried to access them via KeyTouch, but no key codes on the mentioned keys were recognized. 

Finally, I was toying with the XKB settings (with the older MS protocols) with no success. I.e. the behavior of the keyboard did not change. 

Has anyone more experiences with that keyboard hardware? 

Christian

---

### Post by cyberkost on 2007-12-14
OP, could you please replace "Mixeosoft" with "Microsoft" in the title (not that I like the company, but so that the post is found by more searches -- I think this keboard is great and needs to be discussed in greater details).  Anyone else out there who could comment which features of this keyboard work and don't work (and how to make them work?!) with Ubuntu 7.10.  Thanks!

---

### Post by phish108 on 2008-03-13
Hi, I fear nobody will read this ...

After using the "microsoft wireless entertainment desktop" keyboard for a while I wanted to find out why I cannot use all of the keys it has. 

Finally, I figured out that the kernel usb_hid driver does not return the all key presses for the keyboard. By running 

   cat  /dev/input/by-id/usb-Microsoft_Microsoft_Wireless_Entertainment_Keyboard_7000_00125A5E5F71-event-kbd

I only  got  responses for some of the extra keys. 

I also tried the USB dongle with m$ windows, where all keys send events.

Interestingly, I get all events from the keyboard via

/dev/usb/hiddev0

I wonder why the events are not reported for the input device.

Christian

---

### Post by phish108 on 2008-03-13
OK, this is the last bit that I found out and am able to handle myself: 

/dev/usb/hiddev0 returns all events from the keyboard

/dev/input/by-id/usb-Microsoft*event-kbd  returns only some of the events.

However, there is a drawback. The values that are returned by the two sources are not the same. Thus, it is not possible to use hiddev0 as an alternative for the /dev/input/* method.

I digged a bit into the linux-usb documents and mailing lists and it appears that the  problem is on the HID-keyboard driver level. This means, without a patch of the kernel modules it is not possible to gain access over the additional keys of this nice keyboard.

Cheers
Christian

---

