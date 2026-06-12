---
title: "&quot;Force&quot; boot"
date: 2010-07-03
forum: Hardware
---

### Post by akoskm on 2010-07-03
Hi!

On my Laptop (MSI 670X, Ubuntu 10.04 LTS - Lucid Lynx) after turning it on, all I get is black screen. The display won't turn on, I need to hold the power button to force-shut down.
After the next try it's starting "normally". I see the BIOS screen and after a few second - when the booting is finished - the nvidia drivers logo. There is no loading screen while it's booting.
It's very annoiyng because every time I need two times to start my laptop. :D

Any suggestions are greatly appreciated!

---

### Post by robsoles on 2010-07-03
It almost sounds like a hardware/BIOS problem to me - "nVidia drivers logo" is something I just don't see after BIOS has finished doing it's thing and the boot-up show is handed over to GRUB2, which in turn pulls in my lovely Lucid OS and I am offered a login screen with my (user)name on it!

Does lappie have a CD/DVD ROM tray? If so can you go into BIOS settings and make boot order so it will try CD/DVD ROM first and then move on - that way we can find out whether or not I am right that it is your hardware/BIOS and not LTS at all!

An alternative, if you don't have an internal CD/DVD ROM tray is to plug in an external one and then don't put a bootable disc in it - Also, jumping into BIOS and selecting 'Load failsafe defaults' may be helpful.

Do you know how to get into BIOS on this system? It's DEL key during P(ower) O(n) S(elf) T(est) on many systems and on others it is F2 key - during POST is usually a message displayed saying what the key is to enter BIOS!

---

### Post by akoskm on 2010-07-05
Thank you for your reply!
I'll try to describe the boot process of my laptop more precisely:
1. Boot - every time fails, there is no POST screen, need to force - shut down.
2. Boot again.
 2.1 MSI logo instead of the default BIOS screen, with the instructions how to enter to the setup, boot menu, BIOS is doing it's job, etc... after 5 sec.:
 2.2 There is no GRUB - i have no other operating systems installed - and there is no booting screen while Ubuntu is booting, just a "_" character in the top left corner... after 20 sec.:
 2.3 The nVidia logo.
 2.4 GNOME Desktop - autologin.

Yes, my laptop have CD/DVD tray, and this option is at the end of the boot order list.

---

### Post by wilee-nilee on 2010-07-05
There are key prompts for various functions after the bios prompt. A prompt for choice of boot from that is usually a f key, or esc, depends on the computer. Also a grub prompt, shift I think, to get the grub menu. Get the boot prompt figured out and see if the computer will boot from a live Ubuntu cd, to see if it is a hardware problem, or just a graphic driver problem. Any of the key prompts are run from power on to reach them including a bios access key.

---

### Post by akoskm on 2010-07-12
> **wilee-nilee said:**
> There are key prompts for various functions after the bios prompt. A prompt for choice of boot from that is usually a f key, or esc, depends on the computer. Also a grub prompt, shift I think, to get the grub menu. Get the boot prompt figured out and see if the computer will boot from a live Ubuntu cd, to see if it is a hardware problem, or just a graphic driver problem. Any of the key prompts are run from power on to reach them including a bios access key.

I did a reinstall, and nothing changed. Still need two power-on to start my laptop.
If it's a hardware problem, how can I detect which hardware is causing it?

---

### Post by robsoles on 2010-07-12
If you can't just pick it by watching it and you are not advanced enough to disassemble the machine and test parts independently then detecting what the problem is will be unlikely.


Can you change boot order? Please change it to have DVD/CD ROM tried first but don't insert a disc! Post back what it does then, one of us might be able to pick it from that.

---

### Post by akoskm on 2010-07-13
It's a laptop so I can't test parts independently.
I changed the boot order from Hard Drive, CD/DVD, NVIDIA Booting Agent to CD/DVD, Hard Drive, NV B. A. and nothing changed regarding to the boot procedure - described in my 2nd post.

---

### Post by robsoles on 2010-07-13
> **akoskm said:**
> It's a laptop so I can't test parts independently.
I changed the boot order from Hard Drive, CD/DVD, NVIDIA Booting Agent to CD/DVD, Hard Drive, NV B. A. and nothing changed regarding to the boot procedure - described in my 2nd post.

I've been aware it was a laptop since your first post.

Being a laptop only makes it only ''so'' much trickier to test parts independently if you are advanced enough to disassemble it - It is easier in modern laptops because they (more often) use SATA drives (meaning can be tested in PC and vice-versa) and at worst case scenario (as home user without other laptop machines) RAM and peripherals can be taken to a shop for testing at nominal fees (relying on access to a good shop though!!)


