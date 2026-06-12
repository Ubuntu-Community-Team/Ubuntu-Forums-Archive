---
title: "Project: A trustworthy Ubuntu pen drive"
date: 2016-08-12
forum: Hardware
---

### Post by Megadoomer on 2016-08-12
Hi everyone,

I am working on an idea that I'd like to share with you and maybe optimise the details and missing elements of it.

*The problem:* You're often at different computers either at work, at school/university or at public places and you want to check your emails or log into banking accounts/online shops on the go from a safe, trustworthy system without having to worry about your confidential data being intercepted by a compromised OS and without altering the machine you're at in any way.

*The concept:* You could take along a small piece of hardware that contains a system that you have set up (e.g. with an encrypted partition, password manager, pre-configured VPN tunnel) and that boots from as many different machines as possible and runs reasonably stable and safe.

With the possibility to install Ubuntu on USB drives, I got the idea to buy a small pen drive for my keychain to always have a bootable system with me from which I can access my emails and online accounts securely. I have already tested this and it has worked well in many situations, but there is still room for improvement, so I would like to reach out to you and look for ways to improve this concept.

So far, my drive looks like this:

[ATTACH=CONFIG]270666[/ATTACH]

sdx = A generic, bootable 16GB USB pen drive
```
dev/sdx
   /sdx1   4GB fat32-partition (25% of drive space, for easy measurement. Used to easily share data between all most common systems. Since it is the first partition, it will be recognised automatically and all systems can read/write to it, handy to have. Should a computer-illiterate thief find the drive and plug it into their (most likely) Windows machine, they will only see this partition and may format/use it until the end of time without suspicion.)
   /sdx2   boot-partition (unencrypted, containing the boot information)
   /sdx3   ext4 Ubuntu system-partition (encrypted by LVM, containing all program and personal data including /home)
   /sdx4   swap-partition (reasonably sized, depending on the remaining space of the drive, for system stability)
```

I have had good experiences where the system to-go and the small USB memory have come in handy, but I have also noticed inconsistencies that I would like to work on.

1. Choice of derivative: On a first thought, the logical choice would be Lubuntu/Xubuntu, as they require less resources and the USB connection benefits from all performance gains that can be achieved (especially when on USB 2.0 speed). However, both Lu- and Xubuntu sometimes do not recognise the WiFi adapters of certain laptops while vanilla Ubuntu on the exact same version will, by default. This is a huge drawback, as internet connection is, of course, an essential benefit for this system. But are there maybe better options that could even enhance compatibility?

2. Choice of kernel: Another question regarding stability/compatibility. I have not yet changed the standard Ubuntu kernel in any way. Are there Linux kernels that could work with a greater amount of hardware than the stock kernel and could they easily be installed on the drive's system?

3. Set-up/initialisation problems: I noticed that Ubuntu 14.04 and 16.04 do not boot as reliably on all devices as 12.04. The exact issues I have not been able to define, yet. Much seems to be related to ACPI problems on certain Dell and Acer SoC-laptops or dw_dmac modules, on others the graphics are broken before or after grub. I've had success by removing the string "quiet splash" from the grub config file at /etc/default/grub and adding "acpi=off" to the grub parameters. Since the system is usually not in use for an extended period of time, this adds no problems and increases compatibility greatly. Can someone think of other changes that could benefit the potential to be able to boot reliably from as many devices as possible?

4. Concerning UEFI/Secure Boot: There are more and more new machines with UEFI and Secure Boot motherboards. I have no experience with this at all and was wondering how to ensure that the USB drive will be able to boot in UEFI/Secure Boot as well as a legacy device on older machines. Is this even possible?

5. The guest account: It would be great to be able to lend the drive to a person that is in need of a secure and trustworthy system without having to log into the main account, so an enabled guest session would be nice. However, although a system cracker finding the drive is unlikely to succeed in breaking and accessing the encrypted system partition before the owner is able to change all passwords, how secure is it to have a guest account that everyone finding the system has immediate access to? Could there be exploits that someone could use to quickly get access to personal data? Should the guest account rather be disabled in this scenario?

