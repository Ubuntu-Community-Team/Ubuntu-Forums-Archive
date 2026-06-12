---
title: "Hardy hanging up on first boot"
date: 2008-08-04
forum: General Help
---

### Post by Fstop on 2008-08-04
I'm having an issue when booting up. The first time I boot up, just after the kernel says it's loaded/ing, the screen goes black. An error message pops up at the top but it's too quick to read. Once I reset my machine, it boots up fine. It does this every time. I checked /var/log/messages but don't really understand what all is going on in there. 

Any help would be appreciated!

---

### Post by Taxman415a on 2008-08-04
If you keep track of the times when you boot you should be able to find the error message that flashes by too fast to see. Except try looking in /var/log/syslog and in /var/log/dmesg if you don't find the error in syslog. You should be able to tell the timing of when the boot process starts over and look for the error just before that.

---

### Post by Fstop on 2008-08-28
> **Taxman415a said:**
> If you keep track of the times when you boot you should be able to find the error message that flashes by too fast to see. Except try looking in /var/log/syslog and in /var/log/dmesg if you don't find the error in syslog. You should be able to tell the timing of when the boot process starts over and look for the error just before that.

here is the message in /var/log/syslog:

```

Aug 28 15:11:40 uSempron NetworkManager: <info>  Updating allowed wireless network lists. 
Aug 28 15:11:40 uSempron NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Aug 28 15:11:42 uSempron kernel: [   87.071598] UDF-fs: No VRS found

```

i couldn't find anything specific in the other log files. these are the last entries before i rebooted.

---

### Post by Fstop on 2008-09-08
I'm still lost with this problem. I've attached my syslog and dmesg files. If anyone can see something wrong, I'd love to get this working properly. :)

---

### Post by Fstop on 2008-10-12
bump!

i've noticed that it's hanging before it gets to the nvidia logo. maybe it's an issue with my resolution or something? i'm using standard res(1920x1200) on a 24" widescreen.

---

