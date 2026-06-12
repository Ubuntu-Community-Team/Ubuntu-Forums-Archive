---
title: "handy R4000 update script"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by doog on 2005-09-13
I threw together an installation/update package for the Compaq R4000 laptop. It does the following:
[B]
1)  build a new kernel with the atiixp/IDE-DMA fix and the 2X CPU speed fix[/B]
[INDENT]installs kernel source and needed packages, copies patched files over kernel files,[/INDENT]
            [INDENT]builds kernel and installs it.[/INDENT]
**2) update the grub loader to pass timerhack to the kernel on boot**
            [INDENT]adds timerhack to #kopt line in grubs menu.lst and sets the new kernel as the default boot kernel[/INDENT]
**3) install the Wifi driver( ndiswrapper and needed driver ).**
            [INDENT]you'll have to enter your essid and wep key via the GUI based Network configuration utility.[/INDENT]
         [INDENT]You'll find it under this menu structure: *System*->*Administrator*->*Networking*[/INDENT]
**4) install the ATI FGLRX driver for 2D/3D support with updated xorg.conf and Synaptic Touchpad support**
           [INDENT] installs and patches the fglrx driver, compiles it and copies a new xorg.conf( 1024x768 res )[/INDENT]

Just install Ubuntu 5.04 as usual, when the system finally boots to the GUI/login screen( drumroll ), you'll need to go to the Ctl-Alt-F1 console, login, get the startup script and run it to start the whole update process. If you try to login to the GUI, it'll lock up the system( Xorg server ). To patch your system, just type these simple commands after you login to the Ctl-Alt-F1 console:
   wget [http://www.pellicosystems.com/linux/Ubuntu/r4000-start](http://www.pellicosystems.com/linux/Ubuntu/r4000-start)
   sudo bash ./r4000-start

NOTE: This requires the Ubuntu Install CDROM and a working wired network connection.

If you want to see all of what's going on then you can download the files package directly with this:
    wget [http://www.pellicosystems.com/linux/Ubuntu/r4000-install.tgz](http://www.pellicosystems.com/linux/Ubuntu/r4000-install.tgz)
   tar -xvzf r4000-install.tgz

I've run the script/process a couple of times to verify it and it seems pretty complete now. Ofcourse, I could be overlooking something so I'll answer any questions about this script and process in this forum.

UPDATES:
09/14/05- I updated the ATI driver portion so it uses wget to retrieve the fglrx driver from ATI, tests for the file, apt-get's alien and uses it to convert the rpm driver file to a deb file before continuing. This reduced the original package size by about 5MB and let's ATI know the file is getting downloaded.
09/17/05- swapped the Wifi and ATI driver installs so that the wired network is used during the ATI driver install and then the WiFi networking is installed and configured.
09/19/05- The script no longer requires the user to run a 2nd script( doit2 ) and now the WiFi install is done during the first phase. Only the ATI driver install occurs in the 2nd phase and that is now injected into the Runlevel 2(/etc/rc2.d) startup process.

---

### Post by aitvo on 2005-09-13
[QUOTE=doog]I threw together an installation/update package for the Compaq R4000 laptop. It does the following:
[B]
1)  build a new kernel with the atiixp/IDE-DMA fix and the 2X CPU speed fix[/B]
[INDENT]installs kernel source and needed packages, copies patched files over kernel files,[/INDENT]
            [INDENT]builds kernel and installs it.[/INDENT]
**2) update the grub loader to pass timerhack to the kernel on boot**
            [INDENT]adds timerhack to #kopt line in grubs menu.lst and sets the new kernel as the default boot kernel[/INDENT]
**3) install the ATI FGLRX driver for 2D/3D support with updated xorg.conf and Synaptic Touchpad support**
           [INDENT] installs and patches the fglrx driver, compiles it and copies a new xorg.conf( 1024x768 res )[/INDENT]
**4) install the Wifi driver( ndiswrapper and needed driver ).**
            [INDENT]you'll have to enter your essid and wep key in a VI session so know enough to change a word,[/INDENT]
         [INDENT]   save changes and exit VI[/INDENT]

