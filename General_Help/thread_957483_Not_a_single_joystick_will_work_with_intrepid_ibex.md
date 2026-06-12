---
title: "Not a single joystick will work with intrepid ibex, just so you know."
date: 2008-10-24
forum: General Help
---

### Post by eragon100 on 2008-10-24
Due to a change in the xserver, not a single joystick will work with the new ubuntu, at least not on 64-bit. What's more, as long as it's plugged in, the cursor will jump over the screen like an idiot. There are also no plans to fix this before final, because it's not considered a "critical issue". Yeah, right. You will have to wait for an update :mad:

Proof:

[http://ubuntuforums.org/showthread.php?t=953662](http://ubuntuforums.org/showthread.php?t=953662)

You can convince the developers this is a critical bug by leaving comments in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951)

---

### Post by DrMega on 2008-10-24
Wow. That's a bit of a step backwards. I liked the idea that in Ubuntu you don't have to mess about with special drivers or config for joysticks and joypads.

EDIT: I've just read the instructions for reporting it. I'm sure all novices with no interest in the technical side will all do that and get it exactly right (or not).

---

### Post by eragon100 on 2008-10-24
Okay, I have put this forum thread on the phoronix forums, as well, and I have digged it: [http://digg.com/linux_unix/Not_a_single_joystick_will_work_with_ubuntu_intrepid_ibex](http://digg.com/linux_unix/Not_a_single_joystick_will_work_with_ubuntu_intrepid_ibex)

---

### Post by Northsider on 2008-10-24
> because it's not considered a "critical issue"
Lame lame lame LAME.  Regardless if they *want*to expand to new users, how will they expect to gain new users (and keep current ones for that matter) if something as "simple" as plugging in a joystick doesn't work?!

---

### Post by hessiess on 2008-10-24
> **northsider said:**
> lame lame lame lame.  Regardless if they *want*to expand to new users, how will they expect to gain new users (and keep current ones for that matter) if something as "simple" as plugging in a joystick doesn't work?!

+1

---

### Post by bobbocanfly on 2008-10-24
> **eragon100 said:**
> 
You can convince the developers this is a critical bug by leaving comments in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951)

Please **DO NOT** spam a bug with comments like "oh noes, this is bad, hurry up and fix it". That is just going to get in the way of developers talking to each other about how to actually fix it. If i read a bug report where all the comments were like that, I would ignore it and find another bug to fix (and I know lots of other devs do the same). 

Anyway, read the second comment from Timo Aaltonen: "This will be fixed before the release.". It is set to High priority, which is fairly rare.

---

### Post by eragon100 on 2008-10-24
> **bobbocanfly said:**
> Please **DO NOT** spam a bug with comments like "oh noes, this is bad, hurry up and fix it". That is just going to get in the way of developers talking to each other about how to actually fix it. If i read a bug report where all the comments were like that, I would ignore it and find another bug to fix (and I know lots of other devs do the same). 

Anyway, read the second comment from Timo Aaltonen: "This will be fixed before the release.". It is set to High priority, which is fairly rare.

That's good news! But why is the milestone said to "intrepid-updates", then?

---

### Post by Polygon on 2008-10-24
i also read that in a future ubuntu version it will be made so you dont have to provide seperate config files for every joystick.

and honestly a lot more things are more important then that....like what good is your joysick if ubuntu doesn't even start? or if x doesn't start? kernel panics?

---

### Post by bobbocanfly on 2008-10-24
> **eragon100 said:**
> That's good news! But why is the milestone said to "intrepid-updates", then?

From the bug report:

[QUOTE=Bryce Harrington (Ubuntu Developer)]Since accepting this package before RC would require respinning all images to get them up-to-date, and I don't think this is critical enough to justify accepting it between RC and final (in particular, game support is not all that relevant to liveCDs), I think we should handle this as an SRU post-release. I've rejected the package from the unapproved queue for now.[/QUOTE]

Basically, it would cause too much disruption to fix it now. It will more than likely be amongst the first few updates released after Intrepid is and will probably be a top priority in the Stable Release Update (SRU) queue. It was almost definately be in the point release (normally a month or two after the actual release, so before Christmas) as it is such a High priority in the updates milestone.

---

### Post by eragon100 on 2008-10-24
That's nice, altough I think we can lose a lot of users trying out ubuntu because of this. If the cursor, and hence the desktop is unusable because a joystick is plugged into the pc, which is something a lot of people have, the last thing someone who is new to ubuntu and doesn't know anything about it will think of is unplugging the joystick to get the mouse to work. It's not something people will easily figure out :(

---

### Post by Lakergirl5 on 2008-10-24
I love arcade type joystix

---

### Post by crhylove on 2008-10-25
I can confirm this, however, The joystick DOES work in virtualbox via the USB pass through.  So I got my Zsnes on in a VM any way!  But yeah..... this should seriously be fixed before release..... I was of the opinion that Ubuntu was trying to be a serious contender with OS X and Windows....  But no working joystick is a pretty glaring error for anybody with a resident 5 year old!

Of course I wouldn't complain at all if virtualbox had working 3d support (like vmware already does!)..... :)

---

### Post by sat_e_llite on 2008-11-02
Oh this explains the jumping cursor when I first booting up in Ibex.

---

### Post by BigSilly on 2008-11-02
I was really worried about this, but luckily my joypads work just as they did in Hardy. I have a couple of Speedlink (GreenAsia) Strike 2 pads that are very similar to PS2 pads, and thankfully they work fine with all my emulators and games.

---

### Post by Vince4Amy on 2008-11-02
My Thrustmaster 360 Modena Upad works fine on Intrepid x64.

---

### Post by crhylove on 2008-11-02
How does anyone get any joystick to work?  My joystick(s) just move the cursor around the screen pointlessly.  I have not seen a single stick work on my box....

---

### Post by K.Mandla on 2008-11-02
Since Ibex is out now and this is turning into a joystick support thread, I moved it to General Help.

---

### Post by unebaguettesvp on 2008-11-03
> **crhylove said:**
> How does anyone get any joystick to work?  My joystick(s) just move the cursor around the screen pointlessly.  I have not seen a single stick work on my box....

Same here. I have two Logitech Cordless RumblePad 2 joysticks and another wired controller and neither of them work.

Follow these bug reports:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/284951")
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/274203]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/274203")

There are two tricks listed there. One is to manually configure your joysticks in your xorg.conf file. The other is to try the patch in intrepid-proposed for xserver-xorg-input-evdev. It seems like people are having success with one or the other. I'm not having any luck whatsoever. Try it out. Maybe it will work for you.

---

