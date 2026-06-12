---
title: "Hoary AMD64 Nvidia Question"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by brad.arth on 2005-05-14
To start off, I am new to linux, Ive searched the forums as best as I know how and cannot seem to find 'new' information on my question.

How can I install 64-bit drivers on my new Ubuntu system? 

Do I do apt-get nvidia-glx? is that the driver and is it 64-bit?

Thank you
[email]brad.arth@gmail.com[/email]

---

### Post by monchichi on 2005-05-14
Install the following:```
sudo apt-get install nvidia-glx
sudo apt-get install linux-restricted-modules-amd64-k8
```
Then reboot, and voila, 64-bit NVIDIA drivers are installed. Including compatibility libraries for 32-bit games.  :smile: 

If you have problems, you may have to edit your /etc/X11/xorg.conf accordingly.

---

