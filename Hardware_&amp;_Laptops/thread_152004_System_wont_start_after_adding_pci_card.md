---
title: "System wont start after adding pci card"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by slipk487 on 2006-03-29
after adding my ati radeon 9250 my comp will not start up does that mean that it is not supported

---

### Post by drummer on 2006-03-29
That card works, I have it.
At which point does the boot process stop/fail? More info is needed for anyone to help fix the problem.

---

### Post by slipk487 on 2006-03-29
it loads right up to the GUI screen and nothing else happens and do you have an integrated graphics card or just the radeon

---

### Post by drummer on 2006-03-29
I have a pci card, not integrated. Is this a new addition to the computer, ie. replacing a previous graphics card? If so, you probably have to just reconfigure xorg. When the comp boots up and fails to load X, switch to a vterm with Ctrl-Alt-F1 and login there. then run "sudo dpkg-reconfigure xserver-xorg" (without quotes) and follow the prompts. Most of it should be auto detected and it will create a new xorg.conf file, but check the driver, resolution and so on a correct before pressing next on each screen.

---

### Post by slipk487 on 2006-03-30
i have and integrated and pci video card and i had to reinstall ubuntu to fix errors in it and when i had the radeon in it installed and when i got to the point when the black screen whith text becomes the GUI screen it just sat there with a _ at the top left corner of the screen and i reinstalled it w/o the radeon and it install and booted up right

---

### Post by drummer on 2006-03-30
So you have integrated as well, try disabling the integrated graphics in the bios, as the 2 might be conflicting in sime way when setting up ubuntu.

---

### Post by slipk487 on 2006-03-30
dont know how to theres nothing about my intergrated card in the bios

---

