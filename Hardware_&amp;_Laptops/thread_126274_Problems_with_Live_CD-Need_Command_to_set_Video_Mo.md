---
title: "Problems with Live CD-Need Command to set Video Modes from prompt"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by cosmic_nomad on 2006-02-06
I cannot boot into Gnome using the Ubuntu Live CD on my HP Pavilion ZD8000, it kicks me to the prompt.  I know the problem is the video modes and not detecting the display properly but I've fixed this in other versions of linux by setting the video driver to vesa.

[SIZE="4"]**Question: How to I configure the video modes from the Prompt?**[/SIZE]
I have tried setxconf and xorgconfg and neither are recognized commands

---

### Post by newuser111 on 2006-02-06
sudo dpkg-reconfigure xserver-xorg

---

