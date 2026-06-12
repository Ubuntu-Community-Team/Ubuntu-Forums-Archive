---
title: "What to BlackList to get Suspend Working"
date: 2012-08-13
forum: Hardware
---

### Post by beenny on 2012-08-13
Hello,

After upgrade to 12.04 my suspend has stopped working. All that happens is that the wifi disconnects for a second or two (as if it is going to suspend) and then it reconnects and all is back to normal. This is also the case when I try to hibernate manually.

Looking at my var/log/pm-suspend.log suggests to me it has something to do with the WIFI (posted below). From reading around I guess I need to blacklist something but I'm not quite sure what that would be and how exactly to do that.

I was wondering if anyone has any thoughts. I have a lenovo x220 with an SSD and kernel 3.2.0-27

Thanks,

bg

```

Thu Aug 9 22:23:33 PDT 2012: Inhibit found, will not perform suspend
Thu Aug 9 22:23:33 PDT 2012: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
```

---

### Post by beenny on 2012-08-16
One gratuitous bump...It would be great to know if anyone has any thoughts on this...

bg

---

### Post by Toz on 2012-08-16
The first log entry in your post is interesting:
> Thu Aug 9 22:23:33 PDT 2012: Inhibit found, will not perform suspend

However, it would be important to see what information comes before that. Can you post the full contents of your pm-suspend.log file? Try using pastebinit:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by beenny on 2012-08-16
Thanks for the reply - laptop is at home so will post tonight...

bg

---

### Post by KFoder on 2012-08-16
I had the same problem, but in 11.04, the cause was the USB 3.0 ports, the problem was solved in 11.10. 

I have not updated this machine to 12.04 yet so I do not know if the problem has been reintroduced.

Just my 2 cents ....

Kim

---

### Post by beenny on 2012-08-16
I also had the same problem with 11.04 (I think) with USB 3.0 ports that was solved by upgrading to Kernel 3.0...From the output this sounds different - but may not be...

---

### Post by beenny on 2012-08-16
So I think KFoder may have been right as the line before indicates the USB3

```
/etc/pm/sleep.d/disable_usb3 suspend suspend: Returned exit code 1.
```

TOZ, here is the link to the full log:

[HTML]http://paste.ubuntu.com/1151768/[/HTML]

(btw, thats a pretty nice function)...

Thank you for your thoughts,

bg

---

### Post by Toz on 2012-08-16
> Running hook /etc/pm/sleep.d/disable_usb3 suspend suspend:
FATAL: Module xhci_hcd is builtin

/etc/pm/sleep.d/disable_usb3 suspend suspend: Returned exit code 1.
Wed Aug  8 21:35:31 PDT 2012: Inhibit found, will not perform suspend

Can you post back the contents of /etc/pm/sleep.d/disable_usb3?

---

### Post by beenny on 2012-08-16
```

#/bin/bash

##unload module

case "$1" in
        suspend)
                /sbin/modprobe -r xhci_hcd
                ;;
        hibernate)
                /sbin/modprobe -r xhci_hcd
                ;;
        thaw)
                /sbin/modprobe xhci_hcd
                ;;
        resume)
                /sbin/modprobe -r xhci_hcd
                ;;
esac


```

---

### Post by Toz on 2012-08-16
What happens if you delete that file? Does suspend hang?

---

### Post by beenny on 2012-08-16
Thanks that seemed to solve it. I think that file may be a legacy of previous suspend issues...

---

### Post by Toz on 2012-08-16
Yeah - I believe that xhci_hcd is now built into the kernel and no longer a module.

---

