---
title: "Issues with Earfun Air Bluetooth earphones"
date: 2024-08-07
forum: Hardware
---

### Post by guybu on 2024-08-07
Since updating to Ubuntu 24.04 a few weeks ago, I've been having problems with my Earfun earphones ([https://www.amazon.co.uk/EarFun-Wireless-Bluetooth-Detection-Headphones-Matte-Black/dp/B088H7GMHZ](https://www.amazon.co.uk/EarFun-Wireless-Bluetooth-Detection-Headphones-Matte-Black/dp/B088H7GMHZ)). 

They worked fine before, but now they cut in and out, and the sound distorts intermittently, which makes them impossible to use for meetings.

Please let me know what further info you'd need in order to diagnose the problem, I'll do my best to find it!

---

### Post by currentshaft on 2024-08-07
.

---

### Post by guybu on 2024-08-07
I've had a search for Bluetooth logs on the forums, and I've used the terminal to run a few commands, but I don't know what I'm looking for. 

What command should I try? Should I run commands with the earphones connected? 

Just let me know and I'll copy/paste outputs here.

---

### Post by currentshaft on 2024-08-07
.

---

### Post by guybu on 2024-08-20
Thank you for your reply, sorry for the delay in my own response. 

Here's what happens when I run the first command in a terminal:

```
[Tue Aug 20 09:14:16 2024] audit: type=1107 audit(1724141656.643:213): pid=841 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/timedate1" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.113" pid=3474 label="snap.firefox.firefox" peer_pid=5532 peer_label="unconfined"
                            exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[Tue Aug 20 10:42:22 2024] perf: interrupt took too long (2542 > 2500), lowering kernel.perf_event_max_sample_rate to 78000
[Tue Aug 20 11:05:50 2024] perf: interrupt took too long (3185 > 3177), lowering kernel.perf_event_max_sample_rate to 62000
[Tue Aug 20 11:26:03 2024] input: EarFun Air (AVRCP) as /devices/virtual/input/input21
```


I don't know how much you need, there's a lot to copy and paste, so that's the last part.


Here's what I got when I ran the second command:

```
Aug 20 11:25:26 guy-desktop gnome-shell[1813]: meta_window_set_stack_position_no_sync: assertion 'window->stack_position >= 0' failed
Aug 20 11:26:02 guy-desktop systemd[1595]: Reached target bluetooth.target - Bluetooth.
Aug 20 11:26:03 guy-desktop kernel: input: EarFun Air (AVRCP) as /devices/virtual/input/input21
Aug 20 11:26:03 guy-desktop systemd-logind[959]: Watching system buttons on /dev/input/event9 (EarFun Air (AVRCP))
Aug 20 11:26:03 guy-desktop wireplumber[1630]: RFCOMM receive command but modem not available: AT+CSCS="UTF-8"
Aug 20 11:26:04 guy-desktop gsd-media-keys[2070]: gvc_mixer_card_get_index: assertion 'GVC_IS_MIXER_CARD (card)' failed
Aug 20 11:26:40 guy-desktop rtkit-daemon[1653]: Supervising 9 threads of 6 processes of 1 users.
Aug 20 11:26:40 guy-desktop rtkit-daemon[1653]: Supervising 9 threads of 6 processes of 1 users.
Aug 20 11:26:48 guy-desktop rtkit-daemon[1653]: Supervising 9 threads of 6 processes of 1 users.
Aug 20 11:26:48 guy-desktop rtkit-daemon[1653]: Supervising 9 threads of 6 processes of 1 users.

```

---

