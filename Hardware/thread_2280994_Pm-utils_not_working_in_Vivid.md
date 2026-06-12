---
title: "Pm-utils not working in Vivid?"
date: 2015-06-03
forum: Hardware
---

### Post by oscar-tiderman on 2015-06-03
Hi, I noticed after installing Vivid that none of my pm scripts in /etc/pm/power.d/ wast triggered anymore when connecting or disconnecting my charger. I also had a problem with WiFi that had poor connectivity, so I tried disabling power management on it with a sudo touch /etc/pm/power.d/wireless but that has no effect whatsoever, power management is still switchted on on every boot for wlan0. What is going on? Has power management completely changed with Vivid? If so, where are the updated instructions? Or is it something that only affects my laptop? Any feedback on this is appreciated.

---

### Post by oscar-tiderman on 2015-06-05
Wrong section? Please move it to the appropriate section

---

### Post by oscar-tiderman on 2015-07-04
This is a bug caused by the switch to systemd, details here: [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1461386]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/1461386")

---