OK, setup an alternative operating system (yep, I'm talking crap like Windows) to see if it is an OS based problem or a hardware based problem - then when proven it is hardware save up some pennies and take it to shop....

Prove it isn't hardware somehow coz problem seriously sounds like hardware to me!

---

### Post by akoskm on 2010-07-25
I tried to start it with an Ubuntu Live-CD, it was successful - after the 2. boot -, but after rebooting from the live CD my laptop halted again.

Here is a part of my "messages" log maybe it means something:
```

Jul 25 16:07:50 akoskm-laptop kernel: [    2.697101] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 25 16:07:50 akoskm-laptop kernel: [    2.982551] ata2: SATA link down (SStatus 0 SControl 300)
Jul 25 16:07:50 akoskm-laptop kernel: [    3.094585] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jul 25 16:07:50 akoskm-laptop kernel: [    3.144361] ata4.00: ATAPI: Optiarc DVD RW AD-7530A, EX32, max UDMA/33
Jul 25 16:07:50 akoskm-laptop kernel: [    3.160307] ata4.00: configured for UDMA/33
Jul 25 16:07:50 akoskm-laptop kernel: [    3.162168] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EX32 PQ: 0 ANSI: 5
Jul 25 16:07:50 akoskm-laptop kernel: [    3.171570] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 25 16:07:50 akoskm-laptop kernel: [    3.171584] Uniform CD-ROM driver Revision: 3.20
Jul 25 16:07:50 akoskm-laptop kernel: [    3.171788] sr 3:0:0:0: Attached scsi generic sg1 type 5
Jul 25 16:07:50 akoskm-laptop kernel: [    3.490568] ata6: SATA link down (SStatus 0 SControl 300)

```.
Of course this log message is generated after booting twice like usual.
Regarding to the log message it seems to be my HDs fault ?

---

### Post by robsoles on 2010-07-25
a decent experiment with the log file would be;

From completely off, look at the time on a watch that matched the system previously, try to start the laptop and leave it trying to start for 2 mins -
look at the time on your watch again, do the restart procedure you are used to -

Check log entries - just one log entry from the time of the first start attempt and it just maybe software, not one log entry from about the time of the first/cold start attempt and it is getting clearer and clearer to be a hardware issue that is pointless to pursue in this way.

---

### Post by akoskm on 2010-07-26
I did the following:
10:40 Shut Down
10:42 First attempt to boot - failed
10:44 Second attempt to boot - successful

Nothing registered in the logs from 10:40 to 10:44.
The last message from 10:40 was
```
Jul 26 10:40:50 akoskm-laptop kernel: Kernel logging (proc) stopped.
```,
and the next one begins at ~10:44
```

Jul 26 10:44:23 akoskm-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.

```.
I searched for log entries in all log files represented in the Log File Viewer which contains the pattern " 10:4", but there is no event registered in the (10:40, 10:44) interval.
Here is one part of the log message after my first successful boot (10:44):
[http://pastebin.com/LcW1NZ7G]("http://pastebin.com/LcW1NZ7G").

---

### Post by robsoles on 2010-07-26
OK, I read as much of your log entries as I could stand - to be honest not a great deal - tried grep'ing for 'error', 'failed', 'failure' and 'stopped' and didn't get any decent hits within.

I re-read this thread - that was easier than reading the whole log by far! :)


Would you please try the following three items out a bit each:

(1) Set BIOS defaults / failsafe defaults and try booting like that - I didn't spot the indication you followed that piece of my advice previously.

(2) Try booting off the LiveCD a few times from cold/powered off.

(3) If #2 fails in similar way then please make a USB/Flash stick bootable using "System"->"Administration"->"Startup Disk Creator" and the LiveCD iso and try booting off that a few times running.


I can't diagnose your hardware from here like this - I could only physically test so much about it if I did have direct access before I'd have to go to a shop for more support as it is. Can check if HDD is SATA connection and try an alternative SATA HDD in the lappie?

---

### Post by akoskm on 2010-07-26
> **robsoles said:**
> OK, I read as much of your log entries as I could stand - to be honest not a great deal - tried grep'ing for 'error', 'failed', 'failure' and 'stopped' and didn't get any decent hits within.

I re-read this thread - that was easier than reading the whole log by far! :)


Would you please try the following three items out a bit each:

(1) Set BIOS defaults / failsafe defaults and try booting like that - I didn't spot the indication you followed that piece of my advice previously.

I already set the BIOS options to setup defaults - I forget to mention that one - without any success.

> **robsoles said:**
> 
(2) Try booting off the LiveCD a few times from cold/powered off.

Already tried this one, doesn't work.
> **robsoles said:**
> 
(3) If #2 fails in similar way then please make a USB/Flash stick bootable using "System"->"Administration"->"Startup Disk Creator" and the LiveCD iso and try booting off that a few times running.

I can't try this one but it'll fail like the others. There is absolutely no interaction with my laptop after odd booting.
> **robsoles said:**
> 
I can't diagnose your hardware from here like this - I could only physically test so much about it if I did have direct access before I'd have to go to a shop for more support as it is. Can check if HDD is SATA connection and try an alternative SATA HDD in the lappie?
I'll try to disassemble it and check the cables.
Thank you!

---

### Post by akoskm on 2010-08-09
And finally.... It's just booting. :KS

---

