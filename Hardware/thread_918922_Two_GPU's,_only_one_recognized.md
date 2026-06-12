---
title: "Two GPU's, only one recognized"
date: 2008-09-13
forum: Hardware
---

### Post by tierro on 2008-09-13
Hello, I just installed Ubuntu with Wubi. Wubi works pretty awesome but it's not about that.

I have a new system with two identical GPU's. (2xHD3450, crossfire off)
I installed the proprietary drivers for this model, along with Catalyst for Linux.

I hoped ubuntu would recognize both cards, but it doesn't, yet I'm pretty sure you guys know something to do about it!

I use the second card for the third and occasionally the fourth monitor, if that needs any special attention as well, you're free to tell me.

A lot of thanks in advance :)
Rob.

---

### Post by Ub1476 on 2008-09-13
Did you install the drivers from Ubuntus repos? Cause ATI just added support (it's ATI, right?) for multi-GPUs in Linux. Check out phoronix.com and search for ATI on details about it.

Those new drivers will probably be available in Ubuntu 8.10 (Intrepid Ibex), which is scheduled for release next month, October. 

If you can't wait you have to remove the current drivers and use Envy (from repos) which is a GUI script which can fetch and install the latest drivers from you.

But I haven't done this in a while, so do some research if you plan to install the new drivers..

---

### Post by tierro on 2008-09-14
> **Ub1476 said:**
> Did you install the drivers from Ubuntus repos? Cause ATI just added support (it's ATI, right?) for multi-GPUs in Linux. Check out phoronix.com and search for ATI on details about it.

Those new drivers will probably be available in Ubuntu 8.10 (Intrepid Ibex), which is scheduled for release next month, October. 

If you can't wait you have to remove the current drivers and use Envy (from repos) which is a GUI script which can fetch and install the latest drivers from you.

But I haven't done this in a while, so do some research if you plan to install the new drivers..

Okay, thanks!

I'm going to find out more about that straight away.

I've used Envy before, without succes though. But that was on my Old system, things might have changed.

Again, Thanks!!
Rob.

EDIT:
The Third and fourth screen switch on but I can't get them to display anything. What be the next step?
EDIT2:
No more 2D hardware acceleration. Hm...

---

### Post by markbuntu on 2008-09-14
The latest 8.8 driver from ati has some support for crossfire and dual cards through  aticonfig. You can install it following the dorections here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Then you can type

aticonfig --help

to get the dual card options.

---

### Post by tierro on 2008-09-15
> **markbuntu said:**
> The latest 8.8 driver from ati has some support for crossfire and dual cards through  aticonfig. You can install it following the dorections here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Then you can type

aticonfig --help

to get the dual card options.

Yes, but that config can't help me with my triscreen. I'm sad... 

I quote from the Aticonfig manual.

> Dynamic Display Management Options:
  Following options will not change the config file. They are
  used for querying driver, controller and adaptor information.
  These options will be effective immediately. Other options on 
  the same command line will be ignored.
  --enable-monitor=STRING,STRING
        Setting current monitor to be enabled. Only 2 displays
        can be enabled at the same time. Any displays
        that are not on the list will be disabled.
        STRING can be one of the following set, separated 
        by commas:
            none
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            auto   -- use default policy to enable the displays.
  --query-monitor
        This will return connected and enabled monitor information
  --swap-monitor
        This only works for big desktop setup. This will swap the
        contents on the two monitors.
  --swap-screens={on|off}
        Enable/disable swap heads in dual-head mode.
        This option works only in dual-head mode.


At the end of line 7, I read something...

Heck, I'm gonna tackle that little xorg.conf myself...

---

