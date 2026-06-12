---
title: "Acer Aspire s3 and Ubuntu 11.10 fan/power managment problems"
date: 2011-10-31
forum: Hardware
---

### Post by linux99user99 on 2011-10-31
Dear Ubuntu users,

I have a new Acer Aspire S3 and problems with the fan. It is running constantly. Has anybody experiences with this notebook and Ubuntu (or any other type of linux)? I would appreciate the answers to the following questions

a) How can I access the fan on this laptop
b) Is there a way to use better drivers (i.e. for the graphics) to reduce the heat produced by the computer



I also reported the problem to the following forum, so see also whats written there

[http://askubuntu.com/questions/73859/fan-runs-constantly-on-an-acer-aspire-s3](http://askubuntu.com/questions/73859/fan-runs-constantly-on-an-acer-aspire-s3)

But there I saw that also simillar questions did not obtain results. Since I need to think about returning the product soon, I also post the question here. I hope this is ok.

---

### Post by nandelbosc on 2011-11-23
Hi!

I NOT have this problem with my Acer S3. I'm runnig linux mint 12 RC with Kernel 3.0.0-12-generic #20 (64bits).

All works perfect except the touchpad: no multitouch, no vertical/horizontal scrolling.

---

### Post by rouch on 2011-11-23
There seems to be a simple solution for the brightness. Here is a link to a global overview of the Acer Aspire S3 running on Linux.  Pleas, feel free to add/correct the information you will find on the page.
[http://www.linlap.com/wiki/acer+aspire+s3](http://www.linlap.com/wiki/acer+aspire+s3)

Hope this helps

Bernard

---

### Post by horadee on 2012-01-17
> **nandelbosc said:**
> Hi!

I NOT have this problem with my Acer S3. I'm runnig linux mint 12 RC with Kernel 3.0.0-12-generic #20 (64bits).

All works perfect except the touchpad: no multitouch, no vertical/horizontal scrolling.

have you gotten the multitouch and vertical/horizontal scrolling fixed?

---

### Post by peterpall on 2012-03-08
After updating to the beta of precise pangolin nearly everything should work. For the details that don't I have created the following wiki page: [https://help.ubuntu.com/community/AspireS3](https://help.ubuntu.com/community/AspireS3)

---

### Post by aegdawson on 2012-03-13
> **peterpall said:**
> After updating to the beta of precise pangolin nearly everything should work. For the details that don't I have created the following wiki page: [https://help.ubuntu.com/community/AspireS3](https://help.ubuntu.com/community/AspireS3)

Wish... I tried that and nothing worked not even the bits that worked in 11.10
try saving  a bit of power and u might find the battery last longer and perhaps the fan runs less here is something that worked for me

                     vi /etc/default/grub
 Change
 **GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash**”
 To
 **GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash pcie_aspm=force  pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1  i915.lvds_downclock=1&#8243;**
 update-grub  Saves about 10 Watts you battery now should last about 3 to 3.5 hours depending on what you do of course

---