A small note on the remaining security issues: Having a trustworthy system is great, but there are still threats that can not be fixed on the software-side, such as malicious firmware or hardware keyloggers. Taking along a small keyboard and observing the hardware before use is an initial safety measure, but 100% security is difficult to achieve. Yet, this drive is still a better choice than a public system on which students and co-workers may browse unsafe sites and download all kinds of files when needing to quickly access online accounts or personal data.

As you are able to read, I am mainly concerned with the objective of improving the compatibility and stability of the system to make it useful in as many situations as possible and I am wondering what settings and configurations could improve the ability to boot and run from the largest amount of hardware possible out of the box.

I hope someone may benefit from my ideas and observations and I am looking forward to read your suggestions! ;)

If you have any advice that could improve this concept, please feel free to criticise and comment.


Kind regards!

---

### Post by sudodus on 2016-08-12
> **Megadoomer said:**
> 
[CODE]

1. Choice of derivative: On a first thought, the logical choice would be Lubuntu/Xubuntu, as they require less resources and the USB connection benefits from all performance gains that can be achieved (especially when on USB 2.0 speed). However, both Lu- and Xubuntu sometimes do not recognise the WiFi adapters of certain laptops while vanilla Ubuntu on the exact same version will, by default. This is a huge drawback, as internet connection is, of course, an essential benefit for this system. But are there maybe better options that could even enhance compatibility?

Standard Ubuntu has the drawback, that several old computers have too little CPU horsepower, GPU horsepower (3D) or RAM to work well. I have not seen the WiFi drawback of Lubuntu and Xubuntu, but I guess you are right. Maybe you can try Ubuntu MATE, which is about as light as Xubuntu.
> 
2. Choice of kernel: Another question regarding stability/compatibility. I have not yet changed the standard Ubuntu kernel in any way. Are there Linux kernels that could work with a greater amount of hardware than the stock kernel and could they easily be installed on the drive's system?

You could consider the 32-bit version (with a 32-bit kernel). It works in [very] old computers too, but it is tricky to make it work in UEFI mode. You can make a persistent live drive work with a 32-bit version also in UEFI mode according to the following link,

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

It is possible to create a second user with log-in and encrypted home in a persistent live system. But I am not sure that it is as secure as a system with encrypted disk (actually encrypted partition). See this link

[EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)
> 
3. Set-up/initialisation problems: I noticed that Ubuntu 14.04 and 16.04 do not boot as reliably on all devices as 12.04. The exact issues I have not been able to define, yet. Much seems to be related to ACPI problems on certain Dell and Acer SoC-laptops or dw_dmac modules, on others the graphics are broken before or after grub. I've had success by removing the string "quiet splash" from the grub config file at /etc/default/grub and adding "acpi=off" to the grub parameters. Since the system is usually not in use for an extended period of time, this adds no problems and increases compatibility greatly. Can someone think of other changes that could benefit the potential to be able to boot reliably from as many devices as possible?

Use the mount option noatime and turn off journaling to reduce wear. You can also reduce the swappiness for the same reason.
> 
4. Concerning UEFI/Secure Boot: There are more and more new machines with UEFI and Secure Boot motherboards. I have no experience with this at all and was wondering how to ensure that the USB drive will be able to boot in UEFI/Secure Boot as well as a legacy device on older machines. Is this even possible?

You can make portable installed systems that boot in both UEFI and BIOS mode according to the following link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

These systems have 64-bit kernels and will not boot in old 32-bit computers.

> 
5. The guest account: It would be great to be able to lend the drive to a person that is in need of a secure and trustworthy system without having to log into the main account, so an enabled guest session would be nice. However, although a system cracker finding the drive is unlikely to succeed in breaking and accessing the encrypted system partition before the owner is able to change all passwords, how secure is it to have a guest account that everyone finding the system has immediate access to? Could there be exploits that someone could use to quickly get access to personal data? Should the guest account rather be disabled in this scenario?

I don't know, but I suspect that the guest account adds some risk.

You can offer other users a small live pendrive (a separate USB drive with a live *ubuntu system, 'Try *ubuntu') instead of a guest system in your encrypted pendrive.

---

### Post by Megadoomer on 2016-08-13
> **sudodus said:**
> I have not seen the WiFi drawback of Lubuntu and Xubuntu, but I guess you are right. Maybe you can try Ubuntu MATE, which is about as light as Xubuntu.

