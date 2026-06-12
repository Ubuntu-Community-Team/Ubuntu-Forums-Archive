---
title: "Trust tb-3100 aka Aiptek issue"
date: 2011-04-16
forum: Hardware
---

### Post by Abisso on 2011-04-16
Hi all, I'm a Kubuntu 10.10 user and owner of a Trust tb-3100 tablet too.

I've followed [this thread]("http://ubuntuforums.org/showthread.php?t=1262073"), which looks like exactly what I needed and after I rebooted the tablet was recognized. But:

as soon as I press the pen's tip in order to start drawing, the cursor stops moving, unless I press the tip. But this of course makes the tablet almost unusable, since I can't move the cursor without drawing at the same time. What stops to work is the proximity recognition, what allows the pen to move the cursor when it's close to the tablet.

I wonder if anyone has the same issue, or maybe solved it.

Thanks anyway.

---

### Post by Favux on 2011-04-16
Hi Abisso,

Welcome to Ubuntu forums!

I gather from the thread you linked to you installed the Aiptek driver.  Is that correct?  Also I'm assuming you entered *lsusb* in a terminal and verified it's an Aiptek tablet and not a rebranded Waltop or whatever.

If so the problem is the current Aiptek driver package does not include a .conf file, which it should.  The xorg.conf.d .conf files are used in Lucid and Maverick instead of the HAL .fdi files.  So most likely your tablet is on the evdev X driver and that is the problem.  You could check in Xorg.0.log in /var/log to verify that.

If you have installed the Aiptek driver try adding this .conf file and rebooting.  Use the following command in a terminal to create the file:
```
gksudo gedit /usr/share/X11/xorg.conf.d/50-aiptek.conf
```
Then add as the contents of the new aiptek.conf file the following:
```
Section "InputClass"
        Identifier "Aiptek class"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection
```

Hope this helps.

---

### Post by Abisso on 2011-04-17
Thanks for the quick reply.

Yeah, I've verified that my tablet is actually an Aiptek:

Bus 002 Device 005: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet

And I'd forgotten to mention I had also followed [this guide]("https://help.ubuntu.com/community/AiptekTablet") which basically suggest me to do the same you did.

[s]I must add that adding that .conf file hasn't changed at all the issues given by the tablet. It worked with just the aiptek drivers and the /etc/hal/fdi/policy/10-aiptek.fdi (which probably is pointless to have now) and it works now that I added the .conf file. But in both cases, the pen stops to be recognized, unless I click the tip, as soon as I start drawing.

Any other option? Should I remove the /etc/hal/fdi/policy/10-aiptek.fdi file, or is it just a pointless move?[/s]

EDIT: I previously named the .conf file 10-aiptek.conf. Naming it 50-aiptek.conf as you suggested seems to have fixed it, which sounds surprising, but it's true.

I've marked the thread as solved.

Thank you Favux, I really appreciate the possibility to use my tablet inside Kubuntu. Having to switch OS just for that reason was very frustrating.

---

### Post by Favux on 2011-04-17
Great!  :)

The number determines the order in which the file is run.  The last run .conf file controls.  So something being run at or near the same time was controlling - the evdev driver?

> Should I remove the /etc/hal/fdi/policy/10-aiptek.fdi file, or is it just a pointless move?
If you haven't installed HAL it shouldn't do anything.  If adding the file (and directory(ies)?) didn't break anything no harm.  But since it is not doing anything you should probably remove it.

---

