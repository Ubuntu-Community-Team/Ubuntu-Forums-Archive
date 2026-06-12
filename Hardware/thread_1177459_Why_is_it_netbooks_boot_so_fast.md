---
title: "Why is it netbooks boot so fast?"
date: 2009-06-03
forum: Hardware
---

### Post by weeman7007 on 2009-06-03
I was wondering why it is a Linux netbook using an intel atom processor can boot in 5 seconds, but yet it takes more powerful systems 4 or 5 times as long?

---

### Post by Teutorix on 2009-06-03
Thats quite odd, Im no expert but my guess is magic. :p

Nah but seriously, it could be just the way that they are put together or something makes them more efficient.

---

### Post by weeman7007 on 2009-06-03
i think you could be right lol

---

### Post by mcduck on 2009-06-03
SSD hardrives used in many netbooks have really fast random data access, which gives a noticeable performance boost when starting operating systems (or loading any program that depends on large amounts of small files scattered around the disk).

Booting operating system isn't really about raw processing power, simply loading all required stuff from disk to RAM as quickly as possible.

---

### Post by weeman7007 on 2009-06-03
well the thing is that i have an OCZ 30gb ssd and it still takes me 24 seconds from grub to having desktop loaded (auto logon)

---

### Post by mcduck on 2009-06-03
> **weeman7007 said:**
> well the thing is that i have an OCZ 30gb ssd and it still takes me 24 seconds from grub to having desktop loaded (auto logon)

Not all SSD drives are that great. Also many netbooks run a bit more lightweight setup that what the normal Ubuntu desktop version is.

Anyway, you might want to read this great article about SSD drives (I found it from Linus Torvalds' blog :)): [http://www.anandtech.com/storage/showdoc.aspx?i=3531]("http://www.anandtech.com/storage/showdoc.aspx?i=3531")

If you want to know what's taking the time when loading the OS, you could install bootchart package, it will generate a graphical representation of what's going on when the system is booting. (you'll find the images in /var/log/bootchart)

Edit: If it takes your system 24 seconds to boot your SSD drive might not be one of the good ones, or there's something else that's not optimal on your system. My 3-years old laptop with very slow (5400rpm) hard drive boots in 24 seconds, disk throughput being the biggest bottleneck.

---

### Post by duckfeet on 2009-06-03
Bummer: After this thread, I know some of us are now looking at our little netbooks when they boot up, and muttering: "Come on slowpoke, yer 5 seconds are *up*!  All the other netbooks would be booted up by now...get a move on!"  ;)

---

### Post by Teutorix on 2009-06-03
i have a shitty old desktop and it boots in about that time to desktop

25secs btw, not 5 XD

windows XP used to take a century to boot

---

### Post by snowpine on 2009-06-03
> **weeman7007 said:**
> I was wondering why it is a Linux netbook using an intel atom processor can boot in 5 seconds, but yet it takes more powerful systems 4 or 5 times as long?

Wow, which netbook and operating system are you using for 5 second boot time??

---

### Post by ddrichardson on 2009-06-03
> **snowpine said:**
> Wow, which netbook and operating system are you using for 5 second boot time??
I was wondering that.  I have an Aspire One running Arch with only the required daemons and kernel modules optimised for the Atom and it's quick but not five seconds.

Part of me wonders if this is resume, if not I'd love to know.

One thing that hasn't been mentioned about netbooks is their BIOS boot time is faster. Percentage wise how much difference that makes I wouldn't think by much.

---

### Post by mcduck on 2009-06-03
> **ddrichardson said:**
> I was wondering that.  I have an Aspire One running Arch with only the required daemons and kernel modules optimised for the Atom and it's quick but not five seconds.

Part of me wonders if this is resume, if not I'd love to know.

One thing that hasn't been mentioned about netbooks is their BIOS boot time is faster. Percentage wise how much difference that makes I wouldn't think by much.

Could make quite a difference, if we really are talking boot times around 5 seconds. All my computer take almost that long to POST & load Grub :)

---

