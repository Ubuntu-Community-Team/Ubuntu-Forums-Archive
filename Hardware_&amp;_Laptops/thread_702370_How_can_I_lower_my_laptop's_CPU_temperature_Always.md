---
title: "How can I lower my laptop's CPU temperature? Always 57-67 C and high CPU = Shutdown!"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by motin on 2008-02-20
**The Problem**
Short: Too high CPU Temperature

Long:
Every time I use ffmpeg to convert a movie my computer shuts down eventually with the following syslog message:
```
Feb 20 13:49:19 laptop kernel: [ 5696.848000] ACPI: Critical trip point
Feb 20 13:49:19 laptop kernel: [ 5696.848000] Critical temperature reached (102 C), shutting down.
Feb 20 13:49:19 laptop kernel: [ 5696.896000] ACPI: Invalid passive threshold
Feb 20 13:49:20 laptop kernel: [ 5696.899000] ACPI: Critical trip point
Feb 20 13:49:20 laptop kernel: [ 5696.899000] Critical temperature reached (84 C), shutting down.
Feb 20 13:49:20 laptop kernel: [ 5696.905000] ACPI: Critical trip point
Feb 20 13:49:20 laptop kernel: [ 5696.905000] Critical temperature reached (102 C), shutting down.
Feb 20 13:49:20 laptop kernel: [ 5696.909000] ACPI: Critical trip point
Feb 20 13:49:20 laptop kernel: [ 5696.909000] Critical temperature reached (84 C), shutting down.
```

In perfect idle, with only Opera running and the laptop elevated (for fan space), my CPU temperature ir around 57-66 constantly. Shouldn't it be around 30-40 in idle?

I have an alarm set (using the computertemp applet) that reports temperatures over 75 - and it comes up frequently whenever I use the computer normally. 

(Earlier I occasionally experienced this problem when the fan grids were blocked by ie bed covers - but now this occurs even when the laptop sits on the desktop with but free space around the fan grids!)

**Any solution?**
I have heard that cleaning or even replacing the fan could help - but I have blown spray can air onto the fan to remove dust and I hear no abnormal noise from the fan... 

Also, I've heard that the thermal paste might need to be replaced - but is this a likely error here and - is it possible to replace it oneself you think? Model: Hp dv4000...

What are my other options? I'd love to be able to use ffmpeg again...

As a workaround - It would be swell if the initiated critical shutdown instead would trigger the hibernation script - so that one at least could resume work without losing all unsaved data!

Thanks for any help!

**Notes**
Frequency scaling works great and the fan adjusts to high workload (I hear...). 
(Although, I seem not to have ACPI throttling:
```
motin@laptop:~$ cat /proc/acpi/processor/*/throttling
<not supported>
```
Which could be an issue that triggers the Critical shutdown according to [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/22336](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/22336))

To get more diagnostics, I tried running sensors-detect but there are no drivers for my sensor chip:
```
#----cut here----
# Chip drivers
# no driver for Nat. Semi. PC87591 Super IO yet
#----cut here----

```
(And according to [http://forums.fedoraforum.org/showthread.php?t=178822](http://forums.fedoraforum.org/showthread.php?t=178822) there might never be...)

PS I checked [how to lower the cpu temperature in ubuntu](http://ubuntuforums.org/showthread.php?t=660957) but it was only for Macbooks...

---

### Post by oldsoundguy on 2008-02-20
photo processing and data conversions take processor and memory .. and in big chunks.  Maybe a laptop cooler would be in order when it is tied down doing such at home (know you do do this when mobile, so should not be a problem).   There are many after market coolers available, but the nicest ones I have seen are like a refrigerator in operation.  You could make ice cream on the surfaces of the things! (not really, but they do get very cold to the touch) 
There are cheap (noisy) fan type coolers, there are moderately priced and relatively quiet coolers, and then there are the refrigeration type. There are even some that run off of your USB bus!
Go shopping at a couple of big box stores .. find what you want .. and then buy it off of eBay (carefully)
What you are looking for is about a 10 degree reduction

---

### Post by baeckel on 2008-02-20
You could underclock your processor -or-  My house gets really hot in the summer (god i wish it was summer) and I found that putting my laptop on some books or something that takes the air vents off of the surface helps, then for extra fun i pointed a house fan (or 2) right at the sucker to move the hot air away from it.  You could do that if you need to do your doings right away and don't have time to wait for your laptop cooler to come via the lightning fast postal service -or- if you're feeling lucky (well punk?) you could dig around in your BIOS settings and possibly raise the shutoff temp of your motherboard to 70.

---

### Post by KCPokes on 2008-02-20
Does it actually get hot, meaning you can feel the hot air coming from the fan and the machine itself is hot to the touch?  I ask because I've had issues with the temperature on my laptop reporting it was running hot yet the air from the fan was cold.  The machine wasn't even warm.  I've done tests, rebooting back into Vista and running an Intel monitor and the CPU wasn't running any hotter then 40C, yet Gutsy would show it in the upper 60C range.  Of course yours may be a legitimate heat issue, but if not you may check out [http://ubuntuforums.org/showthread.php?t=539365](http://ubuntuforums.org/showthread.php?t=539365) .

---

### Post by motin on 2008-02-21
Hey big thanks for your replies!

I think I'll invest in one of them USB-powered coolers - not to keen on underclocking... 

Also after searching some more on the net I realized that 60-70 is a pretty average value actually. Although it doesn't hurt to stay cool... 

Cheers mates!

---

