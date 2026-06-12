---
title: "Need help with my laptop real fast"
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by pestypest on 2006-03-14
ok i just got my new 2nd HD and im wanting to install it on my laptop. Its a 60GB SATA internal (my laptop supports 2 drives). Im going to install ubuntu on the new and leave doze where it is now. I was wondering what i should do first after i put it in and power up? like is.. settings in bios if any? so i can still use grub and dual boot. i want to install the MBR on the 60GB also. thanks for any suggestions :D

---

### Post by jpkotta on 2006-03-14
I'm pretty sure you can (and should) install GRUB to your Windows drive, and not even worry about the MBR of the other drive.  I have done this before, but it was a while ago.  Here is the menu.lst from the machine I did it on.  PM me if you figure it out (so I can add a section to the wiki about it) or if it doesn't (so I can help).

---

### Post by pestypest on 2006-03-15
[QUOTE=jpkotta]I'm pretty sure you can (and should) install GRUB to your Windows drive, and not even worry about the MBR of the other drive.  I have done this before, but it was a while ago.  Here is the menu.lst from the machine I did it on.  PM me if you figure it out (so I can add a section to the wiki about it) or if it doesn't (so I can help).[/QUOTE]
ok cool. well it seems to be working with no issues yet (knocks on wood) i have both dirves in and i booted into both OS's with no problems.

---

### Post by LoclynGrey on 2006-03-15
I boot win xp and ubuntu from seperate drives. (actually going to just be Ubuntu from now on as Windows has decided after many months to just bluescreen lol)

Here's my main grub settings.

------
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
makeactive



title		Ubuntu Linux, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

---

