---
title: "Laptop won't switch to battery power"
date: 2009-08-04
forum: Hardware
---

### Post by Velvet_Man on 2009-08-04
Hi Everyone,

I've been using Ubuntu on my Compaq Presario R3000 laptop for a little over a year now with no real problems. I started with 8.10 and upgraded last month to 9.04 through Update Manager. The update went smoothly and everything worked perfectly.

Last week I didn't use my laptop all week. Then two days ago I tried to fire it up, but it wouldn't boot from the battery. So I plugged in the AC adaptor and it started up no problem.

When I got into my Gnome desktop, I checked kpowersave (I didn't like the Gnome app, so I've been using the KDE one -- works great for what I need) and it said my battery was 100% charged. So I unplugged the AC and the computer instantly shut off.

It still wouldn't boot from battery, so I plugged the AC back in and booted it up again, and again it went off as soon as the AC was unplugged.

I tried removing the battery and putting it back in. Nothing.
I tried leaving the battery out overnight. Nothing.
I even tried a suggestion I saw in another thread about taking the battery out and holding the power button for 10 seconds. Nothing.
I tried booting from a live CD (again, based on something from another thread) and it didn't seem to recognize the battery. So I tried ACPI in terminal and it said ACPI wasn't installed.

I forget the commands, I just copy and pasted from other threads I found about battery issues - but the computer knows it's a laptop and it knows there's a battery connected and that's it's 100% charged, it just won't use it.

I have no idea why this started all of a sudden. Everything was working perfectly. And the battery is only about two months old. 

Any help would be greatly appreciated.

---

### Post by Velvet_Man on 2009-08-04
Here's an update.

I figured if the Ubuntu LiveCD didn't do anything maybe Kubuntu would.

So I downloaded Kubuntu 9.04 and ran the live CD. It recognized the battery right away, reported it as 100% charged. But again, once I unplug the AC adapter, the computer turns off.

I also tried disconnecting the battery while in the Kubuntu LiveCD. It recognized that the battery was disconnected. Upon re-inserting the battery, Kubuntu reported the battery was there again and still at 100%.

Does anyone have any ideas what I can do here?

---

### Post by Uncle Quag on 2009-08-05
Hi Velvet_Man,

If your laptop won't boot at all when on battery power alone (power button does nothing, machine won't POST), that's pretty much an indicator the battery itself is fried, rather than having anything to do with the OS.  I've been through plenty of situations like this over the years, especially with aftermarket batteries.  If know someone who has the same machine or a machine that uses the same battery, borrow it to see if your machine will boot and/or whether or not your friend's machine will boot with yours.

If a battery that's known as working won't boot your machine, you may have a problem with your laptop's charging system, at which point I hope you still have warranty coverage on the machine.  If it turns out to be the battery itself, since it's only a couple of months old, hopefully your warranty is still in effect and will cover a replacement.

---

### Post by ubudog on 2009-08-05
Yep, you need a new battery.

---

