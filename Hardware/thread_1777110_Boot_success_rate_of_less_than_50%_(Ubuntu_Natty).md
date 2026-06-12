---
title: "Boot success rate of less than 50% (Ubuntu Natty)"
date: 2011-06-07
forum: Hardware
---

### Post by Perow on 2011-06-07
Hello,
I've tried looking around these forums and other parts of the web for solutions to my problem, but the details are so vague, it's difficult to find accurate keywords.

I recently got a new laptop, a HP Pavilion dv6, that came with Windows 7 installed. I installed Ubuntu 11.04 (Natty Narwhal) as well, side by side (and a shared partition for documents, etc).

The problem is simple: whenever I select Ubuntu in the grub boot menu, I have a black screen with a blinking cursor for a few seconds, after which there's a chance I'll actually boot in Ubuntu, but a bigger chance that nothing happens: black screen. The chance is about... 1/6 success, but it varies. This is incredibly annoying, because I need to force shutdown and try over and over to boot in Ubuntu, ending up in Windows when I really get sick of it.

Something possibly interesting: when I'm in the black screen, I can switch "viewports" (I'm not sure about the correct term), using Alt+Fkey. One of the other views (Alt+F7) shows a list of operations, etc.

I'm really not sure what it can be, mostly because there appears to be a random factor (or 'luck', if you please) deciding whether or not the boot will succeed.

I hope the community can provide some help.
Thanks.

---

### Post by esdi on 2011-06-07
Hello, 

Sounds like your issues are similar to these 

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by sanderd17 on 2011-06-07
can you login in one of the tty terminals?

if so, can you execute the 
```

startx

```
command and see if you can start x manually?

---

### Post by Perow on 2011-06-08
@Sanderd - Nope, that's not possible. It goes wrong before I get to a working terminal.

@Esdi - Thanks, looking into it.

Here are some notes, mainly for self-reference.
> 
phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware

That seems to be the wrong-doer. Thank you camera phone.
rt2800pci seems to be my wireless. I'll try disabling my wireless antenna before booting. See if that works.

---

