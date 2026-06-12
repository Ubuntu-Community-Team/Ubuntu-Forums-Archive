---
title: "How to prevent auto-mount of partitions"
date: 2008-11-21
forum: Hardware
---

### Post by frank.zappa on 2008-11-21
Here is my fstab:
```
proc            /proc           proc    defaults        0       0
/dev/sda1	/mnt/Acer	ntfs-3g	user,noauto	0	0
/dev/sda2	/mnt/XP	ntfs-3g	user,noauto	0	0
/dev/sda3       /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
But for some reason, when I log into Debian, Gnome auto-mounts the partitions for me, even when I have specified 'noauto' in the fstab.

A little background info: when I created the mountpoints, I had to do a 'sudo chmod 777 /mnt/Acer' and the same for XP because when I tried to mount the paritions from the GUI, it said I did not have the privileges. I also had to add myself to the 'disk' group before I could access them through Gnome.

Any ideas?

---

### Post by pelle.k on 2008-11-21
Yeah. Unless debian has patched gnome-volume-manager to respect the automount_enabled_hint, you can't do anything about it.
This is enabled by default since gnome 2.22, but i guess debian ships 2.16 (etch) or 2.20 (lenny)?

Either way, this is the patch; [http://patches.ubuntu.com/by-release/extracted/ubuntu/g/gnome-volume-manager/2.17.0-2ubuntu2/02_honour_automount_enabled_hint.patch](http://patches.ubuntu.com/by-release/extracted/ubuntu/g/gnome-volume-manager/2.17.0-2ubuntu2/02_honour_automount_enabled_hint.patch)
Also, if this patch IS applied, you'd put this in /etc/hal/fdi/policy/preferences.fdi
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->

  <device>

    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>

  </device>

</deviceinfo>
```
If i remember correctly
That is, you don't set this up in /etc/fstab.

---

### Post by frank.zappa on 2008-11-21
This is what my preferences.fdi looks like right now:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
<!--
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->
</deviceinfo>

``` 
Which is the same as what you posted. Are you saying I have to add parameters to this file?

Edit: nevermind, I have to uncomment it, don't I?

---

### Post by frank.zappa on 2008-11-21
Thanks a lot, I uncommented the bit that you posted and it works. Well, the first time I restarted, it hung at 'setting up system clock', so I did a cold boot and it worked.

---

### Post by pelle.k on 2008-11-22
Hey, glad you got it working! :)

---

