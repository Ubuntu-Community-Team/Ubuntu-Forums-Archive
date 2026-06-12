---
title: "want to change a protected file /etc/fstab"
date: 2008-10-12
forum: General Help
---

### Post by ragnarokeve on 2008-10-12
I need to change the file fstab so that it automatically mounts two hard disks, but i have tried to edit it and am unable to save it back to the folder /etc, due to the protections on the folder and the file, i have tried to change the permissions but it says that i am not the owner and can't change the permissions



(Changed /exec to /etc, thanks taqkavar)

---

### Post by taqkavar on 2008-10-12
sudo <command> will give you administration rights in a terminal (Applications > Accessories > Terminal ). But be very careful using sudo as you can do unrecoverable or hard to undo damage to your system using it. I say this, since I see that you want to save fstab back to "/exec" which is not where it is supposed to be.

try: 

sudo gedit /etc/fstab

save a a backup of your original fstab as ftabBackup, then modify the fstab file.

---

### Post by ragnarokeve on 2008-10-12
I have tried to run the command sudo gedit /etc/fstab but it comes up with a message saying sudo: /etc/sudoers is mode 0644, should be 0440

---

### Post by taqkavar on 2008-10-12
Try rebooting, then select recovery mode in the boot menu (grub). Then log in as root. ( Enter root as user name, and your password ) you should see a # instead of $ in your terminal where you type. then try doing : 

sudo chmod 0440 /etc/sudoers

Hopefully this will fix your problem. Also, how did the permissions for /etc/sudoers changed in the first place? :confused:

---

