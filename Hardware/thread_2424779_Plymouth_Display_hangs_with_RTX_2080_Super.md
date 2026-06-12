---
title: "Plymouth Display hangs with RTX 2080 Super"
date: 2019-08-14
forum: Hardware
---

### Post by souparnoa on 2019-08-14
Hi all,

I have a Ubuntu (16.04 LTS) machine which is dedicatedly used for scientific calculations. Has a Xeon E5 2620@2.00GHz processor with 64 GB DDR3 1866MHz memory on a X79 generic MoBo (BIOS- American Megatrends).

I have two gpus right now- a 1050Ti OC and a 1060 OC with 1050Ti being the primary display gpu. It was running fine.

I bought an RTX 2080 Super recently and tried to install it in the place of 1050Ti. The machine was booting successfully and hanged just after showing "Starting Show Plymouth Display" etc.

I searched in the internet for the possible solutions and found out the GRUB edit solution. I entered into GRUB and removed "quiet splash" from the linux line. The machine booted successfully into command prompt. But, whenever I'm trying to restart or start lightdm, it gets back to the same place.

I don't have a Xorg.conf file in my directory.

Can anyone solve it, please?

---

### Post by Autodave on 2019-08-14
What Nvidia driver are you using and where did you get it from?

---

### Post by souparnoa on 2019-08-14
I am using 418.39 from official site with CUDA 10.1...

---

### Post by Autodave on 2019-08-14
You need the 430.40 driver: that is the newest one and (I believe) the only one that supports the Super card.  You should be using the repository for the driver: you shouldn't be using the driver from the website.

---

### Post by souparnoa on 2019-08-14
Let me try... I'll post the updates here...

---

### Post by Autodave on 2019-08-14
You are probably going to have to remove what you installed already.  Use this command:
sudo apt purge nvidia* 
Now you can install from the repository.

---

### Post by joris_donders2 on 2019-08-16
First boot in nomodeset (press e in grub and edit the line " quiet splash"  into "nomodeset" / boot the system) 

normally in updates/setting/ tab extra drivers  (if you wait a little) an automatic respons will show for your nvidea driver choose NOT the open source versions: the are still buggy on some hardware.

---

### Post by souparnoa on 2019-08-16
Yes, installing 430.40 worked...

But, when I tried with 16.04.1 which I had in my machine, the repository didn't show a 430.40 version, it showed only 430.26 which does not support the RTX 2080 Super as suggested here and also I verified from the NVIDIA website.

What I did as follows:-

1. Upgrading to 18.04.1
2. sudo apt-add-repository ppa:graphics-drivers . This repository has the 430.40 version.
3. sudo apt update
4. sudo apt install - put the file names or with 430* here.
5. It took care of the rest.

Now install CUDA from repository. It's pathetic that 10.1 is yet not in there. I had to install 9.2 which works fine with GROMACS-2019.

**IF ANY GROMACS USER IS HERE**

You had to downgrade your gcc compiler first installing gcc-6 and then using update-alternatives. GROMACS 2019 yet does not support the latest compilers.

---

