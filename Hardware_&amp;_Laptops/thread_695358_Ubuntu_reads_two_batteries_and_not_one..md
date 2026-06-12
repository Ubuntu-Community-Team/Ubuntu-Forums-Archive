---
title: "Ubuntu reads two batteries and not one."
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by jakey21 on 2008-02-12
Hello, I'm using Ubuntu 8.04 and when i installed it it shows that i have two batteries under Gnome Power Manager.  This is kinda weird because when i had 7.10 it only showed one battery.  I only have one battery in this laptop. Im not sure if theres 2 different cells that its showing there being charged. But if anyone knows how to make this show one or if its supposed to show 2 batteries that would  be very helpful. thanks very much for your time.


ps. when i just restarted my computer after doing an update it shows 2 different kernels on the grub boot selector screen. Ones Kernel 2.6.24-7 plus other thing that comes with that. then the second ones Kernel 2.6.24-5 plus the extra thing. Then theres the memtest selection and also the 2 windows vista.  could this be why its showing two batteries because theres two different kernels?

---

### Post by Existentialist on 2008-02-13
I'm not sure why it would change and show two batteries, but the current release is still an alpha release so it may be a bug that will still be worked out.  As for the kernels, 2.6.24-5 is the older kernel which has since been updated to 24-7.  This would not be the reason for showing two batteries though.  If you want the older option removed you can run

sudo apt-get autoclean

This should remove the old kernel image and headers.  Obviously don't do this until you have booted the new kernel and are sure it is stable with your system which it should be.

---

### Post by LucaTNT on 2008-02-15
Same issue here, but kernel 2.6.24-7-generic, on feisty and gutsy only one battery was shown.
The "fake" battery is always 100% charged, while the other discharges as usual.

It's also strange that in /proc/acpi/battery/ there's only one battery! I this error is only due to KDE/GNOME monitor (I'm running KDE).

---

### Post by jakey21 on 2008-02-15
alright thanks. one battery was always 10% less than the other.  i just reinstalled using 7.10 and didnt have any problems. im just messing around trying to find a Linux OS that is good for laptops, very energy efficient and supports all the drivers or most of the drivers in my computer which are INtel.  I also want it to look pretty nice but time can heal that too.  if you guys know any that are good for INtels it would be great. thanks for all the help and the replies.

---

### Post by Yellow Pasque on 2008-02-15
> trying to find a Linux OS that is good for laptops, very energy efficient and supports all the drivers or most of the drivers in my computer which are INtel.
I think you'll be happiest with (K)Ubuntu once you get it set up right.

What are your issues with Gutsy? It supports the latest Intel hardware fairly well. You may need to update your ALSA if you're having sound issues, but I have a script that makes that process easy (ask if you need it). The video should run great with the 'intel' video driver, and here is a post I made to guide people with G965 chispets (GMA X3x00 graphics) or later who want to run Compiz.
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

