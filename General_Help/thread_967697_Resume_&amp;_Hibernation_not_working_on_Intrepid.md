---
title: "Resume &amp; Hibernation not working on Intrepid"
date: 2008-11-02
forum: General Help
---

### Post by lastchancetosee on 2008-11-02
Suspend & Hibernation do not work on my computer with Intrepid:

Suspend: Choosing 'Suspend' in the shutdown-menu or via Gnome Do simply does nothing. Nada, no reaction all.

Hibernation: At least something happens here:

- Computer hibernates without problems.
- Waking up seems to work just fine, up until the point where normally the login screen would be displayed, instead of that I only get wild colors on the screen, only thing that gets me out of that seems to be hitting the reset button.

I've looked through sys- and pm-suspend-logs and couldn't find anything out of order:

```
/var/log$ cat pm-suspend.log 
Initial commandline parameters: 
Sun Nov  2 13:41:15 CET 2008: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/00clear hibernate: success.
/usr/lib/pm-utils/sleep.d/05led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager hibernate: success.
/usr/lib/pm-utils/sleep.d/48hid2hci hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/50modules hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate: success.
Sun Nov  2 13:41:18 CET 2008: performing hibernate
Sun Nov  2 13:43:14 CET 2008: Awake.
Sun Nov  2 13:43:14 CET 2008: Running hooks for thaw
/usr/lib/pm-utils/sleep.d/99video thaw: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video thaw: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode thaw: success.
/usr/lib/pm-utils/sleep.d/95led thaw: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw: success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw: success.
/usr/lib/pm-utils/sleep.d/90clock thaw: success.
/usr/lib/pm-utils/sleep.d/50modules thaw: success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw: not applicable.
/usr/lib/pm-utils/sleep.d/48hid2hci thaw: No devices in HID mode found
Returned exit code 1.
/usr/lib/pm-utils/sleep.d/10NetworkManager thaw: success.
/usr/lib/pm-utils/sleep.d/05led thaw: not applicable.
/usr/lib/pm-utils/sleep.d/00clear thaw:
```

```
/var/log/$ cat syslog | grep 13:43
[...]
Nov  2 13:43:18 wolf kernel: [ 4800.772002] ACPI: Waking up from system sleep state S4
Nov  2 13:43:18 wolf kernel: [ 4800.772002] agpgart-sis 0000:00:00.0: restoring config space at offset 0x1 (was 0x22100007, writing 0x32100007)
Nov  2 13:43:18 wolf kernel: [ 4800.772002] pata_sis 0000:00:02.5: restoring config space at offset 0x1 (was 0x2000001, writing 0x2000005)
Nov  2 13:43:18 wolf kernel: [ 4800.772002] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Nov  2 13:43:18 wolf kernel: [ 4800.792016] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Nov  2 13:43:18 wolf kernel: [ 4800.816016] ehci_hcd 0000:00:03.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Nov  2 13:43:18 wolf kernel: [ 4800.848036] C-Media PCI 0000:00:0a.0: restoring config space at offset 0x1 (was 0x2100105, writing 0x2100101)
Nov  2 13:43:18 wolf kernel: [ 4800.848051] C-Media PCI 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov  2 13:43:18 wolf kernel: [ 4800.848267] fglrx_pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov  2 13:43:18 wolf kernel: [ 4800.853999] [fglrx] Power up the ASIC
Nov  2 13:43:18 wolf kernel: [ 4800.855369] serial 00:07: activated
Nov  2 13:43:18 wolf kernel: [ 4800.856488] parport_pc 00:08: activated
Nov  2 13:43:18 wolf kernel: [ 4800.932431] ata2.01: ACPI cmd ef/03:0c:00:00:00:b0 filtered out
Nov  2 13:43:18 wolf kernel: [ 4800.932435] ata2.01: ACPI cmd ef/03:42:00:00:00:b0 filtered out
Nov  2 13:43:18 wolf kernel: [ 4800.932591] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov  2 13:43:18 wolf kernel: [ 4800.932594] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Nov  2 13:43:18 wolf kernel: [ 4800.940237] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Nov  2 13:43:18 wolf kernel: [ 4800.940240] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Nov  2 13:43:18 wolf kernel: [ 4800.956244] ata2.00: configured for UDMA/33
Nov  2 13:43:18 wolf kernel: [ 4800.972246] ata2.01: configured for UDMA/33
Nov  2 13:43:18 wolf kernel: [ 4801.041953] ata1.00: configured for UDMA/100
Nov  2 13:43:18 wolf kernel: [ 4801.042061] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Nov  2 13:43:18 wolf kernel: [ 4801.042090] sd 0:0:0:0: [sda] Write Protect is off
Nov  2 13:43:18 wolf kernel: [ 4801.042093] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov  2 13:43:18 wolf kernel: [ 4801.042130] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov  2 13:43:18 wolf kernel: [ 4801.084030] sd 0:0:0:0: [sda] Starting disk
Nov  2 13:43:18 wolf kernel: [ 4801.107016] PM: Image restored successfully.
Nov  2 13:43:18 wolf kernel: [ 4801.155718] Restarting tasks ... done.
Nov  2 13:43:18 wolf kernel: [ 4801.160845] PM: Basic memory bitmaps freed
Nov  2 13:43:18 wolf kernel: [ 4803.900994] eth0: Media Link On 100mbps full-duplex 
Nov  2 13:43:18 wolf NetworkManager: <info>  Waking up...
[...]
```

