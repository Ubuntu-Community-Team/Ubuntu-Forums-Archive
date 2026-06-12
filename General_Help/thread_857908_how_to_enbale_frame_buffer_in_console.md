---
title: "how to enbale frame buffer in console?"
date: 2008-07-13
forum: General Help
---

### Post by David Shen on 2008-07-13
Hi,

I have followed the thread [https://help.ubuntu.com/community/ConsoleFramebuffer]("https://help.ubuntu.com/community/ConsoleFramebuffer")to modify my system. But I still cannot have the frame buffer enabled...

If I add vga=ask in the grub configure file, I can only see some options like 80x60, 80x25...no 1024x768.

Can any one help? I am using Ubuntu 8.04 LTS

---

### Post by David Shen on 2008-07-13
OK, I got it :)

I worked with Gentoo for a while, and in Gentoo, if I add vga=ask, it will provide all the available options on startup. But in Ubuntu, you can only provide high resolution options directly. The 'ask' option will never give you them. And it looks like that the numbers used in Gentoo is also different from that is used in Ubuntu. Are they really the same mod?

---

