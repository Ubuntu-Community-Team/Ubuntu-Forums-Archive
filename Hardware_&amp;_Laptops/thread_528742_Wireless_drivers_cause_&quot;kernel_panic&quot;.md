---
title: "Wireless drivers cause &quot;kernel panic&quot;"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by Murrquan on 2007-08-18
Hi, all. I recently switched to an XP / Ubuntu dual-boot setup. Before that I was using Fedora 7 for a couple of months.

My notebook computer has an "SiS 900 PCI Fast Ethernet" wireless card, according to Device Manager, the Windows drivers for which XP said were made by Ralink. Last time (i.e. Fedora 7), I downloaded the Linux drivers [here.]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads") Unfortunately, I don't remember which one I used last time, and I think the options may have changed since then.

This time I used the rt2400 drivers they listed there. There are two problems, however.

**One is that they're not working.** A friend of mine walked me through some very complicated setup procedures via instant messaging. Unfortunately I don't understand what all he did, though if needed I can go through the chat logs and tell you what specific commands he used and the output he received. In the end, it finally showed our home wireless network at 50% signal strength, but I wasn't able to connect to it; and when I restarted my computer, it'd be down at 0% again. Repeat every time that we've tried this.

**Two is that they cause kernel panic.** I posted a thread earlier about this, asking for help on the newbie boards. They told me to remove my notebook computer's batteries. So far that's worked, but my PC still keeps locking up. I asked the aforementioned friend about it, and he says it's due to the drivers' messed up kernelspace code.

On Fedora 7 it worked fine -- whichever driver I was using, that is. At one point it went out for a few days, for no apparent reason, but then it came back better than ever with a rock-solid connection. I think that may have been around the time of the last kernel update.

So. I'm not sure what to do, but I have a few ideas in mind.

**1. Remove the drivers I installed.** I want to do this immediately, to stop further lockups. Unfortunately, I don't know how to do this, as they aren't listed in Add/Remove Programs or Synaptic Package Manager. (Maybe I should be posting on the beginners' forum. ^.^; )

**2. Install working drivers.** Or at least, experiment with the ones posted there and see if I can find one that works better, and/or replicate the success I had with Fedora.

So my questions are, how do I do the former, and is there anything that would prevent me from doing the latter? Is this course of action going to solve my problems? Is there anything else I should be aware of, or any more information I need to provide?

Many thanks for the assistance, and I'm sorry to trouble you. *bow*

---

### Post by Murrquan on 2007-08-18
**Update:** Synaptic Package Manager does, in fact, list a bunch of rt2xx drivers available for install. I did things manually, though, so I'm not sure how to uninstall the ones I have now -- none of the boxes are checked, so I can't tell Synaptic to uninstall them. I also don't know which drivers are right for my system, or how to determine that.

---

