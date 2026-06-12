---
title: "Random SMART test failures (Highpoint WebGUI)"
date: 2013-04-25
forum: Hardware
---

### Post by bmcclint on 2013-04-25
Really not sure what I am seeing here. I have recently setup a 12.10 system with a RAID 5 using a Highpoint 640 and 4x2TB WD Red Drives. 

Everything is working as planned. I have the Highpoint software setup to email me on events. 

Occasionally, and I mean one every two weeks or so, I get emails about 'Drive X on contoller1-channelY SAMRT test result:FAILED!’. Seems to be more rlated to reboots of the system rather than for idle activity.

OK that’s fine. Issue is they emails are random across all channels. 

When I go to the WebGUI software to look at the SHI(SMART) data I can see all the drives and their smart data or some of the drives. Each refresh of the browser changes, some, all or random channels failed.

So I don’t think I have an actual drive failing. I’m also pretty confident all drives are not failing at the same time. So this leave a few variables that I am attempting to isolate.

Is it software in Ubuntu? An issue with the Highpoint drivers? Something to do with Western Digital Reds? A combination of all three?

Any insight into where to look is greatly appreciated. I am not overly concerned but email from the RAID controller can raise an eyebrow. I only want to see things that are really happening.

---

### Post by ahallubuntu on 2013-04-25
~

---

### Post by bmcclint on 2013-04-25
> **ahallubuntu said:**
> Install GSmartControl and look at the Attributes tab of each drive and see what the current status. Any Attributes highlighted in red or pink? Those are the ones to worry about.

There is nothing wrong with the drives and all the SMART counters are within norms WHEN the software reports them.  The question is what could possibly be making the software think the test is failing randomly across the channels.

I don't think there is a drive problem, rather the mechanism to check the SMART state.  

So its go to be something in the SMART driver software, HP software/driver or incompatibility with WD Reds.

The randomness across channels points to software...

---

### Post by tgalati4 on 2013-04-25
It sounds like when the Highpoint software queries the drives for SMART data that it may take some time to generate the data and the script fails and sends an automatic FAIL message.  Since it doesn't tell you what the exact SMART parameter has failed indicates to me that it is a script failure not a SMART failure.  Send an email to HP.  Sounds like their problem.

Compare the *smartctl* messages on each drive.  Most modern drives will store errors.  If you find no errors on any of our drives then I would suspect a Highpoint script problem.

---

### Post by bmcclint on 2013-04-25
> **tgalati4 said:**
> It sounds like when the Highpoint software queries the drives for SMART data that it may take some time to generate the data and the script fails and sends an automatic FAIL message. Since it doesn't tell you what the exact SMART parameter has failed indicates to me that it is a script failure not a SMART failure. Send an email to HP. Sounds like their problem.

Compare the *smartctl* messages on each drive. Most modern drives will store errors. If you find no errors on any of our drives then I would suspect a Highpoint script problem.


That's actually what I attempting to isolate.  This is actaully my second system using an HP card.  Last system did not exhibit this behavior using same WebGUI software and version.  Different card and driver.  But lots of other things changed.

Old: AthlonXP, PCI HP Raid Card, 4x500GBSata2 WD Blue on FC12.
New IntelI5, PCIe HP Raid Card, 4x2TBSata3 WD Red on Ununtu 12.10.

So many differences hard to isolate an issue...

---

