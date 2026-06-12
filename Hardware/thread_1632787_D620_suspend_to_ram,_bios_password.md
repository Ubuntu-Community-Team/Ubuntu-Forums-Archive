---
title: "D620 suspend to ram, bios password"
date: 2010-11-28
forum: Hardware
---

### Post by vdbijl on 2010-11-28
This took me quite a while to figure out. I hope other people can benefit from my tinkering.

What was the issue? Suspend to ram on my Dell D620 was not working. Actually I cannot remember it ever working on whatever Ubuntu version I used. FYI right now I'm using Ubuntu 10.04.1 LTS.

It turned out that it consisted of two problems. One was my nvidia card that had some problems. The other one was that I had a bios password on my hard disk.

Starting with the latter. Ubuntu does not ask for the bios password after a resume. As a result it has trouble reconnecting the hard disks. I did not find a solution for this. Disabling the hard disk password in the bios is a work-around.

The nvidia problems seem to be related to some VBE incompatibility between nvidia and pm-utils (the nvidia man pages have a vague remark about it). 

Anywayz, I played a while with the settings in /etc/default/acpi-support and I found a setting that works. I changed the following settings:
SAVE_VBE_STATE=false
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=true

If the problems really are only VBE related, the last two options probably do not matter.

Good luck, happy hacking

---

