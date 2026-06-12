---
title: "RICOH card reader driver (deb)"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by chunchengch on 2008-04-20
**2008/05/10 :** [COLOR="Red"] If the deb does not work, you can try to download the source [ATTACH]69504[/ATTACH], extract it to the home folder, and compile it with the command **make**, then type **sudo make install** to install the driver[/COLOR]


I make a RICOH card reader driver deb file [ATTACH]66496[/ATTACH] for Ubuntu 8.04 (Hardy), wish it will be helpful for those who have problems on making card reader working.


PS: 

1. I am not the developer of the RICOH card reader driver, I just pack it as a deb file for easy installation, you can find the official website here [http://sourceforge.net/project/showfiles.php?group_id=190281](http://sourceforge.net/project/showfiles.php?group_id=190281) , thank the developer for the good job.

2. This driver does not support MMS card at this moment.

[COLOR="Blue"]Memory sticks are not supported at the moment.
MMC Plus cards probably do not work (not even on windows).

Some Notebooks (JVC MP-XV941, Dell X300) seem to have the cards lock status the other way round so that it is not possible to write to unlocked cards. Modprobe the driver with the switchlocked=1 parameter in this case.[/COLOR]

---

### Post by Acionyx on 2008-04-20
I think it's just what I was looking for...

Nonetheless, since I'm kinda new to all of this linux stuff, could you please tell me how to get it working? I installed the packaged and now what? 

I tried to insert my card in the ricoh slot, but it doesn't mount it automatically... I'm afraid you lost me :/

I would appreciate it if you could at least point me in the right direction. Sorry if I'm such a noob...

Thx!

---

### Post by chunchengch on 2008-04-20
This driver does not support MMS card, try to insert a SD card and test if it works, good luck !

---

### Post by Acionyx on 2008-04-21
Well, I was actually trying with an SD card.

I used to use Windows (just a couple of months ago) and, after installing the drivers, the computer simply recognized the card the moment I inserted it.

I was expecting Linux to do the same. But nothing actually happens...

I refuse to go back to Windows and this is actually the only thing that doesn't work for me. That said, I want to make it perfectly clear that I'm never going back, even if I have to buy a separate usb-connected card reader (I'm currently using a slot embedded on my laptop).

I'm sorry if I'm unable to give you more detailed and technical specifications on what's happening. Maybe one day I'll know enough about Linux to figure out these simple matters on my own :p

Cheers!

---

### Post by chunchengch on 2008-04-21
Please run command [COLOR="Red"]lspci | grep Ricoh[/COLOR] to check if the system can recognize the card reader, here is the output of mine for your reference.


$ lspci | grep Ricoh
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)

---

### Post by Caps18 on 2008-04-21
$ lspci | grep Ricoh
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)

I am in the same boat as Acionyx.  I abandoned Windows (although I started using Linux quite a few years ago) and this is one of the few things that isn't working as it should.  I am using Linux Mint, which is pretty close to Ubuntu.

I am using a SD card, and I have been able to use an external SD card reader.

Do you think that driver will work?  And how would I install it?

Thanks!

---

### Post by Acionyx on 2008-04-22
Funny enough, I got the exact same thing as Caps18:

$ lspci | grep Ricoh
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:01.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:01.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)

I also regrettably noticed that this output doesn't mention any type of card whatsoever :(

Does this mean my system doesn't recognize the card reader at all, and that I should simply forget about it?

Thanks again for your patience chunchengch!

---

### Post by chunchengch on 2008-04-22
I think you have to compile the source directly, here is the link to download [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4762682](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4762682)

extract the source file and then switch to the uncompressed directory,
type command [COLOR="Red"]make[/COLOR] to compile, if there are no errors, type [COLOR="Red"]sudo make install[/COLOR] to install the driver.

This is all I can help you, good luck!

---

### Post by Caps18 on 2008-04-22
It looks like that link goes to a reply box instead of a file.

---

