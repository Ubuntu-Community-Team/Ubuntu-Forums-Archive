---
title: "D945GCLF2 and ACPI"
date: 2009-06-20
forum: Hardware
---

### Post by richbl on 2009-06-20
Hello all,

I thought I'd xpost this from the Intel Community Forums, as this issue may be related to running Ubuntu (though, as it's a BIOS issue, I'd assume that this is not the case).

I'm running 9.04 (jaunty), and my goal with this new mini-itx box is to build a backup server that wakes up at a predefined time, runs a backup script, and then goes back to sleep until it's time to perform backups again.

I recently purchased a D945GCLF2 board, and I'm having some difficulty with ACPI S3 and S5 wake state setting is BIOS.

At the moment, I am unsuccessful in configuring BIOS (rev. 009.0528.2014) to permit a timed wake on S5 (or S3).

Using UTC time from the RTC, I've attempted to set the "Wake System from S5" feature for either daily wake or a date-specific wake, and no joy. I've also determined that when the system is in a S3 state, the board does not wake.

Separately, I can confirm that a software enabling of the RTC (via /sys/class/rtc/rtc0/wakealarm ) does correctly wake the board on S3 or S5, so the issue appears to be centered around a problem with BIOS settings.

As an aside, and perhaps as a clue, a cat of /proc/driver/rtc never identifies the correct BIOS wake configuration. Neither is the date/time for the next wake set, nor is the alarm_IRQ enabled. I'm not certain of the correlation of this observation, but it is a little strange nonetheless.

Has anyone been successful in enabling the RTC wake in BIOS? If so, what BIOS release was used, and what was the BIOS config settings?

Please advise.

Thanks.

rich

---

### Post by richbl on 2009-06-27
**bump bump**

Anybody?

---

### Post by bluetoad on 2009-07-15
I've found that 

echo +300 >/sys/class/rtc/rtc0/wakealarm 

will set the wakeup time in 30 seconds.  Only tried wakeup from S3 (suspend) and it seems to be fine.

cat /proc/driver/rtc

and make sure the alarm date is sane.  If you've been putting the Epoch time wakealarm you would probably have seen a strange looking alarm date

---

### Post by richbl on 2009-07-15
Thanks for the response, but as I mentioned in the original post, setting wake time via command line is not the issue. 

The real issue centers on the ACPI BIOS settings for the D945GCLF2 board.

thanks,

rich

---

### Post by bluetoad on 2009-07-15
How are you setting the alarm time?

---

### Post by richbl on 2009-07-15
> **bluetoad said:**
> How are you setting the alarm time?

Alarm time is enabled via ACPI settings in the BIOS.

I'm not sure I understand the purpose of your question?

thanks,

rich

---

