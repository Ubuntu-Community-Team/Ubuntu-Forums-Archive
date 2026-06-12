---
title: "How do I add a fax modem?"
date: 2006-02-08
forum: Hardware &amp; Laptops
---

### Post by BobSongs on 2006-02-08
I've got a Conexant HCF modem that works as a faxmodem under XP. Can anyone point me to a tutorial on how to enable a faxmodem. I believe it's completely functional. Here's the relevent output from **scanModem**> [FONT="Courier New"]PCIBUS=0000:00:0f.0

Providing detail for device at  0000:00:0f.0
  with vendor-ID:device-ID
            ----:----
Class 0780: 14f1:1036   Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
  SubSystem 14f1:1036  Conexant HCF 56k Data/Fax/Voice/Spkp Modem
        Flags: bus master, medium devsel, latency 32, IRQ 12

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 14f1:1036 14f1:1036 ubuntu 2.6.12-10-686  3.4.5 4.0.2    i686
  14f1:1036 is a Conexant HCF modem.[/FONT]I know a few people who have this modem too. If Ubuntu has a fax/modem feature where applications can "print to fax" it would help as a selling point for those I'm trying to influence.
:D

---

### Post by AllenGG on 2006-02-08
Bob, the only company that I know of that uses that modem is IBM.
And it's a "Win-modem". It may be in other OEM's but of the hundreds that I've seen it's always been IBM and a similiar package that was in fact made by the same company in China. (Mexico units too)
Modems are cheap. Infact, ask around, someone may give you one. Most Winmodems will work with Linux as fax modems. They may not work as IP units.
Allen

---

### Post by BobSongs on 2006-02-09
[QUOTE=AllenGG]Most Winmodems will work with Linux as fax modems. They may not work as IP units.
Allen[/QUOTE]Just what I'm looking for. I think I mistitled this thread. I'm aware this is a win-modem. I'm just trying to figure out how I would print to the fax, say, through OpenOffice. I'd like to send an invoice to someone's fax. How would I add the modem to my list of printers? I'm sure it's a different idea than in Windows.

Thanks.

---

### Post by beanni on 2007-02-07
Check this out: [http://www.ubuntuforums.org/showthread.php?t=320534&highlight=faxing+with+ubuntu](http://www.ubuntuforums.org/showthread.php?t=320534&highlight=faxing+with+ubuntu)

It might work for you.  I am not having much luck with it at the moment, but I am a complete newbie.

---

### Post by drpaul on 2007-02-07
Look at efax.

Paul

---

