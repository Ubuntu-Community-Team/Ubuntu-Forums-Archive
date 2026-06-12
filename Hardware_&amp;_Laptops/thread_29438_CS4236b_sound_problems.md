---
title: "CS4236b sound problems"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by Hamilton on 2005-04-24
Hello everyone.  I have Ubuntu 5.04 installed on a Dell OptiPlex GX1. I am having problems getting sound to work. When I login I get this message:

"Informational - artsmessage

Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device."

I have searched high and low and followed all advice from the below searches:

Search results for cs4236b at [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)

[http://www.ubuntuforums.org/showthread.php?t=23369&highlight=cs4236b](http://www.ubuntuforums.org/showthread.php?t=23369&highlight=cs4236b)

[http://www.ubuntuforums.org/showthread.php?t=27618&highlight=cs4236b](http://www.ubuntuforums.org/showthread.php?t=27618&highlight=cs4236b)

[http://www.ubuntuforums.org/showthread.php?t=16501&highlight=cs4236b](http://www.ubuntuforums.org/showthread.php?t=16501&highlight=cs4236b)

[http://www.ubuntuforums.org/showthread.php?t=2343&highlight=cs4236b](http://www.ubuntuforums.org/showthread.php?t=2343&highlight=cs4236b)

[http://www.ubuntuforums.org/showthread.php?t=1689&highlight=cs4236b](http://www.ubuntuforums.org/showthread.php?t=1689&highlight=cs4236b)

When following advice from the searches I get the following errors:

root@ubuntu:~# modprobe snd-cs4236
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
FATAL: Error running install command for snd_cs4236
root@ubuntu:~# apt-get install esound-clients
Reading package lists... Done
Building dependency tree... Done
esound-clients is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~# esdplay /usr/share/sounds/startup3.wav
/bin/sh: -c: line 0: unexpected EOF while looking for matching `''
/bin/sh: -c: line 1: syntax error: unexpected end of file
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
root@ubuntu:~# sudo modprobe cs-4236
FATAL: Module cs_4236 not found.
root@ubuntu:~# alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
root@ubuntu:~#

I use to have SuSE 9.1 and 9.2 installed and they detect and play sounds without any problems. I have tried the newest editions of SuSE 9.3 and Scientific Linux and they can not detect my sound card.  I am starting to think that Ubuntu 5.04, SuSE 9.3 and Scientific Linux have the latest Linux Kernel and for some reason support for the cs4236b chipset has been dropped or changed in some way that causes the sound not to work. Any thoughts or ideas on how to correct this?

---

### Post by Hamilton on 2005-04-25
:confused:

---

### Post by Hamilton on 2005-04-26
Support for Ubuntu sure sucks. I figured out how to get the sound to work, I booted to Win XP.  \\:D/

---

### Post by kelean on 2005-04-27
Hamilton I have the same computer and the same problem.  I just came across in one of the threads these lines
         
          Adding the following line to /etc/modules
          snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

I added that to to the /etc/modules file saved it rebooted and sound works now.  I have been doing a lot of reading and tring things with no luck.  But just doing that one simple thing sound works now. 

here is the post:
 [http://www.ubuntuforums.org/showthread.php?t=2343&highlight=cs4236b](http://www.ubuntuforums.org/showthread.php?t=2343&highlight=cs4236b)

It was one of the ones you had in your post thanks
kelean

---

### Post by ka1axy on 2005-11-25
Works on Ubuntu 5.10, too - I just had the same problem and that one line, added to /etc/modules fixes it!

Peter

---

### Post by holomate on 2005-11-27
[QUOTE=kelean]
          Adding the following line to /etc/modules
          snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

I added that to to the /etc/modules file saved it rebooted and sound works now.  I have been doing a lot of reading and tring things with no luck.  But just doing that one simple thing sound works now. 
[/QUOTE]

Just tried it and rebooted. No change. My Dell Optiplex GX1 is still refusing to install sound.

---

### Post by danrael on 2006-05-24
[QUOTE=Hamilton]Support for Ubuntu sure sucks. I figured out how to get the sound to work, I booted to Win XP.  \\:D/[/QUOTE]


Yes, your sound card now works, but your entire computer is now re-immersed back into shark-infested waters!  That's OK.  Just stick your head in the sand and maybe they will go away.  At least you have sound, right? :shock:

---

### Post by danrael on 2006-05-24
[QUOTE=kelean]Hamilton I have the same computer and the same problem.  I just came across in one of the threads these lines
         
          Adding the following line to /etc/modules
          snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

I added that to to the /etc/modules file saved it rebooted and sound works now.  I have been doing a lot of reading and tring things with no luck.  But just doing that one simple thing sound works now. 

here is the post:
 [http://www.ubuntuforums.org/showthread.php?t=2343&highlight=cs4236b](http://www.ubuntuforums.org/showthread.php?t=2343&highlight=cs4236b)

It was one of the ones you had in your post thanks
kelean[/QUOTE]

I can't seem to get to square one with this line:  I cannot enter text into the modules file.  Can you please explain exactly how you went about doing this?  T'would be much appreciated.  Others here all say the same thing, but don't tell how to do it.

---

### Post by danrael on 2006-06-01
Here is the final procudere I used to get my sound working:

**How to activate Crystal CS4236B Audio on Optiplex GX1:**

> At the Desktop, open Applications> Accessories> Terminal
> At the flashing cursor, type: sudo gedit
> Type your system password
> In gedit, click on the "Open" icon
> Double-click "File System" from the lefthand sidebar
> Double-click the "etc" folder
> Scroll down past the folders to the "modules" file, and open it
> On the line after the last entry, type:

snd-cs4236 dma1=1 dma2=3 io=0x0534 irq=5

> Click the "Save" icon, and Quit the program. Reboot.
> Go to System> Preferences> Sound
> "CS4236B" should appear in the Default sound card field
> Make sure "Enable sound server startup" is unchecked
> Go to Applications> Sound and Video> Volume Control
> Make sure the volume level is up in both Playback and Capture
> Open CD Player or Sound Juicer and test for audio from a music cd

---

### Post by DarkW0lf on 2006-10-13
I am being told that this device does not exist when using 'sudo modprobe snd-cs4236'.

Could this have anything to do with Drake telling me my sound is an AT-style speaker sound and not the CS4236 as Brezzy and Warty told me.

It seems like that drake is detecting the sound card differently or something. Would adding that line to etc/modules still work if modprobe can't load the module ?

---

### Post by sandyeggoboy on 2007-02-24
Darkw0lf ---

sudo nano /etc/modules

This will allow you to edit the file. Then Cntl-X, then Y, then Enter

hope this helps.

---

### Post by frehberg on 2007-03-30
check if your user is in group "audio", required to access device /dev/dsp

$ groups MyLogin

If "audio" is not listed here, add the group "audio" to the list, comma-seperated list:

$ usermod -G CommaSeperatedList,audio MyLogin

eg: I did for my login "frehberg":

usermod -G frehberg,users,audio frehberg

Hope that helps

---

