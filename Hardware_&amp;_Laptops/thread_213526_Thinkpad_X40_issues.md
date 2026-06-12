---
title: "Thinkpad X40 issues"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by cmsj on 2006-07-11
Hi

I just installed Dapper on a Thinkpad X40 and there are two things I'm trying to clear up (after what was otherwise a very successful install);

1) the power button doesn't seem to do anything - that is to say, it's not bringing up the shutdown/restart/suspend prompt, which is a bit weird. It switches the thing on fine, so I assume that whatever keycode it's sending or acpi event it's generating isn't being recognised

2) the power consumption seems a bit high - from a freshly charged battery (the thing is brand new and was charging most of yesterday evening, so should definitely be full) it reckons it's only going to get about 1 hour 45 mins of life, with the screen set to about 70% brightness. I did notice that laptop_mode is reporting that it's not enabled, but I want to be sure that I'm doing things "the ubuntu way" before I start hacking around on this myself.

Any/all input would be greatly appreciated :)

---

### Post by yzord on 2006-07-11
1) Doesn't do anything for me either (TP X31). Doesn't bother me, as I never use it. Sorry.
2) Laptop_mode is disabled by default, due to some hang issues. However, it's easily re-enabled (and I've never had a problem with it).

Go here:
[http://www.ubuntuforums.org/showthread.php?t=202240&highlight=laptop-mode+enable](http://www.ubuntuforums.org/showthread.php?t=202240&highlight=laptop-mode+enable)

And check out Huygen's post (it's the 2nd one). That oughta fix you right up.

HOWEVER, don't expect power usage to be as good as XP. As I've mentioned in another thread, Ubuntu only does CPU frequency throttling (you can add a little frequency monitor to your panel by right clicking on the panel, selecting Add to panel... and choosing it off the list under System and Hardware), while Speedstep under Windows does both automatic freq and voltage throttling. To get manual voltage throttling, you need to install Linux PHC and recompile the kernel (something I'm not about to attempt currently).

Here's the link to it:
[http://www.ubuntuforums.org/showthread.php?t=146366&highlight=phc](http://www.ubuntuforums.org/showthread.php?t=146366&highlight=phc)

Hope that helped,
Yz

---

