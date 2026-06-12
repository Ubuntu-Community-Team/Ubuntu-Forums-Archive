---
title: "Speedsteep on Coppermine procs?"
date: 2009-07-20
forum: Hardware
---

### Post by thetick1 on 2009-07-20
Hi,

I  have a Thinkpad A22m with a Coppermine PIII proc.  With 8.0.4 Ubuntu I needed to force[FONT=monospace] speedstep-smi module to load and the driver worked fine.  

For info see 
[http://www.thinkwiki.org/wiki/How_to_get_SpeedStep_working_on_Coppermine-piix4-smi_based_Thinkpads](http://www.thinkwiki.org/wiki/How_to_get_SpeedStep_working_on_Coppermine-piix4-smi_based_Thinkpads)

With the latest Ubuntu Desktop (2.6.28-13-generic) I don't have speedstep-lib / smi modules?  

Were these modules dropped in a recent kernel or is there a get-apt package that includes speedstep-smi and speedstep_lib?

I have built custom kernels/modules in the past but I would prefer to use prebuilt modules.


[/FONT]

---

### Post by thetick1 on 2009-07-31
Well I was expecting a few replies.  Anyway I rebuilt my kernel (argh I would rather run a mainstream built kernel) and the steepstep-smi module works fine with cpufreq utils.  I guess if no one on this forum knows I'll ask in the ubuntu package mailing list why speedstep-smi was omitted in the latest Ubuntu.  Previous versions of Ubuntu had the module built.  Note speedstep-smi is NOT  deprecated in the latest kernel builds like speedstep-centrino.

---

