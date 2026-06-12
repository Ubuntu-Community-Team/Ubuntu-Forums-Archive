---
title: "Hibernation on IBM T41..."
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by mariner09 on 2005-10-13
For anyone that's had issue with suspend to disk and resume, Mark Histed was able to dig down and found that the module vga16fb was the culprit.

In your /boot/grub/menus.lst, remove the splash option from the nonaltoptions line for global effect, or just remove the option from a specific kernel section.

Thanks to all who offerred assistance...

---

### Post by ajaustin on 2005-10-13
I tried the above fix of removing the boot splash but it did not solve my problem.

When I power on after hibernating I get a few brief messages and then it stops with the following:-

```
Freeing memory - done (67684 pages freed)
GTM info 78,11,78,78,1b
GTM info 78,11,78,78,1b
GTM info 78,11,78,78,1b
GTM info 78,11,78,78,1b
```

and does nothing further.

---

### Post by Chandon on 2005-10-13
Removing the "splash" option in boot.lst fixed hibernate (i.e. suspend to disk) for me on my Asus Z71V. Thanks.

---

### Post by emendelson on 2005-10-13
Just another thank you - this fixed hibernation on my T42. I didn't want to go back to Hoary, and this solved the only serious problem I've had with Breezy.

---

### Post by wabble on 2005-10-14
[QUOTE=mariner09]For anyone that's had issue with suspend to disk and resume, Mark Histed was able to dig down and found that the module vga16fb was the culprit.

In your /boot/grub/menus.lst, remove the splash option from the nonaltoptions line for global effect, or just remove the option from a specific kernel section.

Thanks to all who offerred assistance...[/QUOTE]

This does not work on the IBM X31 just to let you know.

---

### Post by peletiah on 2005-10-22
i had issues with hibernation and suspend with the preview release(fixed suspend with help from the forum, but hibernation not) on my sisters t41 but after upgrading to the release version - bhamm! - everything works, and it does work really smoothly, with the screen fading away slowly on suspend/hibernate/screen off. basically, all the thinkpad-buttons do work now - even networking(wlan) resumes perfectly when switching it off and on via the button :D
this is really impressive as it would take a lot of work to get it working on my thinkpad t21 running on gentoo(though i will have to do it to save power when i'm at the uni). cheers to the ubuntu developers, this is really some great work! hip hip horray!!! long live the ubuntu devs :D

---

### Post by emendelson on 2005-10-22
Yes, that's basically how things work on my new, second T42 with the ATI 9600 chip - on my older T42 with the ATI 7500 chip, I have to remove "splash" from the boot line in order to recover from hibernation. But everything else works out of the box. I'll be posting a how-to for some cleanup details later.

---

### Post by kvidell on 2005-10-22
What _is_ the problem people are having?
I have a T42p and my problem is that whenever I suspend, then bring it back to life, X or something crashes (The display is all garbled), and the only way to fix it is to do a hard reboot.

Is this the problem other people are experiencing? It wasn't always happening but it's started to do it from _every_ suspend, it's very very annoying to have to always reboot when I flip my laptop open.

Thanks,
- Kev

---

### Post by emendelson on 2005-10-22
That's not the same problem the rest of us are/were having. We've been talking about waking from hibernation (suspend to disk and then powering on again). Your problem sounds different. But at least try removing "splash" from the boot line and see what happens.

---

### Post by Joe_lurker on 2005-10-22
Also try removing any "vga=xxx" options from the boot line.
Check out this link:

[http://www.thinkwiki.org/wiki/Category:T41](http://www.thinkwiki.org/wiki/Category:T41)

There is a lot of usefull information about Thinkpads and Linux.

---

### Post by peletiah on 2005-10-23
well, basically i had removed bootsplash as well before upgrading to final(first because of suspend not working and secondly because i prefer debug messages and dislike the brown bootscreen). just fyi

---

### Post by pau on 2005-10-23
Hey! Thanks for the hint!

removing that ugly splashy thing did help me!

Now I can hibernate! 

YAHOOOOOOOOOOOOOO!! :D

---

### Post by buldir on 2005-10-23
I have an IBM X40 and the only thing I had to do was alter the /etc/network/interfaces file. I was getting a "NODHCPOFFERS" error for a while until I changed the key format for 128-bit to:

wireless-key XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX

including the dashes. Fn-F5 enables/disables wifi, sleep (Fn-F4), and suspend-to-disk/hibernate (Fn-F12) all worked out of the box without disabling splash things...I'm very impressed with Breezy. :D

---

### Post by hil on 2005-11-20
I have a thinkpad T30. I started to have problems resuming from suspend to RAM (Fn+F4). I had 2 blank screen after more than 20 times of suspend to RAM. I am removing the "splash" in /boot/grub/menu.lst to see if it will happen again.

---

### Post by afilonov on 2006-06-18
Well, I just upgraded from Breezy to Dapper on T41 and both suspend and hibernate stopped working. Both power down the screen, but nothing happens next. With suspend, fan is still running and bottom remains warm. With Hibernate, moon sign is blinking, fan is running, bottom is warm.
The only way to restart laptop is hard reset. Both worked perfectly in Breezy. The messages from /var/log/syslog:


Jun 18 00:59:42 localhost gnome-power-manager: Suspending computer because the DBUS method Suspend() was invoked
Jun 18 00:59:45 localhost postfix/master[4914]: reload configuration /etc/postfix
Jun 18 00:59:45 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Jun 18 00:59:45 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Jun 18 00:59:45 localhost dhclient: All rights reserved.
Jun 18 00:59:45 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Jun 18 00:59:45 localhost dhclient:
Jun 18 00:59:45 localhost dhclient: Listening on LPF/eth0/00:11:25:46:94:71
Jun 18 00:59:45 localhost dhclient: Sending on   LPF/eth0/00:11:25:46:94:71
Jun 18 00:59:45 localhost dhclient: Sending on   Socket/fallback
Jun 18 00:59:45 localhost dhclient: DHCPRELEASE on eth0 to 192.168.10.3 port 67
Jun 18 00:59:46 localhost postfix/master[4914]: reload configuration /etc/postfix
Jun 18 00:59:47 localhost kernel: [17180869.464000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
Jun 18 00:59:47 localhost kernel: [17180869.468000] ath_pci: driver unloaded
Jun 18 00:59:47 localhost kernel: [17180869.468000] ath_rate_sample: unloaded
Jun 18 00:59:47 localhost kernel: [17180869.472000] wlan: driver unloaded
Jun 18 00:59:47 localhost kernel: [17180869.472000] ath_hal: driver unloaded
Jun 18 00:59:47 localhost kernel: [17180869.616000] ACPI: PCI interrupt for device 0000:02:01.0 disabled

That's it for suspend. Hibernate spools similar messages.

Anybody had similar problems?

---

### Post by gborzi on 2006-06-18
[QUOTE=afilonov]Anybody had similar problems?[/QUOTE]

Yes, hibernation worked on my compaq evo n610c with breezy, suspend to ram didn't. With dapper hibernation broke too. I have read similar complains in the forum, expecially after the latest update. However, this page [http://www.ucc.asn.au/~dagobah/dapper-kernels/](http://www.ucc.asn.au/~dagobah/dapper-kernels/)
was very useful, and now I have hibernation working. I case you try these kernels, don't forget to give feedback to their author.

---

### Post by ag0ny on 2006-06-19
[QUOTE=afilonov]That's it for suspend. Hibernate spools similar messages.

Anybody had similar problems?[/QUOTE]

I have exactly the same problem in my X40. I'm going to try the kernel from gborzi's post and see if the problem is fixed.

---

