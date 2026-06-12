---
title: "Hoary array 6, ATI Radeon 9800 SE, X.org and Alsa"
date: 2005-03-06
forum: Hardware &amp; Laptops
---

### Post by b_west on 2005-03-06
I'm fairly new to Linux, love Ubuntu and tend to be able to find what I need when I have a problem, but this is one of the rare times I must make a post -- and hopefully it may assist someone else as well.

I'm using Hoary from the Array 6 CD download (gnome;2.6.10-4-386 kernel) and have two major problems:

I have an ATI Radeon 9800 SE video card with 128 MB -- but I can't seem to get direct rendering to activate. As such all interactive 3d environments are choppy and unusable.

I've tried all the work-arounds I could find in the Ubuntu forums and elsewhere. Nothing worked until I found the vanilla solution in the post at the following address:

[http://www.linuxquestions.org/questions/history/294150](http://www.linuxquestions.org/questions/history/294150) 

While the America's Army gameplay was awesome :) , problem two arose -- the sound would not initiate with the game --except on rare occasions immediately after reboot. :-? 

I tracked this to the difference between OSS and Alsa mixers. Alsa was installed but wouldn't mix the sound between the desktop and the game and, thus, no in game sound. I figure initiating the game before the desktop took sound control were the only times it would work in gameplay.

It was during the Alsa troubleshooting that I just really screwed things up and finally opted to........ reinstall -- no big deal 'cause it was a new install anyway and I could just repeat the vanilla for the fglrx functionality... right?

I've now spent a whole day just trying to duplicate whatever I had done before to absolutely no success. I've gone through how-to after how-to, mixed processes, used the vanilla, used synaptic, configured XFree86 and copied information into xorg.conf.... and to no avail. ](*,) 

