---
title: "VirtualBox - Kernel Module Not Found."
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by n0an on 2009-04-25
Hello,

I am trying to setup Windows XP using Sun Virtual Box on my Ubuntu Desktop(Server) 8.04 Hardy Heron. I am getting the "Kernel Module is either not loaded or their is a permission problem.

[IMG]http://i44.tinypic.com/t0lun5.jpg[/IMG]

I'm sure it's a permission problem 'cause I get this error in the terminal:
[IMG]http://i40.tinypic.com/53s09c.jpg[/IMG]

```
admin@ks302332:~$ nano /etc/init.d/vboxdrv
admin@ks302332:~$ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module 
Opening /proc/modules: No such file or directory
 *  done.
 * Recompiling VirtualBox kernel module              
_**etc/init.d/vboxdrv: line 275: /var/log/vbox-install.log: Permission denied**_
* Look at /var/log/vbox-install.log to find out what went wrong

```I tried root access using "su" for once, but then I messed up something and it now says authentication failure when I do "su" to gain root access again. Anyway, does anyone know what to do in this situation? I really need Windows to run some of my applications.

Thanks a lot!

---

### Post by drs305 on 2009-04-25
Did you add yourself to the group "vboxusers"? Check by running "id".


Here is a link that gives a few more instructions:
[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html]("http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html")

---

### Post by albinootje on 2009-04-25
> **n0an said:**
> 
```
admin@ks302332:~$ nano /etc/init.d/vboxdrv
admin@ks302332:~$ /etc/init.d/vboxdrv setup

```


Try this :
```

sudo apt-get install build-essential dkms

```
If you reboot now, then the dkms package should make sure that the module for VirtualBox gets compiled automatically.

Or simply do this without rebooting :
```

sudo apt-get install build-essential dkms
sudo /etc/init.d/vboxdrv setup

```

---

### Post by n0an on 2009-04-25
Yup, I had used the same tutorial to add myself.

> sudo adduser $USER vboxusers
Adding user `ionstorm' to group `vboxusers' ...
Adding user ionstorm to group vboxusers
Done.

Running "id" gives this:

> admin@ks302332:~$ id
uid=1001(admin) gid=114(admin) groups=114(admin),126(vboxusers)


Now?

---

### Post by albinootje on 2009-04-25
> **n0an said:**
> I tried root access using "su" for once, but then I messed up something

Please use sudo in Ubuntu, see here :
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by n0an on 2009-04-25
I did everything you said, but this time it gives some other error:

> admin@ks302332:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                            
_**Opening /proc/modules: No such file or directory**_
 *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
This is the log file:

> Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxdrv/2.2.0/source ->
                 /usr/src/vboxdrv-2.2.0

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.28.1-xxxx-std-ipv4-32 cannot be found at
/lib/modules/2.6.28.1-xxxx-std-ipv4-32/build or /lib/modules/2.6.28.1-xxxx-std-ipv4-32/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:143: Warning: using /usr/src/linux as the source directory of your Linux kernel. If this is not correct, specify KERN_DIR=<directory> and run Make again.
Makefile:178: *** Unable to find the folder to install the support driver to. Stop.

**./Modules dir:**

>  admin@ks302332:/lib$ cd ./modules
admin@ks302332:/lib/modules$ ls -a
.  ..  2.6.24-23-386  2.6.24-23-generic  2.6.24-23-rt  2.6.24-23-server


---

### Post by albinootje on 2009-04-25
> **n0an said:**
> I did everything you said, but this time it gives some other error:

Are you using a custom compiled kernel ?
Can you show the output of :
```

uname -a

```

---

### Post by n0an on 2009-04-25
I tried updating the kernel to the latest one, but failed.

"uname -a" gives:

> admin@ks302332:~$ uname -a[B]
[FONT=Arial][SIZE=2]_Linux ks302332.kimsufi.com 2.6.28.1-xxxx-std-ipv4-32 #2 SMP Fri Jan 30 09:55:02 UTC 2009 i686 GNU/Linux_[/SIZE][/FONT][/B] 
admin@ks302332:~$ 


