---
title: "aticonfig seems to have broken"
date: 2010-05-13
forum: Hardware
---

### Post by rldasilva on 2010-05-13
Greetings,

I have been having an aggravating day trying to set up my new monitor. I have an HP laptop with an ATI graphics card. I used to have an old second monitor which I attached to my laptop and worked perfectly.

I went through the normal steps of 
```
sudo aticonfig --initial=dual-head --screen-layout=right

sudo aticonfig --dtop=horizontal --overlay-on=1
```

which had worked on my previous monitor and it was working. Then I noticed that the image wasn't filling the whole screen so I started to mess with 
```
aticonfig --set-dispattrib=crt1,positionX:0 
aticonfig --set-dispattrib=crt1,sizeY:0 
```

and I had it working. It was perfect. Then I rebooted and after the Ubuntu progress bar fills up the screen just hangs on a black screen forever never reaching the log on screen. So I rebooted in recovery mode and replaced my xorg.conf with the failsafe and it worked (but the monitors only mirror each other now).

Additionally now if I simply use
```
sudo aticonfig --initial
```
the same thing happens (if I reboot it will just hang forever without actually loading in). So I copied to my older xorg.conf and connected to my old monitor. Nothing should have changed and that doesn't work either!!!! What used to work before is now completely broken!!!

I googled for a few hours and couldn't find anything.

Please I am completely stumped and at a complete loss! Any help would be appreciated.

Thank you in advance,
rldasilva

---

