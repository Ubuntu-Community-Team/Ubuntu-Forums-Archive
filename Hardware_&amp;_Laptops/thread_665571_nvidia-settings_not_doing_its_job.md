---
title: "nvidia-settings not doing its job"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by ElTimo on 2008-01-12
I have an nVidia Quadro 110m (equivalent to a 7300), and I'm trying to get antialiasing working for compiz. I have the latest nVidia driver (as far as i know) and I update everything else religiously. When i tell nvidia-settings to override application AA settings, nothing happens. Same when i run it as root. I enabled nvidia-glx-config and still nothing. I'm out of tricks. Any help would be much appreciated.

---

### Post by []Milo on 2008-01-12
Hi ElTimo, 

Have a look here:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=646356&highlight=antialiasing]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=646356&highlight=antialiasing")

---

### Post by ElTimo on 2008-01-13
Milo,

Thanks, but i didnt have any luck with that. It seems like it should work, too.......

---

### Post by chenel on 2008-01-20
Not that it's any help, but I have the same problem...

---

### Post by chenel on 2008-01-20
Have you tried running nvidia-settings with the flag --verbose=all?  This will hopefully spit out any errors you may be getting without realizing it.

Also, are you running nvidia-settings from the 'run application' box you get from Alt-F2 (using gksudo), or are you actually running 'sudo nvidia-settings' from a terminal?  It worked all of a sudden (inexplicably) for me when I ran it from the terminal...

---

