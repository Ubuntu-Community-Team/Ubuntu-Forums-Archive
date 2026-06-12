---
title: "popping noise in ubuntu 9.10"
date: 2010-01-01
forum: Hardware
---

### Post by grimey44 on 2010-01-01
hey i noticed lately that my laptop has been making a popping noise randomly. through a bit of reading i found out it is the power save feature turning on or off the speakers. i used the fix shown at this link:

[http://www.youtube.com/watch?v=RSbw42MkPvE](http://www.youtube.com/watch?v=RSbw42MkPvE)

but now i just have no audio  altogether.
any suggestions???

---

### Post by grimey44 on 2010-01-03
any suggestions from anyone?

---

### Post by IcarusR on 2010-01-03
How about instead of commenting out the line change the power_save value to 0. This should turn audio powersaving off.

Have you checked that your audio is not muted.

---

### Post by grimey44 on 2010-01-03
yeah at first commented it out then put it back, then tried to put the powersave to 0 then put it back. none seems to make any changes.

---

### Post by kronictokr on 2010-01-03
almost willing to bet fix all sound issues in karmic, unless hardware completely doesnt support it, like SIS graphics. also fixes freezing issues.

could reverse the process to keep pulse if you wanted

software conflict, this should fix it

since this is a microsoft, i mean software conflict problem, you should be able to use this method on all karmic install no matter what your hardware is. if not, i would suggest backing up your info and starting from the top. again tho, you shouldnt have to. any pakages you already have shouldnt affect the script either, or your install. restores all sound including system sounds. also stops freezing issues that happened when adjusting audio settings.

THIS METHOD CLEARS OUT PULSE COMPLETELY BUT DOES FIX THE SOUND. I TESTED THE SCRIPT ON A FRESH INSTALL EVERYTHING WORKS PERFECT AFTER SUDO NAUTILUS. KEEP READING

sudo apt-get remove libsdl1.2debian-alsa

includes audacious music player, vlc , and ubuntu restricted extras(minus pulse updates :D ).
VVVV VVVVV

sudo aptitude install libdns53 libdns53 linux-headers-2.6.31-16 linux-headers-2.6.31-16-generic linux-image-2.6.31-16-generic ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk audacious audacious-plugins audacious-plugins-extra cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-16-generic linux-backports-modules-alsa-2.6.31-16-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-16-generic vlc

java will pop up
hit tab enter, tab enter to select yes

this is a BIG script, it will take some time....
so how bout those canucks.... :D
bout ten mins later....

sudo /etc/init.d/alsa-utils restart

sudo apt-get update

CAUTION,CAUTION, when you use this command, you have sudo priviledges, be CAUTIOUS when deleting files, double check to see that a non pulse file is in not your search results!!!! if so drag and select around them. read on.....

sudo nautilus

Now use this virtual sudo desktop, enter pulse in the search in the SAME window (click the magnifying glass top right), make sure to add hiden files, and search the file system so that you get everything. When you use this method search is slowed down, be patient, wait. Now you have all the pulse files, and sudo privilege, look through the search results and make sure some misc data dint get mixed in (non pulse related files) , if its all good , drag and select all remaining pulse files, while selected, hit shift+del, hit enter when it asks to permanently delete. Close the window. Terminal should pop up.
In that terminal type

sudo reboot

I had to use this method, because for some reason, 9.10 karmic bonds itself to a lot of programs, removing asociated programs. For example pulse and alsa both take almost half the main operating sytem with it, when trying to remove them in terminal, or synaptics . Including ubuntu-desktop, and a good list of others. With the sudo nautilus search and destroy method, its downright surgical

Now, using gnome-mixer Application>>>sound&video>>gnome mixer
Unmute and control every aspect of your sound, including multi soundcard issues!!



HP Pavilion dv6-2020ca
AMD athalon II dual core notebook
3072mb DDR2 SDRAM (2 Dimm)
ATI Radeon HD 4200 Graphics with 128MB DDR2 Display Cache

---

### Post by grimey44 on 2010-01-03
alright so i tried all the steps you suggested. 
is there any installing i need to do after that?
sound still doesnt  work. it does however work out of the headphone jack but not the speakers.

---

### Post by kronictokr on 2010-01-03
go to applications>>>sound & video>>>gnome mixer and unmute your speakers. should work.

---

### Post by grimey44 on 2010-01-03
they are all unmuted and still nothing

---

### Post by grimey44 on 2010-01-05
also, my volume icon is gone now.
any idears?

---

### Post by kronictokr on 2010-01-08
also, my volume icon is gone now.
any idears? 
quote/\/\

your volume icon is gone because it was pulseaudio based. all your sound apps that used pulse can be removed via SYSTEM>>>PREFERENCES>>>MAIN MENU
as they are not needed.  the replacement program is GNOME ALSA mixer, it will control every audio aspect of your computer , including hdmi and second sound cards.

question. did you do a system update after you installed. the only time this hasnt worked for me , was when i had forgot to do a system update.

quoteVVVVV
alright so i tried all the steps you suggested.
is there any installing i need to do after that?
sound still doesnt work. it does however work out of the headphone jack but not the speakers. APPLICATIONS>>>SOUND&VIDEON>>>>GNOME ALSA mixer
thats where you will find your sound controls. uncheck the boxes at the bottom of the equalizer bars to unmute. 

you have to have done a system update for this to work

make sure all pakages were installed without errors

go into you synaptics program, top left click edit, scroll down to and click fix broken pakages.  if there are any, then apply. reboot.

ensure to finish with these two commands in terminal, followed by a reboot.

sudo /etc/init.d/alsa-utils restart

sudo apt-get update

sudo reboot

the changes will not happen if you do not update your file system and reboot

---

### Post by mwolfgang on 2010-01-25
Open terminal and enter the following comamnd
 [INDENT]gksudo gedit /etc/modprobe.d/alsa-base.conf
[/INDENT] This will prompt for password
 Now you have to delete last two lines where you see power-save option
 Save and exit the file.
  [U]
[/U]
_[http://ubuntuforums.org/showthread.php?t=1335045](http://ubuntuforums.org/showthread.php?t=1335045)_[]("http://ubuntuforums.org/showthread.php?t=1335045")

---

