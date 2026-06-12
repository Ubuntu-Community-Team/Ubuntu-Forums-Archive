---
title: "Question about G33 (Bearlake) SATA settings on Gigabyte Mobo"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by oneleaftea on 2007-08-15
Hello,

I am a Linux newbie, and have a few hardware questions regarding installation of Ubuntu (am also considering LinuxMint Cassandra) on my new system. 

The spec's are:
Gigabyte GA-G33M-S2  (Intel G33/Bearlake ICH9 chipset)
2 Gigs of RAM DDR26400
1 SATA HD
1 SATA DVD-RW drive
Onboard graphics and sound
No PATA/IDE drives (Jmicron IDE controller disabled in the BIOS)
Currently running Windows XP (with 30 gigs unpartitioned space available for Linux)

I am a bit uncertain on what the proper settings are for SATA. I installed Windows XP with AHCI mode disabled. Can I install Ubuntu with the AHCI mode disabled? It is my understanding that if I enable AHCI, my Windows will fail to boot.

Additionally, I have SATA Port0-3 Native mode set as enabled in the BIOS. Not sure if this is the proper setting?

I have heard some people having problems with the ICH9, and it seemed to involve SATA operation, so I'm not sure what the best settings are and the best way to approach installation. 

Does anyone know if I will have better luck installing with the next Ubuntu release (Gutsy) when it is officially released? If so, I don't mind waiting a bit. 

Thank you very much for any advice!

---

### Post by fredj on 2007-08-15
You will have to try it and see. My own experience was that Ubuntu wouldn't install from the Live
CD (the partition stage failed). It installed from the Alternate CD but was reluctant to boot up
in IDE mode. When I switched the mode to AHCI I had no more Linux boot problems but now
windows wouldn't boot.
The solution to all this was to set the disk to AHCI mode and reinstall Windows. Then Install
Ubuntu. Now both OSes boot without problems.

---

### Post by oneleaftea on 2007-08-16
Thank you very much for sharing. Hmm, i am reluctant to reinstall windows at this point. I will see if there is a way to fix this without reinstalling.

Do you or anyone know whether Gutsy will be able to handle non-AHCI mode? If so, i might wait until then.

---

