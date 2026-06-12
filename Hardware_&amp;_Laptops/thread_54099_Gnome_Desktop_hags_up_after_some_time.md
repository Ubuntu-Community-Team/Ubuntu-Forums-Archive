---
title: "Gnome Desktop hags up after some time"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by rogeriovinhal on 2005-08-03
I have a recurrent problem with Gnome. It just locks up everything after some time of execution no matter what I am doing. I have experienced lock ups with the computer stopped, in firefox, in nautilus, in terminal...

I have a overclock in my computer, but that have never been a problem and i have this same overclock for about 2 years, so i don't think it is the reason.

What can I do?

---

### Post by varunus on 2005-08-03
Is this lockup a hard freeze?  You can't hit CTRL-ALT-F1 to go to a terminal?  You can't move the mouse?  Or can you just not click on things?

This does sound like an overclock problem, frankly.  I've seen Ubuntu generate more heat on some computers than it should because acpi was configured strangely...Is cpufreq scaling working for you (ie, post the output of lsmod in a terminal here)?  What processor do you have?

---

### Post by rogeriovinhal on 2005-08-03
It locks up everything, even the mouse and CTRL + ALT + Anything won't work.

It really looks like an overclock problem, but this overclock has never given me any problems in so many time, even in Slackware, what i was using before...

The temperature is fine, is even lower than in Windows. It is 42 C.

My lsmod is this:

```
Module                  Size  Used by
proc_intf               4100  0
cpufreq_powersave       1920  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
freq_table              4100  0
fglrx                 229568  7
video                  16260  0
battery                10244  0
container               4608  0
button                  6800  0
pcc_acpi               11264  0
sony_acpi               6280  0
ac                      4996  0
ipv6                  229504  9
8139too                24320  0
8139cp                 19200  0
mii                     4736  2 8139too,8139cp
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
tsdev                   7488  0
usbhid                 29376  0
ehci_hcd               29444  0
ohci_hcd               19848  0
usbcore               107384  4 usbhid,ehci_hcd,ohci_hcd
i2c_nforce2             6400  0
i2c_core               21264  1 i2c_nforce2
nvidia_agp              7452  1
agpgart                31784  2 nvidia_agp
analog                 10784  0
gameport                4608  1 analog
floppy                 54864  0
pcspkr                  3816  0
rtc                    12216  0
evdev                   9088  0
ntfs                   97136  1
nls_iso8859_1           4224  1
nls_cp437               5888  2
vfat                   12928  1
fat                    37792  1 vfat
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
reiserfs              225616  1
ext3                  120968  0
jbd                    54168  1 ext3
ide_generic             1664  0
ide_disk               18176  5
amd74xx                13340  1
ide_core              118988  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   26164  718
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

```

My processor is Athlon XP 1700+ and the over is to 2600+. I know it sounds a little agressive, but it hasn't given me any problems, even doing some stress tests.

I also installed Ubuntu in RasierFS, it seems tha most people install in ext3, but I find RaiserFS faster...

---

### Post by varunus on 2005-08-03
Wow, that does sound like an aggressive overclock...but 42C is good, so I don't know what the problem is.

Can you leave the System Monitor (Applications->System Tools->System Monitor) open?  And also add a System Monitor applet to your panel?  Then maybe watch them and see if something happens when you hard freeze...

---

### Post by heimo on 2005-08-03
[QUOTE=rogeriovinhal]
I have a overclock in my computer, but that have never been a problem and i have this same overclock for about 2 years, so i don't think it is the reason.

What can I do?[/QUOTE]

I'd compile kernel. :D Then I'd undo the overclocking and compile kernel. That's one of the best stress tests (and it has a tradition in testing stability and performance). But of course... you don't need to. Run lots of heavy applications and try to reproduce the freeze. Then undo overclocking and redo the same test. This is just to rule out the most obvious reason first.

---

### Post by rogeriovinhal on 2005-08-03
Actually, i did compile the kernel in the past when i was using Slackware... Twice.
And twice it worked fine.

I am afraid to compile the kernel in Ubuntu, because everything works so perfect that I think that I can compile a kernel missing something and waste hours of work.

The most strange about this freezings is that they are impredictable, right now i am in Ubuntu for about 1 hour and nothing happened, yesterday it froze about 20 minutes after login.

EDIT: It seems that those freezings disappeared after getting the K7 kernel in synaptic. I'm running for some hours and no freezings.

---

### Post by heimo on 2005-08-03
I wasn't too serious about compiling kernel. (But if you want to use that as a stress test, there's no reason to actually install the new kernel or do any bootmanager configuration changes, just the compiling stuff.) However, as you have so frequent hangups, why not undo the overclock and see if it occurs again. If it's not overclock related, it will happen anyway. I'm just saying that you should always rule out this kind of reasons when it's so easy to do.

Read log file /var/log/messages and put one terminal on your desktop, run tail -f /var/log/messages on it and keep it always on top, so when the hangup happens, you may get some error message just before.

---

