---
title: "Customizing grub boot password prompt"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by FiberOptix on 2009-03-21
Hello,

I recently installed via alternate into encrypted LVM and now I would like to customize the boot password prompt. Anybody know how I can do this?

---

### Post by lemming465 on 2009-03-22
I think you'll have to recompile grub with a patch.  It doesn't appear to be something you can control from the configuration file.

---

### Post by FiberOptix on 2009-03-22
> **lemming465 said:**
> I think you'll have to recompile grub with a patch.  It doesn't appear to be something you can control from the configuration file.

Well thanks for the reply - I'll likely leave it since it's a cosmetic thing, but thanks very much for at least putting this issue to rest.

---

### Post by Herman on 2009-03-23
If you mean you want to set up a GRUB password, here's a link that should help you, [# password topsecret]("http://users.bigpond.net.au/hermanzone/p15.htm#password")

If you're talking about the luks (encrypted file system) password  I don't know.

If it's your Ubuntu login screen you want to change, I think I found your answer, take a look in this link and scroll down a bit, [HOWTO: Customize Ubuntu A-Z]("http://ubuntuforums.org/showthread.php?t=856190&highlight=login+customization") .
Look for [FONT=trebuchet ms][SIZE=3]*"Login Screen (gdm)",*[/SIZE][/FONT]I think that's probably the answer you're looking for. 

NOTE: You aren't restricted to only the 'Avio-GDM 0.9.2', although it is very nice. Take a browse around in [GDM Themes]("http://www.gnome-look.org/index.php?xcontentmode=150"), there are plenty to choose from. :)

---

