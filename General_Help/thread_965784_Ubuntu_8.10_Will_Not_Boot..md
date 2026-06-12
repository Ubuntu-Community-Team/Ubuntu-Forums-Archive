---
title: "Ubuntu 8.10 Will Not Boot."
date: 2008-10-31
forum: General Help
---

### Post by rags01 on 2008-10-31
Currently Ubuntu will not boot under the latest kernel and crashes with an error that goes something like this:

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1 Ubuntu6) Built-in Shell (ash)

The Error is then followed By:

(initramfs) [36.396048] ata2: SRST failed (errno=-16)

I previously had 8.04 and GRUB had the option to boot using an older kernel if you pressed 'escape' before the countdown and I could get into Ubuntu fine howver the new ubuntu does not have this option, only to boot using the regular kernel or the same kernel in recovery mode. Is there anyway I could fix the current problem or add an older kernel?

Any help would be great. :)

PS. I am very new to Ubuntu and Linux so I'm not even sure if you call it a 'boot kernel' it's just the options that you get in the grub menu when you press 'escape' I am refering to.

---

### Post by rags01 on 2008-10-31
Please Help Me!

---

### Post by the lush on 2008-10-31
Sorry, I can't help you, but I have seen the same error message. I originally tried the x64 version of 8.10, and then the x86 version. Using Wubi all seems to go well, but when I try to boot into Ubuntu all I get is a white screen. On one of my install attempts I saw the error you reported. 8.04 worked perfectly on almost identical hardware, so I have no idea what the issue is, which is a pity as I timed the purchase of this laptop to coincide with the release of 8.10, but now I am stuck in Vistaland.

---

### Post by the lush on 2008-10-31
Oh, in case this is useful to the folk here who understand Ubuntu, here are the machine specs:

Old Laptop (8.04 - worked perfectly on first install)

CPU: Intel T8300
Chipset: Intel 965PM + ICH8
Graphics: ATI MR3650
Platform: Santa Rosa

New Laptop (White screen, cannot even get a terminal after the splash screen)

CPU: Intel T9400
Chipset: Intel 965PM + ICH9
Graphics: ATI MR 3650
Platform: Montevina

---

### Post by phidia on 2008-10-31
rag01, what happens if you try to boot in recovery mode? You can also try to press Ctrl+D after this line appears > (initramfs) [36.396048] ata2: SRST failed (errno=-16) sometimes boot may resume. I think there's a hardware problem or bug.

the lush, at the white screen does pressing Alt+Ctrl+F1 bring you to a terminal?
if it does you can check logfiles (/var/log/messages) and try the "startx" command.

---

### Post by the lush on 2008-10-31
Unfortunately not, the white screen persists and then the machine crashes.

I'm downloading 8.04 now, and will see if it installs to determine if it it the hardware hating Ubuntu in general, or an issue with 8.10 with this hardware.

---

### Post by rags01 on 2008-10-31
I pressed Ctrl+D And Managed To Get Through To The Recovery Menu.

Now in that menu which option should I select?

The Options Are:

Resume - Resume Normal Boot
Clean - Try To Make Free Space
DPKG - Repair Broken Packages
FSCK - File System Check
Root - Try To Root Shell Prompt
Xfix - Try To Fix X Server

And Thanks For Your Help So Far.

---

### Post by rags01 on 2008-10-31
I resumed boot and managed to get into Ubuntu! Now What?

---

### Post by phidia on 2008-11-01
> **rags01 said:**
> I resumed boot and managed to get into Ubuntu! Now What?

The best thing I believe would be to do > sudo apt-get update && sudo apt-get upgrade You can also open synaptic from System > Admin click the "reload" icon and when that completes click "Mark All Upgrades" which is essentially the same as the apt commands I provided. 

If you have a hardware problem-or this is a bug that hasn't been dealt with yet that may not solve your problem.

---

### Post by rags01 on 2008-11-01
Okay I updatedd and am Now restarting.

---

### Post by rags01 on 2008-11-01
No Good It Still Won't Boot!

However there is another error message that is now appearing.

[40.956c36] ata2: link is slow to respond

Then There Is Another Error But Runs Down The Screen To Quick! It's Something Like This:

ata2: SSTAS Failed

---

### Post by rags01 on 2008-11-01
No Good It Still Won't Boot!

However there is another error message that is now appearing.

[40.956c36] ata2: link is slow to respond

Then There Is Another Error But Runs Down The Screen To Quick! It's Something Like This:

ata2: SSTAS Failed

---