### Post by chunchengch on 2008-04-22
[http://sourceforge.net/project/showfiles.php?group_id=190281]()

---

### Post by Caps18 on 2008-04-22
Good News!  It Works!

Thank you very much.

The only thing I would add is that you only needed the sdricohcs source .gz file.  Extract that file, use a terminal to go into that directory and type make and sudo make install. 

I did this without the card in the drive.  When it was completed, I put the card in and it was recognized.

---

### Post by andreselsuave on 2008-04-29
Doesn't work 4 me... anyone know another solution? I use Ubuntu Hardy with 2.6.24-16-generic
lcpi output:
```

02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)
02:06.5 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 10)
02:06.6 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 10)

```

---

### Post by aasche on 2008-05-01
> **andreselsuave said:**
> Doesn't work 4 me... anyone know another solution? I use Ubuntu Hardy with 2.6.24-16-generic
lcpi output:
```

02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)
02:06.5 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 10)
02:06.6 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 10)

```

```

02:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)

```
works as expected with sdricoh-cs (both: .tar.gz and .deb by chunchengch) on Ubuntu Hardy with Asus A3800G (alias A3G, A3878, A3878GLP, A3000).

---

### Post by chunchengch on 2008-05-01
> **andreselsuave said:**
> Doesn't work 4 me... anyone know another solution? I use Ubuntu Hardy with 2.6.24-16-generic
lcpi output:
```

02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)
02:06.5 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 10)
02:06.6 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 10)

```

I make a new deb, maybe you can give it a try. please get it in first post.

---

### Post by andreselsuave on 2008-05-04
> **chunchengch said:**
> **2008/05/02 :** [COLOR="Blue"]I make a new deb [ATTACH]68390[/ATTACH], it will check and install necessary dependencies, so it may be available for models R5C552 and RL5c476 etc, because I don't have RL5c476, so it will be appreciated if someone can test it and post the result, thanks![/COLOR]

I make a RICOH card reader driver deb file [ATTACH]66496[/ATTACH] , wish it will be helpful for those who have problems on making card reader working.

PS: This driver does not support MMS card at this moment.

[COLOR="Red"]Memory sticks are not supported at the moment.
MMC Plus cards probably do not work (not even on windows).

Some Notebooks (JVC MP-XV941, Dell X300) seem to have the cards lock status the other way round so that it is not possible to write to unlocked cards. Modprobe the driver with the switchlocked=1 parameter in this case.[/COLOR]

Your previous package I could install it but didn't work, but this new one, sdricoh-cs_0.1.3-2_i386, I can't even install... I get this error:

Error: Dependency is not satisfiable: kernel-default

Thanks a lot for your efforts.

---

### Post by chunchengch on 2008-05-04
> **andreselsuave said:**
> Your previous package I could install it but didn't work, but this new one, sdricoh-cs_0.1.3-2_i386, I can't even install... I get this error:

Error: Dependency is not satisfiable: kernel-default

Thanks a lot for your efforts.


The driver requires kernel version to be equal to or greater than 2.6.18, will you check this first? thanks!

---

### Post by andreselsuave on 2008-05-06
my kernel is latest version (I think 2.6.24.x) included  with latest paxk of Hardy heron

andreselsuave

---

### Post by FunckyJack on 2008-05-06
Thanks for that. I have tested with my notebook asus W1GC, now it's working fine.

---

### Post by fedjai on 2008-05-07
Hi,
I guess I have the same issue as andreselsuave, still no device available for mounting:
# lspci |grep Ricoh
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)

dmesg |grep ricoh
[   23.074435] ricoh-mmc: Ricoh MMC Controller disabling driver
[   23.074437] ricoh-mmc: Copyright(c) Philip Langdale
[   23.334391] ricoh-mmc: Ricoh MMC controller found at 0000:02:06.4 [1180:0843] (rev 10)
[   23.334405] ricoh-mmc: Controller is now disabled.
[   26.209852] sdricoh_cs: Ricoh PCMCIA Secure Digital Interface driver
[   26.209855] sdricoh_cs: Copyright(c) 2006 - 2008 Sascha Sommer


