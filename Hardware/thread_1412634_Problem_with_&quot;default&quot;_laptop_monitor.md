---
title: "Problem with &quot;default&quot; laptop monitor"
date: 2010-02-21
forum: Hardware
---

### Post by stayfrosty555 on 2010-02-21
When I powered on my computer this morning I had no picture on my "internal" display on my laptop Half of it was full of random lines and the other was totally black. I checked nvidia-settings (I got an  9600 integrated graphics card). The laptop screen was there but i was only allowed to select resolutions up to 640x480 while the native resolution on the screen is 1280x800. I have tested different drivers 173,185,190,195 without luck.

At first I thought the display was broken since it didnt work in Windows Vista either (i got dualboot) but an driver update solved it. Any one got a clue? It was working the night before and i cant remember updating packages related to the graphics card or something like that so I can't figure out while it stopped working.

---

### Post by stayfrosty555 on 2010-02-22
I'll give this another try.

---

### Post by RRF2525 on 2010-02-22
I'm trying to tech-out a NV related issue too...mine is not exactly like yours but in the end it seems that the NV drivers are corrupting the system.  I have no basis for this but all I can get on my machine is an Unknown monitor and 1280x960 (I need 1680x1050).

I would start looking at recent updates...do you allow updates to d/l and install automatically?  If so I'd suggest disabling that feature and manually check for updates.

---

### Post by stayfrosty555 on 2010-02-22
I Saw your thread after I bumped this thread, and yes I also think that the drivers have corrupted / destroyed the monitors EDID. It seems logic now that I know of the settings in the monitor since the screen in windows was also reconfigured (max 1024x768 ) at the same time. Atfer installing new drivers it solved the issue in Windows but in linux they remain. Next I will try to use an windows tool to copy the edid in the registry to the monitor and see if it works.

---

### Post by stayfrosty555 on 2010-02-22
I managed to solve it! :)

The problem was that it could not read the EDID information from the laptop screen. I wasn't able to retrieve the EDID with get-edid in linux and didn't do any more research to solve it from within ubuntu, since i got Windows Vista on the same computer. I downloaded Phoenix EDID Designer and read the edid from the registry, then exported it to a "raw" file. After that i booted up ubuntu again and copied the raw file to my X11 folder (the location shouldn't matter) and added Option         "CustomEDID" "DFP-0:/etc/X11/monitor.raw" under the [Device] section in my xorg.conf

---

