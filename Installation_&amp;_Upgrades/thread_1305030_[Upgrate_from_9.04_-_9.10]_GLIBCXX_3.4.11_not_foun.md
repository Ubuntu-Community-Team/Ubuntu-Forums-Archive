---
title: "[Upgrate from 9.04 - 9.10] GLIBCXX_3.4.11 not found"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Conzar on 2009-10-29
I upgraded from 9.04 to 9.10 today using the alternate CD method.  I also enabled the internet patch feature too.

After the upgrade, when I try to use apt-get, I get the following error:
"apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by apt-get)
"apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libapt-pkg-libc6.10-6.so.4.8)

Anyone know what I can do to solve this problem?
Thanks

---

### Post by tony_wh on 2009-10-30
I too have this problem.

I have nothing but the upmost respect for the opensource community but I'm afraid upgrading from Intrepid to Karmic has been a bit of a disaster;
1) Right-click does nothing
2) When I'm asked for my administrator password, nothing happens
3) I can't access my home folder
4) I can't open nautilus
5) I lost all my desktop files (they were unimportant but still...)
6) Firefox icons are gone
7) I can't, as a result, access any of my files (as they were on an different partition)

I've found these after the first hour of discovery - I'm sure there's more but if there's anyone out there who can at least help with this, I can perhaps begin to put the rest back together.

Thanks

---

### Post by tony_wh on 2009-10-30
Ok - I've found a fix that works for me here:

