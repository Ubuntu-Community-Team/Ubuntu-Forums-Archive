---
title: "Sony VAIO VGN-B88GP sound does not work"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by pashby on 2005-07-20
Hello all

I have been trying for a while to get sound to work on my laptop.  
I have been pleased with the way wireless networking and thanks to these forums, Video installation with the correct resolution settings have gone.

This is not my first installation of Linux on this laptop - I have had Fedora core 4 on before and have lately replaced it with Ubuntu and I find it is very good to use.  However Fedora did find my sound card and was happy to play sounds and music which unfortunately Ubuntu cannot.

I have tolled around these forums and used Google etc to see what I can do.  As a novice user (of Linux) I have reached a point where I can go no further.

I tried using the instructions in Starters Guide but have not improved the problem.

Here is the output when I try to execute Noatum

Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (Device or resource busy)
The sound server will continue, using the null output device.

and the message when trying to follow the Starters Guide instructions

root@ubuntu:/home/peter # sudo killall esd
esd: no process killed
root@ubuntu:/home/peter # sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup
root@ubuntu:/home/peter # sudo gedit /etc/esound/esd.conf

(gedit:7878): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

This is as much info as I have and to find the actual sound hardware I will need to reinstall windows again.......................

Any help would really be appreciated

Peter

---

### Post by s_p_a_r_k_y on 2005-07-20
[QUOTE=pashby]Hello all

This is as much info as I have and to find the actual sound hardware I will need to reinstall windows again.......................

Peter[/QUOTE]
the lspci command should give us a hint of what hardware you are using.
I believe noatun is a kde program and therefore will be looking for the arts sound server(someone correct me here if I'm wrong). Try using another program such as xine (sudo apt-get install xine-ui) and try playing a movie/song in xine.

In xine you have the option to specify what sound driver to use, mine is set to alsa (right click in xine->settings. Then the audio tab. You might need alsa or oss depending on your card)

Also starting up the esd sound server should play a song (in a console type in esd). Once the sound server is started, my belief is that other programs can't use the sound card unless they are being piped through the sound daemon, so other programs (should be by default) setup to use esd.

I currently don't use a sound server and just have one program that uses the sound card at a time.

Hope something works. Also what I do sometimes is boot with a knoppix cd and then see what modules its loading. I in a console lsmod  and either write them down, print em, or pipe it to a file lsmod > /mnt/hda1/home/username/lsmod (after you mounted your home to /mnt/hda1 or whatever it is on ur computer)

then run lsmod in ubuntu to see if you have the same modules being loaded. You can load modules via ```
modprobe modulename
```
and if it works ```
sudo nano /etc/modules
``` and put the module name on a new line.

---

