---
title: "[SOLVED] Sound drivers."
date: 2008-12-24
forum: Hardware
---

### Post by raj.adluri@gmail.com on 2008-12-24
Hi,

I have installed Ubuntu 8.10 desktop today and looks like all the device drivers are installed by default. I also have Windows XP installed on the same computer. But when I play any media file from Ubuntu, the sound is unusually low even though the sound volume on the notification area and in the media player is at its maximum.

Is there a place where I can check if the Device drivers are installed properly like Device management in Windows XP. Or if some device drivers are not properly installed, then how to install them online when we know the device model number etc.
Please do the needful as I am basically using Ubuntu for email, Playing music and browsing. . . .this does not let me play my music files with full volume. . .I use VLC player to play music files. . . 

Thanks,
Rajesh Adluri.

---

### Post by Nepherte on 2008-12-24
Are both channels 'Master' and 'PCM' maxed? You can verify it by double clicking on the volume icon in the notification area.

---

### Post by raj.adluri@gmail.com on 2008-12-24
Hello Nepherte,

Thanks for the quick resopnse on this one. Can you please brief me whether they both have to be at their maximum or should they be minimum. And if they are already at their maximum, and I still continue to get the low volume, then what else do I need to check in that case.

Thanks,
Rajesh Adluri.

---

### Post by namdung on 2008-12-24
Type in terminal: alsamixer

Use arrow keys to adjust the volume level.

---

### Post by Nepherte on 2008-12-24
To raise the volume, you will need to raise one or both sliders. The volume icon itself only controls one channel. You can choose which one, but both channels control the volume. So if, let's say the Master channel is up all the way, you can still raise the volume if PCM is not at its maximum.

I can't think of anything else right now if that doesn't work.

---

### Post by raj.adluri@gmail.com on 2008-12-26
Hey !!!!!!!!!!! I am all set now the sound is now increased and much metter than Windows now.

Thanks,
Rajesh Adluri.

---

