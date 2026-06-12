---
title: "Lucid and Aiptek tablet 8000u"
date: 2010-05-10
forum: Hardware
---

### Post by rvlander on 2010-05-10
Hello,

I am trying to get working a 8000u tablet on 10.04 but I am struggling.

I tried this :

[https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) which seems to follow that discussion : [https://bugs.launchpad.net/ubuntu/+sour  … bug/361693]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-aiptek/+bug/361693").


Nothing appears in** /dev/input**

**lsusb** says:
[INDENT]Bus 003 Device  004: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet

[/INDENT]**dmseg** seems to signal a problem when trying to speak with the tablet
[INDENT][   18.255602] aiptek 3-2:1.0: Aiptek tried all  speeds, no sane response
[   18.255619] aiptek: probe of 3-2:1.0  failed with error -12
[   18.255653] usbcore: registered new  interface driver aiptek
[   18.255657] aiptek: v2.3 (May 2,  2007):Aiptek HyperPen USB Tablet Driver (Linux 2.6.x)
[   18.255659]  aiptek: Bryan W. Headley/Chris Atenasio/Cedric Brun/Rene van Paassen

[/INDENT]**xinput list** says the tablet is not present.


Where does the problem come from ?


Thanks in advance,


rvlander

---

### Post by andy_spoo on 2010-05-16
Hi. I'm having fun with a MD 41217 myself!

That help document is very incomplete.

For example, the line:-

LABEL="xorg_aiptek_end

has missing speach-marks at the end, and should read LABEL="xorg_aiptek_end"

Don't forget that you need to install the driver package: xserver-xorg-input-aiptek

sudo apt-get install xserver-xorg-input-aiptek

God knows what else is wrong with that document. If I'd known how to update it, I would have!!

---

### Post by hva on 2010-05-17
> **andy_spoo said:**
> Hi. I'm having fun with a MD 41217 myself!

That help document is very incomplete.

For example, the line:-

LABEL="xorg_aiptek_end

has missing speach-marks at the end, and should read LABEL="xorg_aiptek_end"

Don't forget that you need to install the driver package: xserver-xorg-input-aiptek

sudo apt-get install xserver-xorg-input-aiptek

God knows what else is wrong with that document. If I'd known how to update it, I would have!!

the terrible error has been corrected. Instead of complaining, if you know what horrible things are wrong in the document, go and fix it, otherwise please respect the efforts of people that try to share useful informations.

---

### Post by hva on 2010-05-17
> **andy_spoo said:**
> Hi. I'm having fun with a MD 41217 myself!

That help document is very incomplete.

For example, the line:-

LABEL="xorg_aiptek_end

has missing speach-marks at the end, and should read LABEL="xorg_aiptek_end"

Don't forget that you need to install the driver package: xserver-xorg-input-aiptek

sudo apt-get install xserver-xorg-input-aiptek

God knows what else is wrong with that document. If I'd known how to update it, I would have!!

"very incomplete" means a missing quote sign at the end of a line?

---

### Post by rvlander on 2010-05-17
@andy_spoo :
I don't think that document is incomplete. Installing xserver-xorg-input-aiptek was also mentioned.

@all
Anyway, it still does not work although working on windows ... Don't tell me it is my only fate to use that OS.

By the way, any piece of advice concerning a tablet 100% linux comptatible (mainly lucid), with good resolution and big surface for a price lower than 100~150€ ?

Bye

---

