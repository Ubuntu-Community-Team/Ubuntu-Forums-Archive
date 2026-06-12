---
title: "USB hub overloads port"
date: 2012-11-09
forum: Hardware
---

### Post by olligobber on 2012-11-09
I know this isn't strictly ubuntu related, but this is the best computer forum I know of.

I fairly recently got a laptop which I set up to dual boot Windows 7 and Ubuntu 12.10. As the laptop has only 3 usb ports, and I wanted up to 6 things plugged in at once (or more than 3 atleast), I purchased a $6 4 port usb hub. 

When on Windows to play some games that aren't on ubuntu (yet) my mouse froze up, my keyboard stopped working and my headphones also stopped. Using the built in keyboard and touchpad I booted to ubuntu. When the issue remained I blamed my kvm switch, but then realised the headphones working.

I have done some research into the issue (with my built in keyboard and touchpad) to find the hub is overloading the usb port, and a powered hub will permanently resolve the issue. However, until I can go and get a new hub I want a quick fix. I thought unplugging some things from the hub would do this, or unplugging the hub for a bit, with no success.

Any suggestions appreciated.

---

### Post by cwsnyder on 2012-11-09
If you really are overloading the USB port, you need to plug in your laptop and remove ALL devices which are not USB 1.1 compatible (that are powered from the port, like your headphones).  You can have them plugged in on the ports on the laptop, but not on the hub.  Only things like a wired USB mouse or wired USB keyboard can then be plugged into the hub.

And you thought you could get by with a non-powered hub.  Passive hubs are only good for USB 1.1, which is also something like 1/5th the speed of powered USB 2.0 hubs, also.

---

### Post by olligobber on 2012-11-09
> **cwsnyder said:**
> If you really are overloading the USB port, you need to plug in your laptop and remove ALL devices which are not USB 1.1 compatible (that are powered from the port, like your headphones).  You can have them plugged in on the ports on the laptop, but not on the hub.  Only things like a wired USB mouse or wired USB keyboard can then be plugged into the hub.

And you thought you could get by with a non-powered hub.  Passive hubs are only good for USB 1.1, which is also something like 1/5th the speed of powered USB 2.0 hubs, also.

Of my six devices, only one has an external power cable. I have a KVM which receives power, I assume from one of its two usb plugs (two per computer), headphones, printer (with external power source), game controller and external hard drive. I can't fit all these into my laptop's usb ports, so is the only solution a powered hub?

Also, how can I be sure when purchasing a hub that it is powered? A search reveals hubs that do not state they are powered. Is there a certain price range that would be suspicious?

Thankyou for your help so far.

---

### Post by cwsnyder on 2012-11-09
Look for one in which the packaging includes a wall wart and states that it is certified for USB 2.0 or USB 3.0.  USB 2.0 should be able to supply up to 500 mA of power at 5V, according to the standard.  I refer you to the Wikipedia article: [http://en.wikipedia.org/wiki/USB_hub](http://en.wikipedia.org/wiki/USB_hub)

---

### Post by olligobber on 2012-11-09
> **cwsnyder said:**
> Look for one in which the packaging includes a wall wart and states that it is certified for USB 2.0 or USB 3.0.  USB 2.0 should be able to supply up to 500 mA of power at 5V, according to the standard.  I refer you to the Wikipedia article: [http://en.wikipedia.org/wiki/USB_hub](http://en.wikipedia.org/wiki/USB_hub)

Thankyou. The article explained it all.

Just mentioning my hub started working just then. It lasted 2 days last time, let's see how long it lasts today.

---

### Post by olligobber on 2012-11-09
A few more questions related to this issue:

1. Which of my devices is more likely to be using more than 1 unit of power? I have a KVM on two usb ports, headphones, printer with AC power, External HDD and usb game controller.

2. What kind of price am I looking at for a powered usb hub?

3. Can I have my powered hub chained from the unpowered hub?

Thankyou!!!

---

### Post by cwsnyder on 2012-11-09
My best guesstimate is your headphones and external HDD probably pull almost as much as your KVM, but the KVM definitely will pull the most or it wouldn't have two connectors.

A powered hub, according to what I have seen in Wally World and on-line should run between $11 to $20 for a 4 port USB 2.0 powered hub.

Remember that a USB 1.1 (so-called full speed) hub, unpowered is only rated for up to 12 MB/sec, while a USB 2.0 (high speed) hub, powered, is rated for up to 480 MB/sec.  If you put a slower hub between your computer and your peripherals, especially for your game controller and external HDD, you will definitely notice the difference.

---

### Post by olligobber on 2012-11-09
> **cwsnyder said:**
> My best guesstimate is your headphones and external HDD probably pull almost as much as your KVM, but the KVM definitely will pull the most or it wouldn't have two connectors.

A powered hub, according to what I have seen in Wally World and on-line should run between $11 to $20 for a 4 port USB 2.0 powered hub.

Remember that a USB 1.1 (so-called full speed) hub, unpowered is only rated for up to 12 MB/sec, while a USB 2.0 (high speed) hub, powered, is rated for up to 480 MB/sec.  If you put a slower hub between your computer and your peripherals, especially for your game controller and external HDD, you will definitely notice the difference.

The hub says "USB 2.0" and "Up to 480mbps" on it. Is that believable?

Also, I believe my laptop has only USB 2 sockets, and am pretty sure all my devices are usb 2 (I know the hdd is usb2). Is there a way of checking whether the sockets are usb 2 on ubuntu?

---

### Post by cwsnyder on 2012-11-09
Yes, it is believable, as the Wikipedia articles state, some hubs are buss powered, which is fine if you are not trying to power devices from the hub.

You will not need USB 2.0 on your printer unless you have a 4 ppm or faster printer.  It depends on the type of game controller and type of game whether you need USB 2.0.

Any KVM in use with a laptop needs the power of USB 2.0, and needs to be plugged in, if not the speed, to keep from draining the internal battery relatively quickly.  The same is true of a USB external hard drive if it is used more than occasionally.

I personally would not use a USB headphone or USB speakers on a laptop operating off battery.  I would rather suggest headphones which plug in to the headphone jack.

---

### Post by olligobber on 2012-11-09
I will only be using the hub when the laptop is on AC power.

Thankyou for everything, marking as solved.

---

