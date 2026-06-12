---
title: "Is there virtualisation software which does not require a new install ?"
date: 2008-09-12
forum: General Help
---

### Post by harambe on 2008-09-12
I have a PC with Windows XP in one partition, and Ubuntu 804 in the other.

There is some XP software which I can't get to work properly in Wine.

I have looked at several Virtualisation products, but all seem to be saying I need to reinstall whichever OS is not my host.

Does anyone know of a Virtualisation product which will allow me to keep both my current OS installs ?

---

### Post by mb_webguy on 2008-09-12
If I understand it correctly, you wouldn't be losing either of your current installations.  Rather, you would gain a third virtual installation in the VM.  You have to install the OS on the VM, not to a partition.

---

### Post by lovinglinux on 2008-09-12
Do you mean using your installed OS inside the virtual machine? 

You can keep both OS's but you won't be able to access them inside a virtual machine. Let's say you boot on Ubuntu, install the virtualbox sofware, then you need to create a virtual disk for your first virtual machine and install any OS you want on it. When you finish, you can close the virtual machine, shut down Ubuntu and boot on Windows again. But the Windows installation inside the virtual machine will be different from the Windows installation on dual-boot.

What you could do is make ghost image of your dual-boot Windows installation and restore it inside the virtual machine, so this way your virtual machine will be an exact snapshot of your dual-boot Windows. Any further changes on the virtual machine or the dual-boot installation will not be synchronized. That is the nature and the beauty of virtualization, it provides the ability to run a self-contained OS inside a virtual machine, without affecting the host OS.

---

### Post by gaussian on 2008-09-12
> **harambe said:**
> I have a PC with Windows XP in one partition, and Ubuntu 804 in the other.

There is some XP software which I can't get to work properly in Wine.

I have looked at several Virtualisation products, but all seem to be saying I need to reinstall whichever OS is not my host.

Does anyone know of a Virtualisation product which will allow me to keep both my current OS installs ?

I think that both VMWare and Virtualbox can be **hacked** into doing this. I have not done it, but I have seen it referenced.

---

### Post by Sycron on 2008-09-12
I would like to know how is this possible...

---

### Post by Sunborn on 2008-09-12
This thread should show you what you want to do. Boot an existing XP partition with VirtualBox.

[http://ubuntuforums.org/showthread.php?t=769883]("http://ubuntuforums.org/showthread.php?t=769883")

---

### Post by EmanresuusernamE on 2008-09-12
> **harambe said:**
> Does anyone know of a Virtualisation product which will allow me to keep both my current OS installs ?

There's a slight problem with doing something like this with Windows.  If Windows detects that the hard drive and the mother board have been changed, (and virtual machines emulate their own hardware) then it will lock itself up and tell you to give microsoft a call.  However, I think you can install Windows on the virtual machine, copy the stuff in C:\windows\system32\config of the virtual machine to a safe location, then take a snap shot of your windows installation, put it in the virtual machine, and the put the old contents of the C:\windows\system32\config folder into the virtual machine.  Do them one at a time so you can find out which one you really need.  I should think it should just be the SYSTEM file, but I'm not sure.  I stopped hacking like this on windows boxes some time ago.

---

### Post by EmanresuusernamE on 2008-09-12
Hmmm, just finished reading the link above, seems you can do it without any hacking at all.  Will wonders never cease.

---

### Post by harambe on 2008-09-13
Thanks all for your input - I can see some fun coming up.

---

