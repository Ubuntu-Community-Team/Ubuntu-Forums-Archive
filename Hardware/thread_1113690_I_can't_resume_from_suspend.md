---
title: "I can't resume from suspend"
date: 2009-04-01
forum: Hardware
---

### Post by tsger on 2009-04-01
I know this is one of those issues that plagues many users, but I thought I'd ask again, if anyone can tell me how to successfully resume from suspend when I have the proprietary nvidia driver installed.

It seems to be hit and miss, depending on the laptop.  I have a Dell Inspiron 8600, using the Nvidia GeForce FX Go5200 video card.

When I resume from suspend the screen pixels start to slowly light up, starting from the lower edge.  I then have to do a hard shut down, because I am afraid the display will get damaged.

I'd much appreciate any help!

Update:  I now have a different laptop, so I never got around to fixing the problem.  Thanks for the reply below, though!

---

### Post by William Anderson on 2009-04-24
Hi,

I have the same laptop and had issues with resume. I am running 9.04 Jaunty Jackalop and am using the open nv video driver.

To get suspend to resume correctly, I had to remove all of the HAL suspend quirks that were defined for this laptop. I detailed the steps that I took in the bug report that apport created related to this issue. The bug report is at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/361853](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/361853) . 

In short, I had to edit the file /usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-dell.fdi , search for the string "8600" used to match the hardware, and then remove the "8600" from the file. After rebooting with this change, suspend resumed with no issues, sound worked, network comes back up, video file play back works. 

Hope this helps,

William

---

### Post by UnixMan2 on 2011-12-14
Same problem with the now ancient Dell Inspiron 8600 with:

01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)

Fresh install of Ubuntu 11.10 "Oneiric Ocelot" (server) with TDE desktop ("Kubuntu trinity remix") manually installed afterwards.

By default, resume from both suspend to ram & to disk failed.

Problem solved by:

*) removing all "quirks" from the files:

/usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-dell.fdi

/usr/lib/pm-utils/video-quirks/20-video-quirk-pm-dell.quirkdb

*) adding "NvAGP " "1" to xorg.conf

I've also edited /etc/default/acpi-support; AFAIU in principle this should not matter. Nevertheless, changes are as follows:

- SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"
+ SUSPEND_METHODS="dbus-pm pm-utils"

- ACPI_SLEEP=true
+ #ACPI_SLEEP=true

- ACPI_HIBERNATE=true
+ #ACPI_HIBERNATE=true

- ACPI_SLEEP_MODE=mem
+ ACPI_SLEEP_MODE=standby

- SAVE_VBE_STATE=true
+ SAVE_VBE_STATE=false

- POST_VIDEO=true
+ POST_VIDEO=false

- # DOUBLE_CONSOLE_SWITCH=true
+ DOUBLE_CONSOLE_SWITCH=true

That's all folks!

Hope it helps.

---

