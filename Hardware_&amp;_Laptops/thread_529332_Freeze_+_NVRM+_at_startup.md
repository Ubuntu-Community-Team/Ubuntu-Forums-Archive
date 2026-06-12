---
title: "Freeze + NVRM+ at startup"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by stijngysemans on 2007-08-19
I've got a major problem that makes my computer totally unusable and I hope you guys can help me out.

Problem:
After my computer boots up in the morning, it just totally freezes. This happens both at the login-screen and it can happen in the first minutes after the login. I can't move my mouse anymore, i can't press [ctrl] [ alt] [esc], i can't switch to another tty,...

My resolution so far:
After I reboot the system two to four times, the freeze doesn't happen anymore. So each morning I boot my computer, it freezes, i reboot it, it freezes again, and i reboot it until it stops freezing. quit annoying don't you think!

Some messages in the /var/log/syslog, just before the freeze

```

Aug 19 09:06:35 ubuntu-desktop kernel: [  204.706777] NVRM: Xid (0002:00): 6, PE0000 081c ffdbba75 ffdbba74 00000000 ffdbba75
Aug 19 09:06:35 ubuntu-desktop kernel: [  204.729250] NVRM: Xid (0002:00): 6, PE0000 0420 01010420 00000000 01010420 00000000
Aug 19 09:07:19 ubuntu-desktop syslogd 1.4.1#20ubuntu4: restart.

Aug 19 09:10:52 ubuntu-desktop kernel: [  253.302422] NVRM: Xid (0002:00): 6, PE0000 07fc ff1786ca 1f1786c8 00000000 ff1786ca
Aug 19 09:10:57 ubuntu-desktop kernel: [  253.352377] NVRM: Xid (0002:00): 6, PE0000 07fc ff097cc2 1f097cc0 00000000 ff097cc2
Aug 19 09:11:50 ubuntu-desktop syslogd 1.4.1#20ubuntu4: restart.

Aug 19 09:13:47 ubuntu-desktop kernel: [   66.144725] NVRM: Xid (0002:00): 8, Channel 00000000
Aug 19 09:13:59 ubuntu-desktop kernel: [   78.142889] NVRM: Xid (0002:00): 8, Channel 00000000
Aug 19 09:14:11 ubuntu-desktop kernel: [   90.147045] NVRM: Xid (0002:00): 8, Channel 00000000
Aug 19 09:14:57 ubuntu-desktop syslogd 1.4.1#20ubuntu4: restart.

```

NV had something to do with my videocard, maybe it is an hardware problem but because when the system used to be stressed under windows XP, the system became irresponsive also. Now it happens too much, my dad is going crazy.

Ty

---

### Post by stijngysemans on 2007-08-20
bump

---

### Post by stijngysemans on 2007-08-20
As i did some research myself, heat problems ([http://www.nvnews.net/vbulletin/showthread.php?t=96579](http://www.nvnews.net/vbulletin/showthread.php?t=96579)) could be causing this error. How can I read my temperature!?

---

### Post by stijngysemans on 2007-08-20
Dust removed, problem seemed to be solved now.... :lolflag:

---

