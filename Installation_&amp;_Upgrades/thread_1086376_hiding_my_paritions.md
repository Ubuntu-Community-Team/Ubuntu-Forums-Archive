---
title: "hiding my paritions"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by cowboyup6983 on 2009-03-04
i installed ubuntu just now, and its a dual boot with vista and ubuntu. i have 4 partions in vista and one with ubuntu. when you go to the "places" tab and it gives a drop down list of all my drives, can i hid all my vista partitions and only show my ubuntu partition.

---

### Post by lha on 2009-03-05
Create the file /etc/hal/fdi/policy/hide_vista_partitions.fdi with the following contents:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

<device>
  <match key="volume.uuid" string = "[COLOR="Blue"]UUID_HERE[/COLOR]">
    <merge key="volume.ignore" type="bool">true</merge>
  </match>
</device>

<device>
  <match key="volume.uuid" string = "[COLOR="Blue"]ANOTHER_UUID_HERE[/COLOR]">
    <merge key="volume.ignore" type="bool">true</merge>
  </match>
</device>


</deviceinfo>

```

The blue bits above need to be changed to the uuids' of the partitions you want to hide; run
```
ls -l /dev/disk/by-uuid
```
to find out what they are. Finally, restart hal with
```
sudo /etc/init.d/hal restart
```

---

