---
title: "Hot plugging an IDE hard drive"
date: 2010-07-12
forum: Hardware
---

### Post by akimbrel on 2010-07-12
Hi,

I am trying to solve a problem relating to hot plugging an IDE hard drive. I know that IDE drives don't support hot plugging at the hardware level. That is, they don't have a way to let the kernel know that they are plugged in like AHCI sata drives do. But there should be a way to go backwards and instead of having the drive tell the kernel that it is there, have the user tell the kernel to check if the drive is there. There must be some way to do it as the kernel has to detect the drives and create the device nodes when the system is booting.

If I know that an IDE hard drive has been removed from my system, or will be shortly, is there a way to tell Ubuntu that the drive is no longer there and to remove all of the associated device nodes, etc? If I wanted to then plug another IDE drive into the system and let Ubuntu know that it is there so that it can load the device node, how do I do that?

I have been searching for an answer to this and all I have found is that it might have something to do with udev, udevadm, or initctl. I haven't be able actually figure out how to do it. What I'm really after is the generic scsi nodes (i.e. sg0, sg1 etc) being updated when the hardware changes so that I can open a file and use libata to pass ata commands to the drive. I don't care about file system mounting and stuff like that.

I am new to Linux, so if I don't know how all of the systems work together 100% yet. If I have missed something simple please let me know. Thanks for any help.

---

### Post by tookyourtime on 2010-07-12
This isn't really related to the software side. But in the past, if I've plugged a big IDE drive into the power supply when everything is running, the computer resets because of the voltage drop.

Just something for you to check, unless you're using a separate supply for this. And there may be a very good reason that after all these years hot-plugging was never introduced.

---

### Post by ST3ALTHPSYCH0 on 2010-07-12
I'd say that your best bet is to invest in an external USB enclosure.

---

### Post by xb12x on 2010-07-12
Make backups.

Connectors/cables of devices that support hot-plugging are designed to guarantee that during connection or disconnection the voltage-pins vs the data-pins make or break electrical contact in the proper order. Else there could be undefined states of data pins flailing while voltage is not settled.

Those undefined states could possibly cause random garbage to be placed anywhere on your IDE drive.

---

### Post by akimbrel on 2010-07-13
Thanks everyone for responding. I guess I should expand on what I'm trying to do since it definitely isn't the usual use pattern. For one, I don't care about the data on the drive. That is because I want to do things like data destruction, custom hard drive testing, diagnostic self tests, checking for smart errors, etc. Some of these tests are very short, so rebooting the computer each time becomes costly in terms of the time that it takes. I am able to do this hot swapping in DOS using polling, and it works fairly decently. The problem that I run into and the reason I want to move to Linux is that our DOS software is not 100% stable and it crashes relatively frequently (even when not hot swapping drives). I don't have access to the source code, so I can't just go in and fix it there. In addition, Linux is a modern, multi-tasking, network enabled enviroment that I believe would give us more benefit than just fixing the stability issues. I just hope there is a way to do what I want to with this. I know this is kind of an obscure question, so if no one knows the answer, perhaps some one knows who / where I could ask?

> **tookyourtime said:**
> This isn't really related to the software side. But in the past, if I've plugged a big IDE drive into the power supply when everything is running, the computer resets because of the voltage drop.

Just something for you to check, unless you're using a separate supply for this. And there may be a very good reason that after all these years hot-plugging was never introduced.

Our computers don't reset when plugging a drive in unless we accidentally short the connections, which is easy to do with molex connectors. I'm sure with some computers it would reset anyways, depending on how nice the power supply is. If this becomes a problem in the future, I'll have to look into a soft start system for the drives. In any case, hot swapping an IDE is definitively not something that I would recommend that the average user do on a regular basis and there probably are good reasons it hasn't been introduced.

> **ST3ALTHPSYCH0 said:**
> I'd say that your best bet is to invest in an external USB enclosure.

I would like to as I could plug in up to 127 drives to one computer (in reality, maybe 10 or so). However, unless things have changed, usb enclosures don't pass ata commands to the drive correctly. Perhaps I should look into this again to see if the situation has changed (although I kind of doubt it has). Thanks for the suggestion.

> **xb12x said:**
> Make backups.

Connectors/cables of devices that support hot-plugging are designed to guarantee that during connection or disconnection the voltage-pins vs the data-pins make or break electrical contact in the proper order. Else there could be undefined states of data pins flailing while voltage is not settled.

Those undefined states could possibly cause random garbage to be placed anywhere on your IDE drive.

