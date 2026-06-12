---
title: "D-Ban on usb won't boot"
date: 2020-09-13
forum: Hardware
---

### Post by Dirk_Ouellette on 2020-09-13
D-Ban on usb stick that has worked previously to wipe another drive, will not boot, even though I have the usb stick set as first in boot order. Can I wipe a drive I am presently using,  from a terminal?

---

### Post by sudodus on 2020-09-13
- Which version of DBAN?
- What drive are you trying to wipe?
- How is that drive connected (SATA, USB ...)?

[HR][/HR]
- I have used [FONT=Courier New]**dban-2.2.7_i586.iso**[/FONT] to wipe hard disk drives, but I would not use it with an SSD.
.. You may have to treat the iso file with [isohybrid](https://help.ubuntu.com/community/mkusb/isohybrid) and then clone it in order to make a bootable USB drive.
.. I think that DBAN only works in BIOS mode, so if your computer boots in UEFI mode you must switch boot mode.

- It is possible to use [FONT=Courier New]**hdparm**[/FONT], but risky, if you don't know how to use the options correctly.
.. Warning: Do not attempt to issue a Secure Erase ATA command via hdparm on a device connected through USB.

- This link may be useful: [Securely wipe disk](https://wiki.archlinux.org/index.php/Securely_wipe_disk)

---

### Post by Dirk_Ouellette on 2020-09-13
Thank you Sudodus.  I used DD to wipe the drive. How do I know when it is finished wiping if there is only a non accessible screen now. Do I turn the machine off and see what happens? :-) :-) I am not worried about the content that may no longer exist.  Even if the drive is ruined, I'm not too worried

---

### Post by sudodus on 2020-09-14
1. Put your [FONT=Courier New]**[SIZE=3]dd[/SIZE]**[/FONT] process to the background with the hotkey combination [FONT=Courier New]**[SIZE=3]ctrl z[/SIZE]**[/FONT] and then the command [FONT=Courier New]**[SIZE=3]bg[/SIZE]**[/FONT]

2. Then look for the process number and run a very special kill command to make dd output a status report (how much that is written)
```

ps -A|grep ' dd$'
kill -s USR1 'the number found by the ps command'

```

You can find more details via the command [FONT=Courier New]**[SIZE=3]info dd[/SIZE]**[/FONT]

Demo example:
```

sudodus@bionic64 ~ $ [COLOR="#0000FF"]dd if=/dev/zero of=/dev/null[/COLOR]
[COLOR="#0000FF"]**^Z**[/COLOR]
[1]+  Stoppad                 dd if=/dev/zero of=/dev/null
[148] sudodus@bionic64 ~ $ [COLOR="#0000FF"]bg[/COLOR]
[1]+ dd if=/dev/zero of=/dev/null &
sudodus@bionic64 ~ $ [COLOR="#0000FF"]ps -A|grep ' dd$'[/COLOR]
 **3615** pts/1    00:00:18 dd
sudodus@bionic64 ~ $ [COLOR="#0000FF"]kill -s USR1 **3615**[/COLOR]
36862722+0 poster in
36862722+0 poster ut
18873713664 byte (19 GB, 18 GiB) kopierade, 34,9622 s, 540 MB/s
sudodus@bionic64 ~ $ [COLOR="#0000FF"]kill -s USR1 3615[/COLOR]
42813475+0 poster in
42813474+0 poster ut
21920498688 byte (22 GB, 20 GiB) kopierade, 40,1621 s, 546 MB/s

# [COLOR="#cc0000"]when overwriting with zeros, you should wait until **dd** stops with a message that the drive is full, so[/COLOR]
# [COLOR="#cc0000"]that it cannot write more to the drive.[/COLOR] During this test case I bring the dd process back to the foreground
# and kill it with **ctrl c**. You should also be able to stop it by sending a strong kill flag to the process,
# for example **kill -9** (instead of kill -USR1)

sudodus@bionic64 ~ $ [COLOR="#0000FF"]fg[/COLOR]
dd if=/dev/zero of=/dev/null
[COLOR="#0000FF"]**^C**[/COLOR]59240419+0 poster in
59240418+0 poster ut
30331094016 byte (30 GB, 28 GiB) kopierade, 54,5142 s, 556 MB/s

[130] sudodus@bionic64 ~ $ [COLOR="#0000FF"]ps -A|grep ' dd$'[/COLOR]
[1] sudodus@bionic64 ~ $ 

```

---

