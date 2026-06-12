---
title: "Problem installing Asus Zenbook 14 UX431FN"
date: 2020-07-31
forum: Hardware
---

### Post by neti-treves on 2020-07-31
Hi,
I'm trying to install Xubuntu in dual boot on an Asus Zenbook 14 UX431FN.

I got the Live USB version to run only in sage graphics mode. It started automatically a files check but then I could press ESC and the graphic server started. I've installed Xubuntu and everything seemed working fine.

However, now the safe graphics mode doesn't work anymore.
If I choose "Ubuntu" I only have a dark screen.

I've tried the following solutions:
- advanced options &#8594; recovery mode. It only shows me a menu where I updated/upgraded everything, but I can't start the GUI
- I booted with ```
nomodeset noacpi acpi=off
```, but it doesn't work either. It stops with a dark screen and the cursor in the top left corner. However, in this case all the other shells work perfectly (Ctrl-Alt-F_). 
- I followed the advice in this post: [https://ubuntuforums.org/showthread.php?t=2420705](https://ubuntuforums.org/showthread.php?t=2420705) installing manually the binary file for 1920x1080. But it didn't work, same results.

I guess the problem is the Nvidia graphif card MX150.
I installed nvidia-drivers-440 as suggested, but with no results.

What can I do?

Thanks!

---

