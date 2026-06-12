---
title: "3rd attempt at linux in 10 years, fixing bug#1 starts at home, fingers crossed"
date: 2008-08-21
forum: General Help
---

### Post by stg on 2008-08-21
Here goes, spankin' new ubuntu here.  Tried some Mandrake back in the day, then Suze about 3 years ago till I hung on drivers.  My life has been clenched fists wanting to lob mortar shells over the hill into Redmond but simply not having the time to invest in figuring this all out.  A devil's bargain for sure.  The other day my frustration level with MS boiled over and I paved a drive.

Impressive!  Loaded quickly, put itself on the internet, got updates, detected all my hardware (had to enable nonfree driver for Maudio Delta44 soundcard).  Learned how to edit fstab to mount my big NTFS volume with all the MP3s on it at boot.  Really quite nice...which brings us to...well, nice.

So here I am playing audio in rythymbox and browsing in firefox.  If I drag down quickly in a big webpage the audio chunks badly.  System monitor confirms that CPU usage is pegged.  A couple of times I managed to modify rythymbox and pulseaudio's nice# in system monitor/processes and that helped, but the changes do not stick on reboot, annoying.  And sometimes when I click "change priority" system monitor craps all over itself and closes without doing anything.  Ugh.  

I know I'm getting long winded, sorry, I guess my first question is...Is a 1.2GHz P3 with 1.2GB RAM really so modest anymore that one can't play audio and browse at the same time??  Do I need to downgrade?  WTF?

And if so, how do I make nice changes stick (or take at all) as a workaround so I can stand this thing long enough to learn it.

Thanks in advance, I'm ignorant, but not, I think, a total idiot, and I want to try.

---

### Post by unutbu on 2008-08-21
The command
```
nice -n -20 rhythmbox
```
runs rhythmbox with the niceness priority set to -20 (most favorable scheduling).
If you are starting rhythmbox from the menu, then go to System>Preferences>Main Menu, Right-click the rhythmbox item, select Properties, and edit the command to be like the one above.

---

### Post by stg on 2008-08-21
Hey, thanks for the response!!

Tried editing the command in the menu as you suggested, now the app won't start from the menu.

from the command line

stg@gigtower:~$ nice -n -20 rhythmbox
nice: cannot set niceness: Permission denied
stg@gigtower:~$ sudo nice -n -20 rhythmbox
[sudo] password for stg: 

(rhythmbox:6674): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
stg@gigtower:~$ 

and rythymbox will no longer recognize my folders

any ideas??

---

### Post by tuxxy on 2008-08-21
Try adding a SUDO to the start of the command

---

### Post by stg on 2008-08-21
I assume you mean in the menu command, as I had sudoed (is that a word?) from the command line as pasted above.  I tried adding the sudo to the command in the menu, still no start.

Thanks for the suggestion!!

---

### Post by caljohnsmith on 2008-08-21
I think the problem you are experiencing is because to "nice" rhythmbox to -20, you need root privileges; but when you run:
```
sudo nice -n -20 rhythmbox
```
It will also run rhythmbox as root, which is dangerous. I think what you really want to do is grant yourself the privilege to "nice" a process without using sudo. You can do that by opening up:
```
gksudo gedit /etc/security/limits.conf
```
And add the following line at the end:
```
<username>   -  nice   -20
```
Replace <username> with your username. You'll need to either reboot or log out and log back in. Then you can run Rhythmbox with just:
```
nice -n -20 rhythmbox
```

---

### Post by stg on 2008-08-21
BINGO!  THANKS!  by combining these suggestions now rythmbox starts from the menu with a niceness of -20, which helps a lot.  I still have to turn off all visual effects in appearance to avoid chunking when I scroll and my CPU usage always seems really high.  Questions remain...

1. Would it help to set pulseaudio niceness to -19, if so how would I set that to occur on boot?

2. Is there stuff I can disable to free up processor time, Inability to walk and chew gum at the same time is why I paved Win2K in the first place.  I mean, is this right? will a modern OS simply not run right on this box?  It used to do all kinds of stuff at the same time under Win98se but then the drivers started falling off the back of the bus.  I always thought that one of the big advantages of Linux was that it would run well on older boxes.  Is there anything like the -ck patch for Ubuntu?

---

### Post by jerome1232 on 2008-08-21
I would probably go for a Window Manager rather than a Desktop Enviroment like gnome, Your processor is pretty low end, that seems to be the bottleneck of your computer. Something like icewm (what dsl uses), openbox, fluxbox, or xfce would help.

---

### Post by stg on 2008-08-21
Wow, OK, 1.2GHz is low end, thanks.  It's all the mobo will clock at so I guess there I am.  at least I have tunes while I learn about window managers.

---

### Post by wolfen69 on 2008-08-21
try ```
sudo apt-get install xfce4
``` xfce is a lighter weight desktop. then at login (session) you can choose which desktop to boot to. it cant hurt. 

installing xubuntu-desktop (xfce) is probably pointless since you already have a suite of apps.

---

### Post by caljohnsmith on 2008-08-21
Actually, stg, if you watch your CPU carefully when you have problems with sound, you may notice you can still have problems with the sound stuttering even when CPU is < 100%. It has to do with interrupts (IRQs), and not process priority (nice value). For instance, the process priority affects the scheduling, or which processes will get to use the CPU before other processes, but once a process with lower priority gets its turn to use the CPU, it can monopolize the CPU for the duration of its interrupt time. So if that processes' interrupt time is longer than the period your audio player needs to replenish your sound card's audio buffer, you'll still get stuttering sound, since the audio player can't stream more data to the sound card in time. 

The way around that problem is with using a "realtime" enabled kernel, where you can set the "preemption" value for different processes; preemption is what allows a higher priority process to override another process that is hogging the CPU because it has a long interrupt time. At least that's my understanding of it all after having done quite a bit of research on the subject. :)

Unfortunately though, I have found from experience that even though using a realtime-enabled kernel can help alot to mitigate stuttering/choppy sound, still it is not a complete panacea. Some processes, like my wifi card for instance, use proprietary drivers (i.e. ndiswrapper + Windows driver), and their interrupt times seem to be hard-coded and immune to IRQ requests. Just another reason why proprietary software is such a bane for open source software. :roll:

---

### Post by stg on 2008-08-21
WOW! Thanks!!

I will look into this "realtime" enabled kernel thing.  This box's raison d'etre is audio, everything else can wait as far as I'm concerned.  Been running this about 24Hrs now. Skeptical partner was able to surf web and check email no problem, plays audio, plays movies, sees the camera and pulls in the images (which, along with the all of a sudden choppy audio thing, was one of the main triggers that prompted this attempt, some DDE server window hangup) sees memory sticks, cd ripper built in, you folk's help...Microsoft tm products might just be an endangered species around here.

---

### Post by caljohnsmith on 2008-08-21
If you want to give the realtime-enabled kernel a whirl, just download the following packages:
```
sudo apt-get install linux-headers-2.6.24-21-rt linux-image-2.6.24.21-rt linux-restricted-modules-2.6.24-21-rt linux-ubuntu-modules-2.6.24-21-rt
```
Make sure the kernel gets added to your /boot/grub/menu.lst.

But that's actually the easy part. The part that takes a little work is setting up which processes you want to give pre-emption privileges to, such as your sound card and your audio player. If you actually get serious enough to install the realtime kernel and can boot into it OK, I can give you directions of how to do the pre-emption stuff. Just let me know. :)

---

