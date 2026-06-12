---
title: "Gateway NV79 series wireless connect error"
date: 2011-01-23
forum: Hardware
---

### Post by DWade on 2011-01-23
Ubuntu 10.04 LTS 64 bit.
Wireless connect problem.

I have a gateway nv79 series.  I wasn't having a lot of problems, just the normal that 64 bit seems to have, some software doesn't work.

After the kernel update to 2.26.32.25 my Dlink Dir 615 will not connect up to the Ubuntu.  kernel 2.26.32.27, does not work either. 

I have two wireless units, one is the Nexconnect by Nexaira for my Aircard, the other is the Dlink Dir-615.

The Dlink will fail to connect.  

Also a Keyboard Keypad problem.  I am also having a problem with my key board, the key pad will not work.

Numlock on Numlock off no effect. The keypad won't work in any mode.

I thought this worked when I first installed.

If any body knows any fixes, I'd appreciate.

---

### Post by DWade on 2011-02-05
If your reading this then some of you may have the same notebook.

It appears that the 64 bit version is a little quirky.  You have to download dpkg-dev and install, run a couple of older kernels, [you can do this by going to applications and downloading from Ubunutu Software, Startup Manager, this will allow you to change the timing of grub.] a couple of times, then load back into the latest kernel, and then...  The wireless will connect like it supposed to. (weird)

and then run the keypad fix from another post which is":
go to 
      System
      Preferences
      Keyboard
      Mouse Keys 
and then unselect Pointer can be conntrolled by using the key pad.


Also the a fix for 64 bit is to load the 32 bit version, and then download the PAE kernel
sudo apt-get update
sudo apt-get install linux-headers-server linux-image-server linux-server
This will allow the 32 bit version to run more 3.5 gigs of memory.:lolflag:

Not so good sound doesn't work on the 32 bit..  will look for solutions.

---

### Post by DWade on 2011-02-07
:KS It seems, the sound was corrected some time back in May 16th 2010 and Iidex introduced this fix on post #9
 [This web link]("http://ubuntuforums.org/showthread.php?t=1478602&highlight=nv79+sound") [http://ubuntuforums.org/showthread.php?t=1478602&highlight=nv79+sound](http://ubuntuforums.org/showthread.php?t=1478602&highlight=nv79+sound)
Edit this file     /etc/modprobe.d/alsa-base.conf file
and insert this line and reboot.
options snd-hda-intel model=3stack-dig

Oh and easy way to edit the file is to open a terminal
type sudo nautilus
In the open nautilus window go to filesystem and the folder /etc then to folder modprob.d and then right click on the alsa-base.conf file use gedit and add the "options snd-hda-intel model=3stack-dig" to the file and save

Now it could have been introduced by some one else eariler, but that is what I found so far and, I found another post for November 2010 that had 3 lines to add to /etc/modprobe.d/alsa-base.conf file, but Iidex posted and said only the one line was necessary.

I Installed 64 Bit Ubuntu in June 2010.  I can't remember if I used it or I used the Pulse audio update in my download directory. to fix the audio problem.

I had the wireless problem and I done something to the log out button, and I wanted to try the PAE headers.  So I backed up my data, but forgot my Bookmarks. Loaded 32 bit 10.04 LTS and updated not really noticing there was no sound. Dumped it and reloaded 64 bit. No Sound. Searched and found these fixes

I have backed up the new 64 bit partition, where the /etc/modprobe.d/alsa-base.conf file has been modified and updated to the latest updates.  Sound works and wireless works.

Will now try the 32 bit version and add the line to the "alsa-base.conf" file and see if the sound works, if it does then I will add PAE Headers, check the sound, then update and check the sound.:confused:

---