[http://ubuntuforums.org/showthread.php?t=808045](http://ubuntuforums.org/showthread.php?t=808045)

I had to go into terminal then cd to the directory that was quoted in the error when I typed sudo nautilus

The fix in the post restored my desktop, fixed nautilus, allowed me to enter my password for administrative stuff.

Phew!!

---

### Post by Conzar on 2009-11-02
How did you solve the GLIBCXX_3.4.11 problem?

---

### Post by tony_wh on 2009-11-02
The solution solved the apt-get problem too.

---

### Post by Conzar on 2009-11-11
> The solution solved the apt-get problem too.
```
sudo mv libstdc++.so.6 libstdc++.so.6.orig
sudo mv libgcc_s.so.1 libgcc_s.so.1.orig
```
It did not work for me.  In fact, firefox crashes on startup when these libraries are moved.

Anyone else know what my problem might be?

Thanks

---

### Post by fdv on 2009-11-13
I'm guessing the LD_LIBRARY_PATH variable is set, causing binaries to dynamically link to libstdc++ residing in non-standard places. Check this by issuing the command 'echo $LD_LIBRARY_PATH'. LD_PRELOAD is another option.

Anyway, all the references to libstdc++.so.6 I've seen in this thread (and the thread referred to) list it in non-standard places, and whether the linkage is due to meddling with environment variables or compile time linking, I would presume that the programs having issues really want to use /usr/lib/libstdc++.so.6 instead of e.g. /usr/local/lib/libstdc++.so.6 (note 'local' in the path). If these versions differ, you're likely to have problems.

So, check the environment variables and unset the LD_* variables mentioned above if they are there (e.g. 'unset LD_LIBRARY_PATH'). If that fails, check where the binary complaining about the linkage comes from ('dpkg -S /path/to/binary). I had installed libstdc++6.4.3-dbg explicitly, so when libstdc++ was upgraded to 6.4.4, linking against the 6.4.3 debug library didn't work too well. In my case, the fix was removing that lib (or upgrading it).

You can also explicitly load the right library by prepending 'LD_PRELOAD=/usr/lib/libstdc++.so.6' to the command line you're using, but this subverts the programs dynamic library handling, so don't use it as a general solution, it's a work-around. It's better to try and find the problem and fix it.

---

### Post by Conzar on 2009-11-13
So the LD_LIBRARY_PATH isn't set as shown below.

```
:~$ echo $LD_LIBRARY_PATH

:~$ dpkg -S /usr/bin/apt-get 
apt: /usr/bin/apt-get

```

I am able to use the LD_PRELOAD and get apt-get to work correctly.  So you are correct, looks like apt-get is pointing to /usr/local/lib/ instead of /usr/lib.  

There are other programs that this effects too such as natilus.  

Any ideas of how to fix this?  Can I use apt-get to update gcc?

---

### Post by fdv on 2009-11-13
Just to make sure, what is the output from 'ldd /usr/bin/apt-get'?

---

### Post by Conzar on 2009-11-13
```
:~$ ldd /usr/bin/apt-get 
/usr/bin/apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/bin/apt-get)
/usr/bin/apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libapt-pkg-libc6.10-6.so.4.8)
	linux-gate.so.1 =>  (0x001cf000)
	libapt-pkg-libc6.10-6.so.4.8 => /usr/lib/libapt-pkg-libc6.10-6.so.4.8 (0x0075f000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0x00346000)
	libstdc++.so.6 => /usr/local/lib/libstdc++.so.6 (0x001d0000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00110000)
	libgcc_s.so.1 => /usr/local/lib/libgcc_s.so.1 (0x008dd000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x0034a000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00f27000)
	/lib/ld-linux.so.2 (0x009a1000)

```

---

### Post by fdv on 2009-11-16
Well, I can't say I can see what's causing this. Provided /usr/lib/libstdc++.so.6 exists, I don't know what, other than LD_PRELOAD or LD_LIBRARY_PATH, could thwart which dynamic libraries a given binary links to. Maybe a broken library? In that case it could mean your system is compromised, but I wouldn't jump to conclusions, I'm no expert in these things.

I think I'd at least try re-installing apt ('apt-get install --reinstall apt' as root), you might have to prepend that command with 'LD_PRELOAD=/usr/lib/libstdc++.so.6', but again, be careful with preloading libraries. Should the re-install of apt fail somehow, you could find yourself without a package manager, making it more difficult to install and fix packages (though you can always use dpkg directly).

---

### Post by mishkind on 2009-11-17
Hi,
I'm having a similar issue. I installed a .deb file, and after doing so, all my previous dynamically linked programs that worked fine in 9.10, now link libstdcc++ to a non-standard place (in my case /opt/SAS/JMP8/lib/libstdc++.so.6), and as a result don't work.

For example:
```
thinkpad[~/JMP_8.0.1_DEB]$ einstein 
einstein: /opt/SAS/JMP8/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by einstein)
thinkpad[~/JMP_8.0.1_DEB]$ ldd `which einstein `
/usr/games/einstein: /opt/SAS/JMP8/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/games/einstein)
	linux-gate.so.1 =>  (0x00ad3000)
	libSDL_ttf-2.0.so.0 => /usr/lib/libSDL_ttf-2.0.so.0 (0x00d3e000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00183000)
	libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0x00202000)
	libz.so.1 => /lib/libz.so.1 (0x00b25000)
	libSDL_mixer-1.2.so.0 => /usr/lib/libSDL_mixer-1.2.so.0 (0x00be7000)
	**libstdc++.so.6 => /opt/SAS/JMP8/lib/libstdc++.so.6 (0x00715000)**
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00110000)
	**libgcc_s.so.1 => /opt/SAS/JMP8/lib/libgcc_s.so.1 (0x00136000)**
```

If I go ahead and set my LD_LIBRARY_PATH, it takes care of the problem.

```
thinkpad[~/JMP_8.0.1_DEB]$ export LD_LIBRARY_PATH=/usr/lib/:/lib
thinkpad[~/JMP_8.0.1_DEB]$ ldd `which einstein `
	linux-gate.so.1 =>  (0x00e3d000)
	libSDL_ttf-2.0.so.0 => /usr/lib/libSDL_ttf-2.0.so.0 (0x00997000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00114000)
	libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0x00b99000)
	libz.so.1 => /lib/libz.so.1 (0x00f06000)
	libSDL_mixer-1.2.so.0 => /usr/lib/libSDL_mixer-1.2.so.0 (0x00928000)
	**libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00193000)**
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00471000)
**	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00b11000)**

```

I would really like to know how/what/where was set in order for my library paths to be mixed up and to not show up in my environment:
```
thinkpad[~/JMP_8.0.1_DEB]$ env
ORBIT_SOCKETDIR=/tmp/orbit-mishkin
SSH_AGENT_PID=2717
HOST=thinkpad
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=bc21c0c08b8203b474b4f7cb4af0cea7-1258435619.40349-690080672
GTK_RC_FILES=/etc/gtk/gtkrc:/home/mishkin/.gtkrc-1.2-gnome2
WINDOWID=62930176
OLDPWD=/home/mishkin
GTK_MODULES=canberra-gtk-module
USER=mishkin
SSH_AUTH_SOCK=/tmp/keyring-g8QcYa/socket.ssh
GNOME_KEYRING_SOCKET=/tmp/keyring-g8QcYa/socket
SESSION_MANAGER=local/thinkpad:@/tmp/.ICE-unix/2678,unix/thinkpad:/tmp/.ICE-unix/2678
USERNAME=mishkin
DESKTOP_SESSION=gnome
PATH=/home/mishkin/bin:/usr/local/bic/bin:/home/mishkin/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/mishkin/JMP_8.0.1_DEB
EDITOR=emacs
GDM_KEYBOARD_LAYOUT=us
LANG=en_US.UTF-8
GNOME_KEYRING_PID=2663
GDM_LANG=en_US.UTF-8
GDMSESSION=gnome
SPEECHD_PORT=7560
SHLVL=1
HOME=/home/mishkin
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=mishkin
CVS_RSH=ssh
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-NiXvzkcAG0,guid=6cf201132e8e6dd8dce0fa404b023423
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
LESSOPEN=| /usr/bin/lesspipe %s
ARCH=linux
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/var/run/gdm/auth-for-mishkin-shIuOb/database
_=/usr/bin/env
```

---

### Post by mishkind on 2009-11-17
Update:
It seems the .deb I installed changed the contents of /etc/ld.so.conf to:

```
thinkpad[/etc]$ cat ld.so.conf
include /etc/ld.so.conf.d/*.conf

/opt/SAS/JMP8/lib
```

By taking out the /opt/SAS/ line, and then running
```
sudo ldconfig
```

All my library paths are back to normal, without having to explicitly set any environment variables.

The one problem is that the program I wanted to run, then will not work as it needs libraries in this non-standard place. I fixed this by doing:

```
thinkpad[/opt/SAS/JMP8]$ LD_LIBRARY_PATH=/opt/SAS/JMP8/lib/ ./jmp

```

If anyone knows of a better, more general solution to fix this sort of problem please let me know.

---

### Post by fdv on 2009-11-17
Ah, this makes things clearer. I mistakenly thought that binaries linked specificly to dynamic libraries, but unless you link them with -rpath, they will use system defaults, defined by /etc/ld.so.conf. /lib and /usr/lib* are special, as they are not listed in /etc/ld.so.conf, but apparently used by ldconfig by default.

In /etc/ld.so.conf.d/libc.conf, I have listed /usr/local/lib (karmic). This seems very strange to me, as I can't see why libc would want to search there by default. This also means that if you have libraries in /usr/local/lib that are named the same as in /usr/lib, the ones under /usr/local/lib will have priority. If anybody knows why libc-bin has chosen to do this, please enlighten me.

Conzar: I wonder which package has put C++ standard libraries under /usr/local/lib, can you do a 'dpkg -S /usr/local/lib/libstdc++.so.6'? This package is probably the culprit, and there's no easy way to get around it (as I know). If you wish to keep this package, you have two options as far as I can see, either:

 1) Move the library to a different, non-standard, place and start the program using mishkind's solution: 'LD_LIBRARY_PATH=/some/nonstandard/location <some program>', or:

 2) Add /usr/lib to the _beginning_ of /etc/ld.so.conf and use the LD_LIBRARY_PATH trick: 'LD_LIBRARY_PATH=/usr/local/lib <program>'.