Here's are of SOME of the how-to's I've tried:
[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) 
[http://ubuntuforums.org/showthread.php?t=15990&highlight=ati+driver+install](http://ubuntuforums.org/showthread.php?t=15990&highlight=ati+driver+install) 
[http://ubuntuforums.org/showthread.php?t=3567&highlight=ati+driver+install](http://ubuntuforums.org/showthread.php?t=3567&highlight=ati+driver+install)
[http://ubuntuforums.org/showthread.php?t=13226&highlight=ati+driver+install](http://ubuntuforums.org/showthread.php?t=13226&highlight=ati+driver+install) 
[http://www.stanchina.net/~flavio/debian/fglrx-installer.html](http://www.stanchina.net/~flavio/debian/fglrx-installer.html) 

I've spent so much time and gone through so many how-to's I'm desperate and I've got no problem with reinstalling if necessary.

Thanks to all who reply!

---

### Post by b_west on 2005-03-06
woohoo!!! I found what I believe was the problem -- it's workaround is in the following thread:

[http://ubuntuforums.org/showthread.php?t=18108](http://ubuntuforums.org/showthread.php?t=18108) 

Now I just need to get Alsa working right... Good luck if you're having similar dificulties!

---

### Post by b_west on 2005-03-15
I've noticed that this post has been getting a bit of traffic, so I've decided to write the process I've constructed from multiple tutorials. So, here's the process I use to install the latest ATI Radeon fglrx drivers onto Hoary (Preview CD) in 5-10 minutes when necessary (this is my first tutorial, so I hope it's helpful):

First, of course is the prepairation:

1. Download the latest ATI drivers (.rpm file) for X.org from ati.com, or the following link:

[http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.10.19-1.i386.rpm](http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.10.19-1.i386.rpm) 

1a. I don't think it really matters where the file is located, but for simplicity, I copied the fglrx file into the /usr/src directory using sudo:

```
~$ sudo mv fglrx_6_8_0-8.10.19-1.i386.rpm /usr/src
```

2. Make sure gcc libraries are installed.

[INDENT]I searched Synaptic for 'gcc' and found the gcc4.0 and other libraries already installed. However, there is a package simply labeled 'gcc' that was not installed. After installing this package, I no longer received any gcc related errors.[/INDENT]

3. Remove all fglrx packages via Synaptic.

[INDENT]Perform a Synaptic search for 'fglrx' and remove all installed packages.[/INDENT]

4. Install Linux Kernel Image source files:

[INDENT]Perform a Synaptic search for 'linux-image' and install the package which corresponds with your machine's kernel. Use the following command if you're unsure which image to get:

```
$ uname -r
```

Unpack the linux image and create a symbolic link (named 'linux') to the new folder using the following commands:

```
$ cd /usr/src 
$ sudo tar -xvfj linux-image-2.6.10.tar.bz2
$ sudo ln -s linux-image-2.6.10 linux
```[/INDENT]

Now we'll start the actual installation:

5. Press CTRL+ALT+F1 to move out of Gnome into a command session (CTRL+ALT+F7 returns you to your Gnome session while gdm is active).

6, Login as a user with the ability to use 'sudo' commands.

7. Here is a list of commands followed by a brief description of what they do (after '//'s) which will perform the actual install :

[INDENT]//shut down Gnome
$ sudo /etc/init.d/gdm stop
     //create a file listing locations of current fglrx.ko files -- not sure if it does anything else
$ sudo find / -name fglrx.ko > files.txt 
    //make sure current fglrx.ko is out of the way
$ sudo mv /lib/modules/<your_kernel_version>/kernel/drivers/video/fglrx.ko $HOME 
     //or wherever you have your ATI drivers
$ cd /usr/src 
       //create a .deb installation package from the .rpm file
$ sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm
      //install the .deb package
$ sudo dpkg --force-overwrite -i fglrx-6-8-0_8.10.19-2_i386.deb
$ cd /lib/modules/fglrx/build_mod
        //create make file
$ sudo sh make.sh
$ cd /lib/modules/fglrx
    //install drivers and create fglrx.ko in current directory
$ sudo sh make_install.sh
        //create 'misc' directory
$ sudo mkdir /lib/modules/<your_kernel_version>/misc
    //copy fglrx into new 'misc' directory
$ sudo cp fglrx.ko /lib/modules/<your_kernel_version>/misc
        //Note: ENABLE EXTERNAL AGP GART--do not use kernel for agp!!!
$ sudo fglrxconfig
        //probe for and install 'fglrx' module
$ sudo modprobe fglrx
        //restart Gnome session
$ sudo /etc/init.d/gdm start[/INDENT]

[INDENT]You'll notice I was pretty adamant about enabling the External AGP GART while running fglrxconfig. I found this to be what really makes things work as it forces the rendering to be performed by your video card instead of your linux OS -- make sure you enable this!!![/INDENT]

8. Once you are back in Gnome, open a command window check for direct rendering. There are three ways -- if any one works, then they all do:

[INDENT]I. Use the following command:
```
$ fglrxinfo
```
The 'OpenGL vendor string' shoud read as 'ATI Technologies Inc.'. If it says 'Mesa Project' anywhere, then the install was unsuccessfull.

II. Use the following command:
```
$ glxinfo
```
This will spit out a whole mess of code. Scroll back to top of the spit-out and look for the line "direct rendering:". If it says 'Yes' then all's good -- if it says 'No' then the install was unsuccessful.

III. Use the following command:
```
$ glxgears
```
This will open a little window with three colored gears (RGB). Give it a few seconds and the command window will start giving framerate updates. If the updates show FPS over 2000 to 5000 somewhere then, congratulations, you've got 3d rendering. If the FPS is only in the 100's then the install was unsuccessful.
[/INDENT]

Since I combined many different tutorials to create this process for my own use, I've had to use it about four times (fglrx.ko seemed to get outdated after Synaptic Update Manager did some kernel stuff for a little while) and it's worked every time. Just give me about 5 minutes, and I'm golden.

I know this wasn't perfect, but I hope it helps as it's worked for me and it took me a while to get it all figured out.

Best of luck to ya! :cool:

---

