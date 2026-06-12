---
title: "fglrxinfo finds mesa when it should find my radeon 9250"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by mjkelly on 2005-07-15
Im gonna keep it short. I know im beating a dead horse and i wouldnt have posted this unless i was really at wits end here.

Its going on about a week now of surfing through posts here in the hardware forum and im at step 1. Heres my fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Ive searched for that through the forums but i have yet to find a solid answer to it. Theres alot of people taking stabs at how to fix it, but i couldnt find an answer.

My xorg.conf looks fine also. Everything that was supposed to be added was added. Heres the device part:
Section "Device"
        Option          "backingstore"              "true"
	Option 		"AllowGLXWithComposite" "true" 
	Identifier	"Radeon 9200"
	Driver		"radeon"
	BusID		"PCI:1:2:0"
EndSection

If i change the Driver to fglrx my X server goes to a black screen.
Also, in my /var/log/Xorg.0.log, i searched for the words "fglrx" and "mesa" and neither are located anywhere in the log.
Someone who has done this and isnt guessing at "maybe this will work", please help me here.

---

### Post by mjkelly on 2005-07-15
Ok so now i tried stopping the x server and installing ati-driver-installer.8.14.13.run from a prompt, as one of the posts suggested. It got through the installation but told me there was errors and it wrote them to /usr/fglrx/fglrx-install.log.
Heres the errors

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.

Is this why everyones having problems with this? Has anyone fixed this yet?
EDIT
I found a post where someone actually fixed it, yet he didnt explain how. Heres what he said:

Finally....after a few hours it's all sorted. The missing files in make.sh is normal so that's ok, but the problem is my old drivers was still clogging up my system despite havnig uninstalled it so I had to purge it from my system and disable composite and few other stuff and finally I now get 4715fps in glxgears and 280fps fullscreen glxgears

Can someone guide me through this?

---

### Post by varunus on 2005-07-15
I'm no expert with the ATI drivers, but could you change your driver to fglrx, let it go to a black screen, hit CTRL-ALT-F1, copy your /var/log/Xorg.0.log to a text file in your home directory, and then change back so you an get a GUI and post it up here?  Changing to radeon makes you use mesa instead of fglrx...Maybe the log from the black screen can help.

---

### Post by mjkelly on 2005-07-15
If i change the driver in xorgconf to fglrx and let it go to the blackscreen... CTRL ALT F1 doesnt do anything and i cant change sessions.
All i could do is restart the comp manually by holding the power button in.
Heres the more recent directions im following after finding a post where someone had the same problem and fixed it like this:

1. download official driver .rpm from ATI
2. remove fglrx packages using Synaptic
3. shut down Gnome (terminal: sudo /etc/init.d/gdm stop)
4. cd to download-location
5. sudo alien fglrx_ ... .rpm
6. sudo mv /lib/modules/YOURKERNELVRSIONHERE/kernel/drivers/video/fglrx.ko $HOME
7. sudo dpkg --force-overwrite -i fglrx- ... .deb
8. cd /lib/modules/fglrx/build_mod
9. sudo sh make.sh
10. cd /lib/modules/fglrx
11. sudo sh make_install.sh
12. sudo modprobe fglrx
13. sudo fglrxconfig

Unfortunately when i get to number 9 i get this error:

root@ubuntu:/lib/modules/fglrx/build_mod # sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
root@ubuntu:/lib/modules/fglrx/build_mod #

Now i KNOW someone out there knows how to fix that little error. Any takers? :)

EDIT: I know someones going to tell me i have the wrong headers or wrong kernel installed but i dont. Heres my uname

root@ubuntu:/lib/modules/fglrx/build_mod # uname -r
2.6.10-5-386

In synaptic it reads like this
Package ---------------------------------------------------Installed version
linux-image-2.6.10-5-386 --------------------------2.6.10-34.3
linux-headers-2.6.10-5-386 -----------------------2.6.10-34.3

Is there anything wrong with that?

---

### Post by varunus on 2005-07-15
Go to /usr/src/.  Is the a symbolic link "linux" to your current kernel version?  If not, type:

```
sudo ln -s linux-headers-2.6.10-5-386 linux
``` 

Then try the ATI drivers.

---

### Post by mjkelly on 2005-07-15
Ok as i was tinkering around with the header package in synaptic i uninstalled the wrong thing, ruined my GDM and everything else apparently so i reinstalled :)

Now im stuck on number 11 and i get this error:

@ubuntu:/lib/modules/fglrx$ sudo sh make_install.sh
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko): Operation not permitted
failed.

????

---

