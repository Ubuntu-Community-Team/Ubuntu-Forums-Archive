---
title: "issue with Hauppauge TV tuner, possibly after software update"
date: 2022-02-26
forum: Hardware
---

### Post by ccrs8 on 2022-02-26
I'm running Xubuntu 20.04 LTS.  I have a WinTV-HVR-955Q Hauppauge OTA TV tuner.  I got it in mid-2020 (after already running 20.04) and installed it very easily using the instructions found here:
[https://hauppauge.com/pages/support/support_linux.html](https://hauppauge.com/pages/support/support_linux.html)

Since then I have been flawlessly watching my OTA TV with it using Kaffeine.  I probably use it two or three times a week, deviating quite a bit depending on the sports schedule. Some time last week I launched Kaffeine and the TV picture didn't appear.  At first I thought it was an issue with the antenna itself, but a few days later I tried again and got the same result.  I hooked up the coax cable to a real TV and got OTA picture right away without issue, meaning the problem was with the computer and/or tuner.

I hooked the coax back to the computer and did some troubleshooting.  I see the tuner in the Configure Television setup in Kaffeine:
[ATTACH=CONFIG]290098[/ATTACH]

However, in the Channels section of Kaffeine, the Source is greyed out with no ability to select my device:
[ATTACH=CONFIG]290099[/ATTACH]

Finally, the pertinent dmesg output is:
```

si2157 11-0060: found a 'Silicon Labs Si2157-A30 ROM 0x50'
si2157 11-0060: Can't continue without a firmware.

```

I didn't install anything or mess with anything between the last time I successfully watched OTA TV on the machine and when it stopped working.  However, I run Software Updater every morning when I turn on the machine and more often than not something gets updated.  Maybe I'm misremembering, but I think I even recall one of the updates being for linuxtv, but I can't say for sure.

Any suggestions?  Either for a fix or for a more specific forum I could post my question to?

---

### Post by TheFu on 2022-02-26
1 - I'd check the apt logs to see what was installed.
2 - I'd stop patching so often.  Knock that down to once a week, so you have 5+ days of a stable system and time for little package dependency errors to be corrected BEFORE they impact your box.

I have a Haupauge 950Q and it works find on 18.04. I don't have any 20.04, sorry. 

However, I generally use HDHR tuners which are networked and integrate with Jellyfin media server really well. Any computer on the LAN can access an available tuner from the HDHR using DLNA or the normal protocol. HDHR is probably the easiest and most supported tuners in North America.  Plus, the coax runs only need to get to the tuner, not your computer.  Any DLNA client can access the tuners - so VLC works and there are specific URLs if you just want to record or watch a show.  Say I want to watch virtual channel 2.1 - then the URL is [http://hdhr4:5004/auto/v2.1](http://hdhr4:5004/auto/v2.1)   .... so if I use **mpv [http://hdhr4:5004/auto/v2.1](http://hdhr4:5004/auto/v2.1)** it will display a playback window with that live channel.  To record, I use **wget [http://hdhr4:5004/auto/v2.1](http://hdhr4:5004/auto/v2.1)** - well, I have a little script that let's me control the duration and filename everything gets saved into, but is basically a wget command for a specific period of time.  Or just use Jellyfin, tell it you have an HDHR (it can search the LAN) and then hook up schedule data and you have a TiVo/DVR.  Always want to record every episode of "Grand Ole Opry" with Minnie Pearl?   You can.

---

### Post by ccrs8 on 2022-02-27
Alright, I figured it out.  Per the apt logs, on 2/18 linux-mediatree was updated from 0.2.2+focal to 0.2.3+focal.  In the past when that package was updated, I didn't have to do anything, but for whatever reason this time it messed up the firmware.  I followed the instructions found on the original hauppauge URL I linked to ([https://hauppauge.com/pages/support/support_linux.html](https://hauppauge.com/pages/support/support_linux.html)) titled "Firmware Install" even though it specifically stated that my device and location meant that I didn't have to do that step (and I definitely did NOT have to do that step when originally setting things up back in mid-2020) and after doing so everything resumed working perfectly.  The following fixed all of my problems immediately:
```

sudo apt-get install linux-firmware-hauppauge

```

---

