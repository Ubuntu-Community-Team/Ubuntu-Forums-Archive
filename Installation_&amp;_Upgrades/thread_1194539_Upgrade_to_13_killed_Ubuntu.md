---
title: "Upgrade to 13 killed Ubuntu"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by IsmAvatar on 2009-06-22
I've been running ubuntu 9.04 ever since upgrading from 8.10, and it's been fine until just yesterday/today.

I upgraded Ubuntu kernel just yesterday (I think it was kernel, because the it went from version 11 to version 13). It seemed to go fine for the most part, but I had to fiddle with Grub because I had made some custom changes to rearrange the menu items, and it wanted to auto-generate the grub menu again. I manually merged the two, making sure that all the numbers and IDs were correct.

I then rebooted without a problem. Today, however, ubuntu started acting up. It booted fine, but X would have trouble showing certain applications, sometimes pausing for a minute while it tried to show it. The Update Manager also tried to run, but the password screen wouldn't display. I was running Firefox and Pidgin relatively fine. Then suddenly it crashed, and I got an ASCII-Graphics screen saying the X Server was having trouble, with an OK button. Pressing Enter had no effect, and it seemed unresponsive, so I pressed the power button for a soft shutdown and it shut down instantly. When I powered up, it tried to load ubuntu then started spewing errors.

Things like:
Buffer I/O error on device sda6, Logical block 2730059
and
bash: no job control in this shell

it also told me that fsck failed with error code 4 (which man tells me is "file system errors left uncorrected) and that I'd have to run it manually, and then gives me a terminal.
I type "fsck" and hit enter, and it starts checking the filesystem, then runs into problems and starts spewing more errors with numbers and such that mean nothing to me. One thing that kind of stands out is "[DRDY ERR]" whatever that means.
I rebooted into Ubuntu Recovery, and it loads Ubuntu and then seems to run fsck, spewing the same errors before dumping me at a terminal again.

Please help, I really want Ubuntu back. I'm using the dual boot Windows right now, and, although it works, it sucks balls...

-IsmAvatar

---

