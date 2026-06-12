---
title: "Access to home-folder on other partition"
date: 2008-10-05
forum: General Help
---

### Post by NexusHumanis on 2008-10-05
I just installed the Ubuntu 8.10 beta, and now I am wondering how I can make the ubuntu home-icon link directly to the home folder on my Kubuntu Hardy installation on sda1. 

Also, the nm-applet doesn't give me the option of entering a password to open my wireless network-connection. Instead I have to enter the full 10 digit access code every time I log in.

---

### Post by lian1238 on 2008-10-05
> **NexusHumanis said:**
> I just installed the Ubuntu 8.10 beta, and now I am wondering how I can make the ubuntu home-icon link directly to the home folder on my Kubuntu Hardy installation on sda1. 

Also, the nm-applet doesn't give me the option of entering a password to open my wireless network-connection. Instead I have to enter the full 10 digit access code every time I log in.

For the password thing, try starting keyring manager. (gnome-keyring-manager)

---

### Post by NexusHumanis on 2008-10-05
> **lian1238 said:**
> For the password thing, try starting keyring manager. (gnome-keyring-manager)

How do I start it? Why doesn't it run by default?

---

### Post by lian1238 on 2008-10-05
> **NexusHumanis said:**
> How do I start it? Why doesn't it run by default?

For me, it starts automatically. I didn't know what it was at first. I just ran it and created a new keyring. After that, it always asks me for my password for most things (FTP, Wifi, etc).

To start it, try going to System->Administration->Keyring Manager or run (Alt+F2) **gnome-keyring-manager**.

---

### Post by NexusHumanis on 2008-10-05
> **lian1238 said:**
> For me, it starts automatically. I didn't know what it was at first. I just ran it and created a new keyring. After that, it always asks me for my password for most things (FTP, Wifi, etc).

To start it, try going to System->Administration->Keyring Manager or run (Alt+F2) **gnome-keyring-manager**.

I cannot find any gnome-keyring-manager anywhere in my system. I tried running apt-get install gnome-keyring-manager, but no such package was found. No such thing in system-> administration. I have logged out, and back in, but no password prompt(exept for the network-code)

---

### Post by lian1238 on 2008-10-05
> **NexusHumanis said:**
> I cannot find any gnome-keyring-manager anywhere in my system. I tried running apt-get install gnome-keyring-manager, but no such package was found. No such thing in system-> administration. I have logged out, and back in, but no password prompt(exept for the network-code)

In Hardy, for some reason, it's called **seahorse-preferences** and it's under System->Preferences->Encryptions and Keyrings. I was trying it out with my Hardy LiveCD with VirtualBox. When I restarted X to test if it worked, I unintentionally restarted the host. You can find out how to use it. I guess you need to create a keyring.

---

### Post by NexusHumanis on 2008-10-05
> **lian1238 said:**
> In Hardy, for some reason, it's called **seahorse-preferences** and it's under System->Preferences->Encryptions and Keyrings. I was trying it out with my Hardy LiveCD with VirtualBox. When I restarted X to test if it worked, I unintentionally restarted the host. You can find out how to use it. I guess you need to create a keyring.

I am working in Intrepid.The choices under Encryptions and keyrings are "encryption" and "Pgp-passfrases".

---

### Post by NexusHumanis on 2008-10-06
But what about my other problem; Linking my intrepid installation to the Hardy home-folder? Can it be done? Anyone?

---

### Post by NexusHumanis on 2008-10-08
No one?

---

### Post by jerome1232 on 2008-10-08
Do you know which partition it is on? 
Can you post the output of fdisk -l (small letter l)
```
sudo fdisk -l
```

---

### Post by NexusHumanis on 2008-10-08
> **jerome1232 said:**
> Do you know which partition it is on? 
Can you post the output of fdisk -l (small letter l)
```
sudo fdisk -l
```

The home-folder I want to use is on sda1, the intrepid installation is on sda3. I suppose sda2 is a swap partition. (I think I have two swap partitions at the moment, but I will deal with that later.)
No need to fdisk it, exept if there is something else in the output that is needed for good advice.

---

### Post by mixmaster on 2008-10-08
if sda1 contains only your home directory tree then 
sudo mount /dev/sda1 /home will place it over your intrepid created home 
directory.  This is probably not a good idea as changes made under intrepid
will be reflected back to hardy, and vice versa.

I would do the following:

sudo mkdir /hardy
sudo mount -o ro /dev/sda1 /hardy 

This will give you a read-only directory tree based on /hardy containing all the stuff on sda1.  You can copy over or link to anything you need but you will be protected from intrepid alpha nastyness damaging your hardy setup.

---

