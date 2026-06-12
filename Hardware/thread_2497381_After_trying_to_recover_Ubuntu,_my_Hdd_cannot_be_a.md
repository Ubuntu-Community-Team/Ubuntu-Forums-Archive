---
title: "After trying to recover Ubuntu, my Hdd cannot be accessed!!"
date: 2024-05-02
forum: Hardware
---

### Post by nonyg. on 2024-05-02
[COLOR=#0C0D0E][FONT=-apple-system][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]
Please help me saving my data on my hard drive. And please excuse me as I'm not an expert in Ubuntu but can follow instructions.[/FONT][/FONT][/FONT][/FONT][/FONT][/COLOR][FONT=-apple-system][FONT=inherit][FONT=inherit][FONT=inherit]

I have a lenovo ideapad 330 with 1 tera hdd that have dual boot of windows 10 and Ubuntu, Ubuntu is my main OS.

Last month I've encountered repeated problems while booting with the error "filesystem on /dev/sda1 requires a manual fsck" and by searching the problem I was able to solve it and it boots normally.

As Ubuntu 24.04 is out I thought it'll solve this problem for me so I did a clean installation of Ubuntu 24.04 along side windows 10.

Yesterday while using Ubuntu it suddenly freezes and didn't respond at all so I restarted it and choose the recovery mode, but it stuck again during that so I restarted it but it only gives me a blank screen.

I tried to reinstall Ubuntu, but gparted cannot find my Hdd at all, it gives the error "error fsyncing/closing/dev/sda: input/output error" with each partition on my hdd.

BIOS can still see my Hdd but Ubuntu installation can not. I tried to boot windows but I get the error "Default boot Device Missing or Boot failed".

My HDD partitions is as follows:

Sda1 swap partition 14 gb

Sda2 ubuntu OS 149 gb

Sda3 entertainment 781 gb

Sda4 work 722 gb

Sda5 backup 165 gb

Sda6 EFI boot 100 mb

Sda7 win10 30 gb

I don't understand now, is my Hdd dead?! But how can Windows tries to repair itself?

Could you please help me? I really need to get the Hdd fixed it contains all my data and stupidly I don't have a backup for it.

Please help &#65533;&#65533;


Update:

When I boot I can see the grub menu and When I try to enter the recovery mode of ubuntu it stuck at the first line: Loading Linux 6.8.0.31-generic


Second update:

I realized that it freezes quickly at any stage even at BIOS!! It freezes even at Just pressing F10!

Please help!! Is my Hdd dead?

[/FONT][/FONT][/FONT][/FONT]

---

### Post by TheFu on 2024-05-03
"He's dead Jim"   Ref:   [https://www.youtube.com/watch?v=MH7KYmGnj40](https://www.youtube.com/watch?v=MH7KYmGnj40)

Sorry.

Data recovery services for complex issues with spinning HDDs are $2000 and up.  They usually have to replace the disk controller manually. This assumes the platters are fine, which may not be true.

Learn the lesson.  If the data is that important, automatic, daily, backups are critical.  For a home environment, weekly automatic, versioned backups are still important.  Compared to the $40 cost of a 2TB USB HDD, the effort you will spend trying and failing to get anything back cannot compare.

---

