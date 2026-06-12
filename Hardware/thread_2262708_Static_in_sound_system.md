---
title: "Static in sound system"
date: 2015-01-26
forum: Hardware
---

### Post by knight69 on 2015-01-26
I'm sure this is not new, but I still can't find a solution.  

In the last ubuntu 12.04 update (last Friday), my sound system went to hell (again).  The sound from the speaker port is distorted with the static volume being proportional to the sound volume.  (Low sound volume, low static - high sound volume, loud static - speach is unintelligible).  The last time this happened, I followed the instructions at the [SoundTroubleshootingProcedure - Community Help Wiki]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") site and the problem went away and my sound worked perfectly.  This time I followed the instructions and there is no change.  The problem is unique to the speaker port at the back and doesn't affect the headset port.

I ran the following diagnostic commands 
wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh

and copied the results to a file that I just attached to this post (hopefully).

Help solving this problem will be greatly appreciated.  (Help solving it forever would be even more appreciated.)


PS  This is a dual boot computer with Windows 7.  The sound system is perfect in Windows, so we can eliminate the speakers being the problem.

---

