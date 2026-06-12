---
title: "ubuntu on hp pavilion dv8 (sound issues)"
date: 2009-11-03
forum: Hardware
---

### Post by wolfgangpauli on 2009-11-03
Hey,

I just got a hp dv8 laptop. Everything pretty much worked out of the box.

Video - works great after apt-get install nvidia-glx-185 (karmic)
wireless - worked right away

however, the sound is strange. It seems like there is only sound coming out of the sub-woofer. the card seems to be 

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

the alsa info is here
[http://www.alsa-project.org/db/?f=a3903ba058eae145d9aac568e41a88c01cf4646a](http://www.alsa-project.org/db/?f=a3903ba058eae145d9aac568e41a88c01cf4646a)

phonon describes it as stac92xx

There is also a gain for treble and bass on above the keyboard (next to volume control). Unfortunately, that gain is inactive though. 

The headphone jack seems to be dead too. 

Hopefully there are more people with this laptop. ;)

---

### Post by langostino on 2009-12-11
I have the same notebook and the same sound issue. Sorry, I can not help you now. 

But, maybe you can help me...

I tried last Ubuntu 9.10 Live CD (64 bits) and it boots normaly. Wifi is working. But, when I shoutdown or halt system from this Live CD, notebook is halted, but when I switch on the notebook, BIOS shows an abnormal hibernation or shutdown process ocurred, maybe for an overheating operation.

I tried that this BIOS message is not displayed when I boot Ubuntu LiveCD with ACPI=off option.

Do you have the same issue? My BIOS version is F.05.

PD: Sorry for my bad english.

---

### Post by wolfgangpauli on 2009-12-11
Hi,

I get the same msg during boot, everytime. I am wondering whether it is because I nuked the hp partition, or the master boot record. I just ignore the msg, sorry. Also, still no sound ...

---

### Post by anjanaya on 2009-12-12
Hey!
I've just bought the HP dv8 1080ea and was having the same problems.
Thought HP would be a little Linux friendly, but alas once again we're on our own.([HP dv 6018]("http://wiki.archlinux.org/index.php/HP_Pavilion_dv6018"))

Nevertheless, I got my speakers working with a little searching around in the forums.
[snd-hda-intel]("http://ubuntuforums.org/showthread.php?t=1330569")

I think slowly and patiently we shall be able to configure our systems to our liking, without a doubt. (Fingers crossed)

---

### Post by wolfgangpauli on 2009-12-12
Thanks, this did indeed work. even headphone and mic are working now. 

note: before I bought this laptop I for some reason called their sales hotline. I am not sure how it came up, but I mentioned that I would be nuking windows and put kubuntu on it, and that person told me that this action would void the warranty on the laptop. Turns out that this seems to be normal, but what I heard from others that should only void the software warranty (on nuked windows?) but not the hardware warranty. I kind of have my doubts that is actually the case, given that overheating msg ...

---

### Post by langostino on 2009-12-22
HP has delivered a new bios version: F.12. Anybody had installed on its laptop?

---

### Post by langostino on 2010-01-03
I followed steps ahead, and sound is right, but mic does not work. Must i to dowload and compile new alsa drivers versions? I only changed alsa.conf file.

---

### Post by anjanaya on 2010-01-03
Hi,
I know that this thread is solved, but anyway
The overheating BIOS message does not appear anymore on my DV8-1080ea anymore.
All i did was Upgrade the BIOS! just find update for your lappy on HP website and upgrade it.Alas Windows will be required to do that but once done, I do not need to pass acpi=off boot option (anyway it was not an option for me since it disabled Wireless card and multimedia keys) and the fan runs at full speed with no more crap message even though it did not overheat!

If you have already figured this out never mind :-)

Thanks,
anjanaya

---

### Post by kronictokr on 2010-01-03
you may like this fix much better


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

