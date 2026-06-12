---
title: "Dell Inspiron 8100"
date: 2009-02-17
forum: Hardware
---

### Post by evolipel on 2009-02-17
I don't really know where to post this, but my Dell Inspiron 8100 has two fairly noticeable bugs left in Ubuntu (three if you count the nvidia binary driver suspend issue, which isn't Ubuntu's fault). They are the Dell lid closing issue, where if you close and re-open a lid, the backlight doesn't turn on again, unless you do it twice; and something going wrong with the SpeedStep module, where.

The launchpad entries for these bugs are...

CPU scaling module issue:
[https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/24353](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/24353)

Lid issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/67231](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/67231)
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/44393](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/44393)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/22987](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/22987)
(Take your pick; I really have no idea which one of these, if any, touches upon the exact problem that I'm having.)

(The nvidia binary driver suspend issue: )
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

Quite frankly, I have no idea what's going on with the CPU scaling. Someone with more knowledge of the way this is handled in the kernel may want to shed some light on this. The lid issue, however, seems easy enough to fix (see my shameless cross-posting on those four launchpad entries).

I know that the Inspiron 8100 is close to an 8 year old machine (!), but it'd be nice and impressive if Ubuntu managed to support it perfectly without workarounds or other tweaking. I don't know if any of this has been fixed in Intrepid or Jaunty (it doesn't look like that to me from the launchpad entries), but I know that at least the lid issue affects many other, newer Dell models besides the Inspiron 8100. So my question is, is there any way to bring some attention to the appropriate developers about these bugs? Alternatively, is there a way I could somehow help in fixing them? The reason I'm even asking is because after I worked around them, Ubuntu runs so well on this very old computer (with compiz enabled, too), that it seems a shame for that to be prevented by two small issues in the first place.

---

