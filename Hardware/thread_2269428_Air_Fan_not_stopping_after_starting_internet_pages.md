---
title: "Air Fan not stopping after starting internet pages"
date: 2015-03-15
forum: Hardware
---

### Post by mohammed-moumen on 2015-03-15
Hello to all,

I need your assistance please to help figure out what is wrong with my Air Fan! I have Dell Inspiron 15R 5537 64 bits with 2 partitions : Ubuntu 14.04 LTS and Win7.

Lately the SAV have changed my Mother Card because of failures I got and these failures are solved but since I changed it when I start my laptop (either on Win7 or Ubuntu) after a while (at first it was immediately after launching the internet pages then I found a what looks like a solution which I will describe here after) the air Fan begins to run constantly and noisy! I tried to do some research and I found some tools that calculate the CPU heat degrees which I found very normal by the way (It was like a little bit higher than the minimum value It should have and lower to the max value), I also found a thread in some forum with what looks like a solution which I tried blindly  and here are the steps I did:

Fan speed is normalized by editing the line 
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
  in the grub configuration file found at */etc/default/grub* so that it reads 
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=!Windows 2012".
  Follow these steps to try this solution:

  
[LIST=1]
[*]Open a terminal, type *sudo gedit /etc/default/grub*, and press ENTER 
[*]Enter your login password and press ENTER (the password will not be displayed as you type it) 
[*]Edit the line,
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
  such that it reads, 
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=!Windows 2012". 
[*]Click "Save", wait a few moments for the file to save, then close the text editor. 
[*]In the terminal, type 
  sudo update-grub
  and hit ENTER 
[*]Finally, shut down your computer. Shut it down completely, so don't "restart" it.

I noticed that something has changed : before these steps the air fan get started immediately after launching an internet page, after these changes the time needed so the air fan has started is significantly more!

Can anyone help me please? 
[/LIST]

---