Just install Ubuntu 5.04 as usual, when the system finally boots to the GUI/login screen( drumroll ), you'll need to go to the Ctl-Alt-F1 console, login, get the startup script and run it to start the whole update process. Just type these simple commands from your home directory:
   wget [http://www.pellicosystems.com/linux/Ubuntu/r4000-start](http://www.pellicosystems.com/linux/Ubuntu/r4000-start)
   chmod +x r4000-start
   ./r4000-start

If you want to see all of what's going on then you can download the files package directly with this:
    wget [http://www.pellicosystems.com/linux/Ubuntu/r4000-install.tgz](http://www.pellicosystems.com/linux/Ubuntu/r4000-install.tgz)
   tar -xvzf r4000-install.tgz

I've run the script/process a couple of times to verify it and it seems pretty complete now. Ofcourse, I could be overlooking something so I'll answer any questions about this script and process in this forum.[/QUOTE]

Does this script work on 64bit Ubuntu (I assume it would since it's a script) and does it enable 3d support as well? That's my only hang-up.

---

### Post by doog on 2005-09-14
[QUOTE=aitvo]Does this script work on 64bit Ubuntu (I assume it would since it's a script) and does it enable 3d support as well? That's my only hang-up.[/QUOTE]

It has only been tested on the 32bit Hoary install.

But, if someone wants to discuss this IN ANOTHER/NEW THREAD that's fine and I'll be more than willing to help out.

I should change the script so it "wget's" the ATI driver anyways since that's a large part of the current tgz'ed package and ATI should know how many downloads it's getting. Also, the script could be changed such that it checks for 32 or 64 bit-ness and gets the appropriate driver. The patch to the ATI driver is the same in both cases( 32/64bit ). Let's discuss this in/on another thread if there's any interest in applying this to the 64bit Hoary.

---

### Post by aitvo on 2005-09-14
[QUOTE=doog]It has only been tested on the 32bit Hoary install.[/QUOTE]


I picked it apart and saw that it won't work on 64bit Hoary.

---

### Post by locutus42 on 2005-09-17
you might want to change the doit2 part of the program so that the video driver is installed before the networking stuff is changed. Getting the driver off the network after tweaking the network stuff is asking for trouble, and there shouldn't be any problems just swapping the two sections in doit2.

---

### Post by doog on 2005-09-18
[QUOTE=locutus42]you might want to change the doit2 part of the program so that the video driver is installed before the networking stuff is changed. Getting the driver off the network after tweaking the network stuff is asking for trouble, and there shouldn't be any problems just swapping the two sections in doit2.[/QUOTE]

Done. 

Not as straight forward as just swapping the order of the WiFi and ATI sections though. But only because I don't think the GUI/Xorg server should be started until it's all done. So the ATI driver is installed first, then the WiFi is configured, and onyif the ATI driver installed OK( downloaded ), then the GUI system is started and the 2nd stage script if finished.

---

### Post by doog on 2005-09-19
I've updated the script to streamline the install process. No more manual second phase installation and the WiFi installation just installs the driver. Now you use the Ubuntu Network GUI application to set your essid and wep key.

Also, there is a thread in another forum for HP laptops( zv6000/r4000 ) discussing this script: [http://www.zv6000forums.com/viewtopic.php?t=957](http://www.zv6000forums.com/viewtopic.php?t=957)

**VERIFIED**: I've just reinstalled Hoary 32bit and tested this and it works, also one other person has just used this and verified it works.

FYI, for 1280x800 screens use "gtf 1280 800 60" to generate a working modline and paste that into your /etc/X11/xorg.conf file along with adding "1280x800_60.00" to the head of the "Modes" line if the Display Subsection( of the Screen Section ). This has also been verified to work.

---

### Post by Salane on 2005-10-07
Do you have plans to do this for Breezy when it is released?

---

### Post by doog on 2005-10-11
[QUOTE=Salane]Do you have plans to do this for Breezy when it is released?[/QUOTE]

No plans per se but it's likely I'll give it a shot. In my eyes, the big gotcha is most likely going to be with the ATI driver.

Have you tried Breezy yet to see what the problems are?

---

### Post by cyberlync on 2005-10-14
This script no longer works as the ati drivers cannot be downloaded by wget. Ati  is now checking the http referer and replacing the download with a 'leach' notice. Any idea how to resolve this?

---

