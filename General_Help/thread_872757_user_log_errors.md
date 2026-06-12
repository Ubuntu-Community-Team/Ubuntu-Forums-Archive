---
title: "user log errors"
date: 2008-07-28
forum: General Help
---

### Post by justborn on 2008-07-28
```
Jul 12 21:39:08 appy-desktop bonobo-activation-server (appy-6401): could not associate with desktop session: Failed to connect to socket /tmp/dbus-fKPN4qlq64: Connection refused
Jul 13 14:46:29 appy-desktop dhcdbd: Started up.
Jul 13 14:50:28 appy-desktop dhcdbd: Started up.
Jul 13 14:52:03 appy-desktop bonobo-activation-server (appy-5847): could not associate with desktop session: Failed to connect to socket /tmp/dbus-PgSLSp1rus: Connection refused
Jul 13 14:52:04 appy-desktop pulseaudio[5863]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jul 13 14:52:04 appy-desktop pulseaudio[5863]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jul 13 14:52:04 appy-desktop pulseaudio[5863]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Jul 13 14:52:04 appy-desktop pulseaudio[5863]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Jul 13 14:55:34 appy-desktop aide-cron-daily: terminated because lock /var/run/aide/cron.daily.lock could not be obtaiend.
Jul 13 18:55:19 appy-desktop gnome-power-manager: (appy) Resuming computer
Jul 13 22:09:47 appy-desktop gnome-power-manager: (appy) Resuming computer
Jul 28 19:05:06 appy-desktop gnome-power-manager: (appy) Resuming computer
Jul 28 19:07:34 appy-desktop dhcdbd: Started up.
Jul 28 19:08:09 appy-desktop bonobo-activation-server (appy-6065): could not associate with desktop session: Failed to connect to socket /tmp/dbus-BFYYqW9UiN: Connection refused
Jul 28 19:08:11 appy-desktop pulseaudio[6081]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jul 28 19:08:11 appy-desktop pulseaudio[6081]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jul 28 19:08:11 appy-desktop pulseaudio[6081]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 37286 Hz.
Jul 28 19:08:11 appy-desktop pulseaudio[6081]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Jul 28 19:12:40 appy-desktop aide-cron-daily: terminated because lock /var/run/aide/cron.daily.lock could not be obtaiend.
Jul 28 19:57:35 appy-desktop pulseaudio[6081]: shm.c: shm_open() failed: No such file or directory
Jul 28 19:57:35 appy-desktop pulseaudio[6081]: pstream.c: Failed to import memory block.
```

---

### Post by justborn on 2008-07-28
someone please check-out my log & please help me

---

### Post by chrisccoulson on 2008-07-28
Which log is this from? are you actually experiencing any other side-effects?

---

### Post by justborn on 2008-07-29
as the title reads .. "user log errors",its my 'user.log'.Ya, lots of side effects ,my sys is going bonkers.i think ,it is is error regarding ownership(user).

---

### Post by justborn on 2008-07-30
someone please help me

---

### Post by chrisccoulson on 2008-07-30
Please could you attacht your ~/.xsession-errors file as well?

Thanks

---

### Post by justborn on 2008-07-31
> **chrisccoulson said:**
> Please could you attacht your ~/.xsession-errors file as well?

Thanks
 with what application should i open the file.

---

### Post by chrisccoulson on 2008-07-31
You can view the file in any text editor (Gedit being the default). However, you shouldn't need to open it. You can attach it to your next post using the 'Manage Attachments' button that you'll see below the text entry area when you write your next post.

---

### Post by justborn on 2008-08-04
> **chrisccoulson said:**
> You can view the file in any text editor (Gedit being the default). However, you shouldn't need to open it. You can attach it to your next post using the 'Manage Attachments' button that you'll see below the text entry area when you write your next post.

there was no application by default,and i did try opening it wid gedit,but the output is not in human readable English.

---

