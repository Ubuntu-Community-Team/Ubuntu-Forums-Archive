---
title: "Can not find NIC under HyperV"
date: 2009-01-15
forum: Hardware
---

### Post by jasont80 on 2009-01-15
I'm trying to use Ubuntu under **Microsoft HyperV**, where I have bound a Broadcom wired NIC.  Everything seems to be working great, but the OS does not appear to see the NIC.  When I run "lspci", I get the following items:

Host bridge: Intel Corp 440BX
ISA bridge: Intel Corp 82371AB
IDE interface: Intel Corp 82371AB
Bridge: Intel Corp 82371AB
VGA compatible controller

None of these look like a NIC to me.  Anyone get this to work?  If so, please help!

Thanks!
J

---

### Post by blkspade on 2009-09-22
So far the only way to get a NIC in ubuntu under hyperv is to manually configure it as a  Legacy NIC in the hyper-v vm settings. Which apparently is much worse performing than the standard one which is unavailble without the Linux Intergration Tools. That only install under SUSE Enterprise and Red Hat.

---

### Post by matthew.mattoon on 2010-05-29
Hi Jason/Blkspade,

If you are using Ubuntu on Hyper-V by default in the VM properties you will have a Synthetic Network Card.  If you do not have the Linux Integration Components installed this will not work.  You do have the option of using the Emulated Network Card.  However a better option is to install the Synthetic Device Drivers (which are included in the LIC released by Microsoft as well as in the 2.6.32 kernel bundled with Lucid).  I have documented all of your options in a blog post.

[http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx](http://blog.allanglesit.com/Blog/tabid/66/EntryId/60/Ubuntu-and-Hyper-V-The-Paths-to-Enlightenment.aspx)

-matt

---

### Post by DJonsson2008 on 2011-09-04
I've finding getting Ubuntu to run under Hyper-V vexing.

Neither legacy network card or network card configurations work,
after numerous tries. Either static or DCHP settings can't get 
the NIC card to communicate with Ubuntu in the VM. 

In this instance am dedicating a separate card to for the Hyper-V/Ubuntu instance. 

The process does not instill confidence in Hyper-V.

* Is there some key concept to the process I'm missing somehow?

* Is Hyper-V/Ubuntu stable enough for production?

* What other production quality VM options are out there?

---

