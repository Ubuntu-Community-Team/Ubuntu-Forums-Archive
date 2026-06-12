---
title: "Extra keys on laptop"
date: 2008-04-25
forum: Hardware
---

### Post by yadayada2 on 2008-04-25
Can anyone tell me how to get my extra keys working? I am speaking of the Fn keys as well as the other buttons (AV Mode, mute, volume up and down, capture and so on).

My laptop is a VAIO CR420E/T, if that is of any concern.

---

### Post by yadayada2 on 2008-04-26
At least for volume up, down and mute I found a solution. I started xev to get the key codes of the corresponding buttons. So I got 160, 174 and 176. With these I could fill up my personal .xmodmap in my home directory (which didn't exist before). The symbols were XF86AudioLowerVolume and so on.

The xfce settings manager -> keyboard allready had those symbols assigned to aumix with different parameters like -v-10. All I had to do then was to restart the X server. Now it works fine :)

---

