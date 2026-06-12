---
title: "usb flash players, sync, noatime and utf8 on vfat file-systems"
date: 2005-11-22
forum: Hardware &amp; Laptops
---

### Post by reztho on 2005-11-22
Hi,

      I have a mp3 flash player of 1 Gb, and I want to activate sync, noatime and use "iso8859-1" iocharset instead of "utf8" everytime I connect it to my computer. I investigated and realised this a job for HAL, so I edited my /etc/hal/fdi/policy/preferences.fdi file, uncommented the part of the 1 Gb removable devices, modified it a bit and added some lines:

<!--
  The following shows how to put sync and noatime on for devices smaller then 2Gb
  and off for device lager then that.
-->
  <device>
    <match key="block.is_volume" bool="true">
      <match key="volume.size" compare_lt="2000000000">
        <match key="@block.storage_device:storage.hotpluggable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
        <match key="@block.storage_device:storage.removable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
      </match>
      <match key="volume.size" compare_ge="2000000000">
        <match key="@block.storage_device:storage.hotpluggable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
        <match key="@block.storage_device:storage.removable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
      </match>
      <match key="volume.fstype" string="vfat">
      <merge key="volume.policy.mount_option.iocharset" type="string">iso8859-1</merge>
      </match>

    </match>
  </device>

(As you can see I consider "noatime" neccesary for every kind of removable device)

     But this doesn't work. Everytime I mount the mp3 flash player I don't see with the "mount" command it's using sync, noatime and iso8859-1. But here is something rare. I installed the hal-device-manager (it's a gnome application) and I see with that program than all my rules work, but as I said above, the device isn't mounted as I want. Investigating a bit more I think it's a question of a program called "pmount", but i don't know who invoke "pmount" in this puzzle.

    Here is the output of the "mount" command:
/dev/sda1 on /media/usbdisk type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)

     So thanks in advance.

( I'm a kubuntu 5.10 user, so I opened a thread with the same contents too on kubuntuforums: [http://kubuntuforums.net/index.php?topic=1799.0](http://kubuntuforums.net/index.php?topic=1799.0) )

---

### Post by reztho on 2005-11-23
Reading about what happens with vfat and sync, now I prefer to not put the "sync" flag for any removable device, but at least I want to activate "noatime". Does someone know about?

---

### Post by xtifr on 2007-11-23
Well, if it's a problem in pmount, it's shared by gnome-mount, because I'm getting similar results (no "noatime" on my flash drive).  And, like you, I can see that the policy option is getting properly set in the hardware device list.  It just gets ignored when the device is actually mounted.  On my other system, which runs Debian, I don't use automounting (or gnome or kde), and I have an entry in fstab for the flash drive, and *that* works properly.  I'm tempted to go the same route with my Ubuntu system, but I'd prefer to find a better solution.

After reading a little more: according to the gnome-mount man page, both gnome-mount and HAL itself will simply defer to /etc/fstab if there's an entry there for the device. So creating an fstab entry might be enough to meet your needs (noatime for all removable devices), but *I'd* still like to find a way to make the system work as advertised.

---

