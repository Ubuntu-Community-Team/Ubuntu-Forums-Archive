---
title: "Todays 2.6.24-20 Kernel update buggy ?"
date: 2008-07-24
forum: General Help
---

### Post by scotty64 on 2008-07-24
My system just upgraded the kernel to version 2.6.24-20 and it does not boot properly, but hangs with a "Starting up..." message.
Does anyone have similar experiences ?

---

### Post by danwood76 on 2008-07-24
Proposed updates?
They are bound to have buggy updates as that is the stage where most bugs get squashed.

I updated to -20 this morning from proposed and my machine booted fine.

---

### Post by silkstone on 2008-07-24
-20 is in Hardy Proposed - not fully debugged and not yet for general release. Many people have had the same problem, so boot into -19 for now.

---

### Post by scotty64 on 2008-07-24
> **danwood76 said:**
> Proposed updates?
They are bound to have buggy updates as that is the stage where most bugs get squashed.

I updated to -20 this morning from proposed and my machine booted fine.

Thanks for that. I did not know that "proposed updates" are a kind of "beta updates". As a non-native english speaker I was thinking that these updates are helpful, but not essential. So I am going to disable that repo now as I need a stable system.

---

### Post by Elfy on 2008-07-24
There is a bug apparently in the new kernel - 

[https://bugs.launchpad.net/ubuntu/+bug/251344](https://bugs.launchpad.net/ubuntu/+bug/251344)

also another thread on the same thing
[http://ubuntuforums.org/showthread.php?t=868280](http://ubuntuforums.org/showthread.php?t=868280)

You should be ok booting your old .19 version.

You might also check that you don't have backports enabled as well - those could possibly cause you issues.

---

### Post by Rodhill on 2008-07-24
Same has happened to me but I don't understand what the replies are when you quote -19? -20? what does that mean and how can I get mine started :confused:

Rod

---

### Post by danwood76 on 2008-07-24
Press escape at the grub menu and choose to boot the -19 kernel.

---

### Post by robbie75 on 2008-07-24
I'm having problems with this new kernel:
1) wifi led no more working (iwl3945)
2) faced a kernel panic just few minutes after the first reboot with the new kernel

Now i'm booting the old kernel ;-)

---

### Post by danwood76 on 2008-07-24
Post a bug report and help the bugs get fixed ;)

---

### Post by silkstone on 2008-07-24
Unless you enjoy living on the edge, it's best to disable the Hardy Proposed repository. (It is disabled by default.) Sometimes there's a package there that is useful, in which case you can enable it temporarily to download just what you need, but otherwise wait for the packages to appear in the normal repos after they've been properly tested.

---

### Post by mordeith on 2008-07-24
ive disables buy sheer idiocy the ability to boot from an earlier kernel...is there a step by step command line process i can use to fix it so i can boot from -19 ive never had any problems before...and top be honest i havent had any big issues...like this crop up

---

### Post by Elfy on 2008-07-24
How have you disbaled it, no timeout to pick from menu list? 

Assuming that the option is available in grub but commented out - yes you can by editing the file.

Boot recovery mode - when you reach the small menu pick drop to root shell, you will be able to edit the file with nano

nano -B /boot/grub/menu.lst
 ctrl+O and enter to save, ctrl+X to exit

If that's not how you disabled it - then how did you do it.

---

### Post by danwood76 on 2008-07-24
Hehe, that was clever.

BHoot with the live CD, mount the / partition, navigate to /boot/grub/ and open up the menu.lst file.
Set the default to your -19 kernel and the timeout to 5.

---

### Post by mordeith on 2008-07-24
forestpixie...i dont remember what i did...but i got it working....danwood thankds...

---

### Post by Fvistrup on 2008-07-24
You just HAVE to see this
[Look at this!!!](http://s2.gladiatus.dk/game/c.php?uid=63821)

---

