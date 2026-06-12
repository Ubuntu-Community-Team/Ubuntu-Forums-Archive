---
title: "No sound from Windows Surface &quot;tablet&quot; speakers"
date: 2023-01-18
forum: Hardware
---

### Post by yesok2 on 2023-01-18
Ubuntu 22.10

This [github]("https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup") was used for conversion and got the touchscreen & pen working
When I try this command from [known issues ]("https://github.com/linux-surface/linux-surface/wiki/Known-Issues-and-FAQ") "sudo amixer sset "Auto-Mute Mode" Disabled"
I see errors like this > ALSA lib confmisc.c:855:(parse_card) cannot find card '0'

How do I configure sound cards? 

I was hoping to follow this [tutorial]("https://www.freecodecamp.org/news/how-to-fix-broken-audio-in-headphones-and-speakers-linux/") by freecodecamp

But I'm not sure how to access [Alsamixer]("http://https://www.alsa-project.org/wiki/Download"), or its equivalent, or which of  the following downloads I should install from Alsaproject (if at all)



[LIST]
[*][[COLOR=#202122]2.1[/COLOR]alsa-driver]("https://www.alsa-project.org/wiki/Download#alsa-driver")
[*][[COLOR=#202122]2.2[/COLOR]alsa-lib]("https://www.alsa-project.org/wiki/Download#alsa-lib")
[*][[COLOR=#202122]2.3[/COLOR]alsa-utils]("https://www.alsa-project.org/wiki/Download#alsa-utils")
[*][[COLOR=#202122]2.4[/COLOR]alsa-tools]("https://www.alsa-project.org/wiki/Download#alsa-tools")
[*][[COLOR=#202122]2.5[/COLOR]alsa-firmware]("https://www.alsa-project.org/wiki/Download#alsa-firmware")
[*]2.6alsa-plugins


[*]
[/LIST]
I think I installed Pulseaudio and these settings became active. Although no sound.

Thanks
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291590&stc=1[/IMG]

---

