---
title: "Please help."
date: 2008-11-20
forum: Hardware
---

### Post by esculayd4724 on 2008-11-20
Hello,

I recently upgraded to Ubuntu 8.10 from 8.04.  Just about every day I have to try to repeat the same steps I find on the internet to fix my issue which is:

There is no sound in Firefox.
The version is 2.0.0.17 .

I have used this website to try to fix it, but after I shut down my computer and then turn it back on, the problem re-appears:
[URL="http://ubuntuforums.org/showthread.php?t=789578"]

I have also tried a few others, but all come out to the same conclusion, which is no fix I have found is permanent.

Thanks for your help.

---

### Post by pytheas22 on 2008-11-20
Could you please list in detail the exact steps/commands that you have to enter to get sound working after each fresh reboot?  With that, we can probably either write a boot script to do it automatically for you, or figure out another way to make the changes persist after reboots.

---

### Post by esculayd4724 on 2008-11-20
I follow the steps listed on the website which I stated :

Part A: Common instructions (Hardy & Intrepid)
All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.

1. Backup (and then delete) your previous configuration files:
Code:

$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
$ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf

Note: Don't worry if some of these files did not exist on your system.

2. Ensure you have Adobe Flash & the necessary PulseAudio libraries and configuration utilities installed:
Code:

 $ sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree

3. Ensure the evil "libflashsupport" library is not installed:
Code:

$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound

4. Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "PulseAudio". Close the application when you're finished.

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

---

### Post by pytheas22 on 2008-11-20
If you do just step 4, does sound work?  If not, after step 5, does it work?

This will help to further figure out what exactly needs to go in the script.

---

### Post by esculayd4724 on 2008-11-20
Doing only 4 did nothing.
So then I tried 5 and that didn't work either.
Also, everything was already like it when it told me those steps, so nothing was changed anyways.

---

### Post by pytheas22 on 2008-11-21
Strange...

In that case, please reboot, then run these commands and post the output:

```
mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree
sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound

```

I'm still not sure what exactly does the trick to make your sound work, but hopefully the output of the stuff above will reveal it.

---

### Post by esculayd4724 on 2008-11-21
the first couple said the files didnt exist.
the last two made no changes.

---

### Post by pytheas22 on 2008-11-21
Could you post the whole command-line output from the four commands, please?  I'd really like to see the entire output in order to figure out what it's doing.

---

### Post by esculayd4724 on 2008-11-23
#1 :

lucas@lucas-laptop:~$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
mkdir: cannot create directory `/home/lucas/pulse-backup': File exists

#2:

lucas@lucas-laptop:~$ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
[sudo] password for lucas: 
rm: cannot remove `/home/lucas/.asound*': No such file or directory
rm: cannot remove `/etc/asound.conf': No such file or directory

#3:

lucas@lucas-laptop:~$ sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2-plugins is already the newest version.
padevchooser is already the newest version.
libao-pulse is already the newest version.
libsdl1.2debian-pulseaudio is already the newest version.
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

#4:

lucas@lucas-laptop:~$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not installed, so not removed
Package flashplugin-nonfree-extrasound is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by pytheas22 on 2008-11-23
Thanks for that.  If you run these commands after a reboot, does it fix the problem?  These seem to be the only commands that are actually doing anything:
```

sudo cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
sudo rm -r ~/.pulse
```

---

### Post by esculayd4724 on 2008-11-24
None worked.

#1:

lucas@lucas-laptop:~$ sudo cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
cp: cannot stat `/home/lucas/.pulse': No such file or directory
cp: cannot stat `/home/lucas/.asound*': No such file or directory
cp: cannot stat `/etc/asound.conf': No such file or directory

#2:

lucas@lucas-laptop:~$ sudo rm -r ~/.pulse
rm: cannot remove `/home/lucas/.pulse': No such file or directory

---

### Post by pytheas22 on 2008-12-05
Sorry, I lost track of this thread and just remembered it.  Is your problem still unresolved?  If so I can try to work harder to figure out what's going on.  I admit that so far nothing has been going as I expected, but with enough work we should be able to figure it out.

---

