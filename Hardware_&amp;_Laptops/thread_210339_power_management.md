---
title: "power management?"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by shooterae5 on 2006-07-06
I seam to have some power management control. My Toshiba M35X-S149 laptop hibernates and comes out OK. I haven't tested suspend. What is troubling me is that none of the power indicators give me a reading. they will not change from AC power. Twice now the laptop has shut off without going through a shutdown procedure. 

how can I get to tell me how much battery power I have?

What info will any of you need to help with this problem.

---

### Post by shooterae5 on 2006-07-06
doing an:   acpi -V gives me no info and it should give me everything about ac and battery...
same with acpi -a, acpi -s, acpi -b.

that was earlier today.

I booted up with AC and then got the idea to remove the battery. waited about 10 sec. then replace the battery and the meter showed the battery at 100% and on AC power. after unplugging the AC the meter changed to no battery and on AC only. If I plugged the AC back in nothing changed. I still not getting any information on the amount of power left in the battery.

this has got to be a config file that needs to be fixed but I have no idea where to look for it or what to change/edit if I find it.

anyone have idea's for me?

Saturday, July 08 2006  08:14 PM
more info to look at:

dale@Alix:~$ gnome-power-manager --verbose --no-daemon
[gpm_debug_init] gpm-debug.c:130 (20:07:51):     Verbose debugging enabled
[gpm_hash_new_devices_cache] gpm-hal-monitor.c:630 (20:07:51):   creating cache
[gpm_hal_has_power_management] gpm-hal.c:132 (20:07:51):         Power management type : acpi
[gpm_hash_new_kind_cache] gpm-power.c:1302 (20:07:51):   creating cache
[gpm_hash_new_device_cache] gpm-power.c:1328 (20:07:51):         creating cache
[gpm_manager_init] gpm-manager.c:1864 (20:07:51):        Using hal to monitor lid status
[gpm_hal_lid_is_closed] gpm-hal.c:187 (20:07:51):        Lid status: open
[gpm_brightness_init] gpm-brightness.c:135 (20:07:51):   No devices of capability laptop_panel
[gpm_idle_set_check_cpu] gpm-idle.c:206 (20:07:51):      Setting the CPU load check to 1
[gpm_manager_init] gpm-manager.c:1897 (20:07:51):        creating new tray icon
[gpm_dpms_set_enabled] gpm-dpms-x11.c:422 (20:07:51):    setting DPMS enabled: 1
[x11_sync_server_dpms_settings] gpm-dpms-x11.c:117 (20:07:51):   Syncing DPMS settings enabled=1 timeouts=0 0 0
[x11_sync_server_dpms_settings] gpm-dpms-x11.c:117 (20:07:51):   Syncing DPMS settings enabled=1 timeouts=0 0 0
[gpm_brightness_level_save] gpm-brightness.c:363 (20:07:51):     Saving brightness as 70%
*** WARNING ***
[gpm_hal_handle_error] gpm-hal.c:225 (20:07:51):         power save failed
(No powersave method found)
GNOME Power Manager has encountered a non-critical warning.
Consult [http://bugzilla.gnome.org/buglist.cgi?product=gnome-power-manager](http://bugzilla.gnome.org/buglist.cgi?product=gnome-power-manager) for any known issues or a possible fix.
Please file a bug with this complete message if not present
[gpm_screensaver_enable_throttle] gpm-screensaver.c:123 (20:07:51):      setThrottleEnabled : 1
[gpm_idle_set_system_timeout] gpm-idle.c:272 (20:07:51):         Setting system idle timeout: 1800
[x11_sync_server_dpms_settings] gpm-dpms-x11.c:117 (20:07:51):   Syncing DPMS settings enabled=1 timeouts=0 0 0
[gpm_manager_init] gpm-manager.c:1952 (20:07:51):        Using per-time notification policy
[gpm_manager_init] gpm-manager.c:1961 (20:07:51):        Using a supressed policy timeout of 5 seconds
*** WARNING ***
[main] gpm-main.c:238 (20:07:51):        Power Manager is already running in this session.

---

### Post by nab on 2006-07-06
I have a Toshiba M30x-165 with an fresh install of dapper.

acpi -V and gnome applets are working without any hassle. 
(At least I can't remember twiking anything in power management; but I remember that I had to tweak power management in breezy)

- Well, you probably made sure power management in BIOS is enabled. 
- Do you use the Omnibook kernel module for viewing and setting custom BIOS functions?
- Do you use the toshiba_acpi module? It's as far as I know written for a different BIOS and does not work on this machine.
-Have you tested the behavior with the live-CD? Just to make sure it isn't an upgarde or tweaking problem:) 

Just my 5 cents;) 
Niko

---

### Post by shooterae5 on 2006-07-06
[QUOTE=nab]I have a Toshiba M30x-165 with an fresh install of dapper.

acpi -V and gnome applets are working without any hassle. 
(At least I can't remember tweaking anything in power management; but I remember that I had to tweak power management in breezy)

- Well, you probably made sure power management in BIOS is enabled. 
- Do you use the Omnibook kernel module for viewing and setting custom BIOS functions?
- Do you use the toshiba_acpi module? It's as far as I know written for a different BIOS and does not work on this machine.
-Have you tested the behavior with the live-CD? Just to make sure it isn't an upgrade or tweaking problem:) 

Just my 5 cents;) 
Niko[/QUOTE]

My install is fresh install to. I can only find one bios control for power
and it is enabled. Power work under Ubuntu 5.04, I never could get 
it to work under 5.10, so I went back to 5.04. 

the toshiba_acpi module isn't showing up in the terminal or synaptic
package manager, so I don't think it is installed.

No I wasn't able to get it to work under the live CD. But I did a clean 
install anyway and now I'm trying to tweak it.

I'll work on getting "toshiba_acpi module" installed and get back to 
the forum about it

thnaks for the starting point

Dale

---

### Post by shooterae5 on 2006-07-10
I got this figured out...

I checked the BIOS version while rebooting the system. It was at Phoenix 1.2. Tried a couple of idea's I had, which didn't work. then went to the Toshiba web site to check for a BIOS update. there were several. I downloaded the latest, 1.9 and made the boot floppy (there are instruction for making a CD that come with the download). Ran it and now it works great.

Thanks to all for the help you all kept me thinking about it and now it works. It always helps to have someone to bounce ideas off of.

---

### Post by daynah on 2007-03-27
Please tell me if you get it working. I also have a Toshiba M35X and have the same problem as you do. My computer just proudly told me that it was all charged up, but my hardware says differently. Good job, ubuntu.

My friend, oh master of Linux did get it working on Dapper. After making me cry because he caused  "kernel panic." But I've updated to edgy and it's broken again.

M35X's also notoriously have a problem where the power socket gets a loose connection to the motherboard, so it would be nice for my laptop to be accurate in telling me when I'm getting power or when it just looks like I'm plugged in and ready. (I've never soldered, quite scared of this).

If my beg my friend to fix it again, I'll get him to write down how he does it so that I can do it next upgrade (soon! yay!) and that you can do it also.

---

### Post by shooterae5 on 2007-03-27
All I can help with is the fix I posted above. I had to update the laptops BISO to get power management to work correctly. My problems were not with Ubuntu, Gnome or any other part of the Ubuntu distro, It was an out dated BIOS. You can Find BIOS updates at the Toshiba web site for this model. 

Try this address:

[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modelLanding.jsp?ProductMenu_0=Portables&ProductMenu_1=Satellite&ProductMenu_2=835422&x=18&y=10&BV_SessionID=%40%40%40%400576767463.1119363229%40%40%40%40&BV_EngineID=ccciaddemeimjdgcgfkceghdgngdgnn.0&moid=835422&smoid=true&ct=MH&ListType=Model](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modelLanding.jsp?ProductMenu_0=Portables&ProductMenu_1=Satellite&ProductMenu_2=835422&x=18&y=10&BV_SessionID=%40%40%40%400576767463.1119363229%40%40%40%40&BV_EngineID=ccciaddemeimjdgcgfkceghdgngdgnn.0&moid=835422&smoid=true&ct=MH&ListType=Model)

---

