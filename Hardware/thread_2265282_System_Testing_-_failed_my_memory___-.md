---
title: "System Testing - failed my memory   -   ?"
date: 2015-02-13
forum: Hardware
---

### Post by michael-piziak on 2015-02-13
Using Ubuntu 12.04 LTS.

I ran the "System Testing" application and all passed except my memory.

It said it failed with this message:  "Meminfo total: 3965516 kBDMI total: 8192000 kBAccuracy: 48.00Memory totals not close enough"

Comments please.

I haven't had any issues with my system.  Just wandering how detrimental this test result is.

Perhaps there is something else in the software center that I could run and get a second opinion on - ?

---

### Post by v3.xx on 2015-02-14
Maybe this will help with understanding mem totals.

[http://askubuntu.com/questions/338614/ubuntu-12-04-32bit-system-fails-memory-testing](http://askubuntu.com/questions/338614/ubuntu-12-04-32bit-system-fails-memory-testing)

---

### Post by michael-piziak on 2015-02-14
Thanks for the link.

So, [B][SIZE=3]"[COLOR=#333333][FONT=UbuntuRegular]So this test is for testing if your OS is correctly detecting an using all your available RAM. If the [/FONT][/COLOR]Accuracy[/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=3] is above 90% then the test PASSes, if it is under it FAILs."

So my number of "48"  means that my OS is only correctly detecting and using 48% of the available ram - ???[/SIZE]


[SIZE=3]This is not good is it - ?[/SIZE][/FONT][/COLOR][/B]

---

### Post by v3.xx on 2015-02-14
No, this does not look good, but maybe not that bad?  I have not delt with this error before, but found a couple of old tickets.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994103)

[https://answers.launchpad.net/ubuntu/+source/unity/+question/246087](https://answers.launchpad.net/ubuntu/+source/unity/+question/246087)

---

### Post by michael-piziak on 2015-02-14
I skimmed through those 2 links.  I think perhaps much of that is beyond my expertise.

I think that one solution was to update the bios.  I have Ubuntu installed 100% on this HP desktop.  Does anyone think I could still update it's bios?

Update:  I went back and read both of your links twice.

One thing I'd like to note is that [B]I have 4 gigs ram installed.  I believe something is reporting 8192000 kb - isn't that a false report of 8 gigs ?

[/B]michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$ sudo /usr/share/checkbox/scripts/memory_compare
[sudo] password for michael: 
Meminfo total: 3965516 kB
DMI total: 8192000 kB
Accuracy: 48.00
Memory totals not close enough
michael@michael-HP-Compaq-dc5800-Small-Form-Factor:~$

---

### Post by michael-piziak on 2015-02-14
Update:  I booted to grub and did the memory test - took about 45 minutes then the test restarted.  The memory passed 100%.
Perhaps the memory is fine but there is a problem somewhere else that is not letting the OS access all or most of the memory?

One other thing I thought of is that I installed a 64 bit version of Ubuntu 12.04 lts on a machine that perhaps use to be a 32 bit Windows system - perhaps the bios is set to be 32 bit - ??

Comments please.

See attached image of memory test.

Update:  I opened up many many programs and youtube movies to see if I could get the system to use most of the 4 gigs of memory.  I was using 3.2, then 3.4 out of 3.8 available gigs.  It would seem the system is certainly accessing more than 48% of the ram.

Comments please.

---

### Post by sudodus on 2015-02-15
> **michael-piziak said:**
> I ran the "System Testing" application and all passed except my memory.

It said it failed with this message:  "Meminfo total: 3965516 kBDMI total: 8192000 kBAccuracy: 48.00Memory totals not close enough"

Comments please.

I haven't had any issues with my system.  Just wandering how detrimental this test result is.

Perhaps there is something else in the software center that I could run and get a second opinion on - ?

> **michael-piziak said:**
> Update:  I booted to grub and did the memory test - took about 45 minutes then the test restarted.  The memory passed 100%.
Perhaps the memory is fine but there is a problem somewhere else that is not letting the OS access all or most of the memory?

One other thing I thought of is that I installed a 64 bit version of Ubuntu 12.04 lts on a machine that perhaps use to be a 32 bit Windows system - perhaps the bios is set to be 32 bit - ??

Comments please.

See attached image of memory test.

Update:  I opened up many many programs and youtube movies to see if I could get the system to use most of the 4 gigs of memory.  I was using 3.2, then 3.4 out of 3.8 available gigs.  It would seem the system is certainly accessing more than 48% of the ram.

Comments please.

I think memtest and other evidence show that your memory works as it should :-) so I think that the "System Testing" application does not work correctly concerning the memory.

---

### Post by michael-piziak on 2015-02-15
> **sudodus said:**
> I think memtest and other evidence show that your memory works as it should :-) so I think that the "System Testing" application does not work correctly concerning the memory.

I downloaded Ubuntu 14.04 LTS and made a bootable USB flash drive and booted into 14.04 LTS.
I ran the System Testing application that 14.04 uses, selecting memory, and my memory passed it's test twice.

So my conclusion is the same as yours.  System Testing in Ubuntu 12.04 lts does not work correctly concerning memory.

It would be nice if this bug were fixed, as 12.04 LTS is still supported.

Thanks so much for your replies and time.  I choose to use 12.04 LTS for a few reasons.

---

### Post by Yellow Pasque on 2015-02-15
This bug was fixed since the days of 12.04:
[https://bugs.launchpad.net/checkbox/+bug/960087](https://bugs.launchpad.net/checkbox/+bug/960087)

An updated version with the fix never found its way into the default repos. If you want an update version of System Testing, see: [https://launchpad.net/~brendan-donegan/+archive/ubuntu/ppa](https://launchpad.net/~brendan-donegan/+archive/ubuntu/ppa)

---

### Post by michael-piziak on 2015-02-15
> **Temüjin said:**
> This bug was fixed since the days of 12.04:
[https://bugs.launchpad.net/checkbox/+bug/960087](https://bugs.launchpad.net/checkbox/+bug/960087)

An updated version with the fix never found its way into the default repos. If you want an update version of System Testing, see: [https://launchpad.net/~brendan-donegan/+archive/ubuntu/ppa](https://launchpad.net/~brendan-donegan/+archive/ubuntu/ppa)


Thanks so much for the reply.

If you could tell me exactly which file to click to download I'd appreciate it.

---

### Post by Yellow Pasque on 2015-02-15
Read the instructions:
```
You can update your system with unsupported packages from this untrusted PPA by adding ppa:brendan-donegan/ppa to your system's Software Sources.
```
[https://launchpad.net/+help-soyuz/ppa-sources-list.html](https://launchpad.net/+help-soyuz/ppa-sources-list.html)

---

### Post by v3.xx on 2015-02-15
I don't know, looks safe to me.  But if you do get in a pinch with a ppa its nice to have a way out.

[PPA-purge]("http://askubuntu.com/questions/309966/difference-between-ppa-purge-and-add-apt-repository-r")

---

