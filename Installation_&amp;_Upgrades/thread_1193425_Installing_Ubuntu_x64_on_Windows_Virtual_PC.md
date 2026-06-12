---
title: "Installing Ubuntu x64 on Windows Virtual PC"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by Floss on 2009-06-21
Does anyone know if there is a way to install Ubuntu x64 on Windows Virtual PC?  I am running Windows 7 RC x64 on a 64 bit architecture (obviously since the main OS is 64 bit).  When I try to boot up though it gets this error: "This kernel requires an x86-64 CPU, but only detected an i686 CPU" Does this mean that the virtual machine is being made as a 32 bit environment and I can't install Ubuntu x64 on it?

---

### Post by starcraft.man on 2009-06-21
> **Floss said:**
> Does anyone know if there is a way to install Ubuntu x64 on Windows Virtual PC?  I am running Windows 7 RC x64 on a 64 bit architecture (obviously since the main OS is 64 bit).  When I try to boot up though it gets this error: "This kernel requires an x86-64 CPU, but only detected an i686 CPU" Does this mean that the virtual machine is being made as a 32 bit environment and I can't install Ubuntu x64 on it?

Please don't use Virtual PC, hate that program. To my knowledge, VPC is only for Windows guests, it's an MS product after all. Don't know if they fixed it now but it was always garbage when I *tried* to use it. [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") should run on 7 I believe, I mean it's just a polished off Vista. Follow the screens, it's a pretty straightforward install for host and guest. VBox has full 64bit support, it's a much better program.

And yes, that's what the error means. The CD is reading a 32 bit only CPU being virtualized.

---

### Post by Floss on 2009-06-21
> **starcraft.man said:**
> Please don't use Virtual PC, hate that program. To my knowledge, VPC is only for Windows guests, it's an MS product after all. Don't know if they fixed it now but it was always garbage when I *tried* to use it. [VirtualBox]("http://www.virtualbox.org/wiki/Downloads") should run on 7 I believe, I mean it's just a polished off Vista. Follow the screens, it's a pretty straightforward install for host and guest. VBox has full 64bit support, it's a much better program.

And yes, that's what the error means. The CD is reading a 32 bit only CPU being virtualized.

Thank you I will give VirtualBox a try.  And VirtualPC seems to be better now.  Everything works just fine except for the mentioned problem.

---

### Post by Floss on 2009-06-21
"VirtualBox is a general-purpose full [virtualizer]("http://www.virtualbox.org/wiki/Virtualization") for x86 hardware"

This is from their own website.  Are you sure VirtualBox can do x64?

---

### Post by KOld Iron on 2009-06-21
> **Floss said:**
> "VirtualBox is a general-purpose full [virtualizer]("http://www.virtualbox.org/wiki/Virtualization") for x86 hardware"

This is from their own website.  Are you sure VirtualBox can do x64?

From the User Manual (from the same website):
[I]**1.6 64-bit guests**
Starting with Version 2.0, VirtualBox also supports 64-bit guest operating systems.
Starting with Version 2.1, you can even run 64-bit guests on a 32-bit host operating
system, so long as you have sufficient hardware.
  In particular, 64-bit guests are supported under the following conditions:
   1. You need a 64-bit processor with hardware virtualization support (see chapter
      1.2, Software vs. hardware virtualization (VT-x and AMD-V), page 11).
   2. You must enable hardware virtualization for the particular VM for which you
      want 64-bit support; software virtualization is not supported for 64-bit VMs.[/I]

---

### Post by Floss on 2009-06-22
You are right I didn't see that thank you.

---

### Post by kundanpro on 2009-06-29
Here are some instructions.
[http://nemesisv.blogspot.com/2009/04/installing-ubuntu-904-on-microsoft.html](http://nemesisv.blogspot.com/2009/04/installing-ubuntu-904-on-microsoft.html)

I am downloading the 64 bit ubuntu 9.04 and will be installing on win 7.

---

### Post by kundanpro on 2009-07-08
Virtual PC does not support x64 Guests. Tried on x64 Win 7 RC.

So downloaded again, i386 Ubuntu and installed on x64 Win 7 RC.

Working fine, just a bit slow.

System Configuration:
E8400
DG45ID
2GB
320GB

---

