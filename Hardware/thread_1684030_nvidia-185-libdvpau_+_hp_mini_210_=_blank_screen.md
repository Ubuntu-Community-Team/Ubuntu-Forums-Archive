---
title: "nvidia-185-libdvpau + hp mini 210 = blank screen"
date: 2011-02-08
forum: Hardware
---

### Post by pjdfred on 2011-02-08
Just so anyone else who has this problem can find this - In an attempt to get DVD playback working I installed a bunch of crap I probably shouldn't have, which didn't do much until my first full reboot. Then mutter refused to start because it couldn't find the GLX extension, resulting in a nice background after auto-login but nothing else.

Some trial and error after searching though /var/log/dpkg.log identified nvidia-185-libdvpau as the culprit - I've verified that adding it kills mutter, and removing it fixes everything again. Hopefully this post will get indexed for anyone else dim enough to do this as well...

[whoops - you need to remove nvidia-current and nvidia-settings as well]

---

