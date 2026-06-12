---
title: "HP Pavilion 5000 series  - Dapper work??"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by mutenewt on 2006-08-26
Anyone try intalling/running Dapper on a HP Pavilion 5000 series notebook?  If so, I'd be interested in hearing what worked and what didn't.  I searched the boards but did not find any previous discussions.  

I was able to pick up a 5224nr (AMD Turion 64 model) fairly cheaply and would love to install Ubuntu but figured I better do some research first.

Thx for the help!

---

### Post by DuncanNZ on 2006-08-26
Start here: [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

You'll find 4 HP 5000 series laptops. Maybe you'll be good enough to add yours to the testing database?

---

### Post by mutenewt on 2006-08-27
Thx Duncan!

---

### Post by Richard Kut on 2006-08-27
Yes, it absolutely does work! I have been running Ubuntu on my HP zv5450CA (zv5000 series Canadian edition) since April 2005 using Hoary (5.04), Breezy (5.10), and now Dapper (6.06).

Almost everything worked from the start, except that wireless needed to use the ndiswrapper software for the Broadcom 4306 wireless card. Also, the Texas Instruments flash card reader does not work, but that is a minor annoyance. Otherwise, the experience has been wonderful, from installation thru configuration, and daily use is a joy. I find it much faster than Windows XP Pro ever was, even after a great deal of tweaking.

One note: my experiences are based on an upgrade from Hoary to Breezy to Dapper. I have not tried to do a fresh install of Dapper yet.

Hope my review helped. Ciao.

---

### Post by MadKAT on 2006-08-28
Hi,

I have a Pavillion zx5000 (P4 3.2GHz; 1G ram), and it gets stuck on "Loading Linux Kernel" (37%) when booting the CD.

As many have suggested I tried "live acpi=off noapic nolapic" at the boot prompt, but it still gets stuck at "Loading /casper/vmlinuz......."

Any ideas?

PS: Other distro I tried on this machine is Mandriva 2006 works, which is what is currently installed. 

Thanks in advance.

---

### Post by MadKAT on 2006-09-02
Nothing??? sheesh... ](*,) 

Anyway, since this has been too long, I tried a couple of other Live distros:

Suse 10.1 --- works
Freespire --- wouldn't even start

So if Suse and Mandriva works and Ubuntu and Freespire doesn't even load the kernel I'm thinking the problem might be upstream to the Debian. Just a wild guess, i know nothing about how all these works...

Damn, and I was so excited to put Ubuntu on this machine...  
Oh well, I guess I might just have to go with openSuse.

---

### Post by firstc624 on 2006-09-02
i am running a pavillion dv5040us and i have wireless working w/ the existing supplied driver,,  i did have to install network manager though to get it running and tweak a little.

my card reader i am not sure if it is working or not.  

the touchpad works but it can go kinda crazy when it is working on something and you try to do something else.

other than that, it works well.

---

