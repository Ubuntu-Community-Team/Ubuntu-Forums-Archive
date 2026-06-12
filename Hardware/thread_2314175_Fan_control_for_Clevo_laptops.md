---
title: "Fan control for Clevo laptops"
date: 2016-02-18
forum: Hardware
---

### Post by AqD on 2016-02-18
I completed a fan control indicator for Clevo laptops by reverse-engineering the ECView program (found on some Chinese website). Anyone know what is the appropriate subforum for this? Also is there some de-facto fan control/monitor utility that I can integrate mine into, instead of an independent program? lm-sensors seems dead...

The source code is on [github](https://github.com/AqD/clevo-indicator)


[img]https://camo.githubusercontent.com/a918478d2e232c7b42d92f7b3c131e6c5a7a72fa/687474703a2f2f692e696d6775722e636f6d2f75637757784c712e706e67[/img]

On the terminal it shows messages from the new auto-fan control which is far more aggressive than the builtin algorithm, due to the latter being broken on newer models.

It might be dangerous to write into the IO ports concurrently by multiple programs, as a result it uses information from sysfs whenever possible and also added signal control to prevent unclean exit and have detection of multiple instances, but there is no guarantee this program wouldn't fry your laptop. Manual control on windows did cause the fan to stop once or twice last year, and caused my laptop to shut down due to overheat (but now with auto control it should be able to correct itself).

No support for multiple fans in workstation models.

---

