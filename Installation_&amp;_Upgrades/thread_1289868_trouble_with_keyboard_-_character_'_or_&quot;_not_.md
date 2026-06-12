---
title: "trouble with keyboard - character ' or &quot; not showing up; have to key twice"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by nguyen4062 on 2009-10-12
Hi,

Please offer me some solution once i installed new Ubuntu server/client. Keyboard key ' or " not showing up when i press it once.  I have to press it twice for it to show up on screen.  How to fix this weird thing, i know that the keyboard is working normal.  Does this mean linux did not recognize the key or something wrong with keyboard layout during the installation. Thanks so much:(

---

### Post by prshah on 2009-10-13
> **nguyen4062 said:**
> Keyboard key ' or " not showing up when i press it once.  I have to press it twice for it to show up on screen.

Check your keyboard layout; you need to set it to US. I have seen this problem when the layout is Arabic <?>, I think, can't exactly remember.

For exact steps, post the version and type of Ubuntu you are using; is it server or client (desktop)?

---

### Post by nguyen4062 on 2009-10-13
Hi,
I am using Ubuntu server version 8.04.1 LTS. Thanks and tell me the steps to fix this problem. :(

---

### Post by prshah on 2009-10-13
> **nguyen4062 said:**
> Hi,
I am using Ubuntu server version 8.04.1 LTS. Thanks and tell me the steps to fix this problem. :(

After logging in, give the command```
sudo dpkg-reconfigure console-setup
``` and select the correct layout, language, encoding etc from the options available.

---

