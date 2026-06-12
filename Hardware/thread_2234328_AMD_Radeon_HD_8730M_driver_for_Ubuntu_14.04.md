---
title: "AMD Radeon HD 8730M driver for Ubuntu 14.04"
date: 2014-07-14
forum: Hardware
---

### Post by ShanDooo on 2014-07-14
Hello there. I have a problem installing graphic driver. I tried many tutorials, from this site and some other, to install fglrx with command line or manualy install driver from site and no luck. When installing manualy I were using latest Beta driver. Its AMD Catalyst 14.6 Beta.
Following the tutorials i manage to install driver with success (at least I think), but when i finish installation, before reboot i run:

```
[COLOR=#545454][FONT=arial]sudo amdconfig --initial -f[/FONT][/COLOR]
```

and i get this:

```
amdconfig: No supported adapters detected
```

And when i reboot PC got black screen and window that says its running low graphic mode. So i need to ctrl-alt-f2 and purge fglrx etc. 
I done some searches to see if maybe my graphics isnt supported but i didnt found. So does anyone know how should i solve this problem, and if do would be nice to write it step by step since im new to Ubuntu and noobish.

Some usefull informations (maybe):

Dell Inspiron 3521
Graphic: AMD Radeon HD 8730M
Processor: Intel® Core™ i3-3227U CPU @ 1.90GHz
OS: Ubuntu 14.04LTS 64bit

```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8730M] (rev ff)

```

```
~$ lspci | grep ATI
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8730M] (rev ff)

```

If you need more information let me know. 
Sorry for my bad english.

---

### Post by QIII on 2014-07-14
Hello!

Your system has what is known as "hybrid graphcs".

Please uninstall the fglrx driver and issue the following in the terminal:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then have a look at [this]("https://wiki.ubuntu.com/X/Config/HybridGraphics").

---

### Post by ShanDooo on 2014-07-14
First thank for answering.
> **QIII said:**
> Hello!

Your system has what is known as "hybrid graphcs".

Please uninstall the fglrx driver and issue the following in the terminal:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then have a look at [this]("https://wiki.ubuntu.com/X/Config/HybridGraphics").

I tried, but still low graphic mode and black screen after installing fglrx. Is there maybe any certian way to do it? I just can't manage to install it properly :(

And yeah when I do:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

it says:
```
mv: cannot stat &#8216;/etc/X11/xorg.conf&#8217;: No such file or directory
```

Edit:

Also tried this way: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) but still the same problem

---

### Post by QIII on 2014-07-14
Are you still able to get in to low graphics mode?

If so, the fact that xorg.conf could not be found is a clue.  By default, Ubuntu does not need an xorg.conf to run.  But when you install the fglrx driver, *it *does need an xorg.conf for initialization.

Did you initialize the ATI driver?  I included instructions for that in the command line instructions for installing the driver in the wiki in my signature -- if you used the command line method.  It is not supposed to be necessary if you use the GUI driver installation method, but to be honest I usually tell people to do it anyway for machines that have only ATI GPUs.  It gets a little tricky for hybrid system.

If you did not initialize and if you can get into a GUI even in low graphics mode and if you still have the fglrx driver installed, then please issue the following in the terminal to create the initial xorg.conf.  If it doesn't work, we'll try something else.

```
sudo amdconfig --initial
```

then reboot.

With your combination of GPUs, your setup *should *be muxless (no multiplexer).  But if the Intel GPU is acting as a mux (multiplexer),  this may not work at all.  Most of the industry uses a muxless system if the ATI card is an HD 6000 or beyond, but Dell has a habit of going its own way.

---

### Post by ShanDooo on 2014-07-14
No i purged fglrx so i can actualy see my screen. When i reboot after fglrx I get some window that gives me a choice for several options and says i can run low graphic mode (or something like that) but when i choose it, it says Wait one minute to blabla i gave it 10 minutes and nothing happend. So I did ctrl-alt-f2 and purged fglrx.

But I just installed again fglrx by your guide in wiki signature, here's output during the installation:

```
~$ sudo apt-get install fglrx fglrx-amdcccleReading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/64.2 MB of archives.
After this operation, 275 MB of additional disk space will be used.
Selecting previously unselected package fglrx.
(Reading database ... 328491 files and directories currently installed.)
Preparing to unpack .../fglrx_2%3a13.350.1-0ubuntu2_amd64.deb ...
Unpacking fglrx (2:13.350.1-0ubuntu2) ...
Selecting previously unselected package fglrx-amdcccle.
Preparing to unpack .../fglrx-amdcccle_2%3a13.350.1-0ubuntu2_amd64.deb ...
Unpacking fglrx-amdcccle (2:13.350.1-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up fglrx (2:13.350.1-0ubuntu2) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Loading new fglrx-13.350.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-30-generic
Building for architecture x86_64
Building initial module for 3.13.0-30-generic
Done.


fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-30-generic/updates/dkms/


depmod.........


DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up fglrx-amdcccle (2:13.350.1-0ubuntu2) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-30-generic
Processing triggers for libc-bin (2.19-0ubuntu6) ...
~$ 
```