I'd probably go for 1, as putting /usr/lib explicitly in /etc/ld.so.conf seems very wrong.

mishkind: Thanks for the input, it made it all clearer. I'd think the package you're referring to is broken and needs to be fixed, possibly by linking using -rpath. Adding a non-standard library path to ld.so.conf where you put libraries that are almost identical to ones under /usr/lib seems dangerous at best. I can't see any better solution than the one you outlined (except getting the maintainer to fix the package).

---

### Post by Conzar on 2009-11-17
```
etc$ sudo dpkg -S /usr/local/lib/libstdc++.so.6
dpkg: /usr/local/lib/libstdc++.so.6 not found.

```

Still not sure whats wrong :(

---

### Post by fdv on 2009-11-19
That means that /usr/local/lib/libstdc++.so.6 was not installed by apt, and comes from some other source. It is likely that some program uses this lib, but there is no simple way to tell as long as it hasn't been installed by the package manager. I'd suggest moving it and see if your system behaves afterwards. I'd presume you're likely not to have issues afterwards, as you have a somewhat newer libstdc++6 installed under /usr/lib, but I'm not certain.

You don't need to be root to run dpkg queries, btw. :-)

---

### Post by Conzar on 2009-11-24
You are correct.  By just removing the library (both the symoblic link as well as the hard file), this solves the problem.

Although, the "software center" doesn't show any installed programs plus it doesn't show any available to download programs either.

---

### Post by dinesh2n on 2010-01-08
Hi...this problem I also faced. as below
$lyx
lyx: /home/shoonya/OpenFOAM/ThirdParty-1.6/gcc-4.3.3/platforms/linux/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by lyx)