After that come the messages from after I hit the reset button.
Since the last entry is the NetworkManager waking up, could that be responsible? Some sort of error with the NetworkManager.
Or the graphics card (since I have graphics errors)? I use a Radeon 9600 with proprietary drivers.

---

### Post by lastchancetosee on 2008-11-02
Update: I've switched to the open source graphics driver.
This had no effect on the suspend-problem, the first time I hibernated the computer stopped just before the login screen, but without weird things onscreen, the second time it restarted just fine, but the network was disabled, forcing me again to reboot.

The plot thickens.

Any ideas?

---

### Post by lastchancetosee on 2008-11-05
Further testing.

Hibernation with open source driver extremely buggy:
a) When resuming from hibernation with the open source driver, the NetworkManager reports a faulty network-connection EVEN THOUGH the connection is working perfectly alright (fixed IP, no WLAN). I've read somewhere that the can NetworkManager fail with WLAN and hibernation but I have no WLAN.

b) When resuming from suspend the "IEC958 In Monitor"-switch on my audio mixer is unset, resulting in no sound until I set the switch again.

c) When beeing asked for a password on resume the first try in entering the password is ALWAYS rejected or there are two login windows. I ALWAYS have to put in my password twice.
Well, at least I AM beeing asked, huge improvement over Hardy, where I never could get this to work.

b) Still no suspend.

c) since hibernation is working if buggy with the open source and not worling with the proprietary driver, there must be something wrong with the latter ones config. While I can live with the open source driver, I'd still very much appreciate any insight into what is going wrong.




Isn't there ANYBODY who has SOME idea about what could be causing this?
Please.

---

### Post by fizyk on 2008-11-13
I've tried mainly hibernation on my notebook, but so far it gets me nowhere, it seems to hibernate without problems, then, when I'm booting it again it Ubuntu get's back to gnome session only to be shut down.

Suspension worked good for me, apart from NetworkManager remembering old wireles networks. Had to turn all wireless off and on.

I'm using Intrepid 64bit and there's Nvidia GS 9200M graphi card on my notebook

---

### Post by milasch on 2008-11-13
I tried for months to make my desktop able to suspend/hibernate.

I gave up...

My old laptop (Compaq n610c) used to suspend fine on Hardy... Now it doesn't anymore. 

The idea of digging this problem up doesn't bring me good memories. I'll just leave like that. (Not trying to be pessimistic lol).

---

### Post by Paul S on 2008-11-14
Similar experience on my Dell E1505 (aka 6400) with ATI video card. Suspend works sometimes, but hibernate will not resume. This happened after I upgraded to intrepid from hardy. So, I tried doing a fresh install, but have the same experience. I tried both 32-bit and 64-bit versions of intrepid, with the same result.

After the fresh install hibernate worked once, but has not worked since. Suspend works sometimes, but not always. I've switched back to hardy on another partition, where both suspend and hibernate work almost always.

