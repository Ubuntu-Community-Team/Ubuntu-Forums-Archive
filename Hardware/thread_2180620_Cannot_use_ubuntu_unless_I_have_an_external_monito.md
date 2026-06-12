---
title: "Cannot use ubuntu unless I have an external monitor connected"
date: 2013-10-13
forum: Hardware
---

### Post by moriokasan on 2013-10-13
I have a fresh install of Ubuntu 13.04 64bit. over a Toshiba Satellite P75-7200 which came with Win8.
During install I had brightness issues, the brightness was so low that I connected an external monitor (on HDMI) to be able to install Ubuntu. Then I had to use the Boot-Repair-Disk to enable the Grub. 

Now, that Ubuntu is installed, I downloaded all updates, I turned off my laptop, disconnected the monitor cable and restarted the machine without monitor plugged in. 
The result is that the laptop display is completely off (it is not turned on and the screen is black, but it is off completely, nothing lit). If I connect the external monitor again, using HDMI, that external monitor displays correctly.

In Win8 it works.

Using the second monitor I saw that, by default the monitors were mirrored (in display settings). When I removed that my laptop display came to life. I set the resolution (maybe too high... don't know) and I forced the launcher on that laptop display hoping that next time  I turn the laptop on (without the external monitor connected) it will do the trick. Reboot and again laptop display is off and... I shot myself in the leg... external monitor doesn't even have the launcher to allow me to play with resolution again :).

Question is obvious: how can I set ubuntu in such a way that it works without an external monitor attached to the laptop? What am I missing?

Thanks all!
Marius




SOLUTION:

1) lower the resolution of laptop display 
2)  $ gksu gedit /etc/default/grub
                  Find the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
                  Replace with : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
     $ sudo update-grub


I hope I helped at least one person. 
I guess now I have a pretty solid procedure of how to install Ubuntu on a Toshiba Satellite. Please let me know if anyone is interested.

---

### Post by moriokasan on 2013-10-13
One issue: resolution. After posting this thread I noticed that the resolution was too big so I lowered it down. Now half the problem is resolved. Once I start my monitor is still off but after I log in (using second monitor) at least laptop display comes to life now without any tweaking. Now the only thing remaining , hopefully, is to move the login screen to the laptop display. 

Any help is appreciated.

---

