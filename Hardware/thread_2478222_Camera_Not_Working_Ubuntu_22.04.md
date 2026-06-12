---
title: "Camera Not Working Ubuntu 22.04"
date: 2022-08-20
forum: Hardware
---

### Post by salambe19 on 2022-08-20
I had installed Ubuntu by removing Windows from my laptop and my camera stopped working. Please resolve this issue. I need camera urgently.

Output for lsusb:

> 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e300 Qualcomm Atheros Communications QCA61x4 Bluetooth 4.0
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by QIII on 2022-08-20
If you ask a question and leave the community to guess at the details of your hardware, you will not get much help.

---

### Post by salambe19 on 2022-08-20
I have updated the post. Sorry I am a new user of Ubuntu and I really do not know much. Anything else do you want to see?

---

### Post by QIII on 2022-08-20
What is the make and model of your machine?  What camera is included?

---

### Post by salambe19 on 2022-08-20
Here is the make and model of my machine: [https://ibb.co/R9QqBvZ](https://ibb.co/R9QqBvZ)

<large image removed>

---

### Post by QIII on 2022-08-20
Please do not include large images in your posts.  Some of our users work from cell phones, some have slow connections and some pay for data use in excess of their plan limits.  If you need to include an image, use the attachment facility provided by the paperclip button, which will insert an expandable thumbnail a user can choose as they wish to expand.

In this case, an image was not a good choice in any case.  When presenting terminal commands and their results, please copy and paste the terminal content between code tags provided by the # button.

---

### Post by salambe19 on 2022-08-20
Sure, I will do the necessary changes.

---

### Post by salambe19 on 2022-08-20
Output: 
>  
sudo dmidecode -s bios-release-date
01/15/2021 


> 
sudo dmidecode -s baseboard-product-name
LNVNB161216 


> 
sudo dmidecode -s baseboard-manufacturer
LENOVO 


> 
sudo dmidecode | less | grep Version | sed -n '2p'
Version: E8CN27WW 


> 
sudo dmidecode | less | grep Version 
    Version: AMD Athlon Silver 3050U with Radeon Graphics   
    Version: E8CN27WW
    Version: IdeaPad 3 15ADA05
    Version: SDK0Q55724WIN
    Version: IdeaPad 3 15ADA05
 

> 
v4l2-ctl --list-devices
Iriun Webcam (platform:v4l2loopback-000):
                        /dev/video0 


---