I edited the grub boot line to elimate "quiet splash" and noticed that the hibernation resume successfully unpacked the resume image file, but hung at the next step with the error message:

suspending consoles (use no_console_suspend to debug)

I tried this at the end of the boot line and it showed a little more messages, but still did not show any errors. It just hangs,

See launchpad bug 273986.

---

### Post by lastchancetosee on 2008-11-14
Hey, if not help, at least some people with similar woes ...

I did some more testing.
1) I again looked at syslog an pm-suspend-log (I hadn't checked them after switching to the open source video driver), both still report that everything is fine and dandy, thank you very much. In fact, nothing changed, so I wont be posting them here.
2) I did some fiddling with pm-action etc. and the sleep.sh/hibernate.sh scripts:
2.1) I know why suspend doesn't work: pm-is-supported --sleep (--sleep-hybrid) reports that neither sleep nor sleep-hybrid is supported. Why? No idea.
2.2) Running sleep.sh does nothing, running it with "-sleep" (so as to make it not use power-manager etc) results in the following:

```
cat: /etc/network/run/ifstate: No such file or directory
cat: /etc/network/run/ifstate: No such file or directory
```

After that, nothing more happens, I aborted with Ctrl+c.
2.3) hibernate.sh puts the computer to sleep, but on resumes it only produces a black screen with blinking cursor. Syslog reveals an error with the image.
3) The error that I have to enter my password twice after resuming is not reproducible. It happens most of the time, but not always.

So, still no progress, but new (additional) questions:

- Any idea where I can find or how I can produce a log, that tells me something is wrong? These "everything's peachy"-log entries are getting on my nerves :-)
- Why THE HELL is pm-suspend suddenly not supported anymore? Suspend worked (in contrast to hibernate) flawlessly in Hardy.


Since I never managed to get hibernation to work properly in windows I guess I can live with not getting it to work in Ubuntu. But no suspend? That's ridiculous.

---

### Post by Paul S on 2008-11-14
> **lastchancetosee said:**
> 
2.1) I know why suspend doesn't work: pm-is-supported --sleep (--sleep-hybrid) reports that neither sleep nor sleep-hybrid is supported. Why? No idea.


I hadn't seen that command or tried it before.  According to the man page you have to check the exit status.  On my 64 bit intrepid:

paul :~$ man pm-is-supported ; echo $?
0
paul :~$ pm-is-supported --suspend ; echo $?
0
paul :~$ pm-is-supported --hibernate ; echo $?
0
paul :~$ pm-is-supported --suspend-hybrid ; echo $?
1

So, pm is supposed to work in suspend and hibernate, but not hybrid.  I imagine s2both from the uswsusp would work there.

I'd like to get a 64-bit that works as good as hardy 32-bit.  So far, I've had freezes on 8.04 and 7.10 64-bits.  8.10 has not frozen after only a couple days, but with hibernation bugs and kde4, it's not a good production platform.  Maybe I need to try debian next.  I see Lenny is just out with RC1.

regards,

---

### Post by lastchancetosee on 2008-11-15
Sorry, I meant to type 'suspend', not 'sleep'. I blame sleep.sh ...

So, corrected version:
pm-is-supported --hibernate reports "is available" (exit code 0)
pm-is-supported --suspend reports "is not available" (exit code 1), pm-is-supported --suspend-hybrid ditto.

---

### Post by Interpreter on 2008-11-15
Neither standby nor hibernation work for me.
They actually force me to reboot.

---

### Post by slambrick on 2008-11-16
I am having a similar issue. I tried to hibernate my desktop only to find Intrepid (64) comes back with several failures from thaw then after  a PM 7-2.1 error -19 shutsdown i cannot get the session to resume. Does anyone know how to correct the boot sequence???

---

### Post by Ubuntist on 2008-11-20
I'm have the hibernate bug on a Dell 8300 under Intrepid.  I'm using the proprietary driver for my ATI Radeon 9800 Pro graphics card, but I doubt that's the problem, because I had no trouble hibernating or suspending under Hardy.

This post:

