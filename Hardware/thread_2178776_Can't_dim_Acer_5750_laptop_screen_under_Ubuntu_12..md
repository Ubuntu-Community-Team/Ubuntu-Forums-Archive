---
title: "Can't dim Acer 5750 laptop screen under Ubuntu 12.04"
date: 2013-10-05
forum: Hardware
---

### Post by johnarro on 2013-10-05
Obviously it would be great to be able to dim the laptop screen on this Acer 5750 in order to extend the battery life when I'm unplugged.

Sadly, using Ubuntu 12.04, nothing does dim it: software settings - nope, unplugging from the mains - nope, Fn+dimmer/brighter keys - nope.

It's a dual-boot machine and when I (ever more infrequently these days :) boot into Windows 7, everything screen-brightness-related works just as you'd expect it to, but running it under Ubuntu 12.04 it simply doesn't :(

(And why Skype under Ubuntu does everything EXCEPT send texts to mobiles I also have no idea, but that's another story :)

Old John

---

### Post by johnarro on 2013-10-05
ps graphics are Intel Sandybridge Mobile x86/MMX/SSE2, processor is an Intel core i3-2310M @ 2.1Ghz x4, and it's a 32-bit OS.

---

### Post by Toz on 2013-10-05
Have you tried any kernel boot parameters? Your best option would be to try **acpi_osi=Linux acpi_backlight=vendor**. Here is how (using a terminal window):

1. With root privledges, edit the /etc/default/grub file:
```
gksu gedit /etc/default/grub
```
...enter your password when prompted.

2. Change the line:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

3. Save the file.

4. Commit the change:
```
sudo update-grub
```

5. Reboot.

---

### Post by johnarro on 2013-10-06
> **Toz said:**
> Have you tried any kernel boot parameters? Your best option would be to try **acpi_osi=Linux acpi_backlight=vendor**. Here is how (using a terminal window):

**Toz, I am for ever in your debt !!!!**

Keyboard dimmer/brighter keys work, "Go dimmer after (eg) n minutes of no activity" works too.

**Brilliant** reply. "Job's a good 'un!" etc etc etc :)

With many thanks,
OAP John 
--
[I]Volunteer for UK Rock Challenge
[www.rockchallenge.co.uk]("http://www.rockchallenge.co.uk")
(Videos are at [www.globalrockchallenge.co.uk]("http://www.globalrockchallenge.co.uk"))[/I]

---

### Post by Toz on 2013-10-06
Glad to hear. If you don't mind, can you makr this thread "Solved" using the "Thread Tools" link above so that others can easily find this thread? Thanks.

---

### Post by johnarro on 2013-10-07
Done :)

---

