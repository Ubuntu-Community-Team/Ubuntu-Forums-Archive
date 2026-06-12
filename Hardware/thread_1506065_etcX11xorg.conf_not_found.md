---
title: "/etc/X11/xorg.conf not found"
date: 2010-06-09
forum: Hardware
---

### Post by Isamtron on 2010-06-09
Hello,

I'm trying to disable the touchpad by following the tutorial here: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I tried to uninstall xserver-xorg-input-synaptics package and restarted my computer but it still working.

I tried to edit /etc/X11/xorg.conf and it's not found! /etc/X11/ content as follow:

```
my-laptop:/etc/X11$ ls
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config
```

I'm using Dell laptop (inspiron 1525) and Ubuntu Lucid Lynx.

Your help is greatly appreciated.

---

### Post by anglican on 2010-06-10
> **Isamtron said:**
> 

I tried to edit /etc/X11/xorg.conf and it's not found!
Boot into recovery mode, when you get to the command line type:
```
sudo Xorg -configure
```which will create a default /etc/X11/xorg.conf file.

H

---

### Post by quadproc on 2010-06-10
> **Isamtron said:**
> ...
I tried to edit /etc/X11/xorg.conf and it's not found! /etc/X11/ content as follow:

anglican showed what you can do to create an xorg.conf file; the explanation of why you didn't have one is that the xorg.conf file is optional in later versions of Ubuntu.  If the file is not present then the system looks at the hardware and tries to do something sensible with it.  If the file is present then it will be honored.

If you get into trouble with a bad xorg.conf file then you can use recovery mode to boot up, then change the name of xorg.conf to something else, then reboot.  That will let you run the system well enough to fix the (now renamed) xorg.conf file; then you can put the file back and restart the X server.

quadproc

---

### Post by Isamtron on 2010-06-10
Thanks guys. By executing sudo Xorg -configure, the file was created in /root/xorg.con.new. Can I just copy it to /etc/X11/?

---

### Post by efflandt on 2010-06-10
Strange that it would put it in /root/xorg.conf.new, usually it puts it in your home dir, so you must have been running as root instead of a user.

So you can: **sudo mv /root/xorg.conf.new /etc.X11/xorg.conf**

Just type carefully (you said xorg.con.new).

---

### Post by Isamtron on 2010-06-12
Thanks for your help.

> **Isamtron said:**
> I tried to uninstall xserver-xorg-input-synaptics package and restarted my computer but it still working.

I just want to clarify, the above is not entirely true as I realized later. The pointer was moving but by uninstalling the package, I couldn't click using the mouse pad (which is good but having the pointer disabled as well would be better).

---

### Post by lamle on 2010-06-15
Hi,
I am using Ubuntu 8.04 and I did updated it to Ubuntu 9.04 but because  it is an unstable version, after upgrading I can not log in to the  graphical user interface anymore. 
Thinking that it has something to do with my graphic driver (is it  xorg?), I removed xserver-xorg-core and installed it again but it cries  about 1 dependency not found: 
dependency xserver-xorg-input-4 but it is not installale. 
This xserver-xorg-input-4 is a virtual package and I cannot install it  either. It contains xserver-xorg-input-synaptics,  xserver-xorg-input-wacom and 2 others but i dont remember. 

Please give me an advice how I can recover my graphic driver? I use ATI card 
Thank you for your help and have a nice day  :-)  
BR,Lam

---

### Post by lamle on 2010-06-15
Hi,
I am using Ubuntu 8.04 and I did updated it to Ubuntu 9.04 but because  it is an unstable version, after upgrading I can not log in to the  graphical user interface anymore. 
Thinking that it has something to do with my graphic driver (is it  xorg?), I removed xserver-xorg-core and installed it again but it cries  about 1 dependency not found: 
dependency xserver-xorg-input-4 but it is not installale. 
This xserver-xorg-input-4 is a virtual package and I cannot install it  either. It contains xserver-xorg-input-synaptics,  xserver-xorg-input-wacom and 2 others but i dont remember. 
 
Please give me an advice how I can recover my graphic driver? I use ATI card 
Thank you for your help and have a nice day  :-)  
BR,Lam

---

### Post by JSchultheis on 2011-09-19
> **quadproc said:**
> anglican showed what you can do to create an xorg.conf file; the explanation of why you didn't have one is that the xorg.conf file is optional in later versions of Ubuntu.  If the file is not present then the system looks at the hardware and tries to do something sensible with it.  If the file is present then it will be honored.

quadproc


> **Isamtron said:**
> 

I tried to edit /etc/X11/xorg.conf and it's not found! /etc/X11/ content as follow:

```
my-laptop:/etc/X11$ ls
app-defaults             fonts    xinit   Xreset.d    Xsession.d
cursors                  rgb.txt  xkb     Xresources  Xsession.options
default-display-manager  X        Xreset  Xsession    Xwrapper.config
```






Hello! I am quite noob here so please be gentle! ;)

I found that in my /etc/X11/ folder I also have a file called "X" which actually is a (shortcut) file pointing to /usr/bin/Xorg.conf

I have been trying everyway I have found to configure my xorg, but alas, to no avail. 

This is on an (drumroll:) Inspiron 1100 XD

Any ideas? (other than burning the ancient laptop lol)

---

### Post by .... on 2011-09-19
> **JSchultheis said:**
> I found that in my /etc/X11/ folder I also have a file called "X" which actually is a (shortcut) file pointing to /usr/bin/Xorg.conf
/etc/X11/X should be a shortcut to /usr/bin/Xorg. This is a binary executable, not a text .conf file (all the files in /usr/bin should be executables). That shortcut is unrelated to what you're trying to do.

Speaking of which, what exactly are you trying to do?

---

### Post by .... on 2011-09-19
If you're trying to change video drivers and test the intel driver, see: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

The command for editing/creating xorg.conf is:
```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by JSchultheis on 2011-09-22
> **.... said:**
> /etc/X11/X should be a shortcut to /usr/bin/Xorg. This is a binary executable, not a text .conf file (all the files in /usr/bin should be executables). That shortcut is unrelated to what you're trying to do.

Speaking of which, what exactly are you trying to do?

As for the 'X' file, I mentioned it not to mislead that it is a .conf file, but rather to show that it points to an Xorg.conf file, and that the Xorg.conf file happens to be in another directory. Considering the thread is named pertaining to a file not found and that previous posters had stated that the Xorg.conf file was not included in this build, I wanted to point out that the file is in this build, just not in the /etc/X11 folder as expected. I found it by looking at the properties of 'X', which pointed me to this other folder. Clearly a shortcut cannot be edited to produce any effect like what we are talking about. However, can the file that it points to be edited to achieve the desired results? 



> **.... said:**
> If you're trying to change video drivers and test the intel driver, see: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

The command for editing/creating xorg.conf is:
```
gksu gedit /etc/X11/xorg.conf
```


I have yet to find a file that I can open, then manipulate the existing data, then save & close and be done; or at least I'm not using the proper command to edit it, as each time a blank file appears. I guess that means you expect that I will not be editing but instead creating. The greater majority of posts I have found discussing this topic describe editing the Xorg.conf file. 

My plan is to simply get 1024x768 resolution.

I see your Mavericki post, and raise you a post:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell)

but which should be used, where should the file be created, what should happen to 'X' and what should happen to /usr/bin/Xorg.conf?

---

