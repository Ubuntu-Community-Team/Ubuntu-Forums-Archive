---
title: "ThinkPad Press-To-Select persistence"
date: 2009-05-18
forum: Hardware
---

### Post by fisherm on 2009-05-18
I found the command:

echo -n 1 | sudo tee /sys/devices/platform/i8042/serio1/press_to_select

   This command makes my trackpoint work as desired as "Press to Select". There are two problems though...(A) The change is not persistent through a reboot cycle, but it is persistent through login/logout cycles. (B) It prompts for a password when run. I understand why it must ask for a password, but I want to put the command somewhere to be run automatically, and therefore need it to be run without a password prompt.

   Can anyone enlighten me as to where I can put this command to be run at boot time so it will be in effect from GDM to infinity, and be persistent through reboots. Any help would be greatly appreciated.

---

### Post by fisherm on 2009-05-20
Figured it out...if anybody else wants to know.

First, open as root: /etc/gdm/Init/Default

Just above the final "exit 0", I added :
echo -n 1 | tee /sys/devices/platform/i8042/serio1/press_to_select

Works for me on an X31.

---

### Post by camper365 on 2009-06-13
I've tried that but it doesn't work for me on a thinkpad t43.

---

### Post by fisherm on 2009-06-14
Did you simply copy and paste what I had? If so, you may try searching for the file named "press_to_select" and making sure that is is located in the same place on your machine as it is on mine...Places > Search for files, and then type "press_to_select"...and Look In = /sys. Hope this helps.

---

### Post by camper365 on 2009-06-14
I got it to work now.

I added these to /etc/gdm/Init/Default

```
echo -n 128 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
echo -n 0 > /sys/devices/platform/i8042/serio1/serio2/inertia
echo -n 95 > /sys/devices/platform/i8042/serio1/serio2/speed
echo -n 10 > /sys/devices/platform/i8042/serio1/serio2/reach
echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/draghys
echo -n 20 > /sys/devices/platform/i8042/serio1/serio2/mindrag
echo -n 8 > /sys/devices/platform/i8042/serio1/serio2/thresh
echo -n 255 > /sys/devices/platform/i8042/serio1/serio2/upthresh
echo -n 57 > /sys/devices/platform/i8042/serio1/serio2/ztime
echo -n 141 > /sys/devices/platform/i8042/serio1/serio2/jenks
echo -n 1 > /sys/devices/platform/i8042/serio1/serio2/press_to_select
echo -n 0 > /sys/devices/platform/i8042/serio1/serio2/skipback

```

I think there was something about the serio1/serio2 that had to be put in.

---

### Post by camper365 on 2009-06-14
However, when I do that, it doesn't work when I resume from standby.

---

### Post by camper365 on 2009-07-09
I wrote a script that works when resuming from standby also. The only problem is that it has to be run manually after resuming from standby. I haven't extensively tested it, so be careful when using it. Nothing bad should happen, as there is no mkdir in there, however, the second line ("cd /sys/devices/platform/i8042/serio1/serio*") might not work in every situation because of the *.

```

# !/bin/sh

cd /sys/devices/platform/i8042/serio1/serio*

echo -n 128 > ./sensitivity
echo -n 0 > ./inertia
echo -n 95 > ./speed
echo -n 10 > ./reach
echo -n 255 > ./draghys
echo -n 20 > ./mindrag
echo -n 8 > ./thresh
echo -n 255 > ./upthresh
echo -n 57 > ./ztime
echo -n 141 > ./jenks
echo -n 1 > ./press_to_select
echo -n 0 > ./skipback

exit 0

```

---

