---
title: "Ubuntu 10.10 problem with Nvidia Geforce 7100 /nforce 630i"
date: 2011-01-12
forum: Hardware
---

### Post by yans_fied on 2011-01-12
hello all!!
i have a problem with my onboard graphic card, nVidia GeForce 7100, i tried to install nvidia-glx-185 and i get some error, after i reboot, the ubuntu won't start and some times i get blank screen.

so.. what driver package should i use??? :confused:

---

### Post by yans_fied on 2011-01-13
no body can help me?? or just give me sugestion??

---

### Post by yans_fied on 2011-01-13
no body can help me?? or just give me sugestion??

---

### Post by Janoka on 2011-01-20
Hello, I have a Geforce 210 card, and I also encountered errors with drivers downloaded from Nvidia's site. In a forum I found a suggestion to use the XSWAT PPA, I think it is worth to try.
Open a terminal, and type the following to add the repository:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

then, when the repository added successfully, update and install the driver like this:

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

I hope this will help!
Good luck!

---

### Post by Janoka on 2011-01-20
Hello, I have a Geforce 210 card, and I also encountered errors with drivers downloaded from Nvidia's site. In a forum I found a suggestion to use the XSWAT PPA, I think it is worth to try.
Open a terminal, and type the following to add the repository:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

then, when the repository added successfully, update and install the driver like this:

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

I hope this will help!
Good luck!

---

### Post by Janoka on 2011-01-20
Hello, I have a Geforce 210 card, and I also encountered errors with drivers downloaded from Nvidia's site. In a forum I found a suggestion to use the XSWAT PPA, I think it is worth to try.
Open a terminal, and type the following to add the repository:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

then, when the repository added successfully, update and install the driver like this:

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

I hope this will help!
Good luck!

---

### Post by Janoka on 2011-01-20
Hello, I have a Geforce 210 card, and I also encountered errors with drivers downloaded from Nvidia's site. In a forum I found a suggestion to use the XSWAT PPA, I think it is worth to try.
Open a terminal, and type the following to add the repository:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

then, when the repository added successfully, update and install the driver like this:

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

I hope this will help!
Good luck!

---

### Post by pattykam on 2011-01-27
It works!!
Thank you for your help...

---

