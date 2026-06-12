---
title: "Refresh rate problems with Acer GD245HQ and Nvidia Quadro FX 4800"
date: 2010-07-26
forum: Hardware
---

### Post by oxford on 2010-07-26
Dear Forum,

I have recently set up a new workstation with an  nvidia quadro FX 4800 graphics card with the aim of getting the 3D  visualisation from nvidia to work.  I also purchased the Acer GD245HQ  monitor, as this is compatible with the 3D vision IR emitter and glasses  as it has a refresh rate of 120 Hz.  I am running Ubuntu (10.4 LTS;  kernal 2.6.32-23-generic).

The problem is that the stereo only  works when the box "Force Full GPU Scaling" is ticked in the DFP-0  settings of the Nvidia X Server Settings application.  Unfortunately  this automatically lowers the refresh rate to 99 Hz, which makes the  screen unusuable for viewing 3D.  If I untick this box the settings  return to 120 Hz, but the 3D doesn't activate. 

I am confused as  to why the graphics card feels it needs to lower the refresh rate in the  first place and whether I can override this setting in some hidden configuration file?  It seems as though all I need to do is force the graphics card to run the monitor at 120Hz while it has Full GPU scaling enabled.  But I have no idea how I would do this!  Any thoughts?

Many thanks,

Simon.

---

### Post by schockschwerenot on 2011-12-21
i have exactly the same hardware constellation and the same trouble.

up to now, i've always started windows first along with a 3d application before restarting into ubuntu in order to be sure my nvidia 3d vision works properly (for molecular simulation stuff).
however, this is not the best solution. have you found a better solution meanwhile?

vedat

---

