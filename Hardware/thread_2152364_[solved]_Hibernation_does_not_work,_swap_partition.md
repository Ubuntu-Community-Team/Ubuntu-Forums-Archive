---
title: "[solved] Hibernation does not work, swap partition problem?"
date: 2013-06-07
forum: Hardware
---

### Post by cloutz on 2013-06-07
Hi, 
Everything worked until I decided to change my partitions.

Now when I click Hibernate option it shut down, but when resuming it just start up, _flushing all the informations_.
Can you help me??

Following I explain what I did...

I config partitions like this:

[ATTACH=CONFIG]243609[/ATTACH]
Changed **/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla** like this:
```
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

```

Nothing worked, and I noticed that swap partition (sda5) was not mounted by default.
 So I configured it to mount at boot time adding last line in** /etc/fstab** like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=772c3bd4-5d07-484e-9fa6-ea8a0f03aba2 /               ext4    errors=remoun
# swap was on /dev/sda4 during installation
#UUID=76f394db-0a8d-4dc1-ab92-840f991c5771 none            swap    sw         
/dev/sda5                                 none            swap    sw          

```

Now swap partition is mounted at every startup/resume from Hibernation, but maybe it was cleared, flushed, because Hibernation results as a clean startup (no windows was kept ecc..).

Can you help me??


Thank you, 
sorry for my bad english

---

### Post by ajgreeny on 2013-06-07
Not sure how much it matters, but in my fstab there are two zeros separated by spaces at the end of the swap line
```
# swap was on /dev/sda3 during installation
UUID=0707fdc8-1299-4c11-9f93-8158d3c313d0 none            swap    sw              0       0
```
It would also be netter to keep the UUID rather than /dev/sda5 for your swap, so let's see the output of ```
sudo blkid -c /dev/null
```and we can sort out the line that way.

---

### Post by ahallubuntu on 2013-06-07
~

---

### Post by cloutz on 2013-06-07
Thanks!!

---

