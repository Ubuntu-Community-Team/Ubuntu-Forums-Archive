---
title: "Asrock ION 330HT rtc wakeup working?"
date: 2010-01-10
forum: Hardware
---

### Post by olliraa on 2010-01-10
I'm trying to get the rtc wakeup working. I can set the rtc alarm time from Ubuntu 9.10 and the command 

cat /proc/driver/rtc

gives me rasonable results (date & time correct). Bios time is in UTC, so it should not be a problem. However the computer never wakes :( I have tried both RTC WAKEUP -feature on/off in BIOS, but the result is the same. I have also tried to run the command 

sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm"

as root, but no avail. 

Has someone got this working with the Asrock Ion 330?

---

### Post by olliraa on 2010-01-13
Ok, got an interesting reply from ASrock tech support... They sent me a new test bios (1.12), but at the same time told me that the rtc does not work with 9.10. They had tested rtc wakeup with 9.04 and Fedora 12 and stated it works fine. They stated also that it's a "kernal setting" in 9.10 that prevents the rtc from working. When I then asked to define that "kernal setting" more precisely they didn't answer.

Any gurus out there? What on earth could the "kernal setting" be? I really woud not like to downgrade to 9.04 just for the rtc.

---

### Post by JonasBardino on 2010-01-23
Hi Olliraa

Unfortunately, no :-(
 
From the MythTV wiki at
[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
I would have guessed it to be the hpet=disable settings, but I've tried all the suggestions there along with completely disabling the hwclock/hwclock-save upstart actions.

I also tried the reboot hint from 
[http://ubuntuforums.org/showthread.php?t=305751](http://ubuntuforums.org/showthread.php?t=305751)
without luck.

Wake from RTC works when manually set in the BIOS but no matter of tweaking the BIOS or Karmic has helped me to effectively set it from Linux.

I still haven't tried a custom kernel, using suspend instead of power off or upgrading the BIOS to 1.10, though. 

Please report back if you make any progress or hear from Asrock!

Cheers, Jonas

---

### Post by JonasBardino on 2010-01-23
Status update:
Upgrading to latest official BIOS, 1.10, does not help.
Neither does using the 2.6.32 kernel from the upcoming Ubuntu 10.04 or the 2.6.32.4 or 2.6.33rc4 kernel from the Ubuntu mainline kernel archives.

Cheers, Jonas

---

### Post by JonasBardino on 2010-01-29
Success!!

I contacted ASRock support about the problem and received their beta 1.12 BIOS and some information similar to what olliraa reported.

After upgrading the BIOS a nice new 'By OS' option appeared for the RTC wake up setting in the BIOS and with that one enabled wake up from off now works: tested with a Xubuntu 9.04 Live and wth my Mythbuntu 9.10 installation (both 64-bit).

I just use the latest linux-image-2.6.31-17-generic kernel from karmic-updates and no longer need to touch hpet or hwclock settings at all.

All my tests with BIOS version 1.10 and 1.00 indicate that RTC wake up from off is **not** supported with **any** Linux in the official BIOS releases. I did manage to get wake up from suspend-to-ram working with those BIOS versions, though.

So now I'm just waiting for an official 1.10+ BIOS release - but thanks to ASRock for actually caring about their Linux users!

Cheers, Jonas

---

### Post by RaiDRo on 2010-02-15
Hi Jonas,

running yavdr on the ASRock ION 330HT, I have the same problems as described above. Since the ASRock support is closed until  2010/2/21, there is no possibility to get this beta bios directely from ASRock. Is there another download URL anywhere?

Thanks

Rainer

---

### Post by gdachs on 2010-02-25
Hi RaiDRo,

like you I am using yaVDR on an ASRock ION 330HT. Like you I am waiting for the new BIOS. In the meantime you could use nvram-wakeup with the ASRock, it works just fine.

Move the attached file nvram-wakeup.conf.txt to /etc/nvram-wakeup.conf and the file vdr-nvram-wakeup.conf.txt to /etc/vdr/vdr-nvram-wakeup.conf. If you made recently 
```

sudo apt-get update
sudo apt-get dist-upgrade

```you should have nvram-wakeup already installed. Don't forget to disable acpi-wakeup in the file /etc/vdr/vdr-addon-acpiwakeup.conf.

If you have more questions regarding yaVDR you can find me in the [VDR-Portal]("http://vdr-portal.de"). There exists a yaVDR forum. It is German, but posting in English is just fine.

Gerald

---

