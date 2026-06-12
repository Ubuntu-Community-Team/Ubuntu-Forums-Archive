---
title: "Acer 4061NWLCi: HOWTO get everything working under Ubuntu Breeze Badger 5.10"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by saurabhnanda on 2006-04-02
It's been two days since I've bought my laptop, and I've been struggling since then to get everything working under Linux -- Ubuntu Breezu Badger 5.10. I've still not managed to get ACPI working fully (fan doesn't start at all). Everything else seems to be working just fine -- if not like clockwork. 

I'll share my experience so that others with the same laptop might find the process easier (I'll keep updating this post as and when I keep getting things to work better):

[SIZE="4"]**Display**[/SIZE]
This is the standard i915 resolution problem. Just apt-get install 915resolution read the docs and proceed.

[SIZE="4"]**ACPI**[/SIZE]
ACPI is basically power management features. The ACPI DSDT in this laptop is broken. Period. You'll have to work around it. The GNOME battery status indicator will always show as the AC adapter as plugged in and the battery level as zero. The ACPI module will throw up a lot of errors while booting.

You might want to look at the [DSDT listing for Acer](http://acpi.sourceforge.net/dsdt/view.php?manufacturer=ACER) at the [ACPI4Linux website](http://acpi.sourceforge.net/) to check if someone else releases the fixed ACPI for this laptop. To know what a broken DSDT is, and what you can do about it you might want to look at the ACPI4Linux website and this page [here.](http://www.whoopy.it/linux/ACPI_problem_linux_resolved.html)

**ACPI Fix**
I downloaded the vanilla 2.6.16.1 kernel of [kernel.org](http://kernel.org) compiled and installed it. **ACPI works -- partially!** 

Stuff that works: Automatic CPU frequency scaling, battery level indicators, ac adapter status, CPU temperature monitoring.

Stuff that doesn't work: CPU fan -- does not switch on at *all* -- this is dangerous! Haven't checked sleep/hibernate.

**Important Note:** With the 2.6.16.1 kernel the Fn+Left arrow key (to decrease the LCD brightness) will put the laptop in sleep/hibernate mode. I don't know why this happens, but I narrowed down the cause to atkbd driver. The Fn+Right arrow key (scancode: 0x0e 0x6e) is happily ignored by the driver -- a releavant message shows up in /var/log/messages when you press it. But, the Fn+Left arrow key is recongnized by the driver and converted a keycode, which is then probably picked up by some user space app to put the laptop to sleep. Here's the temporary fix for this till the time I figure out something more permanent:
$ sudo setkeycodes e06f 00

[SIZE="4"]**Sound**[/SIZE]
The default kernel in Breeze Badger is 2.6.12. This kernel does not have the proper drivers for the sound card -- **Indel HDA Realtek ALC260 ** -- on this laptop. The ones downloaded off Realtek's site are a modified version of alsa-1.0.9b_26. They did not work for me. I dowloaded alsa-driver-1.0.11rc4 off ALSA's website and compiled/installed them. Everything worked perfectly.

#tar -jxvf alsa-driver-1.0.11rc4.tar.bz2
#cd alsa-driver-1.0.11rc4
#./configure --with-cards=hda-intel
#make
#make install

**Caution:** The make install step will remove all the other sound drivers modules from /lib/modules/2.6.16.1/kernel/sound -- only snd-intel-intel and related modules will be left.

I'll keep updating this post as and when I figure out how to make more stuff work. If anyone else finds anything, even if it is how *not* to make things work -- please post & share.

---