I just cut that folder "OpenFOAM" folder for a while and pasted somewhere else. and again ran
 $lyx
it just ran ....

so this means the "OpenFOAM" folder was using different version of gcc than gcc version installed in my ubuntu 9.10. So when I was running lyx, it was taking gcc of OpenFOAM folder instead asking for root ....
for confrimation when I ran cammand lyx 
#lyx
it perfectally ran even that "OpenFOAM" folder was in home folder (i.e. is not displaced)

---

### Post by aarongc on 2010-01-16
I had exactly this problem too. Turned out it was caused by a line in my ~/.bashrc which pulled in stuff from an OpenFOAM bashrc. I think I put this in manually when following some installation instructions for OpenFOAM a year or so ago. Anyway, commented it out and now apt-get, python, etc are working again. Haven't tried FOAM yet.

---

### Post by vnarmy on 2010-01-22
> **Conzar said:**
> You are correct.  By just removing the library (both the symoblic link as well as the hard file), this solves the problem.

Although, the "software center" doesn't show any installed programs plus it doesn't show any available to download programs either.

I tried ```
 sudo mv libstdc++.so.6 libstdc++.so.6.orig 
```

It works too.

Thanks fdv and Conzar.

---

### Post by vnarmy on 2010-01-22
The error appear again after I update: ```
Upgraded the following packages:
python2.4 (2.4.6-1ubuntu3) to 2.4.6-1ubuntu3.2.9.10.1
python2.4-minimal (2.4.6-1ubuntu3) to 2.4.6-ubuntu3.2.9.10.1
```

---

### Post by mukau on 2010-12-06
I had the exact same problem though I upgraded from 8.04 to 10.04 (lucid).

On my system, the problem manifested itself in numerous applications failing to start which all could be traced back to the "GLIBCXX_3.4.11 missing" problem.

As it turned out, the file /etc/ld.so.conf.d/libc.conf contained the line: ```
/usr/local/lib
``` I changed this to: ```
/usr/lib
``` and did: ```
sudo ldconfig
``` and all started working just normal.
Thanks for the help everyone.

---

### Post by AnveshakAkula on 2010-12-29
> **mukau said:**
> I had the exact same problem though I upgraded from 8.04 to 10.04 (lucid).

On my system, the problem manifested itself in numerous applications failing to start which all could be traced back to the "GLIBCXX_3.4.11 missing" problem.

As it turned out, the file /etc/ld.so.conf.d/libc.conf contained the line: ```
/usr/local/lib
``` I changed this to: ```
/usr/lib
``` and did: ```
sudo ldconfig
``` and all started working just normal.
Thanks for the help everyone.

even better, change it to```
 /usr/local/lib:/usr/lib
``` then do ```
sudo ldconfig
```

---

### Post by Courage on 2011-07-15
[https://bbs.archlinux.org/viewtopic.php?id=86809](https://bbs.archlinux.org/viewtopic.php?id=86809)

the forum moderator's solution from above site works...

how to create symlink-http://www.cyberciti.biz/faq/creating-soft-link-or-symbolic-link/\

what worked for me-the files to which symlink creation has been instructed..i just copied those files directly and pasted in the $MATLABROOT/sys/os/{glnx86,glnx164} folder....
 still did not work and i restarted the comp and it worked like a charm that it is supposed

---

