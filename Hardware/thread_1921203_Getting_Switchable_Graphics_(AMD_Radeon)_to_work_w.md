---
title: "Getting Switchable Graphics (AMD Radeon) to work with compiz, usp, conky, etc..."
date: 2012-02-06
forum: Hardware
---

### Post by sevenearths on 2012-02-06
If you have tried to get switchable graphics to work (using among others this [site]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide")) (i.e. you have an intel graphics card and an AMD one but you can't change them in the BIOS, the software/OS has to change them for you) on your laptop but have had limited success then try the following.

[INDENT]1. Make sure you install the 32bit support binaries for your 64bit system (that's if you have one and a 64bit OS) by typing the following into a terminal ```
sudo apt-get install ia32-libs
```

2. downloaded the latest [Catalyst driver install]("http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx") for linux.

3. Install it using it default selections. Example:

```
cd Downloads/
chmod 0777 amd-driver-installer-12-3-x86.x86_64.run
./amd-driver-installer-12-3-x86.x86_64.run
```

4. Reboot

5. In the terminal run the command ```
fgl_glxgears
``` and see if you have some nice gears in a window

6. In the terminal run the command ```
fglrxinfo
```. If any of the lines you get back from the system have 'AMD' in them then your install of the drivers was successful. For example my system gives me the following.

```
dave@dave-computer:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: **AMD** Radeon 6600M and 6700M Series
OpenGL version string: 4.2.11318 Compatibility Profile Context
```

7. Then try to enable ```
System > Preferences > Appearance > Visual Effects > Extra
```. If it fails with ```
Desktop Effect could not be enable
``` then...

8. Open a terminal and enter ```
compiz --replace ccp
``` if this return a line that has the following ```
Blacklisted PCI ID XXXX:XXXX detected
``` (where XXXX:XXXX is a set of numbers. it was ```
Blacklisted PCI ID 8086:0116 detected
``` in my case) remember these numbers and then...

9. Type the following into the console ```
sudo gedit /usr/bin/compiz
```. If gedit opens with a BIG RED ERROR saying ```
Could not open the file /usr/bin/compiz
``` that means that the file in hexadecimal (don't ask!). If this happen then...

10. Type the following in to the console ```
sudo apt-get install ghex
``` followed by ```
sudo ghex2 /usr/bin/compiz
``` (thanks to this [post]("http://ubuntuforums.org/showthread.php?t=1465935"))

11. in the hex editor that pops up scroll to the bottom of the file and then slowly scroll up looking for those number I told you to remember (I found mine about 1/3 of the way up the file).

12. When you have found the number replace any number with another number just to make it different (I replaced 8086:0116 to 8086:0117) and then save the file.

13. Then try to enable compiz effects again ```
System > Preferences > Appearance > Visual Effects > Extra
```.[/INDENT]

Hope this helps someone because I have been working on getting this working for weeks.

Thanks to:

[http://playingwithsid.blogspot.com/2009/08/how-to-override-compiz-blacklist.html](http://playingwithsid.blogspot.com/2009/08/how-to-override-compiz-blacklist.html)
[https://bbs.archlinux.org/viewtopic.php?id=57084&p=147](https://bbs.archlinux.org/viewtopic.php?id=57084&p=147)
[http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)
[http://webcache.googleusercontent.com/search?q=cache:-gDg3RYNwXwJ:https://github.com/MrMEEE/bumblebee/issues/394+compiz+%22Blacklisted+PCI+ID+8086:0116+detected%22&cd=4&hl=en&ct=clnk&gl=uk&client=firefox-a](http://webcache.googleusercontent.com/search?q=cache:-gDg3RYNwXwJ:https://github.com/MrMEEE/bumblebee/issues/394+compiz+%22Blacklisted+PCI+ID+8086:0116+detected%22&cd=4&hl=en&ct=clnk&gl=uk&client=firefox-a) << Big Help!!!
[http://ubuntuforums.org/showthread.php?t=1465935](http://ubuntuforums.org/showthread.php?t=1465935)

---

