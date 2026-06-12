---
title: "backing up installed softwares"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2009-10-24
I am about to format my os but i don't want to go through the rigorous process of installing the software from the online repositries. I learnt that when i install through the synaptic downloads the .deb file before installing it offline. 
HOW can one create a backup of all this .deb file so one can install from this backup later after reinstalling the os?
Where are this .deb files located on the system?

Please i would require a detailed explanation of this process.

---

### Post by mikewhatever on 2009-10-24
Well, the debs in question are located in /var/cache/apt/archives. You can either copy them or use Aptoncd application.

Edit: Let's say you wanted to copy the debs to a folder on your desktop named backup. Create the folder first, then

```
sudo cp /var/cache/apt/archives ~/Desktop/bacup
```

---

### Post by Cavsfan on 2009-10-25
> **mikewhatever said:**
> Well, the debs in question are located in /var/cache/apt/archives. You can either copy them or use Aptoncd application.

Edit: Let's say you wanted to copy the debs to a folder on your desktop named backup. Create the folder first, then

```
sudo cp /var/cache/apt/archives ~/Desktop/bacup
```

I get this error when trying to enter this command:
cp: omitting directory `/var/cache/apt/archives'
Any help would be much appreciated!

---

### Post by oldos2er on 2009-10-25
> **Cavsfan said:**
> I get this error when trying to enter this command:
cp: omitting directory `/var/cache/apt/archives'
Any help would be much appreciated!

 Try **sudo cp /var/cache/apt/archives/* ~/Desktop/backup**

---

### Post by vinutux on 2009-10-25
Try [AptonCD ]("http://aptoncd.sourceforge.net/")**[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")**

it is in repos ```
sudo apt-get install aptoncd
```

---

### Post by raymondh on 2009-10-25
> **vinutux said:**
> Try [AptonCD ]("http://aptoncd.sourceforge.net/")**[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")**

it is in repos ```
sudo apt-get install aptoncd
```

+1 on apton CD.  

Disclaimer .... I have used it successfully when transferring from 9.04 to 9.04 (i.e same versions).  I don't know what tweaks needed to be done when going from one version to another (i.e. jaunty to karmic, etc.)

Regards,

---

### Post by vinutux on 2009-10-25
> **raymondhenson said:**
> +1 on apton CD.  

Disclaimer .... I have used it successfully when transferring from 9.04 to 9.04 (i.e same versions).  I don't know what tweaks needed to be done when going from one version to another (i.e. jaunty to karmic, etc.)

Regards,

it backup your debs and you can able to install form that cd like repos (installation source)...but moving to another release.... probably this tool is useless coz... of all new updated apps ready for you...this old one not works with new version of ubuntu

---

### Post by Cavsfan on 2009-10-25
Thanks very much for the replies, but when I enter "sudo apt-get install aptoncd" or try
to install it from Synaptic, it says it wants me to mount a previously 
used (and blanked) DVD 
[B]"Media change: please insert the disc labeled
'APTonCD for ubuntu jaunty - amd64 (2009-08-19 18:10) DVD1'
in the drive '/cdrom/' and press enter"[/B]
is what the terminal says with the sudo apt-get command and it gives a 
similar message when using Synaptic.
The AptOnCD disappeared from the left pane of places after a reboot, but it is 
like it still has a reference to the old backed up package that was on the DVD.

Thanks :confused:

---

### Post by raymondh on 2009-10-25
[http://aptoncd.sourceforge.net/download.html](http://aptoncd.sourceforge.net/download.html)

---

### Post by Herman on 2009-10-25
:) I agree, it's a good idea to keep a backup of /var/cache/apt/archives in a USB flash memory stick.

The way I do it is to have two directories, (i386 and 64bit), for each current version of Ubuntu, (Hardy Heron, Intrepid Ibex, Jaunty Jackalope and soon to be released Karmic Koala). 
Each directory stores the latest .deb files for one kind of Ubuntu.

Immediately after installing Ubuntu for myself or for a friend, I copy all of the .deb files for the appropriate version of Ubuntu to the new installation's /var/apt/cache/archives.
Then I run apt-get update and apt-get upgrade, and after that I install all the fonts and software that will be wanted to begin with.
I also have a collection of Ubuntu videos from [Ubuntuclips]("http://ubuntuclips.org/") and [Ubuntu Screencasts ]("http://screencasts.ubuntu.com/")which I copy into new installations if there's enough disc space, especially if the user is new to Ubuntu.
I have a large collection of desktop backgrounds and other assorted goodies to copy across too.

Once everything has been installed and updated, I copy the new installation's /var/cache/apt/archives/ back to the corresponding USB directory again so that it will be refreshed with the latest updates.

That greatly speeds up the time it takes to update and install software in new Ubuntu operating systems because the internet usage is kept to a minimum. It's a lot quicker to copy files from a flash memory stick than wait while the same files are re-downloaded from the internet every time. Some people still have fairly slow internet connections too.

I use a simple script to run a list of commands to do all of that and it includes the commands from  [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") - Ubuntu Web Forums as well. I use the -v (for verbose) option in most of my commands so I can sit back and watch what's happening as the files are all copied across and the system gets updated and upgraded and so on. I think it's really cool! :)

```
#!/bin/bash
# for 64 bit karmic koala

# If flash memory, make swapfile and set swappiness to 0 first
#if not mounted as /media/disk then try /media/2FD8-F14F

##################################
#copy files
echo 'making Software directory'
mkdir Software
#echo 'copying bigpond software sources script'
#cp -v /media/2FD8-F14F/installation\ kit/sources.list_files/switchsourcesbigpond.sh Software/
echo 'copying iinet software sources script'
cp -v /media/2FD8-F14F/installation\ kit/sources.list_files/switchsourcesiinet.sh Software/ 
echo 'copying ubuntu software sources script'
cp -v /media/2FD8-F14F/installation\ kit/sources.list_files/switchsourcesubuntu.sh Software/ 

#echo 'copying frostwire installer'
#cp -v /media/2FD8-F14F/installation\ kit/frostwire-4.18.0.i586.deb Software/
#echo 'copying skype installer'
#cp -v /media/2FD8-F14F/installation\ kit/skype-debian_2.0.0.72-1_i386.deb Software/

echo 'copying desktop backgrounds'
cp -Rv /media/2FD8-F14F/installation\ kit/desktop_backgrounds Pictures/
echo 'copying grub splashimages'
cp -Rv /media/2FD8-F14F/installation\ kit/grub2_splashimages Pictures/
echo 'copying openclipart'
cp -Rv /media/2FD8-F14F/installation\ kit/openclipart Pictures/

echo 'copying gimp book'
cp -Rv /media/2FD8-F14F/installation\ kit/Grokking-the-GIMP-v1.0 Documents/
echo 'copying instructional videos'
cp -Rv /media/2FD8-F14F/installation\ kit/ubuntu_videos Videos/
echo 'copying spreadsheet templates'
cp -Rv /media/2FD8-F14F/installation\ kit/Spreadsheet_Templates Templates/
echo 'copying ubuntu pocket guide'
cp -Rv /media/2FD8-F14F/installation\ kit/ubuntupocketguide-v1-1.pdf Desktop/
echo 'transfering stored .deb packages'
sudo cp -v /media/2FD8-F14F/installation\ kit/sources.list_files/karmic/deb/*.deb /var/cache/apt/archives/

#######################################
#sources
#echo 'copying bigpond sources icon'
#sudo cp -av /media/2FD8-F14F/installation\ kit/sources.list_files/switchsources128.png /usr/share/icons/
echo 'copying ubuntu sources icon'
sudo cp -av /media/2FD8-F14F/installation\ kit/sources.list_files/switchsourcesback128.png /usr/share/icons/
echo 'copying iinet sources icon'
sudo cp -av /media/2FD8-F14F/installation\ kit/sources.list_files/iinet_icon.png /usr/share/icons/

echo 'making /etc/apt/sources.list backup'
sudo cp -v /etc/apt/sources.list /etc/apt/sources.list.bak

#echo 'copying sources.list.bigpond'
#sudo cp -v /media/2FD8-F14F/installation\ kit/sources.list_files/karmic64/sources.list.bigpond /etc/apt/
echo 'copying sources.list.original'
sudo cp -v /media/2FD8-F14F/installation\ kit/sources.list_files/karmic64/sources.list.original /etc/apt/
echo 'copying sources.list.iinet'
sudo cp -v /media/2FD8-F14F/installation\ kit/sources.list_files/karmic64/sources.list.iinet /etc/apt/

echo 'switching sources'
sudo cp -v /etc/apt/sources.list.iinet /etc/apt/sources.list
echo 'getting repository keys'
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 5227BEBD68436DDF
gpg --export --armor 5227BEBD68436DDF | sudo apt-key add -
echo 'getting ready to update and upgrade'
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get update
sudo apt-get upgrade

########################################
#fonts
echo 'copying fonts'
sudo cp -Rv  /media/2FD8-F14F/installation\ kit/sharefont/  /usr/share/fonts/
echo 'copying more fonts'
sudo cp -Rv  /media/2FD8-F14F/installation\ kit/freefont/ /usr/share/fonts/
echo 'downloading still more fonts from the internet'
sudo apt-get install ttf-sil-gentium ttf-dustin ttf-georgewilliams ttf-sjfonts sun-java6-fonts ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncommon msttcorefonts ttf-dejavu ttf-xfree86-nonfree ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts rhino-doc sun-java6-plugin ttf-arphic-uming sun-java6-fonts ttf-bitstream-vera 

########################################
#multimedia

echo 'installing multimedia codecs and software'

sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla

sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs ia32-sun-java6-bin icedtea6-plugin libmp3lame0 non-free-codecs openjdk-6-jre unrar xfs equivs libdvdcss2 debhelper fakeroot build-essential libfftw3-dev jackd libjline-java-doc sidplay-base xsidplay mplayer
# lib32asound2-plugins ia32-sun-java6-plugin

# To check if adobe flash player is installed, visit http://adobe.com/products/flash/about
# if not, wget http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)

########################################
#programs
echo 'installing programs'
sudo apt-get install drapes gparted gpass testdisk stopwatch gcolor2 lm-sensors gthumb ntfsprogs gnome-specimen  
# grass qgis qgis-plugin-grass  kompozer 
# openclipart cheese
# partimage smartmontools

echo 'backing up .deb files'
cp -v /var/cache/apt/archives/*.deb /media/2FD8-F14F/installation\ kit/sources.list_files/karmic64/deb/

echo 'done'

###########################################
# Don't forget to 
# set up drapes desktop background switcher
# edit the 'Applications'-->'Programs' menu with the iinet/Ubuntu Sources Switchers
# configure GRUB and add a splashimage
# Open Firefox and link to hermanzone and Ubuntu Web Forums
# visit adobe website to make sure flash is working
# Configure Evolution
# Add 'Search for Files' to top panel
# Set Desktop Backgrounds
# Play some music and video files to get any more needed codecs
```Maybe someone who's better than I am at scripting can suggest a few improvements to my crude effort at writing a script. :)

---

### Post by vinutux on 2009-10-25
> **Cavsfan said:**
> Thanks very much for the replies, but when I enter "sudo apt-get install aptoncd" or try
to install it from Synaptic, it says it wants me to mount a previously 
used (and blanked) DVD 
[B]"Media change: please insert the disc labeled
'APTonCD for ubuntu jaunty - amd64 (2009-08-19 18:10) DVD1'
in the drive '/cdrom/' and press enter"[/B]
is what the terminal says with the sudo apt-get command and it gives a 
similar message when using Synaptic.
The AptOnCD disappeared from the left pane of places after a reboot, but it is 
like it still has a reference to the old backed up package that was on the DVD.

Thanks :confused:

disable that cd source from software sources | system > Administration > Software sources un tick apt on cd from installable form cd/dvd section

---

### Post by Cavsfan on 2009-10-25
vinutux - excellent idea about removing the source! That is what the problem was! 
I was even there a couple of times, but it didn't register! I unchecked 2 DVDs and deleted them.

Thanks for all of your help!
I finally just copied all the DEBs to my desktop.
Then I cut and pasted them to my 1TB USB Phantom Drive with no errors. Whew!!!
I was getting ready to kill something! (just kidding)! :popcorn:

Herman, thanks for the excellent example of a good script.

I have a triple boot system: windows vista 64 bit (which doth suck),  Jaunty Jackalope                                                                                      64 bit, Windows 7 RC 64 bit. (soon to be a dual-boot system)
Windows 7 is much improved over vista, but it is still windows! 
My son plays some heavy duty games, like Crysis, etc. and so I pre-ordered 7 Home Premium for $49! Now it is $119!

Anyway, thanks to all!
Tomorrow I will re-install AptOnCD and create one DVD and I'll be good to go!:guitar:
I guess until I go with the next version of Ubuntu! Oh, well! I like the learning curve!

---

### Post by vinutux on 2009-10-25
Good luck for you .......anyway plz.... mark thread SOLVED

---

### Post by Cavsfan on 2009-10-26
> **vinutux said:**
> Good luck for you .......anyway plz.... mark thread SOLVED

vinutux, I am not the OP. Should I be marking it as solved?

---

### Post by vinutux on 2009-10-26
> **Cavsfan said:**
> vinutux, I am not the OP. Should I be marking it as solved?

Oh..... Sorry only [COLOR="YellowGreen"]10ghost[/COLOR], who started this thread do that.............

---

### Post by Herman on 2009-10-26
> Herman, thanks for the excellent example of a good script.:oops: Well, it gets the job done.
There are some commands in there that will only be useful to me and some that are only useful to somebody else who uses the same ISPs as I and my friends have available. (For the IPS's free repository mirrors). Hopefully it will give somebody the idea and they'll be able to modify it to suit themselves. :redface:

---

### Post by 10ghost on 2009-10-28
Thanx a lot u all for your support i solving this problem .
I am sorry for just attaching the tag solved to this thread .
I am not always online like you guys . Thanx a lot because you have solved my problem . thanx one more time.

---

### Post by Cavsfan on 2009-11-18
This may be the best way to do this:
[http://nerdmess.wordpress.com/2009/10/02/allmyapps-com-aptoncd-quick-ubuntu-reinstall/](http://nerdmess.wordpress.com/2009/10/02/allmyapps-com-aptoncd-quick-ubuntu-reinstall/)

---

