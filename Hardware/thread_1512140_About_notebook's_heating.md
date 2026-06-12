---
title: "About notebook's heating"
date: 2010-06-17
forum: Hardware
---

### Post by Ramy89 on 2010-06-17
Lately I got an exaggerate heating of my notebook,so I upgraded the firmware I have on windows.When I use windows it seems all normal,by upgrading the firmware and changing consume settings now it goes better,but does this also affects ubuntu?
When I use linux my pc seems to heat faster than when I use widnows,how do I install a new firmware on ubuntu or something to avoid the pc to heat too much?

---

### Post by yossell on 2010-06-17
There are some issues with ubuntu's handling of power consumption of laptops, many reporting computers that run hotter than under windows. 

My own experience, I found that with, some tweaking, my laptop battery runs longer than under windows, fans come on less often. 

First thing you might try, add cpu frequency scaling monitor to gnome panel, and set to ondemand. Second thing, something I found very useful, install the programme powertop, run it as root from a terminal, and follow its advice and analysis.

---

### Post by Ramy89 on 2010-06-18
Ok with powertop now it's much easier,I have just to press the shortcut and it does all the job itself.Thanks for this suggestion.
But can you now tell me where to find the GNOME panel?

---

### Post by yossell on 2010-06-19
I was just referring to the panels that appear on the standard ubuntu install - the ones that contain 'Applications Places Systems' menu. I think it's default is as the top in the vanilla install, but I tend to have it at the bottom. If you right click some empty space and select add to panel, you'll find a menu of things to add. 

If you're running Kubuntu or Lubuntu though, I don't think you'll have gnome panel running. Some people prefer the 'performance' setting to the 'on-demand' setting. I'm sure there are some terminal commands that will let you do it in whatever you system. This might be a help:

[http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)

but it's dense stuff!

---

### Post by Ramy89 on 2010-06-19
The pc power is now set on "ondemand",it automatically switches the processors,it charges the C1 when the C3 is full,the C2 has always kind of 0.5% or less,it isn't used.
Well I guess that now it's a matter of handling the kernel to reduce the consume.
Thanks for the info,I think for the moment this issue might be considered solved.

---

