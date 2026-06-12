---
title: "Newly installed internal DVD drive isn't found on boot"
date: 2021-03-04
forum: Hardware
---

### Post by steveis2 on 2021-03-04
Hi, 
    I've installed an internal DVD but it doesn't appear in the list of drives or anywhere I can see. If I run the command  inxi -Fxz  to look at hardware the DVD doesn't show up there although all the hard drives do. To make it visible do I need to create some sort of mount point? There's in nothing the the CD-ROM folder. How could I create such a point? On the other hand should the DVD just show up somewhere regardless which would point to something more fundamental perhaps. 

    I have an Asmedia based PCIe SATA expansion card installed which gives access to an additional hard drive without a problem. The DVD is also attached to the same card. I've noticed that with the DVD attached and powered the boot process takes longer although there is no text on the screen during boot that might give a clue. 

     I have ubuntu mate 20.04.

    Any ideas would be welcome.

Regards Steve

---

### Post by CelticWarrior on 2021-03-04
If inxi doesn't show it then it isn't being detected. It has nothing to do with mount point. A new mount point will appear automatically with a readable disk inserted if and only if the drive itself is working and being properly detected.

> [COLOR=#000000]The DVD is also attached to the same card. I've noticed that with the DVD attached and powered the boot process takes longer although there is no text on the screen during boot that might give a clue.[/COLOR]
That shouldn't be the only thing noticeable. LED and/or initialization noise are typical occurrences with optical media. If the drive doesn't react during POST that is a clear indication that something's wrong.

There's hardware troubleshooting to be done before considering anything software related. The basic troubleshooting either wasn't done or wasn't mentioned in the OP. Is it a known good drive, i.e., has it been confirmed to work? If confirmed then is it detected when connected to the onboard SATA? If affirmative you should proceed to connect only the optical drive to the expansion card.

---

### Post by steveis2 on 2021-03-04
> **CelticWarrior said:**
> If inxi doesn't show it then it isn't being detected. It has nothing to do with mount point. A new mount point will appear automatically with a readable disk inserted if and only if the drive itself is working and being properly detected.


That shouldn't be the only thing noticeable. LED and/or initialization noise are typical occurrences with optical media. If the drive doesn't react during POST that is a clear indication that something's wrong.

There's hardware troubleshooting to be done before considering anything software related. The basic troubleshooting either wasn't done or wasn't mentioned in the OP. Is it a known good drive, i.e., has it been confirmed to work? If confirmed then is it detected when connected to the onboard SATA? If affirmative you should proceed to connect only the optical drive to the expansion card.

Thanks for your reply,
    The PC dual boots to windows and ubuntu. The drive works fine in a windows , attached to the same PCIe SATA expansion card. A hard drive connected to the card is detected OK in Ubuntu but the DVD isn't. If you put a disc in the drive the light flashes for a few seconds and then goes out and the drive goes dead. If I change the socket I plug the DVD SATA cable into (there are two) it makes no difference. It's still not detected.
     Looking at log messages could this have anything to do with it?

16:30:36 kernel: kfd kfd: device 1002:15dd NOT added due to errors
16:30:35 kernel: ahci 0000:05:00.0: AHCI controller unavailable!
16:30:35 kernel: ACPI Error: Evaluating _BCM failed (20200528/video-357) 

It seems strange that the hard drive is detected and connected no problem but the DVD isn't. I should point out also that the DVD drive worked perfectly with Linux when connected via the motherboards SATA sockets without the expansion board being there.

Regards Steve

---

### Post by Yellow Pasque on 2021-03-06
[https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208](https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208)

---

### Post by steveis2 on 2021-03-08
> **Yellow Pasque said:**
> [https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208](https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208)

Thanks for your reply.

I'm using ubuntu but I'll see if this can work.


Regards Steve

---

### Post by steveis2 on 2021-03-08
> **Yellow Pasque said:**
> [https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208](https://www.linuxquestions.org/questions/showthread.php?p=5819208#post5819208)

Hi
    This actually solved the problem. Great. I can now read and use DVDs to play my films and my CD music collection (yes I know I'm old-fashioned). I can't boot from the DVD but I think that's a characteristic of the motherboard not booting from PCIe SATA expansion cards rather than anything else.

Many thanks for the link.

Regards Steve

---

### Post by steveis2 on 2021-03-10
Thanks to Asrock support the dirives can now be booted as well.

---

