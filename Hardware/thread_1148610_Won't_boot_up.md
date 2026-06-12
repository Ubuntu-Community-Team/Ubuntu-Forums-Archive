---
title: "Won't boot up"
date: 2009-05-04
forum: Hardware
---

### Post by Imoen on 2009-05-04
My computer won't boot and I really don't want to loose everything I have on it. It was working fine but Skype kept saying it couldn't start because it was already running even after I killed any skype processes, so I thought I should just restart and see if that would help. Now I get the press esc to select boot options message and after that my monitor just goes black and flashes out of range. I have tried editing out quiet and it made no difference nor does trying to boot to recovery mode. I have not installed the update to 9.04 so I believe I'm using 9.03 (9.04 does not have a driver for my video card). Please help me, I'm a Ubuntu noob and have no idea how to fix errors like this.

I posted this in the general and a person suggested I post here instead.

---

### Post by Imoen on 2009-05-04
Well after much searching I have found that the issue seems to be with my monitor.

Following what is [here](http://ubuntuforums.org/archive/index.php/t-856902.html) I changed the vga=799 to vga=795 and it boots into a command line type screen where it says /dev/sda1 unexpected inconsistency and runs through some kind of disk scan then tells me run fsck manually, fsck died with exit status 4.

when I type fsck nothing seems to happen though. I tried to run the livecd but that won't even load, it just says out of range still.

Can anyone please help me with this, I need my computer to run. There is web sites that are not working right now because they run from the computer.

---

