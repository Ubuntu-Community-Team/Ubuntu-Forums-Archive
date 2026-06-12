---
title: "Unable to prevent laptop screen dimming when on low battery"
date: 2014-09-24
forum: Hardware
---

### Post by sgarman on 2014-09-24
Hello,

I'm running Ubuntu 14.04 with Gnome Shell on a Lenovo T440s laptop. I have the "Dim screen to save power" checkbox un-checked in my System Settings->Brightness & Lock dialog, but yet when the system thinks my battery is low, it will dim my screen when idle for 10 seconds or so. 

The problem is my laptop has two batteries, and this behavior starts when the first battery is getting low. But in fact I still have hours of battery life left.

I assume this is some sort of ACPI setting or script, but I've been unable to find anything by digging around myself. Can anyone point me to where this kind of automatic screen-dimming on inactivity is controlled?

Thanks,

Scott

---

### Post by sgarman on 2014-09-24
I will add that suspending and then waking up my laptop after the transition to the other battery has occurred stops the auto-dimming behavior. So this is a temporary workaround. Presumably upon wakeup the system will see the second battery's remaining life.

---

### Post by tgalati4 on 2014-09-25
I presume that the BIOS handles the 2-battery behavior.  So if one battery is weak, then it triggers the "Oh No, must save power at all costs." mode.  First, I would look for a BIOS update.  Make sure you are running the latest.  If that doesn't fix the behavior, then you need to get creative.

You have found a work-around.  You can write a script to check the battery status and when below 15% trigger a notify-osd message asking you suspend and transfer batteries.

Or, spend the $120 and get a new battery.  The nature of lithium batteries is that when one cell (out of 6 or 9) gets weak, it makes the whole battery pack worthless.  As soon as voltage drops to a trigger level (typically 11 VDC for a 12 VDC pack) all hell breaks loose--instant shutdowns, mysterious suspend behavior, etc.  Having a second battery doesn't fix this situation because the batteries are separate and require a manual step to transfer.  I've seen some scripts for semi-automatic transfer, but I wouldn't risk my work to that handover.  I'm sure in Windows, there are drivers that make this transition smoother.  Just as docking and undocking with lots of external peripherals attached.  With linux it is hit-or-miss, but generally works under Windows as you would expect.  Try hot-swapping an Ultrabay device in linux.

I have an older T43p and I have the same behavior, but I'm too lazy to fix it.  But I have researched it.  You could say I am an educated derelict.

---

### Post by sgarman on 2014-11-04
I just wanted to follow up and mention that this issue is fixed on Ubuntu 14.10.

---

