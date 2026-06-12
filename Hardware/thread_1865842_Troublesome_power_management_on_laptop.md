---
title: "Troublesome power management on laptop"
date: 2011-10-20
forum: Hardware
---

### Post by funky_uncle on 2011-10-20
On an HP G72.

I'm having the same problem in both Mint and Kubuntu 11, so I suppose the problem is in the Ubuntu base system.

Plugging or unplugging the power cable doesn't affect performance - plugged out the PC apparently thinks it's still connected and runs at full speed until suddenly the battery is empty. The battery monitor(s) only shows whatever it showed when I turned the PC on.

No suprise then, that closing the lid to suspend/sleep doesn't work either, I have to do it manually.

Any solution or workaround?

---

### Post by penguin7009 on 2011-10-20
> **funky_uncle said:**
> On an HP G72.

I'm having the same problem in both Mint and Kubuntu 11, so I suppose the problem is in the Ubuntu base system.

Plugging or unplugging the power cable doesn't affect performance - plugged out the PC apparently thinks it's still connected and runs at full speed until suddenly the battery is empty. The battery monitor(s) only shows whatever it showed when I turned the PC on.

No suprise then, that closing the lid to suspend/sleep doesn't work either, I have to do it manually.

Any solution or workaround?


Hi funky_uncle, I had basically the same problem and I installed:

ibam
kgrellem
tp_smapi

Although tp_smapi is for the thinkpad it worked great for acpi calls on my alienware m17xr2 which was an absolute nightmare to get the bat charge working.

Just put these in the startup program ie: start>system>preferrences>startup programs. These are in the repositories.

penguin:)

---

### Post by funky_uncle on 2011-10-21
Thanks.
I found and installed ibam, but couldn't find the other two. I'm using Kubuntu and I assumed the repos were the same as for Ubuntu, but apparently they aren't.

Anyway, running ibam on startup doesn't seem to have made a difference :/

---

### Post by fyfe54 on 2011-10-21
> **funky_uncle said:**
> On an HP G72.

I'm having the same problem in both Mint and Kubuntu 11, so I suppose the problem is in the Ubuntu base system.

Plugging or unplugging the power cable doesn't affect performance - plugged out the PC apparently thinks it's still connected and runs at full speed until suddenly the battery is empty. The battery monitor(s) only shows whatever it showed when I turned the PC on.

No suprise then, that closing the lid to suspend/sleep doesn't work either, I have to do it manually.

Any solution or workaround?


Jupiter.
[http://www.jupiterapplet.org/](http://www.jupiterapplet.org/)
Works for me.  Dell Inspiron 1545

---

### Post by penguin7009 on 2011-10-21
> **funky_uncle said:**
> Thanks.
I found and installed ibam, but couldn't find the other two. I'm using Kubuntu and I assumed the repos were the same as for Ubuntu, but apparently they aren't.

Anyway, running ibam on startup doesn't seem to have made a difference :/


If your running kubuntu it may be called kgrellem or a variation thereof.  It also comes under kgrellem-ibam.  Put it in the startup menu and then select the battery monitor under the applets menu.  Under options select, >start>ibam.  The battery applet will start and appear on your desktop and tell you if the battery is charging.

You may have to install screenlets app using tweak under the compiz heading to get the ibam batt applet.

penguin

---

### Post by funky_uncle on 2011-10-21
> **fyfe54 said:**
> Jupiter.
[http://www.jupiterapplet.org/](http://www.jupiterapplet.org/)
Works for me.  Dell Inspiron 1545

Nice applet, though it took me a while to figure out that "jupiter notification icon" in the package manager was actually the name of the program. But it doesn't change my system's inability to determine whether or not the computer is (un)plugged or (dis)charging.

---

### Post by funky_uncle on 2011-10-21
> **penguin7009 said:**
> If your running kubuntu it may be called kgrellem or a variation thereof.  It also comes under kgrellem-ibam.  Put it in the startup menu and then select the battery monitor under the applets menu.  Under options select, >start>ibam.  The battery applet will start and appear on your desktop and tell you if the battery is charging.

You may have to install screenlets app using tweak under the compiz heading to get the ibam batt applet.

penguin
I've added it to the startup programs, but I don't see it anywhere. I have no idea what you mean by that last sentence.

---

### Post by penguin7009 on 2011-10-21
> **funky_uncle said:**
> I've added it to the startup programs, but I don't see it anywhere. I have no idea what you mean by that last sentence.

Hi funky_uncle.  Remember I'm running ubuntu (Zorin OS).  I'm not sure kubuntu has the same programs as ubuntu.  See if you can find ubuntu or kubuntu Tweak in synaptic.  If you can download it and then open it.  In ubuntu its under start>system tools>ubuntu tweak.  Its a program for tweaking various settings in Ubuntu.

Look on the left side and find compiz settings.  When you open it you will see a checkbox for downloading the applets program.  Go ahead and check it, type your password and make sure synaptic is closed.

After that you will see an applet program under the accessories listing called applets or screenlets.  There you will find the batt desktop screenlet.  Set it so it will start at bootup by using the options settings. 

For some reason it will show the correct battery settings when the taskbar applet does not.  Hope this helps.  If kubuntu is very different from ubuntu then I guess this wont help much, sorry.

penguin

---

