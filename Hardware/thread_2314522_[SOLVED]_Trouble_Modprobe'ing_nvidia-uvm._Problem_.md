---
title: "[SOLVED] Trouble Modprobe'ing nvidia-uvm. Problem with part of the &quot;Workaround&quot;"
date: 2016-02-21
forum: Hardware
---

### Post by Vitor_Nazario on 2016-02-21
Today, I came across a day fulfilled of PURGES and APTITUDE/APT-GET's.
I was trying to fix the problem of activating the nvidia-uvm.

I have a CUDA 6.5 already installed.
I updated my nvidia to 352 thinking that the 340 was with problems. 
But as you will see, it was a matter of activating components blacklisted by the bumblebee.


I run: 

sudo apt-get install bumblebee bumblebee-nvidia 

However, I decide to comment the following from file "/etc/modprobe.d/bumblebee.conf":
# Workaround to make sure nvidia-uvm is removed as well
#remove nvidia rmmod nvidia-uvm nvidia (commentted)

It was giving problems in my modprobe activation.
First of all, I do not know why, but I have to, always, run the optirun command with some process and, then,
execute sudo modprobe nvidia-XXX-uvm

EX: 
"sudo optirun glxspheres64 
sudo modprobe nvidia-352-uvm"

I think it is because bumblebee blocks some component that should be activated when optirun is executed.
Anyway, it worked for me and I hope can save some PURGE/INSTALL that everyone maybe be tired of executing.

Best wishes,

---

### Post by mörgæs on 2016-02-22
Thanks for posting.
If you mark the thread solved using Thread Tools there is a better chance that people will find it.

---

### Post by Vitor_Nazario on 2016-02-22
Thanks, maaaa friend.
I just checked it as you suggested.
Best wishes,

---

