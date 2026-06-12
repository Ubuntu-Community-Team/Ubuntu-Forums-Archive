---
title: "Fresh Install from 8.04 to 8.10"
date: 2008-11-22
forum: General Help
---

### Post by cashmoney on 2008-11-22
First thanks to the Ubuntu Wiki for the fix on the sound and Rami Taibah for the [How to]("http://hehe2.net/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/") on how to do this.  I just added upon his article and fixed a dpkg command.  

So you want to do a fresh install and upgrade from 8.04 to 8.10 and keep your settings.  Easy.  ***read issues prior to upgrading***

First back up your home Directory.

   ```
sudo su
    cd /home
    tar cvpzf backup_home.tgz  --exclude=/.local/share/Trash* --exclude=/backup.tgz /home/  <username>
```

This says take everything in my home folder and place it in backup_home.tgz except everything what is excluded and your backup will be located at /home/backup_home.  You can exclude anything else by adding** --exclude=/ <and the path>/file**

next type in 


    ```
dpkg --get-selections > /home/user/package.selections
```

This makes a list of all packages you have installed and uninstalled.


    Also do

    ```
cp /etc/apt/sources.list /home/user/sources_bak.list
```

 Now copy the Tar file, package.selections, and sources_bak.list file to an external HDD (or onto server).

Install Ubuntu 8.10 as you normally would. 

Installed great moving on.  Now move the files from your external HDD/server to your desktop.


Open your sources.list files and compare the two.

    ```
sudo gedit /etc/apt/sources.list
    sudo gedit /home/<user>/Desktop/sources_bak.list
```

What you want to do here is copy and paste from the old sources to the new sources anything that you manually added for any aps you have installed at one point of time or another.  Don't just copy the whole thing the main Ubuntu links are release dependant.

Done?  Great now run.

    ```
sudo apt-get update
```

Now time to get all your previous packages back.  Do this by putting the following into terminal

    ```
sudo dpkg --set-selections < /home/<user>/Desktop/package.selections && apt-get dselect-upgrade
```

If your like me and had a lot of stuff installed this will take a while.  Make a sandwich, play a game, bump uglies with your significant other or the one you brought home from the bar last night.  This will also uninstall the aps you removed FYI.

You have all your packages.. Awesome.  Now lets return your settings back to the way they were.

    ```
tar xvpfz backup.tgz -C /home/ncash/Desktop/
```

This will extract everything onto your desktop.  Here is a good time to delete folders your not going to move over (last chance)  I removed the Gimp folders and the like since I didn't use it that much and I didn't possibly want to overwrite any newer version files with the older ones and cause conflict?  Click and drag the icon from the newly extracted home folder to the fresh install home folder and when it asks to overwrite, merge, or cancel click on merge.

reboot and enjoy

*I_**ssues (and fixes)***_

This does not install anything you manually compiled and installed.  Such as VBbox, AWN, Cisco vpn client and whatever else you might have manually compiled and installed.

I had a problem with my sound not working with my Dell Latitude D630.  So I followed this.

       [Alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2")
               [Alsa-lib 18a]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2")
           and [Alsa-Utils 18]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.18.tar.bz2")

Or go to [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) and click on alsa-driver*, alsa-lib*, and alsa-utils* on the right hand side.  The links above did this for you already but check the versions before just clicking on the links if there are newer versions by the time you read this download them and follow the same steps.

install compiling tools 

    ```
sudo aptitude install build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r`
```


Next 
    ```
sudo mkdir -p /usr/src/alsa
```          makes a directory called alsa in the /usr/src
    ```
cd /usr/src/alsa 
```                    moves to said directory
    ```
sudo cp ~/downloads/alsa* . 
```         This copies the files from <downloaded directory> to present directory
    ```
sudo tar xjf alsa-driver*.bz2 
```       untars
    ```
sudo tar xjf alsa-lib*.tar.bz2
```      
 ```
   sudo tar xjf alsa-utils*.tar.bz2
```     

Now lets compile shall we

  ```
 cd alsa-driver*
       sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
     sudo make
     sudo make install
```

1st we change directory,  Then we configure our our driver using our kernel headers to compile against the hardware.
Once it is configured we make the driver then we install it as a module to the kernel.

Now lets do the rest.
 alsa-lib compile and install
    > cd ../alsa-lib*
    sudo ./configure
    sudo make
    sudo make install

alsa-utils compile and install
   ```
cd ../alsa-utils*
   sudo ./configure
   sudo make
   sudo make install
```

Reboot- Sound should work

When your system reboots go to terminal and type

   ```
cat /proc/asound/card0/codec#* | grep Codec
```

you should get something similar to this

Codec: SigmaTel STAC9205
Codec: Conexant ID 2c06

If you get the same.. awesome.  If not check this link and search for your codec [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)


next type 

  ```
sudo nano /etc/modprobe.d/alsa-base
```
  

At the end of the text paste this in Changing MODEL to the matching model number.  If you have the STAC9205 card then the model number is dell-m42

STAC9205/9254
		  ref		Reference board
		  dell-m42	Dell (unknown)
		  dell-m43	Dell Precision
		  dell-m44	Dell Inspiron



Add this to the bottom of the text and change the MODEL to your model number.

options snd-hda-intel model=MODEL
    
If you have the STAC9205 the command should look like this.

options snd-hda-intel model=dell-m42

save and exit.

Your probably asking why the hell did we do this?  Well I'll tell you.  I wanted to mess with you and see if you read though prior to doing anything.....  Kidding.  You should do it becuase there is a bug with the auto-detect so your sound may work after the first reboot after compiling the kernel and drivers but it may revert back to the older drivers and conflict and you have no sound.  So this basically says "You use this driver or Ima turn you on and place you in a creek!" to the laptop.  The laptop doesn't want this and complies.

Now type into terminal

  alsamixer 

and adjust sound volume.  

Now your running 8.10 and have all your settings from 8.04.

Word up!

With this latest ALSA driver though the Mic doesn't work I have submitted a bug to the ALSA-Project and will update accordingly.

---

