---
title: "Problem with Nvidia beta driver on 8600gts"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by Budgetperson on 2007-06-07
Hi All.

Just built new pc, and I am having trouble with 3d acceleration on my Nvidia 8600gts. I downloaded the beta driver from Nvidia (100.14.06). This is what has happened so far - 

1. I try to do sudo sh NVIDIA-Linux-x86-100.14.06-pkg1.run , but it says I have to leave x, so I logoff and select "Failsafe Terminal" for my session and try to do it there, and I get the same error message.  

2. Go back to GUI, do sudo /etc/init.d gdm stop, it gets me to text, but no terminal!

So what do I do to install the driver?

Stumped.
Budgetperson

---

### Post by logos34 on 2007-06-07
Like this:
[B]
CTRL+ALT+Del F1[/B]

This drops you to the  CLI.

Enter user name, pswd

Then,
[B]
sudo /etc/init.d/gdm stop[/B]

cd over to the directory with the downloaded beta driver:

Ex:
**cd Deskto**p

**ls**

Your driver should show up.

**sudo sh NVIDIA-Linux-x86-100.14.06-pkg1.run**

This launches the interactive installer.

If it complains about the runlevel, just tell it to ignore (although you shouldn't get this unless in recovery moder/init1), OK everything and away you go.

Oh and make sure **build-essential gcc xserver-xorg-dev pkg-config** packages are installed beforehand.

At the end allow nvidia-xconfig to write your xorg file.

Good luck! Hope it works for you.

---

### Post by tonester on 2007-06-09
Worked for me - Thanks!

---

