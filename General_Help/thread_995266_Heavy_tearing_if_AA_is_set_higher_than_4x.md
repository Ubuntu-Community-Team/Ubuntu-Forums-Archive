---
title: "Heavy tearing if AA is set higher than 4x"
date: 2008-11-27
forum: General Help
---

### Post by simpsonatwork on 2008-11-27
On my config (Nvidia GF7950GT 512, Intrepid with default drivers), when antialiasing in nvidia-settings is set to somewhat higher than 4x heavy tearing appears while moving windows, in dynamic scenes on movies etc.
I tried to play with CCSM settings  a lot on 'Display settings' tab of General options, no success. Here they are:
```
Texture filter: best
Detect refresh rate: unchecked
Lighting: checked
Refresh rate: 200 (tried with 60 of my LCD monitor, no way)
Sync to VBlank: checked
Detect outputs: checked
Outputs list: none
Overlapping output mode: smart
```

Is there any way to work around this? AA really does its job only beginning from 8x, but the tearing is just annoying and makes it uncomfortable to watch movies.

---

### Post by keypox on 2008-11-27
> **simpsonatwork said:**
> On my config (Nvidia GF7950GT 512, Intrepid with default drivers), when antialiasing in nvidia-settings is set to somewhat higher than 4x heavy tearing appears while moving windows, in dynamic scenes on movies etc.
I tried to play with CCSM settings  a lot on 'Display settings' tab of General options, no success. Here they are:
```
Texture filter: best
Detect refresh rate: unchecked
Lighting: checked
Refresh rate: 200 (tried with 60 of my LCD monitor, no way)
Sync to VBlank: checked
Detect outputs: checked
Outputs list: none
Overlapping output mode: smart
```

Is there any way to work around this? AA really does its job only beginning from 8x, but the tearing is just annoying and makes it uncomfortable to watch movies.

Yeah ati tears with compiz enabled, and disabled unless gl is selected in vlc.

---

### Post by simpsonatwork on 2008-11-28
> **keypox said:**
> Yeah ati tears with compiz enabled, and disabled unless gl is selected in vlc.

The problem is with Nvidia+Compiz, not ATI. No VLC too

---

