---
title: "ATI Catalyst Control Centre 9.3 breaks suspend on Latitude D810"
date: 2009-04-27
forum: Hardware
---

### Post by bluelamp999 on 2009-04-27
Hi friends,

Just installed the above on my Dell laptop and it seems to have broken the suspend function key functionality - i.e. pressing Fn + Esc no longer puts the machine into suspend mode.

The screens go blank and the mouse and keyboard are inactive but the power light stays on permanently. Pressing the power button does not revive the machine.

Selecting 'Suspend' from the panel menu works perfectly...

I'm assuming it might be some setting in the acpi-support file?

Any help appreciated...

---

### Post by bluelamp999 on 2009-04-28
Respectful *bump*

Anybody?

---

### Post by StuartN on 2009-04-28
> **bluelamp999 said:**
> Respectful *bump*

Anybody?

Yes, officer. What version of Ubuntu are you using? And what video card? (paste the output from "sudo lshw -C video").

---

### Post by bluelamp999 on 2009-04-28
Actually, I'm not a cop (despite the signature!)...

I'm running 8.10 and my video card is an ATI Mobility Radeon X300.

Here's the output from "sudo lshw -C video"

  *-display               
       description: VGA compatible controller
       product: M22 [Mobility Radeon X300]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

At this stage I can't suspend the machine at all - the hot-key combo (Fn + Esc) doesn't work, 'Suspend' from the panel menu doesn't work, and suspending from the terminal ("sudo /etc/acpi/sleep.sh force") doesn't work.

The laptop just sits there with the power light, fan etc. running but with a blank screen. The only option available is to hold down the power button to switch the laptop off and then to switch it on again.

As I'm a big suspend user I'd totally appreciate any help...

Many thanks

(And I'm definitely not a cop):)

---

### Post by StuartN on 2009-04-28
It looks like the place to start is any errors in the kernel log.

There is a guide [http://ubuntuforums.org/showthread.php?p=3066404](http://ubuntuforums.org/showthread.php?p=3066404) to suspend and hibernate failures.

---

### Post by bluelamp999 on 2009-04-28
Thanks Stuart...

What I did in the end is just to revert to an earlier Catalyst version.

I reverted to Catalyst 8.12 which solved the suspend issue.

If I've time I might gradually test 9.1 and 9.2 but 9.3 (after a complete wipe and install) is not good for suspend on my system...

Evening all...

---

