---
title: "upgrade killed my 3 monitor setup :("
date: 2012-06-25
forum: Hardware
---

### Post by andrewhamming on 2012-06-25
Greetings all,

I was running Ubuntu 11.10 with Xfce/gnome/LXDE. I have a Z68 mobo with intel onboard graphics and an old radeon x300 graphics card(using soley for extra display ports)

I had it setup with 3 monitors all working nicely.
There was one big display that i could drag mouse around, but windows would only go either on 1 monitor plugged into onboard graphics or move between 2 monitors plugged into radeon card.

My hd is on the blink so i got new one and installed fresh 12.04 Xubuntu.

My question is where do i look for conf files to setup screens as I had them before.

My main display (onboard) is working but radeon is not :(
When i log in the 2 radeon monitors briefly display the logon screen then turn off again.

I can still access old hdd to lookup configuration but I have no idea where to start looking.

Any tips work be great,

TY in advance.

Hammo

Its still picking up displays, here a copy of my .config/xfce4/xfconf/xfce-perchannel-xml/displays.xml file 

<channel name="displays" version="1.0">
<property name="HDMI1" type="string" value="ACI 22"">
<property name="Active" type="bool" value="true"/>
<property name="Resolution" type="string" value="1680x1050"/>
<property name="RefreshRate" type="double" value="59.851764"/>
<property name="Rotation" type="int" value="0"/>
<property name="Reflection" type="string" value="0"/>
<property name="Primary" type="bool" value="false"/>
<property name="Position" type="empty">
<property name="X" type="int" value="0"/>
<property name="Y" type="int" value="0"/>
</property>
<property name="VGA-0" type="string" value="ViewSonic 19"">
<property name="Active" type="bool" value="true"/>
<property name="Resolution" type="string" value="1440x900"/>
<property name="RefreshRate" type="double" value="59.887445"/>
<property name="Rotation" type="int" value="0"/>
<property name="Reflection" type="string" value="0"/>
<property name="Primary" type="bool" value="false"/>
<property name="Position" type="empty">
<property name="X" type="int" value="0"/>
<property name="Y" type="int" value="0"/>
</property>
</property>
<property name="DVI-0" type="string" value="OTC 19"">
<property name="Active" type="bool" value="true"/>
<property name="Resolution" type="string" value="1280x1024"/>
<property name="RefreshRate" type="double" value="60.064363"/>
<property name="Rotation" type="int" value="0"/>
<property name="Reflection" type="string" value="0"/>
<property name="Primary" type="bool" value="false"/>
<property name="Position" type="empty">
<property name="X" type="int" value="0"/>
<property name="Y" type="int" value="0"/>
</property>
</property>
</property>
</channel>

---

### Post by andrewhamming on 2012-06-26
If I boot from a Ubuntu off a usb, what are;

1. the commands to copy my old hdd partition onto new hdd partition so i can just upgrade from 11.10 to 12.04?

2. whats the command to upgrade grub once i have done the above?

New hdd has win 7 on one partition, which i would prefer not to have to reinstall, plus partition for linux and swap.

sda3 = new harddrive linux partition

sdf2 = old harddrive linux partition

so looking to copy sdf2 over sda3. Also sda3 is bigger then sdf2

Cheers

---

