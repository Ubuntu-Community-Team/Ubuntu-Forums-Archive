---
title: "No ISDN support?"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by juraj on 2007-08-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/132325](https://bugs.launchpad.net/ubuntu/+bug/132325) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I can't get my ISDN connection to work. I have an ASUSCOM ISDN passive card, and have absolutely no idea what to do. 

Such a shame, really - in SUSE it was a matter of clicking a few times in YaST and the connection worked. Ubuntu isn't user friendly when it comes to setting up an internet connection.

In hardware information the device shows up as "Dynalink IS64PH ISDN Adapter". Device type and capabilites are unknown.

BTW here is output of lspci -v related to the ISDN card
01:07.0 Network controller: Dynalink IS64PH ISDN Adapter
        Subsystem: Winbond Electronics Corp Unknown device 6692
        Flags: medium devsel, IRQ 10
        Memory at e6000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 9000 [size=256]

---

### Post by juraj on 2007-08-14
I've tried modprobing hisax, as SUSE reported that this module works with my card, but I got no success.

Please, anyone?!

---

### Post by shad0w_walker on 2007-08-14
It sounds blunt but i suggest waiting a little while longer for a reply, I very very rarely see anyone with an ISDN (I'm going to be no help on this BTW) so give it maybe 24 hours for the forum regulars to come along, baring in mind all the different time zones people are in (GMT here so posting at 1:15am)

I imagine there is a relatively simple answer to this question as this works in suse, have you got a list of things you had to install/do to get it working suse? If we get some more info on how you got it working in suse it could be very possible to work out how to get it going on Ubuntu.

---

### Post by juraj on 2007-08-15
> **shad0w_walker said:**
> I imagine there is a relatively simple answer to this question as this works in suse, have you got a list of things you had to install/do to get it working suse? If we get some more info on how you got it working in suse it could be very possible to work out how to get it going on Ubuntu.

Well, I have described how to get it working in SUSE - it was a matter of creating a new connection in YaST and I could dial it via network-manager. I think that the only important detail is that SUSE reported that it uses the hisax module, and the connection mode was syncronous ppp.

---

