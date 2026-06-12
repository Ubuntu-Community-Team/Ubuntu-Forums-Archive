---
title: "Simple nVidia PRIME and Bumblebee configuration"
date: 2016-03-17
forum: Hardware
---

### Post by THastings on 2016-03-17
[SIZE=3][FONT=Ubuntu]**Introduction**[/FONT][/SIZE]
[FONT=Ubuntu]For using Optimus hardware in GNU/Linux environments, nVidia's official PRIME package was the to-go solution in recent times. Bumblebee, the open-source implementation of Optimus isn't considered too efficient, sometimes even slow. I found a new way of using these solutions together, resulting in unexpectedly high performance.[/FONT]

[SIZE=3][FONT=Ubuntu]**Hardware and software**[/FONT][/SIZE]
[FONT=Ubuntu]Asus G46VW (i7-3630QM with Intel HD Graphics 4000 and GTX 660M)[/FONT]
[FONT=Ubuntu]Ubuntu 14.04.4 MATE 64-bit[/FONT]
 
[SIZE=3][FONT=Ubuntu]**The idea**[/FONT][/SIZE]
[FONT=Ubuntu]A known issue with PRIME is that it doesn't let the Intel GPU synchronize each frame with the built-in display if the nVidia card is selected, resulting in massive tearing while watching videos or playing games. Solving this was my primary intention, this is why I started fiddling around the drivers and different packages.[/FONT]
[FONT=Ubuntu]I started out on a system with PRIME set up and working properly. Since I didn't care much about losing the installation, I acted brave and added Bumblebee to the system. It worked fine. When I  removed nvidia-prime (in order to see if Bumblebee even works), I got to the blank login screen that shows up when video drivers fail to initialize. So from a terminal I reinstalled it and worked again like a charm. From that point on I started experimenting to create a tutorial for it.[/FONT]

[SIZE=3][FONT=Ubuntu]**Method**[/FONT][/SIZE]
[FONT=Ubuntu]In order to achieve this (tested it multiple times) I followed these steps:[/FONT]
[FONT=Ubuntu]1. Install Ubuntu MATE[/FONT]
[FONT=Ubuntu]2. Run all the official updates[/FONT]
[FONT=Ubuntu]3. Open a terminal (Ctrl+Alt+T) and run these commands:[/FONT]
```

[FONT=Ubuntu]sudo apt-get install nvidia-352 nvidia-settings nvidia-prime[/FONT]
[FONT=Ubuntu][FONT=Ubuntu]sudo [/FONT]reboot[/FONT]
```
[FONT=Ubuntu]4. Open a terminal again:[/FONT]
```

[FONT=Ubuntu]sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic[/FONT]
[FONT=Ubuntu]sudo reboot[/FONT]
``` 
[FONT=Ubuntu]5. One last time:[/FONT]
```

[FONT=Ubuntu]sudo prime-select intel[/FONT]
[FONT=Ubuntu][FONT=Ubuntu]sudo [/FONT]reboot[/FONT]
```
[FONT=Ubuntu]6. You're ready to go.[/FONT]
[FONT=Ubuntu]7. When launching something graphically intensive, use the term “optirun”, e.g.:[/FONT]
```

[FONT=Ubuntu]optirun steam[/FONT]
``` 
 
[SIZE=3][FONT=Ubuntu]**Performance**[/FONT][/SIZE]
[FONT=Ubuntu]Originally I expected Bumblebee to be slower, but it isn't, according to the numbers.[/FONT]
 
**[FONT=Ubuntu]1. GRID Autosport benchmark mode, ultra settings, full screen@1366x768, no AA[/FONT]**
[FONT=Ubuntu]Running *with optirun* (prime-select intel)[/FONT]
[FONT=Ubuntu]average FPS: 32.87[/FONT]
[FONT=Ubuntu]min FPS: 25.29[/FONT]
[FONT=Ubuntu]max FPS : 46.21[/FONT]
 
[FONT=Ubuntu]Running *without optirun* (prime-select nvidia)[/FONT]
[FONT=Ubuntu]average FPS: 32.03[/FONT]
[FONT=Ubuntu]min FPS: 25.65[/FONT]
[FONT=Ubuntu]max FPS: 43.45[/FONT]

 
**[FONT=Ubuntu]2. Unigine Heaven Benchmark 4.0, medium quality, full screen@1366x768, 2xAA[/FONT]**
[FONT=Ubuntu]Running *with optirun* (prime-select intel)[/FONT]
[FONT=Ubuntu]score: 952[/FONT]
[FONT=Ubuntu]average: 37.8[/FONT]
[FONT=Ubuntu]min: 9.4[/FONT]
[FONT=Ubuntu]max: 65.5[/FONT]
 
[FONT=Ubuntu]Running *without optirun* (prime-select nvidia)[/FONT]
[FONT=Ubuntu]score: 925[/FONT]
[FONT=Ubuntu]average: 36.7[/FONT]
[FONT=Ubuntu]min: 18.0[/FONT]
[FONT=Ubuntu]max: 64.0[/FONT]
 
[SIZE=3][FONT=Ubuntu]**Issues**[/FONT][/SIZE]
[FONT=Ubuntu]The only problem I had was that once I used optirun by accident while prime-select was set to nvidia. The application ran fine, but the system froze after exiting and I had to force reboot. Note, that this usage scenario isn't intended and shouldn't occur if the tutorial was followed properly.[/FONT]
 
[SIZE=3][FONT=Ubuntu]**Conclusion**[/FONT][/SIZE]
[FONT=Ubuntu]The framerates produced with the explained method are very close to the ones I got by using the traditional PRIME solution, but when using optirun, every frame is synced to the screen, resulting in a more enjoayble overall experience.[/FONT]
[FONT=Ubuntu]Even if this is Bumblebee only and has nothing to do with PRIME, this guide may help others set it up, since nvidia-settings and nvidia-prime configure everything for Bumblebee, making it easy to use for anyone.[/FONT]

---

