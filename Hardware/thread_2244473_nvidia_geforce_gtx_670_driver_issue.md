---
title: "nvidia geforce gtx 670 driver issue"
date: 2014-09-16
forum: Hardware
---

### Post by bigbudz on 2014-09-16
Hi I am having a time getting the video driver installed right on my alienware x51 r2.
clicking on additional drivers would say i am using nvidia-331 but the screen looks like its 800x600.
so I figured I would try the latest nvidia driver and I gave nvidia-340 a shot.
well here's where i stand so far.

al@al-Alienware-X51-R2:~$ lspci -vnn | grep -i VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [GeForce GTX 670] [10de:1189] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: NVIDIA Corporation Device [10de:097a]
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at da000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Memory at d8000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	[virtual] Expansion ROM at db000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia

01:00.1 Audio device [0403]: NVIDIA Corporation GK104 HDMI Audio Controller [10de:0e0a] (rev a1)
	Subsystem: NVIDIA Corporation Device [10de:097a]
al@al-Alienware-X51-R2:~$ sudo nvidia-settings 

(nvidia-settings:17013): IBUS-WARNING **: The owner of /home/al/.config/ibus/bus is not root!
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

does anyone have any idea of where to go from here?
any help would be really appreciated.

---

### Post by oldfred on 2014-09-16
If it is in /home I do not think it should be root. My ibus is owned by me.

How did you install?
Repository is always the first and usually best choice. 
Then there are ppa's that pre compile newer drivers & kernels to work with Ubuntu. 
And then you have the direct download from nVidia which leaves you on your own. Really only required if you have so new of a video card that the only drive that works is the newest driver. Or if you like to experiment to see if there are improvements. But even tests often use the ppas.

Did you totally purge previous install, as a new install from a different source almost always conflicts?

 But you have to totally purge before installing a different version or else you will have major conflicts
Shows various install methods for nVidia. 13.04 but still the same
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

      
 # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
# newest versions do not seem to normally have xorg, so if an error just ignore and proceed.
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by redrumrogue on 2014-09-17
What happens if you open the nvidia-settings from the app menu rather than sudo command line?

---

### Post by bigbudz on 2014-09-19
i tried purging the old nvidia drivers, and installing by dash -> addition drivers, but when i tried 
'sudo nvidia-settings' the registry key file is gone. here is the output.

ERROR: Error querying target relations


(nvidia-settings:2911): IBUS-WARNING **: The owner of /home/al/.config/ibus/bus is not root!
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at either
       /usr/share/nvidia/nvidia-application-profiles-331.38-key-documentation
       or /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       preopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.

---

### Post by oldfred on 2014-09-19
I get the same error, but it runs for me.

But the issue really is that you must use gksudo for gui apps and sudo for terminal apps. 
It gives all sorts of errors if you use sudo for gui apps. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
> You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo  sets HOME=~root, and copies .Xauthority to a tmp directory.  This  prevents files in your home directory becoming owned by Root.  (AFAICT,  this is all that's special about the environment of the started process  with gksudo vs. sudo). 

Recent versions of some flavours might not have gksu installed. 


---

### Post by redrumrogue on 2014-09-19
Question for oldfred - do you know if sudo -i <command> is the same as gksudo <command>?  I read somewhere that it was but not sure if it's true.  The reason I ask is that it appears that gksudo (gksu) is not included in ubuntu 14.04.  I was looking for an alternative a while back and read a little about sudo -i

---

### Post by oldfred on 2014-09-19
I do not think so. the sudo -i just lets you stay in Admin mode until you exit. sudo lets you stay  in for something like 5 minutes.
You have to install gksu.
sudo apt-get install gksu

Not sure then if gksudo works or now you just use gksu?
There was some discussion about pkexec but I do not know about that.

---

### Post by redrumrogue on 2014-09-19
Sorry, don't mean to hi-jack this thread.  I've opened a new thread under General Help for this question.  Thanks OldFred!

---

