---
title: "t460 waking up after closing lid"
date: 2024-10-23
forum: Hardware
---

### Post by 7-vric-8 on 2024-10-23
I have a Lenovo T460 laptop. It was working as expected on 22.04 bit  after I upgraded it to 24.04 (upgrade in place), it started having power management  problems.   


     When I run the laptop off wall power or battery, after closing the  lid, or letting the machine go to sleep, the power button flashes  slowly, but touching the keyboard or pressing the power button does not  wake the machine up. Powering off the machine by holding the button down  long enough to turn off the laptop the only way I can get the machine  back. If the laptop is on battery, turning off the machine via the  system menu shuts it off hard. I can't get it to restart till I plug it  into line power.   


     ideas or suggestions where I should start looking?

[edit add log info]
- Boot df34be0d1d694e709405ab2bd11fbc5c --
Oct 23 14:27:34 juno systemd[1]: Starting systemd-logind.service - User Login Management...
Oct 23 14:27:35 juno systemd-logind[1808]: New seat seat0.
Oct 23 14:27:35 juno systemd-logind[1808]: Watching system buttons on /dev/input/event2 (Power Button)
Oct 23 14:27:35 juno systemd-logind[1808]: Watching system buttons on /dev/input/event0 (Lid Switch)
Oct 23 14:27:35 juno systemd-logind[1808]: Watching system buttons on /dev/input/event1 (Sleep Button)
Oct 23 14:27:35 juno systemd-logind[1808]: Watching system buttons on /dev/input/event3 (AT Translated Set 2 keyboard)
Oct 23 14:27:35 juno systemd-logind[1808]: Watching system buttons on /dev/input/event6 (ThinkPad Extra Buttons)
Oct 23 14:27:35 juno systemd[1]: Started systemd-logind.service - User Login Management.
Oct 23 14:27:44 juno systemd-logind[1808]: New session c1 of user gdm.
Oct 23 14:27:56 juno systemd-logind[1808]: New session 2 of user eric.
Oct 23 14:28:01 juno systemd-logind[1808]: Session c1 logged out. Waiting for processes to exit.
Oct 23 14:28:01 juno systemd-logind[1808]: Removed session c1.

[edit 2  power off doesn't]

doing more tests: shutdown doesn't.  shutdown gets almost all the way down but the keyboard backlight stays on and full shutdown take a long press on the power switch.

---

