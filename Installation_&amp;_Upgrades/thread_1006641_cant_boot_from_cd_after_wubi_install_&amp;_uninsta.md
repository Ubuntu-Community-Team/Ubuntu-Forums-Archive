---
title: "cant boot from cd after wubi install &amp; uninstall"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by nood1e on 2008-12-09
ok, i installed ubuntu via wubi and decided that i wanted to do a full ubuntu install on a spare HDD of mine, but now my system wont boot from the DVDrom, when it was having no problem doing this prior to the wubi install/uninstall. 

a few notes:
trying to install ubuntu 8.10 or 8.04 (tried both)
burning iso and trying to boot from that
i have amd 64 x2 processor
3 gigs ram
320gb hdd
cd/dvd drive IS recognized through bios, even tried to tell pc to boot from that drive. it does try it seems, but it just continues on to xp if i have my xp hdd connected, and with my blank hdd connected it just says "error loading os" as if it were a blank or useless cd or something.

i really really want ubuntu on my spare hdd, im currently loving it on my laptop, which installed no problem! 

when i install the via wubi i can boot into all that stuff, just cant boot to the cd anymore. any help would be greatly appreciated.

---

### Post by ANew on 2008-12-09
> **nood1e said:**
> ok, i installed ubuntu via wubi and decided that i wanted to do a full ubuntu install on a spare HDD of mine, but now my system wont boot from the DVDrom, when it was having no problem doing this prior to the wubi install/uninstall. 

a few notes:
trying to install ubuntu 8.10 or 8.04 (tried both)
burning iso and trying to boot from that
i have amd 64 x2 processor
3 gigs ram
320gb hdd
cd/dvd drive IS recognized through bios, even tried to tell pc to boot from that drive. it does try it seems, but it just continues on to xp if i have my xp hdd connected, and with my blank hdd connected it just says "error loading os" as if it were a blank or useless cd or something.

i really really want ubuntu on my spare hdd, im currently loving it on my laptop, which installed no problem! 

when i install the via wubi i can boot into all that stuff, just cant boot to the cd anymore. any help would be greatly appreciated.

I think i have similar problem, i can not install full version,
in addition installation via wubi does not work either

---

### Post by nood1e on 2008-12-09
ok, i have figured this out i think. through the gui that comes up from the cd in XP it allows you to get help booting from the CD. that problem is solved. and if i had problems booting to it later i just had to restart my computer and open the CD tray right after start up and close it again very quickly. that would make the CD drive start reading the disk. that got me by. 

now, after i try to install i had more problems. couldnt get the installer to load. ubuntu would start its loading deal, then right at the end of it my screen would start tweaking out then freeze. then later i set the paramaters with "F6" to choose acpi=off. this would allow the installer to load completely but my USB mouse wouldnt work, but my PS2 one did. so i installed ubuntu completely successfully. restarted to boot into the OS and had the ubuntu OS loadup screen get to the very end of the load bar and the computer would restart.

so, i reboot, press ESC for more boot options, goto the KERNAL command line and add acpi=off. now my computer will boot into ubuntu perfectly fine, BUT now i get an error saying "HAL failed to initialize" and neither my USB or my PS2 mouse will work. 

so, thats what ive been doing since 7am-8:30pm. researching and messing around with all that. and now im going to sleep. but thats my story today. hope this helps someone out with their troubles, and hopfully someone else reads this and has a solution. i would be most greatful! 

again, i have:
HP pavillion a1610a
added a 400watt psu
amd 64 x2 2.5ghz
3 gig ram (2 1gig sticks and 2 512 sticks)
lightscribe DVD multi drive
multicard reader
asus motherboard i think
and i installed ubuntu into a completely blank HDD. did not use the wubi or install it on a partion on a drive sharing an XP install or anything of the like. completely fresh install on a 320gig HDD, using the whole disk.

---

### Post by nood1e on 2008-12-10
bump. :confused:

---

### Post by nood1e on 2008-12-12
bumpity bump?!

:?

please!

---

