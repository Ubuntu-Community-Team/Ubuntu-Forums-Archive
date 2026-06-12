---
title: "Ubuntu 14.04 LTS on HP Compaq dc7800"
date: 2020-02-09
forum: Hardware
---

### Post by rokas-j on 2020-02-09
I'm not sure if this is OS dependent =).

If electricity islost for a while or after plugging off computer (extension cord) fromsocket this happens:

_Either computer turns on itself orwhen you press computer's power on button beep sound is emitted and__this__ screen appears:_
162 – System Options NotSet
Your system configuration has changed since your last boot.Addition of a hard drive, etc., or loss of power to the Real TimeClock has occured. Pressing F1 will record the new configuration. Ifthis message persists, you may need to replace the onboard battery.


InitializingIntel(R) Boot Agent GE v1.2.50
PXE 2.1 Build 086(WfM 2.0)


The followingconfiguration options were automatically updated:
  Memory: 3072MB
  Disk: 160 GB                WDC WD1600AAJS-60WAA0
 CD-ROM:                    TSSTcorp CDDVDW  TS-H653N
    If you arerunning Unix, you need to configure your system using the ComputerSetup Utility (F10).
CMOS checksuminvalid, default values loaded.


F1: SaveChanges

_After that, computer boots up and when you turn offand turn it on second time the screen appears:_
163 – Time &Date Not Set
The system time is invalid. This may be a result of aloss in battery power. Set the correct time and date using youroperating system. If this message persists, you may need to replacethe onboard battery.


InitializingIntel(R) Boot Agent GE v1.2.50
PXE 2.1 Build 086(WfM 2.0)


F1: Boot

---

### Post by CatKiller on 2020-02-09
That's hardware: the little battery on your motherboard has run out, so it can no longer keep its settings without mains power. They're cheap.

As another matter, 14.04 went end of life in April last year. You should upgrade to a supported release.

---

### Post by rokas-j on 2020-02-10
Hello =),

Thanks for an answer.
I did replace a Lithium Cell CR2032 V3 battery.
_However, this screen about time and date still appears, although time and date displays correctly:_
[COLOR=#000000]163 &#8211; Time & Date Not Set[/COLOR]
[COLOR=#000000]The system time is invalid. This may be a result of a loss in battery power. Set the correct time and date using your operating system. If this message persists, you may need to replace the onboard battery.[/COLOR]


[COLOR=#000000]Initializing Intel(R) Boot Agent GE v1.2.50[/COLOR]
[COLOR=#000000]PXE 2.1 Build 086(WfM 2.0)[/COLOR]


[COLOR=#000000]F1: Boot[/COLOR]

---

