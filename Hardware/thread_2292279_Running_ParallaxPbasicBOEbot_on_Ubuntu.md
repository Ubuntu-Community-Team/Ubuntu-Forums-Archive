---
title: "Running Parallax/Pbasic/BOEbot on Ubuntu"
date: 2015-08-26
forum: Hardware
---

### Post by CorsairTrumpet on 2015-08-26
After much reading and searching I have found my solution and would like to share it with anyone else who's looking.

I have a Parallax basic stamp 2 micro-controller ([www.parallax.com](www.parallax.com)).  
I run Ubuntu 15.04 on a number of platforms (classroom set of hodgepodge machines to make a 'lab' for robotics).

 I discovered that Chrome has an extension which will compile the code and is maintained by Parallax ([https://chrome.google.com/webstore/detail/parallax-ide/djbdelcnligmaaddjeenddjodmiaoffo?hl=en](https://chrome.google.com/webstore/detail/parallax-ide/djbdelcnligmaaddjeenddjodmiaoffo?hl=en)). However I was not able to access the device through the usb/serial port.

Steps to solution:
1. Ensure Chrome and Parallax extension are installed
2. Open terminal:
3. type: ls -al /dev/ttyUSB0  (Where ttyUSB0 is the location of your usb or serial to usb converter.)
4. type sudo gpasswd -a *yourusername* dialout

That simple.


I also found this tread somewhat helpful ([http://ubuntuforums.org/showthread.php?t=1523814](http://ubuntuforums.org/showthread.php?t=1523814)) but had issues with the link to bugs2.winehq.org file

---

