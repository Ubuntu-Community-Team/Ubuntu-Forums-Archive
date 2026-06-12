---
title: "External monitor refresh rate resets on lid close"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by jrial on 2007-05-27
Anyone who can help me with this? I tried to get dual monitors (clone mode) to work on a Dell Inspiron 510m; I basically want the LCD image cloned onto a CRT when the laptop is docked in it's docking station. In this, I succeeded; both the image on the LCD and the external CRT are crisp, and the CRT is driven at a comfortable 87Hz refresh rate.

However, things turn sour as soon as I close the laptop lid. By default, the lid switch toggles the laptop between LCD and CRT before the OS loads. Once the OS is loaded, though, you can assign actions to it by either using the files provided by acpid, or by using gnome's power manager. Now, gnome power manager only offers two choices when it comes to deciding what to do with the display when the lid is closed: do nothing, or blank screen. Since blank screen is not what I want (I only want to turn off the LCD, not the CRT), I selected "Do nothing" in the "When running on AC" tab.

So onto a more flexible approach; with gnome-power-manager out of the way, the road is clear for acpid and acpi-support to do their magic.

First off, there's a line that runs a function called CheckPolicy in the /etc/acpi/lid.sh file. This line has to go; it's defined in /etc/acpi-support/policy-funcs and checks (among other things) for a running instance of gnome-power-manager. This daemon will always run when you start gnome, and is needed for other power-related stuff as well and hence can not be simply killed. So in order for the lid.sh script to continue instead of bailing out on this check, I commented that line out.

Next was reworking of the script to run my own stuff instead of what was originally intended; I don't want to run the default /usr/share/acpi-support/screenblank script, but instead turn the LCD off and CRT on when closing the lid, and both on when opening it, through i810switch. See code below:

**/etc/acpi/lid.sh:**
```

#!/bin/bash

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

#if [ `CheckPolicy` == 0 ]; then exit; fi

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    su $user -c "i810switch crt on"
            su $user -c "i810switch lcd off"
	fi
    done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
            su $user -c "i810switch lcd on"
            su $user -c "i810switch crt on"
	fi
    done
fi

[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

Now, one might expect to be done by this time, and have a working setup, right? Well, except for the fact that AFAIK there's currently no way of detecting if there's even an external monitor connected (no need to turn CRT on if it isn't; don't know if it will need more power or not), and neither is there a way to determine if we're actually docked (we can assume a CRT is connected if we are); checking for AC power through ACPI is the closest I could find, and I still have to work that into the upper part of the script, but that's another matter which is irrelevant here.

So now we get to the problem I'm experiencing. The setup works. Kind of... When I start X, when connected to the external monitor, it's driven at a nice 87.2Hz. However, when I close the lid, it flickers off and on again, and is then driven at a flickery 60.0Hz. When I open the lid again, and both LCD and CRT are active, it's suddenly driven at a flickery 59.6Hz, and distorted: characters "dance" on screen and even the on-screen-display of the KVM switch through which the laptop dock is connected is affected by this jitter.

Upon further investigation, I found that when I use neither gnome-power-manager nor acpid-support to dictate what should happen when I close the lid, closing and opening the lid switches the display between LCD and CRT. This appears to be a hardware function which can not be overridden through the BIOS or acpid. It's after this switch took place that the CRT's refresh rate gets screwed up. I can accomplish the same thing by using Fn+F8 on the laptop's keyboard (which toggles between LCD, CRT and LCD+CRT).

So... Does anyone have an idea if this can be fixed, and if so, how?

---

### Post by jrial on 2007-05-28
Update: found a somewhat functional solution using the i855crt tool in the i855-crt package.

Right now, the cursor disappears (and I get an ugly square) when using it, but that may be due to me disabling the hardware cursor in xorg.conf; will test with hwcursor enabled and post my experiences here, including a complete step by step walkthrough so others won't have to figure out the solutions to the same issues I face.

Update 2: The hwcursor setting makes no difference. Seems like I have some debugging to do before I can post a walkthrough...

---

