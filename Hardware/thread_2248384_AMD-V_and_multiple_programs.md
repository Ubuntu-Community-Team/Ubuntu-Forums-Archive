---
title: "AMD-V and multiple programs"
date: 2014-10-14
forum: Hardware
---

### Post by bewareofthephog on 2014-10-14
Firstly, I'm not a hardware guy, so forgive the ignorance :)

I have an AMD processor with AMD-V enabled in my BIOS on Ubuntu 14.04.  I'm writing and android application and have been using the Atom x86 target to speed up the emulator.  Now, I need to run a VM in Virtual Box.  This VM has to be a 64-bit OS.  It appears that VirtualBox can't start because my Android emulator has already taken up AMD-V for itself.  My question is this:  Is this behavior on an AMD-V platform expected or should I be able to run more than one process that uses virtualization?  I ask because I know I've run more than one 64-bit VM at the same time in the past.  Is this because VirtualBox already has a lock on AMD-V and is splitting the resources among it's own processes?

Bonus question:
The whole reason I need a VM running is because I can't get the software I need to communicate with from my AVD installed on my machine.  This is due to a missing depedency, libstdc++
I've tried ia32-lib ia21-lib-multiarch (right package name), and all the other suggestions on the forum posts I've read.

Either way, even if someone knows how to fix my libstdc++ question, I'd still like to know what gives with AMD-V

Thanks!

---

### Post by TheFu on 2014-10-14
AMD-v is a way for the CPU to change contexts quicker - there is no known limit on the number of concurrent VMs that are supported with it. RAM and CPU run out first.

To run a guestOS as 64-bit, 
* the CPU must be 64-bit
* the hostOS must be 64-bit
Besides that, I don't know any limitations that aren't obvious.

The stdC++ question most definitely has ZERO to do with amd-v. It is purely a C++ library question that most experienced C++ programmers on Linux should be able to answer. My C++ experience was pre- std::templates - sorry. Templates are cool - which they were stable when I was coding C++.

BTW - this is more a virtualization question than hardware. For the most part AMD-v "just works", like vt-x does in intel systems.  I've never heard of any issues specific to either of these. Not 1.

---

