---
title: "Problem with pointer stick on a Compaq Evo N400c"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by benjy on 2006-01-17
Hi there, the basic premise of the problem is that the 'pointing stick' on my laptop has gone crazy. It has a will of it's own. I know this is nothing to do with ubuntu but when I first recieved the laptop it had XP on it so I could just disable it and use a USB mouse...

However, this seems to be a very difficult thing to achieve in Ubuntu.

Having searched a lot on the forum regarding both my specific laptop AND anything referring to a pointing stick... I have become stuck. I just cannot disable this thing. And to add insult to injury none of my screwdrivers fit the case so I cannot just unplug it.

The first thing I did was check the bios setup to see if there was some way I could disable it - alas no. All it offers me is to disable or enable multiple input devices which, on either setting makes no difference.

I then tried simply commenting out what's referred to as a trackpad in the xorg conf but still nothing.

If someone could assist me on this I would be very grateful - armed only with the tab button my finger is beginning to ache :(

Cheers

Benjy

ps. I accidently posted this in the hoary forum. My apologies.

---

### Post by benjy on 2006-01-24
Well, it looks like I've managed to sort this out now anyway.

Basically, despite the xorg file saying the "pointer stick" is using the synaptics driver it is not.

If you are using a usb mouse and don't wish the little nub in the middle of the keyboard to control your life just:

sudo modprobe -r psmouse

I had assumed this would disable the usb mouse but apparently it doesn't.

One more thing - ignore what people say about simply putting a hash in front of the innputdevice entry in your xorg file - that makes no difference.

Hope this is useful to someone else.

Cheers

Benjy

---

### Post by v3nd3tta7 on 2007-11-16
:guitar: dude you're awesome, thanks for posting this! Works perfectly! Seems like so many other people gave up, I was getting a little frustrated. Cheers mate.

---

