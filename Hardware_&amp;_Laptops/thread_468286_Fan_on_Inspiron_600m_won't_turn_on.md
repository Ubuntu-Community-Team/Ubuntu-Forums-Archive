---
title: "Fan on Inspiron 600m won't turn on"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by andnobodyslept on 2007-06-08
I think the title said it all. It's not a huge deal, since I try to only use the laptop for short periods, but for those times I am watching flash videos for a long time the thing really heats up. It's not an fglrx issue since it uses a Raedon 9000 and I have to use the Raedon driver. Also don't have windows on this machine so I don't know if it is a software problem or if the fan is busted. But it would be nice to turn the fan on.

Thanks

---

### Post by 444 on 2007-06-08
Poke around in the /proc/acpi/ folder, there might  be a way to manually turn the fan on there.
If you don't have the Dell diagnostics on your HD anymore, it's on the Dell Resource CD. Use that to see if it's a  hardware issue.

---

### Post by andnobodyslept on 2007-06-08
I'll dig out the CD, I think I still have it. Either way after looking in /proc/acpi for a while I really can't do anything, not even view files, they always come up as having been changed on the drive and needing to be reloaded, so I can't read anything. Maybe if I go in as root, but I would rather not do that until I have a better idea.

Thanks for the help though.

EDIT: There are no files in the /proc/acpi/fan folder...Not quite sure if this changes anything....

---

### Post by 444 on 2007-06-08
How about this tool:
[http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)
I'm guessing that since the Windows i8kfangui works for 600m this one will work since it uses the same method.

---

### Post by andnobodyslept on 2007-06-08
Thanks again, the program seems to work fine, but the fan doesn't start...I'm beginning to guess that it is a hardware problem, or something even bigger than that (since the lm-sensors didn't detect anything). Either way that will have to wait since I'm moving and the Dell CD is all packed away. At least everything is running just fine.

btw this is a nifty little program (dellfand) might want to keep everyone with their dell fan problems informed about it. I know I will.

Thanks

---

