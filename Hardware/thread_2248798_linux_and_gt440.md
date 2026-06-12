---
title: "linux and gt440"
date: 2014-10-17
forum: Hardware
---

### Post by Mercury1946 on 2014-10-17
hi there. i had problems with booting ubuntu or any other distro since i changed my graphics card from nvidia gt8800 to gigabyte gt440. i asked for solution at linuxforums.org and one member gave me solution. i tried to boot it up with NOMODOSET option and got some progress. before that after choosing to run live cd of any distro it just stuck at black screen, no signals from graphics card to monitor. so yesterday i tried nomodoset, boot logo appeared and then it didn't boot as it should. i'm adding picture so you can see: 
[IMG]http://www.linuxforums.org/forum/attachment.php?attachmentid=5950[/IMG]
would really like some help, thanks in advance

---

### Post by grahammechanical on 2014-10-17
Do you get a Grub boot menu? Use recovery mode and at the recovery menu select Resume. That may load to a desktop using an open source video driver that Ubuntu uses as a fall back video driver. Once, at the desktop use Additional Drivers to change to another video driver.

I cannot give more detailed advice as I do not know which version of Ubuntu you are using. There are differences between Ubuntu 12.04 and 14.04 on how to do this.

As for using the live session disc, see section 6 - F6 Other Options and try nomodeset or a combination of options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You should not need to make nomodeset as a permanent boot parameter but just in case you need to, 

[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Regards

---

### Post by Mercury1946 on 2014-10-17
Okay, i will try as soon as i get home. I'm using 14.04 :) thank you very much. I now see picture is not loading when i'm on my phone, hope you can see it

---

