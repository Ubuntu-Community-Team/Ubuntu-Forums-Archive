---
title: "Second hand laptop, terrible battery life, any suggestions?"
date: 2008-08-29
forum: Hardware
---

### Post by Tarmael on 2008-08-29
I got a second hand laptop off a mate, the battery life isn't that flash hot.

Any ideas or ways to better improve the battery life?

I've already done a few things; System > Administration > Services and taken out a few more useless services (Bluetooth, CUPS, etc); changed my background to black (black is more power efficient); I've edited the power management thing to settings I like.

Any way to dim the screen down a little? The task bar applet doesn't support my GPU (ATi 200M).

I hear 8.10 will have better optimisation for laptops.

Keep thinking people!! I need my battery!!

---

### Post by erudite on 2008-08-29
System > Preferences > Screensaver > Blank Screen
Making the background black doesn't make a difference with LCD screens just to let you know because most of the power is used by the back light.

---

### Post by Redptc on 2008-08-29
Are the batteries due to be replaced, some go beyond recharging! New batteries may show an improvement.

---

### Post by sdennie on 2008-08-29
Try:

```

cat /proc/acpi/battery/*/info

```

If there is a large difference between "design capacity" and "last full capacity" then, a large part of the problem is just that the battery is old and should be replaced.

Either way, you might be able to get some extra battery life using one of these guides: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644) and [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773).  The first one is just a generic way of setting up the scripts whereas the second is a more hands on example on how to set them up for a specific laptop model.  You may find useful information in both.

---

### Post by Scunge on 2008-08-29
Don't know whether you have this laptop and just want to use it for something, or if it's your only machine and need to get it working as best you can.

If it's the former, read on...

I was in the same situation a while back. I got an old, *old* laptop from a friend who had it just lying around doing nothing.

It had a broken keyboard, a 2 GB disk, 64 MB memory, a 150 MHz PII processor, no ethernet port, a single USB 1 slot, and a 20-minute battery life. Throw it on the tip, right?

Nope.

I have a USB keyboard so plugged that in and changed the BIOS to allow it to be recognised upon boot. I bought a mew 80 GB disk and a second-hand USB to Ethernet dongle. I took the battery to the tip and permanently plugged the laptop into the mains instead. I installed Ubuntu Dapper on it from the alternative CD, which works in "low memory mode" and doesn't install the GUI. I installed BackupPC.

Now it sits hidden away, never needing to use the broken keyboard because everything relevant starts upon boot. I ssh into it whenever needed, and BackupPC has a web interface so I use any other machine's browser for that. It's attached to my network from it's single USB 1 slot via the Ethernet dongle, and has been running 24/7 apart from the occasional reboot for about a year now, backing up every other computer on my home network.

It's the most important PC in the house.

Perhaps that's a use for your second-hand laptop?
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by Tarmael on 2008-08-29
> **erudite said:**
> System > Preferences > Screensaver > Blank Screen
Making the background black doesn't make a difference with LCD screens just to let you know because most of the power is used by the back light.

@ erudite:

I did that one before, forgot to mention. I did it on the idea that I don't want to be using the graphics card when I don't need it.
Is there a way to edit the back light settings then?

@ Redptc, vor and scunge:

design capacity:         1726 mAh
last full capacity:      1726 mAh

Battery looks fine.

I DO need to replace the charge pack though, it's frayed and there is a home job to fix it. My first stage instead of just going out and buying a new one is to first strip this one and solder it down. I know it's not as good an idea as getting a new one, but I'm also saving for my wedding next year so I don't have much spare $$

I lose battery power when it's plugged in... I get a bit more than 45minutes from it when it's not plugged in, so I think I need to do something drastic...

I think there may be some internal over workings.

I'm going to bust it open and clean it out today.

@ vor:

Thanks heaps. I'm modifying those scripts now.

---

### Post by nicedude on 2008-08-29
Unfortunately Ubuntu does not manage batteries very well by default and instead needs heavy tweaking to get some decent battery life per charge. My brand new laptop was getting only 1hr25min with battery in Hardy and 2.5hr in XP which is pretty bad difference. I now have a custom power management script in place with different settings for AC & BATT and have been able to get mine back up to 2hr in Hardy which is at least allot more livable but I still keep meaning to try and tweak it more. So don't think your battery is broke before you follow vor's links and look at tweaking your own :-)

I still have had heat and other issues as well and Linux needs some definite power & heat management work to catch up with the bad OS in these matters :-)

Goodluck

---

### Post by Tarmael on 2008-08-30
Thanks everyone, I can now charge the lappy (I called it Balthasar, now I have Balthasar and Melchior... Neon Genesis Evangelion) and use it at the same time.

Next stop, replacing the charger.

Thanks heaps.

---

### Post by erudite on 2008-08-30
I don't think there is a way to change backlight brightness in Ubuntu but I could be wrong.

Usually you change it with your monitor?  If not then I guess you can't do it.

Glad that you can use it and charge it at the same time now.  Enjoy!

---

### Post by Tarmael on 2008-08-30
I can change the back light on the Desktop, but the lappy doesn't have those options (which is standard).

Oh well, good enough as is.

Thanks again, all.

---

