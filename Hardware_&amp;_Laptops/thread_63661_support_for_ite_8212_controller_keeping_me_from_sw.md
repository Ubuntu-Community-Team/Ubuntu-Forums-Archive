---
title: "support for ite 8212 controller keeping me from switching from fedora"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by iramhernandez on 2005-09-08
Hi,

I've been testing out Ubuntu and I really like it.  I am currently using fedora core 4 and I would like to switch distros, however,  I am currently unable to switch because it does not support my ite 8212 controller (onboard my motherboard).

When I first tried fedora core 3 I had a similar problem.  I tried patching the kernel with Alan Cox's patches and tried compiling a module using the sources available from the chip manufacturers website.  Finally, fedora released a new kernel version (I belive it was 2.6.11) and support for my hardware was built into the kernel.

But now the sad part... I can't use Ubuntu because I already have all my data spread over four ATA disks connected to the ite controller.  They disks are configured as one big LVM volume.

This is the only thing keeping me from switching to Ubuntu.   I tried using a live cd version of breezy colony 4 and it would still not recognize my hardware.   Any body have any ideas?

---

### Post by Brent Dax on 2005-09-09
Linux 2.6.11 is available via apt-get or Synaptic, but in my (very limited) experience it doesn't work that well.

Your best bet might be to wait until the next release, Breezy Badger, which will have 2.6.12 as the kernel.  It's scheduled for release in October.  You can even download the test release if you're feeling adventurous--instructions are in the "Official Ubuntu Announcements" forum at the top of the home page.  (Be careful with it, though--it **is** a test release.)

---

### Post by iramhernandez on 2005-09-12
Like I mentioned above.   I tried Breezy live CD and it had kernel 2.6.12 but the driver is either not there on not enabled.  I tried grep'ing  the source code in the linux-kernel package for 'ite' and it turned up nothing.  I did the same in fedora and it is in a couple of placed in the ide directory of the kernel source.  As far as I could tell,  the ite driver was supposed to be a part of the kernel now.  I guess I should download the 'official' kernel from kernel.org and see if it is indeed included.  Will post what i find.

---

### Post by iramhernandez on 2005-09-12
Well,

I did some research...  I downloaed the kernel source for 2.6.12.1 and 2.6.13.1.  I grep'ed for 'ite 8212' in both kernel trees and found that 2.6.12.1 does not have the code for supporting the ite8212 but  2.16.13.1 does.  Somewhere in between those two releases the code was included.  My guess is that fedora is using something newer that 2.16.12.1 (uname -a reports 2.6.12-1.1398_FC4).

A little more research revealed that fedora has been using patched source code for this device and that it is finally being included in 2.6.13.  Quote the Changelog:

```
[PATCH] ide: it8212 backport for Bartlomiej IDE
    
    This lets you throw out the iteraid stuff that has ended up back in due
    to stupid goings on in the IDE world. Its the same heavily tested code
    shipped in Fedora/Red Hat products but without the other dependancies on
    the Bartlomiej IDE layer.
    
    Pre-requisite: the ide-disk patch I sent to handle pure LBA devices.
    
    Obviously you lose things like hot unplug with the Bartlomiej IDE layer
    at the moment but that won't matter to most users.
    
    The patch does the following
    - Add IT8211/12 to pci_ids.h
    - Add Makefile/Kconfig entry
    - Add it8212 driver
    
    No core IDE code is touched by this diff
    
    Embedded system testing and the ability to force raid mode off by David
    Howells
    
    Made possible by the ite reference code, documentation and also several
    clarifications and pieces of assistance provided by ITE themselves
    
    Signed-off-by: Alan Cox <alan@redhat.com>
    Acked-by: Bartlomiej Zolnierkiewicz <B.Zolnierkiewicz@elka.pw.edu.pl>
    Signed-off-by: Andrew Morton <akpm@osdl.org>
    Signed-off-by: Linus Torvalds <torvalds@osdl.org>


```

Well, this answers my question as to why my controller is not working...  Now I need to figure out what to do in order to get breezy to work when it comes out.  Is there any chance of getting 2.6.13 anywhere.   I read on another thread that it might be in 'universe'

---

### Post by sergiopereira on 2006-04-21
[QUOTE=iramhernandez]Hi,

I've been testing out Ubuntu and I really like it.  I am currently using fedora core 4 and I would like to switch distros, however,  I am currently unable to switch because it does not support my ite 8212 controller (onboard my motherboard).
[/QUOTE]

Good news in the current beta LiveCD. See this thread:
[http://ubuntuforums.org/showpost.php?p=944250&postcount=10](http://ubuntuforums.org/showpost.php?p=944250&postcount=10)

---

