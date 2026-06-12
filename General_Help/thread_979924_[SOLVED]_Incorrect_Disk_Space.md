---
title: "[SOLVED] Incorrect Disk Space"
date: 2008-11-12
forum: General Help
---

### Post by Eric B on 2008-11-12
Hi. I think my partition is reporting the incorrect space.

I have a VMware image and a few other things in my /opt directory which is /dev/sda6. Its a minimal windows VM. All that is installed is office really. If I highlight all items and go to properties, it tells me that it is using 16.3 GB. It is a 27.7 GB partition. If I go into the /opt directory it status that are 0kb in the status bar in Nautilus. If I go into my System Monitor, it says I am using 16.3 GB. Where is the extra 10 GB going to?

---

### Post by Eric B on 2008-11-12
Okay, so there is a 10GB trash file in there. I did sudo rm -rf /.Trash-0 and its still there. I did gksudo nautilus and deleted it that way. Resolved.

---

