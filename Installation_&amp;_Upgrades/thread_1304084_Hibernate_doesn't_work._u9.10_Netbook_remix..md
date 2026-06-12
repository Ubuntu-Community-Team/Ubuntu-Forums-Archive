---
title: "Hibernate doesn't work. u9.10 Netbook remix."
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by FrostCake on 2009-10-28
Hi Ubuntees,

I'm 2-days old to linux/Ubuntu, and I'm going to use it for my latex writing. 
No problems on setting up that part thanks to the help floating around the internet. 
However, this morning I tried hibernating for the first time, and it doesn't work. 

Computer specs are netbook Lenovo s10-2. 1gb ram.

My dual-boot winxp installation went like this:

USB-install of netbook remix 9.04, updated to 9.10.
Screen resolution didnt fit my 1024x600, so i manually installed desktop switcher 0.5.8.
Repartitioned my swap file to 2gb as i have 1gb ram, so now it looks like this:
\ext4 /     8gb
\swap       2gb
\ext4 /home 5gb

I tried hibernating after I got to here, and all it did was to show a black screen. 
The CPU lights were still running. No hibernate.

Here's what I tried so far.

(a) remapped the resume UUID to the new swapdrive UUID
```

sudo fdisk -l
cat /etc/fstab
blkid
/etc/initramfs-tools/conf.d/resume //set resume-id = swap-id
sudo update-initramfs -u
rebooted

```(b) checked that my hibernate settings were on. They were.
gconftool-2 -R /apps/gnome-power-manager
```

 /apps/gnome-power-manager/buttons:
  lid_battery = hibernate
  hibernate = hibernate
  suspend = suspend
  lid_ac = suspend
  power = interactive
 /apps/gnome-power-manager/keyboard:
 /apps/gnome-power-manager/actions:
  low_ups = hibernate
  sleep_type_ac = suspend
  event_when_closed_battery = true
  critical_ups = shutdown
  critical_battery = hibernate
  sleep_type_battery = suspend
 /apps/gnome-power-manager/ambient:
  enable = true
 /apps/gnome-power-manager/thresholds:
  time_low = 1200
  time_critical = 300
  percentage_low = 10
  time_action = 120
  percentage_critical = 3
  percentage_action = 2
 /apps/gnome-power-manager/ui:
  show_context_menu = true
  show_actions_in_menu = false
  icon_policy = always
  enable_sound = false
 /apps/gnome-power-manager/lowpower:
 /apps/gnome-power-manager/lock:
  hibernate = true
  suspend = true
  gnome_keyring_hibernate = true
  blank_screen = false
  use_screensaver_settings = true
  gnome_keyring_suspend = false
 /apps/gnome-power-manager/timeout:
  sleep_computer_battery = 1800
  sleep_computer_ac = 3600
  sleep_display_ac = 600
  sleep_display_battery = 300
  sleep_computer_ups = 0
  sleep_display_ups = 600
 /apps/gnome-power-manager/disks:
  spindown_timeout_ac = 600
  spindown_enable_ac = true
  spindown_timeout_battery = 60
  spindown_enable_battery = true
 /apps/gnome-power-manager/general:
  check_type_cpu = false
  network_sleep = false
  installed_schema = 3
  use_profile_time = true
  use_time_for_policy = false
  can_hibernate = true
  can_suspend = true
 /apps/gnome-power-manager/backlight:
  dpms_method_battery = off
  idle_dim_time = 10
  battery_reduce = true
  brightness_ac = 10
  idle_brightness = 30
  enable = true
  idle_dim_ac = true
  dpms_method_ac = off
  idle_dim_battery = true
  brightness_dim_battery = 50
 /apps/gnome-power-manager/statistics:
  graph_type = power
  show_events = true
  show_axis_labels = true
  smooth_data = true
  data_max_time = 21600
 /apps/gnome-power-manager/notify:
  discharging = true
  low_power = true
  sleep_failed = false
  sleep_failed_uri = 
  perhaps_recall = true
  low_capacity = true
  fully_charged = false

```Anything else i could try? Thanks!

---

### Post by FrostCake on 2009-10-30
Doesn't work on my desktop as well. u9.10

So is there's nothing we can do about this? 

Hibernate is bugged?

---

### Post by FrostCake on 2009-10-30
:rolleyes:

---

### Post by entropic_existence on 2009-10-30
Hibernate and suspend have always been a little hit or miss in Linux. On some machines it works great, in others not so much. I am curious does suspend work for you or are both suspend and hibernate broken?

Does your laptop have an SDHC card mounted by any chance?

---

### Post by FrostCake on 2009-10-30
Thanks entropic. Suspend works fine for me. And yes, it has a SDHC slot.

Hibernate doesn't work even when the SDHC is not mounted. 

Weird thing is that on Hibernate, the screen goes black, but the cpu/hdisk/batt lights are still lit after 5mins. Doesn't feel like the hibernate I know.

The moment I press a key/move a mouse, it goes right back on to the logon screen. :frown:

---

### Post by FrostCake on 2009-10-31
:rolleyes:

---

### Post by FrostCake on 2009-11-01
:???:

---

### Post by cmwatford on 2009-12-07
I also have this problem on my Dell Inspiron B-130 running 9.10. My suspend works fine but hibernate only makes my laptop look like it's trying to shutdown and then locks my screen. It prompts me for my password if I move my mouse. While this isn't a life stopping problem it its an annoyance.

---

### Post by Sapfeer on 2009-12-27
I have the similar problem on my Lenovo S10-2: Ubuntu suspends and hibernates normally, but wakes up after hibernation occasionally, sometime is does, sometime is doesn't.

---

