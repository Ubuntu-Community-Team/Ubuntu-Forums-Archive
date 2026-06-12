---
title: "Can't use keyboard with USB extension cable?"
date: 2023-07-24
forum: Hardware
---

### Post by clepsdyrae on 2023-07-24
I have an apple keyboard that I am using with my linux machine (Kubuntu 23.04). Works great. (Mouse is also plugged into the keyboard.)

It's currently plugged into the side of a monitor. I wanted to plug it into a USB port on the front of my desktop case. Plugged in to that port directly, it works fine, but the cable is too short. I got a USB male/female extension off eBay (approximately 2 feet long), but it doesn't work. Sometimes, after a significant delay, it does work.

That USB extension cable had no shielding, which I guessed might be the issue, so I bought a different one (~8 feet long). It is shielded. On both cables I confirmed connectivity of all four pins and that the plugs are clean, etc. Resistance for all five connections measures less than 4 ohms.

It also works if I plug the extension cable into the monitor.

Summary:

Monitor -> extension cable -> keyboard: works
Monitor -> keyboard: works
Front of case -> keyboard: works
Front of case -> extension cable -> keyboard: doesn't work

When it fails to connect, In journalctl I see the following lines over and over again (along with many, many snap_cups related lines failing with exit code 1, but that seems to happen all the time regardless of functionality):

```
Jul 24 13:00:26 mycomputer kernel: usb 3-14: new high-speed USB device number 95 using xhci_hcd
Jul 24 13:00:26 mycomputer kernel: usb 3-14: New USB device found, idVendor=05ac, idProduct=1006, bcdDevice=96.15
Jul 24 13:00:26 mycomputer kernel: usb 3-14: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 24 13:00:26 mycomputer kernel: usb 3-14: Product: Keyboard Hub
Jul 24 13:00:26 mycomputer kernel: usb 3-14: Manufacturer: Apple, Inc.
Jul 24 13:00:26 mycomputer kernel: usb 3-14: SerialNumber: 000000000000
Jul 24 13:00:26 mycomputer kernel: hub 3-14:1.0: USB hub found
Jul 24 13:00:26 mycomputer kernel: hub 3-14:1.0: 3 ports detected
Jul 24 13:00:26 mycomputer kernel: usb 3-14: USB disconnect, device number 95

```

Any idea what is going on?

---

### Post by TheFu on 2023-07-25
I had a Logitech keyboard that worked connected to 3 out of 4 computers (I have a 4-port KVM switch).  I moved all the cables around to determine it wasn't the KVM switch. The problem was only with 1 computer.  That computer was identical to another with the same motherboard, same CPU, same RAM, exact same BIOS version.  That left just the connection between the KVM and the computer as the possible culprit.  

I'd tried a number of different connectors (it was male-to-male USB) that I had already, none made any difference.  

Ordered a 3-pak and it seemed to make everything work.  So, all I can say is that not all USB cables are the same.  I wouldn't expect any to be different, but there seem to be some differences which make keyboards that are too smart fail to work.  


**Background/OT:**
I'd intended to use a USB-2-PS2 (mouse/keyboard) connector.  I've been using some of those for over a decade, but none of them worked with the Logitech keyboard either. A new KVM was required just because my old keyboard died.

Before switching to the new KVM switch, I had a VGA+PS2 KVM switch that I'd used about 20 yrs.  It worked perfect with every computer I connected.  Alas, USB keyboards seem to be the only answer these days, hence why I got a new KVM switch. While I was at it, I upgraded to a 4K HDMI display connection, since most of my computers don't have VGA ports anymore either.

I hate USB keyboards and mice.  They have screwed my KVM switch experience completely, in a bad way.

Of course, I contacted Logitech about it.  "We don't support any KVM switches."  Getting them to say that took far too long.  They kept saying "for the best experience, directly connect the keyboard to the computer."  Which was useless for my needs.

I miss my IBM keyboard, though it was noisy. It was from 1995, so I definitely got my $0.50 of use from it.  Bought 3 of them for $0.50/each back then.

---

### Post by #&amp;thj^% on 2023-07-25
> **clepsdyrae said:**
> 
Any idea what is going on?
Cables matter for sure proven over and over, but what shows with this:
```
cat /etc/default/keyboard
```

---

### Post by clepsdyrae on 2023-07-25
Thanks, all.

> **1fallen said:**
> Cables matter for sure proven over and over, but what shows with this:
```
cat /etc/default/keyboard
```

```

# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

BACKSPACE="guess" 
```

So is the basic theory that the cable is mediocre, and in combination with some characteristic of the USB ports on the front of the case, this causes the issue? (Asking because the extension cable does work with this keyboard (see above) just not in the port I want it to work in.) I get that compounding errors can be a thing, so maybe that's what's happening... just wish I could know what the specific problem was so I could attempt to work around it. The extension cable also works with the keyboard when it is plugged into the back of the computer enclosure. I know that in general the USB docks on the fronts of cases are, to put it charitably, "special" in some ways, so maybe that's all it is.

