---
title: "Laptop gets hot and drains battery during suspension"
date: 2021-03-26
forum: Hardware
---

### Post by jbh54enwiler on 2021-03-26
I recently installed Kubuntu 20.10 on my new Lenovo IdeaPad Slim 7 (14IIL05) and I've managed to fix some of the problems it had but there's one that's ongoing.  When I close the lid on the laptop and leave it in my bag, it'll get quite warm, and it'll quickly drain the battery, as if it didn't go to sleep.  I've tried looking at the logs, and the only thing that seems to stick out is this error: 

```
3/25/21 11:06 PM	nvme nvme0	I/O 528 QID 5 timeout, aborting


```

I'm not entirely sure if the SSD in the NVMe slot is actually causing suspend to fail or not.

---

### Post by blackbird34 on 2021-03-26
Hi. I've had a lot of sleep issues with my new NVME-equipped laptop (in signature) too. I can't be sure of this (not a hardware specialist at all), but I don't think it's the SSD.

A lot of these newer laptops don't suspend the way they used to. Microsoft has been pushing a new "Modern standby" sleep mode, which works like phone sleep i.e. it can do various things and connect to the internet while "asleep". Linux systems AFAIK can't do this, but in some cases, they don't go to sleep either and just stay on. 

I solved it by updating to the latest MSI UEFI (BIOS), which seemed to reset a bunch of boot parameters, realise that I was running Linux, and offer a Linux-compatible sleep mode. Maybe try that?

---

### Post by jbh54enwiler on 2021-03-27
Just a quick update, I managed to catch my PC in the act of failing to suspend, and I have the correct logs of it now.

```
3/26/21 9:19 PM    jbh-IdeaPad-Slim-7-14IIL05    kernel    [94098.721260] PM: Device 0000:00:1f.3 failed to suspend: error -110
3/26/21 9:19 PM    jbh-IdeaPad-Slim-7-14IIL05    kernel    [94098.721264] PM: Some devices failed to suspend, or early wake event detected
```

I'm pretty sure this is the relevant log.

Edit: According to "lspci," the device that prevented suspension was the audio controller, which had stopped working when the suspension failure happened.

---

### Post by CelticWarrior on 2021-03-28
First thing to do was already suggested: Update UEFI.

---

### Post by jbh54enwiler on 2021-03-29
OK, so my hardware vendor only issues UEFI updates through EXE files and attempting to run the EXE from Windows PE failed because the UEFI updater EXE doesn't support WinPE.  It doesn't seem like my BIOS supports updates directly from a USB drive in BIOS so short of reinstalling Windows on my machine every time I need to update the UEFI I'm not sure what I can do.  I've heard that it's not a good idea to use Wine to update the UEFI either since it's a very low level call.  Any suggestions?

---

### Post by CelticWarrior on 2021-03-29
Any Windows executable for such update can also be run from a simple DOS bootable media. And usually there are other options even when the update is release as OS dependent (it should be OSA agnostic in any case but some vendors are... like that).

That said, even with your current version, try to find a setting about "OS Selection" (it can be hidden under an unassuming name) and change any "Windows 8/10" to anything else, Linux, Android, Other or even "Windows 7"...

---

### Post by jbh54enwiler on 2021-03-30
There's no setting on Lenovo's website besides Windows 10, unfortunately.  As for DOS, I made a bootable USB with FreeDOS on it.  Now, do you know what I need to do to get the updater EXE running in there?  I have it on a flash drive, but I'm not sure if DOS supports flash drives, and I don't know which commands to use.

---

