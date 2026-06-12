---
title: "help! looking to install nVidia GPU driver on 64bit ubuntu 11.10"
date: 2011-10-16
forum: Hardware
---

### Post by bwjp08 on 2011-10-16
Hey everyone,

First off, I should let anyone reading this know that I have been running linux for a couple months now, so I am somewhat still new to its differences from windows/mac. this problem was not noticed until I recently tried to use the HDMI out from my laptop.

After installing NVTV and attempting to run I was given the error message - "Fatal: No supported video card found"

This must mean that I need to install a driver, correct?

I'm currently running Ubuntu 11.10 64-bit on an HP HDX16 laptop, with a GeForce GT 130M. I'm trying to install the driver recommended from the nVidia site that will support my GPU. (Which is NVIDIA-Linux-x86_64-285.05.09.run)

I've tried using Alt + Ctrl + F2 to switch to the console, and tried to stop x-server with 2 different methods I  found online. init 3 & /etc/init.d/gdm stop. init 3 seems to do absolutely nothing and the latter method prompts me with a message saying 'gdm' not installed, use apt-get install to install it.

How can i install / configure the correct driver? (My guess is that if NVTV will open, the driver is functioning properly)

Any input will be greatly appreciated!
If anyone needs clarification on what I've stated above, please feel free to ask and I will do my best to show you what I am seeing on my screen.

Cheers!

---

### Post by Uuindouus on 2011-10-20
I followed these steps
open terminal >
type>
```
sudo service lightdm stop
```desktop will be kill 
press Ctrl+Alt+F1 your terminal will run again
type your ***<username***>
type your <***password>*** 
if you save the file in Downloads then type>
```
cd Downloads
```to be sure your file is there then type>
```
ls
``````
sudo sh <copy & paste the nvidia file name> 

```then nvidia-installer screen will appears 

wish you good luck

---

### Post by phendrome on 2011-10-21
Something else you might want to consider:

```
sudo apt-get install libgl1-mesa-dri-experimental
```

[Source](https://launchpad.net/ubuntu/oneiric/+package/libgl1-mesa-dri-experimental)

---

