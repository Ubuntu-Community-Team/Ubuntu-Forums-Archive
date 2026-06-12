---
title: "SMART says drive ready to fail"
date: 2018-05-19
forum: Hardware
---

### Post by ra7411 on 2018-05-19
SMART says drive ready to fail.

It's a Hitachi 1tb with about 3yrs 8mns run time on it.

Is there any remedy, or should I just drill a hole in it and toss it?

---

### Post by kurt18947 on 2018-05-19
I'm not sure how reliable SMART data is. 3 years 8 months seems within the expected lifetime of modern hard drives though perhaps in the early end of the range. If it were mine, I'd be sure to back up any important data frequently and monitor SMART state. If an unexpected total failure would make my life complicated, I'd replace it. As far as remedies, there are none that I know of.

---

### Post by TheFu on 2018-05-19
backup.
SMART produces all sorts of raw data, some it useful. Most is not.  Depends on what it actually says.   Old-Age isn't sufficient to swap out a HDD, IMHO, unless it is 10+ yrs old.  I have some old, old, 320G drives from the early 2000s, still going fine.

Some SMART data isn't about the disk at all, but the controller and cables and power.

Remedies?  Move the HDD out of any critical storage placement. Perhaps use for sneakernet only?  I only drill 8 holes in disks once they'd actually failed without any relocation sectors remaining.

So ... first, we'd need to see the SMART data.

---

### Post by QIII on 2018-05-19
Hello!

What does it say *exactly*?  

It may not be about to fail.  The terms used by SMART can be confusing.

Please copy and paste the output.

---

### Post by ra7411 on 2018-05-19
> **QIII said:**
> Hello!

What does it say *exactly*?  

It may not be about to fail.  The terms used by SMART can be confusing.

Please copy and paste the output.

Below is a screenshot of  the Disks Short test output.

[ATTACH=CONFIG]279753[/ATTACH]

---

### Post by rsteinmetz70112 on 2018-05-19
Others may disagree but that seems to be a pretty large number of reallocated sectors, if that is increasing I'd be concerned. I see a new hard drive some where in your future. Luckily a new hard drive will not cost that much. If you decide to change out the drive ddrescue is a good way to clone the drive.

---

### Post by QIII on 2018-05-19
Yep. Back up an hour ago.  Go to your local computer components shop right now.  Don't wait for a new disk to show up in the mail.

---

### Post by TheFu on 2018-05-19
> **rsteinmetz70112 said:**
> Others may disagree but that seems to be a pretty large number of reallocated sectors, if that is increasing I'd be concerned. I see a new hard drive some where in your future. Luckily a new hard drive will not cost that much. If you decide to change out the drive ddrescue is a good way to clone the drive.

I've never seen that GUI view.  I'm used to seeing "raw" values for SMART data, as produced by smartctl.
I consider any number of relocated sectors over 10 a disk replacement requirement, but there is time unless they are failing rapidly.  Sometimes, there will  be 1-5 relocations, but none for the next year or two.  The rate of the relocation events matters.  Weekly monitoring is necessary.

If the raw number is over 10 (and 1300 definitely is), I'd expect total failure any minute and act accordingly.

If you have backup religion already, then this is a minor inconvenience and money hassle. It isn't about data loss.

---

### Post by lisati on 2018-05-19
Making a regular backup of your important data is always a good idea.

Side note: The laptop I use for day-to-day stuff the number of reallocated sectors is a lot higher, much much higher. It doesn't always run at its best, which can be annoying.

---

### Post by ra7411 on 2018-05-19
Yeah, I'm going to drill it and ditch it.

Thanks all.

---

### Post by rsteinmetz70112 on 2018-05-20
> **TheFu said:**
> I've never seen that GUI view.  I'm used to seeing "raw" values for SMART data, as produced by smartctl.


That view looks like gnome-disks which probably calls smartctl or some related library to fill in the data, but I'm not sure. I find gnome-disks very useful for quickly getting a lot of information about the devices on the system.

---

### Post by undoIT on 2018-05-21
Yes, it is gnome-disks.

@ra7411

Were you noticing specific issues that made you think the disk might be failing or did you just randomly check and see the Smart Data & Self-Tests FAILING message?

---

