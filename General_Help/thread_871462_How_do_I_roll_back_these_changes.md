---
title: "How do I roll back these changes?"
date: 2008-07-26
forum: General Help
---

### Post by Steve.G on 2008-07-26
Recently I downgraded my Xubuntu Hardy installation to Ubuntu Feisty, because I got sick of all the crashes and problems. I find it to be running much more stable now-a-days.

I was trying to use a webcam, and not meeting much success, as it uses the Z-star microelectronics chip, which I now realize does not work with Linux unless you are some type of magician. In trying to make it work, I attempted to manually install the Spca5xx driver using [these directions]("https://help.ubuntu.com/community/Spca5xx"). For some reason the makefile met a bitter end, and was LOADED with errors when I tried to use the make command. I am treading in unfamiliar waters here, so I don't know what went wrong.

Since that time, Firefox seems to be crashing on most websites. I googled for the problem, and found a few websites talking about Firefox crashes after installing a few things, so I want to roll back the changes I made before I started having all of these problems. I wasn't able to read the entire pages, since, of course, they crash Firefox. :(

Even when I run firefox in safe mode, with all add ons disabled, I still have problems. The same sites load in Opera just fine. Here's what it looks like with Firefox if I run it from the terminal:

> ** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Illegal instruction (core dumped)


and in Opera (which doesn't crash) I still see some errors:
> ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

So anyways, here's what I want to roll back:

apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4

and

ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

I can remove all the makefiles, etc, by myself. Also, do you think this could be part of the problem? Or am I barking up the wrong tree?

Also, sorry for the long post, I'm just trying to be detailed. I'd be willing to try whatever else others might suggest.

Some known offending websites:

answers.yahoo.com
wheeloffortune.com

Thanks.

---

### Post by Steve.G on 2008-07-26
Well, I just went into synaptic and reinstalled the following packages:

firefox
firefox-gnome-support

and now the offending websites load with no problem. Either way I still would like to uninstall the aforementioned packages since 76MB of disk space is a chunk I'd rather not live without on my relatively small hard drive.

---

