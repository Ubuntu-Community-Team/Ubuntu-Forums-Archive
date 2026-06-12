---
title: "Nvidia Displayport 2nd monitor issues with 15.10 Wily"
date: 2015-11-28
forum: Hardware
---

### Post by DJonsson2008 on 2015-11-28
With Nvidia I'm unable to get a dual monitor setup going with Ubuntu 15.10 using a display port. The VGA port works no problem.

Nouveau drivers work no problem.  But after trying various flavours of Nvidea drivers the only way I could get Nouveau to work again was to purge all Nvidea
items from the install. 

I've tried various versions of Nvidia drivers 340.96, 304.,352...

None of them will fully recognize the display port monitor. 

All of them have compatibility issues with Xubuntu display settings,
generally making the Xubuntu display settings widget unusable.

xrandr 
xrandr --output DisplayPort-0 --left-of VGA-0 --rotate left --primary --output DisplayPort-0 --auto

Returns error unable to see Displayport error
along with  
"Failed to get size of gamma for output default."

Any suggestions appreciated. 


Video card : GT218GLM [Quadro FX 380M]
Xubuntu/Ubuntu 15.10
Intel I7 CPU

---

### Post by DJonsson2008 on 2015-11-28
Research on the Nvidia site was very helpful.

[https://devtalk.nvidia.com/default/topic/791786/linux/dpms-not-working-on-gtx980-with-displayport-connection/3](https://devtalk.nvidia.com/default/topic/791786/linux/dpms-not-working-on-gtx980-with-displayport-connection/3)

This development discussion revealed variances between 
Nvidia driver sets, with some driver sets regressing the displayport feature.

358.16, 352.63 revisions were reported as working well with displayport,
but often with subsequent revisions not working.

So I downloaded those 2 run files. They reported only 340 legacy would work.

The Nvidia dev discussion stated that 340.96 was working 
so downloaded that update from there and installing it solved the problem.

[http://www.ubuntuupdates.org/package/core/wily/restricted/updates/nvidia-340](http://www.ubuntuupdates.org/package/core/wily/restricted/updates/nvidia-340)

Xubuntu display settings work as expected and now on dual screen with Nvidia.

---

