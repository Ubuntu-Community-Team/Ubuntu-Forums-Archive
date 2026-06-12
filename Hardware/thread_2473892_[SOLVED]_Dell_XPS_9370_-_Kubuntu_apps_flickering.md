---
title: "[SOLVED] Dell XPS 9370 - Kubuntu apps flickering"
date: 2022-04-17
forum: Hardware
---

### Post by ftirapelle on 2022-04-17
Dell XPS 9370 - Kubuntu apps flickering

Hi,

about 2-3 weeks on all Kubuntu applications, when I hover the mouse over menu items, I notice a flicker (see picture).

If I start a Windows WM within kubuntu, the Windows apps work correctly.

Can anyone help me?

Thanks

Kubuntu 20.04.4 LTS

Kernel version: 5.4.0-107-generic

```
main@mylaptop:/home# lspci 
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
```

---

### Post by him610 on 2022-04-18
Naughty ftirapelle, 
> main@mylaptop:/home# lspci 
Your prompt line indicates you are using root to run routine commands that can be run from the user account. Suggest you exit from root and rerun the command.
Bad things can happen to your installation when you perform operations as root.

---

### Post by ftirapelle on 2022-04-22
Hi 

here the result if I run the command with my user

> 
ft@mylaptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)


---

### Post by #&amp;thj^% on 2022-04-22
Go into System Setting > Hardware > Display and Monitor > Compositor and change the tearing prevention to "Full screen repaints"

As an alternative, in the same menu change the compositor to XRender

---

### Post by ftirapelle on 2022-04-22
Thanks it solved by setting "XRender"

---

