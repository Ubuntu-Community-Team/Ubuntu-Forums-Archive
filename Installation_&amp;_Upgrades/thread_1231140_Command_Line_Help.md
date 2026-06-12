---
title: "Command Line Help"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by optimistique1 on 2009-08-04
Hi All

Can anyone advise me how to do the following two commands in Ubuntu :

(4a.) Add the line 'psb' to /etc/modules

5. Modify/add to the parameters of kernel 2.6.28-13 in /boot/grub/menu.lst: nosplash mem=1500MB

Many thanks

Garry

---

### Post by Partyboi2 on 2009-08-04
Hi, open a terminal and type
```
sudo nano /etc/modules
``` at the end of the file add
```
psb
``` then save the changes Ctrl+o then press 'enter' followed by Ctrl+x to exit.
Then open your /boot/grub/menu.lst
```
sudo nano /boot/grub/menu.lst
``` look for the line starting with "# kopt=" and add to the end of the line
```
nosplash mem=1500MB
```then save and exit Ctrl+o, enter, Ctrl+x then 
```
sudo update-grub
```[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation")

---

### Post by slakkie on 2009-08-04
> **optimistique1 said:**
> Hi All

Can anyone advise me how to do the following two commands in Ubuntu :

(4a.) Add the line 'psb' to /etc/modules




echo "psd" | sudo tee -a /etc/modules

---

