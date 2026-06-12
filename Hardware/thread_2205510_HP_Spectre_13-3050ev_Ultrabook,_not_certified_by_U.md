---
title: "HP Spectre 13-3050ev Ultrabook, not certified by Ubuntu"
date: 2014-02-14
forum: Hardware
---

### Post by marvelousvts on 2014-02-14
[FONT=arial]Hello!
Can I install ubuntu in [COLOR=#000000]**HP Spectre 13-3050ev Ultrabook?    **[/COLOR][/FONT][http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c04064322](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c04064322)[FONT=arial][COLOR=#000000][B]
[/B][/COLOR][/FONT][FONT=arial]I don't have problem if touch screen doesn't work...

kind regards![/FONT]

---

### Post by oldfred on 2014-02-14
That it is very new Haswell processor and an Ultrabook make it a bit more difficult.

Intel has offered lots of updates to not just video driver, but kernel and other support software but a lot of it has not made it into Ubuntu until 13.10, 12.04.4 and even more int 14.04. Even though 14.04 is quite a ways away some have tried it also.

HP's also seem to have other issues. Some others.
       acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
      
 HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Even though a Dell it mentions some common issues with Intel chips.

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

See also link in my signature for other Ultrabook issues and suggestions. Best to try live installer in live mode and see what works (or does not).

 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

 Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)
      
 Intel "Haswell" System 76 Iris Pro Linux Graphics Yield Some Wins Against Windows
[http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1)

---

### Post by G_Ajith_Kumar on 2014-02-14
Hi Welcome! i am writing from an old HP Laptop 2006 model. So very good chances that things will work out. :) However some finer and latest applications might not work correctly or not at all. You have expressed your thought that you do not mind the touch screen not working.That's a good start point.

Best option would be to TRY Ubuntu from a CD. If it works then go ahead and install; if not you can maintain with you current operating system till Ubuntu has all the drivers for your system.

These links might help you.

link for downloading Ubuntu 12.04 [http://releases.ubuntu.com/precise/u...ktop-amd64.iso]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-desktop-amd64.iso")
link for making a DVD?CD  [http://www.ubuntu.com/download/deskt...dvd-on-windows]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows")
link for running Ubuntu from a CD [http://www.ubuntu.com/download/deskt...re-you-install]("http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install")
link for configuring BIOS [http://www.wikihow.com/Set-Bios-to-Boot-from-a-CD-ROM](http://www.wikihow.com/Set-Bios-to-Boot-from-a-CD-ROM)

Good Luck :)

---

