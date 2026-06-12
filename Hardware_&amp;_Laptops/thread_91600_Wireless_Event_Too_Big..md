---
title: "Wireless Event Too Big."
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by trivialpackets on 2005-11-17
I've been having issues since the beta testing with wireless event too big error on bootup causing a kernel panic.  It works fine when I'm at home, and there is one source generating one ESSID.  But when I'm on campus, I have like 6 sources, all broadcasting the same ESSID, and I'm assuming that is what is causing the issue.  Does anyone have any ideas as to how to resolve this issue, as it is annoying at least, and makes me miss Suse, as this was not an issue, but I really prefer Ubuntu/Kubuntu.

---

### Post by trivialpackets on 2005-11-21
Anyone else experience this or have any ideas?

---

### Post by hw-tph on 2005-11-21
How is your wireless device configured? What driver do you use? Do you use a real driver or ndiswrapper (or similar NDIS driver wrapper)? These are prone to generate weird errors and you should really use a real driver if accessible (also consider buying hardware after how well it is supported).

What other messages surround the "wireless event too big" error in the log?


Håkan

---

### Post by trivialpackets on 2005-11-21
I'll look into it when I get home, however as stated, this is the first distro, previous as well where ndiswrapper has ever caused an issue, and all distros use it with my card.  As to hardware, too late for that and I can't afford a new card.  In any case, I'll look into this as soon as I get home.

---

### Post by trivialpackets on 2005-11-23
With respect to the log, I'm not sure as of right this moment, however I will look into it as I'm not on campus for a few days.  But the issue is still standing as far as I know.  The driver I use is the bcmwl5.inf driver for my broadcom wireless.  It worked fine in Hoary, but is frankly the only problem I have right now beyond my splash screen prematurely turning back to text, but this is more than cosmetic.

---

### Post by dangermouse28 on 2006-01-13
Had exactly same problem - fixed by removing the ndiswrapper supplied with badger and installing ndiswrapper-1.7 from source. Now - if only I could get usplash working again....

---

### Post by sopordave on 2006-03-23
I'm having the same problem with the same situation (multiple same-named APs), with the same driver (bcmwl5.inf + ndiswrapper).

Anybody have a quick fix for this?

I also get the occasional error saying that there aren't any IPv6 APs in the area, which isn't true.  I'm not sure what the pattern to this messed is, though;  it seems to randomly pop up (it will even connect to an IPv6 AP, then when I came back to the same area later that day the warning popped up).

---

### Post by davidfdr on 2006-05-02
[QUOTE=sopordave]I'm having the same problem with the same situation (multiple same-named APs), with the same driver (bcmwl5.inf + ndiswrapper).

Anybody have a quick fix for this?

I also get the occasional error saying that there aren't any IPv6 APs in the area, which isn't true.  I'm not sure what the pattern to this messed is, though;  it seems to randomly pop up (it will even connect to an IPv6 AP, then when I came back to the same area later that day the warning popped up).[/QUOTE]

I having this same problem with this same driver. HP L2000 AMD64 Lance Amstrong.

But my note is halting when I turn on the wireless network...

---

