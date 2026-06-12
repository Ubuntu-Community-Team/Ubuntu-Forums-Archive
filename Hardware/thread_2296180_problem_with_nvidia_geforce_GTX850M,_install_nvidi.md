---
title: "problem with nvidia geforce GTX850M, install nvidia-current, now Ubuntu doesnt start"
date: 2015-09-24
forum: Hardware
---

### Post by marilia15 on 2015-09-24
I have Ubuntu 14.04 and I had black thick frames around each window and menu in Ubuntu, in addition the terminal was totally black because of this graphic problem, but the desktop was fine and also navigation on internet. 

So I decide to follow some instructions from forums:
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
-----------------------------until this moment, nothing new happened, problem not solved, same black frames.
sudo apt-get install nvidia-current

Now, Ubuntu doesn't start. Also I can not open a virtual terminal with Ctrl+Alt+F1. I am trying to fix this with the Ubuntu recovery mode, however I can not enable the wifi, and any apt-get install or apt-get purge gave me the error about the only-read blocked file /var/lib/dpkg/lock.

How can I solve it? Thanks in advance.

---

### Post by Bashing-om on 2015-09-24
marilia15; Well,

We can try. A terminal interface is a must.
Let's try this and see if NetWorking is available .
Reboot to the grub boot menu, with the latest kernel selected press the 'e' key for edit mode -> boot parameters screen.
In this screen arrow down to the line starting with linux, and arrow across to the terms "quiet splash" replace these terms and all after with the term "text" - without the quotes.
key combo ctl+x to continue the boot process to terminal TTY1.
Log in at this terminal with your credentials - no response at all to the screen when password is entered, enter password blindly and hit the enter key .
Once logged in what returns from terminal command:
```

ping -c3 ubuntu.com

```
IF we can activate the terminal and we have internet access. Then we can work to remove the broken graphic's driver and properly install another .

[INDENT][INDENT]All in the process
[/INDENT][/INDENT]

---

