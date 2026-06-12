---
title: "ACPI error, system halt, HP Omen laptop, every Ubuntu distro"
date: 2019-01-09
forum: Hardware
---

### Post by marcocipriani01 on 2019-01-09
Hello everyone,
What happened:

[LIST]
[*]    Working, suddenly screen blocked, only mouse movement, not even responding to keyboard commands
[*]    Pressed Ctrl-Alt-F5 to access the command line (Ctrl-Alt-F[number] are the only combinations detected in those cases)
[*]    No login, only screen full of errors telling that my ext4 filesystem is read-only, so the OS couldn't logrotate (see photo). Some lines on the screen were regarding acpid (Linux's daemon for delivering ACPI events, [https://wiki.archlinux.org/index.php/Acpid](https://wiki.archlinux.org/index.php/Acpid))
[*]    Forced shutdown by pressing the power button
[*]    Ran dmesg after startup: full of ACPI errors, like:
[/LIST]

> ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS14._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
ACPI Error: Skip parsing opcode Method (20180531/psloop-542)

PC:

[LIST]
[*]HP OMEN 15-ce0xx
[*]UEFI BIOS F.18 11/09/2018 (latest version)
[*]i7-7700HQ, 16 GB RAM, NVMe SSD (Ubuntu's partition is in /dev/nvme0n1p5) + SATA HDD
[*]NVIDIA GeForce GTX1050 Mobile, nvidia-driver-390 installed
[*]Kubuntu 18.10, Kenel 4.18.0-13-generic, but experienced similar errors in previus installations of Ubuntu 18.10 on the same PC
[/LIST]


Looking for "ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS10._PLD]" (one of the errors I got from dmesg) I found this thread: [https://ubuntuforums.org/archive/index.php/t-2404566.html](https://ubuntuforums.org/archive/index.php/t-2404566.html)
Summary:

[LIST]
[*]Problem:
[LIST]
[*]Linux doesn't recognize the NVIDIA graphics card as an audio card, and applying a patch to the Kernel to fix it makes suspending/hibernating the laptop impossible
[/LIST]

[*]Solution:
[LIST]
[*]Apply kernel patch to fix NVHDA (NVIDIA HD audio): [https://github.com/hhfeuer/nvhda](https://github.com/hhfeuer/nvhda)
[*]As result, suspend/hibernate won't work, fix it: manually disable the NVHDA Module before putting it to suspend/hibernate
[LIST]
[*]sudo tee /proc/acpi/nvhda <<< OFF"
[/LIST]

[*]Then to turn it on again after resume with
[LIST]
[*]sudo tee /proc/acpi/nvhda <<< ON
[/LIST]
[/LIST]

[*]Similarities with my case:
[LIST]
[*]I can't play audio via HDMI and the NVIDIA graphics card isn't recognized as audio output device (not listed in /proc/asound/cards)
[*]Some errors regarding ACPI reported in the thread are the same I got from dmesg
[/LIST]
[/LIST]


I didn't install the Kernel patch, I'll do it only when I am sure it will fix everything.
So, are my ACPI error and the problem that NVDIA audio is missing related? I suppose yes, because, as far as I can read in the thread, NVHDA, ACPI and suspend/hibernate interfere with each other.
How to can I fix the ACPI error?
I also tried setting the "acpi=off" Kenel parameter but it made my PC extremely slow, with 100% CPU usage doing nothig, I wasn't able to shutdown via Ubuntu and my graphics card wasn't detected.
Attached photo of tty5 after system halt and tar.gz archive with logs from dmesg.
Kind regards,
Marco

[ATTACH]282161[/ATTACH]

[ATTACH=CONFIG]282160[/ATTACH]

---

### Post by luks911 on 2019-01-09
Hello,

First of all, sorry for my English.

I have a HP OMEN 15-ce001la with Ubuntu 18.10 working without problems. I installed the nvidia drivers from de graphics-drivers PPA repository and never experienced a problem like yours. So, I am not helping much... but, ¿could your issue been related to a hardware problem? :-k

---

### Post by marcocipriani01 on 2019-01-09
> [COLOR=#000000]could your issue been related to a hardware problem?[/COLOR]
Windows (dual boot) runs without problems on this computer... which is also brand new
> [COLOR=#000000]from de [/COLOR][COLOR=#000000]graphics-drivers PPA[/COLOR]
Is the package you installed "[COLOR=#000000]nvidia-driver-390[/COLOR]"?
Thanks

---

### Post by luks911 on 2019-01-09
No, I installed nvidia-graphics-drivers-410, which is the latest version recommended in the Nvidia web.

---

### Post by marcocipriani01 on 2019-01-09
OK! Thanks, tomorrow I'll try to remove *[COLOR=#000000]nvidia-driver-[/COLOR]390* and install *[COLOR=#000000]nvidia-graphics-drivers-[/COLOR]410*. It should work, both computers have a GTX 1050. One more question: are you able to play audio via HDMI?
Kind regards

---

### Post by luks911 on 2019-01-09
Sorry, I've never tried to play audio via HDMI. I don't have a HDMI cable neither a TV. Let me know if you need more data on this subject. 
And, well, now I am at my notebook, and dmesg show me the same errors:  

> [    0.094807] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS10._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.094810] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.094812] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)

but I've never have problems like you describe with the screen blocked or those you show in the photo of the screen.

---

### Post by marcocipriani01 on 2019-01-10
Just installed *nvidia[I][COLOR=#000000]-drivers-[/COLOR]410*[/I] and everything seems to be OK. I hope the error won't happen again.
> [COLOR=#000000]now I am at my notebook, and dmesg show me the same errors[/COLOR]
So they aren't the issue. Thanks again

---

### Post by marcocipriani01 on 2019-01-11
Unfortunately the error occurred again, so the issue isn't graphics. This time, I don't why, some foreground programs continued running even if plasmashell crashed and everything else freezed. Krunner wasn't available so I wasn't able to restart Plasma again. One of the foreground programs was Android Studio, which reported that my filesystem was **read-only**: exacly what all the logs from tty5 said last time. From Android Studio I tried opening a terminal, but since the filesystem was read-only, the program crashed. Other programs, like Chromium, continued working until I tried accessing files from my fs. I closed everything and turned off the computer from the power button. The problem must be, I suppose, a Kernel error: I exclude a corrupted filesystem (etx4) because the same problem occurred in other installations, but I'll try scanning my fs anyway. Does anyone have an idea?

---

### Post by marcocipriani01 on 2019-01-11
e2fsck -vf /dev/nvme0n1p5 reported no errors.

---

