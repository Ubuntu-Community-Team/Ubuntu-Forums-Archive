---
title: "Hardy does not recognize hp pavilion zu1175 docking station"
date: 2008-06-22
forum: Hardware
---

### Post by zeroandone on 2008-06-22
The Xubuntu Live CD of Hardy can detect my HP Pavilion zu1175 laptop's docking station and I got Xubuntu 8.04 installed without a problem. But the problem is after the installation, my laptop failed to reboot with the docking station on. Now, I can only use my laptop without the docking station, which means I don't have DVD-ROM or CD-RW ROM.

Can anyone help me?

Thanks,

Jeffrey

My Old Laptop:
CPU: PIII 700
RAM: 384MB
Hard Drive: 20GB
DVD-ROM, and CDRW on the docking station.

---

### Post by inportb on 2008-06-22
What does "failed to reboot" mean, specifically?

---

### Post by zeroandone on 2008-06-23
I found out that Xubuntu DOES boot up with the docking station on, but it does it after a long process with numerous error messages. It takes about 15 minutes to boot up Xubuntu, and after login, Ubuntu still does not detect the docking station. Here is what happened in details:
1. Xubuntu gets stuck at the splash screen stage for about 3 minutes
2. Xubuntu switches to the text mode with a lot of error messages, for example:
Load Hardware Drivers...
[66.685784]: ata3.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[66.XXXXXX]: ata3.00 cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
[66.xxxxxx]: ata3.00 status: {DRDY}
then the same errors repeat many times with different [xx.xxxxxx] in front of it. Then it comes to another stage like this:
Load Manual Drivers...
the errors are the same as above with different [xx.xxxxxx] in front of the errors.
3. It takes about 12 minutes to finish the step 2, then the login screen appears.
4. After login, Xubuntu does not show DVD-ROM or CDRW which are in the docking station.

Because the step 2 takes about 12 minutes to finish, I used to think the boot process failed, and just removed the docking station. Without the docking station, the boot process only takes a couple minutes to finish.

Please help,

Jeffrey

---

### Post by zeroandone on 2008-06-23
inportb,

With the error message that I have posted, will you be able to help me?

Thanks,

Jeffrey

---

### Post by zeroandone on 2009-03-24
Finally got it fixed by adding "irqpoll" in my boot menu.

---

