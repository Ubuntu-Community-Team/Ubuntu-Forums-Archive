---
title: "OS gets stuck shuting down"
date: 2008-07-25
forum: General Help
---

### Post by Spaceman9 on 2008-07-25
I don't know if it's due to a kernel update or because I've had to reboot a frozen Ubuntu a few times in the last few weeks, but for a while Ubuntu doesn't reboot/shutdown right. More than half the time it gets to 

sending all processes the KILL signal

And then a black screen with with print that's all about the NetworkManger. Here's the last line of print it puts up

NetworkManger: nm_dbus_signal_device_status_change: assertion 'cb_data->dbus_connection' failed

Then I have to do a warm reboot with the magic warm reboot button. When it boots up and the usplash screen comes up it says

unclean shutdown checking drives
/dev/sdb6

and it cleans up the partition and goes to the login screen. 

Is there anyway to fix the shutdown problem? Thankx for any help.

---

### Post by Sef on 2008-07-25
> I don't know if it's due to a kernel update or because I've had to reboot a frozen Ubuntu a few times in the last few weeks, but for a while Ubuntu doesn't reboot/shutdown right. More than half the time it gets to

I had a somewhat similar problem with the -19 kernel.  I would just press ctrl, alt, backspace and then it would shutdown.  Once I updated to -20, the problem disappeared.

What kernel are you running?  Applications > Accessories > Terminal > type in: ```
uname -r
```

---

### Post by Spaceman9 on 2008-07-26
Thankx for the help Sef. I'm using kernel 2.6.24-19-rt. I installed Ubuntu Studio into Ubuntu 8.04 last month so I use the rt kernel.

---

### Post by Spaceman9 on 2008-07-26
I don't believe this. I tried booting with the Ubuntu 8.04 kernel 2.6.24-18-generic and there were no problems rebooting. Then I tried booting up with the Ubuntu 8.04.1 kernel 2.6.24-19-rt and there were no problems rebooting. Just to make sure I wasn't seeing things I booted up with the Ubuntu 8.04.1 kernel 2.6.24-19-rt again and again there were no problems rebooting.

May be it was just a glitch or an anomaly or may be the little penguin in my computer had a 24 hour virus...I don't know. If I have the problem again I'll post it in this thread.

---

### Post by Spaceman9 on 2008-07-26
It happened again with the Ubuntu 8.04.1 kernel 2.6.24-19-rt so I changed to the Ubuntu 8.04 kernel 2.6.24-18-generic as my default bootup kernel and it's not happening anymore. It must be a problem with the Ubuntu 8.04.1 kernel 2.6.24-19-rt.

---

### Post by Krydahl on 2008-07-26
You might want to read this:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/138691](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/138691)

---

### Post by Spaceman9 on 2008-07-26
> **Krydahl said:**
> You might want to read this:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/138691](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/138691)

Thank you very much for taking the time to find this bug report. I filed a bug report this week that turned out to not be a bug but a problem with the new Gnome file system and not all the Gnome apps have been updated yet to work with it.

But Ubuntu seems to have a lot of bugs including one that keeps it from playing a shut down sound. Something happened to my install and it can't play startup sounds now either. So I used StartUp-Manger to add a startup sound. 

Just between you and me if it wasn't for the forums here I'd use a different distro.

---

### Post by Krydahl on 2008-07-26
I knew about the bug already. I have a NAS box mounted with CIFS which is what led me to it - not found a solution yet, but it seems to do no real harm. Mine at least closes down, it just spews out a few error messages while it does.

---

