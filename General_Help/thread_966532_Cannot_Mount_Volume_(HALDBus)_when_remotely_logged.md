---
title: "Cannot Mount Volume (HAL/DBus) when remotely logged in"
date: 2008-11-01
forum: General Help
---

### Post by EReckase on 2008-11-01
I have a headless Hardy 64-bit machine that I use as my music server (Squeezecenter, etc) that I'd like to plug my ipod into to transfer some files.  I use nomachine as my remote server/client, which works very well for me.  The problem is that if I'm not logged in locally to the machine, I get errors when the machine tries to automount the ipod, or any external storage device for that matter.  I get this error:

Cannot mount volume.
Error org.freedesktop.DBus.Error.AccessDenied.

Details: A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")

I've tried changing the stuff in the policykit to permit non-console users to mount devices, but it doesn't seem to help.  I'll happily provide details from any logfile or the output of any command to be able to get this to work - and I'll also be ok with mounting the ipod manually (sudo), I just don't know how to do that.

Regards,
Erik

---

### Post by zo0o0ot on 2009-04-11
I'm having the same problem with mounting volumes.  I have ubuntu 8.04 server with gnome installed, and I can mount drives locally, but not when using Nomachine NX.  I get the same error message.  Any help would be appreciated.

---

### Post by blumagic on 2009-06-30
I hope that someone can assist as I am having the same problem. In addition, I cant unlock the services gui, the users and groups and also the Network gui program. Any help would be appreciated.

thanks,

blumagic

---

