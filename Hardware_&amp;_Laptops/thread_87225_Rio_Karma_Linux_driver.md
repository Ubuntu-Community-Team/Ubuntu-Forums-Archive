---
title: "Rio Karma Linux driver"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by l3lackEyedAngels on 2005-11-07
Hi,

This is my first Ubuntu forums post. I've been using Breezy successfully for about three weeks now and I really like it. Ubuntu is the first Linux that I have used. Thanks to everyone who made it possible.

I own a 20GB Rio Karma. It is officially compatible with Linux, but only via lava and Ethernet, which just isn't as fast as USB. I would like to be able to plug the player with USB and add and remove files just like I used to do with XP.

I found a guide ([http://bobcopeland.com/karma/]("http://bobcopeland.com/karma/")) that claims to do what I want, but it's rather scary. I'm a newb and applying a patch or doing anything to the kernel is something that I'm not even comfortable trying.

Are the guide's instructions compatible with Ubuntu? If not, is there a compatible way? Is there an easier way?

I really want to put some more music on the player. I just need some reassurance and advice.

---

### Post by SickTwist on 2005-11-07
I own a Rio Karma. The problem with transfering via USB is that the Karma uses its own specialized file system so it cannot be mounted automatically like digital cameras and thumb drives. (This decision was made for better efficiency on the device, according to some of the Karma's developers that post(ed) on [Riovolution]("http://www.riovolution.com/")). I assume that patch you linked to attempts to read the Karma's filesystem but I have never tried it. If you're new to Linux, compiling a patched kernel might be more trouble than its worth.

I transfer to my Karma via ethernet with Rio Music Manager Lite (RMML) and it works great. You're right, it's not quite as fast as USB but unless one is filling the entire drive, the speed isn't a big deal (to me at least). The developer responsible for RMML has his work available [here]("https://rmml.dev.java.net/") including newer versions of RMML than the one offered on Rio's website. The newest version of RMML is [20040928]("https://rmml.dev.java.net/files/documents/1105/7250/rmmlite.jar"). You will need to install Java to run it. Directions for installing Java are all over the forums so I won't bother with that here.

I created /usr/rmml and copied rmmlite.jar and a Rio Karma picture (for the icon) there. Then I added a nice launcher on my menu for it. (The command for the launcher: java -jar /usr/rmml/rmmlite.jar).

If you do play with that kernel patch, please let us know how it works. Good luck and have fun!

---

### Post by l3lackEyedAngels on 2005-11-07
Great suggestions and thanks for the links. It's just that I only have one Ethernet jack in my dorm room and I have a crappy router that I've gotten in trouble for using. Using ethernet would be easier than USB in my case, but not very convenient or elegant.

---

### Post by SickTwist on 2005-11-08
You could add a second ethernet adapter to your computer and connect it to the Karma dock if you would rather not use a router. Just an idea.

EDIT: If you do decide to hook it up this way, you might need a crossover ethernet cable instead of a regular one ( Sorry, I'm not completely sure).

---

### Post by brallan on 2006-05-26
WIll this work for other devices that require the rio music manager firmware? 
this is just about the only thing that keeps me from wiping my linux partition.
I have a rio cali 128M with 512MB SD card, so it holds around 100 songs, and works fine, so I hate to toss it just so I can move over to linux.

Will it provide ogg support?

thanks,
brian

---

### Post by brallan on 2006-06-03
UPDATE: the ONLY driver which will work with the Rio Cali is the package rioutil. This works as su for me (type **sudo rioutil -l** to get started) but neither of the rioutils frontends worked for me: krioutil or jrioutil, which may be related to the fact that rioutil only warks as su.

---

### Post by alhizeer on 2006-08-28
How did you get the rioutil program to work correctly?  When I use it I get the following output:

Attempting to open Rio and retrieve song list.... failed!
Reason: Device or resource busy.
librioutil tried to use method: libusb

I've installed libusb and ran the program using sudo.  Do I need to change the mounting rules in fstab?

---

### Post by srf21c on 2006-09-29
> **SickTwist said:**
> 
I created /usr/rmml and copied rmmlite.jar and a Rio Karma picture (for the icon) there. Then I added a nice launcher on my menu for it. (The command for the launcher: java -jar /usr/rmml/rmmlite.jar).


Ok, tried getting the latest version of rmmlite.jar to run on my system as per sicktwist's instructions and got this error:

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.7)
   at java.awt.Window.<init>(libgcj.so.7)
   at java.awt.Frame.<init>(libgcj.so.7)
   at javax.swing.JFrame.<init>(libgcj.so.7)
   at com.rio.rmmlite.ChooseRmmlOrTaxi.main(ChooseRmmlOrTaxi.java:22)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...5 more
```

So I tried installing the package libgcj6-awt, but still getting the same error.   Next I tried installing the libgcj7-awt package and it works now,   Cool.

---

### Post by pmadavi on 2006-11-08
Hi guys, I've almost got this working, but when I enter the IP address of my Rio, I get an error:

> Failed to download the music database from the device.  Communication with the device failed or was rejected.  You will not be able to connect to your device until you have properly configured it with a network password.

Failed to download the music database from the device. caused by:
Communication with the device failed or was rejected. caused by:
com.rio.protocol.packet.StatusFailedException: You will not be able to connect to your device until you have properly configured it with a network password.
	at com.rio.protocol.packet.AbstractStatusReplyPacket.checkStatus(AbstractStatusReplyPacket.java:53)
	at com.rio.protocol.packet.AbstractStatusReplyPacket.read(AbstractStatusReplyPacket.java:60)
	at com.rio.protocol.PearlRequest.readPacket(PearlRequest.java:152)
	at com.rio.protocol.PearlRequest.readReply(PearlRequest.java:119)
	at com.rio.protocol.PearlRequest.writePacketAndReadReply(PearlRequest.java:172)
	at com.rio.protocol.PearlRequest.readLock(PearlRequest.java:378)
	at com.rio.protocol.PearlProtocolClient.readLock(PearlProtocolClient.java:278)
	at org.jempeg.protocol.AbstractSynchronizeClient.download(AbstractSynchronizeClient.java:147)
	at org.jempeg.manager.SynchronizeUI.download(SynchronizeUI.java:177)
	at org.jempeg.manager.SynchronizeUI$2.run(SynchronizeUI.java:155)
	at java.lang.Thread.run(Thread.java:595)

Does anybody know if this is a java problem, or if I need to set the password.  And if so, how the heck do I set the password if I can't access the sucker.

Sorry if these are dumb questions.  I'm a linux newb.

---

### Post by l3lackEyedAngels on 2006-11-08
Don't you set the pass with with the Rio Karma its self? Should be somewhere under settings.

---

### Post by pmadavi on 2006-11-12
Dude!

Thanks so much.  I didn't even know that network settings were on the Karma itself.  It's working great now!

---

### Post by srf21c on 2006-11-15
Sweet, I got the USB drivers for the Karma installed no problem according to the instructions here:  [http://bobcopeland.com/karma/](http://bobcopeland.com/karma/)

Had been battling performance problems and highly annoying application hangs while using Rio Music Manager Lite build 20040928, so I thought I'd give the USB driver a crack.

Got the Karma's filesystem mounted in short order, without any problems which was a pleasant surprise.

The file system is a little wacky however, so I'm not sure exactly how to work with it at this point. 

So I'm connected (great!), but I'm struggling to see the point of it all if I can't easily manage and view the songs on my Karma.  More info as I figure it out.  For now here's a little tidbit;  The output of the tree command (w/2 levels deep option) so you can get an idea of the directory structure.

|-- fids0
|   |-- _00000
|   |-- _00001
|   |-- _00002
|   |-- _00003
|   |-- _00004
|   |-- _00005
|   |-- _00006
|   |-- _00007
|   |-- _00008
|   |-- _00009
|   |-- _0000a
|   |-- _0000e
|   `-- _0000f
`-- var
    |-- config.ini
    |-- dynamic
    |-- dynamic0
    |-- dynamic1
    |-- dynamic3
    |-- dynamic4
    |-- smalldb
    |-- smalldb2
    `-- state

UPDATE:  ok, so I did a little more digging and found out you need to install two more programs in order to make the Karma usable over a USB connection.  LibKarma, and LKarmaFS.   I downloaded and untarred libkarma-0.0.6.tar.gz, (don't forget to install the libtagc0-dev package first) then tried to build the program using make, but it crapped out with the following errors.   

```
gcc -I../src -ltag_c -lz -Wall -pedantic playlist_show.c -o playlist_show ../lib/libkarma.a
gcc -I../src -Wall -pedantic karma_helper.c -o karma_helper -lusb
karma_helper.c:5:17: error: usb.h: No such file or directory
karma_helper.c: In function ‘usage’:
karma_helper.c:114: warning: implicit declaration of function ‘exit’
karma_helper.c:114: warning: incompatible implicit declaration of built-in function ‘exit’
karma_helper.c: In function ‘get_device’:
karma_helper.c:122: error: ‘usb_busses’ undeclared (first use in this function)
karma_helper.c:122: error: (Each undeclared identifier is reported only once
karma_helper.c:122: error: for each function it appears in.)
karma_helper.c:122: error: dereferencing pointer to incomplete type
karma_helper.c:124: error: dereferencing pointer to incomplete type
karma_helper.c:124: error: dereferencing pointer to incomplete type
karma_helper.c:126: error: dereferencing pointer to incomplete type
karma_helper.c:127: error: dereferencing pointer to incomplete type
karma_helper.c: In function ‘main’:
karma_helper.c:144: error: ‘usb_dev_handle’ undeclared (first use in this function)
karma_helper.c:144: error: ‘handle’ undeclared (first use in this function)
karma_helper.c:145: warning: ISO C90 forbids mixed declarations and code
karma_helper.c:241: warning: implicit declaration of function ‘usb_init’
karma_helper.c:243: warning: implicit declaration of function ‘usb_find_busses’
karma_helper.c:244: warning: implicit declaration of function ‘usb_find_devices’
karma_helper.c:249: warning: incompatible implicit declaration of built-in function ‘exit’
karma_helper.c:252: warning: implicit declaration of function ‘usb_open’
karma_helper.c:255: warning: implicit declaration of function ‘usb_detach_kernel_driver_np’
karma_helper.c:257: warning: implicit declaration of function ‘usb_claim_interface’
karma_helper.c:260: warning: incompatible implicit declaration of built-in function ‘exit’
karma_helper.c:263: warning: implicit declaration of function ‘usb_resetep’
karma_helper.c:274: warning: implicit declaration of function ‘usb_bulk_write’
karma_helper.c:275: warning: implicit declaration of function ‘usb_bulk_read’
karma_helper.c:295: warning: implicit declaration of function ‘usb_release_interface’
karma_helper.c:296: warning: implicit declaration of function ‘usb_close’
make[1]: *** [karma_helper] Error 1
make[1]: Leaving directory `/home/seth/software/libkarma-0.0.6/tools'
make: *** [tools] Error 2

```

Maybe something to do with a usb module?  ](*,)

---

### Post by mathewb on 2006-12-24
You have to install libusb-dev to compile libkarma.
After i did that, it worked and i was able to run make install.

---

### Post by LycoLoco on 2007-01-26
After running make install, what's the best way to use this? Can RMML interface with the USB interace?

---

### Post by bluesterror on 2007-02-28
Sorry to be late to the party, but as the author of the USB driver, maybe I can help :)

Ok first things first: the OMFS filesystem driver just presents the files in the raw format.  As you have seen, this is totally useless from a user's standpoint, but this is how all the songs are actually stored on the Karma's hard drive.

You pretty much need libkarma to do anything useful with the device.  LKarmaFS is nice if you plan on using the command line exclusively, but you do not need it.  Libkarma comes with some handy utilities, like 'riocp' in the tools/ directory which might be all you need.  I would get libkarma from the mercurial repository due to some recent nasty bugs being fixed.

My preferred way to use the Karma in Linux is via Banshee, but you'll need to install it from source.  There's this page here, which is out of date but I intend to update it in the next couple of days:

[http://bobcopeland.com/karma/banshee/]("http://bobcopeland.com/karma/banshee/")

---

### Post by chadlongstaff on 2007-05-17
[http://jcconnor.wordpress.com/2007/02/11/my-karma-is-better-than-your-karma/](http://jcconnor.wordpress.com/2007/02/11/my-karma-is-better-than-your-karma/)
^provides a fairly complete howto to get karma functioning with Amarok

---

### Post by VortX_Planet on 2007-10-25
I just got my Rio Karma working with omfs and libkarma in Gutsy. I generally followed the instructions at [http://linux-karma.sourceforge.net/Karma-HOWTO.html](http://linux-karma.sourceforge.net/Karma-HOWTO.html) but here is what I did step-by-step:

Using Synaptic:
Install the build-essential package (Gutsy asked for the Ubuntu CD)
Install the zlib1g-dev package
Install the libtagc0-dev package
Install the libusb-dev package

Download and extract the OMFS module and libkarma packages from [http://sourceforge.net/project/showfiles.php?group_id=155788](http://sourceforge.net/project/showfiles.php?group_id=155788) then build the packages
```
~$cd ~/omfs-0.7.5
~/omfs-0.7.5$sudo make module install_module
~/omfs-0.7.5$cd ~/libkarma-0.1.0
~/libkarma-0.1.0$sudo make install
```

Create a link so Ubuntu can find the compiled libkarma library
```
$ln -s /usr/local/lib/libkarma.so.0.1.0 /usr/lib/libkarma.so.0
```

Create a mount point for the Rio Karma
```
$sudo mkdir /mnt/karma
```

libkarma is now installed. To use, plug your Rio Karma into a USB port, then mount the second device that is detected (usually /dev/sda2). You may need to run dmesg to see what it is.
```
$dmesg
$sudo mount -t omfs /dev/sda2 /mnt/karma
```

The only thing I have used thus far is riocp, which does the one thing I need: put music on the player.

Before unplugging the Rio Karma from the USB port, unmount it.
```
$sudo umount /mnt/karma
```

The Karma will claim to still be communicating, but I have experienced no problems just unplugging it when it is idle and unmounted.

---

### Post by zaklad on 2007-11-19
I've managed to do this on Fiesty but not on Gusty:
I get errors when trying to build OMFS.
```
$ sudo make modules modules_install
make -C /lib/modules/2.6.22-14-generic/build M=/home/gil/Desktop/omfs-0.7.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/gil/Desktop/omfs-0.7.4/inode.o
/home/gil/Desktop/omfs-0.7.4/inode.c: In function ‘omfs_new_inode’:
/home/gil/Desktop/omfs-0.7.4/inode.c:85: error: dereferencing pointer to incomplete type
/home/gil/Desktop/omfs-0.7.4/inode.c:86: error: dereferencing pointer to incomplete type
make[2]: *** [/home/gil/Desktop/omfs-0.7.4/inode.o] Error 1
make[1]: *** [_module_/home/gil/Desktop/omfs-0.7.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

```

Any suggestions?

Thanks

---

### Post by mc.schroeder on 2007-12-10
I had that same error. I fixed it by adding
```
#include <linux/sched.h>
```
at the top of inode.c

---

### Post by asafm on 2008-04-29
Guys, 

Will the method described work with Rio Cali?

---

### Post by Jeffery Mewtamer on 2008-04-29
I am using Kubuntu Remix 8.04

I have successfully installed OMFS support following JCConner's "My Karma is better than you Karma" how-to, and I installed LibKarma via Synaptic.

I can now mount my Karma via command line, and I can view the raw contents via Dolphin.

If someone could provide me usable instructions on using riocp(I cannot make heads or tails of rio -h), I think I will be set. Ideally, I just want to copy the contents of ~/Music to my Karma with a single commandline statement.

---

