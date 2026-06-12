---
title: "[SOLVED] How do I STOP automounting of USB drives"
date: 2008-10-20
forum: General Help
---

### Post by Milliways on 2008-10-20
I have an external USB drive with 3 partitions.

How do I stop Ubuntu mounting the HFS+ partition?

---

### Post by shawnrgr on 2008-10-20
system>preferences>removable media, just turn off the mount when inserted or hotpluged

---

### Post by dcstar on 2008-10-21
> **Milliways said:**
> I have an external USB drive with 3 partitions.

How do I stop Ubuntu mounting the HFS+ partition?

Doubtful you can choose which partition not to automount, it's all or nothing.

---

### Post by kpkeerthi on 2008-10-21
Add an entry to /etc/fstab and set 'noauto' option, like so:
```

/dev/<device>   <mount-point>  <partition-type>   <other-options>,**[COLOR="Red"]noauto[/COLOR]**  0 0

```

You should Reboot for the changes to take effect.

See [this]("https://help.ubuntu.com/community/Fstab") link for help with FSTAB and HFS specific details

---

### Post by Milliways on 2008-10-22
> **shawnrgr said:**
> system>preferences>removable media, just turn off the mount when inserted or hotpluged

system>preferences>Removable Drives and Media
has entries for Cameras, PDA, Printers & Input Devices
but not drives

---

### Post by Milliways on 2008-10-22
> **kpkeerthi said:**
> Add an entry to /etc/fstab and set 'noauto' option, like so:
```

/dev/<device>   <mount-point>  <partition-type>   <other-options>,**[COLOR="Red"]noauto[/COLOR]**  0 0

```


/dev/sdb1   /media/Mac  hfsplus   noauto,ro  0 0

seems to do the trick.
I wanted to use UUID, but the partition does not seem to have this.

LABEL=XXXX works better than /dev/sdb1, which stopped USB keys from being mounted

I had read the fstab document, but did not realise this could be used

---

### Post by dcstar on 2008-10-22
> **Milliways said:**
> system>preferences>Removable Drives and Media
has entries for Cameras, PDA, Printers & Input Devices
but not drives

Same on my 8.04 system, I had to use the Configuration Editor and go into:

Apps-Nautilus-Preferences-media_automount to actually make mine automount after some naughty software disabled the feature.

---

