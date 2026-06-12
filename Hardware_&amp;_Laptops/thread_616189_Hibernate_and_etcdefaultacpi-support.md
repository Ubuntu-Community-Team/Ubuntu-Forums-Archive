---
title: "Hibernate and /etc/default/acpi-support"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by mikeage on 2007-11-17
Hi,

I recently started trying to use the hibernate program to put my desktop into S3 suspend-to-ram. It suspends just fine, but upon resuming, there's no networking. Rerunning /etc/init.d/networking fixes the problem.

I've added "networking" to STOP_SERVICES in /etc/default/acpi-support, but it's not doing anything. In fact, having put deliberate garbage in that file and in the resume.sh script in /etc/acpi/, it appears that it's not running any of those scripts at all.

I'm hibernating using /usr/sbin/hibernate, not using any button events or any GUI (it's a server that doesn't have a graphical desktop).

Any ideas what might be wrong? Thanks in advance.

---

### Post by nick_h on 2007-11-18
You should be running /etc/acpi/hibernate.sh

To debug, try adding **set -x** to the hibernate.sh script as described [here](http://ubuntuforums.org/showthread.php?t=505890) (for sleep).

---

### Post by mikeage on 2007-11-18
Ok. That script seems to restart networking properly... but it doesn't suspend!

I've placed logs (kern.log, as well as the output from stdout and stderr from hibernate.sh) at [http://mikeage.net/hibernate.tgz](http://mikeage.net/hibernate.tgz)

---

### Post by nick_h on 2007-11-18
OK - I didn't read your original post carefully enough.  In Ubuntu, Suspend to RAM (S3) is referred to as sleep or suspend whereas Suspend to Disk is referred to as hibernate.  When you said you were running a hibernate script I assumed you wanted to Suspend to Disk.

If you want to test Suspend to RAM you need to run /etc/acpi/sleep.sh probably with the parameter "force".

With the Suspend to Disk it looks like it is a swap file problem - in your kern.log there is the line "swsusp: Cannot find swap device, try swapon -a."

I seem to remember one or more threads giving a solution to this problem but I can't find one at the moment.

---

### Post by mikeage on 2007-11-18
I was a little confused regarding the terminology since the /usr/sbin/hibernate script handles both (in any case, what's that one for, if I'm supposed to use "/etc/acpi/sleep.sh force" (or /etc/acpi/hibernate.sh)?

In any case, /etc/acpi/sleep.sh works! (even without the force).

As an aside, I know I have a problem with my swap partition, which I have to fix. It's not being mounted on boot; probably the wrong signature or something.

Thanks for your help! Now to get PME working...

---

