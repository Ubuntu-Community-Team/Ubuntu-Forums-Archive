---
title: "Alsa not configured right or Maybe installed...?"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by cokehabit on 2006-06-17
ALSA was working perfectly before but now only OSS works. ALSA seems to have uninstalled itself but alsa-driver isn't in the repos. Also no other ALSA related programs seem to bring it in as a dep.

/etc/init.d has alsa-utils but no alsa and when i try to open alsamixer i get 
```
alsamixer: function snd_ctl_open failed for default: No such device
```

If i try to test it in the Multimedia Systems Selector i get:
```
ALSA - Advanced Linux Sound Architecture: Could not open resource for writing.
```

Why does the driver package not seem to be in the repos? Neither a search for emu10k1 nor alsa reveals the driver :mad:

---

