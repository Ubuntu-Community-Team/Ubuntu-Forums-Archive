---
title: "Another Ubuntu 9.04 RAID 1 problem"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Marcin Kraszewski on 2009-06-29
Hello, everyone
I was quite impressed when LiveCD of Ubuntu 9.04 recognized my RAID 1 and the NIC on my new ASUS P5Q Pro motherboard. The install worked without a glitch, again GParted showing one RAIDed drive. However, when I boot after the successful installation, my system does not see the hard drive. I have BIOS RAID based on the Intel chip. It is a single boot system. What boot parameter do I have to use to make my system boot? Thank you very much for your help.
Cheers,
Marcin

---

### Post by ronparent on 2009-06-29
Unless the distribution disk for ubuntu 9.04 has been changed, the sad fact is that the live cd does NOT see the raid drive. What you probably actually saw was one drive of the raid set and installed to it. In that case your install was not mirrored on the second drive! If what I suspect is true your raid set would indicate as broken when inspected by the raid bios on boot.

Not all is lost because raid1 incorporates redundancy. The drive you installed to shoud be valid and the raid should reconstruct itself once activated. Try booting to a live cd and installing and activating the raid thru ubuntu raid software. Open a terminal and enter **sudo apt-get install dmraid -y**. Then activate it by entering **sudo dmraid -ay**. This is only a temperary step that should reconstruct a valid raid set (to hopefully protect against further mishap). 

Your best bet initially would have been to install from the alternate cd that does recognize raid drives present. Thie following reference tells you how to install to raid drives: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto). As you can surmise you have what some in the linux community love to refer to as fakeraid.

I am frankly uncertain of where we go from here. You didn't say but if you have windows installed you should now at least be able to boot to windows. What needs to be done is to get dmraid installed to your ubuntu system. Barring that, you would have to reinstall from the alternate cd. If you love the challange of doing it the hard way, I believe you can chroot to install dmraid to your hard drive (while dmraid is still active). If sucessful with dmraid the ubuntu 9.04 you installed would be able to boot. I would have to research this to be of any help but I believe the reference I gave you above would provide some clue. Keep us posted.

---

### Post by Marcin Kraszewski on 2009-06-30
My apologies for using incorrect thread prefix. The problem I have is a desktop issue.
Thanks, ronparent, for your reply.
I activated RAID in BIOS on my ASUS P5Q Pro motherboard and then configured it using the RAID utility. When the system boots, the disks show as mirrored, that is why when I saw just one disk running Live CD, and then when running installation, I thought Ubuntu 9.04 recognized my RAID. I was hoping that all I need is a boot parameter to make Ubuntu see the raided disk during boot...
The two raided disks are brand new, no other OS installed. I finally got rid of Windows! If I have to run it, it will be under Linux.
I will play with dmraid, but if I can't fix it, I will reinstall with the alternate disk. I will keep you posted.

---

### Post by ronparent on 2009-06-30
Glad to see you have a better sense of your situation. Do post if you need more help.

---

