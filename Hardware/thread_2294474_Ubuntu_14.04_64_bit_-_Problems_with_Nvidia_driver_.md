---
title: "Ubuntu 14.04 64 bit - Problems with Nvidia driver on Nvidia GeForce G100"
date: 2015-09-11
forum: Hardware
---

### Post by bigblackcar on 2015-09-11
Hi, I'm using Ubuntu 14.04 with a GeForece G100 and Nvidia Drivers.
I'm getting random crashes of Xorg, with no useful information. The crashes sometimes lead me back to the login page, sometimes I need to reboot the computer from the terminal.
The error message is: "Xorg crashed with SIGABRT".
I was thinking of upgrading the Nvidia drivers, because the official Ubuntu package provides 340.76 (which I currently have installed), whereas the Nvidia drivers site has a newer version: 340.93.
What do you suggest?
Should I manually install 340.93? Should I just follow Nvidia's installation instructions? Am I at risk of random crashes? 
Is there a way to get 340.93 from the Ubuntu repositories? And how?
Or would you suggest to upgrade to a newer version of Ubuntu, that maybe uses newer drivers by default? I was originally planning to wait for 16.04 before upgrading...

This is a computer I use for work, so I need the most secure option.
Any suggestions? Thanks in advance.

---

### Post by yuriy-feldsherov on 2015-09-11
Hi. Try connecting ppa: graphics-drivers.
And do the installation:
> 
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt-get install nvidia-340 nvidia-settings


---

### Post by bigblackcar on 2015-09-11
The installation worked. Thank you very much.
In the next days, I'll see if the random crashes stop.

---

