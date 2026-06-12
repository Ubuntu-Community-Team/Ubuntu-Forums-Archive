---
title: "What is &quot;Begin: Running /scripts/local-top&quot; ?"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by gustl87 on 2006-08-06
Hi @ all !

I am running Ubuntu Dapper on a Compaq Evo N410c - and (except the 3D-acceleration) it works fine.

But the last days i get some confusing lines when i am booting.
I turned the bootsplash off so i can see the text (console).

The lines are e.g.:

"Begin: Running /scripts/local-top"
"Begin: Running /scripts/local-bottom"
"Begin: Running /scripts/init-bottom"

I can't list them all, because it disappears too fast ... but if you could tell me in which logfile they are i will post more.

So my question:
What are these scripts doing ? How can i turn them off ? Why are these scripts starting since just a few days ?

Thank you !

---

### Post by nijhawank on 2006-08-18
You dont need to worry about these scripts, and they were very much getting executed even when you were not aware of it. Only thing was that the logs were not being printed because a kernel boot parameter "quiet" was provided.
So if you are seeing these logs now... did you change something in the menu.lst of grub i.e. remove "quiet" parameter

In fact I myself dont know the exact functions of these scripts but I know they are used to do some preprocessing prior to mouting the root filesystem.
These scripts reside in initrd.img.

- Kamal N

---

### Post by gustl87 on 2006-08-18
thank you !

it might have beent the reason - but i can't proof it now, because i already reinstalled ubuntu - not for this reason but i tried another OS and decided to switch to ubuntu again.

---

### Post by nijhawank on 2006-08-19
You can still check it.

When presented with the GRUB menu, don't just press ENTER on Ubuntu selection but press 'e' which will take you into a temporary edit mode.

In the new screen you'll see a line (2nd line) something like 
kernel /boot/vmlinuz-xxx blah blah

Go over this line and press 'e' again. Remove "quiet" and "splash" from the line and press ENTER. It will come back to the original screen, now press 'b' to boot and you'll see all the boot messages including "Running: /scripts/local-xxx" and others.

The edition is just temporary and for this session only, the next time you boot, it will again be a splash screen.

Regards,
- Kamal N

---

### Post by gustl87 on 2006-08-19
hey ! you are right ! thank you !

so the scripts are allways runnig but only visible, if i remove the quite and splash from the menu.lst

cool i learned something new^^

---

