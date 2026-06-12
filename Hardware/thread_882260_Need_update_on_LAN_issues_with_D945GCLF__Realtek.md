---
title: "Need update on LAN issues with D945GCLF / Realtek"
date: 2008-08-06
forum: Hardware
---

### Post by rdenney on 2008-08-06
I'm new to this forum (and to Linux/Ubuntu) and am not sure of the boundaries between the various forums. I'll just have to try this and see. Go easy on me, please.

I have had a oft-reported problem of being unable to install 8.04 on an Intel D945GCLF Little Falls mobo, with the Realtek LAN chip enabled. It installed fine and works well, near as I can tell, when I disable the LAN chip in the BIOS setup.

I am currently downloading 8.04.1 and will attempt a fresh install. I cannot do regular upgrades on the target machine, because 1.) it doesn't have a working NIC (and my installation provides no room for a PCI card), and 2.) I'm putting it together at home where I only have dialup.:(

I have also flashed the latest BIOS from Intel, version 099, as of this morning, using the XP partition (which works fine with the LAN chip enabled). I have also obtained updated drivers (for both XP and Linux) from Intel for the Realtek LAN implementation on that mobo. The XP drivers work fine. The new BIOS does not improve the problem, and 8.04 still fails at the same point during boot as it did before.

In searching the forums as best I can, I have noted that 8.04.1 seems to address the failure-to-install problem, mostly by updating to a newer kernel, but that a problem with inconsistent LAN function, especially following warm boots, still exists.

The instructions for installing updated Realtek drivers, found here

[http://ubuntuforums.org/showpost.php...4&postcount=10](http://ubuntuforums.org/showpost.php...4&postcount=10)

are frankly incomprehensible by me. I found nothing in the referenced txt file that gave me the slightest clue as to where I needed to put my fingers to implement the change. Sorry, but we all have to start somewhere, and I'm at ground zero with Linux (my last experience with Unix was with the SCO kind, about 20 years ago, and those brain cells are now apparently fully dead).

1. If that is still a correct procedure (to implement after I install 8.04.1), can someone lead me by the hand, or point me to where I need to look to (easily) figure it out?

2. Has the issue with the Realtek implementation on the D945GCLF mobo been resolved or investigated beyond what I've described?

Thank you for your assistance.

Rick Denney

---

### Post by rdenney on 2008-08-13
> **rdenney said:**
> ...
1. If that is still a correct procedure (to implement after I install 8.04.1), can someone lead me by the hand, or point me to where I need to look to (easily) figure it out?

2. Has the issue with the Realtek implementation on the D945GCLF mobo been resolved or investigated beyond what I've described?


You guys went so easy on me that nobody responded. Either that means nobody knows the answer, nobody cares, or nobody reads this particular part of the forum.

But in case someone searches for the same information, my questions have been superseded by events. Here is the answer:

Ubuntu 8.04.1 installs and works properly on an Intel D945GCLF motherboard, without the need to install any new drivers for the Realtek Ethernet interface, and without the need to disable the interface. I have not seen the problem reported in another thread that the motherboard has trouble maintaining LAN operation after warm boots.

I did flash the BIOS with version 099, available from here:

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2916&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2916&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I did NOT install the "Linux LAN driver" that is also listed on that page. That driver does not solve the problem.

This Intel web page describes Linux implementation issues for this motherboard. It was updated after my original post to reflect that the 8.04.1 indeed works properly (and also that 8.04.0 did not):

[http://www.intel.com/support/motherboards/desktop/d945gclf/sb/CS-029475.htm](http://www.intel.com/support/motherboards/desktop/d945gclf/sb/CS-029475.htm)

Rick Denney

---

### Post by Nullexe on 2008-08-18
I have the same board and had the same issue (flakey NIC) I installed the 099 BIOS and still had the same problem.  Intel released a 0103 BIOS which I'm going to use.

---

### Post by Xeon3D on 2008-08-31
AFAIK You need to update the kernel to a newer version to make the RTL chip work in this board.

---

### Post by n3wbi32linux on 2009-02-12
Hi,

Can anyone offer any help please I'm having the same problems with Ubuntu 8.10 installed on a D945GCLF.

Tried the following but 'eth0' doesn't appear at all now:-
[http://ubuntuforums.org/showpost.php?p=4210510&postcount=6](http://ubuntuforums.org/showpost.php?p=4210510&postcount=6)

LAN was working okay prior to installing updates after a fresh install however once rebooted LAN is disconnected.

Am a complete newbie to Linux therefore would appreciate a step by step guide on how to get back up and running again.

Thank you.

---

### Post by krowland44 on 2009-02-25
I just installed 8.10 and, after installing numerous updates, found that my network connectivty stopped functioning.
I am using the 	Intel® Desktop Board D945GCLF board.

Any help with this would be appreciated...I am also a newbie at Linux, trying to move away from Windows (at home and for my customers' sake).

---

### Post by n3wbi32linux on 2009-02-25
> **krowland44 said:**
> I just installed 8.10 and, after installing numerous updates, found that my network connectivty stopped functioning.
I am using the 	Intel® Desktop Board D945GCLF board.

Any help with this would be appreciated...I am also a newbie at Linux, trying to move away from Windows (at home and for my customers' sake).

Hi,

Here's what you need to do:-

Download a Kernel from the following URL. Once downloaded double click on the .deb file to install. Reboot and you will probably find that Etho works again. Didn't find this out myself however as I'm aware of the issues having experienced the same problem myself I'd wanted to post a reply.

[http://people.ubuntu.com/~smb/bug326891/linux-image-2.6.27-11-generic_2.6.27-11.27b326891v2_i386.deb](http://people.ubuntu.com/~smb/bug326891/linux-image-2.6.27-11-generic_2.6.27-11.27b326891v2_i386.deb)

Hope this works okay for you.
All the best.

---

### Post by lagrz on 2009-03-12
Thanks for the Kernel Package n3wbi32linux worked perfectly for me. I just hope I don't have to do the same everytime ubuntu releases any updates.:o

---

