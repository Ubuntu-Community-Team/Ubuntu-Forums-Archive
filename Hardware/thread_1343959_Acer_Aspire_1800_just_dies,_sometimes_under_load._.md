---
title: "Acer Aspire 1800 just dies, sometimes under load. WinXP is fine."
date: 2009-12-02
forum: Hardware
---

### Post by fizzybrain on 2009-12-02
'ello.
My Acer Aspire 1804 laptop just stops sometimes. Like dead. Switches itself off, as though the power had been pulled. I have a base install of Kubuntu (upgraded to 9.10), but it also happens when running xfce4.

Annoyingly (or maybe not annoyingly), WinXP has *never* done this which implies that it's not as simple as bad CPU, RAM, etc.
I have done full memtest86 scan with no errors. Fans and heatsinks are clean and re-set (I have re-set the heatsink with new thermal paste).

About half the time I'd say the system was working hard (like playing .dv video), but at other times it just seems to give up (though it does tend to wait until I'm just about to start thinking about saving what I'm working on).
Is it possible that k/ubuntu is using the hardware differently? maybe not managing power correctly?

What logs should I look for? Is there a background diagnostic programme which I can run which might give more information on crash? I have a network so could even log diagnostic data on another machine (to avoid running disk constantly).

Any thoughts?

Share and Enjoy,

---

### Post by slumbergod on 2009-12-02
I have an Acer Aspire 5720 laptop. Under Jaunty and Karmic the system seems to struggle at times. Karmic in particular seems less compatible in the sense that the fan is always in overdrive. Converting flac files to ogg is actually enough to overheat the system and cause a shutdown as you described.

Running Windows on it never posed any problem at all, same as you. It is just a weird issue with Ubuntu. I never found a workaround for this so for now I have had to avoid audio conversion and mkv files.

---

### Post by fizzybrain on 2009-12-02
I wonder - have you tried any other distros? I'll maybe have a go at installing something else. Sometimes I use Puppy and I don't think that ever failed this way - but I never drove it hard with anything like doing video processing....

---

### Post by Teto_z on 2010-01-10
I have the same problem, and I'm investigating on it. if you check /var/log/messages, you can see that there is a Bios bug. So, like log suggested ( :D ), you can use the 2nd ACPI/MADT table by adding
```

acpi_apic_instance=2
```to the kernel line in grub.cfg

---

