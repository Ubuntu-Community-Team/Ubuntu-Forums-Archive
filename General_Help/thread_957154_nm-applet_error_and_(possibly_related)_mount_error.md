---
title: "nm-applet error and (possibly related) mount error"
date: 2008-10-24
forum: General Help
---

### Post by monkeydragon707 on 2008-10-24
Alright, I have two main problems that I can't fix by myself. I know the cause of these problems but I don't know how to fix them.
First of all, my nm-applet when I run it through terminal works but can only connect through ethernet and not wireless, which is grayed out when I select it. In terminal it gives me this message: 

** (nm-applet:8101): WARNING **: Could not retrieve dbus connections: The permission of the setuid helper is not correct.


Secondly, when I try to mount an external hard drive, it gives me an error message saying Error *org.freedesktop.DBus.Error.AccessDenied.*
[I]Details: 
A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface 'org.freedesktop.Hal.Device.Volume' member 'Mount' error name '(unset)' destination 'org.freedesktop.Hal')[/I]

Now, the cause for this would most probably be a very retarded mistake I made not too long ago: typing in sudo chmod 777 /usr -R. 
I didn't know what I was doing, I still don't, but now I know never to be so liberal in using chmod ever again. 
I had a problem with sudo but was able to fix it, and I may have many more problems from this mistake. If someone can tell me how to change the permissions back to default in the subfolders of /usr, I think/hope that would solve all my problems. 
But until then, these two are the ones I'm most worried about. So any help would be greatly appreciated. Thanks.

---

### Post by plucky on 2008-10-24
> Now, the cause for this would most probably be a very retarded mistake I made not too long ago: typing in sudo chmod 777 /usr -R.

Seriously,I would re-install as changing permissions on the root partition can cause all sorts of obscure problems down the line and you would never be sure that this error didn't cause the problem.

At least with a clean install,you know that any further problems is not related to this root partition permissions error.

And be careful with the sudo command.

Good Luck

---

### Post by monkeydragon707 on 2008-10-24
Hey, thanks for the quick reply.
I can try a reinstall, but I don't want to lose all my apps, repositories, etc that' I've collected over time... Is there a way to preserve these? 
Also, my home folder is in another partition, so if I reinstall only on the root filesystem partition, it will be left intact right? 
If there's a howto or tutorial on how to do this, that would be really helpful.

---

### Post by plucky on 2008-10-24
> I can try a reinstall, but I don't want to lose all my apps, repositories, etc that' I've collected over time... Is there a way to preserve these?

All the downloaded applications are stored in ```
/var/cache/apt/archives
``` so you could copy them to a backup disk or use an application called "aptoncd" to make a backup of all the application packages.

> Also, my home folder is in another partition, so if I reinstall only on the root filesystem partition, it will be left intact right?

When you are installing you must not format your home partition but just mark the partition as your home,just as you have to mark and format the root partition.This can only be done from the **manual** partitioning section when installing. 
See this [link](http://www.psychocats.net/ubuntu/dualboot) for installing a dual boot system.

As with any installation,make sure you have backups,just in case something goes wrong and you need to recover.


Good Luck

---