I can assure you that this anecdotal observation was the case for both derivatives. I can't remember though if they were installations or live systems with which I had this problem, I also noticed this a while ago, so it might still have been on version 12.04 or 14.04 and is maybe not the case for 16.04 anymore. Still, would be helpful to know of this is common for some DEs, there were probably also certain features left out, as the ISOs are smaller than that of vanilla Ubuntu. I will definitely test MATE for this, although it will be hard to test it in order to be really safe. Normally I would not care for this too much, but for this situation, it's nice to know that the system is as compatible as possible, of course.

> **sudodus said:**
> You could consider the 32-bit version (with a 32-bit kernel). It works in [very] old computers too, but it is tricky to make it work in UEFI mode.

I forgot to mention this in my first post: I have been using the 32-bit version for the USB drive the whole time, again, for compatibility. I also think that 64-bit has no real benefit, since the system will mostly be used for Firefox/Tor, email clients, file management and office programs, maybe an occasional image/media playback, but video already gets tough in some cases.

> **sudodus said:**
> It is possible to create a second user with log-in and encrypted home in a persistent live system. But I am not sure that it is as secure as a system with encrypted disk (actually encrypted partition).

That's actually another alternative I haven't though of. I've done a bit of reading on Ubuntu's native encryption methods and apparently the only (practical) difference between the LVM/dm-crypt partition encryption and an encrypted home-folder in this sense is that eCryptfs doesn't encrypt the metadata of the user folder, but the content is supposed to be secure. Encrypting a single folder with dm-crypt is not even possible, I believe, so that would be the only option any way without using third-party software, I guess.

> **sudodus said:**
> Use the mount option noatime and turn off journaling to reduce wear. You can also reduce the swappiness for the same reason.

I was aware of these options, but deliberately chose to not change them for two reasons respectively: With this drive, I do not actually care very much about wear on the flash memory. The data bandwidth will be very limited, as the system will only be used occasionally for short periods of time and there won't be large collections of data passing through, so the drive will probably be physically damaged from travelling more likely than the memory being worn out by those additional writes, so I guess I would rather have that information. Also, I would prefer the system to slow down and swap, if necessary, than have it completely lock up, because the swappiness is set too aggressively (although I could slightly lower it without turning it off, probably).

> **sudodus said:**
> You can make portable installed systems that boot in both UEFI and BIOS mode according to the following link,

[Installation/UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

These systems have 64-bit kernels and will not boot in old 32-bit computers.

I wasn't aware that you have done work on this. Thank you for the link, I  will look into that! It seems a bit more complicated than I expected  and apparently a decision has to be made here regarding Secure  Bootability. Could this be in any way related to the newly found Secure  Boot exploit and used in a way to circumvent it in this case?

---

### Post by sudodus on 2016-08-13
> **Megadoomer said:**
> ...

I wasn't aware that you have done work on this. Thank you for the link, I  will look into that! It seems a bit more complicated than I expected  and apparently a decision has to be made here regarding Secure  Bootability. Could this be in any way related to the newly found Secure  Boot exploit and used in a way to circumvent it in this case?

This UEFI and BIOS system was *not* made in any way related to the newly found Secure Boot exploit.

---

### Post by autocrat on 2016-09-08
I think Puppy is probably the best way to accomplish what you are trying to do. It is pretty much made to run from Flash Drives. I think you can even run it from a DVD and use the DVD to save changes. The downside of puppy of course being that it is not nearly as user friendly, and WiFi is bound to be a hassle on unfamiliar machines. If you want to stay in the Ubuntu family, I would recommend Ubuntu Mate. It runs light, and is well put together.

---

### Post by vasa1 on 2016-09-08
Please read the thread title carefully and limit your posts to the topic. Off-topic posts will be jailed. If you have something interesting to contribute that isn't directly connected with this thread please start your own thread. Thank you.

---

### Post by QIII on 2016-09-08
To put a finer point on it:  

The OP asked about ***_Ubuntu_*** and mentioned the two flavors Xubuntu and Lubuntu.  Let's keep this to the Ubuntu family.

---

