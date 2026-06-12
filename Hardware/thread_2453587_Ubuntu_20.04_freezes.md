---
title: "Ubuntu 20.04 freezes"
date: 2020-11-13
forum: Hardware
---

### Post by mizurdiaga on 2020-11-13
My laptop (Dell xps 13 7390) randomly freezes with Ubuntu 20.04. I bought it with Ubuntu 18.04, I upgraded to 20.04 (fresh install), and it has been working fine. But since two weeks ago, it randomly freezes. Sometimes, it happens when I plug in the ac adapter. Any suggestions to how to fix it?

Thanks!

---

### Post by TheFu on 2020-11-13
Freezes are generally caused by one of these issues:
[LIST=1]
[*]some hardware fault
[*]out of RAM situations
[*]kernel issue
[/LIST]

Hardware issues sould be oanounced in te system logs.  heck those for erros and warnings. Google can find a guide.

Low RAM is easy to see.  Use **top** and **free -hm**. If available swap goes below 256 MB, you have a low RAM issue. Buy more ram or increase swap or close programs to free memory.

To test a kernel issue, boot using an older kernel. On the grub boot page, choose "Advanced" then pick an older kernel.  Does it freeze still?

If none of these things help, check the ram for issues. In the advanced grub boot, there should be a memtest option. Run that overnight.

---

### Post by mizurdiaga on 2020-11-13
Thank you very much for your message. First, I do not think so that it is a hardware problem, since I made a run the diagnosis tool the computer has. Second, the computer has 16Gb of RAM and, in system monitor app, the usage is around 25%. I will check the kernel, as you suggest.

---

### Post by mizurdiaga on 2020-11-17
More information: When trying to close ubuntu, I sometimes get the message you can see in the attached image, and the computer freezes. Any suggestions?

---

### Post by mizurdiaga on 2020-11-20
It seems that the problem is caused by a dock which I use to connect an external monitor. I've changed the USB-C port an the laptop has not frozen since then.

---

