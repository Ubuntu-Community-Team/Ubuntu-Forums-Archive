---
title: "usb 2.0 halts boot."
date: 2008-11-25
forum: General Help
---

### Post by DeadMissionary on 2008-11-25
I have an acer aspire dual booting xp and ubuntu.  Originally, I had only xp on it and it worked great.  Now that I have ubuntu(8.10) installed, I cannot use my onboard usb2.0.  It still works in windows, but when I try to boot into ubuntu with it enabled(enabled in my bios settings), ubuntu will get to a point in the boot where it is trying to assign ?an address? to the usb device.  Once it gets there, whatever it is doing fails repeatedly and ubuntu will not continue past this.  This does not happen if I have usb2.0 disabled in my bios.  Help please... I like figuring this stuff out on my own, but I do not know where to go from here.  Thanks.

I am pretty sure I did not give whoever helps enough information to really tell me where to go or what to do, so please let me know what you need to know(and maybe how to get that information) and I will get it asap.

---

### Post by cariboo on 2008-11-25
Is there any way that you can write the exact error and write in in you next post? Also do you have any usb devices plugged in when this happens?

Jim

---

### Post by DeadMissionary on 2008-11-25
The error is as follows:

[  33.964018] usb 3-4: device descriptor read/64, error -110
[  33.964018] usb 3-4: device descriptor read/64, error -110
[  33.964018] usb 3-4: device descriptor read/64, error -110
[  33.964018] usb 3-4: device not accepting address 6, error -110

I have a generic keyboard that came with the computer and a logitech g15 lasermouse.  I am googling the error now...  So far no luck

---

### Post by ndefontenay on 2008-11-25
Hi.

I've found this:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273)

and this:

[http://www.linux-usb.org/FAQ.html#ts6](http://www.linux-usb.org/FAQ.html#ts6)

There is mention of using the command:

```
rmmod ehci-hcd
```

The error code is -32 and not -110 however.

You should be finding more information in the faq.

good luck

Nico

---

### Post by DeadMissionary on 2008-11-25
Yeah... Saddly I found those links while googling myself.  The only problem is, nothing that is attached to my usb(keyboard, mouse) works once the system boots.  So I cant even log in to try that command.  I read somewhere about setting acpi=something or other in the boot flags.  I'll find that and give it a shot...  Thanks for the look mate

---

