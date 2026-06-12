---
title: "Is my Harddrive busted?!"
date: 2011-12-25
forum: Hardware
---

### Post by xxhopingtearsxx on 2011-12-25
I can't even use my LIVE CD to install Ubuntu.
Here's my issue.
I installed Windows 7, and I wanted to recover deleted files from my entire harddrive. I figured it'd be easy to delete the giant 300GB Ubuntu 11.10 ext4 partition that I had, because even when I used a program to mount that partition, I still couldn't use Recuva to recover deleted files that I had before I installed Ubuntu.

Well, I went to delete the Partition in Windows 7's partitioning tool. The program froze. I decided to restart. It got stuck on the restarting screen. So I turned off my computer and turned it back on. What happened after that.. Windows 7 will not boot. It gets stuck at the startup screen. No login screen at all.

So, I decided to try to boot from Linux Mint, and I get an error saying "Panic occurred, switching back to text console". So then I tried Ubuntu. Same thing. So then I tried to install Debian. Gets stuck at a blue screen. So then I tried to use my Windows 7 install disc. It's stuck at the startup screen. So then in the boot loader, I clicked Startup Repair instead of going to start Windows 7 normally. Gets stuck at the startup screen.

So now I'm trying gparted LIVE CD, and I get an error I haven't gotten before.. I get "No Default or UI configuration directive found!" on the LIVE CD..

WHAT THE HECK HAPPENED? I need to use my laptop! I'm currently on my old laptop.. It's terrible. I'm worried. This is a new laptop. I don't want to take it anywhere, It seems I can't use LIVE CDs.. what's wrong!

PS: I have no flash drives and as far as I know, you can't boot from SD cards.

EDIT: My attempt to boot into Windows 7 in Safe Mode with Commpand Prompt gets stuck at /windows/system32/DRIVERS/disk.sys..

EDIT: I tried a LIVE CD with the hdd not in it.. the CD works.. so I think it's the harddrive, and I'm currently using my old laptop's harddrive on my new laptop.. Which only has 20GB of space left.. my other hdd had 300GB left. Glad to see the Ubuntu 11.04 installed here recognizes my drivers right away.

Any solutions to my hdd? Is it broken?

---

### Post by darkod on 2011-12-25
Did you try connecting the hdd to another computer with some sata-to-usb adapter or similar? Or if you have a desktop simply connect it with sata cables and see if it reads it.

But even if it reads it, recovering the data on it, both windows and ubuntu might be difficult.

---