And tried that code for generating fresh xorg.conf but it wont work. I tried several codes provided in that guide but always same output, here:

```
:~$ sudo amdconfig --initial
amdconfig: No supported adapters detected
:~$ sudo aticonfig --initial
aticonfig: No supported adapters detected
:~$ sudo aticonfig --adapter=all --initial
aticonfig: No supported adapters detected
:~$ sudo amdconfig --adapter=all --initial
amdconfig: No supported adapters detected
:~$
```

I wont reboot till next instructions since i can't generate xorg.conf because I`ll need again to purge fglrx to get back here :(

---

### Post by QIII on 2014-07-14
Let's go ahead and purge fglrx again now so that you at least have a working system.

If Dell is using a muxed arrangement, there is one more thing we might try, but you'll need to use the open source Radeon driver.

---

### Post by ShanDooo on 2014-07-14
Okay purging. Here's output:

```
:~$ sudo apt-get remove --purge fglrx fglrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fglrx* fglrx-amdcccle*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 275 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 328785 files and directories currently installed.)
Removing fglrx-amdcccle (2:13.350.1-0ubuntu2) ...
Removing fglrx (2:13.350.1-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Purging configuration files for fglrx (2:13.350.1-0ubuntu2) ...
dpkg: warning: while removing fglrx, directory '/usr/share/ati' not empty so not removed
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-30-generic
Processing triggers for libc-bin (2.19-0ubuntu6) ...
:~$ sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'fglrx-amdcccle-updates' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:~$
```


Is this ok, the bolded text, or i must delete it manualy with nautilus maybe?


Anyway, rebooted PC and Im here again. Seems like fglrx driver sucessfully purged. What should I do next? Sorry Im noobish but how to use that open source Radeon driver?

---

### Post by QIII on 2014-07-14
That looks fine.

If you have a GUI, the open source driver is running.

Now, a bit of cleanup to be sure things are all in order.

