---
title: "LIRC what worked for me"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by north on 2005-06-03
This was a headache and a half.  Almost broke down the first time mode2 gave me something resembling a useful output.  This is what eventually worked for me.  First things first: the current Hoary package doesn’t work.  It uses an out of date version of lirc which will result (after a lot of frustrating install crap) giving you modules with a .o extension rather than .ko.  The .ko are the ones used with the 2.6* kernel and you’ll run into a lot of grumpiness trying to get the .o ones to load.  I’m told it is possible to get them to work, but I eventually gave up.  The solution?  Get the current version (0.7.10) from lirc.org.

WHAT YOU WILL NEED:

1. linux-source	Get this from Ubuntu’s packet manager.  Just type linux-source in the search area.  You need this in order to get the setup script to recognize your version of linux and for adding bits to the kernel.

2. linux-headers	Get this the same way as the source.  You need it for the same reason.

3. [http://prdownloads.sourceforge.net/lirc/lirc-0.7.1.tar.bz2](http://prdownloads.sourceforge.net/lirc/lirc-0.7.1.tar.bz2)

WHAT YOU NEED TO DO:

1.	Open a root terminal.  I know, Ubuntu doesn’t like root.  Sudo works great, but I kept running into cascade problems where running a program under sudo wouldn’t allow some scripts to make changes as a su.  It was just easier this way.  To do this type **sudo password root  ** Pick a root password then log in with su.  Once this is all over you can go back to the Ubuntu recommended sudo method by typing **sudo password –l root**

2.	**cd /usr/src ** 	take a look – you should see the linux-source tar and the linux-headers directory here.

3.	**tar -xjvf linux-source-2.6.10.tar.bz2**	Extracting the linux-source tar.

4.	**ls lin*** Have you got a linux directory?  If not, make a symbolic link to the new linux-source folder you just extracted.  **ln -s /usr/src/linux-source-2.6.10 /usr/src/linux**  If you do make sure that it is a symbolic link to the new source directory with **ln –l /usr/src**

5.	Unpack the lirc tar you downloaded from above.  Usually it’ll be on the desktop after you download it.  You can unpack this one anywhere but a temporary folder in your home directory works.  Move into whatever directory the download is in and type **tar –xjvf lirc-0.7.1.tar.bz2  ** 

6.	**cd lirc-07.1**  It’ll either be called this or lircsomething.  Once here run the script **./setup.sh ** This loads a nifty little program that’ll let you make some pre compile choices about your hardware.  I’ve got a Silitek SM-1000.  The options are pretty self explanatory.  The only thing to remember if you’ve got a homebrew receiver is that for the first serial port the normal io port is 0x3f8 at IRQ 4.  

7.	Run the configure script.  It’ll ask you to do this right out of the ./setup.sh program.  If it doesn’t work see ./configure –help or the links at the end of the page and good luck to you.  

8.	type **make**

9.	type **make install**

10.	Half way there!  First lets check to make sure everything went smoothly.  If you've got a commercial reciever this step might not apply.  (see step 11) **cd /lib/modules/2.6.10-5-386/misc  ** You should have two files (lirc_dev and lirc_serial) here both ending in .ko.  If not go into the lib/modules directory and check if there’s a folder 2.6.10.  If there is go into it and it’s misc subdirectory and copy the contents from here to /lib/modules/2.6.10-5-386/misc (or 686 or whatever depending on your kernel version).

11.	The next problem comes with how the linux kernel accesses the serial port.  Basically it ties it up as ttys(#) and won’t share with lirc.  We need to free up ttyS# for use.  To do this (temporarily at least) type **setserial /dev/ttyS# uart none** where # refers to the ttyS device being used to acces your serial port (usually ttyS0).  NOTE: Remember back when you ran the ./setup.sh?  You probably chose the save and run configure option.  At the end of the configure script it will let you know which modules you need to load.  If it says something about serial then you need to load the two modules i was talking about earlier.  IF IT DOESN'T, if it says something like about not needing to load anything into the module then when you start lircd you will need to include the option -d /dev/ttyS0 (or whatever ttyS# corresponds to the serial port you are using.  This is because you're probably using a commercially built ir reciever instead of a homebrew one.  If that's the case there are drivers (such as the ones for the silitek SM-1000) which forgoe the need to load modules into the kernal.  If you're using one of these you don't need can ignore this step and step 12.  Just make sure to inclued the '-d /dev/ttyS0' in the command to start lircd.  This tells lircd where to get it's info from and, with a commercial reciever, it gets it from ttyS0 rather than lirc_dev.  *In fact, if you picked some commercial reciever in the ./setup.sh you won't have either lirc_dev or lirc_serial in your /lib/modules/2.whatever/misc folder so don't panic.*  

12.	With the serial port free for lirc to use we can begin starting up the modules.  First **cd /dev ** then **modprobe lirc_dev ** and  **modprobe lirc_serial** 

13.	Next make sure your hardware is plugged in to the first serial port and run **mode2** (note don’t use mode3 it’s for something else and’ll mess you up)  If it doesn't work type **ls lir*** and check for a lirc or a lirc0.  If it's lirc0 you need to let mode2 know that.  Try **mode2 -d /dev/lirc0** (or **mode 2 -d /dev/ttyS0** if you're commercial)

14.	Point a remote at the receiver and hit some buttons.  Now you’re on to setting up lircd.conf and lircrc.  Basically you need to get a file that lets lirc know what the remote you’ve got does.  This is lircd.conf.  The lirc.org website has a lot of these available and a nifty program called irrecord if you’ve got a remote they don’t have supported.  If you’ve made it this far you’re pretty much home free.  Check out the lirc.org website and the some of these links if you run into problems and for help setting up the conf files.

LINKS
[http://ubuntuforums.org/archive/index.php/t-20952.html](http://ubuntuforums.org/archive/index.php/t-20952.html)
[http://www.lirc.org/html/install.html#compiling](http://www.lirc.org/html/install.html#compiling)
[http://list.wylug.org.uk/pipermail/wylug-help/2005-May/003385.html](http://list.wylug.org.uk/pipermail/wylug-help/2005-May/003385.html)
[http://mythubu.free.fr/phpBB2/viewtopic.php?t=99&sid=2e87babca566ad76d09b4db797c10a84](http://mythubu.free.fr/phpBB2/viewtopic.php?t=99&sid=2e87babca566ad76d09b4db797c10a84) (IN FRENCH, but will probably translate for you)
[http://lirc.org](http://lirc.org)

Check out this guide!
[http://www.ubuntuforums.org/showthread.php?t=30612&highlight=lirc](http://www.ubuntuforums.org/showthread.php?t=30612&highlight=lirc)

Some potential troubleshooting stuff (don't expect too much here)

1.  You keep getting something went wrong in irrecord when trying to establish the buttons but everything else works.

when you ran ./setup.sh way back in the begining you basically built a specific driver into the lircd program.  If you built the wrong one (for example you are using a silitek SM-100 and checked the homebrew option) you'll end up with confusion.  To check type **lircd --driver=?** you can basically use anything instead of ? you're just trying to start lircd with an unsupported driver so it'll show you which drivers it does support.  output should look like this:
> lircd --driver=?
   Driver `?' not supported.
   Supported drivers:

How do you fix it?  There are two things you can do.  If there was a list of drivers that showed up you can try running lircd with a driver that'll match your hardware.  If not you need to recompile and basically start from the top.  There's a special driver called 'any' which will build lircd with a bunch of drivers in it so you can use multiple devices.  I haven't tried the 'any' driver yet and I seem to remember that it makes you build the modules yourself when you do it that way.

2.  ./configure keeps telling you junk about the not finding a proper linux tree.  

try the last [link](http://www.ubuntuforums.org/showthread.php?t=30612&highlight=lirc).  I didn't really run into this problem, but they seem to have a pretty good solution to it there.

3.  Can't get mode2 --device lirc0 to work even when you know it's there.  Don't forget the path! try **mode2 --device /dev/lirc0 ** or just change directories into /dev.  Also make sure /dev/lirc or /dev/lirc0 has the right permissions.  Try it as root.

4.  You can't get modeprobe to work.  

this one's a little more complicated because there's a lot that could be causing it.  First off make sure you use sudo or are logged in as root.  Next try **sudo update-modules ** followed by **sudo depmod -ae**.  Next double check that the files in /lib/modules/2.6.10-5-386/misc (or whatever your kernel directory is) exist and are of the .ko format.  If they arn't there try searching for lirc_ and stick them in the right folder.  If you can't find them start from the top.  Make sure you don't include the .ko when using modprobe; the format is modprobe lirc_serial NOT modprobe lirc_serial.ko. 
If it still doesn't work try some of the links provided for more details.

---

### Post by piedamaro on 2005-10-18
Thanks, very useful guide! It saves me from compiling a whole kernel.

---

### Post by budda on 2005-11-02
Thanks for the guide. Some notes:

You do not need to set a root password to get a root shell. The proper way to do it is call 'sudo -s' (or you could also do a sudo bash | tcsh whatever shell you like)

- To find out which kernel version you are currently running, use 'apt-cache search source | grep kernel'
- To get the current kernel .config file, cp /boot/config-*revision*  /usr/src/linux/.config
- To get the most recent lirc version, go to [http://sourceforge.net/projects/lirc/](http://sourceforge.net/projects/lirc/) and select LIRC, then the highest revision number

If you have a 2.4 kernel, linux-source is kernel-source and you can use apt-get lirc-modules-source to download (it is a tar.gz archive, needing tar -xzvf to extract (z instead of j because of the archive type. see man tar for more info). You can proceed as described in the modules/lirc/README file. 
But the make-kpkg generates a .o file even if you have a 2.6 kernel (which needs the kernel-o files .ko).

---

