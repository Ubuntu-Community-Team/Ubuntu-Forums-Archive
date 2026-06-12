---
title: "[SOLVED] CANNOT BOOT!!! BIOS/Grub problem?"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by cadamr on 2007-10-30
My laptop won't boot!

I am dual booting Vista/Gutsy on an Asus G1 laptop using Grub. I had just shutdown vista, and when I tried to turn it back on the next day, the bios loads, grub starts to load but stops and the computer restarts. It never makes it to menu.lst. If I boot a flash drive w/ a live version of ubuntu on it, it does the same thing. I have a flash drive with just grub on it, but it doesn't work either. If i boot with the grub flash drive, the bios loads, the word "GRUB_" is displayed and then it freezes. 

Unless windowz did it w/o telling me, i haven't done any bios updates recently. windowz did install some updates (no idea what they were for) and i had just installed AutoCAD.

-----------------------------------------------
FIXED!! This is what I did:

I took out the harddrive, booted off my live flashdrive, replaced the harddrive, and finally reinstalled grub to the MBR using grub-install.

---

### Post by froy02 on 2007-10-30
I had almost the same problem. At the time, Vista was installed on the laptop, then I installed Ubuntu.   I was new to Ubuntu so I played with it a lot.  
That time I used my vista install disk to repair the installation.  Boot with your vista disk and choose repair rather than install and you get vista back.
I lost Ubuntu but I was able to re-install it but using  using less of the hard drive space for it.

Later I found out also there's website for super grub that may help you.  Maybe you should try it first.
  
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

This helped me when I messed up the 2nd time.  Recovered both vista and ubuntu.

---

### Post by cadamr on 2007-10-30
Thanks for the reply. 

It didn't work. Supergrub did the same thing that grub did. After the bios finished loading it displayed "GRUB _" and just stopped. If worst comes to worst, i can put my harddrive in someone else's laptop to backup everything and then just reinstall. I really don't want to have to do that though. 

Any other ideas?

---

### Post by cadamr on 2007-10-31
bump!

---

### Post by cadamr on 2007-10-31
bump!bump!

---

### Post by CoolDreamZ on 2007-10-31
This is probably a dumb question but can you boot from a Live CD?

---

### Post by CoolDreamZ on 2007-10-31
See also this thread:

[http://ubuntuforums.org/showthread.php?t=597227](http://ubuntuforums.org/showthread.php?t=597227)

---

### Post by cadamr on 2007-10-31
I can't boot from a live cd because my cd/dvd drive broke a week ago. bad timing, huh? :(  

Another tidbit of information: when I try to boot normally or from my live flash drive, the last thing it does before restarting is beep and flash the words "grub loading stage 1.5"

This makes no sense. The live flash drive and normal boot both seem to be failing at stage 1.5, but they are both using their own copy of stage 1.5.

---

### Post by jellymaster2 on 2007-10-31
Ahhhh I had this problem with my desktop a while back when I was dual booting XP+Ubuntu(switched to XP+Vista now back to XP+Ubuntu)it's a problem with Ubuntu, somehow the Ubuntu bootloader messed up and needs a fresh stall(fixed it for me)you said you disk drive broke? you may haveta put it in another laptop/buy a new disc drive and do a fresh install of ubuntu. Worked for me and I had the exact problem. Showed the compaq logo, pretended to load,beeped,did a "Loading GRUB stage 1.5.......Grub 1.5 load error" and all this other stuff.

---

### Post by cadamr on 2007-10-31
Hmmmm, that's what I was hoping not to hear. I have a few ideas I'd like to try before doing a reinstall:

Replacing grub with lilo
reinstalling the bios

Do you think either of these will work? Thinks for the replies, keep the ideas coming!

---

### Post by jellymaster2 on 2007-10-31
I doubt the bios will work,and I'm not sure if replacing the grub with lilo would work. you could always give it a shot, I haven't tried this personally so I'm not sure the outcome. worst comes to worst you get onto a live CD for ubuntu find the files u wanna back up,get 'em off the HD,reinstall ubuntu,and replace the files.

---

### Post by cadamr on 2007-10-31
I'll try lilo, and if that doesn't work, i'll bakup & reinstall. Thinks for the help.

---

### Post by jellymaster2 on 2007-10-31
no prob I'm not that experienced with Ubuntu but I hope to spend more time playing with it and learning so if you need anything PM me

---

### Post by adrian15 on 2007-11-06
> **cadamr said:**
> I'll try lilo, and if that doesn't work, i'll bakup & reinstall. Thinks for the help.

Get a SGD floppy. Try **GNU/LINUX -> BOOT LINUX** and then within your linux. Do an:

```

apt-get remove grub 
apt-get install grub

```

And see if it fixes the problem.

adrian15

---

### Post by cadamr on 2007-11-06
FIXED!! I don't have a floppy drive, but this is what i did instead:

I took out the harddrive, booted off my live flashdrive, replaced the harddrive, and finally reinstalled grub to the MBR using grub-install.

Thanks for the help everyone!!!

---

