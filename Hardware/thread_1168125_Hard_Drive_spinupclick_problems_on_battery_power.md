---
title: "Hard Drive spinup/click problems on battery power"
date: 2009-05-23
forum: Hardware
---

### Post by jon.reeve on 2009-05-23
I've recently been getting issues with my hd making frightful noises every minute or so on battery power. I suppose the hd must be going to sleep a little too often. This can't be good for the drive, and it creates a 1-2 second delay whenever I do something, while it waits for the HD to spin up. I've tried editing /etc/hdparm.conf and adding a line about power management: 

```
command_line {
hdparm -B 192 /dev/sda
}

```

but that doesn't seem to change anything. This problem is annoying and dangerous, since it happens every minute or so. 

This problem doesn't occur at all on AC power. 

Any ideas about what might be causing this or how to troubleshoot it?

---

