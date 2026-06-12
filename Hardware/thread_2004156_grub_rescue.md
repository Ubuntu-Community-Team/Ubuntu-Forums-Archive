---
title: "grub rescue?"
date: 2012-06-15
forum: Hardware
---

### Post by korben88 on 2012-06-15
I have ubuntu installes on sony vaio, no other os.

Just updated to newest version, and after reboot I get:
error: out of disk.
grub rescue>

I dont know what happened or how to fix it. Any help is appreciated!

Thank you

---

### Post by drs305 on 2012-06-15
korben88,

The simplest thing to try is to boot an Ubuntu LiveCD and install the Boot Repair app. Select the recommended repair and see if BR can fix your system's problem.

If it can't, you can run the 'boot info script' from within the app and post the contents of the file it generates. That will tell us a lot about what might be happening with your system.

A link to Boot Repair is in my signature line.

---

### Post by korben88 on 2012-06-15
Thank you for the reply. Just so im clear, I need to make an ubuntu boot disk and

 boot from it. Then instal the boot recovery?

---

### Post by drs305 on 2012-06-15
Are you running Ubuntu/Linux at the moment? If so you can just install BR from where you are.

If you can boot into Linux, Boot Repair should be able to help. You can use another installation, the CD, a bootable USB or Boot Repair, which  has its own bootable CD as well.

---

### Post by korben88 on 2012-06-15
I cannot boot into any os on my laptop, i'm posting from my phone.
I'll need to go to a friends to make an ubuntu disk or a repair disk.

---

### Post by korben88 on 2012-06-16
Okay, So I downloaded the boot repair iso and burned it to disk, and went into the bios on my laptop to set the boot order to boot from usb diskdrive (my internal cd drive doesn't work.

When I reboot though it still just gets the same thing
error: out of disk.
grub rescue>

what to try next?

---

### Post by drs305 on 2012-06-16
Did you run the "recommended repair"? If not, please do so.

If you did, next try going to the advance options and tick the ATA option. 

If that doesn't work either, please run the boot info script and post the link it generates.

---

### Post by korben88 on 2012-06-16
I didn't even get that far, when I rebooted it was went to the same error screen. I don't think I made the disk right though. I just burned the iso to a dvd, but didn't make it bootable. I'm having someone make me a bootable disc though and will try again.

Thank you for your help and patience!!!!

---

### Post by korben88 on 2012-06-19
Okay, so I got the disk, and booted up. It came to a window that said Boot-Tepair-Disk and gave me the options of
32 bits system
64 bits system
32 bits system (failsafe)
64 bits system (failsafe)
memory test
help

I tried using all of the first four, but they all resulted in a weird page that kept counting and saying error or failed command.

I let it sit for 30-40 minutes, and it just kept repeating the same things over and over and the counter kept going up

I never got to a page to choose recommended repair


What should I do from here?

---

### Post by YannBuntu on 2012-06-19
Boot-Repair-Disk is based on Debian stable, which has quite old drivers.

Please try [Ubuntu-Secure-Remix]("https://help.ubuntu.com/community/UbuntuSecureRemix"), which is based on Ubuntu 12.04.

---