Thanks anyway for the brainstorming!

---

### Post by TheFu on 2023-07-26
Cable distance matters for all electrical connections. USB ports aren't all the same. Some are data-only. Some are data+charging.  There is a wide range of USB cables in the world. Some are charge-only. It is hard to tell the difference looking at the cable.  I have a 6ft USB3 extension cable that is plugged into the front of one of my computers.  It reaches to a convenient place on the desk.  Using it rather than the front panel USB ports moves the plug wear from the computer to the cable.  It was a conscious choice for me.

Some keyboards want USB2 ports, not USB3.  I've run into that a few times.  Being backwards compatible isn't always 100%.

Also, not all USB devices work when going through a USB hub.  Inside may computers, they have USB hubs to share more USB ports.  The USB standard allows up to 128 ports, BTW.  I have a few devices that won't work going through a hub.  I know that my ubuntu ISO flash drives will not boot if there is any hub involved, for example.

You might be able to connect the front USB ports to a different internal USB header on the motherboard.

Is all of this really about a 2ft eBay special?

---

### Post by #&amp;thj^% on 2023-07-26
> **clepsdyrae said:**
> Thanks, all.



```

# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

BACKSPACE="guess" 
```

So is the basic theory that the cable is mediocre, and in combination with some characteristic of the USB ports on the front of the case, this causes the issue? (Asking because the extension cable does work with this keyboard (see above) just not in the port I want it to work in.) I get that compounding errors can be a thing, so maybe that's what's happening... just wish I could know what the specific problem was so I could attempt to work around it. The extension cable also works with the keyboard when it is plugged into the back of the computer enclosure. I know that in general the USB docks on the fronts of cases are, to put it charitably, "special" in some ways, so maybe that's all it is.

Thanks anyway for the brainstorming!

Thanks for your reply you may want to try this along with all the other suggestions here:
```

XKBMODEL="macintosh"
XKBLAYOUT="us"
XKBVARIANT="de_mac"
XKBOPTIONS="lv3:alt_switch"

BACKSPACE="guess"
```
But back your config first:
```
sudo mv /etc/default/keyboard /etc/default/keyboard.bk
```
And edit with 
```
sudo nano /etc/default/keyboard
```
Add the above i show and logout after the change.
You will still have a backup on your system, and here in your post.
Good Luck

---

### Post by clepsdyrae on 2023-07-26
Thanks! -- re: those configs you suggest, does that have anything to do with the USB connectivity?

In terms of overall keyboard config, I'm pretty happy with what I have now; I'm doing this:

in /etc/modprobe.d/hid_apple.conf:

```
options hid_apple fnmode=2
options hid_apple swap_opt_cmd=1
```

in a startup script run after KDE login:

```
 setxkbmap -option "apple:alupckeys"
```

---

### Post by #&amp;thj^% on 2023-07-26
> **clepsdyrae said:**
> Thanks! -- re: those configs you suggest, does that have anything to do with the USB connectivity?
yes, i used that for about an hour on a clients hardware not mine, so use is very short but the results were good.
He had a bad USB cord in this use.
> **clepsdyrae said:**
> 
In terms of overall keyboard config, I'm pretty happy with what I have now; I'm doing this:

in /etc/modprobe.d/hid_apple.conf:

```
options hid_apple fnmode=2
options hid_apple swap_opt_cmd=1
```

in a startup script run after KDE login:

```
 setxkbmap -option "apple:alupckeys"
```
That should be fine as well, so we have narrowed it down to hardware now. (ports and cables)

---

### Post by clepsdyrae on 2023-07-27
> **1fallen said:**
> yes, i used that for about an hour on a clients hardware not mine, so use is very short but the results were good.

It worked! Those configs let me plug into the front of the desktop. Amazing. Thanks!

---

### Post by #&amp;thj^% on 2023-07-27
I just knew you would at least give it a whirl. :)
Good job on verifying it still works though...very helpful

---

### Post by clepsdyrae on 2023-07-27
Oof, except another problem -- the grub screen doesn't see the keyboard (I dual boot).

Oddly, it does work via the keyboard -> extension cable -> monitor USB port -- the bios boot screen works with the keyboard in that case. But if I plug keyboard -> extension cable -> desktop, or front of desktop, it does not work until the OS is booted...

If you have any magic tricks for that I'd love to hear them (perhaps grub or bios configs?)

---

### Post by #&amp;thj^% on 2023-07-27
> **clepsdyrae said:**
> Oof, except another problem -- the grub screen doesn't see the keyboard (I dual boot).

Oddly, it does work via the keyboard -> extension cable -> monitor USB port -- the bios boot screen works with the keyboard in that case. But if I plug keyboard -> extension cable -> desktop, or front of desktop, it does not work until the OS is booted...

If you have any magic tricks for that I'd love to hear them (perhaps grub or bios configs?)

I don't recall that being an issue back then....huuum I'll have to think hard on that one.
I'll report back if anything comes rushing back to me.
But i would for sure explore options in your Bios, wouldn't hurt.

---

