---
title: "gnome-power-manager only says &quot;Laptop Battery (estimating...)&quot;"
date: 2011-03-14
forum: Hardware
---

### Post by Cactusm123 on 2011-03-14
As mentioned in the post title, the message given by the battery monitor isn't very useful. I've done a little bit of poking into it and found that the percentage remaining is always accurate, and found a (general) source mentioning that the problem may arise from lacking ACPI tables.

Is there a place I can get the ACPI tables for an HP G72 laptop (6 cell battery, if it matters), or, if not, is it possible to have the applet show the percent remaining instead of the "time?" (In quotes because in my case, it doesn't.)

Thanks for your time!

EDIT: Tried the fix in this thread [https://bugs.launchpad.net/ubuntu/maverick/+source/upower/+bug/629258/+index?comments=all](https://bugs.launchpad.net/ubuntu/maverick/+source/upower/+bug/629258/+index?comments=all), post #95) but it's the wrong architecture (I use x64, it's i386) and I don't want to screw anything up by using --force-architecture.

---

### Post by rugbeeprop on 2011-06-01
Try #100 to install ppa:brian-rogers/power which works for me as I am also running x64

```

sudo add-apt-repository ppa:brian-rogers/power
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Cactusm123 on 2011-06-01
Hello,

Thanks for the pointer. I tried it, but when I ran the upgrade, it didn't find any packages too update. I also tried the update manager, same thing.

Searching for upowerd on the Software Center returned no results.

Any ideas?

---

### Post by helpad on 2011-06-01
[http://www.omgubuntu.co.uk/2011/02/battery-applet-status-ubuntu/](http://www.omgubuntu.co.uk/2011/02/battery-applet-status-ubuntu/)

---

### Post by Cactusm123 on 2011-06-02
That does the trick!

Thank you very much.

Is there any way to reorder the indicators to put it back where the battery icon was?

---

