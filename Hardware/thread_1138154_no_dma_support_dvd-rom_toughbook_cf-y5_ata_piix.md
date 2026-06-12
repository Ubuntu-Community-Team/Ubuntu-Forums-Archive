---
title: "no dma support dvd-rom toughbook cf-y5 ata_piix"
date: 2009-04-26
forum: Hardware
---

### Post by discord on 2009-04-26
DVD Video playback is poor in linux, however works well in windows.

sudo hdparm -t /dev/scd0
[sudo] password for discord:

/dev/scd0:
Timing buffered disk reads: 2 MB in 4.26 seconds = 480.64 kB/sec

According to someone running 7.04 they saw a much greater speed in 7.04 with piix module loaded

[http://davesource.com/Solutions/Linu...ic-Y5.html#DVD](http://davesource.com/Solutions/Linu...ic-Y5.html#DVD)

Some information about the ICH6-M chipset and dma

[http://www.thinkwiki.org/wiki/Proble...SATA_and_Linux](http://www.thinkwiki.org/wiki/Proble...SATA_and_Linux)


opened a bug on launchpad, but nobody cares...

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/357531](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/357531)

---

