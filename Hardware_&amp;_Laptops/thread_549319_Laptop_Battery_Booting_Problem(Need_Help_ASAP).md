---
title: "Laptop Battery Booting Problem(Need Help ASAP)"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by mingo on 2007-09-12
I've searched the forums and couldn't find anything like my problem. Sorry, this is a long post.

I recently replaced my old battery with a new one yesterday and my laptop will shutdown down without warning right before it gets the the Ubuntu loading screen. The laptop will not turn on afterwards until I plug the AC back in. At this point I was thinking that the battery must be defective, but here's the kicker:

When I turn the laptop on with the AC connected, wait till the log-in screen appears, and then disconnect the AC everything will be fine. I can log-in, surf around, do whatever I want, and even the Battery info will say the proper percentage charged and the proper amount of time left till the battery loses it's charge.

**Two things to take note**
- I should note is that my old battery will only last about 5 minutes which is why I bought a new one, but when using the old battery I can boot the laptop without it shutting off like with what happens with the new one.
- I originally ordered this battery a couple of weeks ago, but I was having the same problem with that one too so I shipped it back to them and they sent me a replacement. And now the replacement is doing the same thing which is why it probably has something to do with either my laptop or ubuntu. Or it might be possible that this second battery is defective.

 I need to know what to do soon so I can ask for a refund or another replacement before the warranty runs out. Any help will be greatly appreciated.

**Specs:**
Ubuntu Feisty Fawn
Alienware Area 51m

Thanks,
mingo

---

### Post by mingo on 2007-09-12
I should clarify that I'm wondering if it's possibly an ubuntu/software solution rather than a battery/hardware problem.

---

### Post by Linicks on 2007-09-12
Just a suggestion:

Are you sure the new battery[ies] you received are really charged up?  I would power-up with mains and leave it for about 6 hours to make sure.

The battery may _show_ it is fully charged, but it might not be - hence when the laptop powers down when it comes up and detects low charge.

Nick

---

### Post by mingo on 2007-09-12
I left the laptop plugged in and off for about three hours till the charge-light stopped blinking. I'm pretty sure that if it wasn't fully charged it at least had *some* charge in it. At least enough to boot up and run to the log in screen.
I'll try leaving it on and plugged in for a few hours to see if the battery status changes.
I'm just not sure where the problem lies. It's pretty frustrating.

---

### Post by walkerk on 2007-09-12
I don't really have an answer for you but I've recently begun having problems with my battery.. according to acpi it will only discharge or read charged at the last percent resgisterd while discharging..

I'm going to let it run to 0% now to see what happens. I suspect its a software issue as my laptop is fairly new.. I could be wrong though.. I guess I'll know in 43 minutes..

---

### Post by Linicks on 2007-09-12
> **mingo said:**
> I left the laptop plugged in and off for about three hours till the charge-light stopped blinking.

I have read somewhere, once, but cannot remeber where that there is an issue with the laptop OFF  - the battery doesn't charge up correctly.

Now, I can't remember if this was concerned with a laptop in a docking station or not.

I would leave the laptop on during this period.

Nick

---

### Post by kgr132 on 2007-10-07
I'm having a similar problem to the one mentioned, except that Feisty hangs during the boot only if I try to boot while using the battery alone. 

After it hangs I can force a shutdown (hold power button for more than 2 secs.), plug in the AC adapter and then power on - everything works great. 

If I shut down again with a normal Ubuntu shutdown, unplug the AC adapter and power back on - the boot will hang. The system is Feisty running on a Dell Latitude D600.

Keith

---

### Post by Wiebelhaus on 2007-10-07
Sounds like a thermal issue to me.

---

### Post by kgr132 on 2007-10-09
Definitely not a thermal issue. I have this problem on cold boots. I'm talking the laptop's been off overnight and won't boot Ubuntu from the battery. Windoze will, Ubuntu won't (unless I plug in the AC adapter).

---

### Post by Onyros on 2007-10-12
Hey, I had the exact same problem with my Thinkpad X31.

I had had this problem before and it was happening again once I upgraded to Gutsy.

What did the trick for me was reinstalling acpi, acpi-support and apmd.

---

### Post by kgr132 on 2007-10-15
Thanks for the reply. I tried reinstalling the packages mentioned above, no luck. Battery bootup still hangs. Plugged in boots fine.

---

### Post by randy_miller on 2007-10-25
I'm was having this same problem on my Dell Latitude D600 with Ubuntu 7.10.  Cold boot on battery power hangs at about 80% of the boot progress bar.  Hold down the power button for 3 seconds to power off, plug in, push the power button again, and it boots right up.

Someone above mentioned "reinstalling acpi, acpi-support and apmd.".  I ran apt-get install on all three of those, and they all said I had the latest versions.  I ran apt-get remove on all three of those anyway.  Then rebooted (plugged in).  Then ran apt-get install on all three.  Rebooted unplugged.   No change.

I found the supported laptop page:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)
and found notes on the Latitude D600 that a some distro had an IRQ conflict between the parallel port and the battery.  I wasn't having any of the other problems that the notes there indicated, but I decided to give it a try.  I never use the pp anyway, so I disabled it.  Problem solved.

-Randy

---

### Post by kgr132 on 2007-10-26
Excellent work. I can't remember the last time I used the parallel port so I disabled it via the BIOS and now I can boot with battery or plugged in. No problems either way. Thanks.

---