lsmod |grep ricoh
sdricoh_cs             12296  0 
pcmcia                 40876  2 sdricoh_cs,pata_pcmcia
mmc_core               51460  3 sdricoh_cs,tifm_sd,sdhci
ricoh_mmc               4352  0 

uname -r
2.6.24-17-generic


Any idea ?

---

### Post by rjcolomina on 2008-05-08
> **fedjai said:**
> Hi,
I guess I have the same issue as andreselsuave, still no device available for mounting:
# lspci |grep Ricoh
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)

dmesg |grep ricoh
[   23.074435] ricoh-mmc: Ricoh MMC Controller disabling driver
[   23.074437] ricoh-mmc: Copyright(c) Philip Langdale
[   23.334391] ricoh-mmc: Ricoh MMC controller found at 0000:02:06.4 [1180:0843] (rev 10)
[   23.334405] ricoh-mmc: Controller is now disabled.
[   26.209852] sdricoh_cs: Ricoh PCMCIA Secure Digital Interface driver
[   26.209855] sdricoh_cs: Copyright(c) 2006 - 2008 Sascha Sommer


lsmod |grep ricoh
sdricoh_cs             12296  0 
pcmcia                 40876  2 sdricoh_cs,pata_pcmcia
mmc_core               51460  3 sdricoh_cs,tifm_sd,sdhci
ricoh_mmc               4352  0 

uname -r
2.6.24-17-generic


Any idea ?

Exactly the same, and the card reader is not working. Any solution, please?:(

---

### Post by apedraza on 2008-05-08
Same here.... HP Compaq 8710w laptop. Did not work on Feisty, Gutsy or now Hardy. 

02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)
02:06.5 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 10)
02:06.6 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 10)

dmesg |grep ricoh
[   51.205077] ricoh-mmc: Ricoh MMC Controller disabling driver
[   51.205080] ricoh-mmc: Copyright(c) Philip Langdale
[   51.205117] ricoh-mmc: Ricoh MMC controller found at 0000:02:06.4 [1180:0843] (rev 10)
[   51.205128] ricoh-mmc: Controller is now disabled.

 lsmod | egrep 'mmc|ricoh|sdhci'
sdhci                  19076  0 
mmc_core               51460  1 sdhci
ricoh_mmc               4352  0 

Please help!!!

---

### Post by lordofthestrings on 2008-05-09
Hi people, I'm a almost 1 year noob and every now and then I've tried to make my ricoh embedded cardbus reader until now without success...

notebook Asus M6N

I tried the deb file and it didn't work for me, then I compiled it from source and IT WORKS!!!

I didn't even reboot! Just unplugged and replugged the SD card!

Thank you!!!!!!!!

UBUNTU is GREAT

---

### Post by chunchengch on 2008-05-10
> **apedraza said:**
> Same here.... HP Compaq 8710w laptop. Did not work on Feisty, Gutsy or now Hardy. 

02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)
02:06.5 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 10)
02:06.6 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 10)

dmesg |grep ricoh
[   51.205077] ricoh-mmc: Ricoh MMC Controller disabling driver
[   51.205080] ricoh-mmc: Copyright(c) Philip Langdale
[   51.205117] ricoh-mmc: Ricoh MMC controller found at 0000:02:06.4 [1180:0843] (rev 10)
[   51.205128] ricoh-mmc: Controller is now disabled.

 lsmod | egrep 'mmc|ricoh|sdhci'
sdhci                  19076  0 
mmc_core               51460  1 sdhci
ricoh_mmc               4352  0 

Please help!!!


You can try to compile the source, please the first post of this thread.

---

