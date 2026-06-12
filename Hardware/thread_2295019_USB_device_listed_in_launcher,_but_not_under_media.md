---
title: "USB device listed in launcher, but not under /media/"
date: 2015-09-15
forum: Hardware
---

### Post by cyberbemon on 2015-09-15
I have 2 USB docks, to which I plug in 2 sensors, once the sensors are plugged in they act as a USB storage device. I'm having a strange issue, where one of the sensor is detected immediately after plugging in, I can go to `/media/username/` and if I do an `ls` I can see the device listed there and I can `cd` into it. 

however when I plug in the second device, it doesn't show up there, unless I go to `file manager` and click the sensor name under `devices`, 
[IMG]http://i.imgur.com/1mZJtU0.png[/IMG]

if I do that and `ls` in `/media/username/` the sensor shows up and I can `cd` into it. 

Both sensors show up on the launcher/taskbar. Both devices are listed under `lsusb`

I'm not sure what's causing the issue.

---

### Post by efflandt on 2015-09-15
It could be because they both use the same partition (volume) name "2.0 GB Volume". Normally USB mass storage is automounted under your username directory in /media as their volume name, or if none, by UUID. But since both have the same volume name, you cannot have 2 directories with the same exact name. Is there some way to change the name that one of them identifies itself as?

---

### Post by cyberbemon on 2015-09-17
> **efflandt said:**
> It could be because they both use the same partition (volume) name "2.0 GB Volume". Normally USB mass storage is automounted under your username directory in /media as their volume name, or if none, by UUID. But since both have the same volume name, you cannot have 2 directories with the same exact name. Is there some way to change the name that one of them identifies itself as?

So the devices are showing up as "2.0 GB Volume" in the file manager, one of them shows up under "/media/username/UUID" the other one shows up after I've clicked on the GUI. 

I used Gparted to look at both the devices, none of them had a volume label (see pics below) 
[IMG]http://i.imgur.com/oSDFvfF.png[/IMG]


And here is the second Device

[IMG]http://i.imgur.com/ZttvObZ.png[/IMG]


I used GParted and changed the labels to their corresponding UUID, but I'm still getting the same issue, only one of them is detected when I plugged in, the other still requires me to go into File manager and click on it, This is how they are showing up now. 

[IMG]http://i.imgur.com/TBTOGnT.png[/IMG]

Notice how the eject icon is only next to one of them, it doesn't show up on the next one, unless I click on it. I'm at a loss right now, not sure what to do next!

---