---

### Post by albinootje on 2009-04-25
> **n0an said:**
> I tried updating the kernel to the latest one, but failed.


Do you really need this special kernel ?
If not, can you reboot, and then boot with the 2.6.24-23-generic or 2.6.24-23-server kernel ?

---

### Post by n0an on 2009-04-25
> **albinootje said:**
> Do you really need this special kernel ?
If not, can you reboot, and then boot with the 2.6.24-23-generic or 2.6.24-23-server kernel ?

I don't. I was just trying if it helps, but apparently it doesn't. How do I boot with the other ones? I'm have learned a lot of stuff in one night, but not this :P.

---

### Post by drs305 on 2009-04-25
> **n0an said:**
> How do I boot with the other ones? I'm have learned a lot of stuff in one night, but not this :P.

Do you have options visible for the other kernels on the grub menu during boot?

If you don't see the grub menu because you have it set to automatically run with a given kernel, hit ESC during the boot to pause grub and allow you to see your options. If one of the standard kernels is displayed in that menu, select it and then hit ENTER to boot.

---

### Post by n0an on 2009-04-25
I have Ubuntu Remote Desktop to a server. I don't have physical or any kind of access to the boot menu. I can just use the desktop interface :|.

Is there a way I can set it via. the terminal?

---

### Post by albinootje on 2009-04-25
> **n0an said:**
>  How do I boot with the other ones? I'm have learned a lot of stuff in one night, but not this :P.

:) Reboot, and then choose the 2.6.24-23 from the Grub boot menu.
You might first need to press the "escape" key at the right moment before the boot menu becomes visible.
Then use the arrow keys to move to the kernel that you want to boot, and hit <enter>.

---

### Post by n0an on 2009-04-25
> **albinootje said:**
> :) Reboot, and then choose the 2.6.24-23 from the Grub boot menu.
You might first need to press the "escape" key at the right moment before the boot menu becomes visible.
Then use the arrow keys to move to the kernel that you want to boot, and hit <enter>.

It's a server, mate. I'm not doing it on my desktop.

---

### Post by albinootje on 2009-04-25
> **n0an said:**
> It's a server, mate. I'm not doing it on my desktop.

Hmm.. okay, after doing a search-engine search I already saw that the kernel you're using is a customized kernel used by some VPS providers.

You will have to edit /boot/grub/menu.lst to make sure that the generic kernel is used.
Please make sure with :
```

dpkg -l|grep linux-image

```
which kernels are fully installed.

You can change the boot order by changing the "default" option in the grub configuration.
"default 0" means booting the first kernel in the list, "default 1" means booting the second kernel in the list, etc.

---

### Post by n0an on 2009-04-25
> admin@ks302332:~$ dpkg -l|grep linux-image
ii  linux-image                                2.6.24.23.25                      Generic Linux kernel image.
ii  linux-image-2.6.24-23-generic              2.6.24-23.52                      Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.23.25                      Generic Linux kernel image
These are the installed kernel images.

Also, the boot dir doesn't have grub on it.

> admin@ks302332:/boot$ ls
abi-2.6.24-23-generic              initrd.img-2.6.24-23-generic
boot.0800                          initrd.img-2.6.24-23-generic.bak
boot.0801                          map
bzImage-2.6.28.1-xxxx-std-ipv4-32  sarge.bmp
coffee.bmp                         sid.bmp
config-2.6.24-23-generic           System.map-2.6.24-23-generic
debian.bmp                         System.map-2.6.28.1-xxxx-std-ipv4-32
debianlilo.bmp                     vmlinuz-2.6.24-23-generic
Now what? :?

Alright, what I'm wanting to do is run a .NET Framework 2.0 based video encoder on my server. Mono-service and devel 1 and 2 along with wine don't allow me to run the app. The comman line says ".wine is now owned by you". 

I've tried almost everything to make it work, but no luck. No,w virtual machine is the only way to make that run in a windows' environment. What would you suggest?

---

