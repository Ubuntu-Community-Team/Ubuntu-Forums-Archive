---
title: "no sound using IDT HDA on-board sound in ubuntu 9.10"
date: 2010-04-27
forum: Hardware
---

### Post by compiz addict on 2010-04-27
I'm using a desktop system, and I haven't had sound since I installed Ubuntu. I'm running 9.10.

Ubuntu used to detect my hardware (but no sound), but someone told me to use this:
```

sudo alsaconf
<Follow directions choose your sound card>
<If your are running gnome, you may need the following>
sudo apt-get -y install gnome-audio esound

```

After that, not only did my sound refuse to work, but it didn't detect my hardware anymore. alsaconf gave me a "command not found" error.

Any ideas? Please help ASAP!

---

### Post by compiz addict on 2010-04-27
.... Please?

---

### Post by lidex on 2010-04-27
First thing to do for no sound in karmic is go to this page and work through it:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

Still no sound? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by compiz addict on 2010-04-28
I also tried things earlier to get my sound working, I don't remember what though.
I can tell my system has quite a few sound related problems though...

Here's the output:
```

eric@jurgen:~$ uname -a
Linux jurgen 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
eric@jurgen:~$ aplay -l
aplay: device_list:223: no soundcards found...
eric@jurgen:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
eric@jurgen:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
eric@jurgen:~$

```

---

### Post by lidex on 2010-04-28
> **compiz addict said:**
> I also tried things earlier to get my sound working, I don't remember what though.
I can tell my system has quite a few sound related problems though...

Here's the output:
```

eric@jurgen:~$ uname -a
Linux jurgen 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
eric@jurgen:~$ aplay -l
aplay: device_list:223: no soundcards found...
eric@jurgen:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
eric@jurgen:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
eric@jurgen:~$

```

Click the alsa-upgrade-script link in my sig to install newer version of alsa. Looks like you don't have a working install.

---

### Post by compiz addict on 2010-04-28
Ok, i've done that, and it successfully finished, but nothing seems to have changed. My hardware still isn't detected, and the output from the command you gave me is still the same.

---

### Post by lidex on 2010-04-28
This command?
```
cat /proc/asound/version

```
Go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
and work through the steps.

---

### Post by compiz addict on 2010-04-28
Still nothing, but most of the steps had problems.
Here is what I did for each step:

Wrong kernel version:
I didn't do anything here,
the kernel was already correct.

Sound drivers need to be updated:
the "linux-backports-modules-alsa-karmic-generic" package didn't launch, it gave me this error:

```

Invalid url: 'apt://linux-backports-modules-alsa-karmic-generic/' given, exiting

Invalid package name 'linux-backports-modules-alsa-karmic-generic/'

```
EDIT: I got it installed using this command and dropping the forward-slash at the end:
apturl apt://linux-backports-modules-alsa-karmic-generic

Another process locking the sound card:

I did this command
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*

and I got this;
```

Cannot stat /dev/dsp7: No such file or directory
Cannot stat /dev/dsp7: No such file or directory
Cannot stat /dev/dsp8: No such file or directory
Cannot stat /dev/dsp8: No such file or directory
Cannot stat /dev/snd/*: No such file or directory
Cannot stat /dev/snd/*: No such file or directory
Cannot stat /dev/seq*: No such file or directory
Cannot stat /dev/seq*: No such file or directory

```

Advanced Mixer (Volume Control):

alsamixer gave me this;
cannot open mixer: No such file or directory

I didn't do anything after this point.

---

### Post by lidex on 2010-04-28
Run this command in a terminal:
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa libao2
```

Reboot!

---

### Post by compiz addict on 2010-04-29
Ok, so after I installed  that package that I said I got to work, my graphics driver messed up, and I had to install the old one. Yeah, my computer must have some serious problems, lol.

So now I've tried the command you sent me and still nothing. Still doesn't detect my drivers and still says "No such file or directory" when I type "cat /proc/asound/version".

I think I might have to backup all my files and re-install Ubuntu.

If I need to, do yo have a script to make it easier to backup my settings and files, and drivers (except sound)? And should I install with the new 10.04?

---

### Post by lidex on 2010-04-29
If you want to install lucid, wait for the official release, which is I believe tomorrow. In the mean time try this:
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by compiz addict on 2010-04-29
Upgraded to 10.04. Didn't re-install Ubuntu or anything, just upgraded. Now it detects my hardware again.

Here's what I get from the original commands you gave me:
```

