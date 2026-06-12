---
title: "No Sound on Thinkpad 600 PII 300 MHZ"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by caulktel on 2005-05-02
Hi, I just installed Kubuntu 5.04 on my ThinkPad 600. Everything seems to be working great after I fought with getting the Xserver configured properly, but the sound. I have tried a few things that I found here and there including insmod, it doesn't show any sound modules loaded at all. I also tried:
/sbin/modprobe snd-cs4236 index=0 port=0x530 cport=0x538 irq=5 dma1=1 dma2=0 isapnp=0 , but that says that it can't find that module. Does anybody have any ideas on how to get this working? I read somewhere that the sound card in the 600 is a isa card and not a pci, so maybe that has something to do with it. Also when I type alsaconf it says that it can't find that command, isn't Alsa loaded at bootup?

---

### Post by ernestoongaro on 2005-05-03
I have a IBM 600x and my sound also did not work, it was an IRQ issue, I fixed it lazily by turning acpi off. Do this during grub (press E i think) and add the line acpi=off, after that if it works then add it to your grub config file. Good Luck, PS - Let me in on any Thinkpad secerets you might run into

---

### Post by caulktel on 2005-05-04
No takers!

---

### Post by caulktel on 2005-05-08
Well,
I installed Slackware 10.1 and then ran alsaconf, it found my sound and configured it fine. So for now I will stay with Slack, but will try back when the next release comes which is suppossed to work better with laptops. All in all though, I really liked Kubuntu. Keep up the good work.

---

### Post by dusty on 2005-07-23
ad the line where?

---

### Post by poptones on 2005-07-23
The thinkpad 600(e) needs to be configured to allow certain onboard features to work properly with linux. It takes a little fiddling, but I found it pretty easy to do using a boot CD with the config program burned to it.

[http://panopticon.csustan.edu/thood/tp600lnx.htm](http://panopticon.csustan.edu/thood/tp600lnx.htm)

---

