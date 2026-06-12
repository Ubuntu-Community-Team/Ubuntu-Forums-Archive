---
title: "Need help  with setting quotas for each user pls"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by husskii on 2009-07-26
Hi I just bought a new server and set 4user accounts on it,
I want to set quotas for each of my user, so they have there own allocated HDD space. I found a command I can use thru putty but Im not sure if it will delete wats on the currently HDD, & Im afraid to use it and ruin everything I have setup in the last 48hrs...

Im using Ubuntu 8.04 (hardy) any advice would be most appreciated. 

The commands I found were sudo edquota to edite the quota and sudo setquota to create the quota

if I use the commands will I be fine or will it delete wats the apps I have currently installed etc...

thanks in advance :)

---

### Post by husskii on 2009-12-05
all solved, i learnt of a new tool called webmin lol..
no setting hdd quotas hasnt been easier...

for anyone else with the same problem, just do the following.

1: install webmin
wget [http://prdownloads.sourceforge.net/w..._1.490_all.deb](http://prdownloads.sourceforge.net/w..._1.490_all.deb)

2: sudo dpkg -i webmin_1.490_all.deb

3: apt-get install quota quotatool

4: open /etc/fstab and find where it mounts /home

5: then nano /etc/fstab

6: now you see /dev/md7 /home ext3 line, change that line so it looks like this
/dev/md7 /home ext3 defaults,usrquota,grpquota 1 2 /dev/sda5 swap swap defaults 0 0 [preserve the spaces] then save.

7: now go into /home & type, cd /home

8: in your home directory, type, touch quota.user quota.group

9: now type in, chmod 600 quota.*

10: then type in, mount -o remount /home

11: now log into webmin & search 'quota' you should see a result called "Disk Quotas"

12: click on it and press enable quotas on /home

13: now u can create hdd quotas for each user...

---

