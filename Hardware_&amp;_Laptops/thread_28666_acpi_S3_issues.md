---
title: "acpi S3 issues"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by Miggy on 2005-04-21
Hi,

I've encountered some issues with acpi s3 mode.
First:
entering the commands from the console as root:

"echo 3 > /proc/acpi/sleep" 
and
"echo -n mem > /sys/power/state"

both works. The computer goes tu suspend an wakes up when i press a key.
But calling the S3 mode with these two command lines doesn't execute the scripts in /etc/acpi (sleep.sh, prepare.sh, resume.sh).
Now, after waking up from suspend I need to restart the hotplug service, so my usb scanner and usb stick work again, and this happens in the scripts in /etc/acpi.

I wanted to automate this. So I found out that in /etc/default/acpi-support you can change some settings for acpi. First of all I enabled ACPI_SLEEP=true, so I can go to S3 mode via the logout dialog. 
My STOP_SERVICES Option looks like this:
STOP_SERVICES="mysql hotplug"

If I now go to S3 via the logout screen the computer resumes immediately (remember: this is not the case with the direct "echo -n mem > /sys/power/state" command in the console).
I'm very confused about this behaviour because the sleep.sh script also triggers the "echo -n mem > /sys/power/state" command" because in /etc/default/acpi-support  ACPI_SLEEP_MODE=mem is set.

Any suggestions what I'm doing wrong?

Not enough with this  :-?  I have another issue with S3. I have a Creative Labs Audigy 2 Soundcard. After S3 resumes no sound is available any longer, although alsamixer shows all the mixers.
My first idea was to write the module "snd_emu10k1" to the MODULES="snd_emu10k1" line in /etc/default/acpi-support. But this doesn't seem to solve the problem.

So, any help would be appreciated. Thanks in advance!
Miggy

---

### Post by Miggy on 2005-04-21
Ok, since nobody has replied yet, i've tried another thing.
When I fire the following command line, the suspend behaviour is the same as when I go to s3 via the logout dialog or a direct invocation of the script /etc/acpi/sleep.sh, i.e. the computer powers down and immediately resumes from S3:

"/etc/init.d/hotplug stop && echo 3 > /proc/acpi/sleep  && /etc/init.d/hotplug start"

The interesting thing now is, if I only fire the following command line, the computer stays in S3 until I press a key to wake it up:

"/etc/init.d/hotplug stop && echo 3 > /proc/acpi/sleep"

So it seems that, if there is a command queued directly after the "s3 command", the computer immediately resumes. 
Now anyone has suggestions how to work around this issue?
Miggy

---

