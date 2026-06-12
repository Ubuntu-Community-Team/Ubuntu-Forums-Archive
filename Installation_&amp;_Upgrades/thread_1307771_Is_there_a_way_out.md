---
title: "Is there a way out??"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by drpain on 2009-10-31
Hi all let me first give you all the details:

Intel Q6600 Cpu 65nm, Updated BIOS to latest available
Biostar TP35D2-A7 Motherboard
Asus Ati 3870 Gpu
4GB of ram
1TB Seagate HDD
250GB Seagate HDD
80GB Seagate HDD
Leadtek Winfast 2000 TvTuner
Sony 16X DVD Writer
Ubuntu 9.04 Desktop AMD 64 and 9.04 Desktop I386.

I can't seem to install Ubuntu properly when ACPI is left on. When I run the setup and turn ACPI off in the F6 menu it installs and runs quite happily. If I boot and run the setup as is (ACPI ON), the pc freezes and I only see a flashing dash in the top left corner. 

I have a installation with ACPI off. And here in lies the problem. I like having my pc on at night and watching / listening to a movie to fall asleep. Once asleep routines are set to shut my pc off at a certain time for example 1am weekdays and 3am weekends. With the ACPI off this is no longer a option, as I have to physically switch the machine off. 

What I want to know is. Is it possibly a combination of BIOS settings causing the installation to freeze, and if so does anyone have a link to some resourses for basic BIOS settings for linux / ubuntu which I can go through to make sure it is set up properly??

Or a way of turing ACPI on after the installation if that is even possible.

Any and all help will be appreciated, I use Ubuntu on my work laptop and I would love to move away from Windows at home as soon as possible.

---

### Post by phillw on 2009-10-31
> **drpain said:**
> Hi all let me first give you all the details:

Intel Q6600 Cpu 65nm, Updated BIOS to latest available
Biostar TP35D2-A7 Motherboard
Asus Ati 3870 Gpu
4GB of ram
1TB Seagate HDD
250GB Seagate HDD
80GB Seagate HDD
Leadtek Winfast 2000 TvTuner
Sony 16X DVD Writer
Ubuntu 9.04 Desktop AMD 64 and 9.04 Desktop I386.

I can't seem to install Ubuntu properly when ACPI is left on. When I run the setup and turn ACPI off in the F6 menu it installs and runs quite happily. If I boot and run the setup as is (ACPI ON), the pc freezes and I only see a flashing dash in the top left corner. 

I have a installation with ACPI off. And here in lies the problem. I like having my pc on at night and watching / listening to a movie to fall asleep. Once asleep routines are set to shut my pc off at a certain time for example 1am weekdays and 3am weekends. With the ACPI off this is no longer a option, as I have to physically switch the machine off. 

What I want to know is. Is it possibly a combination of BIOS settings causing the installation to freeze, and if so does anyone have a link to some resourses for basic BIOS settings for linux / ubuntu which I can go through to make sure it is set up properly??

Or a way of turing ACPI on after the installation if that is even possible.

Any and all help will be appreciated, I use Ubuntu on my work laptop and I would love to move away from Windows at home as soon as possible.

Hi, firstly welcome !!

It's been a while since I was involved with acpi issues (mine works out of the box) .. However, This link should take you to some resources that should go some way to helping you ..

[http://ubuntuforums.org/showthread.php?t=1257361&highlight=phillw](http://ubuntuforums.org/showthread.php?t=1257361&highlight=phillw)

Do let me know how you get on.

Phill.

---

### Post by drpain on 2009-10-31
Thank you for the info,

I have made some headway but I seem to be stuck again.

I sat for the past two hours, just playing with the grub settings and BIOS. I noticed that there was one BIOS setting causing allot of problems. Execute a something. I will have to check. And then the only way grub will load is with either acpi=off or acpi=ht. 

At the moment it is set to acpi=ht. 

Some other good also came out of this. Ubuntu now sees all four cores and there is a noticeable difference. 

I am attaching my kernel log, but I don't know if it logged the boot crashes. If there is another log in specific you guys need to narrow it down please just specify.

---

