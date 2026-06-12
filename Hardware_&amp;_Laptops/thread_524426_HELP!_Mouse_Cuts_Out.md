---
title: "HELP! Mouse Cuts Out"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by SmartRoss on 2007-08-13
Hi, I am new to the forums.

In Ubuntu, after ~30mins of having the OS operational, my optical laser mouse cuts out. It has lights on it, and they stay on, so it is getting power from the PS/2 port. I can get around OK with the keyboard, but give it another ~15mins and it cuts out too. My only option is to then restart the computer with the button on the case. Any clues to what is going on?

---

### Post by Blindraven on 2007-08-13
What version of Ubuntu are you using?
What brand and model is your keyboard and mouse.
How is your keyboard and mouse connected to your PC: PS/2, USB, wireless, ...

Try the following:
1. Direct after gnome login open a terminal and enter the following command:
   $ cp /var/log/Xorg.0.log ~/Xorg.0.log
2. Wait until your mouse and keyboard stop working.
3. Open a terminal by pressing Ctrl-Alt-F1.
4. Enter the following commands:
   $ LANG=C
   $ cp /var/log/Xorg.0.log ~/Xorg.0.log_tmp
   $ diff -ns ~/Xorg.0.log ~/Xorg.0.log_tmp > ~/Xorg.0.log_diff-ns
   $ cp /var/log/dmesg ~/dmesg_boot
   $ dmesg > ~/dmesg
   $ diff -ns ~/dmesg_boot ~/dmesg > ~/dmesg_diff-ns
5. Attach Xorg.0.log, Xorg.0.log_diff-ns, dmesg_boot and dmesg_diff-ns to this thread.

---

### Post by SmartRoss on 2007-08-13
I am using Ubuntu 7.03. The mouse doesn't have a brand on it, and I don't have the original packaging. My keyboard came with my Gateway 2000 G6-233 which is about 13 years old. My keyboard and mouse connect to the ports with the respective symbols, which I believe to be PS/2 ports. I will try your technique.

---

### Post by SmartRoss on 2007-08-17
An error appears at the first command.

---

