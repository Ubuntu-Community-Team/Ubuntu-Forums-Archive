---
title: "INFO: Nvidia Refresh on boot in Kubuntu/Ubuntu"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by RevThain on 2007-08-06
Eurika! I think I've got it!

Ok, knowing nvidia in linux, I thought it was strange that the KDE control center said the refresh rate was 51hz. Every linux distro I have used in the past 4 years said 50hz.
i.e. Knoppix, Kanotix, Mandrake, Redhat

So I started messing with the options it gave me. which were: 51, 55, 57, 59 hz.

If I set it at 55, I got 75, if I set it at 57, I got 60, and if I set it at 59, I got 50.

Using nvidia-settings, I set the display for 1024x768@85hz. Then I went to system settings to monitor/display settings, and set it for 55hz, which was the highest "actual" setting. I rebooted, and Waalaaa, It booted right up to what was set in xorg.conf, which was 85hz!

I went to the control centers display settings, and lo and behold, it's set at 50hz now, which is where it should be.

I tested changing video modes now with nvidia-settings, and all is well, everything works as it should, keeping the mode I set in nvidia settings.

I believe this should work for Ubuntu as well, as I know from past experience that in linux, nvidia-setting takes control of control centers setting.

This was a strange way to do it, but it worked.

Moral of the story?

If you can get control centers refresh rate setting to show 50hz, you're all good.

---

