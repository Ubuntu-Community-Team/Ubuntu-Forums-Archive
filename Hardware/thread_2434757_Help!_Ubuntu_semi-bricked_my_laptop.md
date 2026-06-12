---
title: "Help! Ubuntu semi-bricked my laptop"
date: 2020-01-10
forum: Hardware
---

### Post by vetmawd on 2020-01-10
I've been running Ubuntu 19.10 with nearly no problems for about a year now. My laptop is a Dell XPS 9550 and it came with windows 10. I installed Ubuntu in UEFI mode with dual boot. I use the nvidia drivers (not nouveau) and I have 16GB of RAM.

How it happened:
Yesterday I wanted to increase the mouse pointer size in my Ubuntu. I opened universal access, clicked on the bigger pointer and my system froze completely (not even REISUB worked). I hard rebooted and the same thing happened again. I guess there's some error that keeps freezing the system when it reboots and tries to load the bigger mouse pointer that I selected. After that I tried to boot into recovery kernel mode in grub which worked. I tried to see if I could somehow change the mouse pointer size back but didn't figure out how. I then ran the recovery mode's option to boot normally and it froze again. Whenever I reboot now even the recovery option doesn't work. It freezes up completely in the purple background part after it says "Initializing initramfs...". So now I can't boot anything that's installed in my Grub, not ubuntu, not ubuntu recovery and windows also doesn't work anymore.

Here is everything I tried next:
[LIST]
[*]Booting into windows: Doesn't work anymore. Keeps rebooting.
[*]Running the built in Dell epsa test to check if any hardware is damaged: All shows up fine (RAM too).
[*]Booting into boot-repair-disk-64bit.iso on USB:
[LIST]
[*]UEFI Mode: Doesn't seem to show up as an option in the Dell boot menu at all??
[*]Legacy Mode: Boots completely but the repair software then says it can't repair anything due to being in legacy mode.
[/LIST]

[*]Booting into live Ubuntu 19.10 on USB:
[LIST]
[*]UEFI Mode: Tries to boot then throws [all these errors at me]("http://i.imgur.com/kGduaMG.jpg") and then freezes.
[*]Legacy Mode: Boots fine up until I click "Try Ubuntu" then it tells me that it crashed and that I need to log out the current active user. At this point I am able to drop into a shell with ctrl + alt + F1 though. But I don't know what to do there? It's still legacy mode after all.
[/LIST]

[*]Updating the BIOS: I've successfully updated my Dell BIOS from 1.12.0 to the latest 1.13.1. Unfortunately it didn't solve anything.
[*]Booting into rescatux-0.72-beta6.iso on USB:
[LIST]
[*]UEFI Mode: **Worked! **I can boot and get [all these options]("http://i.imgur.com/66jbKqG.jpg") but I'm nore sure which I should try. Because I don't know what the actual problem is I also don't want to blindly press any of those buttons.
[*]Legacy Mode: Not tried yet
[/LIST]
[/LIST]

Here's what still works:
[LIST]
[*]Dell BIOS works fine
[*]Booting into various legacy systems on USB stick works fine. (Except for Ubuntu live!)
[*]I can drop down to a shell on the Ubuntu live install in legacy mode.
[/LIST]

What can I try next? Is there something I can do in the legacy mode booted ubuntu live terminal? Or should I try something in Rescatux? If so what?
I've decided to run the "UEFI PARTITION STATUS" script in Rescatux. [Here is the output.]("http://i.imgur.com/v0nJKcf.jpg") It seems to show my Ubuntu at "nvme0n1p6". I selected that, clicked ok and now I have [this output]("http://i.imgur.com/BpR1diC.jpg").

Please help. I only wanted a larger mouse cursor... &#55357;&#56834;

---

### Post by vetmawd on 2020-01-10
[B]I was able to fix the problem!

[/B]I took a risk and decided to just run fsck, reinstall grub etc. in rescatux. I ran that, but still couldn't boot afterwards.Then I activated UEFI secure boot in the BIOS and booted into the newly created grub. It launched Ubuntu and everything worked again.

I have no clue why it suddenly needs UEFI secure boot. I have always had this option turned off before. Maybe an ubuntu update made this mandatory? I remember a few days ago I got some intel update from ubuntu's automatic update which I've installed. Maybe it put in some new firmware that made secure boot mandatory? Either way. This fixes the problem and somehow even the mouse pointer works now.

---

### Post by mastablasta on 2020-01-10
did you maybe run some boot repair? can you reformat the efi parittion and set a boot flag on it?

not sure how but the reboot seems to have corrupted some files or worse destroyed the partition table (i had that once on windows XP). i don't know who you restore partitions in this case, especially since you have UEFI install and dual boot. the windows have some tool for the NTFS partition to be recovered without reformat (as i remember it's proprietary).

this looks very similar situation but is not a dual to as i understand: 
[https://interworks.com/blog/smatlock/2015/02/13/restore-damaged-or-corrupted-linux-partition-table/](https://interworks.com/blog/smatlock/2015/02/13/restore-damaged-or-corrupted-linux-partition-table/)

---

### Post by vetmawd on 2020-01-10
> **mastablasta said:**
> did you maybe run some boot repair? can you reformat the efi parittion and set a boot flag on it?

not sure how but the reboot seems to have corrupted some files or worse destroyed the partition table (i had that once on windows XP). i don't know who you restore partitions in this case, especially since you have UEFI install and dual boot. the windows have some tool for the NTFS partition to be recovered without reformat (as i remember it's proprietary).

this looks very similar situation but is not a dual to as i understand: 
[https://interworks.com/blog/smatlock/2015/02/13/restore-damaged-or-corrupted-linux-partition-table/](https://interworks.com/blog/smatlock/2015/02/13/restore-damaged-or-corrupted-linux-partition-table/)

Thanks a lot for your help! I was able to fix it as laid out in my second reply.

It seems really strange to me. Freezes aren't uncommon I had them sometimes with GIMP before. But never did it affect my system to this extent. I'm convinced it has something to do with the intel update that I installed a few days ago. I never needed to run UEFI in secure boot mode before.

---

### Post by oldfred on 2020-01-10
Newer Dell can update UEFI from within Ubuntu.

And UEFI update resets some, but not all UEFI system settings. With old BIOS all settings were reset to defaults.
So you may have had an update & it reset UEFI setting. Perhaps turning on UEFI Secure Boot and then you had conflict that your grub & kernel were not the Secure Boot versions. Fixes then may have added Secure Boot versions?

---

