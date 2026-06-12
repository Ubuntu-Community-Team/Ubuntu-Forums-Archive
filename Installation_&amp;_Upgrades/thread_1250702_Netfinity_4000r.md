---
title: "Netfinity 4000r"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by fornews on 2009-08-26
Anyone install Ubuntu on netfinity 4000 ?
I found some comments referring to other models but they didn't help.

What I experience . . .

Desktop 9.04

Boots to language selection menu.
Select to Try with out installing
Screen blanks then a brief screen ending  no tag to resource
Then monitor takes over with..  Attention Signal freq out of range

Then it just hangs there.

I'm wondering if I should opt for another OS ??
I just loaded SLES on the server so I know it's good.

Thank you,

---

### Post by stlsaint on 2009-08-27
without further testing i would suggest using something like puppylinux or DSL!! check them out and try...they are smaller distros than jaunty or hardy!!!

---

### Post by fornews on 2009-08-28
> **stlsaint said:**
> without further testing i would suggest using something like puppylinux or DSL!! check them out and try...they are smaller distros than jaunty or hardy!!!

Appreciate the reply.

I don't think I have a space issue and if I can't get Ubuntu to work I'll likely try RedHat next.

I've been able to install, or so it appears, using the Alternate CD, however, I still have the display issue. I'm able to boot the Alternate CD and log into the recovery mode hoping to be able to configure the video manually using some command and I've attempted using  **dpkg-reconfigure xserver-xorg** which only provides prompts to reconfigure the keyboard.

Is there any other way to configure the video ?
Some searching implies this last ditch effort has been removed from the install image... can that be true ??

TIA

---

### Post by fornews on 2009-09-08
> **fornews said:**
> Anyone install Ubuntu on netfinity 4000 ?
I found some comments referring to other models but they didn't help.

What I experience . . .

Desktop 9.04

Boots to language selection menu.
Select to Try with out installing
Screen blanks then a brief screen ending  no tag to resource
Then monitor takes over with..  Attention Signal freq out of range

Then it just hangs there.

I'm wondering if I should opt for another OS ??
I just loaded SLES on the server so I know it's good.

Thank you,

Given what I saw on the display I assumed the hang was a display configuration problem, but it ended up being a kernel parm caused hang so the boot process wasn't even getting to the video configuration... oh well.

Fixed by removing 'quiet splash' from the kernel parms in /boot/grub/menu.lst.

Now I need to figure out why Ubuntu 8.04.3 can't recognize my display correctly (7.10 can) and consequently it wont save any resolution above 640x480

---

