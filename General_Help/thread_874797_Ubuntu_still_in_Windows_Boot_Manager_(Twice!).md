---
title: "Ubuntu still in Windows Boot Manager (Twice!)"
date: 2008-07-30
forum: General Help
---

### Post by AGMaster on 2008-07-30
Hiya all

I installed wubi on my computer and it worked fine! THen for some reason it broke so I unistalled it, It did a great job of removing the files but it didn't remove the record from the boot manager. I installed it again, same thing, now I have two ubuntu options, bot dont work!

Here's my setup info (i'l try and be as relevant as possible)
Two 250GB HD's (were raided ages ago, i removed raid from one hd and (after i had installed ubuntu and it broke) unraided the other recently)

HD1 (C: ) Vista Ultimate 64-Bit, I use this one incase anything goes wrong with:
HD2: (F: ) Vista Ultimate 32 Bit, I use this one Primarily.

At first i installed Wubi from 32-bit onto the hd containing 64-bit (C: ), then it broke (Only loaded grub, couldnt find boot.list) so i tried to uninstall but it didnt remove the boot record.

(For some reason, 32-Bit stopped booting at the same time as ubuntu broke, I fixed it by replacing the F:\Windows\system32\winload.exe file with a friends copy. Just before the time when 32-bit vista broke and ubuntu broke, I loaded up vista 32 and it did a disk check on C:, then they both stopped working (after next re-boot)

I next installed it from 64-bit into the same place (C: ), again didnt work (loaded ubuntu, with the orange bar going back and forwards, but thats as far as it gets, then it went into a command line interface)

So now im stuck with boot manager showing

Windows Vista Ultimate 64-Bit
Windows Vista Ultimate 32-Bit
Ubuntu
Ubuntu

Both ubuntu's now say that a file is missing!

msconfig.exe will not show the ubuntu in its list of OS's
The vista repair (part of the install cd) is the same
On the vista cd in the command line console, I tried refreshing the windows boot manager with the fixmbr /F command (or similar, i cant remember exactly, Its stands for fix master boot record) and it said it it did it but they still appear!?

Any ideas any one?

Regards,

AGMaster

P.S If you've read ALL of that, You deserve a medal, Mind you I typed it!

---

### Post by ago on 2008-07-30
It's a known issue of wubi rev505, you can use this uninstaller [https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1](https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1)

Note that if you have already removed the wubi folder manually you need to edit the boot menu manually as shown here: [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

### Post by AGMaster on 2008-07-30
> **ago said:**
> It's a known issue of wubi rev505, you can use this uninstaller [https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1](https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1)

Note that if you have already removed the wubi folder manually you need to edit the boot menu manually as shown here: [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

Thanks for detailed help, Im going to try it later. Im not entirly sure what wubi i was running, I had already got ubuntu 8.0.4.1 iso so i nicked the wubi.exe file from it

---

