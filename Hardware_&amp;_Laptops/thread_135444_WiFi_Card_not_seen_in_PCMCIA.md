---
title: "WiFi Card not seen in PCMCIA"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by stephsully on 2006-02-23
This is a weird problem that's happening to me. My d-link DWL-G630 used to work fine in ubuntu. It was seen fine and worked normally. Then after a reboot, it just stopped working at all, I couldn't even see the card using lspci it just comes up as my TI cardbus with no other identifying info. And when I do ident or info, it just comes up blank with no manufacturer or chipset info. The weird part is that the card works fine in other computers and also works when i use it in windows xp (dual boot). My other PCMCIA cards work and are seen fine in linux, so I don't think it's a problem with my pcmcia adapter. 

I'm really confused what the problem is and being a bit of a linux newbie I don't know how to go any further in my troubleshooting. The only thing that I can think of that changed was I was having a problem with the double (time) clock speed problem.  I updated my bios because Compaq had a new one which addressed the issue and it fixed the problem. I have a compaq M2105US. If anyone can be of help I would appreciate it. 

Thanks in advance.

---

### Post by stephsully on 2006-02-23
Okay so I think I might have found what the problem is. I'll have to check it out later. Here's the info in case anyone else has the same problem, and I'll let everyone know if it works. 
_______________________________________________________________

After I updated the bios, it must've screwed something up.
CardBus (sometimes also PCMCIA) cards not found

On several, especially new systems the Yenta bridge is not on the root PCI bridge, but behind a PCI-to-PCI bridge. On some x86 or x86_64 systems, these bridges aren't corrreclty set up by the BIOS, which may cause CardBus and even PCMCIA devices not to show up in lspci or in pccardctl ident correctly. If you suspect that this may be the cause, issue this command:


	lspci -v | grep subordinate
	

Its result may be like this:


        Bus: primary=00, secondary=02, subordinate=04, sec-latency=64
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
	

Let's decode the first line: bus 0 (primary) is bridged to busses 2 (secondary) to 4 (subordinate) by a bridge. The second and the third line state that bus 2 is bridged to busses 3-6, and 7-10. However, the CPU (which itself is connected to bus 0 through the root bridge) needs to be able to access all these busses. If you try to walk the tree to bus 7, for example, you see that the CPU can't get there, as bus 0 is only bridged to busses 2 to 4.

If this is the case, or you find a message stating "try pci=assign-busses" in the dmesg log, append the following to the kernel boot line:


	pci=assign-busses
[http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html#knownproblems]("http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html#knownproblems")

Here's another person who seemed to have the same problem and it worked for him.
[http://ubuntuforums.org/showthread.php?t=129462]("http://ubuntuforums.org/showthread.php?t=129462")

I'll keep everyone updated on this.

---

### Post by K.Mandla on 2006-02-23
If the *assign-busses* trick doesn't work, you might want to check this thread (of course, you probably have already seen it). ...

[http://ubuntuforums.org/showthread.php?t=125334](http://ubuntuforums.org/showthread.php?t=125334)

Depending on how old your laptop is, it might need the 2.4.__ kernel to read the PCMCIA slots. Hoary is 2.4.27, I believe.

---

### Post by stephsully on 2006-02-24
Thanks, K.Mandla, but I got it to work using the pci=assign-busses. So i guess the best way to solve a problem is to post it here and then you'll find the answer 15 minutes later (and feel kinda sheepish about it)

Anyway, it's my understanding that this issue is getting resolved in the next kernel.

---

