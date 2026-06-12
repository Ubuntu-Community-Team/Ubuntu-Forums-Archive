---
title: "Is this a hardware error?"
date: 2015-06-04
forum: Hardware
---

### Post by Morten ML on 2015-06-04
Hi

I used to dual boot windows 7 and ubuntu. W7 sometimes gave me BSOD so i thought i reinstall it and have w7 as a vm inside ubuntu. So i reinstalled but now the computer froze - in ubuntu. I mean completly froze. I could not even move the mouse. So i just powered it of and now it does not work again. I tried to boot it from a live usb and it gave me some errors. I didn't have time to read them as the boot menu came so fast, but from the kern.log i got a lot of errors and fails. I get these errors: "ata1.00: failed command: READ FPDMA QUEUED" and "nouveau E[     DRM] failed to create 0x80000080, -22" and "usb 2-2: hub failed to enable device, error -22".

So my question is is my harddisk broke?

Thanks for your help

---

### Post by tgalati4 on 2015-06-04
How old is the computer?  It could be the power supply.  Is this a laptop or a desktop?  Try reseating the RAM and clean out the machine.

---

### Post by houstonbofh on 2015-06-04
Start by booting to memtest on the hard drive or from a Live-cd.  Test the memory overnight (several cycles) to make sure it is fully warmed up.  If it reboots overnight, you know it is hardware. If not, it may still be hardware.  The error is a video driver, so try running in text (rescue) mode is see if it is more stable.

---

### Post by weatherman2 on 2015-06-04
You can test the hard drive using S.M.A.R.T.  In Linux you can try GSmartControl (possible to install in a live USB too but a little more complicated - must enable the "Universe" software repository I think.)  Without even running a test, check the S.M.A.R.T. Attributes in GSmartControl - if any are highlighted in red those are the potential problems.  You can also run a short test or an extended test of the hard drive with GSmartControl.

---

### Post by MartyBuntu on 2015-06-04
Run memtest86. Rule out memory errors first...it costs you nothing.

---

### Post by matt_symes on 2015-06-05
Hi

> **tgalati4 said:**
> How old is the computer?  It could be the power supply.

This was my first thought.

Either that or the motherboard is going.

Kind regards

---

### Post by weatherman2 on 2015-06-05
Yes, it could easily be the motherboard or power supply - but those aren't always easy to test.  RAM/Memtest and hard drive/S.M.A.R.T. are very easy to test, so those should be checked first to rule them out.

---

### Post by matt_symes on 2015-06-06
Hi

> **weatherman2 said:**
> Yes, it could easily be the motherboard or power supply - but those aren't always easy to test.  RAM/Memtest and hard drive/S.M.A.R.T. are very easy to test, so those should be checked first to rule them out.

I mostly agree.

I would say a power supply is easier to test that a motherboard.

However a faulty motherboard or power supply can cause other devices to look like they are failing when, in fact, they are not the root cause of the problem but only a symptom of some deeper problem.

In my experience, i have found if a number of devices start throwing errors in a PC at the same time then look for a deeper cause.

Kind regards

---

### Post by weatherman2 on 2015-06-06
Yes, of course a failing power supply can cause all kinds of weird issues.  But testing your power supply requires cracking open the case.  Memtest and S.M.A.R.T. tests do not.

If Memtest passes your RAM is probably good and you can move on to something else.  If it fails, then you can try swapping RAM - and if it still fails, then power supply is suspect.

---

### Post by matt_symes on 2015-06-06
Hi

> **weatherman2 said:**
> Yes, of course a failing power supply can cause all kinds of weird issues.  But testing your power supply requires cracking open the case.  Memtest and S.M.A.R.T. tests do not.

If Memtest passes your RAM is probably good and you can move on to something else.  If it fails, then you can try swapping RAM - and if it still fails, then power supply is suspect.

We'll agree to disagree on this one as, considering the OP's list of error messages, i would start looking elsewhere first.

Kind regards

---

