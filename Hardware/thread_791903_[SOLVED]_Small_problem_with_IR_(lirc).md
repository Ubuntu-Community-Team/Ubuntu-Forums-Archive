---
title: "[SOLVED] Small problem with IR (lirc)"
date: 2008-05-12
forum: Hardware
---

### Post by unimatrix on 2008-05-12
Hello. I've managed to configure my IR controller (Creative Audigy 4 External Hub).

Whenever I run **ircat**, **irw**, or **irxevent**, lirc will immediately crash, producing the following log in /var/log/syslog
```

May 12 20:34:45 Andrej lircd-0.8.3pre1[10287]: accepted new client on /dev/lircd
May 12 20:34:45 Andrej lircd-0.8.3pre1[10287]: cannot open /dev/snd/midiC0D1: No such file or directory
May 12 20:34:45 Andrej lircd-0.8.3pre1[10287]: caught signal

```

Funny thing is, the file DOES exist. I can even read it using
cat /dev/snd/midiC0D1
(if i press any keys on my remote it gets printed out here)

If I ls it:
```

$ ls -la /dev/snd/midiC0D1
crwxrwxrwx+ 1 root audio 116, 9 2008-05-09 19:02 /dev/snd/midiC0D1

```

So why does lirc think that file doesn't exist?

---

### Post by unimatrix on 2008-05-12
SOLVED!

in "/etc/lirc/hardware.conf" i needed to set this variable correctly:
```

REMOTE_DRIVER="livedrive_midi"

```

Everything is explained in this amazing Gentoo wiki:
[http://gentoo-wiki.com/HOWTO_LIRC#Creative_Labs_Sound_Blaster_Audigy_2_Platinum](http://gentoo-wiki.com/HOWTO_LIRC#Creative_Labs_Sound_Blaster_Audigy_2_Platinum)

EDIT: Apparently Gentoo-Wiki decided they don't want people to use it and deleted all the useful articles. Fortunately here's a different source:
[http://www.gentoo-wiki.info/Creative_Labs_Sound_Blaster_Audigy_2_Platinum](http://www.gentoo-wiki.info/Creative_Labs_Sound_Blaster_Audigy_2_Platinum)

---

