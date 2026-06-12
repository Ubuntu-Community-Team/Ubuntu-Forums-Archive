---
title: "How do I make an autoladed module autload with parameters?"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2006-11-02
I need to pass an option to my soundcard module, but it is autoladed (by hotplug?). How can I add the options to this module. The soundcard module is snd-hda-intel.

---

### Post by deepwave on 2006-11-02
Try adding a line to /etc/modules
snd-hda-intel -parameters-go-here

---