Let's make sure the xorg.conf is really gone (I'm going to have you rename it rather than remove it.  Removing it is permanent and immediate.  You may want it later).

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak2
```

If you get the "cannot stat" message, that is fine.

Reboot if you don't get the "cannot stat" message.

Now, make sure all the normally installed bits are there for the default driver.

```
sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg-core
```

You may get some "already installed" messages.  That is fine.

Reboot again (sorry!)

Finally, make sure fglrx is really gone

```
fglrxinfo
```

You should get a message to the effect that the driver is not present.

---

### Post by ShanDooo on 2014-07-14
Yup, its really gone.
```
mv: cannot stat &#8216;/etc/X11/xorg.conf&#8217;: No such file or directory
```
Reboot then:
```
:~$ sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/8,651 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 328491 files and directories currently installed.)
Preparing to unpack .../libgl1-mesa-dri_10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty_amd64.deb ...
Unpacking libgl1-mesa-dri:amd64 (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) over (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) ...
Preparing to unpack .../libgl1-mesa-dri_10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty_i386.deb ...
Unpacking libgl1-mesa-dri:i386 (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) over (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) ...
Preparing to unpack .../xserver-xorg-core_2%3a1.15.1-0ubuntu2_amd64.deb ...
Unpacking xserver-xorg-core (2:1.15.1-0ubuntu2) over (2:1.15.1-0ubuntu2) ...
Preparing to unpack .../libgl1-mesa-glx_10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty_amd64.deb ...
Unpacking libgl1-mesa-glx:amd64 (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) over (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) ...
Preparing to unpack .../libgl1-mesa-glx_10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty_i386.deb ...
Unpacking libgl1-mesa-glx:i386 (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) over (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libgl1-mesa-dri:amd64 (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) ...
Setting up libgl1-mesa-dri:i386 (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) ...
Setting up libgl1-mesa-glx:amd64 (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
Setting up libgl1-mesa-glx:i386 (10.3.0~git20140714.923f7844-0ubuntu0sarvatt~trusty) ...
Setting up xserver-xorg-core (2:1.15.1-0ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
:~$
```
Reboot.

And yeah, fglrx is gone.
```
:~$ fglrxinfo
fglrxinfo: command not found
```
Is everything okay for now?

---

### Post by QIII on 2014-07-14
Good for now.

Since it appears you have a muxed system, you might want to have a look at [this]("https://help.ubuntu.com/community/HybridGraphics").  Unfortunately, you can't use the fglrx driver.

It may seem a bit intimidating, so study it over a bit and don't launch into it unless you are very comfortable with it.

Feel free to ask questions, of course!

---

### Post by ShanDooo on 2014-07-14
Yeah its a bit confusing since Im new to this, but I'll give a look and try it when i get it. 

Seems like I'll have some questions but we'll see. I'll post here results when done.

Thanks alot for fast replays and your time! Cheers!

---

### Post by QIII on 2014-07-14
Sorry this has been such a pain, but the manufacturers have not made this a priority for Linux, so we are left with some frustrating results.

---

### Post by ShanDooo on 2014-07-15
True. Its kinda annoying sometimes but it is what it is. I hope they will change mind and do something for Linux users.

Anyway I took a try at [HTML]https://help.ubuntu.com/community/HybridGraphics#Enabling_vga_switcheroo[/HTML]
So I started at section "Enabling vga_switcheroo":
```
:~$ grep -i switcheroo 
/boot/config-*/boot/config-3.11.0-19-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.13.0-27-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.13.0-29-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.13.0-30-generic:CONFIG_VGA_SWITCHEROO=y

```
```
:~$ sudo ls -l /sys/kernel/debug/vgaswitcheroo/switch
-rw-r--r-- 1 dule root 0 Jul 15 15:17 /sys/kernel/debug/vgaswitcheroo/switch

```

Now at "Using vga_switcheroo" section I didnt know what to do. I dont understand whats those echo commands for, anyway i tried all of them with root account in terminal and nothing happend. But this last "cat" command gave some output:
```
:~$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
[FONT=Ubuntu][COLOR=#333333][sudo] password for dule:[/COLOR][/FONT]
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0
:~$
```
So how I understood it says my Integrated graphic card is on and Im using it right now.

After that I replaced all [COLOR=#333333][FONT=monospace]killall -u "$USER"[/FONT][/COLOR] with [COLOR=#333333][FONT=monospace]gnome-session-save --logout in R[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]oberto Martinez Switching script, saved it on desktop with name "switch_between_cards.sh" and made it executable. 

Now on [https://help.ubuntu.com/community/HybridGraphics#Enabling_vga_switcheroo](https://help.ubuntu.com/community/HybridGraphics#Enabling_vga_switcheroo) site it says i need to add some line in this file [/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]/etc/init.d/rc.local [/FONT][/COLOR]**[COLOR=#333333][FONT=Ubuntu]but on [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/) site I need to add it in this file: **/etc/rc.local**[/FONT][/COLOR][B][COLOR=#000088] 
[/COLOR][/B][COLOR=#333333][FONT=Ubuntu]In first file (**/etc/init.d/rc/local**) I dont have exit 0. It looks like this:
[/FONT][/COLOR]```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO




PATH=/sbin:/usr/sbin:/bin:/usr/bin


. /lib/init/vars.sh
. /lib/lsb/init-functions


do_start() {
    if [ -x /etc/rc.local ]; then
            [ "$VERBOSE" != no ] && log_begin_msg "Running local boot scripts (/etc/rc.local)"
        /etc/rc.local
        ES=$?
        [ "$VERBOSE" != no ] && log_end_msg $ES
        return $ES
    fi
}


case "$1" in
    start)
    do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac 
```


In second file (**/etc/rc.local**) i have echo 0, I added 2 lines before exit 0 and it looks like this:
```
#!/bin/sh -e#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
chown "dule" /sys/kernel/debug/vgaswitcheroo/switch # change "username" with your user name
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
exit 0 
```

When i run script this window appears:
[ATTACH=CONFIG]254733[/ATTACH]

But when I click on switch to Integrated (or Discrete) that window dissapears and nothing happens. I think something is wrong with chown line in step before. Seems like I dont have root access for switcheroo or something (Im just guessing im noob).

How I saw some screenshots on that other site and in script window next to listed graphic cards it have (*)/( ) and Power On/Off which indicates if graphic is working or not (I think thats it) but I dont have it.

So do I need maybe to write only [COLOR=#333333][FONT=UbuntuMono]chown dule /sys/kernel/debug/vgaswitcheroo/switch[/FONT][/COLOR] line in **/etc/init.d/rc/local **and add next line exit 0 just before esac line? Or something else is needed?

---

