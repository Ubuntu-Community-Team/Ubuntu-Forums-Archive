---
title: "Dell E6500 and E-port plus docking station with two monitors attached"
date: 2009-08-17
forum: Hardware
---

### Post by daehenoc on 2009-08-17
Hi all,

I will be getting a Dell E6500 laptop with a E-port plus docking station, which has two DVI outputs on it.  I know that two external monitors work just fine in Windows on this docking station, has anyone got it working in Ubuntu with two external monitors?

Thanks,
Greg

---

### Post by mstringer on 2009-11-04
I have an E6500, with the mini port replicator.  I don't have two EXTERNAL monitors, but I'm running the laptop 15" screen and an external 24" LCD off DVI without any issue.  

I also noted that changes to the multiple monitor setup didn't require a XWindows server reboot (super green).

---

### Post by allg33k on 2010-02-09
Did you have any problems with the monitors not turning on during post when running dual dvi?  I just got a new M6500 and can't get it to turn on the monitors.  Even in windows they don't come on until you get to the login screen.

---

### Post by daehenoc on 2010-03-03
Hi, I wound up running the dual monitors off the docking station with Display Port cables, not DVI.  In Windows 7, both external monitors worked, but I can't remember if they came on prior to the login screen.

I no longer have Win7 natively on this laptop any more, and have had some behavior which has changed on me:
Once Ubuntu was installed, the external monitors worked exactly the way I wanted - I could configure them and rotate them both 90 degrees so now I have two 24" Dell monitors both in landscape mode - cool :)
They would both come on during POST, and both display the Ubuntu logo when the laptop was docked and booting.
About a month after I had got it all working the way I wanted, the behavior of the external monitors has changed:  They no longer display anything during POST, and **may** come on while Ubuntu is booting.  It seems random.  If they don't come on, the laptop doesn't start at all, it seems to hang, I can't SSH to it, and there is no response to CTRL-ALT-F1/F7.  If the monitors do come on at some point, I can no longer log onto X - once I give my username and password, X appears to hang up and lock the laptop again.  Frustrating.

I can start the laptop undocked, log on and **then** dock the laptop - then the external monitors both come to life and are configured correctly, (i.e. both in landscape mode, and arranged side by side) which is nice.

You could try starting your laptop undocked, then dock it and see how you go.

Best of luck,
Greg

---

### Post by wking on 2010-03-16
Hi I am going to get an E Type Plus docking station for my M4400 - I was wondering if it is possible to use the three screens i.e. the two main monitors (external) and the internal laptop (for something like email - skype etc) 

Has anyone tried that?

thanks

---

### Post by daehenoc on 2010-03-17
It'll depend on your video card - my E6500 won't let me use the laptop panel at the same time as the two external displays off the E-plus port adapter.  I should have paid more attention and ordered this laptop with the NVidia video card, as the Intel one is fairly crap, as it wasn't designed to drive two 24" monitors at 1200x1920!

So, I think you may not have success, but give it a shot.

---

### Post by A4orce84 on 2010-10-13
Running into this issue as well. I choose Ubuntu and everything works with my monitor, and then goes black. My keyboard, mouse, and other devices are getting power.

I am also using the NVidia graphics card in my machine.

Anyone have any successes yet?

Thanks.

---

