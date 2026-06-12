---
title: "Screen brightness in gutsy"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by tomcat2007 on 2007-10-18
Am presently running 32 bit Gutsy on an HP Pavilion dv9000z w/ a C51 [NVIDIA GeForce 6150 Go] graphics adapter and have noticed an intermittent problem with the screen brightness suddenly incrementing to 100%.  It usually stays around 65% at home so the amount of increase is rather annoying.

Sometimes this occurs w/o any interaction with the system, but I have noticed it happens more often after playing Sauerbraten.  The HP keyboard shortcut is intact but I was wondering if this a bug in Gutsy or something else, leading up to wondering if there is a fix.

Thanks

---

### Post by msrinath80 on 2007-10-19
Exactly same problem here. I upgraded from Feisty yesterday. I'm on a Fujitsu S7110. Very annoying problem. I would appreciate any help :)

Edit: I think I've solved the problem. We need to set the brightness in Preferences -> Power Management. By default it is set to 100!

---

### Post by tvst on 2007-10-19
same here. setting the brigthness in "power management" works, but i'd really like to be able to do it with my laptop keys instead.

---

### Post by tomcat2007 on 2007-10-20
> **msrinath80 said:**
> Edit: I think I've solved the problem. We need to set the brightness in Preferences -> Power Management. By default it is set to 100!

Hey, thanks!  Worked like a charm!  Never occurred to me that a display setting would exist in power management for times when the laptop is on AC power :)

---

### Post by a8n on 2007-10-20
Same problem on my Dell XPS M1210.  The power settings admittedly work, but it's immensely frustrating that the control buttons on the laptop can't be reliably used for a quick adjustment when the ambient light changes.

(To be fair though, Gutsy is improved over Feisty in many areas.  This is the only downside I've come across.)

---

### Post by -Phi- on 2007-10-30
I have Xubuntu on a Fujitsu s7110 and recently upgraded to Gutsy. The screen brightness buttons (Fn+F6 and F7) started working again when I installed gnome-power-monitor, and I even get a little brightness picture on the monitor now too. Further, my volume buttons started working, and they hadn't in Feisty.

---

### Post by pavkb on 2007-12-31
> **msrinath80 said:**
> Exactly same problem here. I upgraded from Feisty yesterday. I'm on a Fujitsu S7110. Very annoying problem. I would appreciate any help :)

Edit: I think I've solved the problem. We need to set the brightness in Preferences -> Power Management. By default it is set to 100!

I don't see any option about screen brightness in the above quoted window.. not sure how you were able to do this.

---

### Post by msrinath80 on 2008-01-11
Apologies for the late reply. Here you go:

---

### Post by Yellow Pasque on 2008-01-11
> **virtuoso said:**
> does that increase in brightness happens when ou plug in the adapter...?
There should be settings in the Power Management dialog for AC and battery.

You can also access them manually (along with lots of other settings) with gconf-editor. Right-click the Applications menu and select "Edit Menus". Under System Tools, check the "Configuration Editor" (and make any other changes you'd like). Click OK and then go into that Conifguration Editor. Pull down the "apps" tree and you should see a gnome-power-manager folder with all of the power management options.

---

### Post by mosestruong on 2008-01-13
In my power management, there is no brightness settings available. I'm using Gutsy 7.10 i386 on HP Pavilion 2308tx. Are there anything I can do to enable it?

The only way I can control the brightness of the screen is 
echo -n 100 > /proc/acpi/video/GFX0/LCDbrightness
where 100 could be one of the following: 20 28 36 44 52 60 68 76 84 93 100

---

### Post by Quilzas on 2008-01-14
> **Temüjin said:**
> There should be settings in the Power Management dialog for AC and battery.

You can also access them manually (along with lots of other settings) with gconf-editor. Right-click the Applications menu and select "Edit Menus". Under System Tools, check the "Configuration Editor" (and make any other changes you'd like). Click OK and then go into that Conifguration Editor. Pull down the "apps" tree and you should see a gnome-power-manager folder with all of the power management options.

I changed the brightness setting in the configuration editor, but it had no effect whatsoever.

In Power Management there is no option for brightness.

Any other ideas?  I am one confused pup.



Running Ubuntu 7.10 on a Fujitsu T2010

---

### Post by Yellow Pasque on 2008-01-14
Quilzas, perhaps you need to restart for changes to take effect? Other than that, I have no idea why your notebook is ignoring those settings, unless it has special settings in the BIOS.

---

### Post by Quilzas on 2008-01-14
> **Temüjin said:**
> Quilzas, perhaps you need to restart for changes to take effect? Other than that, I have no idea why your notebook is ignoring those settings, unless it has special settings in the BIOS.

I tried rebooting just to check.  No luck.

I didn't see anything in BIOS that would apply off hand.  Perhaps I'll go poke through again.

---

### Post by Quilzas on 2008-01-15
I just stumbled across the Brightness Applet thing that you can add to the panel.

It has a red circle with a line through it and lists:  "cannot get laptop panel brightness" when I mouse over it.  The slider is there, and I can move it, but it does nothing.

I also found a reference in the power management help files that the GConf policy keys may be locking out the brightness settings if the admin has set things that way.  But I've yet to find a way to find/change the policy keys.

However it is late and I'm going to go to bed.  Perhaps a fresh start in the morning will be of assistance!

---

### Post by olavjunior on 2008-01-21
Quilsaz - I have the same problem as you. I think it's a well known problem/bug wich will be fixed in Hardy. But let me know if you solve it! :)

EDIT: Found a solution, here's how to: [http://ubuntuforums.org/showthread.php?p=4178093#post4178093](http://ubuntuforums.org/showthread.php?p=4178093#post4178093)

---

