---
title: "Ubuntu fail's to boot X in live, but boots ok in VMWare virtual machine"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by hq4ever on 2005-10-05
Hi folk's
I have this [1] hd setup on my IBM(Lenovo) r50e laptop.
The main OS is use for every day work is WinXP.SP2, unwhich I've installed ubuntu 5.04 using the VMWare virtual machine software package.

During the VMWare setup I've instructed the software to use the physical drive partitions as it's storage space.

The end result is this : I have both XP & ubuntu installed in a dual boot configuration, both are operational and bootable using grub.

The problem is that while in the Virtual Machine emulated environment Ubuntu boots X without error's; From the "real" boot, the X server fails to load with some error (which I can not just "copy paste" from the screen...)

How can I tell the X server to use different configuration scheme on each of the boot environment? and, How can I instruct Ubuntu to create another xorg.conf file like the one created during the first installation (which was done from VMWare) ?

Thank you, 
Maxim.




[1] : ```
root@ubuntu:/home/hq4ever # cfdisk -P s /dev/hda
Partition Table for /dev/hda
First       Last
# Type       Sector      Sector   Offset    Length   Filesystem Type (ID) Flag
-- ------- ----------- ----------- ------ ----------- -------------------- ----
1 Primary           0    43243199     63    43243200 HPFS/NTFS (07)       Boot
Primary    43243200    43246979      0        3780 Free Space           None
2 Primary    43246980    57898259      0    14651280 Linux (83)           None
3 Primary    57898260    58605119      0      706860 Extended (05)        None
5 Logical    57898260    58605119     63      706860 Linux swap / So (82) None
```

---

### Post by mlomker on 2005-10-05
> How can I instruct Ubuntu to create another xorg.conf file like the one created during the first installation (which was done from VMWare) ?


```

sudo dpkg-reconfigure xserver-xorg

```

That runs you through creation of another /etc/X11/xorg.conf file.  You'll want to back up the current version first.  Assuming that you've installed the VMWare tools it modifies that file to load the special versions of the video and mouse drivers.

You could boot up to a command prompt (the 'rescue' mode) and manually copy your xorg.conf files back and forth prior to running X-windows.  If you are familiar with shell scripting you could write a script that detects which network driver is loaded (vmware uses an emulated card that is probably different than your real one) and then copy over the xorg based upon which one is loaded.

---

### Post by hq4ever on 2005-10-06
At first, Thank you for the idea of running a initialization script based on the identifier of the LAN device - good idea, I will be trying to implement this today and will report back.

Second, I was wondering if such a thing (i.e. different xorg.conf files) using lernel boot parameters [1], maybe I could just create another entry in grub's menu and be done with that ?


Thank you, 
maxim.

[1] : [http://lxr.linux.no/source/Documentation/kernel-parameters.txt](http://lxr.linux.no/source/Documentation/kernel-parameters.txt)

---

### Post by mlomker on 2005-10-06
> Second, I was wondering if such a thing (i.e. different xorg.conf files) using lernel boot parameters [1], maybe I could just create another entry in grub's menu and be done with that ?


There isn't a magic parameter that will tell the system to copy xorg.conf files back and forth.  There probably is a way to set an environment variable that'd tell your script how it should run.  Either way you're going to have to write a script.

You could do two completely separate installs of Ubuntu and select between them in grub, of course.  If they shared the same /home partition then your desktop would look the same.

I ran across a [nice website]("http://linuxcommand.org/writing_shell_scripts.php") today with scripting and command basics.  I'm reading through it and have learned a few things!  Can't ask for better than that.

---

### Post by hq4ever on 2005-10-06
Thank for this site, I have visited it before.
Another highly recommended one is : [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)
Onto the subject : Could you please point to the bash script that is responsible for the actual launching the X server ?
I am thinking that instead of coping the xorg.conf file back and forth, I will create two files: xorg.conf & xorg-vmware.conf; those by default the system will boot the regular xorg.conf file, but when run from the vmware environment the xorg server will be instructed to use the alternative conf file.
This can be checked by querying the return value of the **grep** utility, something like : ```
lspci | grep -i 'vmware svga ii' 2>&1 >/dev/null 
[[$? -eq 0]] && XORG_CONF = xorg-vmware.conf
```

---

### Post by mlomker on 2005-10-06
> Could you please point to the bash script that is responsible for the actual launching the X server ?

I'm not entirely clear on how all the scripts fit together, but the key file seems to be /etc/X11/Xsession.

---

### Post by hq4ever on 2005-10-08
I am sorry to report, but I am failing to find the correct script that is directly responsible for the launching of the X server.

Could you please tell me how the X server main executable is named?
maybe I could place a breakpoint into it to see who called it (that is if it's ELF).

Thank you for your help.

---

### Post by mlomker on 2005-10-08
> Could you please tell me how the X server main executable is named?
maybe I could place a breakpoint into it to see who called it (that is if it's ELF).


/usr/X11R6/bin/xinit

---

### Post by hq4ever on 2005-10-08
[QUOTE=mlomker]/usr/X11R6/bin/xinit[/QUOTE]

Thank you.

At first I thought that the script responsible for loading the X server is **/usr/X11/bin/startx**, and those all my efforts concentrated in this file.
It now turns out the this script is not being even sourced when ubuntu loads it's X window system.

The X server is being launched from **/etc/init.d/gdm** using the syntax : 

```
start-stop-daemon --start --quiet --pidfile /var/run/gdm.pid --name gdm --exec /usr/bin/gdm >/dev/null 2>&1
``` It is unclear to me how this is possible? After all, it's the Xorg server that should be launched first, before the Display Manager, isn't it? Or is the gdm executable it self call's xinit to bring the server up ?

I'm in a bit confused about the subject...

---

### Post by mlomker on 2005-10-08
> I'm in a bit confused about the subject...

I'd recommend making a post on the Developer's forum that summarizes what you are trying to do and what you've looked at so far.  I think this is outside the scope of what end-users (or system administrators like myself) would understand.

---

