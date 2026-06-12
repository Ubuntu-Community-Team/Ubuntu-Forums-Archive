---
title: "ACPI Error: Method parse/execution failed [18.04LTS]"
date: 2018-09-21
forum: Hardware
---

### Post by rhaes on 2018-09-21
Hello,

I actually have this problem a lot. The last time I had it, I was told I should try to update my BIOS. I did that and it never helped. There's no new BIOS for me to try for my motherboard, won't ever be one. Sometimes this problem will occur and will just immediately boot me into Ubuntu, but most of the time it does this and the only solution is to completely reinstall everything....and wait for it to happen after a while again, usually after an update. 

I've spent three days googling this and haven't found anything that can help me. I'm at a complete loss. This is what the screen says;

[https://imgur.com/9VsR2SE](https://imgur.com/9VsR2SE)

I've made sure my system clocks are all set correctly and everything for my other OSes. I can't even boot into Ubuntu to try anything. Any help? :(

---

### Post by xsoto on 2018-11-09
Good day,

I also get same errors on boot, with Ubuntu Mate 18.04.1 64b running on EFI mode on Ryzen 5 2400G box. This error appears sometimes at boot, sometimes it does not, sometimes it appears and the computer still boots, sometimes it appears and the computer does not boot hanging on a black screen after BIOS POST and the two grey screens of mate boot.

> [FONT=courier new]
Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
Linux 4.15.0-38-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux[/FONT]

> [    0.000000] ACPI Error: [SMIC] Namespace lookup failure, AE_ALREADY_EXISTS (20170831/dswload-378)
[    0.000000] ACPI Error: 1 table load failures, 7 successful (20170831/tbxfload-246)
[    0.068286] ACPI Error: [PTOS] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
[    0.068295] ACPI Error: Method parse/execution failed \, AE_NOT_FOUND (20170831/psparse-550)

> [    0.837122] MODSIGN: Couldn't get UEFI db list
[    0.837357] MODSIGN: Couldn't get UEFI MokListRT


Usually, can boot with 4.15.0-20, and can't on 4.15.0-38. Though if the box is off for sometime, it does boot and fast with the 4.15.0-38 kernel. The process is too random to analyze properly in order to find a cause. Please point out how to get info in order to solve the issue and I will post it here.

Thanks and regards,
RR

---

### Post by Bashing-om on 2018-11-09
Maybe worth a shot:
[http://iam.tj/prototype/enhancements/Windows-acpi_osi.html](http://iam.tj/prototype/enhancements/Windows-acpi_osi.html)

[INDENT]could be Yes
[/INDENT]

---

### Post by rhaes on 2018-11-09
Hello,

It has been some time, the issue persists randomly but enough to keep me almost consistently out of Ubuntu. Tonight it seemed to gotten worse. On top of the previous logs, after /dev/sdb2: clean, xxxxxxx, it started saying something about " a start job is running for dev-disk by XXXX (1-3)". Rebooting it several times, I noticed the codes following after it repeated three times of three codes, and those three codes were the UUID of my external HDDs. 

So....I went to recovery, which to my horror I found to be absolutely graphically slaughtered. My keyboard wasn't working right, seemed to be skipping keys when pressed, the root was already prompting immediately to the far left off the menu selection and if I pressed down to highlight something I would have to triple click to go down one option. It took some figuring out to manuever around this broken up recovery menu, but once I did, I dropped into root and did:

* sudo nano /etc/fstab*

and commented out my HDDs with # and rebooted. Ubuntu immediately rebooted without a problem. I will do several reboots now to see if the errors pop back up, but I used to get them every single boot since upgrading to the latest Ubuntu, and I didn't since commenting out my HDDs, so I don't think it'll happen but who knows. I'll also check to see if recovery is still borked.

EDIT

Okay, several reboots, and no errors with my HDDs commented out, but that means no accessing them, which is not good. But at least it is a temporary solution to get into the system to get some help. :(

Any ideas? Is avoiding usage of any external HDDs my only option here? I'm assuming my fstab commands are correct, but this is what I have for the external drives in fstab:

[I]UUID=XXXXXX   /media/Data1 ntfs-3g rw,auto,user,fmask=0111,dmask=0000,noatime,nodiratime   0   0
UUID=XXXXXX  /media/Data2 ntfs-3g rw,auto,user,fmask=0111,dmask=0000,noatime,nodiratime   0   0
UUID=XXXXXX   /media/Data3 ntfs-3g rw,auto,user,fmask=0111,dmask=0000,noatime,nodiratime   0   0[/I]

And I accuired my UUID with *sudo blkid*.

EDIT 2

[**[COLOR=#000000]@[/COLOR]**]("https://ubuntuforums.org/member.php?u=2101552")**[COLOR=#000000][[B][COLOR=#000000]xsoto[/COLOR]**]("https://ubuntuforums.org/member.php?u=2101552")[/COLOR][/B][B][COLOR=#000000][URL="https://ubuntuforums.org/member.php?u=2101552"][B][COLOR=#000000]
[/COLOR][/B][/URL][/COLOR][/B]
Do you also have any external HDDs plugged in on boot by chance and edited into fstab?

---

### Post by rhaes on 2019-02-25
BUMP

I'm still having this issue. I cannot add drives to my fstab, which I need to do so I can properly use Spotify, Banshee etc etc features, because if I do I get boot errors that eventually break my system. It is getting extremely frustrating to deal with. 

I've now tried:

[I]UUID=XXXXX   /media/XXXXX ntfs-3g rw,auto,user,fmask=113,dmask=002,uid=1000,windows_names,locale=en_US.utf8   0   0
UUID=XXXXX   /media/XXXXX ntfs-3g rw,auto,user,fmask=113,dmask=002,uid=1000,windows_names,locale=en_US.utf8   0   0
UUID=XXXXX   /media/XXXXXa ntfs-3g rw,auto,user,fmask=113,dmask=002,uid=1000,windows_names,locale=en_US.utf8   0   0[/I]

but it hasn't helped.

Isn't there *something* I can do? Has the method changed after 14.04? Because this is what I was using just fine back then. 

Thanks for reading,

---

### Post by davidledger on 2019-02-26
Does boot stop at that error or continue and fail elsewhere. I have that error in syslog in my failing boot, but it then continues and just hangs later.

---

### Post by slickymaster on 2019-02-26
*Thread moved to **Hardware**.*

---

### Post by rhaes on 2019-02-27
> **davidledger said:**
> Does boot stop at that error or continue and fail elsewhere. I have that error in syslog in my failing boot, but it then continues and just hangs later.


Yes, if I have edited the fstab, the boot will stop at that error (it is a loop). The only way to get through it is to edit the fstab and remove my edits.

---

