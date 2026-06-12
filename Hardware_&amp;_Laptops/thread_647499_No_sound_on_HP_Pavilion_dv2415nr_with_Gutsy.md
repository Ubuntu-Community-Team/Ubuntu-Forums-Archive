---
title: "No sound on HP Pavilion dv2415nr with Gutsy"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by bbbaldie on 2007-12-22
Volunteered to install Gutsy on a widowed neighbor's Pavilion laptop. She's cool, agrees that Vista sucks.

Everything worked perfectly (even wireless!) with restricted drivers enabled.

However, no sound! No sound through earphones or speakers. All looks well from the system's point of view, but totally silent.

No way to enable/disable sound in bios.

This is my last hurdle to giving her a secure, controllable computer. Any ideas?

---

### Post by LuisC-SM on 2007-12-22
Hi.

Some pavillions have BIOS problems like most of toshibas.

My first guess will be starting gutsy with **[COLOR="DarkRed"]acpi_osi=!Linux[/COLOR]** at boot time, if this brings sound, then most probabily is that you must deal with a custom DSDT.

And by the way, check thiis BUG to see if applying a higher kernel works for you
Check this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)
and search for Henrik Nilsen, almost at the end, he is giving the solution to install this new kernel.

Cheers

Luis

EDIT: If acpi_osi works, let me know, I could give you the solution to recompile a new DSDT... if aplying the new kernel works, then everything is ok

---

### Post by bbbaldie on 2007-12-23
Thanks for the reply, Luis.

The boot line had no effect. Also, the kernel upgrade wasn't found by apt-get, but it sounds like the restricted drivers wouldn't have worked with it anyway.

The thread sounded encouraging about the Hardy kernel making sound work. I'm going to see if she can live with no sound for four months or so until Hardy comes out.

---

### Post by buzzmandt on 2007-12-23
unplug your laptop and then turn it on, see if you have sound

seems odd but that's how my pavilion worked, it only had sound if  i started it up unplugged.....

---

### Post by bbbaldie on 2007-12-23
UN-BE-STINKING-LIEVABLE!

That was the problem, buzzmandt.

THANKS!!!!!

---

### Post by buzzmandt on 2007-12-23
I fixed it by changing a bios setting to do with apci....don't remember what it was but do a google search on pavilion no sound apci and you should find what you need.....i've had a perfect useable laptop ever since....

---

### Post by buzzmandt on 2007-12-23
found one of my other posts here:

>  Originally Posted by buzzmandt  View Post
test this sound problem.....
turn your laptop off, unplug it, turn it on, log in and see if you have sound....

bet you do,

I fixed this with adding the option apci=off to the boot line.

I have a perfectly running hp dv2000


thought i did it in bios, but may be just a boot line option, can't remember

---

### Post by LuisC-SM on 2007-12-23
> **buzzmandt said:**
> unplug your laptop and then turn it on, see if you have sound

seems odd but that's how my pavilion worked, it only had sound if  i started it up unplugged.....

Yes, that's right :).... as a matter of fact, sometimes taking the battery out and waiting for a few seconds seems to fix some issues on certain HP & Compaq models.

Glad to hear this solution

Cheers

Luis

[COLOR="DarkRed"]PS. Booting with ACPI=off makes your laptop loose some thermal features as well as suspend/hibernate funcitions. If this fix works (acpi=off) then the best solution is to work with a custom DSDT (there a several threads talking about this)[/COLOR]

---

