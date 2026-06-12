---
title: "kernel problems with Ubuntu 22.04.3"
date: 2023-09-11
forum: Hardware
---

### Post by jdefed on 2023-09-11
Hi,

I have a pc with a Ryzen 3 pro 2200ge processor. Running Ubuntu 22.04.3lts with normal updates. The system will not run(random lockups) on any kernel in version 6xxxx. It will run in kernel 5.19.0-50. There are no crash logs in var/crash folder. I think its running generic kernel.(hardinfo says generic). Any help as to where to start looking. The system is just used for internet with nothing special added, running Brave browser hardware acceleration off.

Thanks
Jim

---

### Post by TheFu on 2023-09-11
I'd check the system log files.  Web search for "linux system logs" to find where they are, how to view them and more importantly, how to search inside for errors/warnings.  [https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#1-overview](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#1-overview) and [https://www.howtogeek.com/117878/how-to-view-write-to-system-log-files-on-ubuntu/](https://www.howtogeek.com/117878/how-to-view-write-to-system-log-files-on-ubuntu/) are what what I found from reputable sources, but really for the last 30 yrs, the logs in Linux have all be in /var/log/ somewhere.

There's a log tool, **journalctl**, since systemd replace the prior init system. journalctl is very powerful for filtering.  Might be worth learning to use it, since Debian 12 has stopped making extra log files (guess they figure the transition period to systemd/journald has been long enough).  I'm not a fan of systemd. It is solving issues that I never had, but I appreciate journald + journalctl. For log management and searching and filters, **journalctl completely rocks.** It is a real improvement for all of us. [https://www.howtogeek.com/499623/how-to-use-journalctl-to-read-linux-system-logs/](https://www.howtogeek.com/499623/how-to-use-journalctl-to-read-linux-system-logs/) is a quick overview of the tool. Generally, we don't need to know too much.

Obviously, if you don't have a specific reason to use 6.x kernels, don't use them. Keep the older line around.

It would be helpful if you could reproduce the problem 100% of the time. That way, other people could try it, see the issue, and help.

---

