---
title: "Overclocking Nvidia"
date: 2015-09-19
forum: Hardware
---

### Post by cranerja on 2015-09-19
Hello I am running a GTX970 with the driver 352.30. I changed my coolbits from 3 (I believe) to 8 in order to overclock the card. Since then I have lost fan speed controls and any clock changes I make are lost on reboot. How can keep access to fan speeds and save the clock settings?

---

### Post by efflandt on 2015-09-20
Based on [http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item](http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item)

8 is gpu & memory speed adders, 12 is that and manual fan speed. So you likely had 4 set before for manual fan speed only. But unless you want a high enough manual fan speed all the time or have an overheating issue, it may be best to leave that on auto.

I have MSI Twin Frozr Gaming GTX 750 Ti OC that is hardware limited to 60 watts max (no external power connections). So that sort of limits its gain even if its gpu is bumped 220 MHz and it never gets over about 54 C max with its fans automatically bumped up only a few % from 33% minimum (quiet). I do not think you can set up a profile using NVIDIA X Server Settings to save gpu and mem clock offsets, but you can set them using **nvidia-settings** in a script somewhere. Note that I only have 2 performance levels 0 and 1, and speed offsets (in MHz after =) apply to level [1] in my case:```
efflandt@XPS-8100-1404:~$ nvidia-settings -a [gpu:0]/GPUGraphicsClockOffset[1]=220

  Attribute 'GPUGraphicsClockOffset' (XPS-8100-1404:0[gpu:0]) assigned value 220.

efflandt@XPS-8100-1404:~$ nvidia-settings -a [gpu:0]/GPUGraphicsClockOffset[1]=0

  Attribute 'GPUGraphicsClockOffset' (XPS-8100-1404:0[gpu:0]) assigned value 0.
```See **man nvidia-settings**. These are some relevant attributes:```
Attribute 'GPUGraphicsClockOffset':
  - Attribute value is an integer.
  - Attribute is not written to the rc file.
  - Attribute not queried in 'query all'.
  This is the offset amount, in MHz, to over- or under-clock the Graphics Clock.  Specify the performance level in square brackets
  after the attribute name.  E.g., 'GPUGraphicsClockOffset[2]'.

Attribute 'GPUMemoryTransferRateOffset':
  - Attribute value is an integer.
  - Attribute is not written to the rc file.
  - Attribute not queried in 'query all'.
  This is the offset amount, in MHz, to over- or under-clock the Memory Transfer Rate.  Specify the performance level in square
  brackets after the attribute name.  E.g., 'GPUMemoryTransferRateOffset[2]'.
```And look through **nvidia-settings -e all | less** for settings related to fan speed. I am just not sure where to put nvidia-settings commands to run automatically when X starts, or maybe just run a shell script to set over-clocking when you are going to game.

---

### Post by cranerja on 2015-09-20
> **efflandt said:**
> Based on [http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item](http://www.phoronix.com/scan.php?px=MTY1OTM&page=news_item)

8 is gpu & memory speed adders, 12 is that and manual fan speed. So you likely had 4 set before for manual fan speed only. But unless you want a high enough manual fan speed all the time or have an overheating issue, it may be best to leave that on auto.

I have MSI Twin Frozr Gaming GTX 750 Ti OC that is hardware limited to 60 watts max (no external power connections). So that sort of limits its gain even if its gpu is bumped 220 MHz and it never gets over about 54 C max with its fans automatically bumped up only a few % from 33% minimum (quiet). I do not think you can set up a profile using NVIDIA X Server Settings to save gpu and mem clock offsets, but you can set them using **nvidia-settings** in a script somewhere. Note that I only have 2 performance levels 0 and 1, and speed offsets (in MHz after =) apply to level [1] in my case:```
efflandt@XPS-8100-1404:~$ nvidia-settings -a [gpu:0]/GPUGraphicsClockOffset[1]=220

  Attribute 'GPUGraphicsClockOffset' (XPS-8100-1404:0[gpu:0]) assigned value 220.

efflandt@XPS-8100-1404:~$ nvidia-settings -a [gpu:0]/GPUGraphicsClockOffset[1]=0

  Attribute 'GPUGraphicsClockOffset' (XPS-8100-1404:0[gpu:0]) assigned value 0.
```See **man nvidia-settings**. These are some relevant attributes:```
Attribute 'GPUGraphicsClockOffset':
  - Attribute value is an integer.
  - Attribute is not written to the rc file.
  - Attribute not queried in 'query all'.
  This is the offset amount, in MHz, to over- or under-clock the Graphics Clock.  Specify the performance level in square brackets
  after the attribute name.  E.g., 'GPUGraphicsClockOffset[2]'.

Attribute 'GPUMemoryTransferRateOffset':
  - Attribute value is an integer.
  - Attribute is not written to the rc file.
  - Attribute not queried in 'query all'.
  This is the offset amount, in MHz, to over- or under-clock the Memory Transfer Rate.  Specify the performance level in square
  brackets after the attribute name.  E.g., 'GPUMemoryTransferRateOffset[2]'.
```And look through **nvidia-settings -e all | less** for settings related to fan speed. I am just not sure where to put nvidia-settings commands to run automatically when X starts, or maybe just run a shell script to set over-clocking when you are going to game.

Alright, thank you for how to set it through terminal. That may just be easier. But I do need manual fan speeds because of where I live my card gets pretty hot and the fan doesn't automatically go high enough.

---

### Post by pqwoerituytrueiwoq on 2015-09-20
it would be easier to stick a side case fan on the PC for the gpu
alternatively you can modify the GPUs firmware and flash it (this is how i OCed my 650 Ti Boost before we could OC with software on linux)
[http://www.overclock.net/t/1467851/nvidia-maxwell-kepler-bios-editing-thread-gtx-2xx-to-9xx-now-supported](http://www.overclock.net/t/1467851/nvidia-maxwell-kepler-bios-editing-thread-gtx-2xx-to-9xx-now-supported)
you probably can adjust the fan speeds from the firmware editing tools

---

### Post by cranerja on 2015-09-20
> **pqwoerituytrueiwoq said:**
> it would be easier to stick a side case fan on the PC for the gpu
alternatively you can modify the GPUs firmware and flash it (this is how i OCed my 650 Ti Boost before we could OC with software on linux)
[http://www.overclock.net/t/1467851/nvidia-maxwell-kepler-bios-editing-thread-gtx-2xx-to-9xx-now-supported](http://www.overclock.net/t/1467851/nvidia-maxwell-kepler-bios-editing-thread-gtx-2xx-to-9xx-now-supported)
you probably can adjust the fan speeds from the firmware editing tools
I already have a fan jerryrigged to every sensible area. And I will look into it, even though I would rather not risk it.

---