eric@jurgen:~$ uname -a
Linux jurgen 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
eric@jurgen:~$ aplay -l
aplay: device_list:223: no soundcards found...
eric@jurgen:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
eric@jurgen:~$ head -n 1 /proc/asound/card*/codec#*
Codec: SigmaTel STAC9221 A2
eric@jurgen:~$ 

```

Should I run those commands to re-install ALSA again?

---

### Post by compiz addict on 2010-04-29
nevermind, I messed it up again. I'll use that sudo command to reinstall Ubuntu now.

EDIT:
That command didn't make a noticeable difference.

Dang it! I just upgraded and I might have been getting there, and I screwed it up before you replied. Lesson learned: I can't troubleshoot Linux by myself. So, now that it's official, my ALSA driver and everything related are broken, will a normal soundcard work?

---

### Post by compiz addict on 2010-05-02
*bump*

---

### Post by lidex on 2010-05-02
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by compiz addict on 2010-05-02
[http://www.alsa-project.org/db/?f=6e6058a878e31e23c1264c710f52565969492ef5](http://www.alsa-project.org/db/?f=6e6058a878e31e23c1264c710f52565969492ef5)

---

### Post by lidex on 2010-05-02
OK. Take a deep breath. Click the alsa-upgrade-script link in my sig and follow the instructions there. Your alsa install is botched - need to fix it first.

---

### Post by compiz addict on 2010-05-02
Ok, it's done installing. Now what?

Oh, and also, because i'm such a script junkie, I made a little script to go through that whole process. This is the code I made:
```

echo "Downloading TAR file"
echo "Download of TAR file from server:" >> alsa-upgrade-log.log
wget "67.193.97.223/AU.tar" >> alsa-upgrade-log.log

echo "Extraction of TAR file"
echo "extraction of TAR file:" >> alsa-upgrade-log.log
tar xvf AU.tar >> alsa-upgrade-log.log

echo "Running download script"
echo "Running of script with -d (download) option" >> alsa-upgrade-log.log
sudo ./AlsaUpgrade-1.0.22.1-2.sh -d >> alsa-upgrade-log.log

echo "Running compile script"
echo "Running of script with -c (compile) option" >> alsa-upgrade-log.log
sudo ./AlsaUpgrade-1.0.22.1-2.sh -c

echo "Running install script"
echo "Running of script with -d (install) option" >> alsa-upgrade-log.log
sudo ./AlsaUpgrade-1.0.22.1-2.sh -i

```

So, now instead of going all the way over to that other thread, you can upgrade ALSA using these two commands:
```

wget "67.193.97.223/alsa.sh"
sh ./alsa.sh

```
and what that does is it downloads alsa.sh from my server, and then runs it with the sh command.

---

### Post by lidex on 2010-05-02
> **compiz addict said:**
> Ok, it's done installing. Now what?


Do you have sound?

---

### Post by compiz addict on 2010-05-02
nope :(

---

### Post by compiz addict on 2010-05-02
eric@jurgen:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory

Yeah, I think ALSA is still broken...

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by compiz addict on 2010-05-02
```

eric@jurgen:~$ uname -a
Linux jurgen 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
eric@jurgen:~$ aplay -l
aplay: device_list:223: no soundcards found...
eric@jurgen:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory
eric@jurgen:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
eric@jurgen:~$ 

