---
title: "Moving /home files from one computer to another"
date: 2008-09-06
forum: General Help
---

### Post by wersdaluv on 2008-09-06
I just bought a new computer and installed Ubuntu on it. Both are running Hardy now, both have ethernet ports, and I have a netgear wireless router with LAN ports on it. 

I have tried asking around about transferring files using a server but I had a really hard time. I have to transfer my files soon. What do you think is the best option for me? I need a really simple solution because of my lack of knowledge about servers.

---

### Post by Zill on 2008-09-06
If both PCs just have a Linux OS on them then you could use NFS (Network File System).  Set one up as a NFS server and the other as a NFS client.  Not too difficult as I managed to do it!

If one or both of the PCs are dual boot with Linux/Windows then I think you may have to use samba - not sure about this one though as I have been MS-free for years :-)

If this is all too daunting then I suggest you just burn a DVD or two and use good old fashioned sneakernet to transfer your files.

---

### Post by The Cog on 2008-09-06
I would install openssh server on one of the two:
**sudo apt-get install openssh-server**
then connct to it using nautilus as a client on the other one:
launch nautilus and enter in the address bar: 
ssh://1.2.3.4 (or whatever the real address is of course)
then launch a second nautilus to view the destination directory, and drag the files/directoories between the two windows.

---

### Post by wersdaluv on 2008-09-06
> **The Cog said:**
> I would install openssh server on one of the two:
**sudo apt-get install openssh-server**
then connct to it using nautilus as a client on the other one:
launch nautilus and enter in the address bar: 
ssh://1.2.3.4 (or whatever the real address is of course)
then launch a second nautilus to view the destination directory, and drag the files/directoories between the two windows.
How do I know the addresses of each computer? :)

---

### Post by Zill on 2008-09-07
> **wersdaluv said:**
> How do I know the addresses of each computer? :)
There might be a way to use dynamic IP addresses but IMHO it is best to use  static IP addresses for networked PCs - it just makes life simpler :-)

If your PCs are currently using dynamic IP addresses, supplied by your router, then I suggest you change these to unique static IP addresses in the same subnet as your router's IP address.  eg if the router IP address is 192.168.0.1 then PC_A could be 192.168.0.2 and PC_B could be 192.168.0.3

Menu: System, Administration, Networking, Connections tab,
Ethernet connection, Properties
Change configuration from DHCP to Static IP address
Enter your chosen IP address
Enter the router IP address as the Gateway address

You should then restart networking - the simplest way is to reboot ;-)

It should now be possible to ping the other PC using both its static IP address and its hostname as defined in the Network settings.

Once this is done it should be possible to use the methods described earlier to transfer files.

---

### Post by wersdaluv on 2008-09-07
I managed to transfer files using ssh. Found the ip addresses using ifconfig. Now, I'm having a problem with the permissions of the config files. Can't even log in. haha

---

### Post by Zill on 2008-09-07
> **wersdaluv said:**
> ...I managed to transfer files using ssh. Found the ip addresses using ifconfig. Now, I'm having a problem with the permissions of the config files. Can't even log in. haha
Make sure the new /home/user directory has the same UID/GID as the old one.

Which "config files" have the wrong permissions?

---

### Post by wersdaluv on 2008-09-07
I fixed it already. It's good now. Just about all config files had wrong permissions. haha

---

