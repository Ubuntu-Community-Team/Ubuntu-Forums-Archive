---
title: "Nvidia Nforce onboard Surround Sound Fix"
date: 2005-11-28
forum: General Help
---

### Post by kscelt on 2005-11-28
I struggled for some time trying to get the rear speakers to work with Ubuntu 5.10 with my MSI K7N2G-ILSR motherboard using the onboard sound. Here for what it is worth, was the solution for me.

1. Ignore the posts about trying to enable things using alsamixer and the like. You HAVE to use the Nvidia official drivers and nvmixer software to get surround channels working.

2. Download this from the Nvidia site - [http://www.nvidia.com/object/linux_nforce_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_1.0-0310.html)

3. I had a deuces of a time getting them properly installed.  You might not have any problems, give a try by opening a terminal and typing "sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run".
 
      If you get problems relating to not finding a source kernel, make sure you have a copy of the source kernel and kernel headers matching the kernel version you are currently running.  Verify current version by typing "uname -a". 
      Look in the usr/src directory to see if you have the source and kernel headers.  
If you do not, these must be downloaded - you can use synaptic. 

example: my current kernel was  ubuntu 2.6.12-10-k7, so I needed           linux-source-2.6.12 and linux-headers-2.6.12-10-k7. I also applied linux-patch-ubuntu-2.6.12 using synaptic.

 Try running "sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run" again, but specify the location of the files by using "sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run --kernel-source-path=/usr/src/linux-headers-2.6.12-10-k7" (use your specific linux-header version folder)

OK, now you may get an error conerning the gcc version check error.  This one is due to 5.10 using 4.0 rather than the 3.4 version your kernel was compiled with. The solution is to verify in synaptic that you have gcc 3.4 installed, and then type "export CC=gcc-3.4" to force it to use the compatible gcc version. Then once again type "sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run --kernel-source-path=/usr/src/linux-headers-2.6.12-10-k7" (use your specific linux-header version folder).

For me, this finally gave me a successful install.  By the way, at the first install screen, I deselected the network drivers and only selected the sound drivers option to install.

Re-boot Ubuntu prior to trying to use nvmixer.

4. After re-booting, open a terminal window, type "nvmixer".  In nvmixer, first go to the speaker tab and select the correct speaker configuration for your setup.  For me (I have Klipsch pc speakers - 4 speakers and a sub) the 4 speaker option was correct.  

Then the important step and key to everything! Go to the Advance Options tab, and select the "LINE TO SURROUND LR" option.  

This is assuming your rear speakers are plugged in to the line-in socket on the optional bracket for this motherboard.  (see your motherboard manual)

Close nvmixer.  

Now a final problem/solution.  Try playing any sound material such as an mp3 file with the player of your choice.  No sound?????

No problem.  The likely issue is that the Nvidia drivers do not work with ALSA, and you probably have this selected, both in general and in your player application.

First go to Multimedia Systems Selector under the "Systems, Preferences" menu. Try changing both "Default Sink" and "Default Source" to "OSS - Open Sound System".  Then depending on your player, find it's engine setting, and change it as well to "OSS - Open Sound System".  Example - for amaroK, go to settings, configure amaroK, engine and change the Output plugin to "osssink".

5.  Have fun, hope this fixed you up! It should at least lead you in the right direction.

---

### Post by kscelt on 2005-11-29
Oh yes, you will probably then find that you lost your system sounds after changing to OSS.  The fix is to go back to synaptic and make sure you install libesd0, which will uninstall libesd0-alsa, as well as install esound-clients as a dependency.  Re-boot and all should be well.

---

### Post by Dearhell on 2006-01-21
This how-to works great in order to have my 4.1 working at last on nforce chipset (and not only 2.1), thanks a lot

The only problem that I have is that after reboot, I lost the changes I have made in the nvmixer, so I have to start it again and select 4.1 speakers each time I reboot

---

### Post by scrillamaan on 2006-01-23
Thanks for the good guide. Do you have any idea what might be different with a set of 5.1 speakers? My motherboard has ports for rear and center speakers but only the center speaker channel seems to work. I have to plug the rear speakers into the port for the center speaker to get anything from them...but them I have no center. Help?

---

### Post by scam on 2006-02-07
root@fuckstick:~# nvmixer
nvmixer: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I cant figure this part out.. 


 uname -a

Linux fuckstick 2.6.12-10-amd64-k8 #1 Mon Jan 16 17:23:13 UTC 2006 x86_64 GNU/Linux



lsmod!!!

nvsound              1711980  0
snd_intel8x0           35968  1
snd_ac97_codec         92376  1 snd_intel8x0
snd_pcm_oss            55008  0
snd_mixer_oss          18880  1 snd_pcm_oss
snd_pcm                97036  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25352  1 snd_pcm
snd                    59560  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  2 nvsound,snd
snd_page_alloc         11856  2 snd_intel8x0,snd_pcm


seems like its still running the old drivers.


I did the 64 bit  driver isntead of the 32 bit.. Having a slight problem here.. I really dont want to install 32 bit since ive got everythign setup already.. Thanks

---

### Post by scam on 2006-02-07
fixed being able to open up nvmixer.. 

now i get errors when i try to turn the volume up for anythuing but the sub error = "volume set failed" 

 it stays on head phones and wont stay on 5.1. 

 in advance options  it wont let me click line to surround LR error = "swap lineln failed"

I have tried it both with my normal user and root.. Same thing.. Someone please help

---

### Post by neurosis on 2006-02-13
Same problem -- I can't adjust any settings on the 'Speaker' tab without getting "Volume Set Failed", etc. I get "Swap LineIn Failed" on the Advanced Options tab.
This is on an Asus K8N-E.

Another weird thing -- even having the proper kernel sources and headers it tells me it needs to compile an interface.. is that normal?

---

### Post by Jason_25 on 2006-02-13
[QUOTE=neurosis]
Another weird thing -- even having the proper kernel sources and headers it tells me it needs to compile an interface.. is that normal?[/QUOTE]

That's normal. It's compiling the kernel module it will use.  Don't forget to stop snd-intel8x0 from loading before the reboot.

---

### Post by NeTo on 2006-02-14
After several attempts, I think I'll give up using nvsound and return to ALSA. I have a MSI K7N2 Delta2 mobo with a Realtek ACL655 codec.

Not only I didn't get surround sound with the Nvidia driver, it messed up everything else. For example, from dmesg I got:```
[4414700.161000] Nvsound: Unable to change the Playback SampleRate 44100, set back to 48000
[4414700.161000] Nvsound: Unable to change the Channel, set back to Stereo

```That means I have playback rate fixed to 48000Hz in 2 channel mode. It's pretty cool to listen to skype conversations like if you're talking to chipmunks :rolleyes:

I wrote and email to nvidia for support, but haven't received a response yet.

I wonder if anyone else (specially with this particular codec) has had these issues. If so, maybe a list can be made of which boards work better with nvsound and which with ALSA.

---

### Post by melat0nin on 2006-02-24
I get the following error, after having installed linux headers and the gcc.  Any ideas?

ERROR: ./nvsound/main/conftest.sh: line 9: cc: command not found

         If you are using a Linux 2.4 kernel, please make sure
         you either have configured kernel sources matching your
         kernel or the correct set of kernel headers installed
         on your system.

         If you are using a Linux 2.6 kernel, please make sure
         you have configured kernel sources matching your kernel
         installed on your system. If you specified a separate
         output directory using either the "KBUILD_OUTPUT" or
         the "O" KBUILD parameter, make sure to specify this
         directory with the SYSOUT environment variable or with
         the appropriate nvidia-installer command line option.

---

### Post by monkey4 on 2006-02-24
If you keep getting kernel and compiler errors installing the drivers, do the following:

sudo passwd
(enter password to turn on root)
su
(enter password from above)
export CC=gcc-3.4
exit

run the installation script again, possibly with --kernel-source-path= option to specify the path to your sources

check the [nForce readme]("http://download.nvidia.com/XFree86/nforce/1.0-0310/ReleaseNotes.html#Loading_the_drivers") for any other problems as well.

---

### Post by melat0nin on 2006-02-25
Hi guys,

I installed the fix and it appeared to work but now my GNOME is buggered.  It comes up with an error saying my session has lasted less than 10 seconds (!) then returns me to the session login screen. It also gives me an error, here it is:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "laurence"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntulaurie:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntulaurie:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntulaurie:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:789: WARNING **: Unable to read ICE authority file: /home/laurence/.ICEauthority

I can't get into ubuntu properly at the moment (I'm running the failsafe terminal, with which i manually opened Firefox to send this).

I also get this error when running synaptic from the failsafe terminal:

(synaptic:9775): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
bash: syntax error near unexpected token `:'


I was attempting to install Amarok from this thread ([http://www.ubuntuforums.org/showthread.php?t=80492](http://www.ubuntuforums.org/showthread.php?t=80492)) around the same time, so it could be either thing that has messed up my system.

Can anyone help?  My Ubuntu is kaput!!

---

### Post by melat0nin on 2006-02-25
Well I managed to sort that error by changing the permissions of .ICEauthority, but my nvmixer doesn't work right.  When I change the Line to Surround LR option, I get an error 'Swap Linein failed'.  Changing my speaker config to 5.1 doesn't work either (well, it changes but the sound doesn't become surround).

Any ideas?

---

### Post by melat0nin on 2006-02-26
[QUOTE=melat0nin]Well I managed to sort that error by changing the permissions of .ICEauthority, but my nvmixer doesn't work right.  When I change the Line to Surround LR option, I get an error 'Swap Linein failed'.  Changing my speaker config to 5.1 doesn't work either (well, it changes but the sound doesn't become surround).

Any ideas?[/QUOTE]

Can anyone help?

---

### Post by melat0nin on 2006-02-27
bump

---

### Post by melat0nin on 2006-02-28
And again?  :(

---

### Post by moffa on 2006-03-01
I can't install the driver at all:

  ERROR: Unable to load the kernel module 'nvsound.ko'.  This is most likely
         because the kernel module was built using the wrong kernel source
         files.  Please make sure you have installed the kernel source files
         for your kernel; on Red Hat Linux systems, for example, be sure you
         have the 'kernel-source' rpm installed.  If you know the correct
         kernel source files are installed, you may specify the kernel source
         path with the '--kernel-source-path' commandline option.

in the installer.  I have the --kernel-source-path as in the first post.

---

### Post by melat0nin on 2006-03-05
This thread might help:

[http://www.ubuntuforums.org/showthread.php?t=58065&highlight=alc650](http://www.ubuntuforums.org/showthread.php?t=58065&highlight=alc650)

It got nvmixer working for me, but I still don't get surround sound.  It's a step in the right direction, though!

---

### Post by Jason_25 on 2006-03-05
I've never used the --kernel-source-path option and it's always installed fine for me.

---

### Post by thagame on 2006-03-13
ERROR: ./nvsound/main/conftest.sh: line 9: cc: command not found

         If you are using a Linux 2.4 kernel, please make sure
         you either have configured kernel sources matching your
         kernel or the correct set of kernel headers installed
         on your system.

         If you are using a Linux 2.6 kernel, please make sure
         you have configured kernel sources matching your kernel
         installed on your system. If you specified a separate
         output directory using either the "KBUILD_OUTPUT" or
         the "O" KBUILD parameter, make sure to specify this
         directory with the SYSOUT environment variable or with
         the appropriate nvidia-installer command line option.


anyone know how to get past this?

---

### Post by tdszero on 2006-03-14
when I watch DVD’s I set up surround sound 5.1 all the speakers work but voices are really quiet and I have tried many different codec but none seem to work any suggestions email me back at [email]travis_labonte@hotmail.com[/email]
i have tried using windows media center, windows media player, nero media player, windvd and many other dvd programs. help me please !!!! :cry:

---

### Post by teletubbie on 2006-04-20
[QUOTE=kscelt]I struggled for some time trying to get the rear speakers to work with Ubuntu 5.10 with my MSI K7N2G-ILSR motherboard using the onboard sound. Here for what it is worth, was the solution for me.

1. Ignore the posts about trying to enable things using alsamixer and the like. You HAVE to use the Nvidia official drivers and nvmixer software to get surround channels working.

2. Download this from the Nvidia site - [http://www.nvidia.com/object/linux_nforce_1.0-0310.html](http://www.nvidia.com/object/linux_nforce_1.0-0310.html)

3. I had a deuces of a time getting them properly installed.  You might not have any problems, give a try by opening a terminal and typing "sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run".
 
      If you get problems relating to not finding a source kernel, make sure you have a copy of the source kernel and kernel headers matching the kernel version you are currently running.  Verify current version by typing "uname -a". 
      Look in the usr/src directory to see if you have the source and kernel headers.  
If you do not, these must be downloaded - you can use synaptic. 

example: my current kernel was  ubuntu 2.6.12-10-k7, so I needed           linux-source-2.6.12 and linux-headers-2.6.12-10-k7. I also applied linux-patch-ubuntu-2.6.12 using synaptic.

 Try running "sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run" again, but specify the location of the files by using "sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run --kernel-source-path=/usr/src/linux-headers-2.6.12-10-k7" (use your specific linux-header version folder)

OK, now you may get an error conerning the gcc version check error.  This one is due to 5.10 using 4.0 rather than the 3.4 version your kernel was compiled with. The solution is to verify in synaptic that you have gcc 3.4 installed, and then type "export CC=gcc-3.4" to force it to use the compatible gcc version. Then once again type "sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run --kernel-source-path=/usr/src/linux-headers-2.6.12-10-k7" (use your specific linux-header version folder).

For me, this finally gave me a successful install.  By the way, at the first install screen, I deselected the network drivers and only selected the sound drivers option to install.

Re-boot Ubuntu prior to trying to use nvmixer.

4. After re-booting, open a terminal window, type "nvmixer".  In nvmixer, first go to the speaker tab and select the correct speaker configuration for your setup.  For me (I have Klipsch pc speakers - 4 speakers and a sub) the 4 speaker option was correct.  

Then the important step and key to everything! Go to the Advance Options tab, and select the "LINE TO SURROUND LR" option.  

This is assuming your rear speakers are plugged in to the line-in socket on the optional bracket for this motherboard.  (see your motherboard manual)

Close nvmixer.  

Now a final problem/solution.  Try playing any sound material such as an mp3 file with the player of your choice.  No sound?????

No problem.  The likely issue is that the Nvidia drivers do not work with ALSA, and you probably have this selected, both in general and in your player application.

First go to Multimedia Systems Selector under the "Systems, Preferences" menu. Try changing both "Default Sink" and "Default Source" to "OSS - Open Sound System".  Then depending on your player, find it's engine setting, and change it as well to "OSS - Open Sound System".  Example - for amaroK, go to settings, configure amaroK, engine and change the Output plugin to "osssink".

5.  Have fun, hope this fixed you up! It should at least lead you in the right direction.[/QUOTE]
Thanks alot! now I have mixing working. :) I love this. 

God bless you

---

### Post by dralaroc on 2006-04-22
I finally got the mixer installed but now I get this error msg in the terminal.  I am not sure what it all means.  I am getting sound but not thru all of my speakers. 

Thanks

dralaroc07@dapperdre:~$ nvmixer
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by Punio4 on 2006-06-16
managed to get the drivers working, however i am getting the same error as the post above, and there is also only one sound source active at a time

---

### Post by Paldo on 2006-06-18
Same problem... Anyone can help? plz...

---

### Post by Paldo on 2006-06-23
2nd try... I getting same problem as "scam" and "neorosis" on first page of this thread... Seems like runnin on old drivers + can't change anything in fvcking nvmixer..... CAN YOU HELP ME/US?

---

### Post by Moiph on 2006-06-26
I'm getting the same input device errors as everyone above...I've gotten everything install, I'm on OSS, sound *works* except for my rear speakers.

---

### Post by computergee on 2006-07-15
I got the drivers installed, and I can run nvmixer, but it dosn't effect anything. When I run nvmixer, I get this in the terminal.
```
jimmy@jimmy-desktop:~$ nvmixer
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

When I try to check off "Line to Surround LR I get, LineIN Failed. I also get error messages when trying to change the volume. Anybody have a fix for this?
Also I can't seem to find the multimedia systems selector, is there a way to set my system to use OSS manually? Will my surround sound games work in cedega? Thanks for the help.

---

### Post by canardo on 2006-09-08
Thank you very much for this I now have SPDIF out on my abit NF7, much aprpeciated was one of the things that had been annoying me and tempting me back to the darkside

---

### Post by one_man_down on 2006-10-22
in order for me to get this to work, i had to add snd_intel8x0 to my hotplug blacklist in /etc/hotplug/blacklist

Thanks to evryone who helped get this solution known!

In an ironic note, my win2K system i dualboot with still can't get surround to work. Makes me love linux that much more :p

---

### Post by dcj on 2007-09-14
This is my first time posting; I've just installed ubuntu and explored around with it (dual boot with winXP). On this particular PC I have an Epox 8RDA+ board with the Nvidia Nforce2 chipset. My 5.1 surround works fine in windows, but in Ubuntu I only get the front 2 speakers. I've tried following the instructions here but I've had difficulty getting the sound drivers to install.

I've downloaded the nforce drivers to my desktop and opened a terminal session and entered the /desktop directory.

The first thing I tried:
helmut@davo:~/Desktop$ sh NFORCE-Linux-x86-1.0-0310-pkg1.run

This loads the installer fine and asks me to accept the license agreement and so on. However, when I accept I get the following error msgs:

"No precompiled kernel interface was found to match your kernel; this means   
  that the installer will need to compile a new kernel interface."
                                         (ok)

and then:

"ERROR: You do not appear to have libc header files installed on your system. 
         Please install your distribution's libc development package. "

Then I tried the next bit:
helmut@davo:~/Desktop$ uname -a
Linux davo 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

In the /usr/src folder I have the following folders: linux=headers-2.6.20-15; linux-headers-2.6.20-15-generic; linux-headers-2.6.20-16 and linux-headers-2.6.20-16-generic.
I don't quite understand how it works yet but I know I've had an update installed via the update manager. When it boots up the boot loader offers the choice to select the -15 version or the -16 version (or WinXP, memtest and recovery mode of course), the default (and the one I'm currently using) is the -16 version.

So the next thing I tried was the command:
helmut@davo:~/Desktop$ sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run --kernel-source-path=/usr/src/linux-headers-2.6.20-16-generic
This did exactly the same thing as with my previous attempt.

Then I tried entering:
su
(password)
export CC=gcc-3.4
exit

and tried doing the installation again, using both commands but getting the same message in the installer. What am I doing wrong and how do I fix it, and get the drivers properly installed?

---

### Post by dennister on 2007-10-04
Hey dcj,

It sounds like ur still kinda new at this, so here are some tips:
[LIST]
[*]the last message in this thread is dated ~18 months ago: a clue that something may be outdated here, and the nvidia package you're trying to install is now quite old...nvidia is up to v 1.23 now, but it's in zip and rpm formats for only the commercial distros...the nvidia forum & news sites keep repeating the fact that they're not willing to support this anymore and we should use the drivers from elsewhere
[/LIST]

'Tis ok, I've been trying for almost a year to get sound from my 7 speakers, all kinds of people from the alsa irc channel have tried to help -- to no avail -- so I tried it just like you did, just for the heck of it. Nooooo way it would build the kernel module.

But I DID finally get sound of my rear speakers tonight, having gotten sound from the center and LFE a few months back. (I'm hoping some other people might help us finish stuff up within the apps.) 
[LIST]
[*]I use kubuntu, so I've got kmix in my kicker...open up the mixer window and select the switches tab. On the right, under "Surround Jack Mode", select "independent", as shared never got me any sound from center speaker or LFE.
[*]To get sound out of rear speakers, (my achievement of the day, which was an idea from reading all sorts of things, including the nvidia faq from their site), try playing around with how the speaker connectors are inserted into the PC's ports. In winblows I had them all working correctly, but the black connector was appropriately in the black port. Move the black connector to the line-in port (probably light grey, but I just had cataract surgery). I had sound from rear speakers at long last, at least according to the test results below.
[/LIST]

Then, in a terminal, type or paste this:
[INDENT]speaker-test -Dplug:surround51 -c6 -twav[/INDENT]

Try these two things to see if you get any improvement; they worked for me.

---

### Post by jocko on 2007-10-04
You are right that this thread is old and outdated.


The problem is that nvidia quit developing their driver a couple of years ago and keep telling us to use the open source alsa drivers, which they claim support our hardware.
That's not completely true, as the alsa driver only supports the generic ac97  compatible part of the sound chipset, and not the actual audio processing unit.
Ok, it is possible to get some sort of sound out of even the ac97, but at least on my computer the sound quality from that is **extremely** poor, and why do software mixing and analog stereo sound when the hardware is capable of hardware mixing and on-the-fly dolby digital encoding?
The only way make use of what made me buy an nforce2 motherboard in the first place is to install nvidia's old drivers.
As the linux kernel have been changed a lot since the last release of nforce drivers, the modules will not compile agains a kernel newer than 2.6.15 (Dapper), but it is possible to patch nvidias drivers to compile even on gutsy, which is why I keep [SIZE=3][an up to date howto for installing nforce sound]("http://ubuntuforums.org/showthread.php?t=253725")[/SIZE].

---

### Post by dcj on 2007-10-05
Thanks for the advice;

sorry about reviving an old thread, I just did a google search for "surround sound ubuntu nforce" before and this was the first result I found. After having a look around I followed the instructions here and still had problems so I decided to sign up and post.

---

