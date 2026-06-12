---
title: "Kernel panic bad EIP value on booting"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by wavingpines on 2007-12-02
Hi

I'm pretty new to Ubuntu (and Linux generally) and I've just upgraded my PC from an old Pentium 4 to the following:

Motherboard : Asrock 2Core1333-2.66G
Processor: Intel 1.6Ghz (model E2140?) overclocked by mfr to 2.66Ghz
Memory: 1GB DDR2 667Mhz 5300
Graphics: Onboard Intel GMA 950
Audio: Onboard
LAN: Onboard
HD: Seagate IDE 40GB ST340810A
CD: LG 40x CD-RW HL-DT-ST GCR-8400B

Basically, I've kept the hard disk and CD drive, case and PSU and replaced everything else.

Now I get a kernel panic every time I boot from either my hard disk or the live CD (7.10 Gutsy in both cases); I've also tried to boot DSL with similar results.

Actual messages I can see before the system freezes are:
[INDENT][FONT="Courier New"]
*pde = 00000000
Oops: 0000 [#1]
SMP
Modules linked in:
CPU: 0
EIP: 0060:[<31c00f01>]  Not tainted VLI
EFLAGS: 00010002    (2.6.22-14-generic #1)
EIP is at 0x31c00f01
eax: 680000b1 ebx: 000f0000 ecx: 00010000 edx: 49430150
esi: 0000ff01 edi: c03c0000 ebp: 000f0031 esp: df813f33
ds: 007b es: 007b fs: 00d8 gs: 0000 ss: 0068
Process swapper (pid: 1, ti=df812000 task=c18e2000 task.ti=df812000)
Stack: ...
Call Trace:
Code: Bad EIP value.
EIP: [<31c00f01>] 0x31c00f01 SS:ESP 0068:df813f33
Kernel panic - not syncing: Attempted to kill init!
[/FONT][/INDENT]

I've Googled and searched the Ubuntu forums but nothing that helps.  I've tried the 'acpi=off ide=nodma' boot options as suggested in some posts, and run a memory test, which was clean.  The threads I found seem to say it's a hardware issue, but where do I start?  I had a look around the forums and there seem to be people out there running Gutsy with this motherboard (but not the onbard video), and, separately, the onboard Intel video, so I'm v. confused.

Any ideas out there?  One thought that occured is whether I need to be running the 64-bit version, or whether running the 32-bit version should run, but not take advantage of new processor features?

Any help gratefully received.
Thanks in advance

---

### Post by ukripper on 2007-12-04
> **wavingpines said:**
> Hi

I'm pretty new to Ubuntu (and Linux generally) and I've just upgraded my PC from an old Pentium 4 to the following:

Motherboard : Asrock 2Core1333-2.66G
Processor: Intel 1.6Ghz (model E2140?) overclocked by mfr to 2.66Ghz
Memory: 1GB DDR2 667Mhz 5300
Graphics: Onboard Intel GMA 950
Audio: Onboard
LAN: Onboard
HD: Seagate IDE 40GB ST340810A
CD: LG 40x CD-RW HL-DT-ST GCR-8400B

Basically, I've kept the hard disk and CD drive, case and PSU and replaced everything else.

Now I get a kernel panic every time I boot from either my hard disk or the live CD (7.10 Gutsy in both cases); I've also tried to boot DSL with similar results.

Actual messages I can see before the system freezes are:
[INDENT][FONT="Courier New"]
*pde = 00000000
Oops: 0000 [#1]
SMP
Modules linked in:
CPU: 0
EIP: 0060:[<31c00f01>]  Not tainted VLI
EFLAGS: 00010002    (2.6.22-14-generic #1)
EIP is at 0x31c00f01
eax: 680000b1 ebx: 000f0000 ecx: 00010000 edx: 49430150
esi: 0000ff01 edi: c03c0000 ebp: 000f0031 esp: df813f33
ds: 007b es: 007b fs: 00d8 gs: 0000 ss: 0068
Process swapper (pid: 1, ti=df812000 task=c18e2000 task.ti=df812000)
Stack: ...
Call Trace:
Code: Bad EIP value.
EIP: [<31c00f01>] 0x31c00f01 SS:ESP 0068:df813f33
Kernel panic - not syncing: Attempted to kill init!
[/FONT][/INDENT]

I've Googled and searched the Ubuntu forums but nothing that helps.  I've tried the 'acpi=off ide=nodma' boot options as suggested in some posts, and run a memory test, which was clean.  The threads I found seem to say it's a hardware issue, but where do I start?  I had a look around the forums and there seem to be people out there running Gutsy with this motherboard (but not the onbard video), and, separately, the onboard Intel video, so I'm v. confused.

Any ideas out there?  One thought that occured is whether I need to be running the 64-bit version, or whether running the 32-bit version should run, but not take advantage of new processor features?

Any help gratefully received.
Thanks in advance

Just saw your private message!

i remember seeing this problem  before. i think what happens is new motherboards are built to take 64bit computing by default that is why jumpers and chipset are set accordingly. Try 64bit version it should work fine. Let me know if you have any problems.

---

### Post by wavingpines on 2007-12-04
Thanks for coming back to me.  I'll give the 64bit version a try (I guess that's what you're running on yours?).

I'm still a bit confused as after a re-install, my old Win2k partition boots and runs OK (well, it recognises the two processors).  Presumably it's running in 32bit mode.

---

### Post by ukripper on 2007-12-04
> **wavingpines said:**
> Thanks for coming back to me.  I'll give the 64bit version a try (I guess that's what you're running on yours?).

I'm still a bit confused as after a re-install, my old Win2k partition boots and runs OK (well, it recognises the two processors).  Presumably it's running in 32bit mode.

Manufacturers are moving forward so should we, 64 bit is present and future so why stick to 32 bit.

Acces to full potential of your hardware is through 64 bit so do give it a go. If there is a problem post any error message you get during boot up.

---

### Post by wavingpines on 2007-12-06
I downloaded the 64bit version and my machine successfully boots from it.  I didn't have long to play with it, but established it starts a working Ubuntu that I ran start Firefox from and access the web.  I'll have a go at installing  it onto the hard disk and take it from there.  Not sure the best way to go about that but I'll have a browse around the 64bit forum first.

Thanks again for your help.

---

### Post by chidge on 2008-07-12
I have the exact same prob as first post.
I'm after some help to get 32bit working though  :confused:
New [thread]("http://ubuntuforums.org/showthread.php?t=857665") here

---

