---
title: "hibernate won't work - blank screen lockup"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by blackdalek on 2006-11-19
If I select hibernate from the ubuntu gnome desktop gui thingy, the computer powers off, but when it restarts it displays a full screen of vertical brown/black stripes followed immediately a blank black screen with a frozen underscore cursor in top left corner. This is how it remains for eternity or untill I press the reset button, then the computer boots up normally but all previously open apps are not restored. What is the problem and how do I fix it?

---

### Post by blackdalek on 2006-11-19
Forgot to add, running Dapper Drake 6.06 LTS.

---

### Post by koki on 2006-11-19
Try 6.10; hibernate did not run on my laptop with Dapper, but it is now happily working since I installed Edgy. You may have the same luck. ;-)

---

### Post by frogotronic on 2006-11-19
> **blackdalek said:**
> If I select hibernate from the ubuntu gnome desktop gui thingy, the computer powers off, but when it restarts it displays a full screen of vertical brown/black stripes followed immediately a blank black screen with a frozen underscore cursor in top left corner. This is how it remains for eternity or untill I press the reset button, then the computer boots up normally but all previously open apps are not restored. What is the problem and how do I fix it?

Hi,

Some basic parameters might help trace the problem:

1) What machine are you using?

2) Do you have "HAL" installed?

3) Can you post your "/etc/hibernate/hibernate.conf" file and your "/etc/hibernate/blacklisted-modules" file?

4) Does "SUSPEND" (suspend-to-RAM) work?

- CH

---

### Post by blackdalek on 2006-11-19
> **cement_head said:**
> Hi,

Some basic parameters might help trace the problem:

1) What machine are you using?

2) Do you have "HAL" installed?

3) Can you post your "/etc/hibernate/hibernate.conf" file and your "/etc/hibernate/blacklisted-modules" file?

4) Does "SUSPEND" (suspend-to-RAM) work?

- CH

1. An old server. Motherboard is Intel L440GX+ as shown here [http://www.intel.com/support/motherboards/server/l440gx/](http://www.intel.com/support/motherboards/server/l440gx/) PDFs of the hardware features of board on that page.
Using an Nvidia GeForce4 MX 4000 PCI video card.
Creative Soundblaster PCI64 sound card.
An Ralink RT2500 chip wireless card.
A VIA chipset IEEE 1394 firewire card.
18Gb Seagate scsi hard disk, two 850Mhz Pentium III CPUs and 512Mb ram.
Running an smp kernel.

2. Wouldn't have a clue. But there is a /etc/hal/ directory present.

3. The directory /etc/hibernate/ does not exist. A search for hibernate.conf finds no files.

4. "Suspend" is not an option available on the menu.

---

### Post by blackdalek on 2006-11-21
so... anyone able to glean anything from the information I gave which might help to trace the problem?

---

### Post by frogotronic on 2006-11-23
> **blackdalek said:**
> 1. An old server. Motherboard is Intel L440GX+ as shown here [http://www.intel.com/support/motherboards/server/l440gx/](http://www.intel.com/support/motherboards/server/l440gx/) PDFs of the hardware features of board on that page.
Using an Nvidia GeForce4 MX 4000 PCI video card.
Creative Soundblaster PCI64 sound card.
An Ralink RT2500 chip wireless card.
A VIA chipset IEEE 1394 firewire card.
18Gb Seagate scsi hard disk, two 850Mhz Pentium III CPUs and 512Mb ram.
Running an smp kernel.

2. Wouldn't have a clue. But there is a /etc/hal/ directory present.

3. The directory /etc/hibernate/ does not exist. A search for hibernate.conf finds no files.

4. "Suspend" is not an option available on the menu.

a) You can check (searchP for HAL from synaptic, install it if it isn't there.

 It sounds as if you can hibernate, but te X server isn't being restarted.

Try installing VBE

---

### Post by cantormath on 2006-11-23
> **blackdalek said:**
> If I select hibernate from the ubuntu gnome desktop gui thingy, the computer powers off, but when it restarts it displays a full screen of vertical brown/black stripes followed immediately a blank black screen with a frozen underscore cursor in top left corner. This is how it remains for eternity or untill I press the reset button, then the computer boots up normally but all previously open apps are not restored. What is the problem and how do I fix it?

that is usually a intel problem, what hardware are you using.  I had the same problem for a long time, but now it works with dapper.

---

### Post by blackdalek on 2006-11-24
> **cement_head said:**
> a) You can check (searchP for HAL from synaptic, install it if it isn't there.

 It sounds as if you can hibernate, but te X server isn't being restarted.

Try installing VBE

HAL and VBE are both already installed.
Another thing I've just noticed is that the caps lock and scroll lock LEDs are flashing on the keyboard while the computer is frozen at the blank screen. Does this suggest anything?

---

### Post by tanari on 2006-11-24
I have the same problem :(.

---

### Post by nmincone on 2006-12-21
Everyone with suspend/hibernation problems, please STF before asking your questions, chances are it has already been addressed.

[Search this thread for clues...]("http://ubuntuforums.org/showthread.php?t=284994")
[Laptop testing team wiki...]("https://wiki.ubuntu.com/LaptopTestingTeam/")
This is a real problem that needs real solutions. Supporting hardware for suspend/hibernation is tricky business and could use some polishing in Linux. There's no magic bullet (at the moment).

---

