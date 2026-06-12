---
title: "Override Google Hangouts/Voice Automatic Mic Volume"
date: 2015-11-26
forum: Hardware
---

### Post by bathynomusBLUE on 2015-11-26
Disclaimer: Use information at own risk

Override Google Hangouts automatic microphone volume adjustment using a bash script. This is an alternative method to override the mic volume and stop auto-adjusting, if the audio-flags=1 option does not work for you.

Distros: Xubuntu 15.04, Ubuntu 15.04
[HR][/HR]1. mousepad volume_fixed.sh

2. paste code:
```
#!/bin/bash
while true
do
  pactl set-source-volume [COLOR=#ff0000]2[/COLOR] 100%
done
```
3. **[COLOR=#ff0000]edit[/COLOR]** (see below)
4. save
5. run script from Terminal
sh volume_fixed.sh

As long as you keep the script running, it will keep resetting the volume to 100%.

[HR][/HR]What do I need to edit?
> set-source-volume 2, the number **[COLOR=#ff0000]2[/COLOR]** is the **[COLOR=#ff0000]index[/COLOR]** number to identify your mic
> 100% is the mic volume

How do I find my [COLOR=#ff0000]**index**[/COLOR] number?
1. change your mic volume to an odd number, like 129, this will help you to find the correct device/**[COLOR=#ff0000]index[/COLOR]** number in the next steps, I use pavucontrol for this step
2. open Terminal
3. pacmd list-sources
4. scroll up to find the 129%, the [COLOR=#ff0000]**index:**[/COLOR] number above that is your mic
5. change the [COLOR=#ff0000]**index**[/COLOR] number in your volume_fixed.sh script

[[IMG]http://2.bp.blogspot.com/-8FP9X-M6Aj8/VlZH7woLCGI/AAAAAAAAAB0/i7zGfps2PYY/s1600/129.png[/IMG]]("http://2.bp.blogspot.com/-8FP9X-M6Aj8/VlZH7woLCGI/AAAAAAAAAB0/i7zGfps2PYY/s1600/129.png")

[[IMG]http://3.bp.blogspot.com/-E_0AO7L0aXg/VlZH9WsFn4I/AAAAAAAAAB8/uaxg4ItVAHU/s1600/find_pactl_device_index.png[/IMG]]("http://3.bp.blogspot.com/-E_0AO7L0aXg/VlZH9WsFn4I/AAAAAAAAAB8/uaxg4ItVAHU/s1600/find_pactl_device_index.png")

---

