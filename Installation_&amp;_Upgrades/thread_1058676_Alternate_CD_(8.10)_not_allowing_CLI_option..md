---
title: "Alternate CD (8.10) not allowing CLI option."
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by davemar on 2009-02-03
I've downloaded the alternative CD (ubuntu-8.10-alternate-i386.iso) to try and make a minimal install without a desktop. It downloaded and burned onto the CD OK (check md5 sums and dd'ed image back off CD to check). The boot options available are (according to the help): install, expert, cli, cli-expert and memteset. I typed in cli and it says it can't find the kernel image. What's going on?

Should I be using something else to install a minimal non-desktop version?

---

### Post by Pumalite on 2009-02-03
Burn a new CD. At 4x or less. Clean the lens in your burner
Download ImgBurn:
[http://www.imgburn.com/](http://www.imgburn.com/)
Install. Go to 'Mode'>ISO>Burn. Make 1x your speed of burn.

---

### Post by davemar on 2009-02-05
The CD burned OK, as the image I read off it matched the one I burned onto it. The image also had the correct md5 number.

---

### Post by dabl on 2009-02-05
> **davemar said:**
> 

 I typed in cli and it says it can't find the kernel image. What's going on?



You'll have to choose one of the "install" or "expert" items to begin the installation -- the Alternate CD is not "Live" - it is not a command interpreter.

---

### Post by davemar on 2009-02-08
I reloaded the iso and burned onto a different CD and it at least had a go at installing. There still didn't seem to have any way of choosing what I want to install from the options, or have I overlooked something? I just want the base system and not the desktop.

---

### Post by ugm6hr on 2009-02-08
It is hidden somewhere in the "Expert" install option somewhere.

I found the eaisest way to do a commandline install is actually to use the mini iso.

[http://ubuntu-lxde.wikidot.com/intrepid](http://ubuntu-lxde.wikidot.com/intrepid)

---

### Post by davemar on 2009-02-11
I managed it in the end with the mini.iso and the cli-expert option. Just needed to select the linux-386 kernel.

---

