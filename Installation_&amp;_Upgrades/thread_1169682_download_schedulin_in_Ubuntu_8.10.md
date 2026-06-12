---
title: "download schedulin in Ubuntu 8.10"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by vpnm_87 on 2009-05-25
has anyone tried configurin downloader for X or anyother download manager to schedule the downloading and installation of all updates to start at a particular time?

coz i got 296 updates totallin a size 0f around 300MB...any help to schedule my download to start at a particular time?

---

### Post by kimda on 2009-05-25
Install the package gnome-schedule.
Start this as root via terminal sudo gnome-schedule
Then add recurring task. Set the time you want to run  and as command enter the following:  
sudo apt-get update && sudo apt-get -d upgrade 

Apply. Now it should download all the packages at a certain time.

---

### Post by vpnm_87 on 2009-05-25
thanks for d suggestion:-)
ll try that soon n post my progress:-)

---

