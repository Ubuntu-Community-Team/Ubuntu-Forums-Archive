---
title: "KB&amp;M not working after Altera Quartus USB Blaster rules.d changes"
date: 2013-04-15
forum: Hardware
---

### Post by eljaywasi on 2013-04-15
Yesterday I got the Altera Quartus II Web Edition 12.1 software working on my laptop with installed so I could play with my DE1 board. I'm running an Ubuntu 12.04 based distro (Mint Nadia 14 64bit). To get the USB Blaster to work I had to [follow the example here]("http://chehsunliu.wordpress.com/2013/01/15/install-altera-quartus-12-1-in-ubuntu-12-04/") (steps 5 and 6) and then it worked and I could program and write to my fpga to my heart's delight... until I booted up this morning and found that the keyboard and mouse (trackpad actually) do not work at the login screen anymore. I tried the [solution posted here]("http://forums.linuxmint.com/viewtopic.php?f=90&t=123409&p=697421#p697421") to see if the problem is unrelated to the USB Blaster rule changes but no luck. 


As I mentioned I followed steps 5 and 6:


I created a file at /etc/udev/rules.d/ and called it 51-usbblaster.rules


```

# Altera USB-Blaster rule to set mode to 666.
SUBSYSTEM=="usb",
ENV{DEVTYPE}=="usb_device",
ATTRS{idVendor}=="09fb",
ATTRS{idProduct}=="6001",
MODE="0666",
NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}",
RUN+="/bin/chmod 0666 %c"

```


```

sudo udevadm control --reload-rules

```


Note that I made the changes suggested in the comments: *ATTR**S*** instead of *ATTR*


That's the only significant change I made yesterday so that's probably the culprit.


Now that the mouse and keyboard don't work, I suspect fixing it is going to be a little difficult. I tried plugging in an external usb mouse and keyboard but they didn't work either. 
Any ideas what I do now? How can I revert the changes or change the rules so that they will still work for my USB Blaster but not conflict with my m&kb?
Thanks!

---

### Post by eljaywasi on 2013-04-15
Solution:


Turns out that the code on Step 5 of the tutorial has to be on a single line in the 51-usbblaster.rules file. The web formatting makes it appear as multiple lines, but you must correct it when you create your file. 


Now, if like me you've already made this mistake to undo it you must:


1. Boot into recovery mode. Hold the shift key after your bios splash to get the grub menu if youre running a single boot system like I am and don't usually see the grub menu
2. Once you log in as root your filesystem is mounted as read only. You must mount it as read/write if you want to fix the rules file, so enter the command ```
mount -o remount,rw /
```
3. Edit the rules file with ```
sudo nano /etc/udev/rules.d/51-usbblaster.rules
``` and move all the code onto one line (the comment can stay on its own line, obv)
4. Save and exit (ctrl-x, y)
5. Reboot ```
reboot
``` and that should be it!


My system is working fine now and so is my Quartus II software; I can write to my DE1 no problem.

---

