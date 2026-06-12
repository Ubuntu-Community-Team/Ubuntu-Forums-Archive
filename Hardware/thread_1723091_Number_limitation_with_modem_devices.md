---
title: "Number limitation with modem devices?"
date: 2011-04-06
forum: Hardware
---

### Post by WilsonJJ on 2011-04-06
Hello everyone,


First sorry if I am being a noob asking questions were it could be simply solved, but I am quite new to Linux. And I really can't think what keywords to use on the search engines, so I ended up here..


Anyway this is what I am trying to doing and problem that I am facing.
I am trying to setup a fax server by using ubuntu 10.10 i386 with hylafax with 18 Conexant pci modem cards by using HSF Linuxant drivers, before I brought all of those 18 card, I tried with just 2. And there weren't any problem with it.

Today I went and brought an other 12 of them, but now the system only can install a total of 8, all 8 of them can install the drive and linked to hylafax with no problem, but I am really running out of ideas what can be the cause if this.

I've tried by running:
dmesg | grep tty
```
ttySHSF0 at I/O 0xcc00 (irq = 16) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)
ttySHSF1 at I/O 0xc880 (irq = 18) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)
ttySHSF2 at I/O 0xc800 (irq = 19) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)
ttySHSF3 at I/O 0xc480 (irq = 16) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)
ttySHSF4 at I/O 0xc400 (irq = 17) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)
ttySHSF5 at I/O 0xec00 (irq = 17) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)
ttySHSF6 at I/O 0xe880 (irq = 18) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)
ttySHSF7 at I/O 0xe800 (irq = 19) is a Conexant HSF softmodem (PCI-14f1:2f50-14f1:205f)

```only 8 of them shows up

Meanwhile if  I go in to **Device Manager**, it will pick up all of them
[IMG]http://wilsonjj.myweb.hinet.net/Screenshot.jpg[/IMG]

so is the same if I run **scanModem** it will pick up total of 14.

I know its rude and nooby just to post a full dump of the report, but I thought might be better off just to post what might be needed all at once, and I am sorry for this..

Just for your intrest:
[**dmesg**]("http://wilsonjj.myweb.hinet.net/dmesg.html")
[**ModemData**]("http://wilsonjj.myweb.hinet.net/ModemData.html")

By the way are there any limitations on how many PCI devices I can install on Linux?


AND big big thanks in advance for reading this :D:D


Wilson

---

