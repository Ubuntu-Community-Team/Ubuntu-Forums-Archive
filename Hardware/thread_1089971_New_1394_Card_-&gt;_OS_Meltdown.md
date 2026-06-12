---
title: "New 1394 Card -&gt; OS Meltdown"
date: 2009-03-07
forum: Hardware
---

### Post by DrewT on 2009-03-07
I just installed a cheapie 1394/Firewire controller card (PCI) to replace the controller on the mainboard, which was apparently fried by a bad cable. My first attempt to boot hung for a very long time, and since I had something else to do I booted into WinXP, which seemed to see the controller fine. I rebooted and left the room, and when I returned the following message was scrolling endlessly:

> ohci1394: fw-host1: SelfID is inconsistent [0x00000000/0x00000000]

This was preceded by a (line?) number that was incrementing steadily upwards; otherwise the message was identical on every line. (And yes, the address or whatever was nothing but zeros, though I can't swear to how many.)

I tried rebooting into the recovery mode of my current kernel and it did the same thing. At this point I presume I need to boot from a CD, but I have no idea what to do once I've regained access to my system. I can take out the card, of course, if that's necessary.

Thanks in advance for any guidance ...

---

### Post by DrewT on 2009-03-08
bump

---

### Post by DrewT on 2009-03-08
Through sheer luck, it looks like I solved this one myself by enforced process of elimination. I couldn't boot from my install CD -- it stalled. So I went into my BIOS settings, since that was all I could get at. (This is on an ASUS M2N-SLI mainboard.) Following the most relevant menu selections (Advanced/PCIPnP), I came to the Plug & Play O/S option, which was set to No. I changed it to Yes. Voila, Intrepid booted normally.

---

### Post by DrewT on 2009-03-08
I would mark this "solved" but I don't see any command for it. Do people just edit the title by inserting "[Solved]"? Or can only administrators do it? Or ... ?

---

### Post by TheLions on 2009-03-08
...just edit title and add [SOLVED]

---

