---
title: "Prolonging battery life"
date: 2009-05-09
forum: Hardware
---

### Post by Neon612 on 2009-05-09
I have a Toshiba Satellite P305D-S8900 with Vista/Jaunty dual boot. I was looking for a way to save power or make the battery last longer when in Ubuntu. The power manager keeps changing my settings and powertop kills the processes only for the present session. (Is that all it is supposed to do?)

I'd like to find some way of getting it to last longer or at least as long as  Vista will, about 2 hours.

---

### Post by Ocxic on 2009-05-09
try powertop from the repos

---

### Post by Neon612 on 2009-05-09
I have powertop, but it only seems to kill the power hungry process for the rest of that session.

---

### Post by mariner09 on 2009-05-10
Powertop should make some recommendations as to how to make the changes permanent.

There's also laptop-mode-tools which may offer some additional power savings like hard drive efficiencies.

---

### Post by Neon612 on 2009-05-13
One quick question, How do I use the laptop-tools addon?

---

### Post by Neon612 on 2009-05-17
bump.

I'd like to get things figured out before I have to start school.

---

### Post by Uncle Quag on 2009-08-04
> **Neon612 said:**
> I have a Toshiba Satellite P305D-S8900 with Vista/Jaunty dual boot. I was looking for a way to save power or make the battery last longer when in Ubuntu. The power manager keeps changing my settings and powertop kills the processes only for the present session...

Hey, Neon, are you by chance getting any messages at boot similar to the following:```
[    2.302213] handlers:
[    2.302254] [<ffffffff8044f6a4>] (acpi_irq+0x0/0x26)
[    2.302352] Disabling IRQ #9
```This may be related to the problems you're having with power manager and powertop not retaining settings.  I have the same model laptop, and a number of functions have stabilized after applying the **acpi_osi=Linux** boot option noted in this thread: [http://ubuntuforums.org/showthread.php?t=1223197](http://ubuntuforums.org/showthread.php?t=1223197)

Note: My battery usage isn't stellar using the stock 6-cell batt that came with the unit.  I'm getting about 70 to 90 minutes out of a single charge (depending on WiFi use and what I have the CPU Frequency Scaling Monitor set to in my panel), but this is pretty much on par with what I was getting out of Vista before dumping it completely for Jaunty... didn't bother tweaking Vista much beforehand.  I've also replaced the stock hard drive with a 7200 RPM Scorpio Black, which would account for a lot of my battery drain, so you might be able to squeeze 2 hrs out of your battery if you've kept the stock Toshiba drive.

Figured the additional info might be helpful.

---

### Post by Velvet_Man on 2009-08-04
I was having a problem with battery life on my laptop and none of the suggestions I found on here seemed to really make a big difference.

Then one day I was trying to configure power management settings and got really frustrated with the Gnome apps, so I decided to install KPowerSave. It ran great in Gnome and did exactly what I wanted it to do. Just by setting it to cut my processor speed in half when on battery and then boost it back to full when on AC (instead of constantly changing all the time based on what I'm doing instead of where the power is coming from) my battery went from lasting maybe 2 hours to hanging on for almost 4 hours. Of course, it's slower when on battery that way, I but it's a trade-off I prefer for the battery life.

---

