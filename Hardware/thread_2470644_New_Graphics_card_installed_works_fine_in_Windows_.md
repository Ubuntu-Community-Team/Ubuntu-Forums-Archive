---
title: "New Graphics card installed: works fine in Windows 10 but major errors in Ubuntu"
date: 2022-01-06
forum: Hardware
---

### Post by makem2 on 2022-01-06
I have just installed an ASUS TUF Nvidea Geforce RTX 3060 OC graphics card in a desktop machine which was using the Processor GPU previously.

I am using Ubuntu 21.04.

After installing the card I went straight to Windows from grub and am currently setting up the drivers because I thought it more likely to work immediately to show that the card was installed and working ok. (First time I have installed such a monster card!)

I rebooted and chose ubuntu from grub and received the following errors:

[FAILED] Failed to start Detect the available GPUs and deal with any system changes.
[FAILED] Failed to start Light Display Manager.

I did see a mention of Nouveau during the boot.

Cursor blinking, no mouse, no keyboard. Only way out is hard reboot. I am unable to get any information to assist in this post.

Can anyone assist

---

### Post by Bashing-om on 2022-01-06
makem2; Hello

Let is do suppose this is a graphic's card issue.
Try to boot the system with a "nomodeset" boot parameter:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If able to boot then we can discuss what options may be available to you.

[INDENT]it is in the process
[/INDENT]

---

