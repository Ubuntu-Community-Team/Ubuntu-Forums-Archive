---
title: "Audio Setup"
date: 2014-08-08
forum: Hardware
---

### Post by RelicUser on 2014-08-08
Hello Everyone.

Having been a Windows user for decades (originally CP/M), I finally took the Linux plunge by installing Lubuntu on an old computer.  Specifics of the computer are:
[LIST]
[*]Lubuntu 14.04.1
[*]Asus P4P800S-X
[*]Intel Celeron D 2.53 MHz
[*]2 GB RAM
[/LIST]

My intent is to use this computer as an internet browser and a way to view PDF documents.  I've figured out how to share the NTFS 2nd internal hard drive on my home network, which turned out to be easier than I thought but took a lot longer than expected.

My computer has on-board audio (ALSA) but it doesn't work with my default Lubuntu installation.  However, I had to install the correct audio driver when I previously used it with Windows XP Pro.  I found a Linux driver on the Asus web site but I have no idea how to install it or if it even needs to be installed.  The "Install" file gives me instructions but I really have no idea if they are applicable to me.  The introduction of "Install" is:

```
The ALSA driver replaces the OSS/Free driver. The OSS/Free driver is
present in current Linux kernels (2.2).  Since version 0.4.0, ALSA has
supported only 2.2+ kernels. The 2.0 kernels are no longer supported. You
must compile the kernel with sound support (you do not need to select
any of the other sound modules apart from sound support).

Before installing this driver, it will be helpful to read carefully
the documentation for insmod, modprobe, kmod and for the isapnp
module if you have an ISA PnP soundcard.

```

Any advice would be greatly appreciated!

---

### Post by Yellow Pasque on 2014-08-08
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> found a Linux driver on the Asus web site 
It's ancient. Forget about it.

---

### Post by RelicUser on 2014-08-10
Thank you for the very prompt reply.  I followed in the instructions in the above link and got the following result:

[http://www.alsa-project.org/db/?f=a5f2fb125626917c4e8c5978be1956148590b314](http://www.alsa-project.org/db/?f=a5f2fb125626917c4e8c5978be1956148590b314)

I hope I copied the address correctly from my terminal screen as I haven't yet figured out how to copy text from it (ctrl & shift insert don't work) or how to make the text in the terminal window larger.

---

### Post by RelicUser on 2014-08-16
Even if the Asus audio driver is ancient, I would expect that it would work well enough to get sound out of my computer.  Those installation instructions aren't very clear to me so it would be great if someone could point me in the right direction.

I have a spare PCI Sound Blaster card.  Does Lubuntu have built-in drivers for this sound card to work?

---

### Post by RelicUser on 2014-08-22
I figured out how to copy from the terminal window so details of my audio system should be available in the link below:

[QUOTE="AlsaInfo"]Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org?") [y/N] : y
Uploading information to [www.alsa-project.org]("http://www.alsa-project.org") ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=a5f2fb125626917c4e8c5978be1956148590b314](http://www.alsa-project.org/db/?f=a5f2fb125626917c4e8c5978be1956148590b314)

Please inform the person helping you.[/QUOTE]

---

