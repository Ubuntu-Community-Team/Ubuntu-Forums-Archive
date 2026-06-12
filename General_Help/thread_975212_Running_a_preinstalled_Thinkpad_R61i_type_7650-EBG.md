---
title: "Running a preinstalled Thinkpad R61i type 7650-EBG - is HArdy kernel upgrade safe?"
date: 2008-11-08
forum: General Help
---

### Post by alexcckll on 2008-11-08
Hi folks, 

I'm running a preinstalled Thinkpad R61i type 7650-EBG, currently at 8.04.1 level, sitting on kernel 2.6.24-19.


I was wondering - is it safe to accept current recommended updates, or is it still advisable to hold off from -21 updates?

Also - will other pacgaes install OK if I leave it at -19?

I've only been using Linux since May... so please be gentle...

---

### Post by alexcckll on 2008-11-10
Bumping...

---

### Post by igknighted on 2008-11-10
I would strongly recommend installing all available updates.  That kernel was tested for months before release, and it offers many bug fixes and security updates.  Note that you are still using the same kernel version, the -19 versus -21 are just patches added on top.

---

### Post by alexcckll on 2008-11-13
Yeah - but with all the problems reported with the -21 kernel (video and Wifi being broken by the update)... has anyone received word from Canonical that the current package is production-standard?

I bought my laptop *pre-installed*; and am a newbie to Linux... so I'd need someone else to confirm that it isn't going to break an R61 with the model number above...

Has anythign been heard?

---

### Post by kostkon on 2008-11-13
> **alexcckll said:**
> Yeah - but with all the problems reported with the -21 kernel (video and Wifi being broken by the update)... has anyone received word from Canonical that the current package is production-standard?

I bought my laptop *pre-installed*; and am a newbie to Linux... so I'd need someone else to confirm that it isn't going to break an R61 with the model number above...

Has anythign been heard?
These type of problems happen every time there is a kernel update for some people. And there is an explanation for that.

The great majority of users don't get any problems after a kernel update.

But in most cases where there is a problem, it's from people that modified their system in such way that an kernel update will break it. For example, some people install drivers for their graphics card directly from Nvidia (or Ati) (i.e. manually compiling them or some other way) and not from the repos so a kernel update will definitely throw them a black screen on the next boot after the update. Similar things for WIFI.

Nevertheless, this is going to change, 8.10 supports DKMS, so manually compiled drivers will be automatically recompiled after a kernel update, thus such problems should gradually eclipse.

There are, of course, some cases where you get problems (for example, lose sound) after such an update without any explanation. These are unfortunate but I don't think are very widespread.

So, my answer to you, yes, you should always install all of the available updates. Even if this update breaks something in your system, you can always use the previous kernel that worked OK. So, it is relatively safe.

---

### Post by alexcckll on 2009-01-16
Bumping this - is the above model safe to accept  updates to 8.04.2 point release?

I have about 103 updates waiting for me.. has anyone else recently accepted security-only updates onto the above model of laptop... will my machine be OK, or am I likely to be knocked offline until I get to a vendor or expert?

---

