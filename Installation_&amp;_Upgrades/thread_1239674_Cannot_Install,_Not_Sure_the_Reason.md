---
title: "Cannot Install, Not Sure the Reason"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by smakand on 2009-08-13
So I've been trying to install SOME type of linux on my desktop for a while. Most give me an error which looks like this (from Fedora, Ubuntu Studio gives me the same message)

[[IMG]http://img515.imageshack.us/img515/7193/dsc01368v.th.jpg[/IMG]]("http://img515.imageshack.us/i/dsc01368v.jpg/")

On Ubuntu 32 (with acpi=off), it shows the ubuntu screen for a while then exits to console, looking something like this:

[[IMG]http://img29.imageshack.us/img29/7633/dsc01380fbi.th.jpg[/IMG]]("http://img29.imageshack.us/i/dsc01380fbi.jpg/")

and the dmesg output:

[[IMG]http://img269.imageshack.us/img269/400/dsc01379v.th.jpg[/IMG]]("http://img269.imageshack.us/i/dsc01379v.jpg/")

I tried with init=bootarg, no change. Any help on what is my problem would be great, thanks!

---

### Post by smakand on 2009-08-14
I'm looking for a tip or something as to what I type or a method as to how I go about debugging this, I have absolutely no idea why the install won't take or what driver I need. I searched the wikis and forums but all the problems listed don't seem to have prevented installs. I'm stumped. :confused:

---

### Post by presence1960 on 2009-08-14
[boot options]("https://help.ubuntu.com/community/BootOptions") Scroll down to section dealing with F6

If none of those work try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

Before trying the above did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded prior to burning it as an image to CD?

Did you burn it as an image at no more than 4x speed? [https://help.ubuntu.com/9.04/switching/installing-burning.html](https://help.ubuntu.com/9.04/switching/installing-burning.html)

When you boot the Ubuntu Live CD did you choose check disk for defects prior to trying to install?

---

### Post by smakand on 2009-08-15
> **presence1960 said:**
> [boot options]("https://help.ubuntu.com/community/BootOptions") Scroll down to section dealing with F6

Before trying the above did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded prior to burning it as an image to CD?

Did you burn it as an image at no more than 4x speed? [https://help.ubuntu.com/9.04/switching/installing-burning.html](https://help.ubuntu.com/9.04/switching/installing-burning.html)

Yes yes made sure of all of this.

> When you boot the Ubuntu Live CD did you choose check disk for defects prior to trying to install?

When I select this, it shows the ubuntu loading screen and then exits to the same console. It doesn't seem to test the media at all.

---

### Post by presence1960 on 2009-08-15
> **smakand said:**
> Yes yes made sure of all of this.



When I select this, it shows the ubuntu loading screen and then exits to the same console. It doesn't seem to test the media at all.

i would burn another Cd at no more than 4x speed. If you have a CD burning program that won't let you choose speed see [here]("https://help.ubuntu.com/9.04/switching/installing-burning.html") for Infra Recorder

---

### Post by smakand on 2009-08-16
Alright so reburning the normal installer gave the same errors I described above, but on a hunch I tried reburning the alternative installer (at 4x) and it did the trick, the install completed successfully.

I now have another problem (instead of GRUB loading up, windows 7 loads up), but thank you for all your help!

---

### Post by presence1960 on 2009-08-16
Don't you want to fix it so GRUB loads at boot? if so post back we will be glad to help.

---

