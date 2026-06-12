---
title: "vlc"
date: 2010-06-26
forum: Hardware
---

### Post by hirendhanani on 2010-06-26
i dnt have the setup file of vlc for ubuntu 9.04, so can u tell me 4m where i found this file and how to install in ubuntu...thnx...

---

### Post by jocko on 2010-06-26
Open up synaptic and search for it.

---

### Post by efflandt on 2010-06-26
In Synaptic if you install **ubuntu-restricted-extras** that installs most codecs and things that you need for multimedia, and read the description for that package for the web link you also need to follow to enable playing DVD.  However, I don't think I could ever get the default Movie Player (Totem) to work properly for DVD in 9.04 or 9.10.  With default gstreamer packages (from restricted extras) DVD menus worked, but I had no sound.  Or if a different mutually exclusive gstreamer package was installed, sound worked, but I could not access DVD menus.

But when I installed **vlc** pakage using Synaptic, that installed everything needed for that, and vlc worked fine in any Ubuntu version.

After doing the above in 10.04, both Movie Player (Totem) and vlc work fine, but vlc has more features.

---

