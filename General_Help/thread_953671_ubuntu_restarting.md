---
title: "ubuntu restarting"
date: 2008-10-20
forum: General Help
---

### Post by xzibiz on 2008-10-20
I have a new installation of ubuntu 8.04.
But suddenly it's restarting.
I have looked in syslog and found something:
> 
Oct 20 07:55 xzibiz-desktop syslogd 1.5#lubuntu: restart.
Oct 20 07:55 xzibiz-desktop anacron: job `cron.daily` terminated
Oct 20 07:55 xzibiz-desktop exit (1 job run)

But i realy dont know why i'm getting this.
So i need some expert help.

---

### Post by Dr Small on 2008-10-20
Is there any lines in the log file above what you posted? Those lines are only telling me what happened after in begins to restart, not before it.

---

### Post by xzibiz on 2008-10-20
no, thats the first line in syslog file /var/log/syslog
but i found an older log, for yesterday:

> 
Oct 19 13:45:02 xzibiz-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct 19 13:45:02 xzibiz-desktop anacron[5854]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Oct 19 13:45:02 xzibiz-desktop anacron[5854]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Oct 19 13:56:49 xzibiz-desktop anacron[22655]: Anacron 2.3 started on 2008-10-19
Oct 19 13:56:49 xzibiz-desktop anacron[22655]: Will run job `cron.weekly' in 10 min.
Oct 19 13:56:49 xzibiz-desktop anacron[22655]: Will run job `cron.monthly' in 15 min.
Oct 19 13:56:49 xzibiz-desktop anacron[22655]: Jobs will be executed sequentially
Oct 19 13:57:05 xzibiz-desktop kernel: [ 1957.791658] audit(1224417425.013:3): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=22856 profile="/usr/sbin/cups$
Oct 19 13:57:42 xzibiz-desktop NetworkManager: <debug> [1224417462.060656] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDR___PX_810SA').
Oct 19 13:57:42 xzibiz-desktop hal_lpadmin: add
Oct 19 13:57:42 xzibiz-desktop hal_lpadmin: URIs: ['usb://Samsung/SCX-4200%20Series', 'hal:///org/freedesktop/Hal/devices/usb_device_4e8_341b_8T21BFEPA18606V__if1_printer_noserial']
Oct 19 13:57:42 xzibiz-desktop hal_lpadmin: HPLIP Fax URIs: None
Oct 19 13:57:42 xzibiz-desktop hal_lpadmin: Not adding printer: SCX-4200_Series already exists
Oct 19 13:57:42 xzibiz-desktop NetworkManager: <debug> [1224417462.366322] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4e8_341b_8T21BFEPA18606V__if1_printer_$
Oct 19 14:06:49 xzibiz-desktop anacron[22655]: Job `cron.weekly' started
Oct 19 14:06:49 xzibiz-desktop anacron[27121]: Updated timestamp for job `cron.weekly' to 2008-10-19
Oct 19 14:06:50 xzibiz-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct 19 14:06:50 xzibiz-desktop anacron[22655]: Job `cron.weekly' terminated
Oct 19 14:11:49 xzibiz-desktop anacron[22655]: Job `cron.monthly' started
Oct 19 14:11:49 xzibiz-desktop anacron[28123]: Updated timestamp for job `cron.monthly' to 2008-10-19
Oct 19 14:14:37 xzibiz-desktop anacron[22655]: Job `cron.monthly' terminated
Oct 19 14:14:37 xzibiz-desktop anacron[22655]: Normal exit (2 jobs run)


---

