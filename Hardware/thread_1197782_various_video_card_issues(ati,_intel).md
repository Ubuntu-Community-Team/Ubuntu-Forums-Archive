---
title: "various video card issues(ati, intel)"
date: 2009-06-26
forum: Hardware
---

### Post by fdm on 2009-06-26
i have recently been working on my friend's Compaq Presario S6010NX. the first hurdle was VisionTek(ATI) 9250 128MB PCI card that was used to bypass the poor performance of the integrated agp video controller. with the pci card set as as the primary adapter in the bios, i witnessed several severe compatibility issuses with linux. for one, live cds will crash while loading. the only one that i could get to load and install was fedora 10(i tried fedora 11, opensuse, mandriva, ubuntu 8.10, and ubuntu 9.04). once installed, the strange things i noticed included the lack of a graphical boot screen, random crashes, and crashes when shutting down. the messages are all the normal crash dumps, but around 10 of them in a row. further configuring seemed pointless after a couple days of trying, so i simply removed the video card to resolve the issue. if anyone knows how i can get relevant crash information from booting live cds i would be more then willing to provide what info i can. i could also reinstall fedora 10 on an extra harddrive if i knew where to pull the crash logs from.

luckily the integrated the intel video controller has pretty stable drivers. here is it's info:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 5778
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Memory at ee000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 1
	Kernel modules: intelfb

on fedora, under kernel modules it said i915. fedora had no xv support and dri failed to load(though X11 video playback ran smooth fullscreen). on ubuntu, those issues were not present. is it a hardware detection issue that the fedora devs should know about, or has ubuntu just adopted some new intel module(s) before fedora?

with ubuntu's intel modules, i noticed several opengl games cause crashes(most of the tests were windowed mode) where keyboard input and X becomes completely unresponsive, but any music continues to play and the mouse pointer is often movable. X11 video playback is also pretty choppy. adobe flash is the same way but with small freezes every couple of seconds while playing flash video in fullscreen. OverrideGPUValidation=true leads to a solid black screen, though i did not expect it to work :p

i have this computer for a couple more days if you guys need more information. my solution was to remove the conflicting hardware and software and move on, but i would be more than willing to provide any information that could help to fix the problems instead of just avoiding them.

---

### Post by fdm on 2009-06-28
my window of opportunity to extract information about why my friend's ati card causes kernel failures is closing. is there anyway to record these failures from live cds? or even an installed system? i realize i should have made the report on a kernel forum, but everyone works together anyway. solutions for this particular computer will come far too late, but i would like other people with similar configurations to not be turned off from linux because it wont run. all i am asking is how to collect information.

---

### Post by fdm on 2009-06-29
ok, it got sent back. on the bright side we have one more ubuntu user and i now have a backup video card :guitar:

---

