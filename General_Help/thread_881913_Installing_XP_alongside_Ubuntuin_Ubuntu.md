---
title: "Installing XP alongside Ubuntu/in Ubuntu"
date: 2008-08-06
forum: General Help
---

### Post by lupinesoul on 2008-08-06
I need to get Windows back somehow.  I have the CD and Key.  I heard about VMWare, which sounds good (running Windows in Ubuntu, I believe?), but it wants me to register and such.  Is it really free?  I don't care whether Windows is alongside or inside Ubuntu, but what do you suggest?  I'm just really confused right now... :(

Edit: Okay, screw these emulators.  Just how do I make the CD run during start-up?  Otherwise it just boots Ubuntu.

---

### Post by geirha on 2008-08-06
You can find [virtualbox-ose](apt://virtualbox-ose) in the repositories. It's an alternative to vmware, it's open source, and is fairly easy to use. Have a look at [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by tuxxy on 2008-08-06
Just install virtualbox its free and easy to use, will allow you have a virtual parition on your drive that will run windows in ubuntu.  Search for virtualbox in synaptic or do this command in terminal;

```
sudo apt-get install virtualbox*
```

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by limasierra on 2008-08-06
Besides vmware and virualbox you can there is also Qemu.

---

### Post by lupinesoul on 2008-08-06
> **tuxxy said:**
> Just install virtualbox its free and easy to use, will allow you have a virtual parition on your drive that will run windows in ubuntu.  Search for virtualbox in synaptic or do this command in terminal;

```
sudo apt-get install virtualbox*
```

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Another problem (I was just reminded) is that when I run setup.exe from the XP CD and I click the "Install Windows XP" button, it stops at the step "Collecting Information".

It came up with this...
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting virtualbox-ose-guest-modules-2.6.24-16-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-20-rt for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-16-rt for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-16-rt for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-18-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-20-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-20-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-20-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-18-rt for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-19-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-20-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-20-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-18-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-18-rt for regex 'virtualbox*'
Note, selecting virtualbox for regex 'virtualbox*'
Note, selecting virtualbox-ose instead of virtualbox
Note, selecting virtualbox-ose-guest-modules-generic for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-20-generic for regex 'virtualbox*'
Note, selecting virtualbox-source for regex 'virtualbox*'
Note, selecting virtualbox-ose-source instead of virtualbox-source
Note, selecting virtualbox-ose-modules-2.6.24-19-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-19-rt for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-19-rt for regex 'virtualbox*'
Note, selecting virtualbox-ose for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-rt for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-18-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-20-generic for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-18-generic for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-rt for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-16-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-19-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-18-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-utils for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-16-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-18-generic for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-18-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-16-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-16-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-16-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-19-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-16-generic for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-20-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-18-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-source for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-20-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-source for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-19-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-16-generic for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-19-generic for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-19-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-20-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-dbg for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-19-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-19-generic for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-16-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-virtual for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-19-386 for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-modules-2.6.24-18-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-16-server for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-18-openvz for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-2.6.24-20-rt for regex 'virtualbox*'
Note, selecting virtualbox-ose-modules-generic for regex 'virtualbox*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-guest-modules-2.6.24-20-386: Depends: linux-image-2.6.24-20-386 but it is not installable
  virtualbox-ose-guest-modules-2.6.24-20-generic: Depends: linux-image-2.6.24-20-generic but it is not installable
  virtualbox-ose-guest-modules-2.6.24-20-openvz: Depends: linux-image-2.6.24-20-openvz but it is not installable
  virtualbox-ose-guest-modules-2.6.24-20-rt: Depends: linux-image-2.6.24-20-rt but it is not installable
  virtualbox-ose-guest-modules-2.6.24-20-server: Depends: linux-image-2.6.24-20-server but it is not installable
  virtualbox-ose-guest-modules-2.6.24-20-virtual: Depends: linux-image-2.6.24-20-virtual but it is not installable
  virtualbox-ose-modules-2.6.24-20-386: Depends: linux-image-2.6.24-20-386 but it is not installable
  virtualbox-ose-modules-2.6.24-20-generic: Depends: linux-image-2.6.24-20-generic but it is not installable
  virtualbox-ose-modules-2.6.24-20-openvz: Depends: linux-image-2.6.24-20-openvz but it is not installable
  virtualbox-ose-modules-2.6.24-20-rt: Depends: linux-image-2.6.24-20-rt but it is not installable
  virtualbox-ose-modules-2.6.24-20-server: Depends: linux-image-2.6.24-20-server but it is not installable
  virtualbox-ose-modules-2.6.24-20-virtual: Depends: linux-image-2.6.24-20-virtual but it is not installable
E: Broken packages
```

---

### Post by tuxxy on 2008-08-06
Also PearPC is available if you would to run osx :)

---

### Post by lupinesoul on 2008-08-06
> **tuxxy said:**
> Also PearPC is available if you would to run osx :)

No, I'm not interested in Mac and the system I currently have the CD for is Windows XP.

Edit: Can someone just tell me how to run the CD during start-up?...

---

### Post by geirha on 2008-08-06
Did you follow the link I posted? It should explain how to set it up. Though since you use a physical CD (and not an image) make sure you choose to use the host CD/DVD drive instead of an image when you get to the point of adding a CD/DVD-drive to the virtual machine.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by civillian on 2008-08-06
Just as a side note; in order to use it well/effectively (as in: to do stuff other than just start windows) you will need a pretty speedy computer.

---

### Post by lupinesoul on 2008-08-06
> **geirha said:**
> Did you follow the link I posted? It should explain how to set it up. Though since you use a physical CD (and not an image) make sure you choose to use the host CD/DVD drive instead of an image when you get to the point of adding a CD/DVD-drive to the virtual machine.

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

I looked at that, but running Windows in Ubuntu is just too much trouble.

---

