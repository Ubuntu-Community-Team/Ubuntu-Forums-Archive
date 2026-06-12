---
title: "Kernel panic during fresh install (8.10)"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by HangingOutWithJim on 2009-02-03
I've been trying to install Ubuntu 8.10 into my Fujitsu Amilo A 7620 laptop (2600+, 512 MB RAM, 40 GB HD). When using live CD, installer hangs completely either during disk partitioning or during actual installation progress usually at about 20-26%. Keyboard and mouse stop responding and CD spins down etc. so that I have to turn power off. 

I've run memtest and checked the CD, no errors found. I've also tried corresponding alternate install CD which hangs too. The error message it gives is "kernel panic - not syncing : attempted to kill idle task".

Closest similar problem I found on this board was [in this thread]("http://ubuntuforums.org/showthread.php?t=770575&highlight=kernel+panic%26quot%3B+%26quot%3Bidle+task") and I tried workarounds suggested there but they didn't work either.

---

### Post by dstew on 2009-02-03
Kernel panic means the linux kernel was unable to run on your hardware. There can be many reasons for this. It is the final common pathway for all fatal errors, so just knowing there was kernel panic does not tell us much. You need to look at the kernel errors before the kernel panic message.

It is easier to see the errors if you boot the Live CD with an edited kernel line. You can edit the line by pressing F6. Remove "quiet splash" from the line, press 'enter' to boot. If you can see some of the errors before the kernel panic, you might be able to narrow it down some, and get a better google search on the error. Often you can add parameters to the kernel line to get a boot, once you have some idea what the problem is.

---

### Post by HangingOutWithJim on 2009-02-05
Well, I finally managed to install Ubuntu. Actually there were two problems: first one apparently had something to do with ACPI. The reason I didn't give more information about the crash was because I couldn't see what exactly caused it. The computer just vomited a long stack trace and after that printed kernel panic message with some hex numbers. However, I could see some references to functions with word "acpi" on the stack trace and figured out that this would cause the crashes. Installing with acpi=off (or whatever it was) solved the "attempted to kill idle task" problem. 

Second and more serious problem was (and still is) causing kernel panics. It was apparently DVD drive's fault and has something to do with dma. The installer would hang and print kernel panic message "Fatal exception in interrupt". Luckily installing was successful after I tried it with ACPI disabled and using workaround I found from that other thread.

However, I have problems with my DVD drive again. If I try to watch DVD (or do something similar which transfers lots of data from drive), it hangs my system just like during installation with that same kernel panic message "Fatal exception in interrupt". I can work this around by putting line 'options libata dma=0' into /etc/modprobe.d/options and running update-initramfs -u. But if I do this, I cannot anymore watch DVDs! System won't crash, but Totem Movie player just freezes.

I'm really getting fed up with this thing. I imagined that this would be easy-to-use and good alternative to Windows but so far I've encountered only problems after problems.

---

