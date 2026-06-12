---
title: "Network card sometimes is not detected"
date: 2012-11-11
forum: Hardware
---

### Post by El Potro on 2012-11-11
Hello guys,

I'm writing this message completely off-line (of course I'll upload it later while on-line). This happens every three, four reboots, and to be honest I don't have an idea of what might be causing it. Once I reboot, the eth0 connection activates normally and works fine. It's annoying and frustrating having to do this constantly every a few boots.

When off-line, in **nm-applet**, Enable Networking is ticked. In my connections I have only one eth0 configuration (which I created and configured manually). I have no chance of selecting it. Nm-applet says “No network devices available”.  

**ifconfig -a** shows only lo, eth0 is not on the list. It seems that the network card is being ignored randomly across reboots. Sometimes it isn't detected but if I reboot it's detected and working again.

I think maybe I screwed up some configuration files, or something happened. It's not likely that my network card is broken, because if that was so, it wouldn't work at all. I think this has to do with Ubuntu 12.04 and my particular installation.

Is there something I can do to solve this? I really don't want to re-install.

By the way, the on-board network card is Realtek RTL8101E/RTL8102E

Thank you very much.

---

### Post by El Potro on 2012-11-13
I need help people, please!

---

### Post by dannyboy79 on 2012-11-13
is this after suspend, sleep, or hibernate? CHeck your dmesg output when you notice the ethernet card is NOT detected. I have a similar problem with a wifi card not being able to be woken up after sleep. in dmesg it states "MAC address is in deep sleep" or something along those lines.

It turns out others are having a hell of a time with this chipset as well, see here: [http://ubuntuforums.org/showthread.php?t=1964200](http://ubuntuforums.org/showthread.php?t=1964200)

---

### Post by El Potro on 2012-12-14
Hello dannyboy79

This happens when I turn the computer on after a long time it was off. Once Ubuntu has booted I always face this problem. Rebooting it will solve it. But if I reboot a second time, I might lose the network again, or a third time, and the solution is again to reboot.

This is the dmesg that I see when I boot and the network doesn't work. There I can't see any reference to Ethernet, eth0, or anything.

Any help will be greatly appreciated.

---

### Post by Cheesehead on 2012-12-15
The dmesg from early boot [0.00] to [0.22] are missing from your posted file. That's the time when all the important hardware messages are, including messages that may indicate a PCI failure or IRQ conflict.

Your description seems to be an intermittent hardware failure. This could have many causes, including a dying NIC, a NIC loosely seated in it's slot, an IRQ conflict, and others.

Many of those causes will not be fixed by a reinstall or settings change.

I suggest you check your hardware and post that early dmesg. Those first steps will eliminate a lot of potential causes...and may foruitously even fix the problem.

---

### Post by El Potro on 2012-12-15
Hi Cheesehead,

Here is a full dmesg from a session without network. [http://pastebin.com/Jzq0qjFR](http://pastebin.com/Jzq0qjFR) 

Hardware (network cable & port) looks OK, and works OK too when it is detected. 

A remark: The network NEVER works the first time when you start the computer after it has been off for a long time. I tried this also with a different distribution that I have installed in my computer (Debian Squeeze) and it's exactly the same.

---

### Post by Cheesehead on 2012-12-16
That startup, the NIC is never detected. (It's not an IRQ conflict)
That means you have loose, dying, or defective hardware, not something Ubuntu can solve.

> **El Potro said:**
> The network NEVER works the first time when you start the computer after it has been off for a long time. I tried this also with a different distribution that I have installed in my computer (Debian Squeeze) and it's exactly the same.
This also indicates loose, dying, or defective hardware.

The most likely cause is a loosely-seated or defective/dying NIC. A less likely cause is a motherboard fault in the PCI controller. A dying power supply seems unlikely if this is the only symptom.

In the case:
Blow or gently vacuum out any dust. Look for excessive accumulations. Gently pull out the NIC from the PCI bus. Look for damage around the PCI bus connector, and for damage or burn marks on the card itself. Gently clean the contacts and reinstall the card.

If that doesn't fix the problem, then the next step is to replace the NIC.

---

