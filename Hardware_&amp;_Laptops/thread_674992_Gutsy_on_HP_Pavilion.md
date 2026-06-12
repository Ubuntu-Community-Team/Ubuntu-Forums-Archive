---
title: "Gutsy on HP Pavilion"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by BobTheWidget on 2008-01-22
Hi there all,
I've installed Ubuntu on my laptop using UNetbootin, and selected the Ubuntu Desktop option (gnome).  The laptop is a HP Pavilion DV6101EU.  It sports a GeForce Go 6150, and has a native screen resolution of 1280x800.

I'm a Linux newbie, so be gentle.

Normal start-up of ubuntu yields the Ubuntu loading screen, followed bygraphical corruption (typically a single white line across the screen, followed by the remainder of the screen filling in white, slowly).

I did a bit of digging, and booted into recovery mode.  From the shell I ran Xorg -configure, then started X -config /root/xorg.conf.new  (the exact commands may be a bit off)
In any case, x started flawlessly
I copied the config file from there to etc/X11/xorg.conf
I then edited the file to include HorizSync and VertRefresh lines (previously missing), added a modeline for my monitor and put the mode in the display subsection.
Happy with this, I tried startx.  I got the chequered screen and cursor (which worked with my mouse).
Ctrl+Alt+Bksp got me back to the command prompt; I then tried to get into the gui using gdm
This worked, and everything was dandy.

Assuming that I'd fixed the problem, I restarted and selected normal ubuntu.
Unfortunately, following the loading screen, the glitch returned.

I'm unable to access the network from recovery mode in the gui (haven't tried from the command line).  There appears to be issues with user rights; it says that I'm not allowed to adjust my network settings (despite being root!)

I'd be grateful for any advice you can offer,
Thanks
-Bob

Oh, just quickly -- UNetbootin didn't offer an option for setting screen resolution when installing Ubuntu Desktop.  I'd've thought, however, that that would have been covered by the config file editing...

---

### Post by insineratehymn on 2008-01-22
Is there any reason why you are opposed to using a CD for installation?

Or was the installation using Unetbootin an experiment of the functionality?

---

### Post by BobTheWidget on 2008-01-22
Hi there,
I picked the netboot install 'cos I don't have any blank CDs to hand;  the install process itself appeared to go fine.

---

### Post by insineratehymn on 2008-01-22
You would be surprised how much can go wrong with a little muffed data in installation.

I believe Ubuntu offers free CD's if you are willing to wait for snail mail.

You can even make the ISO USB Flash drive bootable.

---

### Post by BobTheWidget on 2008-01-22
Got it working!

I added noapic to the relevant line in the bootloader, and it now works.

I'd be interested in knowing what this option does (all I know is that it has something to do with PCI interrupts), possible reasons as to why it didn't work without the option, and whether it's worth fixing anything (and indeed, what might need fixing) to get it to work w/out this option.

Thanks!
-bob

---

