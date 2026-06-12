---
title: "AMD X2 makes Gutsy lock up (still 32 bit)"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by abalone on 2008-03-10
Today I replaced my Athlon 64 3200+ with a dual core 4800+ (doesn't get any faster with my socket 939 mainboard).

Everything looks great, KDE's Infocenter shows both cores... but eventually (within a few minutes at times), the cursor becomes choppy and finally the system becomes unresponsive. 

I've checked the CPU temperature, turned off the "Cool & Quiet" BIOS option... tried "stressing" the CPU a bit in Windows XP, with no problems...

uname -a output: 

Linux earthworm 2.6.22-14-rt #1 SMP PREEMPT RT Fri Feb 1 07:25:25 UTC 2008 i686 GNU/Linux (I *need* realtime for low latency audio.)

I tried booting the generic kernel but it won't start X. Noticed no slowdown in the console though while trying to figure out how to get the Nvidia back (and failing). So here I am back in the RT kernel - so far it's been kind to me, and I have been allowed to send out this plea for help to you kind people. 

What do I do now? :cry:


edit: it locked up again after posting this and running Amarok and Firefox.

---

### Post by abalone on 2008-03-10
Hello?

I burned a JAD live CD and when I finally managed to "annoy" the CPU, it had the same problem. Didn't go away after killing all the busy programs either. 

Somebody tell me what's going on?

Is this it? No Linux anymore? :confused:

---

### Post by abalone on 2008-03-10
Again, the problem doesn't seem to occur in Windows, not even at consistent 100% CPU usage... else I'd wonder if it's hardware issue. I did however reset the BIOS to its defaults (only then proceeded to turn off unneeded on-board components (have no SATA) and the annoying BIOS logo and speech "effects").

---

### Post by abalone on 2008-03-11
Some more information:

> **abalone said:**
> Today I replaced my Athlon 64 3200+ with a dual core 4800+ (doesn't get any faster with my socket 939 mainboard).

Everything looks great, KDE's Infocenter shows both cores... but eventually (within a few minutes at times), the cursor becomes choppy 

and at about the same time, the Internet connection dies.Trying ifup eth0, but getting no DHCP lease from the router. (This is instantly remedied upon reboot.)

Keyboard still works for a while, as do programs in general, and a normal speed. I can still type, switch windows, scroll them. Music keeps playing normally, animations keep playing.

> and finally the system becomes unresponsive. 

And then one or both of the monitors go blank and to standby. 

Really seems to be a problem with realtime kernels (JAD's, too). The generic kernel works (as does PCLinuxOS' non-realtime), so I can at least use Ubuntu if not the way I meant to. Although it's begun freezing spontaneously after ...some time... in response to nothing identifiable.

---

### Post by poofyyoda on 2008-03-11
I'm not sure why your computer crashes, but if you're using 32bit Ubuntu, then you won't get any performance gain.  Go 64bit.  Otherwise, your 64bit cpu can only be used at 32bit.

Also,
Having a dual-core cpu will not really speed you up unless, you have 2 RAM modules
(since  each ram is 64bit width, it can't have 128bits from your cores)
 If you want more speed you might want to check.

None of this should crash your computer though, so I'm not sure why you've got problems.

---

### Post by abalone on 2008-03-11
> **poofyyoda said:**
> I'm not sure why your computer crashes, but if you're using 32bit Ubuntu, then you won't get any performance gain.  Go 64bit.  Otherwise, your 64bit cpu can only be used at 32bit.

Also,
Having a dual-core cpu will not really speed you up unless, you have 2 RAM modules
(since  each ram is 64bit width, it can't have 128bits from your cores)
 If you want more speed you might want to check.

None of this should crash your computer though, so I'm not sure why you've got problems.

I do have two RAM modules (what about four?)

64 bit seems to bring some problems and some of the stuff I need to use is Win32 binaries. (VSTs, some apps, the usual codecs.) Would that be a problem? How about browser plugins - Java, Flash, etc.?  

Well, as long as it crashes anyway...

Thanks for the response

---

### Post by rfruth on 2008-03-11
I disagree poof, when I went from a single core to AMD X2 (dual core) there was a big speed difference (same RAM ((1x512)) same hard disk ... I did a reinstall (32 bit) - to the OP does your BIOS 'see' your new CPU(s) ok ? :confused:

---

### Post by abalone on 2008-03-11
BIOS sees it ok - as far as I can tell. It doesn't say anything about there being two CPUs or two cores, except in the sense that "Dual Core Processor" seems to part of the name of the CPU...? KInfoCenter shows "processor 0" (core id 0) and "processor 1" (core id 1).

And it does seem notably faster - on the Athlon 64 3200+ I couldn't let it play my music (using several VSTs) "live" without constant breaks and glitches - now that same song runs without a hitch. 

Maybe it's just the sheer MHz increase from 2000 to 2400.

If even the generic kernel didn't lock up completely every 1-2 hours, it'd almost be usable




Oh...  here's a thought... I could try a single core Athlon FX instead? 

Though at some point I might as well get a new computer :/

---

### Post by abalone on 2008-03-12
I'm being advised to recompile the kernel... how'd I best go about doing that I don't know right now.

---

### Post by sloggerkhan on 2008-03-12
hmm. It might be something particular to the real time kernel. A lot of things can have odd issues with that, don't know why.

---

### Post by Iceni on 2008-03-12
Just to confirm: I did a similar switch a little while ago (3000 -> x2 4400) and it gave me no problems at all.

---

### Post by abalone on 2008-03-12
> **Iceni said:**
> Just to confirm: I did a similar switch a little while ago (3000 -> x2 4400) and it gave me no problems at all.

Using the realtime kernel?

---

