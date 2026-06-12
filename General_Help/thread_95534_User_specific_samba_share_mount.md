---
title: "User specific samba share mount"
date: 2005-11-26
forum: General Help
---

### Post by Botter on 2005-11-26
I have installed Kubuntu 5.1 on a notebook. The notebook is beeing used by different users. All the users can access a NAS (Maxtor Shared Storage), but with user specific access limitations.

When I use the Konquerer environment I can easiliy access the NAS via smb://NAS_Server/NASdirectory. The access limitations are defined by the network-browser settings in the systemsettings.
So far - so good.

A big problem is, that a lot of applications (like vlc, kaffeine, openoffice, ...) do not work properly if they have to access a file via smb://NAS_Server/NASdirectory/file . But they work properly when the network drives are mounted like e.g. /home/user/mnt/NASdirectory.

Now, here is my question:
How can I mount the network directories with specific access settings for each user WITHOUT having to type the sudo password?
The Konquerer network folder application shows that there must be a way to achieve this.

Modifing Fstab does not work, because it applies the same access restrictions to all computer users, which I would like to avoid (why: I would like to have rw on the NAS directories, other users should have ro access).

I did not manage to create a .kde/Autostart script mounting the NASdirectory without having to use the sudo and being prompted for the password.

Can somebody help?

---

### Post by Jens7677 on 2005-11-27
take a look at smb4k.

---

### Post by Botter on 2005-11-27
[QUOTE=Jens7677]take a look at smb4k.[/QUOTE]

Thx for the hint!
:D 
Botter

---

