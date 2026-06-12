---
title: "hosts file screwed"
date: 2008-07-15
forum: General Help
---

### Post by ngms27 on 2008-07-15
Hi,

My hosts file looks corrupted so when I try sudo for example I get this:

ngms27@ngms27-desktop:/etc$ sudo
sudo: unable to lookup ngms27-desktop via gethostbyname()

Anyone know how I can modify my hosts file given I cannot write to the folder?

---

### Post by Elfy on 2008-07-15
Try using gksudo gedit or open nautilus as gksudo. Was how I got someone else to do it I think.

Alternatively boot recovery mode and you won't need sudo and can edit it with nano

Edit - [https://answers.launchpad.net/ubuntu/+question/33164](https://answers.launchpad.net/ubuntu/+question/33164)

---

### Post by ngms27 on 2008-07-15
gksudo gets the same issue as does every administrative task.

How do I boot into recovery mode?

---

### Post by Elfy on 2008-07-15
When you boot - there should be a recovery option on the menu - use that.

If you have hardy there is a little menu you get to eventually, drop to a root shell - you won't need sudo there.

If you have gutsy or before recovery just drops to a root prompt.

---

### Post by fragos on 2008-07-15
sudo nano /etc/hosts

---

### Post by bodhi.zazen on 2008-07-15
You can also edit the file from a live CD

Mount your ubuntu root partition at say /mnt

then

gksu gedit /mnt/etc/hosts

---

