---
title: "HP LaserJet 1018 not working"
date: 2011-04-20
forum: Hardware
---

### Post by Ghostlove on 2011-04-20
As the title says, my HP LaserJet 1018 is not working. It's not even being recognised by my computer. I've tried it in two different USB slots but it's still not working. Funnily enough, if I leave it plugged in, the computer won't start. Could it be something wrong with the cable, or is there some magic fix that will make it work? I really, really need to print an important document. Thanks in advance for any help. :)

---

### Post by dandnsmith on 2011-04-21
Some more detail might be helpful (both to you and us).
1. Has it ever worked (a) on this PC (b) anywhere?
2. Have you set up the printing?
3. Was the printer on the PC when you installed Ubuntu?
4. which version of Ubuntu are you using?

Comment: PC may not start with printer plugged in because the drain on USB at the start is too great (well known problem). Plugging into a self-powered hub might help (or might stop printer recognition). On the whole HP printers seem to be well coped with by Ubuntu.

---

### Post by Ghostlove on 2011-04-24
1. Has it ever worked (a) on this PC (b) anywhere?

Yes, on this PC on a previous incarnation of exactly the same operating system.

2. Have you set up the printing?

Um... I don't know? It just plugged and played before.

3. Was the printer on the PC when you installed Ubuntu?

I believe so but I'm not completely sure.

4. which version of Ubuntu are you using?

Maverick 64-bit.

My USB hub is self-powered (I assume by that you mean it has a mains plug) and it still does the same thing.

---

### Post by dandnsmith on 2011-04-25
That's rather a lot of 'don't knows' to be reasonably sure what's going on.

If it still stops the PC starting when plugged in via a self-powered hub, then you'd do well to suspect cable/printer.

Next on my (personal) list to suspect would be
- 10.10 which is significantly different from 10.04 and previous
- 64 bit, as there seem to be some problems between drivers originally for 32 bit

I'd also be looking to see just what has been set up for printing - I think the default would be CUPS, but haven't had a lot of trouble-shooting to do so far in this area (it's ben mostly sorting out default printer model and size of paper defaults.

Derek

---

### Post by Ghostlove on 2011-04-25
> **dandnsmith said:**
> That's rather a lot of 'don't knows' to be reasonably sure what's going on.

If it still stops the PC starting when plugged in via a self-powered hub, then you'd do well to suspect cable/printer.

Next on my (personal) list to suspect would be
- 10.10 which is significantly different from 10.04 and previous
- 64 bit, as there seem to be some problems between drivers originally for 32 bit

I'd also be looking to see just what has been set up for printing - I think the default would be CUPS, but haven't had a lot of trouble-shooting to do so far in this area (it's ben mostly sorting out default printer model and size of paper defaults.

Derek

I'll try to get hold of a different cable to see if that's the culprit. I was just using it in 10.10 a few weeks ago. And let's assume I'm totally daft - how would I look into what's been set up for printing?

---

