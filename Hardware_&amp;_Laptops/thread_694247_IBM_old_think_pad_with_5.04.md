---
title: "IBM old think pad with 5.04"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by jwxie on 2008-02-11
hey guys, I have a few questions want to ask

I am using IBM's old think pad, the i-Series
Celeon CPU, and with 64MB

1. How do i check my pc preference ? You know how window xp, press ctrl+delete+alt, you can see how much memory ram have been use... I want to see that on 5.04, anyone knows how? And CPU as well.

2. I think 64mb is still a bit too low for 5.04, any suggestion to reduce anything?

---

### Post by kerry_s on 2008-02-11
ubuntu is not made for those specs.

i recommend DSL-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

if you really want to stick with ubuntu, go custom-> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

debian is better for the old stuff, a custom install is the best thing.
[http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r2/i386/iso-cd/debian-40r2-i386-businesscard.iso)

base install, so when it comes to the package selection uncheck everything.
log in as root
apt-get install xorg (a wm) (what ever else)
reboot(ctrl+alt+delete)
log in as your user
startx
keep on building

those are simplified instructions, it's almost exactly like the ubuntu custom install.

example, when i do mine, i use->
apt-get install xorg synaptic rox-filer leafpad jwm
reboot

to start my build up, once in the gui i do a little bit of setting up than continue adding what ever else i want.

---

### Post by jwxie on 2008-02-11
thank you
i will try it ^^

---