### Post by albinootje on 2009-04-25
> **n0an said:**
>  Now what? :?

Try the suggestion in the comment here :
[http://forums.virtualbox.org/viewtopic.php?f=7&t=15161](http://forums.virtualbox.org/viewtopic.php?f=7&t=15161)
```

apt-cache search 2.6.28 | grep head

```
If that is not there, then ask the tech support for it.

---

### Post by n0an on 2009-04-25
That command doesn't return anything. I just checked the proc folder and it doesn't have any /modules dir in it. How to get one now?

Log file:

> Attempting to install using DKMS
  removing old DKMS module vboxdrv version  2.2.0

------------------------------
Deleting module version: 2.2.0
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/2.2.0/source ->
                 /usr/src/vboxdrv-2.2.0

DKMS: add Completed.

Error! Your kernel source for kernel 2.6.28.1-xxxx-std-ipv4-32 cannot be found at
/lib/modules/2.6.28.1-xxxx-std-ipv4-32/build or /lib/modules/2.6.28.1-xxxx-std-ipv4-32/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:143: Warning: using /usr/src/linux as the source directory of your Linux kernel. If this is not correct, specify KERN_DIR=<directory> and run Make again.
Makefile:178: *** Unable to find the folder to install the support driver to. Stop.

Here's my thread at the VirtualBox forum:

```
[http://forums.virtualbox.org/viewtopic.php?f=7&t=16944](http://forums.virtualbox.org/viewtopic.php?f=7&t=16944)
```

---

### Post by revival on 2009-05-20
Hello,

I also have a OVH server with their poorly built 'custom compiled kernel'. In order to install Virtualbox I had to recompile my own kernel with module support. After that, I installed Virtualbox from VB repository, but it was dropping this error:
[B]
Makefile:178: *** Unable to find the folder to install the support driver to. Stop.[/B]

The fix for me was to to create the folder manually. Try this as root:

*mkdir /lib/modules/2.6.28.1-xxxx-std-ipv4-32*

If you changed your kernel, change the line above, of course.

Hope it helps!
Bye

---

### Post by jkonrad on 2009-05-20
I am having all of the same errors as previous users. I first tried to install virtualbox and got this log error:

[I]Error! Your kernel source for kernel 2.6.27-11-generic cannot be found at
/lib/modules/2.6.27-11-generic/build or /lib/modules/2.6.27-11-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.
Failed to install using DKMS, attempting to install without
Makefile:140: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.[/I]

I then tried;
sudo apt-get install build-essential dkms
sudo /etc/init.d/vboxdrv setup

Still received the same error. So I tried this;
sudo apt-get install build-essential linux-headers-$(uname -r)

After a confirmation that build-essential is already the newest version, I received this error:

[I]Package linux-headers-2.6.27-11-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.27-11-generic has no installation candidate
[/I]
I'm not sure what else to try. I had a perfectly good working virtualbox on ubuntu 8.10. I then did an update to 9.04. Now I can not get virtualbox working. I'm trying and trying to install from their channel or the downloaded .deb package. I just can't get this to work. Any help?

---

### Post by albinootje on 2009-05-21
> **jkonrad said:**
> 
I'm not sure what else to try. I had a perfectly good working virtualbox on ubuntu 8.10. I then did an update to 9.04. Now I can not get virtualbox working. I'm trying and trying to install from their channel or the downloaded .deb package.

Looks like you're using Ubuntu Jaunty, but still booting with the Intrepid kernel. Please post the output of the following :
```

dpkg -l|grep linux-image

```

---

### Post by makno on 2009-06-21
i'm in the same situation, just trying to follow their giudes about installing your custom kernel but no luck. tried with kernelcheck and installed 2.6.30 but after reboot server doesn't ping at all. Now i'm recompiling 2.6.30 using kernelcheck again and the 2.6-config-xxxx-std-ipv4-32 enabling module support. i hoped that jaunty would automatically change the kernel when i did the dist-upgrade but it didn't happen and i was still stuck with the ovh kernel. It's really doing my head in now

---

