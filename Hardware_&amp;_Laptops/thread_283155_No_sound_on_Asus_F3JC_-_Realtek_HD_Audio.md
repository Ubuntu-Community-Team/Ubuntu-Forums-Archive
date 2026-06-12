---
title: "No sound on Asus F3JC - Realtek HD Audio"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by ViGiLnT on 2006-10-23
I've just got my new laptop wich is an Asus F3JC with an Realtek High Definition Audio sound card.

The driver used in windows is ALC660.

I've got no sound in dapper...

What can I do to make it work ? Does anyone have the same problem ?

---

### Post by ViGiLnT on 2006-10-24
There are two sound cards detected in dapper:

- HDA Intel
- Realtek ALC8** (don't know the exact numbers, not in linux at the moment)

Can't anyone help ?

---

### Post by ViGiLnT on 2006-10-25
```
vigilnt@i-laptop:~$ aplay --list-devices
**** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: Intel [HDA Intel], dispositivo 0: ALC861 Analog [ALC861 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

I've already compiled alsa v1.0.12 and added one of this modules to my /etc/modprobe.d/alsa-base from ALSA-Configuration.txt:

```
ALC861/660
	  3stack	3-jack
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack with SPDIF I/O
	  3stack-660	3-jack (for ALC660)
	  uniwill-m31	Uniwill M31 laptop
	  auto		auto-config reading BIOS (default)
```

I've followed this guide: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and already posted my problem on the bugtracker:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/63228](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/63228)

Is there anything else I can do ? I don't think I can give anymore information....

Help ?

---

### Post by ViGiLnT on 2006-10-27
I can't believe that there's not a soul who knows something to solve this issue...

---

### Post by didobuntu on 2006-10-27
> **ViGiLnT said:**
> I can't believe that there's not a soul who knows something to solve this issue...
You are lucky,
download the last alsa-driver 1.0.13 ... now you sound card is taken into account .. 

Mine has never run until now

---

### Post by ViGiLnT on 2006-10-28
I already compiled and installed those drivers, following the guide from [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) ...

I still got no sound, The OSS-lib driver that I downloaded from alsa-project website is in version 1.0.12, may that be the problem ?

I don't know if there's something that I should have done, and haven't, like modprobe snd-hda-intel after the 1.0.13 driver installation...

What have you done to make them work ? What module have you loaded ?

---

### Post by ViGiLnT on 2006-11-16
Still no solution for this problem ?...

---

### Post by cronholio on 2006-11-27
You are not alone. I have sent an email to Realtek requesting investigation of this issue. They provide a driver on their homepage that claims to support the card, but it clearly does not. I'll post here when I get a reply.

---

### Post by cronholio on 2006-11-27
Can you try adding this to /etc/modprobe.d/options and tell me if it works? I don't have access to that laptop right now (might try tomorrow).

```
options snd-hda-intel model=uniwill-m31
```

---

### Post by red_Marvin on 2006-11-27
There is a thread about sound problems on asus laptops [_here_]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2480"). It seems that it should be fixed by now...
How is the laptop in general? Graphic drivers, battery time etc... I haven't found any useful reviews of it :/

---

### Post by navster on 2006-11-27
> **cronholio said:**
> Can you try adding this to /etc/modprobe.d/options and tell me if it works? I don't have access to that laptop right now (might try tomorrow).

```
options snd-hda-intel model=uniwill-m31
```

Hurrar!

I'm using an F3JC & can confirm that, that seemed to do the trick! I got the shock of my life when I rebooted - I stupidly left all the levels up (including the mic) and experienced loud feedback while logging in :rolleyes: 

So make sure your levels are down when you apply this!

Thank you!!!

---

### Post by cronholio on 2006-11-28
> How is the laptop in general? Graphic drivers, battery time etc

I can't say too much, I don't own it myself (it was a friend that had the sound problem). I remember that the NVidia drivers (9626) gave us some trouble. They do work after I install them, but stop working after a reboot. I am sure it's a minor issue. He switched back to the "nv" driver for now.

The maximum resolution of 1280x800 seems a little low for my taste, especially if you like to run Gnome with 2 panels. The quality of the keyboard is pretty bad too, with the keys giving you this "loose" feedback. I can't tell you anything about battery life, this guy runs it on mains all the time.

---

### Post by cronholio on 2006-11-28
I just got an email from Realtek saying that they will update the driver files on their homepage. Kudos to them, I've written to a few companies about Linux issues and usually I don't even get a reply.

---

### Post by cronholio on 2006-11-29
Realtek will support the F3JC in their upcoming driver release, modifying the options file will no longer be necessary. For those of you who want to give it a try, I attached the beta version they sent me. It is supposed to work with alsa-drivers 1.0.12 and 1.0.13. Replace the file alsa-kernel/pci/hda/patch_realtek.c with this one (after unzipping it), then compile and install as usual.

Thanks again to the friendly guys at Realtek. =D>

---

### Post by epimer on 2006-11-30
I have an addendum for this thread.

I couldn't get sound working on my Asus F3J either, but this thread was a great help, and manually adding the option mentioned above has the speakers working great now. My problem is that my headphone socket doesn't work. I've checked "alsamixer", and the channel is turned on but won't allow me to increase the value.

Any ideas?

---

### Post by cronholio on 2006-12-01
IIRC there is an option box in the Gnome mixer (maybe also in alsamixer) for manually switching the headphone output on or off.

---

### Post by epimer on 2006-12-01
Right. There is, and it's set to on, but no sound comes from my headphones when they're plugged in. They do mute the speakers, though, and I know it's not faulty headphones.

Stumped!

---

### Post by cronholio on 2006-12-01
Go to preferences in Gnome mixer and see if there are other channels to display. Maybe there is a separate one for the headphone output that isn't shown by default.

---

### Post by ViGiLnT on 2006-12-04
WOW! I've given up hope on this issue, and was waiting for openSUSE, because they are using alsa v.1.0.13 on their upcoming release.

This way, when I get home, I'll try everything that was suggested here. Thanks for the reply.

---

### Post by eggdeng on 2006-12-07
Previous posters have pointed out that the solution to this problem is often as simple as adding a line at the end of /etc/modprobe.d/alsa-base along the lines of

options snd-hda-intel model= xyz

The problem here is that xyz is different for different makes of laptop. For HP laptops, you (usually) need to put 'hp' (no quotes). My LG laptop requires 'lg' (no quotes). Other options I have seen are 'asus', 'w180', 'uniwill' (again, no quotes).

On dapper, you can find one list of possible options in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz. Gunzip it, open with gedit and search for your soundcard chip. Sample entry:

ALC260
	  hp		HP machines
	  fujitsu	Fujitsu S7020

This tells you that if you have an ALC260 chip on a HP laptop, the appropriate value is 'hp'. And so on and so forth.

---

### Post by ViGiLnT on 2006-12-16
Any news on those driver updates from realtek ?

I still got no sound on my F3JC. Mine has the new core 2 duo processor... Maybe the onboard realtek soundcard   is different too...

---

### Post by epimer on 2006-12-30
From following the bug tracker, I've managed to get perfectly working speakers and headphone socket.

First, I started from scratch by following this guide from the [Comprehensive Sound Problems Guide]("http://www.ubuntuforums.org/showthread.php?t=205449"):

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
``` [/SIZE][SIZE=2]
(2) Reinstall those same packages[/SIZE][SIZE=2]
```
sudo apt-get install linux-sound-base alsa-base alsa-utils 
``` [/SIZE]
[LIST]
[SIZE=2]**VERY IMPORTANT NOTE: **Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following[/SIZE]
[SIZE=2]```
sudo apt-get install gdm ubuntu-desktop
``` [/SIZE]
[SIZE=2](3) Reboot[/SIZE][/LEFT]
[/LEFT]
[*][LEFT][LEFT] [SIZE=2]**VERY IMPORTANT NOTE: **Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the [/SIZE][SIZE=2]linux-sound-base[/SIZE][SIZE=2] packages. If this happens, then do the following[/SIZE]
[SIZE=2]```
sudo apt-get install gdm xubuntu-desktop
``` [/SIZE]
[SIZE=2](3) Reboot[/SIZE]

Then, following the [HdaIntelSoundHowTo]("https://help.ubuntu.com/community/HdaIntelSoundHowto"),  I installed the [latest SVN version]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/") of alsa-driver, library, utils, and oss. Since I did this, there's been a new development release at [alsa-project]("http://www.alsa-project.org/"), so I assume those will work, but **I've not tried those** yet.

After that lot, I edited /etc/modprobe.d/options and added the line:

```
options snd-hda-intel model=asus-laptop
```

Saved, closed, rebooted, and bam! Working speakers and headphones.

---

### Post by ViGiLnT on 2007-01-05
I just want to say THANK YOU to the alsa developers!

I've just installed Ubuntu Edgy again, compiled alsa-driver, alsa-utils and alsa-libs 1.0.14 rc1, and the sound was working!!

Speakers and headphones, without having to do another thing. I didn't even had to edit the /etc/modprobe.d/option file!

Thanks for all your help guys, I knew that sooner or later sound would be working on my laptop!

---

### Post by eggdeng on 2007-01-06
OK! Either of you guys able to record sound? If so, using external/internal mike & which app(s)?

---

### Post by ViGiLnT on 2007-01-08
Haven't tried it yet....

Don't even know if the built-in mic is working...

How can I test it ?

---

### Post by eggdeng on 2007-01-08
Applications -> Sound and video -> Sound Recorder

---

### Post by ViGiLnT on 2007-01-08
I'm using kubuntu... :\

---

### Post by epimer on 2007-01-09
No, no sound recording here. But I'm still on the old 0.13 SVN build from a while back.

When I get a minute (in the middle of exams at the moment), I'll update to 0.14rc and give it another shot.

---

### Post by tomane on 2007-02-22
I tried kubuntu feisty, it brings alsa 0.13, and now sound behaves the oposite way. I only get sound on the *speakers* when my headphone jack is *plugged in*. Weird, to say the least :D
Has anyone testing feisty found a workaround for this?

cheers,
--to

---

### Post by tomane on 2007-02-24
I filed a bug in launchpad, you can check it [here]("https://launchpad.net/ubuntu/+source/alsa-driver/+bug/87195"), and add any additional info that you may have.

cheers,
--to

---

### Post by amaan on 2007-02-24
i tried alsa driver 1.0.14rc2 and the sound isn't working...and when i try to add that line, i can't edit the file (apparently i don't have the permission plus it's a read-only file)

---

### Post by cronholio on 2007-02-24
You have to edit the file with root provileges. Type in a terminal: ```
sudo gedit <filename>
```

---

### Post by amaan on 2007-02-24
still didn't work for my asus w7j after editing that options file, can anyone help? i'm in dire need of some sound :(

thanks in advance

---

### Post by cronholio on 2007-02-25
For the W7J you will need "3stack" as option instead of "asus-laptop". Reported [here.]("http://forum.notebookreview.com/showthread.php?t=63089")

---

### Post by tomane on 2007-03-02
I just finished a fresh install of feisty herd 5 and the problem seems to be solved.
:popcorn::guitar:\\:D/

cheers,
--to

---

### Post by tomane on 2007-03-05
Well, I said, "seems"....
I have sound on the HP once I plug them in, but the main speakers still don't mute. I already tried the model=asus/uniwill-m31/asus-laptop with no avail...


cheers,
--to

---

### Post by djscurippio on 2007-05-01
Audio now working well with Feisty stable.

---

### Post by SikEnCide on 2007-05-03
i had sound on dapper... as well with edgy and it all works fine now with feisty. i have the same laptop the asus fj3c

---

### Post by jackpennello on 2007-07-08
sikencide cna you please contact me??

I have ASUS F3JC MB model  (PRO31J in Italy), and I have some problem with my audio system. 
I heard sound from main speaker, also with the headphone jack inserted, and from control audio in the tray on the top, control the audio only with PCM device.
And the key Fn+F10/F11/F12 doesn't work for me.
Can anyone help me??

my email/msn contact is [email]jackpennello@hotmail.com[/email]

thanks in advance to everybody

---

