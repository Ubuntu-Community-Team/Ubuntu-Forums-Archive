---
title: "Ubuntu does not start properly on HP compaq NX9010"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by ymtoh on 2005-03-30
i just got these cds from a friend. so i would like to give it a try.

i try booting it with the live CD... it boot like normal linux at first... but... at the Ubuntu loading screen.... it suddently flickle once... then the grey colour screen with a "X" came out.. then it flickle again... then my whole system rebooted by itself...

so i tried booting it in expert mode... when the thing is trying to load X windows... loading till half way.. then the X windows shut down by itself then the whole system reboot again...

may i know what happened? i have used FreeBSD 5.2 and red hat linux without problems in this machine...

---

### Post by ymtoh on 2005-03-31
i still can't get it running... anyone please answer me

---

### Post by Dr_Willis on 2005-07-30
Well depending on whats acually in the laptop - theres several possible issues.
You may want to edit the xorg.conf and set the driver to be 'vesa' as a test. 
Be sure to backup your existing xorg.conf just in case.

You may also want to try out the "noapci" and "noapic" kernel options when booting - to see if that helps any.

Im back to fighting with my Compaq V2311us for now, with Turion Processor and X200 video.

Good Luck

---

