---
title: "Ati mobility and xgl, compiz etc..."
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by Marcusg_ on 2008-02-27
Hello,

I have a Compaq Evo N620c laptop. It has an ati gpu ("ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]").

It works OK with the default ati-driver setup chooses. But I want to use compiz and awn.
How do I get this working?

I tried to install xserver-xgl. After this I cannot login, if I don't create a file "~/.config/xserver-xgl/disable". After I log in from gdm, it tries to continue but returns soon to gdm.

I searched both this forum, and the web. But most of the results are for older Ubuntu versions (I have 7.10) and contain warnings that they're not good any more...

Is there any recent howto somewhere?

Thanks in advance.

---

### Post by divague on 2008-02-27
by default ati-driver you mean the one that is installed using restricted drivers manager? because that's the one that you have to use in order to get compiz working.

---

### Post by Marcusg_ on 2008-02-28
Hello,

The only thing the restricted drivers-manager finds is my modem.
My graphics card isn't there at all.

---

### Post by divague on 2008-02-28
Then you'll have to download the driver from ati's web site and install it manually. The newest driver works without xgl.

---

### Post by Marcusg_ on 2008-03-02
Do you have any url?
I only find drivers for newer ati-cards on their homepage.

---

### Post by divague on 2008-03-03
try installing the fglrx driver that is in ubuntu's repositories

$sudo apt-get install xorg-driver-fglrx

---