```

AMD Athlon 64 X2 Dual Core Processor 5000+
2 GB of memory

I have my motherboards serial number somewhere, i'll make a reply when I find it.

---

### Post by compiz addict on 2010-05-02
Ok, here's the motherboards model number: a740gm-m

---

### Post by lidex on 2010-05-02
Try this:
```
sudo apt-get remove --purge alsa-base alsa-oss alsa-utils libasound2 libasound2-plugins linux-sound-base
```

Next:
```
sudo apt-get install alsa-base alsa-oss alsa-utils libasound2 libasound2-plugins linux-sound-base
```

Now REBOOT.

---

### Post by compiz addict on 2010-05-02
Woah! That scared the sh*t out of me! It removed wwwaayyyy more packages than necessary. Had to do "sudo apt-get install ubuntu-desktop" among other things, from a command line prompt, paranoid thinking all my data might be gone!

It gets worse...
Still no sound, and my ALSA driver is still messed up.

---

### Post by lidex on 2010-05-02
ubuntu-desktop is an empty metapackage, no harm in its removal. Yeah, I don't know what you did previously, but something is mightily amiss. At this point i would suggest backing up your data and doing a fresh install.

---

### Post by compiz addict on 2010-05-02
As I feared. Is there an easy way to back up my data, and my settings as well? Like maybe a folder where most packages save their settings? Because I've noticed that if a package is removed, it's settings generally come back when it's re-installed.

---

### Post by lidex on 2010-05-02
> **compiz addict said:**
> As I feared. Is there an easy way to back up my data, and my settings as well? Like maybe a folder where most packages save their settings? Because I've noticed that if a package is removed, it's settings generally come back when it's re-installed.

Yes, your home folder, or more specifically /home/your-username, contains your data and program settings.

---

### Post by compiz addict on 2010-05-02
Really? All of it? I'm assuming not my Apache settings though, right? Because Apache seems to be everywhere (/etc, /var, you name it).

---

### Post by lidex on 2010-05-02
No. I would worry first about my data, then any configuration files you don't want to lose. Some of those things need to start from scratch, like your audio config.

---

### Post by compiz addict on 2010-05-02
Ok, thanks. Those Ubuntu developers (Or is it just Linux in general that has the awesome backup abilities?) sure know what they're doing. In Windows I would have just used my computer without sound rather than format. I still have to burn an Ubuntu 10.04 disk, so i'll do that tomorrow (or overnight) so my parents don't complain to me about using up bandwidth (the internet is the TV at my house).

---

### Post by compiz addict on 2010-05-03
Ok, fresh install of Ubuntu. It's actually detecting my sound-card now! I don't have any sound yet, but I do have a USB headset that works for now :)

---

### Post by compiz addict on 2010-05-05
*bump*

---

### Post by lidex on 2010-05-05
Will need some info. Go back to post #22

---

### Post by compiz addict on 2010-05-06
Here's my output:
```

eric@jurgen:~$ uname -a
Linux jurgen 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
eric@jurgen:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
eric@jurgen:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
eric@jurgen:~$ head -n 1 /proc/asound/card*/codec#*
Codec: SigmaTel STAC9221 A2
eric@jurgen:~$ 

```

Logitech USB Headset is the name of my USB headset i'm using. The headset works perfectly, probably because it's USB and doesn't need a sound-card (I would assume), but I have no sound from my speakers .

---

### Post by lidex on 2010-05-06
OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

---

### Post by compiz addict on 2010-05-06
You forgot to tell me to run apt-get update again after updating the kernel and restarting =P.

Anyway, still no sound.

---

### Post by lidex on 2010-05-06
> **compiz addict said:**
> You forgot to tell me to run apt-get update again after updating the kernel and restarting =P.

Anyway, still no sound.
Have you checked alsamixer?
What is PC mfg/model #?
Or at least motherboard mfg and number of digital/analog audio jacks --be specific.

---

### Post by compiz addict on 2010-05-06
All I have is the mothermoard's model number, which is a740gm-m

I have 3 jacks at the back (Line In, Speakers, and Mic. Line In had an option to be switched to "Back Speakers" in my old Windows driver, and Mic could be switched to center. Also, I have a headphone and a mic jack at the front.

---

### Post by lidex on 2010-05-06
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=3stack  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.


Another option to try is:
```
options snd-hda-intel model= auto
```
Most of the options for this codec seem to be for macs.

---

### Post by compiz addict on 2010-05-07
it didn't work. Maybe my sound-card just doesn't work.

---

### Post by compiz addict on 2010-05-07
AHHHHH!!! noo!!!! my headphones just broke by themselves while I was watching a video!!!! Oh well, they're really cheap for USB headphones.

---

### Post by lidex on 2010-05-08
Use gnome-alsamixer and enable everything in 'Edit>Soundcard Properties'.

---

### Post by compiz addict on 2010-05-08
Didn't work :(. But I got a different soundcard that also didn't work, BUT NOW IT WORKS!!!! Thankyou!!!

---

### Post by compiz addict on 2010-05-08
should I mark it as solved now, even though it didn't work on my on-board sound as I was hoping for?

---

### Post by lidex on 2010-05-08
No, probably not.

---

