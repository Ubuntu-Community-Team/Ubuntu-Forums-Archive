---
title: "Strange AHCI Issue with MD RAID"
date: 2009-10-15
forum: Hardware
---

### Post by rhomboid on 2009-10-15
I was installing 9.04-server on a couple of Supermicro 6016T-NTF machines yesterday and tried to do a very standard RAID-1 mirror of the two drives I put in the box. Everything seems to work as far as booting and running but the "drive fail" LED blinks red on the second drive (in SATA port order) immediately after the kernel starts booting (fine during grub or booting off CD). The RAID is fine according to /proc/mdstat but the alarm is annoying.

This only happens when the SATA controller is configured in AHCI mode instead of "IDE" (I want NCQ, etc.). It doesn't matter what slot/caddie combo I move the second drive to or if I swap the "blinking" drive with the first drive, the "second" drive always "fails".

I see nothing interesting in the kernel log output or in other standard system logs.

Anyone run into this? It's really obnoxious, but I guess I can live with IDE mode if I really have to. Thankfully these machines are not going to see intensive disk use and the ones that do I use either hardware RAID cards or external FC-connected storage boxes.

---

