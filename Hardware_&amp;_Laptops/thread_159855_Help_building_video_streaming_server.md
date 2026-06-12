---
title: "Help building video streaming server"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by alea on 2006-04-13
Hello, 



I have a G4 with MacOSX and a Dreambox 7000 (a satellite receiver with a 100Mbit/s ethernet card running a stripped down and customized version of linux) connected both to a TrendNet Router. The Dreambox can mount nfs-shares (also samba-shares) and play the movies located on the shared disks. (For the moment the shared disk is in my Mac.) 

My aim is to build a server on pc hardware that will contain the shared disks. As I read that ubuntu is quite user-friendly, I thought to use it as the operating system of my server. 

Here are the carateristics I want the server to have: 

- After the first configuration, the server will only consist of the tower connected to the lan (no monitor, no keyboard, no mouse). All maintenance should be done remotely from my mac. Can I do it using vnc? Is there a better solution? 

- When no nfs-streaming is occurring, the server should go in a state where it uses the least energy possible. I thought about the server suspending to disk. When I want to access the server, I would wake it up by a wakeOnLan package sent from the Dreambox. Maybe anyone has a better solution? (There is no point in letting the server run 24/7; it could also live with a shutdown in case of inactivity, if I knew that it would be possible to start it up with a wol.) 



Can I build the server using the following hardware: 

- Carte Mère AsRock 775i65GV Socket LGA 775
It has an onboard graphics card, onboard audio, onboard ide for 4 disk, onboard sata for 2 disks, onboard 100Mbit/s ethernet

- Processor Celeron 2,8Ghz D Socket LGA775 (might be overkill) 
- Memory 512MB DDR 400Mhz KingMax SuperRam

- Medium Tower Case ATX Antec SLK 3700 BQL noir


I read the manual of the motherboard; it only speaks about suspend to ram in the bios section. Will ubuntu override the bios and also allow a suspend to disk? 



What version of ubuntu should I use? Maybe the coming dapper as it will contain the suspend functionality in the standard distribution. I read about server editions, but where can I find info about them and especially, will they suspend when inactive? 



I will be very grateful for any help or comment. Have I forgotten anything? Am I doing anything wrong? 

Thanks in advance. 

alea



PS: Finally, a few words about my knowledge in informatics: I am not a pro; I have never used a Linux distribution; however I am using using MacOSX, where I am able to compile programs when I have an howTo (I recently compiled clamav88.1 to use it on my computer). Further, I played a bit with Fink, a project that aims to port free software to MacOSX. When installing something with Fink, the dependencies are automatically resolved...

---

