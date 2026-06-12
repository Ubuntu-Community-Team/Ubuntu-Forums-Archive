---
title: "Ubuntu 14.04 on AMD A10-5745M APU - unexpected shutdown"
date: 2015-09-09
forum: Hardware
---

### Post by gleedadswell on 2015-09-09
Hello, I'm running a fairly fresh (few days old) install of Ubuntu 14.04 on a new HP Pavillion laptop.  System details say:

Processor: AMD A10-5745M APU with Radeon(tm) HD Graphics × 4 
Graphics: AMD Radeon R7 M260

uname says:

```
uname -a
Linux onsager-go 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

It came with Windows 8.1 installed and I've installed Ubuntu alongside in dual boot.  The install was a joy (one of the most straightforward I've done).  The only issue I noticed at first was that it was dropping wireless which I've fixed with a new module.

Since then it has unexpectedly shutdown on a few occasions (3 or 4 I think?).  My first thought was overheating.  I installed psensor and that is fairly consistently telling me that the temperature is running in the 59-68 C range which I gather isn't a real concern (cpu-world says 105 C is max operating temperature which just sounds scary!).

I've been doing some video rendering, but the shutdowns have tended to happen when I'm not doing anything particularly heavy (the last one happened when the only application open was Firefox and I was browsing entirely text sites).  The only other thing I've noticed, which is probably unrelated, is that LibreOffice seems to be causing a bit of bogging down, especially Impress.  CPU usage seems to be nominal - with video editing software running  cpu usage is high but otherwise there is a fair bit of slack.  The fan  seems to be running on low pretty much constantly.  When I
render a video the fan kicks into a higher mode.  This all seems like it is behaving as it should.

Since it doesn't **seem** like an overheating problem, does anyone have any suggestions?

---

### Post by gleedadswell on 2015-09-09
Update:

Had another shutdown this morning.  The only application running at the time of shutdown (aside from psensor) was LibreOffice writer.  psensor showed 39 degrees at the time of the shutdown, so it certainly looks like this has nothing to do with overheating.  Is there some logging I can set up and post the logs from which would help diagnose this?  I'm far from new to linux but have never messed around with the system logs so I'll need some pointers.

---

### Post by gleedadswell on 2015-09-10
...and another one, this time with only Firefox open.  psensor said 58 C.

I have been mis-speaking.  It is actually restarting, not shutting down.

---

### Post by gleedadswell on 2015-09-10
Here are the last entries from

```
dmesg | less
```

```
[   40.660089] ACPI Error: Needed [Integer/String/Buffer], found [Reference] ffff88022fdc55e8 (20141107/exresop-422)
[   40.660100] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20141107/dswexec-461)
[   40.660107] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VGA_.AF03] (Node ffff880246caaaf0), AE_AML_OPERAND_TYPE (20141107/psparse-536)
[   40.660119] ACPI Error: Method parse/execution failed [\_SB_.PCI0.VGA_.ATIF] (Node ffff880246caa898), AE_AML_OPERAND_TYPE (20141107/psparse-536)
[   42.974812] init: plymouth-upstart-bridge main process ended, respawning
[   42.984530] init: plymouth-upstart-bridge main process (2819) terminated with status 1
[   42.984555] init: plymouth-upstart-bridge main process ended, respawning
[  331.076244] systemd-hostnamed[5132]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

