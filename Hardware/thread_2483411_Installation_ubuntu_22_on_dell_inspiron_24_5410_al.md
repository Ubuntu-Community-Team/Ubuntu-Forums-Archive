---
title: "Installation ubuntu 22 on dell inspiron 24 5410 all in one"
date: 2023-01-29
forum: Hardware
---

### Post by jupiter7455 on 2023-01-29
[COLOR=#000000]Hello,[/COLOR]
[COLOR=#000000]I bought a new dell inspiron 24 5410 all in one which have windows 11 installed.[/COLOR]
[COLOR=#000000]I wish make it dual boot with ubuntu 22.[/COLOR]
[COLOR=#000000]I make a uefi bootable disk with yumi. I choose ubuntu in the startup list but it can't be complete.[/COLOR]

---

### Post by oldfred on 2023-01-29
Ubuntu 22 or Ubuntu 22.04.1? Big difference.

I have a Dell with 11th Gen Intel and Windows 11.
I had to turn off Windows bitlocker & fast start up which sets hibernation flag.
And used Windows to shrink NTFS partition to make unallocated space & reboot as it has to run chkdsk.

Then Ubuntu install worked without issue.

[COLOR=#000000] > it can't be complete.[/COLOR]
Is this booting live installer in UEFI boot mode or the actual install?

---

### Post by guiverc on 2023-01-29
I installed Ubuntu 22.04 LTS & Ubuntu *lunar* (23.04) last Thursday on a device which had windows 11 installed.  To get around the *disabled bitlocker *of the *unused* windows 11 system, I did what oldfred has already suggested, booted the windows & shrunk the *ntfs* partition from there, then had no issues installing the two Ubuntu products I wanted.

Note: Im not experienced with installing Ubuntu Core 22 or a 22 system, I tend to stick to the far more widely used *year.month* products like 22.04 or 22.10.

Do note how you write the ISO to installation media can create problems, thus I recommend doing it using a *supported* method for your release. Whilst I'm not familiar with 22 installs, I am very aware that you can write a 22.04, 22.10 or 23.04 (etc) ISO in a manner that makes it only installable on specific devices (eg. uEFI only, BIOS only etc), however using a QA-tested method (*or simple clone*) makes the media work on all types (uEFI, Secure-uEFI & legacy/BIOS).  I'm not familiar with `yumi`.

---

### Post by rivid on 2023-01-30
Hi
I believe your system is in RAID mode. To enable Ubuntu to install you may need to change to AHCI mode. If you plan on dual booting windows and Linux you will have to be cautious as just changing it in the bios will prevent windows from booting and will require a reinstall. If you intend to change to AHCI mode here are the steps from within windows:

[https://superuser.com/questions/1280141/switch-raid-to-ahci-without-reinstalling-windows-10](https://superuser.com/questions/1280141/switch-raid-to-ahci-without-reinstalling-windows-10)
[LIST=1]
[*]Run cmd as administrator (not PowerShell,)


[*]Copy-paste this command, which will start Windows in Safe Mode the next time you reboot:
 bcdedit /set {current} safeboot minimal

[*]Restart the computer and enter UEFI/BIOS setup.


[*]Change the SATA operation mode from RAID to AHCI.

[*]Save changes and exit Setup and Windows will automatically boot to Safe Mode.

[*]Launch cmd again, as in step #1.

[*]Copy-paste this command, which will start Windows in Normal Mode the next time you reboot:
 bcdedit /deletevalue {current} safeboot
[B]
DO NOT forget this last command or your Windows will be stuck in safe-mode.[/B]

[*]Reboot and Windows will automatically start with AHCI drivers enabled.

Assuming you have enough unused disk space you can proceed to install Ubuntu.

[/LIST]

---

### Post by oldfred on 2023-01-30
While I have for years suggested the change from RAID to AHCI, my Dell worked without that change. Both RAID & UEFI Secure boot were on when I installed 22.04.
My Dell only has one NVMe drive and Ubuntu used the Intel® VMD driver. I was not familiar with it, but it has been available in kernel for a while, but Ubuntu must not have had compiled in until 22.04.

---

### Post by rivid on 2023-01-30
You may well be right about the VMD driver. I did have some bad experiences with an older Dell 2350 all in one which led me down that path to change from RAID to AHCI. Admittedly that was a few years back.

---

### Post by jupiter7455 on 2023-01-31
Hi.
1- i checked the bitlocker option, i find it disabled.
2- i checked the SATA/NVMe operation, i find it in AHCI/NVMe mode.
3- i reboot the system and i boot from a bootable device which have installed ubuntu with YUMI
4- the opeartion stoped in this step and the pc crashes again.

---

### Post by oldfred on 2023-01-31
You never said what version?
Core 22, 22.04.1 LTS or 22.10?

Note that 22.04.2 will be out soon with more updates.
Ubuntu 22.04.2 LTS Delayed To End Of February Over Kernel & Signed Shim Woes
[https://lists.ubuntu.com/archives/ubuntu-devel/2023-January/042419.html](https://lists.ubuntu.com/archives/ubuntu-devel/2023-January/042419.html)

Not familiar with Yumi, but I would think it should work.
But we find many that use a different install tool, a different port, or a different flash drive then find it works. Not sure why?

---

### Post by oylex on 2023-01-31
Hi, I have the same problem with the same computer model.

However, I'm not trying to dual boot, I just want to replace the Windows OS with Ubuntu Server

Here's the specs of my machine:

Dell Inspiron 24 All-In-One Model 5410
23.8" FHD Touch Display with Webcam
Intel Core i7-1255U
16GB Memory
512GB SSD
Integrated Intel Iris Xe Graphics
Windows 11 Home

Here's what I've tried:

- Updated the BIOS to latest using the online updater in the F12 menu
- I tried with secure boot enabled and disabled
- I tried with storage "mode" set to "Raid" and set to "AHCI/NVMe"
- I tried creating the USB key with Rufus and Yumi, I tried GPT, MBR, FAT32, NTFS
- I tried multiple versions of Ubuntu Live Server, I started with 20.04.5 (Resulted in the PC being stuck on the DELL logo), then 22.04.1 and 22.10 (They both load Grub fine, but when I select Try or Install Ubuntu, it freezes)
- I also tried loading gparted to see if I could do something with the hard drive, but it has the same behavior, grub loads, but beyond that it freezes

When the PC freezes, it displays a white cursor that is not blinking and the keyboard seems to shutdown (the LEDs go out) and no keys are working.

I'm experienced with Linux and I'm willing to try suggestions.

Thanks, I'll keep checking this thread.

---

### Post by jupiter7455 on 2023-02-01
Hi, 
yeah Oylex i have the same model, 
i tried to change the BIOS configuration of secure boot and other related option but it can't be resolve.

---

### Post by oldfred on 2023-02-01
You can try 22.10 which is not LTS. Or wait a couple of weeks for 22.04.2.
Ubuntu 22.04.2 LTS Delayed To End Of February Over Kernel & Signed Shim Woes
[https://lists.ubuntu.com/archives/ubuntu-devel/2023-January/042419.html](https://lists.ubuntu.com/archives/ubuntu-devel/2023-January/042419.html)

If willing to experiment you can already download testing versions of 23.04 also not LTS and out officially in April.
 While being updated, it generally works, but some update may break things. Not for production use. 
When released you do not have to reinstall as all updates are applied, but with all the update, log files & history may have a lot of extra info. I always reinstall.

---

### Post by oylex on 2023-02-01
Hi,

Leaving an update on my progress.

I tried installing 23.04, it's still not working, but we're getting further.

First, I tried installing it with the storage mode AHCI/NVMe, I could boot on the live image and I followed the wizard to start the installation, left Ubuntu to choose how to deal with the disk (Overwrite all data), but during the installation progress bar, I got this error message:

```
Installation Failed

The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk.
It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
```

Then, I changed the storage mode to Raid (which was the default in the BIOS), I could access the same steps as above, and I got another error message:

```
Installation Failed

The installer encountered an error copying files to the hard disk:

[Errno 30] Read-only file system: '/target/usr/lib/x86_64-linux-gnu/libpinyin/data/bigram.db'

This is often due to a faulty hard disk. It may help to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
```

Update: After that last error, Ubuntu 23.04 doesn't see the hard drive anymore, nor does the BIOS.

In live mode, the disk doesn't show up in the disk utility I only see the USB key and the Loop Device. When trying to install again it shows an internal error

The bios diagnostic tool found an error: Hard drive not installed.

So I'm gonna see what I can do about that.

---

### Post by LeoBastos on 2023-02-23
Same problem, I have tried the described approaches so far without success. It didn't work on the newest 22.04.2 LTS. I cannot even start the live USB image, it goes to a black screen just after choosing either (Try or Install Ubuntu) or (Ubuntu (safe graphics)).

---

### Post by LeoBastos on 2023-02-24
Thanks for posting your effort here, I really appreciate it. In my case, I am not sure why but what seems to help was editing the grub loading by typing 'e' at Try Ubuntu without installing option from the initial black screen menu.  Then replace the words 'quiet splash' with 'nomodeset'. Then hit F10 to  boot." I try this after reading the post bellow:

[URL="https://askubuntu.com/questions/832163/black-screen-when-loading-ubuntu-live-usb"]https://askubuntu.com/questions/832163/black-screen-when-loading-ubuntu-live-usb

[/URL]After doing that I would expect to see the error msg, but it actually started the live USB and I could install the 22.04.2 version. I haven't test it yet, but so far so good.

Cheers

---

### Post by uspenna on 2023-03-27
Hi, I can confirm LeoBastos post (above) about installation.

I've bought a Dell Inspiron All-in-one 24", model 5410, with Intel i5-1235U. 

I've booted a USB Ubuntu 22.04.2 and have edited the GRUB boot option, typing 'e' and ripping of the 'quiet' and the 'splash' options. No need to insert 'nomodeset' after all (but no harm will be done inserting it :))

The installation went fine and everything worked well, except by the camera. The camera behaves very strange ..

---

