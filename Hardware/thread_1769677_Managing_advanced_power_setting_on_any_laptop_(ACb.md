---
title: "Managing advanced power setting on any laptop (AC/battery)"
date: 2011-05-28
forum: Hardware
---

### Post by danakim on 2011-05-28
Hi all,

I have been using Ubuntu 10.10 on my Acer 3810T for a while now and have been loving it.

I was looking to customize a bit more what happens to my power settings when the laptop switched from battery to AC and vice-versa. For example the file /proc/sys/vm/dirty_writeback_centisecs:

When the laptop is running on AC Ubuntu automatically sets that file to have 500 centisecs in it and on battery it switches to 60000. I would like to customize these for my own usage (I would like it to have 1500 on battery mode) and also add some more settings when switching between states - like tunings some hdparm and iwconfig settings. I have tried setting some udev rules for detecting battery state - which worked - but were overwritten by the OS.

Could you please tell me where these settings (or power state rules) are kept and how to modify/add to them? 

Thank you!

---

### Post by danakim on 2011-05-29
Bump!

---

### Post by Zevaka on 2011-05-29
```
sudo gedit /etc/acpi/power.sh
```
adding (in the beginning) stuff like
```
if on_ac_power; then
echo 6000 > /proc/sys/vm/dirty_writeback_centisecs
else
echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
fi
```

also you might need to make it executable 
```
sudo chmod +x /etc/acpi/power.sh
```

---

### Post by danakim on 2011-05-30
Thank you very much Zevaka!

Although it seems that in that file I already have this:

pm-powersave $*

But that's fine, because that command seems to be looking for scripts in /etc/pm/power.d to run when the power state changes. 

So I will just put all my scrips there.

---

