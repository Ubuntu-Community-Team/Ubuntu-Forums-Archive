---
title: "USB mount problems (iscallerprivileged())"
date: 2008-07-31
forum: General Help
---

### Post by brel on 2008-07-31
I've got a permissions problem that only appeared in the last week or so. When I plug in a usb key, the device fails to mount and the error (in Dolphin) is iscallerprivileged() failed. If I try and force a mount via the right-click menu, I get a pop-up with the same msg and with the title 'kio_media_hand... (handler I suppose, thought the rest is cut off).

Permissions for the media dir seem to be OK: a "USB DISK" dir appears in /media with my name as the owner. In user administration the checkbox for "access external drives etc" is checked. What's missing?

Mounting via sudo/CL works fine but who wants to do that all the time?

I've done nothing but install the updates as they come in.

Thanks in advance.

---

### Post by chipr on 2008-08-11
I'm seeing this problem too.  I just reported it as a bug:
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/257028](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/257028)

---

### Post by riff raff on 2008-11-20
This happened to me again tonight.  What worked for me was to restart the hal with the init script.  A window opens saying that mounting the drive is against the system policy and it asks for a password.  I typed in my regular user password, the drive mounted, and now I can't get it to fail again.  I think hal got confused, and after restarting, needed to be told about that USB thumb drive again.  I started hal once more, but it didn't say anything about policy and didn't ask for a password.  So either sudo hadn't timed out, or hal remembered.  At any rate, I can't make it break now.

---

### Post by crouchingturbo on 2008-11-21
> **riff raff said:**
> This happened to me again tonight.  What worked for me was to restart the hal with the init script.  A window opens saying that mounting the drive is against the system policy and it asks for a password.  I typed in my regular user password, the drive mounted, and now I can't get it to fail again.  I think hal got confused, and after restarting, needed to be told about that USB thumb drive again.  I started hal once more, but it didn't say anything about policy and didn't ask for a password.  So either sudo hadn't timed out, or hal remembered.  At any rate, I can't make it break now.

Thanks for the workaround, saved me a lot of frustration.

---

### Post by DannyB2 on 2008-12-22
> **riff raff said:**
> This happened to me again tonight.  What worked for me was to restart the hal with the init script.  A window opens saying that mounting the drive is against the system policy and it asks for a password.


I'm on Ubuntu Server 8.04 with KDE3 installed.

Very recently, disks inserted stopped being able to mount.  It is the iscallerprivileged() error.

I restarted the computer.  Now when a disk is inserted, inserting a disk doesn't even show an icon on the desktop!

I can manually create a directory under /media, and manually mount it.  But what a pain!

I restarted hal...

sudo -i
cd /etc/init.d
./hal restart

But no joy.

Inserting a DVD does not show up an icon.

This error just suddenly, spontaneously appeared recently.

---

### Post by n0kS on 2009-09-28
Here's how I fixed it (I'M USING GNOME!):

1. Plug in the USB
2. The error appears
3. Menu --> System --> Administration --> New Login
4. Log in with root to KDE4 (I have 4.3.1)
5. In KDE Menu (down left) [CLICK HERE TO SEE PICTURE]("http://img514.imageshack.us/img514/8878/200909282054281280x1024.png")
6. Then the device will mount successfully
7. When it's mounted you can go back to your GNOME desktop (Menu --> Leave --> Log out --> then type your user password to access your gnome active session)

THIS WORKED FOR ME! (The only thing is that you have to have KDE4)
I don't know if this will work if you're using KDE4 and what to make the mount with GNOME... try it

ps: sorry for my english

---