### Post by rjcolomina on 2008-05-11
I have compiled the driver and exactly the same.:(

Do I have to uninstall any other driver?

Thanks a lot for you help and effort.

---

### Post by DrObviousSo on 2008-05-14
Hm, this isn't working for me either.

> drobvious@DrStrangepork:~$ lspci | grep Ricoh
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
drobvious@DrStrangepork:~$ 



---

### Post by chunchengch on 2008-05-15
> **DrObviousSo said:**
> Hm, this isn't working for me either.

Did you try to compile from source? if you did, I think this drive probably does not support chip R5C832.

---

### Post by mizu12 on 2008-05-20
No success either:(

> 02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 10)

HP 6910p, source recompiled.
Nothing happened when card inserted,

---

### Post by WangWeiLin on 2008-05-21
Hi I am running a Samsung x10plus.

I only have a MS port. I hope you'll include the MS part soon.

thx a lot

---

### Post by SKiDRoX on 2008-05-26
> **mizu12 said:**
> No success either:(



HP 6910p, source recompiled.
Nothing happened when card inserted,

Exactly same config here ... samething hapenning.  I've been searching on different site with similar issues ... can't fin anything that works.  If anyone found a solution for our hardware, please post here.

Thanks

---

### Post by AnttiT on 2008-06-01
Thanks mate!:popcorn:

I got it working on my Asus M6Ne and it was easy. I just had to compile and install it.

This was the only annoying hardware issue I still had on my Linux installation.

You have to get this in the official repositories also.

-antti

---

### Post by El_Belgicano on 2008-06-03
> **lordofthestrings said:**
> Hi people, I'm a almost 1 year noob and every now and then I've tried to make my ricoh embedded cardbus reader until now without success...

notebook Asus M6N

I tried the deb file and it didn't work for me, then I compiled it from source and IT WORKS!!!

I didn't even reboot! Just unplugged and replugged the SD card!

Thank you!!!!!!!!

UBUNTU is GREAT

I'm trying for a long time also, and this is great news, I have the same model as you, I'll try this at home tonight ;)

---

### Post by El_Belgicano on 2008-06-22
Expected report: Worked perfectly (compiled from source on Gutsy kernel 2.6.22-15) on Asus M6N ... Thnx

---

### Post by gusmaco on 2008-06-25
thanks chunchengch & Caps18, the SD card reader in my Dell X300 is working because of your contributions

---

### Post by the12plus on 2008-06-27
I have read that this should not work for Memory Sticks :(

Is there ANY known workaround for Memory Sticks ? :confused:

Thanking very much in advance

---

### Post by mochiex2 on 2008-07-11
OH MY GOD~!!!! IT WORKS I have ASUS A3500L also known as A3L

01:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)

Had to do the "make" and "sudo make install" 
Works super well. Amazing. Good for you Taiwan

---

### Post by chunchengch on 2008-07-11
> **gusmaco said:**
> thanks chunchengch & Caps18, the SD card reader in my Dell X300 is working because of your contributions


> **mochiex2 said:**
> OH MY GOD~!!!! IT WORKS I have ASUS A3500L also known as A3L

01:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)

Had to do the "make" and "sudo make install" 
Works super well. Amazing. Good for you Taiwan


I am not the developer of the RICOH card reader driver, I just pack it as a deb file for easy installation, you can find the official website here [http://sourceforge.net/project/showf...roup_id=190281](http://sourceforge.net/project/showf...roup_id=190281) .

I want to thank the developer for the good job.

---

### Post by El_Belgicano on 2008-07-12
When writing to a SD-card, the "mmcqd" process takes an average amount of CPU usage of more than 80%... is that normal or fixed in a new version?

---

### Post by aasche on 2008-07-13
> **El_Belgicano said:**
> When writing to a SD-card, the "mmcqd" process takes an average amount of CPU usage of more than 80%... is that normal or fixed in a new version?
It's a known "bug" with version 1.3 - see: [Ubuntu 8.04 - sdricoh_cs v1.3 success]("http://sourceforge.net/forum/forum.php?thread_id=2046529&forum_id=669719"). So at the moment it's normal...

---

### Post by Timbosteron on 2008-07-19
Well, it doesn' work for me. :( I have a lenovo 3000 N200 and I can't get the xD-card reader working. It worked fine with windows, but it would be great to use it with ubuntu.

There are no error-messages or something, it just does not work.

-Tim

[I][SIZE="1"]08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
[/SIZE][/I]

---

