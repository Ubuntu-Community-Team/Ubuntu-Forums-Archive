---
title: "Audio capture and microphone on ASUS eee PC 701 with Intrepid"
date: 2009-01-27
forum: Hardware
---

### Post by Orange_and_Green on 2009-01-27
Hello everybody! It's been a long time, I hope everyone is well.

I spent the weekend installing Ubuntu 8.10 Intrepid Ibex on our ASUS eeePC 701. 

Unfortunately most hardware doesn't work out of the box; however, following the instructions on [this site]("https://help.ubuntu.com/community/EeePC/Fixes") I could get everything to work _except for audio capture_.

I couldn't find a unitary, comprehensive guide on the Internet about this subject. I succeeded in the end, following several pieces of advice. I thought I'd post all the steps I followed here, so maybe others having the same problem can profit from my efforts too...

OK, here goes. To enable sound recording (especially for programs like Ekiga or Skype) on the ASUS eee 701 on Ubuntu 8.10 Intrepid Ibex, I followed these steps:

1) Install Ubuntu 8.10 Intrepid Ibex, run all the updates first. 

2) System->Administration->Synaptic Package Manager:
   Search for and Uninstall all packages whose name starts with "pulseaudio"
   Install "esound"

3) Delete the file /etc/X11/Xsession.d/70pulseaudio by running the following command:
   ```
sudo rm /etc/X11/Xsession.d/70pulseaudio
```
   Warning: Failing to do so will make you unable to log into the system. If you find yourself in this situation, log into a failsafe GNOME session and delete the file from there.

4) As suggested [here]("https://help.ubuntu.com/community/EeePC/Fixes"), add the line "options snd-hda-intel model=3stack-dig" to the file "/etc/modprobe.d/alsa-base" by doing
   ```
gksu gedit /etc/modprobe.d/alsa-base
``` 
   and paste the line at the end of the file.

5) Reboot your system.

5) Go to System->Preferences->Sound.
   On the tab "sound", make sure that the first two entries read "ALSA - Advanced Linux Sound Architecture". Set the third and the fourth one ("Sound Playback" and "Sound Capture" in "Audio Conferencing") to "HDA Intel ALC662 Analog (ALSA)". The last one ("Device") should read "HDA Intel (ALSA mixer)".

   On the tab "Sounds", _disable_ the system sounds. If you don't, you will get choppy sound when recording, probably because of a buffer that is not flushed or something.

7) Open Volume Control (the loudspeaker icon on the top right panel; if you don't see one, right click the panel and add the "Volume Control" applet), click "Preferences" and tick all boxes. In the "Playback" Tab, make sure that EVERYTHING is full volume and not muted. Raise the volume to 100% for "Capture" in the "Recording" tab, and make sure that the "Input" tab has the "Mic" (not Front Mic) selected.

8) Now you should be able to record from the sound recorder (test it). To be able to use Skype, go into the Audio options and select "HDA INtel (hw:Intel,0)" for "Sound Input".

This should do the trick.

To conclude, a few random tips about other aspects of the installation:

* If you don't see the network manager applet on the top right panel, right click the panel and add "Notification Area".
* I really recommend the eee-control package to make the function keys work. You can download it from [this site]("http://greg.geekmind.org/eee-control/").
* Shutdown doesn't work out of the box, it's hard to notice but watch for the power LED staying on even when the screen is turned off after shutdown. The fix is described in [this article]("https://help.ubuntu.com/community/EeePC/Fixes").
* To make the microphone work in Skype, go into the Audio options and select "HDA INtel (hw:Intel,0)" for "Sound Input".
* I used my backup program to automatically restore all the packages I had installed. Check out my signature if you think this may interest you too. ;) 
* Intrepid Ibex is really fantastic, much smoother and better integrated than its predecessors IMHO. It generally works faster, it recognised and configured my UMTS stick on-the-fly (while it worked on Hardy with the latest version of umtsmon, it was a little awkward to use), and the encrypted Private directory is simply awesome. I like it really much, thanks to all the developers for this brilliant distro.

Good night everyone, and enjoy your Ubuntu :)

---

### Post by asbesto on 2009-02-26
THANK YOU! :)

This solved everything in my eeepc 701 under eeebuntu standard.

Now I can capture thru mic, and also now ekiga is working! :)

:p

---

### Post by nasamuffin on 2009-04-12
Ahhh!  Thank you! :)  This fixed recording on my 1000HA in Ubuntu Eee (Easy Peasy) as well!

---

### Post by rdsherwood on 2009-04-24
This also fixed my Skype and recording problems on an EEE PC 701 running 9.04 Jaunty. Thank you!!

---

### Post by aysiu on 2009-04-28
> **rdsherwood said:**
> This also fixed my Skype and recording problems on an EEE PC 701 running 9.04 Jaunty. Thank you!!
This appeared to work for me in Jaunty... but then I got some annoying loud system beep every time I shut down the computer.

I used a workaround to get the beep to disappear, and now Skype doesn't work.

Do you get the annoying system beep noise?

---

### Post by RitterSport on 2009-05-04
I've gotten that annoying beep once, last night (I only installed 9.04 over the weekend) -- scared the cr*p out of me, actually.  I thought it was a fire alarm for a minute.  
 
Anyway, FWIW, I haven't followed any of the advice in this thread yet, and I still got the beep.  I managed to get Skype to work, but the mic input is very choppy.  I'm going to try some of the above when I get home.
 
I have a eeePC 701 with 1GB RAM and Jaunty.

---

### Post by pp47 on 2009-05-18
Follow this link it works  on Eeeepc 701 U 9.04 (at least the permanent solution) but it at your own risk : I didn't foundd any drawback  to disable "pcspkr" but who knows ?


[http://thedaneshproject.com/posts/how-to-disable-the-beep-in-linux/](http://thedaneshproject.com/posts/how-to-disable-the-beep-in-linux/)

---

### Post by trxgt05 on 2009-06-17
You can spend the time to go through all the fixes on the previously linked eee fixes page, but the simplest solution I've found to fixing the audio issues as well as any other problem is to us the NiceeePC script. 

[https://launchpad.net/niceeepc](https://launchpad.net/niceeepc)

The only real drawback to is is that was designed for Hardy. I've gotten it to work with newer releases though. The only problem I've had on newer versions (especially Juanty) is when I connect to a network via wifi, the connection dies after about 2 minutes. This seems to be a common problem in those releases though. (see [http://ubuntuforums.org/showthread.php?t=1146367&highlight=asus+701+wifi+lose+connection&page=1](http://ubuntuforums.org/showthread.php?t=1146367&highlight=asus+701+wifi+lose+connection&page=1))

Sorry for getting off-topic, but I highly recommend the script.

---

### Post by jinnk on 2009-06-18
After fixing all problems outlined [here]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20701-SD%20/%20702") I only had to adjust the capture source in the Volume Settings to make Skype, Ekiga, etc work.

1. Open Volume Control (from the top right speaker icon)
2. Hit the Preferences button
3. Make sure there's a check mark next to the "Input Source, Options" track.
4. Click OK
5. Go to the Options tab, then choose "Front Mic" for the Input Source.

Do a test call to make sure your volumes are all good.

---

