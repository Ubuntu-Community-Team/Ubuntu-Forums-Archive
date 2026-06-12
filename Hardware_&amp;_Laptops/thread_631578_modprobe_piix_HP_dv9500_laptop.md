---
title: "modprobe piix HP dv9500 laptop"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by Princegiri on 2007-12-04
I have a HP dv9500 series laptop

i had to follow the instructions given on this thread to boot into the live cd and then i could install ubuntu fiesty fawn.

**[http://ubuntuforums.org/showthread.php?t=523733](http://ubuntuforums.org/showthread.php?t=523733)**

basically, this involved typing 'modprobe piix' when the busybox popped up

i followed the instructions further down as well. that is, right after installation i didnt quit live cd and continued to add the 'piix' line to the modules file 
**$echo piix >> /etc/initramfs-tools/modules**
and then $update-initramfs -u

but this seems to have not worked........as now everytime i log into my ubuntu i have to type 'modprobe piix' at the busybox......

is there any way around this? 
i also navigated to  /etc/initramfs-tools/modules and the file has the line "piix" appeneded to it. the update also runs fine but there is no output for that operation.... is that the way it is supposed to work?

---

