---
title: "msi am1i amd 5350 total lock ups, page faults."
date: 2016-08-13
forum: Hardware
---

### Post by pab10 on 2016-08-13
Hello All

just built a socket am1 MSI AM1I, AMD 5350, 8gb hyperx fury ram, unfortunately getting very frequent (inevitable) complete lockups of the whole pc (though sometimes a console is still available on ctl-alt-f1)

Completely default bios settings no overclock or anything. cpu runs at about 21c.

accessing memory from standard user-land python programs, using all the memory in a massive string and checking its integrity and another program just doing maths ops running at 100% on another core, then the memory seems to work ok.

It passed a memtest86 full pass

First tried to install mint standard edition and that gave errors saying file on disk did not match cd even though I had done the verify media integrity check.  Eventually that installed but using firefox crashed/locked the machine soon after boot.

I then moved to trying Xubuntu xubuntu-16.04.1-desktop-amd64.iso which installed OK but as with mint it was locking up the entire windowing system while using firefox.  I then shifted to chrome and that seems to work ok for about an hour or two with no errors in syslog.

I did notice a linux firmware update to the system so not sure if that improved it

The machine will work ok for an hour or so OK playing videos and browsing the web (sometimes even longer and manages to play a full film) but then in syslog start getting odd errors such as this random selection:

BUG: Bad page state in process SimpleCacheWork
[...]
general protection fault: 0000 [#1] SMP
[...]
BUG: Bad page state in process BrowserBlocking pfn:6848b
[...]
BUG: Bad page state in process khugepaged pfn:14d6be
[...]
BUG: Bad page map in process dpkg pte:80000001c8d7d025 pmd:0d031067
[...]
BUG: bad page map in process systemd-cgroups pte:80000001c8d7d025 pmd:2315b2067
[....]
traps: chrome[3927] trap stack segment ip:56508c275f2e sp:7ffdaf611d10 error:0 in chrome[56508b368000+5dfb000]
[...]

and then shortly afterwards locks up the whole machine

This kind of makes me think it could be a firmware problem though
could still be a hardware problem... faulty mobo? faulty cpu? faulty/unsupported memory?

I see there is an extra driver amd microcode I have tried it with and without, crashes either way.

any help would be appreciated.

---

### Post by Yellow Pasque on 2016-08-15
It could certainly be a hardware issue. It's tough to troubleshoot that without spare parts though. Some thoughts:
- Disable unused hardware in BIOS if possible.
- Try running with just one stick of RAM at a time (i.e. test each one separately). Yeah, I know it passed memtest, but this would be a bit more conclusive.
- If you've got a spare discrete GPU, you may want to try that.
- There are a couple BIOS updates for this mobo, but that seems risky if it's freezing randomly and they don't look too interesting/relevant. The changelog for it is as follows:
```
10.2 - Improved PS/2 mouse compatibility
10.1 - Improved system is not able to wake up by RTC or Lan once EUP is disabled.
     - Adjust Super I/O register.
10.0 - Initial BIOS
```

---

### Post by pab10 on 2016-08-16
Thanks, it only has one memory stick, no spares yet to try, but I have noticed it seemed to not have fatal crashes if I disabled cool and quiet and spread spectrum in the bios, though still segfaults.

also discovered some problem in my burning of the usb stick after finding out how to verify the burn.

so now have a good usb stick to install from, going to reset the cmos of board and try again.

board already has latest 10.2 bios.

---

### Post by pab10 on 2016-08-19
I did suspect it was an incompatible memory stick... incompatible default timings, or this board/bios no good with that 8gb chip, got a 4gb kingston valueram ddr3 1600 and it works OK now..

annoying waste of time because kingston website says that 8gb ram chip I purchased first is compatible with this board... maybe the 4gb version works ok????

cool! perhaps the Am1 5350 is sweet spot for cost effectiveness for purchase price, ability to function as a nettop media centre dual monitor dev computer (not using android studio LOL) and not burning massses of power Kw... 

fired up my old dinosaur AMD 3.7ghz and graphics card yesterday... 150-220watts and only about twice as fast as this 5350 pc....

**update:** actually as this is quad core and ffmpeg is multicore, this 5350 2ghz is faster than 3.7ghz dinosaur but is running on an ssd as well....

Linux rocks!

(though I read linux not as power efficient with am1 chipset as windows... perhaps can improve that?)

---

