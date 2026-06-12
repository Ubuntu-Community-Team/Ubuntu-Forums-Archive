---
title: "PCMCIA CF card adapter (Sandisk) not mounting/appearing"
date: 2010-09-02
forum: Hardware
---

### Post by drknot on 2010-09-02
Hello,
I have just aquired a Sandisk PCMCIA adapter.
 from /var/log/messages:
pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
Sep  2 09:40:14 Norton kernel: [  541.110062] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
Sep  2 09:40:14 Norton kernel: [  541.111543] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
Sep  2 09:40:14 Norton kernel: [  541.152908] scsi8 : pata_pcmcia
Sep  2 09:40:14 Norton kernel: [  541.153065] ata9: PATA max PIO0 cmd 0x3100 ctl 0x310e irq 20

It does not automagically appear and I cannot work out what/where to mount this
I have checked forums/google and info is old and unhelpful (other than tracking down where to look in the logs)

Any hints/tips appreciated

---

### Post by drknot on 2010-09-02
Manged to get it running under Vista intermittently - maxing out at 830KB/s.
USB 2 CF multireader managing 1.8MB/S 

PCMCIA is 16 bit device unfortunately so not getting the speed I wanted.
Still interested in getting it to show up properly though

---

### Post by drknot on 2010-09-02
the mystery deepens.
just retried after reboot : initial insertion drive appears, try to open via Places -> "bad superblock"
re-try inserting, no icon appearing.

---