```

But from the reading I've been doing so far it isn't clear to me how I know when this was written in relation to the last unexpected restart.  I expect this has been written after the restart and doesn't tell me anything about what caused the restart.

Why would it be trying to change the hostname?  I'm not inclined to install nss-myhostname until I know why the system would do such a thing.

apport.log contains some entries but they are from 2 days ago so presumably have nothing to do with the restart.

---

### Post by gleedadswell on 2015-09-12
Three times today...

Anyone? At least can someone give me advice on which log file to look in and what sort of messages go there during a restart so I can grep to find the parts of the log files that might shed some light on this?

Generally the computer freezes before it does the restart. But I don't think it has frozen every time.  Some of the restarts have taken me entirely by surprise because I was in the middle of entering some text and suddenly it restarted.

---

### Post by ipillinger on 2015-09-12
There's the log file viewer / system log viewer, or you can find the various logs in their directories mentioned in this post:
[http://ubuntuforums.org/showthread.php?t=1568706&p=9810348#post9810348](http://ubuntuforums.org/showthread.php?t=1568706&p=9810348#post9810348)

Not sure if any of them will be of use, but sounds like it'd be worth having a look anyway.

---

### Post by mörgæs on 2015-09-12
You will probably have a better change of getting an answer if you posted only once, editing the single post when new observations arrive.

This way the thread will be visible in the 'unanswered posts'-list. 

Anyway, is it stable in a live boot of 15.04?

---

### Post by Yellow Pasque on 2015-09-12
Memtest...
Either run it from your BIOS/EFI if it has such an option, or boot to it from GRUB: [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)
As suggested, let it do at least one pass, but run it overnight if feasible.

---

### Post by gleedadswell on 2015-09-13
OK, will try the memtest tonight.

**Later edit.**  
Memory Test ran through 3 iterations and found no issues.  I ran it from the EFI.

Back to the logs?

Thanks ipillinger for pointing me at the location of the logs but that much I knew already.  What (I think) I really need is some way to find the output to the logs immediately preceding one of these restarts.  I *presume* there is a common sequence of log entries that occur during a restart (things like "restarting now"). Not knowing any better things to search for, doing

```
grep "restart" /var/log/* 
```

the only remotely useful looking output is

```
bootstrap.log:invoke-rc.d: policy-rc.d denied execution of restart.
```

but I'm not sure that is at all relevant.  Similarly grepping (is "grepping" a verb?  It should be...) for "shutting down", "going down now", and so on yields nothing.  Can anyone with some knowledge of what typical sequences of outputs go to the logs on a restart point me at something more useful to grep for?  Or if there is some other direction to look in?

---

### Post by gleedadswell on 2015-09-14
> **mörgæs said:**
> Anyway, is it stable in a live boot of 15.04?

Given that it installed cleanly from a live boot of 14.04 I have no reason to believe that it wouldn't live boot to 15.04.  But where would that get me?  I'm perfectly willing to do it, but I'd like to know how it might help.

---

### Post by mörgæs on 2015-09-15
It's not about booting from 15.04, it's about running 15.04 for some time to see if it's stable, that is free from crashing. 

It will tell if this release supports your hardware better than 14.04.

---

### Post by gleedadswell on 2015-09-18
Hmm...at this stage I've got so much on this machine (I've been getting a lot of work done on it) that I'm pretty committed to getting 14.04 working and I think starting over with 15.04 will eat up too much time.  The restarts have only been a minor annoyance so far (for example I've lost no data).  Presumably as kernel upgrades come out on 14.04 the situation will improve.  If the problem persists until the next time I get a break in my workload (i.e. for a few months) then I'll take the time to try a newer Ubuntu.  By that time it will be 15.10.

---

### Post by Yellow Pasque on 2015-09-18
Do you have the latest BIOS from HP? (I would have checked, but you didn't give a model number..)
Do you have amd64-microcode package installed?
```
apt-cache policy amd64-microcode
```

---

### Post by gleedadswell on 2015-10-14
Installed amd64-microcode.  It now says

```

~$ apt-cache policy amd64-microcode
amd64-microcode:
  Installed: 2.20131007.1+really20130710.1
  Candidate: 2.20131007.1+really20130710.1
  Version table:
 *** 2.20131007.1+really20130710.1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages
        100 /var/lib/dpkg/status

```

Is this telling us what version of the BIOS is installed?

---

### Post by Yellow Pasque on 2015-10-15
> **gleedadswell said:**
> Is this telling us what version of the BIOS is installed?

No. This command should tell you (assuming you have dmidecode package installed):
```
sudo dmidecode -t bios -t system
```

---

### Post by gleedadswell on 2015-10-17
That gave

```

~$ sudo dmidecode -t bios -t system
# dmidecode 2.12
# SMBIOS entry point at 0x7ccfa010
/dev/mem: Operation not permitted

```

Looked at a few references about this "/dev/mem: Operation not permitted" message and most of them say this is caused by not having root privileges but I did run it under sudo so I'm confused.

---

### Post by gleedadswell on 2015-10-17
Would upgrading to an "upstream" version of the kernel possibly help?

Edit: ...by which I mean a "mainline" kernel.  For example, it looks like it would be easy to upgrade from my current 3.19.0-30 to anything between 4.0 and 4.1-rc2 from the Ubuntu upstream kernel archive.  Is there any reason *not* to try this?

---

### Post by gleedadswell on 2016-01-09
The problem persisted for a month or two.  But now it has been many weeks since is has spontaneously restarted.  So I think regular updates have resolved the issue without me doing anything.  I'll mark this as resolved.

---

