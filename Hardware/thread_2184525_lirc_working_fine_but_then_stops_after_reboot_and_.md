---
title: "lirc working fine but then stops after reboot and hangs"
date: 2013-10-29
forum: Hardware
---

### Post by sq2d3bipy0t2ou-paul on 2013-10-29
[FONT=microsoft sans serif][SIZE=2]Hello everyone

This is really driving me mad.  

I'm doing a fresh install of 12.04LTS and ```
sudo apt-get upgrade
``` everything.  At that point I install lirc and get it working fine.  I have the right hardware.conf and I can get all the key presses working fine using irw.  I'm using a Hauppauge PVR-150 card and the IR receiver/remote that comes with that.  Everything is fine.  All is good with the world.  I can issue ```
sudo service lirc restart
``` and it all works.  

Then randomly after a reboot everything stops.  ```
irw
``` simply says ```
connect: No such file or directory
```.  If I try to do anything with lirc, either sudo service lirc stop or sudo apt-get purge lirc then the session hangs.  Nothing.  Even reboots start to hang.  All I get is a message on the screen saying 'acpid: exiting Checking for running unattended-upgrades:'.  

If I check the dmesg log I see a bunch of messages along the lines of:

[/SIZE][/FONT]```
[FONT=Arial]Oct 28 22:13:32 borg kernel: [  240.756452] INFO: task lirc:1316 blocked for more than 120 seconds.[/FONT]
[FONT=Arial]Oct 28 22:13:32 borg kernel: [  240.756499] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.[/FONT]
[FONT=Arial]Oct 28 22:13:32 borg kernel: [  240.756547] lirc            D 00000000     0  1316      1 0x00000000 [/FONT]
```[FONT=Arial]

I have tried everything I can think of.  I've had remotes working fine on this machine before.  For about 4 years this was my MythTV backend.  I decided to upgrade a week ago and have been solidly stuck on this issue.  I would greatly welcome any help anyone has.  

Thanks, Paul[/FONT]

---

