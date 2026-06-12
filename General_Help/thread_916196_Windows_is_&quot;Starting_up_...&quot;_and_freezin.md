---
title: "Windows is &quot;Starting up ...&quot; and freezing"
date: 2008-09-10
forum: General Help
---

### Post by poosenki on 2008-09-10
I don't know what exactly has happened, but all of a sudden, I can't boot into Windows XP any more. When I choose the option, it shows the "Starting up ..." text, and then it's just a blinking cursor. I tried using the XP CD to run fixboot and fixmbr, but nothing changed (Except that it no longer says "Starting up", it just is the flashing cursor, but that's because Grub was wiped out).

I ran chkdsk, it said things were fine and it didn't need to be run, but I forced it and it said there were one or more problems. Could that be the root of this? It didn't tell me anything about those problems, it just ended after that.

I recently before this had a problem where right after selected Windows from Grub it would tell me a disk read error had occurred and the only way to solve it was to reinstall Windows. I had Ubuntu and Windows running happily together for about three months, and now it keep running into issues. I really don't intend to get into the habit of reinstalling Windows because I definitely don't think that's the problem since it ran happily by itself for about 3 years.

Anyway, any sort of help would be very much appreciated. Thank you very much in advance.

---

### Post by Predator106 on 2008-09-10
Check in your BIOS to see if your HDD is still there :) It could have died, or maybe a cable came undone.

Well I've had the same problem before, except it wasn't out of nowhere, it was when I was first setting Ubuntu up, and it was pointing to the wrong hard drive/partition, effectively trying to start up a hard drive that didn't have a MBR on it. The read error, that was because of the command that grub was using, I had to modify the commands a little bit, add one remove 2 I think. And then it worked, I could tell you what they were if you want, but since you said nothing changed, it doesn't make sense that it isn't working now.

---