[http://ubuntuforums.org/showpost.php?p=6061315&postcount=9](http://ubuntuforums.org/showpost.php?p=6061315&postcount=9)

has a suggestion that seems to have worked for somebody, at least.

---

### Post by punkybouy on 2008-11-22
I am having the same problem on a new HP G60 laptop with Nvidia graphics card and using restricted drivers.  It suspends but I have to reboot to get the desktop again.  The mouse pointer shows up but the screen is black making a reboot necessary.

---

### Post by mtbsoft on 2008-11-27
I have 8.10 installed on an Inspiron 9400 with ATI X1400 graphics and proprietary driver.  I have no problems at all with suspend - works flawlessly - but hibernate doesn't, it appears to hibernate just fine but never restores.  

The thing is that I don't even see any obvious errors, even with quiet removed in menu.lst, it just seems to ignore the fact that I had saved the hibernate data.

pm-is-supported --hibernate reports 0
pm-is-supported --suspend reports 0 
pm-is-supported --suspend-hybrid reports 1

---

### Post by mordoc on 2008-12-02
> **Interpreter said:**
> Neither standby nor hibernation work for me.
They actually force me to reboot.

I'm having the same problem with an IBM R51. A clean install doesn't seem to make a difference and on resume I get a flashing Caps Lock LED...

---

### Post by Interpreter on 2008-12-02
> **mordoc said:**
> i'm having the same problem with an ibm r51. A clean install doesn't seem to make a difference and on resume i get a flashing caps lock led...

+1

---

### Post by jackobean on 2008-12-03
I have the same problem, was working fine (albeit a bit slow) in Hardy. I have a Dell XPS M1530 lappy.

---

### Post by Nathan Sweeney on 2008-12-03
> **punkybouy said:**
> I am having the same problem on a new HP G60 laptop with Nvidia graphics card and using restricted drivers.  It suspends but I have to reboot to get the desktop again.  The mouse pointer shows up but the screen is black making a reboot necessary.

I have an HP dv5 notebook, and I have the same issue.  Trying to resume from suspend, I get to a black screen with a mouse pointer.  Mouse pointer is moveable, but nothing else comes up.

I have an integrated intel graphics chip, so I don't think that the issue is from graphics as it seems that intel, nvidia, and ati systems have the same issue.

---

### Post by blackpaw on 2008-12-05
Maybe someone should differenciate if it is about 

- suspending or 
- resuming from suspend
- and what version they are running (32 or 64, 8.10 or 8.04)
- and splice the discussions into the proper threads, this is getting confusing. :) 

I followed[ the instructions to debug suspend]("https://wiki.kubuntu.org/DebuggingKernelSuspend") but did not find any hints despite the realtime clock did not even jump forward... can I assume my system refuses to suspend? (why?)
What also confuses me, the suspend/hibernation files change from release to release...
so I can't even browse the forums because the files needed are located in a different place; also the suspend mechanism changes... pm-suspend is the current one, most guides here deal with s2ram or sleep.sh... *confused*

Andreas 

P.S. Will add my suspend/resume log/trace later.

---

### Post by lastchancetosee on 2008-12-06
> Maybe someone should differenciate if it is about 

- suspending or 
- resuming from suspend
- and what version they are running (32 or 64, 8.10 or 8.04)
- and splice the discussions into the proper threads, this is getting confusing.

All of the above :-) .

OK, since I started this originally:

This is about

a) suspend to RAM (NOT resuming from suspend) not working at all since Intrepid
b) resuming from hibernate (suspend to disk) being only partially successful since Intrepid

Version: 8.10, 32bit (with Xfce, but I don't think therein lies the rub)

Since most discussions here now seem to be about hibernation, I'd suggest splicing of the suspend-to-RAM-not-working-part. Feel free to splice away.

I'll try the pm-trace-stuff later.

---

### Post by mordoc on 2009-02-18
> **mordoc said:**
> I'm having the same problem with an IBM R51. A clean install doesn't seem to make a difference and on resume I get a flashing Caps Lock LED...

Here's the fix that worked for me on an IBM R51:
[URL="https://bugzilla.novell.com/show_bug.cgi?id=450256"]
https://bugzilla.novell.com/show_bug.cgi?id=450256[/URL]

---

