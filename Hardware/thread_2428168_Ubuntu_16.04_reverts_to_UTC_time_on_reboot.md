---
title: "Ubuntu 16.04 reverts to UTC time on reboot"
date: 2019-09-30
forum: Hardware
---

### Post by lukon on 2019-09-30
Either my 16.04 reverts to UTC time on reboot, or my attempts to set it to RTC time fail. I don’t know which.

I’m trying to fix the classic problem on my dual boot computer where Windows 7 gets it’s clock messed up after switching from Ubuntu to Windows 7.

I used to be able to fix this problem with the “timedatectl set-local-rtc 1 --adjust-system-clock” command. But that no longer works. Something has changed.

When I try it, I get a response: “Failed to set local RTC: Access denied.” -- even when using sudo and entering my password.

Yet when I check it using the “timedatectl” command, I see: “RTC in local TZ: yes” - whereas before I gave the command to change it, it said “no”. So it says “access denied” yet tells me it made the change anyway, which is inconsistent.

But after rebooting, “RTC in local TZ: no” has returned.

I suspect it did change to RTC time, but only for the current session. And that changing it for all future sessions requires some extra steps involving becoming a super-duper-king-of-all-asministrators security clearance user.

---

### Post by TheFu on 2019-09-30
Unix systems want to use UTC internally and display whatever TZ you request based on the TZ environment variable.
There's a way to get Windows to use UTC, but I don't know how.  That's the easiest, long-term, fix.  
How to set the TZ is in the *Ubuntu Server Guide* or *Ubuntu Desktop Guide*.  Both are easily found with a web search based on the release being used.

My ~/.bashrc has this line:
```
export TZ='America/New_York'
```
Make that match whatever you need.
[https://help.ubuntu.com/](https://help.ubuntu.com/) Has links to both the server and desktop guide for current, supported, releases.

[https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/](https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/) has a few options, including how to get Windows to use UTC.

I've had issues with Windows keeping correct time since 1994. My solution won't help you. Sorry.

---

### Post by lukon on 2019-10-05
Bump. This problem is not yet solved.

Anyone else know what to do?

---

### Post by #&amp;thj^% on 2019-10-05
You did not say if you used this:
_EDIT: I just read your first post, Ah I see now, you may still be using NTP and that will need to be disabled:_
```

sudo update-rc.d -f ntp remove
```
now set it :
```
sysctl start systemd-timesyncd.service
```
```
timedatectl set-local-rtc 1
```

To check:
```

timedatectl | grep local
```

---

### Post by Yellow Pasque on 2019-10-05
It's better to make Windows use UTC time: [https://wiki.archlinux.org/index.php/System_time#UTC_in_Windows](https://wiki.archlinux.org/index.php/System_time#UTC_in_Windows)

---

