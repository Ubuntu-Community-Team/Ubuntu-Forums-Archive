---
title: "*FIX* HP AMD64 Suspend/Hibernate"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by #Reistlehr- on 2007-10-27
Ok, i have a HP dv9000z CTO. I'm not sure how wide the scope is (Older models of HP's if it affects the dv6000z's, if it works on non-64 kernels.. so use at your own risk)

But this is what works for me. it is almost 100% imperitive i got this working as i'm always on the road for work and such. i was losing a total of 1 hour a day in boot time since i have the whole gnome login time takes an hour problem (Bug no, i think it has to do with compiz).

But here it is

I have to use noapic with my bootline, to get buntu to boot. I added, nosmp after it. (Can someone tell me the effects of turning off smp in an smp kernel? I haven't noticed any problems though. It actually runs smoother.

so do:
```

gksudo gedit /boot/grub/menu.lst
```
Look for your Linux entry, and add **nosmp** to it. (after noapic is you use it, or after quiet splash)

```

gksudo gedit /etc/default/acpi-support 

```

make these changes:
```

MODULES="ndiswrapper"
POST_VIDEO=false
ENABLE_LAPTOP_MODE=true

```

Replace ndiswrapper with your module for wireless.

I've been testing it for two days. Hibernating it, taking it out, standby, take it out. I left it in standby for 3 hours, and it came back fine. No problems at all.

I hope this works for someone. 

REMEMBER:: This is for those who need it immediatly. It's not suggested to be used, until someone can confirm it works.

---

### Post by mangoHead84 on 2007-10-30
I just tried this method with no luck. Firstly after adding 'nosmp' to the boot options Ubuntu refused to start up. 

After removing the nosmp option but keeping the modified /etc/default/acpi-support file (the only difference from the recommended file was that I set MODULES="bcm43xx") and trying out suspend it still would not work.

The laptop goes into suspend without problem but then after trying to resume the laptop looks like it's waking up but the screen remains blank and no combinations of keyboard commands work e.g. Ctrl+Alt+Backspace

---

