---
title: "2 problems, sudo and startx"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by fireonyx on 2006-01-14
when I first start up, I get xserver failed.  The lines that look important are :
Skipping /usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o: no symbols found... along with _norm.o and _xforms.  Also /usr/X11R6/lib/modules/libfb.a:fbmmx.o
(EE) RADEON(0):[dri] DRIscreenInit failed.  Disabling DRI.  
xserver recieved fatal signal 4.

also, when I went in to edit the x11org.conf, I couldnt use sudo, I get the error no matter what command I used after sudo, including no command.  I got this error : Unable to lookup ubuntu via gethostbyname()

I am new to ubuntu, and ive done some basic stuff in linux before, so any help would be greatly appreciated!

Thanks, Fireonyx

---

### Post by 23meg on 2006-01-14
> 
also, when I went in to edit the x11org.conf, I couldnt use sudo, I get the error no matter what command I used after sudo, including no command. I got this error : Unable to lookup ubuntu via gethostbyname()Please post the contents of your /etc/hosts file if possible.

---

### Post by fireonyx on 2006-01-14
My hosts file is just 
127.0.0.1 localhost

And host.conf is
order hosts,bind
multi on

and hostname is 
ubuntu

Sorry for taking so long...  found out you cant mount without being a su or root, so had to reboot to debuging mode which gives me root access.

---

### Post by 23meg on 2006-01-14
Make your /etc/hosts look like this, obviously replacing HOSTNAME with your machine's name```
127.0.0.1 localhost.localdomain localhost HOSTNAME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Since you can't use sudo, you'll probably have to boot in recovery mode to do this (try "su" if you've enabled the root account). Type ```
nano /etc/hosts
``` to open the file with the nano text editor.

---

### Post by fireonyx on 2006-01-14
Ok, that has enabled my sudo...  makes life a bit easier :D  It still wont start xwindows..  I have an ATI Radeon XPRESS 200M.  It has shared memory with the main memory.  This is a laptop (Compaq Presario V2312) if that helps..

I also have the log moved to my windows partition, but its pretty long...

---

### Post by 23meg on 2006-01-14
Is it your Xorg.0.log file? You can post its contents [here]("http://sh.nu/p/") and give us the URL. It might help if you posted your xorg.conf as well.

Did you install the fglrx driver (assuming your card is supported)? If it isn't working, try switching to the "vesa" driver as a temporary solution by changing your "Driver" line in xorg.conf to "vesa" instead of "radeon" or "ati".

---

### Post by fireonyx on 2006-01-14
I found the problem with the xserver... it doesnt like the driver.  I have started the xserver, now I just have to get my wireless card to work (its a broadcom, which I have to use a partial driver, or use ndiswrapper.  Which means I have to download the new kernel, and compile it.  Which means I am back in windows till I dl it.  Thanks for the help... I may be back for some more...

Fireonyx

---

### Post by 23meg on 2006-01-14
Cool, hope you got it working with the ATI drivers.

---

### Post by BNAMack on 2008-05-16
> **23meg said:**
> Make your /etc/hosts look like this, obviously replacing HOSTNAME with your machine's name```
127.0.0.1 localhost.localdomain localhost HOSTNAME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Since you can't use sudo, you'll probably have to boot in recovery mode to do this (try "su" if you've enabled the root account). Type ```
nano /etc/hosts
``` to open the file with the nano text editor.
I know this thread is 2 years old but:  Here it is, May 2008 and your advice has helped me fix the same issue in Hardy Heron! There was no "thanks" button so have to do it here.   THANKS for your clear advice and even clearer example!

---

