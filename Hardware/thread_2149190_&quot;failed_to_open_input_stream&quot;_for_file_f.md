---
title: "&quot;failed to open input stream&quot; for file from external hard drive"
date: 2013-05-28
forum: Hardware
---

### Post by bluegreen7 on 2013-05-28
Hi all,

I'm fairly new to ubuntu and don't know much about terminal but I'm learning my way around a bit. I have a WD SmartWare external hard drive that I'm trying to mount in ubuntu. It was formatted for mac, so I've already gone into a mac computer and turned off the password so that I am now able to access the drive in ubuntu (I have version 12.04). So I can at least see it -- it shows up in my home folder and I can see all of its different folders and files. But now when I try to access its files, I can neither open the files nor copy them to my computer. I get the error message specified above, "failed to open input stream." I check the properties and they say that I am not the owner so I can't modify the permissions.

I searched other threads and found advice to change myself to the owner through the "chmod" and "chown" commands. I tried both of these and I get this:

chmod 775 '/media/WD SmartWare'
chmod: changing permissions of `/media/WD SmartWare': Read-only file system

or this:

chown: changing ownership of `/media/WD SmartWare': Read-only file system

It's encouraging that the commands appear to be doing something, however A) read-only is not good enough, and B) it's also not accurate. I still have no additional access to my files than I had before / can't open them. I've tried disconnecting and restarting just in case but that didn't make a difference.


Any advice would be much appreciated!!

---

### Post by steeldriver on 2013-05-28
Hello and welcome to the forum

I've never had to deal with a mac device but I think the problem is likely related to handling of the native HFS filesystem that it uses - see here

[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

I think this information is still current but you might want to wait for someone with mac experience to chime in

---

