---
title: "Ati x200m xorg problem"
date: 2010-01-01
forum: Hardware
---

### Post by karesz on 2010-01-01
Hi! 
I've got some annoying problem. Maybe someone else have met this also. So, the problem:

I've got a Fujitsu Siemens Amilo Li1718, which is a pretty nice machine, almost everything works out-of-box. The problem is the Ati radeon X 200 M video card. It works perfectly, when it works.
Almost at every second boot the machine fails the boot at the point when it changes from userspace to X. It just stops doing anything, the hdd, the lcd goes black and blank (seems powered down), the machine is not responsive to anything. Only a hard reset helps. One of my friends with the same notebook have the same problem, so it's most likely not my nb's fault. Using vista it works perfectly.

Other distros (i've tried fedora10/11/12 [fails to boot the same way], opensuse [same]) also doesn't work. Using ubuntu (karmic) it seems somewhat better, the boot hangs are less often. Older versions also produce (intrepid and janty) this.

Can anyone tell me a solution or just how to get started? What the problem really is? Which log files to see through, where to search for some help? Thx in advance!

(i use the driver which ubuntu installs as default - there are no restricted drivers brought up by ubuntu for this card)

---

### Post by karesz on 2010-01-04
anyone?

---

### Post by karesz on 2010-04-19
Well, this is a bug, which cannot be solved without kms, but it is fixed in Lucid Lynx

---

