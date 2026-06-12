---
title: "USB devices acting strange"
date: 2013-05-31
forum: Hardware
---

### Post by rafe101 on 2013-05-31
I just built a new media center (running mythtv). It has an MSI Z77A-G45 board. And some of the USB devices (either plugged directly into the back ports or front panel) are acting really strange. The remote is the worst. I have to hold down a button for up to 5 seconds before the computer registers a press and when it does it sees a burst of individual presses. This makes the remote practically unusable. I have played with LIRC and nothing makes this better. In fact, it was acting like this with kernel support--before I had LIRC set up. The really strange thing is that my wireless keyboard also acts strangely. It has no range. On the old machine (and the desktop) I can stand across the room and use it just fine, but with this new machine I have to be right up next to the USB dongle (RF, bundled with keyboard) and sometimes it just refuses to register input, especially that from the trackball.

On top of this, it is only these wireless devices that are giving me trouble. If I haul out wired keyboards and mice, they work just fine (as do thumbdrives). Nothing in the living room has changed that would be introducing interference that wasn't there before (plus, we're talking about both IR and RF giving me problems) and I've already done a second fresh install after I identified the problem and before I got too far into setting up mythtv.

I am completely dumbfounded and would really appreciate any suggestions about where I can start to track this problem down.

---

### Post by Autodave on 2013-05-31
I am thinking that it has nothing to do with Linux, but rather a bad USB device.  I would try unplugging EVERY USB device and hook-up a wired keyboard and mouse and start there.  Plug in one device at a time and check operation of everything.  Big slowdown = bad device.  If nothing found that way, again unplug everything and just hook up either wirelss mouse or keyboard: one of them could be the culprit.

---

### Post by mörgæs on 2013-05-31
Which release of Buntu are you using?

---

### Post by Autodave on 2013-05-31
Thinking more on your problem, I also remember having a machine with a borderline power supply: it was fine with one external HD hooked-up, but as soon as a second one was attached, it would run like an ole 8088 machine.  Replaced power supply and all was good again.

---

### Post by rafe101 on 2013-05-31
I was really hoping this wouldn't be a hardware problem. If it is, do you have any idea why the standard devices don't exhibit any strange behavior? The speed reading and writing are just fine to usb drives. I mean--if it's hardware it must be the board or the front panel hardware (silverstone media case) and then I have to figure out which one and try and replace it... Without the keyboard and mouse the only usb are what goes to the front panel and IR receiver. So that would mean replacing really specific stuff (Silverstone). I bought this case used, so it's all on me.

Is there anything I can do to track this down? I don't even know where to start. I don't even know what the problem is.

Mörgaes, Mythbuntu--so XFCE.

---

### Post by rafe101 on 2013-05-31
Autodave, are you saying you were on the cusp of sufficient power or the PSU was done? I think I should be fine for power, but, of course, I can never rule out bad components.

---

### Post by Autodave on 2013-05-31
I am talikng about the power supply.  Was it new or used?  How many watts rating?  How many USB devices are you using at once and what are they?

---

### Post by Autodave on 2013-06-01
Yes......the machine did not have a sufficient power supply to run 2 external HDs.  Upgrading the power supply fixed everything.

---

### Post by mörgæs on 2013-06-01
> **rafe101 said:**
> 
Mörgaes, Mythbuntu--so XFCE.

I meant the release number.

---

### Post by rafe101 on 2013-06-01
Mythbuntu 12.04

The PSU is 350 watts--small, but should be enough. Normally, I have just the front panel (card reader and USB ports) and the VFD display/ir receiver hooked up.

---

### Post by mörgæs on 2013-06-01
Since you have brand-new hardware I would suggest the newest software, that is 13.04. Not a guarantee that it will solve the problem, just general advice.

---

### Post by Autodave on 2013-06-01
PS new or used?

---

### Post by rafe101 on 2013-06-03
Autodave, used--slightly--a few months. You do have me thinking about the PSU. I wish I had a spare one around to try, rather than having to buy a spare one. Any tricks top test for problems with one?

Mörgæs, I used to keep both of my machines updated, but I got tired of working on stuff (video driver problems, update errors...) So I regressed to the LTS on the htpc and determined to stay there.

One thing I've noticed about the behavior that might help-- the remote seems to work pretty well immediately after startup. And-- now it may just be me getting used to this, but--I think it is getting better in general. We're down to 1 to 3 seconds to register activity. It does occasionally record false keys, however.

---

