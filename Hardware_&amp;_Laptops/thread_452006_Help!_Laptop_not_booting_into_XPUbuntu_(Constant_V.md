---
title: "Help! Laptop not booting into XP/Ubuntu (Constant VAIO animation)"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by blahdieblah on 2007-05-22
I had been using Ubuntu installed by Wubi for only half of a day. While looking at a new login screen I had downloaded by switching users, the mouse froze up. I ended up force-rebooting the computer. Instead of asking me whether to boot into XP or Ubuntu, it just showed the normal VAIO boot up animation, went black for about eight seconds, and did it again. The only way I can get anything going is to stick in my Ubuntu Live CD. Looking in the home folder, I see the main hard drive of my machine. Right clicking it, "mount" is an option... But it gives me the following message:

"Unable to mount the volume"

Details: mount: wrong fs type, bad option, bad superlock on /dev/ sda2, missing codepage or other error, in some cases useful info is found in syslog - try, dmesg | tail or so

I am a total newbie to Ubuntu, but I felt like I knew my way around it fairly well after several sessions with the CD. Now, I'm lost. I have no idea what to do. Can someone help?

---

### Post by nioakeim on 2007-05-23
What kind of mount do you do? Can you quote it please?
Probably you screwed your MBR. I have never tried to restore a MBR in ubuntu, But i know what you must look for. It's the grub-install command. You must look further yourself for more details.

If you want at least to restore you windows part, the only thing you must do is to boot from the winxp cdrom, enter recovery console and on the command line write

fixboot (return)
fixmbr (return)

and your boot recond is restored, ONLY FOR WINDOWS...I hope i helped a bit

---

### Post by blahdieblah on 2007-05-23
First, I just want to thank you a lot for the reply... This whole thing has freaked me out. As for what kind of mount I have, I'm not really sure what you mean. All I know is that it's my internal hard drive, about 80 gigs, and normally running Windows XP. 

I will look for the XP CDrom, and try what you suggested. I'll post again when I've tried it.

---

### Post by xenoph0be on 2007-05-23
You might also look into [Super Grub Disk(http://freshmeat.net/projects/supergrub/)]("http://freshmeat.net/projects/supergrub/")

---

### Post by blahdieblah on 2007-05-23
Wow... That looks like a dream piece of software. Thanks. I'll look into it, definitely.

---

