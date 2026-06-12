---
title: "SMART Attributes Data Structure"
date: 2012-02-11
forum: Hardware
---

### Post by bigdeso on 2012-02-11
What is the SMART Attributes Data Structure I'm seeing under the Attributes tab in GSmartControl?
Are these readings from my drive or what the manufacturer says the drive has to reach as a basis to determine whether the drive is on it's way out?
Because I'm seeing a lot of 'old age' and 'pre-failure', as-well as two links "Reallocated Sector Count" & "Spin-Up Retry Count" being highlighted pink

Advice very much appreciated :popcorn:

---

### Post by ahallubuntu on 2012-02-11
Those S.M.A.R.T. attributes are from the drive itself, data indicators reported by the drive's firmware back to GSmartControl.

The attributes in pink are really the ones you want to worry about.  The "old age" etc. are just notations for what kind of attribute it is. 

Reallocated sector count is not fatal but a serious warning.  Reallocated sectors are "spare" sectors that replaced failed sectors.  Every drive has some spare sectors so when bad ones are detected, the drive firmware marks them as "do not use" and replaces them with spares.  If sectors keep failing, eventually you will run out of spares - then the drive is basically no longer safely usable.

One or two reallocated sectors on an older drive is not unusual - just something to keep an eye on.  If that number keeps going up, then you worry.

Pending Sectors ARE bad - they are sectors that could not be read on last attempt to access them.  Pending sectors can mess everything up when the operating system tries to read from them - they can even freeze it or make it really slow.  Sometimes if you zero out a drive (erasing everything on it) those sectors will clear and/or be reallocated.  But, you didn't say you had any of those.

Spin-up Retry Count is definitely worrisome - could be a power problem in the drive itself.

It goes without saying that you have all important data backed up from this drive.  RIGHT?  If not do that ASAP.

---

### Post by bigdeso on 2012-02-11
Thanks a lot for your reply, nicely in-depth! But yea, I finished moving all my stuff off it today, hence the test to see if it's worth putting it all back, everything indicated old age and a few we pre-failure so I won't be using this drive anymore, thanks for letting me know; the tab isn't descriptive at all

---

### Post by ahallubuntu on 2012-02-11
Again, "old age" and "pre-failure" don't indicate problems, these are just types of attributes.  Even a new, healthy drive will show the same tags.  (Try it!) The ones to worry about are the ones in pink.  S.M.A.R.T. is a good thing to get familiar with to monitor healthy drives, too.

---

