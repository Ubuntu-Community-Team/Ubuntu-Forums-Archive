---
title: "Canon ir2525"
date: 2013-11-07
forum: Hardware
---

### Post by Chris_Banakis on 2013-11-07
Trying to get this printer working ASAP (I have a report I need to print)

Canon ir2525 (Network Printer)
Ubuntu 12.04 64bit

I had this working a long time ago. (In 12.04 64bit)

Then I upgraded to 12.10 and had some un-related problems.

Just backed up all my files, and did a clean install back to 12.04.

Followed the same methods as last time, but now it wont work.

I have the correct drivers that I used originally.

Everything installs fine.

But when I print, nothing happens.

Says printed successfully, but nothing prints.

Not sure what could have changed.

Please,if you have any idea on how to troubleshoot this...

Thanks

---

### Post by farrinux on 2013-11-09
When you say nothing prints, does this mean that the printer operated and just spit out a blank page or does it mean it did not make a sound?  No movement no operation nothing?  If the printer spit out a blank page I would suspect your ink cartridges and or print head.  I recently had a Canon i850 that spit out blank text pages.  The problem was the black ink print head was clogged with dry ink.

---

### Post by Chris_Banakis on 2013-11-11
> **farrinux said:**
> When you say nothing prints, does this mean that the printer operated and just spit out a blank page or does it mean it did not make a sound?  No movement no operation nothing?  If the printer spit out a blank page I would suspect your ink cartridges and or print head.  I recently had a Canon i850 that spit out blank text pages.  The problem was the black ink print head was clogged with dry ink.

Nothing happens.

The printer does not react to me printing.

There is nothing wrong with the printer though.

I was using Ubuntu 12.10 printing whenever I needed to.

Reverted back to Ubuntu 12.04 via clean install.

Installed the same driver, the same way as I did when I was using 12.04 the first time.  (I took notes last time)

And for some reason, the result this time, is not the same.

---

### Post by Chris_Banakis on 2013-11-20
I got it working again.

Instead of installing the driver like I did last time, I added this ppa
[http://ppa.launchpad.net/auanswers/canon64/ubuntu](http://ppa.launchpad.net/auanswers/canon64/ubuntu)

Seemed to solve it

---

