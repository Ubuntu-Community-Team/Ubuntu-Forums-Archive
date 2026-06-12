---
title: "Compiz settings don't save"
date: 2008-09-08
forum: General Help
---

### Post by jinndtonic on 2008-09-08
everytime i restart hardy, the advanced desktop settings dont get saved.

here is my .xsession-error file
> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Checking for nVidia: present. 
Starting Xgl with options:  -accel xv:fbo -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Waiting 10 more seconds for Xgl to start...
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
/home/daniel/.Xsession: 8: gnome-window-decorator: not found

Fatal server error:
Server is already active for display 1
	If this server is no longer running, remove /tmp/.X1-lock
	and start again.

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: SESSION_MANAGER=local/daniel-laptop:/tmp/.ICE-unix/6097
present. 
Enabling Xgl with nVidia drivers...
No valid screens to apply stored configuration
Couldn't find a perfect decorator match; trying all decorators
Starting emerald
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'menu'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
expected keysym, got XF86KbdLightOnOff: line 70 of pc
last scanned symbol is: XF86KbdLightOnOff
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
last scanned symbol is: XF86KbdBrightnessDown
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
last scanned symbol is: XF86KbdBrightnessUp
Warning:          Type "PC_RALT_LEVEL2" has 2 levels, but <LALT> has 3 symbols
                  Ignoring extra symbols
Warning:          No symbols defined for <SYRQ> (keycode 92)
...
Warning:          No symbols defined for <I7F> (keycode 255)
Shutdown failed or nothing to shut down.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Segmentation fault
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/home/daniel/.compiz/session/default0"


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC
Throttle level is 5
11
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing nautilus-share extension
evolution-alarm-notify-Message: Setting timeout for 83852 1220936400 1220852548
evolution-alarm-notify-Message:  Tue Sep  9 01:00:00 2008

evolution-alarm-notify-Message:  Mon Sep  8 01:42:28 2008

seahorse nautilus module initialized

** (nautilus:6250): WARNING **: Unable to add monitor: Not supported
seahorse nautilus module shutdown
Shutting down nautilus-share extension
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.7

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
  PID TTY          TIME CMD
 6212 ?        00:00:00 pulseaudio
WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy

WARNING: modinfo for module fglrx failed: modinfo: could not find module fglrx

Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6747): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


---

### Post by jinndtonic on 2008-09-09
bump 4 help!!!

---

### Post by ColdFusionEESG on 2008-09-19
Any luck?  I'm in the same boat

---

### Post by sayakb on 2008-09-19
Open ccsm (Press Alt+f2 and type in **ccsm**)
Click on **Preferences->Export** and save the filename.profile at a convenient location.
Now click on [B]Reset to Defaults.
[/B]Click on **Import **and import the saved file. Now reboot and check.

---

### Post by ColdFusionEESG on 2008-09-19
> **LinuxIsInnovation said:**
> Open ccsm (Press Alt+f2 and type in **ccsm**)
Click on **Preferences->Export** and save the filename.profile at a convenient location.
Now click on [B]Reset to Defaults.
[/B]Click on **Import **and import the saved file. Now reboot and check.

Thanks!

---

### Post by keypox on 2008-11-21
why do you have to reboot?  I mean you can change settings without rebooting.  Yet doing this requires a reboot:confused:

---

### Post by ColdFusionEESG on 2008-11-21
> **keypox said:**
> why do you have to reboot?  I mean you can change settings without rebooting.  Yet doing this requires a reboot:confused:

Dunno....you can just restart X (ctrl + alt +backspace).....but yes the effects usually don't require a re-start.

That said, I have to repeat this friggin process after almost every reboot or X restart.....Compiz DOES NOT SAVE settings correctly....period....nobody can convince me otherwise ;-)

I challenge anyone reading to provide a true FIX not a half baked workaround.

Cheers

---

### Post by Shazaam on 2008-11-21
Installing fusion-icon fixed it for me.

---

### Post by eternalnewbee on 2008-11-21
You could try this.
Go to **Main Menu > System > Preferences > Sessions > Options**, and **click Remember Currently Running Applications**.

---

### Post by ColdFusionEESG on 2008-11-22
> **Shazaam said:**
> Installing fusion-icon fixed it for me.

Thanks, but I have been using it....and no love.

I constantly have to use it to reset Emerald as my window manager....and launch ccsm so I can re-load my profile.

I have never had Compiz keep settings correctly....2 Toshiba laptops....both ATI graphics...Gutsy and Hardy on 1st laptop....Hardy and Intrepid on the new one.

I would think remembering settings should be the least bug prone part of an application.....I just don't get it.

I'll investigate when time permits....thanks again for the suggestion

Cheers

---

### Post by ColdFusionEESG on 2008-11-22
> **eternalnewbee said:**
> You could try this.
Go to **Main Menu > System > Preferences > Sessions > Options**, and **click Remember Currently Running Applications**.

hmmmmm....well that is a thought, but then I'd have to make sure I shut down everything I don't want running for my next session

....but if this drives me crazy enough I might just try it ;-)

Cheers

---

### Post by dannydorko on 2008-12-10
If you install the ccsm-simple package it will add a fourth option (custom) to your visual effects tab. This should solve the problem.

---

### Post by ColdFusionEESG on 2008-12-11
> **dannydorko said:**
> If you install the ccsm-simple package it will add a fourth option (custom) to your visual effects tab. This should solve the problem.

Thanks man!!

I was wondering if there was something missing from the visual effects tab.  I had noticed if I used CCSM to customize my settings....and then went to the visual effects tab, NO selection would be selected....not even "NONE".

So of course after installing the package (simple-ccsm BTW...not ccsm-simple)...I went to visual effects and sure enough the custom option now shows and is selected.  I noticed on the general or info tab that is in the pop-up that the new "preferences" button access shows which profile is the one to use for Compiz....and my custom exported profile is shown.

So...so far so good.

By far the best reply I've seen on this silly issue....and super simple to do ;-)

Cheers

---

### Post by eternalnewbee on 2008-12-11
Glad your problem is solved ColdFusionEESG.
Remember to mark your thread as solved, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

### Post by ColdFusionEESG on 2008-12-11
> **eternalnewbee said:**
> Glad your problem is solved ColdFusionEESG.
Remember to mark your thread as solved, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

Hey Eternal,

Thanks for the advice, but 2 things ;-)

1) I'm not 100% sure it's solved yet (just that so far it's encouraging)

2) Under Thread Tools I have no "Solved" option.

So even if I was ready to mark as SOLVED....I can't ;-)

Is that option only available to the original poster (which I am not)?

TIA

Cheers

---

### Post by eternalnewbee on 2008-12-11
Hahahahaha.
Yes, in deed it is.

---

### Post by thedavis on 2009-02-06
I have a similar issue, my "Visual Effects" tab is "none" selected on every session start. I must select the "extra" and restart compiz for enable it. 

But this config are "reset" on every session start :(

I tried install the simple-ccms, and select the "custom" option, with no luck :(

Any idea?

Thanks

---

### Post by lloydsmart on 2010-05-02
Bump!

I've just started experiencing this exact same behaviour after updating karmic to lucid. Any help would be appreciated!

---

### Post by mustard greens on 2010-05-17
I found a strange work around from another thread which works like this (dont ask me why/how)

re-enable bluetooth as a startup application under system>preferences>startup applications

for some reason this causes the visual effects settings to not reset.
any ideas as to why?

---

### Post by mustard greens on 2010-05-17
so the blue tooth thing did work for me, but then someone recommended un-installing and reinstalling compiz and that did the trick.  now no need for bluetooth at startup.

---