This is a good point. However, for my use I don't care about the data on the drive. I think that maybe even if I did care about the data, that one way to get around this problem would be to put the drives into sleep mode before unplugging them. That way, no garbage data could possibly be written to the drive as it wouldn't even be spinning.

Thanks for all of the responses so far. I'm still looking for the solution. If you don't know what the solution is, but you know of some resource (a person, a more specific forum, an article, etc) that might be useful, please let me know. 

Here are some lines of thought that might be promising:
- "initctl emit" might be related to this problem. However, I don't know how to use it, what context it was intended to be used in, or what it really does.
- The same goes for "udevadm control" and "udevadm trigger."
- Perhaps there is a way to alter the IDE controller's driver so that it claims that the attached IDE drive is an AHCI drive even though it isn't and then simulate the functionality in the driver. The problems include: which driver 'level' should this be done at, how would I do it, and isn't there an easier way?

---

### Post by slavik on 2010-07-13
IDE cannot be hotswapped. PERIOD.

As has been suggested, invest in a 20-30USD USB adapter.

---

### Post by akimbrel on 2010-07-13
> **slavik said:**
> IDE cannot be hotswapped. PERIOD.

As has been suggested, invest in a 20-30USD USB adapter.

Thanks for your response. Due to your and **ST3ALTHPSYCH0**'s suggestions, I have looked into the USB adapter a little more closely. It looks like under the right conditions it might work for what I need. That's great news as I would prefer to use USB adapters. It looks like if the adapter supports SAT (SCSI ATA Translation) then you should be able to pass ata commands through to the drive. It brings up some new questions though:

1. Does anyone know of a USB adapter that definitely supports SAT?
2. Can I still use ioctl with SG_IO to send the ata command like I would with libata, or is there something separate to use with usb devices?
3. If SAT stands for SCSI ATA Translation, what does SATL stand for that is see in all of these T10 documents that I'm finding?
4. What other concerns are there with testing a drive through USB? Bandwidth limitations and timing issues come to mind as possible issues.
5. Are the SG0, SG1, etc nodes created in a predictable and enumerable fashion so that I can see what is connected and communicate with it?

slavik, I appreciate your response and I don't want to get into an argument, but I really think that this statement is wrong: "IDE cannot be hotswapped. PERIOD." The reason why is that I already do this in DOS. So, certainly if you are willing to use DOS, IDE can be hotswapped. Perhaps you meant that in Linux/Ubuntu it would be very difficult to hotswap IDE? I don't know. All I know is that its possible in DOS.

---

### Post by xb12x on 2010-07-13
Do an Internet search for "IDE to SATA converter". You might be able to buy something off-the-shelf which will just plug-in and work for you.

---

### Post by slavik on 2010-07-13
> **akimbrel said:**
> Thanks for your response. Due to your and **ST3ALTHPSYCH0**'s suggestions, I have looked into the USB adapter a little more closely. It looks like under the right conditions it might work for what I need. That's great news as I would prefer to use USB adapters. It looks like if the adapter supports SAT (SCSI ATA Translation) then you should be able to pass ata commands through to the drive. It brings up some new questions though:

1. Does anyone know of a USB adapter that definitely supports SAT?
2. Can I still use ioctl with SG_IO to send the ata command like I would with libata, or is there something separate to use with usb devices?
3. If SAT stands for SCSI ATA Translation, what does SATL stand for that is see in all of these T10 documents that I'm finding?
4. What other concerns are there with testing a drive through USB? Bandwidth limitations and timing issues come to mind as possible issues.
5. Are the SG0, SG1, etc nodes created in a predictable and enumerable fashion so that I can see what is connected and communicate with it?

slavik, I appreciate your response and I don't want to get into an argument, but I really think that this statement is wrong: "IDE cannot be hotswapped. PERIOD." The reason why is that I already do this in DOS. So, certainly if you are willing to use DOS, IDE can be hotswapped. Perhaps you meant that in Linux/Ubuntu it would be very difficult to hotswap IDE? I don't know. All I know is that its possible in DOS.
The fact that DOS exhibits "hot swappable/pluggable" behavior is not part of the spec. Each IDE channel has a master and a slave which are enumerated by the controller on startup. Please read this: [http://en.wikipedia.org/wiki/Integrated_Drive_Electronics](http://en.wikipedia.org/wiki/Integrated_Drive_Electronics)

Fact of the matter is that it was never designed to be hot pluggable (which USB was).

---

