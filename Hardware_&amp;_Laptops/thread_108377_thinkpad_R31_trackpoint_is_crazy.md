---
title: "thinkpad R31 trackpoint is crazy"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by cefs99 on 2005-12-25
Hi,

I'd read several posts here but seems their problems are different from mine. I am using thinkpad R31 with latest Ubuntu distribution CD instllation. My problem is, quite frequently, about every 10 mins, the mouse cursor will move and click out of countrol. For example, when I am reading news online, the mouse suddent move to the up right cornel and click at the calendar button. It also happens even when I am actually using the trackpoint. My R31 only have trackpoint, no touchpad. I am not complaining about the sensitivity or mouse speed issue. The trackpoint works perfect when it's not crazy...

I also experienced same problem when I use Fedora before.

Anything wrong?

Thanks,

Hong

---

### Post by hawkeyes on 2006-01-01
ls,
I have the same machine (with dutch keyboard) and run into the same problem, it happens with me only when i hold the trackpoint for a long time.
If i release is now and then it does not flip around.....
greetings and hope it helpes,
Remco

---

### Post by cefs99 on 2006-01-02
[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2004-February/015859.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2004-February/015859.html)

According to above file, this issue went away after upgrade kernal from 2.6.2 to 2.6.3. but Ubuntu 5.10 use kernel 2.6.10, why this problem still exist?

---

### Post by cefs99 on 2006-01-06
[QUOTE=hawkeyes]ls,
I have the same machine (with dutch keyboard) and run into the same problem, it happens with me only when i hold the trackpoint for a long time.
If i release is now and then it does not flip around.....
greetings and hope it helpes,
Remco[/QUOTE]


Hi, I'd found the solution and it works!

Just use

sudo gedit /boot/grub/menu.1st

then find the line:

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash apm=broken_psr
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot


this line is the default ubuntu booting kernel. Now look at the line start with "kernel". Noticed "apm=broken_psr"? that's the answer to make the trackpoint come down. just add those to the line, save the file then reboot. That's it!

I got this solution from  Stephan Fuhrmann at

[http://kruemel.rnbhq.org/r31.html#apm](http://kruemel.rnbhq.org/r31.html#apm)


Thanks Stephan!

---

### Post by nanofox on 2007-10-21
I'm sure that this problem has given many users a major headache in the search for the correct answer. It seems that the answers above couldn't provide me with the relief that the other users were receiving. My search is over and this worked for me! I hope this will help everyone out!


Just use like the earlier posts

sudo gedit /boot/grub/menu.lst

then find the line:

title Ubuntu, kernel 2.6.12-9-386
root (hd0,1)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash i8042.nomux=1
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

this line is the default ubuntu booting kernel. Now look at the line start with "kernel". Noticed "i8042.nomux=1"? that's the answer to make the trackpoint come down. just add those to the kernel line, save the file then reboot. That's it!

here's the web page where I found the info  http://www.thinkwiki.org/wiki/Problem_with_checking_battery_status'>Problem with checking battery status - ThinkWiki  

If you use apm then the post above might work for you but i use acpi so maybe that's the difference

---

