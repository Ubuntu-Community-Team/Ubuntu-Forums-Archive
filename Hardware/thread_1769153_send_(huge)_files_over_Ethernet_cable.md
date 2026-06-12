---
title: "send (huge) files over Ethernet cable"
date: 2011-05-27
forum: Hardware
---

### Post by yanom on 2011-05-27
I've got an Ubuntu* desktop, a windows XP laptop, a length of Cat5e Ethernet cable (y'know, the one with the squarish plug, usually blue, modern Internet connections use it), and no internet.

I've got to transfer a big bunch of files (Most of the laptop's hard drive, more than 50GB) over the cable to the desktop, into a specific directory. Anyone know how to do this?



*it dual boots Ubuntu and Windows 7, I can use either here.

---

### Post by yanom on 2011-05-27
anyone?

---

### Post by athenroy on 2011-05-27
Not sure you can do it with just an ethernet cable with no router.  MIght try Googling and see if you can come up with anything.

---

### Post by demonipuch on 2011-05-27
Hi

You can share your files on your network with SMB protocol. You need to edit your samba configuration file on your desktop to allow read/write access on the specific folder. Then on your Windows laptop, you'd connect to your shared folder in "my network places"

This is an example of what you should do :

On your desktop you need share your specific folder on your network with Samba.

Edit the file /etc/samba/smb.conf
```
sudo nano /etc/samba/smb.conf
```Under the global settings, set a workgroup name. For example "WORKGROUP" (must be in uppercase)
```
 workgroup = WORKGROUP
```Share your specific folder by adding those lines at the end of the file :
```
[sharename]
# share your specific folder. this is an example
path = /home/yanom/my_specific_folder
# valid users able to access your share. use your login
valid users = yanom
browseable = yes
writeable = yes
```Do ctrl+O to save and ctrl+X to close the file editor

Test the configuration file :
```
testparm
```If you got no error, reload the configuration :
```
sudo service smbd restart
```Now on your windows laptop, check that you're in the same workgroup. It should be MSHOME or WORKGROUP depending on your XP version. Change the workgroup if needed. You have to reboot your laptop now.

After rebooting, you should see your desktop in "My network places". Enter your (desktop) login and password.

You should be able to copy your files in your shared folder.

---

### Post by dandnsmith on 2011-05-28
The other thing to watch for is that the link actually works.
Some ethernet ports don't care whether the other end is configured the correct way round, some would need a x-over cable (default are straight).

The other thing to watch for is assigning IP addresses manually, as this mode of connection won't offer any DHCP.

HTH

---

### Post by yanom on 2011-05-28
wow, this looks hard... can I do it over my LAN instead of a cable? Both computers are on a LAN.

---

### Post by demonipuch on 2011-05-28
> **yanom said:**
> wow, this looks hard... can I do it over my LAN instead of a cable? Both computers are on a LAN.

There is nothing really hard to be honest : 
1- on Ubuntu edit samba config file
2- restart samba

3- on XP set the workgroup and reboot
4-  copy your files.

Of course you can do it over your LAN.

---

### Post by yanom on 2011-05-28
samba... I've heard that name before... but what is it again?

---

### Post by dandnsmith on 2011-05-28
Agreed - why wasn't the LAN mentioned originally.
It reduces the problem to almost nothing.

---

### Post by demonipuch on 2011-05-28
> **yanom said:**
> samba... I've heard that name before... but what is it again?
Taken from samba.org : Since [1992]("http://www.samba.org/samba/docs/10years.html"), Samba has provided secure, stable and fast 	file and print services for all clients using the SMB/CIFS protocol, such as all versions of DOS 	and Windows, OS/2, Linux and many others.

---

### Post by dandnsmith on 2011-05-28
Samba - derived from SMB (something like Short Message Block protocol)

Used by Microsoft for establishing network credentials for shared information.

---

### Post by yanom on 2011-05-28
mm. but I don't feel like setting up a file server for a one-time thing. It's not like I'm going to be doing this every day. mm... is there a way to use **scp** on Windows? Then I could just pop the file over to the linux machine from the windows machine. I tried **pscp** but it doesn't support transfers over the local network.

---

### Post by demonipuch on 2011-05-29
> is there a way to use **scp** on Windows?puTTY allows you to connect to a SSH server. You should take look at this page : [http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/")

If you want to use scp then i assume you have a SSH server running on Ubuntu. Another solution could be to connect to Ubuntu using SFTP protocol with a Windows SFTP client (like FIlezila)

---

