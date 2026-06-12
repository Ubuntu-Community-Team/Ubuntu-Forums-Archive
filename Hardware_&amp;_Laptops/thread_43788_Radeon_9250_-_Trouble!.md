---
title: "Radeon 9250 - Trouble!"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by zaguar on 2005-06-23
I've installed Ubuntu sucessfully on my laptop, and so I decided to try it on a real computer.  So another comp (AMD XP 2600+, 512MB RAM, Abit NF7-S mobo, **RADEON 9250** - 64bit, 128mb etc) was up for another Ubuntu install. So, slip the CD in, splash screen comes up - FINE.

So i proceed with the install. Finally, i reboot, and wait for the GDm to come up.  After the lines of text preceeding the login screen complete - the 1024x768, 60hz screen is a garbled bunch of crap.  The mouse cursor is visible, and that can move, but the rest is just garbled rubbish.  

What do i need to do to fix this terrible problem?

---

### Post by zaguar on 2005-06-24
Anyone with any help?  The disc may be scratched, is that the reason?

---

### Post by afonic on 2005-06-24
Try getting on the console (Control - Alt - F2) and run "sudo xorgconfig" to manually set up your display settings.

Make sure the ati driver is selected and if it doesn't work try setting some lower resolutions through that tool.

---

### Post by zaguar on 2005-06-25
Knoppix works fine, thats the thing.  I think it uses xfree86, not xorg.  

BTW, control-alt-f2, and ctrl-alt-f1 do nothing.  Using recovery mode and running dpkg-reconfigure xserver-xorg does not fix it. 

Can i apt-get xfree86 and use that with hoary?

---

### Post by afonic on 2005-06-25
[QUOTE=zaguar]Knoppix works fine, thats the thing.  I think it uses xfree86, not xorg.  

BTW, control-alt-f2, and ctrl-alt-f1 do nothing.  Using recovery mode and running dpkg-reconfigure xserver-xorg does not fix it. 

Can i apt-get xfree86 and use that with hoary?[/QUOTE]
 Did you try xorgconfig in recovery mode?

Maybe it just needs some manually configuration.

---

### Post by geertja3kus on 2005-06-25
Try changing the agpmode (?) in the bios from 8x to 4x. This worked for me.

---

