---
title: "Hibernate wakeup freeze @ thinkpad t440s"
date: 2015-10-02
forum: Hardware
---

### Post by randomuser2 on 2015-10-02
Hello,
I'm using Ubuntu 15.04 x64.
Laptop is not waking up after hibernate, it's showing percents in console during wake up (like 10%, 20%, ...100%) and freezes.

P.S.
I have [http://www.thinkwiki.org/wiki/Thinkpad-acpi](http://www.thinkwiki.org/wiki/Thinkpad-acpi) and TLP installed.
A couple of times it restored after hibernate, but after - no success.

Syslog: [http://pastebin.com/2RfD0pTF](http://pastebin.com/2RfD0pTF)

---

### Post by tgalati4 on 2015-10-02
Install *acpitool* and examine what parts of the PCI bus have power during hibernation:

```
sudo apt-get install acpitool
acpitool -w
```

Use the -W switch to turn on parts of the bus.  Turn everything on, then selective turn off parts until you get reliable hibernation behavior.

Does sleep work?

```
sudo pm-suspend
```

---

### Post by randomuser2 on 2015-10-03
> **tgalati4 said:**
> 
Does sleep work?


Yes, it works.

> **tgalati4 said:**
> 
Install *acpitool* and examine what parts of the PCI bus have power during hibernation:


```

oops@oops-laptop ~> acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. LID      S4    *enabled   platform:PNP0C0D:00
  2. SLPB      S3    *enabled   platform:PNP0C0E:00
  3. IGBE      S4    *disabled  pci:0000:00:19.0
  4. EXP2      S4    *disabled  pci:0000:00:1c.1
  5. XHCI      S3    *enabled   pci:0000:00:14.0
  6. EHC1      S3    *enabled   pci:0000:00:1d.0

```

This output is showing after wakeup, then freezes.
[http://imgur.com/FUR7LSE](http://imgur.com/FUR7LSE)

---

### Post by tgalati4 on 2015-10-03
So PCI slot numbers 3 and 4 are turned off during S4 (hibernate) sleep.  Try turning them on:

```
sudo apcitool -W 3
sudo apcitool -W 4
acpitool -w
```

Now try to hibernate:

```
sudo pm-hibernate
```

If it doesn't wake properly, then try the quirks:

```
man pm-hibernate
```

Try each quirk separately and take notes.  You only need to find one working configuration.

Your screen shot doesn't reveal the problem.  It shows that it successfully loads the RAM snapshot (3.4 GB in 4.6 seconds) but then freezes.  Look through the /var/log files (pm-suspend.log and pm-hibernate.log).

Personally, I find that hibernate takes just as long as a cold boot, so I don't use it.  I use sleep or cold shutdown.  To me, the only Use Case for hibernate is if you have 8 workspaces and applications open in each of them, and they are sized and placed the way you want them, then hibernate will keep all of that configuration intact.  Otherwise, you risk losing data if you just sleep and have a power outage.  Hibernate saves some power, because the computer turns off completely, but again it's not any faster than a cold boot.

I just did a test.  When I performed a hibernate, it took about a minute to write to disk and hibernate.  It took 3 minutes to wake up completely.  Now, I have a 2 GB RAM laptop, with 1.6 GB of swap in use (many, many tabs open in Chrome), so the stale pages of swap had to be dumped, then the 2 GB snapshot written to swap.  Upon waking, the RAM image is read, but then the cache pages need to reloaded.  I can do a full boot in 2 minutes typically.  

Sleep is only 12 seconds power down, and 8 seconds to wake to full functionality.  So, I use sleep.

---

