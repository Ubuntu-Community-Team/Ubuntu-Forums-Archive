---
title: "fancontrol/acerfand/acer_ec.pl/acerhdf for Aspire One 756 (AO756)?"
date: 2012-08-30
forum: Hardware
---

### Post by vickoxy on 2012-08-30
Hi,
i bought one nice AO756 with Intel Celeron 847, 2x 1.10GHz. And the fan is very silent;), but i noticed that it starts to work as soon as CPU 40 Degrees hat. So, i thought, why not set some fan control to make it start after 60 degrees to spare some energy, and to make it totally silent as soon as i buy SSD. The problem is that i couldn´t make any solution work. Tried:
[http://ubuntuforums.org/showthread.php?t=1424043&page=3](http://ubuntuforums.org/showthread.php?t=1424043&page=3)
[http://ubuntuforums.org/showthread.php?t=1424043&page=3](http://ubuntuforums.org/showthread.php?t=1424043&page=3)
[http://ubuntuforums.org/showthread.php?t=1741572&page=2](http://ubuntuforums.org/showthread.php?t=1741572&page=2)
[http://wiki.ubuntuusers.de/Archiv/Acer_Aspire_One](http://wiki.ubuntuusers.de/Archiv/Acer_Aspire_One)

Well, i tried some, but not all options. So i try here if someone with more experience can make some of known solutions workin...#

Thanks!

Edit: i tried to use acerhdf to control the fan. But it seems that the bios is not supported. Any idea how to make it work?

```
linux@linux:~$ dmesg | grep acerhdf [   14.142604] acerhdf: Acer Aspire One Fan driver, v.0.5.24
[   14.142626] acerhdf: unknown (unsupported) BIOS version Acer/AO756/V1.05, please report, aborting!
```

---

### Post by vickoxy on 2012-08-31
In some previous versions of ubuntu, someone just make patch for the newest version of bios and aspire modell (acerhdf.c)
[http://ubuntuforums.org/showthread.php?t=1424043&highlight=Acer+aspire+fan&page=3](http://ubuntuforums.org/showthread.php?t=1424043&highlight=Acer+aspire+fan&page=3)

Well, would it be worth to try to patch it? If yes, could someone help me, because i don´t know how to add new modell...
This is some output:

```
linux@linux:~$ dmesg | grep acerhdf
[   17.761451] acerhdf: Acer Aspire One Fan driver, v.0.5.24
[   17.761473] acerhdf: unknown (unsupported) BIOS version Acer/AO756/V1.05, please report, aborting!

```

```
linux@linux:~$ sudo modprobe acerhdf
[sudo] password for linux: 
FATAL: Error inserting acerhdf (/lib/modules/3.2.0-29-generic/kernel/drivers/platform/x86/acerhdf.ko): Invalid argument
linux@linux:~$ 

```

---

### Post by vickoxy on 2012-09-01
Found some solution here-this script does stop the fan, but it won´t activate it again-so be careful...!!!

[http://www.acer-userforum.de/linux/45522-aspire-one-d250-luefterregelung-als-perl-script.html](http://www.acer-userforum.de/linux/45522-aspire-one-d250-luefterregelung-als-perl-script.html)

---

### Post by vickoxy on 2012-09-02
No one?

---

### Post by vickoxy on 2012-09-08
Really no one?

---

### Post by freshbook on 2012-09-12
hello vickoxy, 

i have also purchased the acer aspire one 756 (Celeron 847, 4GB RAM) a couple of days ago. most of the hardware worked out of the box with xubuntu 12.04.

i'm quite pleased with the performance so far, but as you have already mentioned ... the fan behavior does need improvement. mine is constantly on and it kind of worries me. the notebook gets pretty warm on the bottom side and on the left palm rest (within 10-15min of operation). did you experience that too?

so i wanted to say "thank you" for bringing this issue up. i hope someone finds the solution (i'm short on time right now, because i have to finish my thesis these days). as soon as i have more time to spare, i'll look into this further. 

on my older notebook i have installed crunchbang linux (debian+xfce version). i might try that on the AO756 and see whether the fan performs better with crunchbang - i'll report back once i actually get around to do that.

until then ... crossing fingers that someone here can help us out with AO756 and xubuntu. 

greetings from vienna

---

### Post by vickoxy on 2012-09-12
Greetings from Vienna too!
Well, i am for now really satisfied with my A0756. I do not experience to much heating (Celeron 847) and most of the time i use the computer without fan-i activated this perl script:
[http://www.acer-userforum.de/linux/45522-aspire-one-d250-luefterregelung-als-perl-script.html](http://www.acer-userforum.de/linux/45522-aspire-one-d250-luefterregelung-als-perl-script.html)
It switches off the fan-an that is it-if you want the fan again you have to restart computer.
So, as said, my AO756 works without fan at 50-60-70 Degrees (libreoffice, chrome, pdf reader) - as soon as i stop working it goes down to 48-52 Degrees. It gets little bit warm,but i like it more warm, as loud ;)
Still, would like to have some functional fan control...

---

### Post by vickoxy on 2012-10-09
No one?

---

### Post by sisyphus1978 on 2012-11-08
I have an AO753 and am having similar problems. Seems to be we have to edit the kernel to include our bios/model numbers. How to do that is another question. I don't want the fan on all the time, nor off all the time.

---

### Post by vickoxy on 2012-11-11
So, we need just to wait?

---

