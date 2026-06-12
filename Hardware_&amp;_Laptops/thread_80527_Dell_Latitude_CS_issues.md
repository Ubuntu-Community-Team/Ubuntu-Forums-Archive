---
title: "Dell Latitude CS issues"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by Tsume on 2005-10-22
A few issues with my Ubuntu installation on this laptop that I hope someone can shed some light on:


This only happens about 1/2 the time on boot.  It will sit there, and I can't CTRL+C or anything.  I have to hard power it off and back on, and then usually it boots fine.  I went into recovery mode, and here's the last few bits before it just sits there with a blinking cursor forever:

> [4294722.506000] ath0: Atheros 5212: mem=0x11000000, irq=11
     piix: already loaded
     uhci-hcd: already loaded
[4294723.446000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
     i2c-piix4: loaded successfully
     ignoring pci display device 01:00.0
[4294724.727000] PCI: Enabling device 0000:01:00.1 (0000 -> 0002)
[4294724.728000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294724.729000] PCI: setting IRQ 5 as level-triggered
[4294724.729000] ACPI: PCI Interrupt 0000:01:00.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294724.729000] nm256: found card signature in video RAM: 0x3fec00
[4294724.729000] nm256: Mapping port 1 from 0x3f09a0 - 0x3fec00
_


My CD-RW/DVD-ROM drive isn't hot pluggable.  I have to reboot to get Ubuntu to detect it.  This works fine in Windows.  Unplugging the drive while the computer is on results in a freeze after 5-10 seconds... this affects Windows too, so I don't expect to see this fixed.  I hope someone can make it so I can plug the drive in and have it work automatically though, after I've already booted.   The drive is external, and it's not a standard interface like USB or Firewire, I believe it's a proprierity Dell interface... this same drive I also use with my C400, and the connector for that PC (on the end that plugs into the laptop) is a slightly different shape than my CS's.  The PC comes with this cable, not the drive, that's why I believe it's a proprierity interface.


Another issue I have is with NoAccel="false" (default) for the neomagic driver AND using a 24bit mode, there is display corruption sometimes, vertical lines in places with random colors.  If I set it to true, it's really SLOW (due to no acceleration) but the corruption is gone, if I use a 16bit mode, the corruption is gone.  If I use VESA driver, corruption is gone.  I'd like to use the 24bit mode if possible... it works fine in windows, and according to the man page for neomagic, my 256ZX should be able to do this fine in 24bit mode.


Yet another issue, the only Fn key that works is Suspend.  I found an entry on the bug tracker that sounds like this... most of the Fn keys never send a keyup message, which is of course the laptop's fault but something that needs to be worked around... looks like they're working on it so not much of a complaint here since it will probably be fixed within a year.


Sound doesn't work in games unless I disable sound server startup in gnome's options... this seems to effect many (all?) installations of Ubuntu, not limited to this PC, so it will hopefully be fixed in the near future.


I ranked those in order of biggest show-stopper to smallest flaw, IMO of course.  On a positive note, I have had much more success getting suspend-to-ram and hibernate to work on this computer with Ubuntu in comparison with my Latitude C400 and Ubuntu.

---

### Post by jorgen_s on 2005-10-23
I have an old Latitude CPt C333GT (also NeoMagic256) and have exactly the same problems in 5.10. Have trided grub boot options irqpoll, noapic and acpi_irq_isa=9 but no luck, it got worse or the same.

Any suggestions are much appreciated...

EDIT: After a little googling I found this: [http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=nm256](http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=nm256)
Anyone tried this?

---

### Post by Tsume on 2005-10-24
Seems too hard for me level of noob skill, or I'd try it.

No one else has any ideas on these problems?

---

### Post by am4c130d on 2006-01-10
Hi Tsume,

Please read the following, hopefully I've spelt it out a little more clearly.

[http://www.ubuntuforums.org/showthread.php?t=90336&highlight=nm256](http://www.ubuntuforums.org/showthread.php?t=90336&highlight=nm256)

However, if you are still reluctant to modify the alsa-base file, I'd highly recommend that you simply upgrade your BIOS - it may well address the problem completely, and I don't think the problem is addressed until the BIOS is upgrade.

I don't have a CS laptop, so YMMV.

Thanks

Alan

---

### Post by fwendt on 2006-02-04
I have the exact same problem, and it fails to boot almost exactly every second time the computer is booted.

I only booted the previous stable version of Ubuntu three-four times, but didn't experience any troubles with it, only with 5.10.

I've updated the BIOS from version A09 to A13, which is the latest available from Dell, and this didn't fix anything. (I've also disabled as good as all features available in the BIOS and none of this helps, (of course) as the problem seems to be related to the NeoMagic chip?)

I'll read up on the the alsa-thing, try it and post back.

---

### Post by fwendt on 2006-02-04
To boot without problems (I've restarted the computer 10+ times now without any hickups) I had to disable the driver for the soundcard, so there's no sound but everything is fine.

To disable the soundcard for the NeoMagic nm256 chipset, write "snd-nm256" (without quote characters) on an empty line in /etc/hotplug/blacklist. This will prevent the hotplug system from loading the linux kernel module named snd-nm256 which is the driver for this soundcard. Hopefully, the programmer who wrote the module will update the driver with a fix for this issue.

---

### Post by tvankirk on 2006-05-02
[QUOTE=Tsume]A few issues with my Ubuntu installation on this laptop that I hope someone can shed some light on:


This only happens about 1/2 the time on boot.  It will sit there, and I can't CTRL+C or anything.  I have to hard power it off and back on, and then usually it boots fine.  I went into recovery mode, and here's the last few bits before it just sits there with a blinking cursor forever:
[/QUOTE]

The instructions is this post fixed the freeze on boot problem for me:

[http://www.ubuntuforums.org/showpost.php?p=977788&postcount=9](http://www.ubuntuforums.org/showpost.php?p=977788&postcount=9)

---

### Post by cwa107 on 2006-06-25
I have a Latitude C400, also with the external, proprietary CD-RW drive.  Although I have no issues with booting on 6.06, I do experience the same problem when disconnecting/reconnecting the CD drive.  I am running the latest BIOS and it is not a problem in XP.  Has anyone had any luck in rectifying this under Ubuntu?  Does the problem occur in other Linux distributions?

---

