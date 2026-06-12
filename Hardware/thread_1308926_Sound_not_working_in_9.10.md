---
title: "Sound not working in 9.10"
date: 2009-11-01
forum: Hardware
---

### Post by willro on 2009-11-01
so, i have a Toshiba Satellite A135-S2276. I used jaunty for a while till an update caused the laptop to freeze after boot before login, reinstalling didn't help, but hey Karmic is ourt now. and i love it, boots faster then win 7 and is ready to go. The only problem i'm having with Karmic is that sound is not working. Under the sound properties/output there is only dummy device.

 it sucks to show how good ubuntu is when i can't show youtube videos with sound.

Now i don't know the name of my specific sound card, i can't find it anywhere online lol.

so what can i do to get sound to work?

---

### Post by Tryfon on 2009-11-01
I have the same problem with a Toshiba Satellite A100-003. I think the sound card is an Intel 82801G (ICH7 Family). Help needed urgently!

---

### Post by willro on 2009-11-01
and just to be clear i didn't update directly from jaunty, i had uninstalled it because it was just wasting 20gb of my 60gb HD. and i installed Karmic WUBI. i tried the one 6 page thread about this and it seemed that everyone there was having problems due to the old kernel, i checked and i have the newest one.

---

### Post by TheForumTroll on 2009-11-01
Except for the kernel thing you could have [a look at this]("http://ubuntuforums.org/showthread.php?p=8218261#post8218261").

---

### Post by Arancaytar on 2009-11-01
I have the same problem. I am running on an AMD x86_64 desktop with on-board Nvidia Geforce and "HD 5.1 CH Audio CODEC".

I've had to jump through quite a few hoops to even get grub, X and input devices working, and somewhere along the way I lost sound. I know I had it before I installed the Nvidia driver, because I heard the login screen even though the screen remained blank. Since then, it's apparently stopped working. I can now only find the dummy device.

---

### Post by Luisnux on 2009-11-01
You may want to try using the hardware drivers, that's worked for me in a lot of situations.  you would need to do System->Administration->Hardware Drivers and let it run to see if it can configure it on it's own.  Or you could try updating the system and then running it.  It's worked when I had "new hardware/installation" issues.

---

### Post by Arancaytar on 2009-11-01
Oh hey, I got it to work. It may have been fixed by one of two things.

1.) I booted straight into graphical mode this time. The last session (actually my first session ever on this system) started in single-user mode (root shell), was bootstrapped to the session level with "telinit 3", and the X session was started with startx. Along the way, it's possible PulseAudio didn't get initialized properly (even though it was running). This matches my earlier experience of sound working on the (non-working, but normally booted) login screen.

2.) I installed linux-backports-modules-alsa-karmic-generic.

---

### Post by willro on 2009-11-01
> **TheForumTroll said:**
> 
If you have the new kernel check if your sound is muted:
```
alsamixer
```and that your soundcard is found:
```
aplay -l
```or:
```
less /proc/asound/modules
```or:
```
lspci -v | less
```The last one will output all PCI devices while the first and the second should output your devices something like this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```If you are running the new kernel and nothing shows up you properly need to either enable it in your BIOS (if it's integrated in your motherboard) or check if ALSA support it at all. There is a list of supported sound cards [here on the ALSA homepage]("http://www.alsa-project.org/main/index.php/Matrix:Main"). If you a running Ubuntu on a laptop you can have a look [here to see if there is any info on your laptop model]("https://wiki.ubuntu.com/LaptopTestingTeam#Manufacturer%20Sub%20Pages").

when i do alsamixer, i get
```
no mixer elms found
```

aplay -l gives me
```
**** List of PLAYBACK Hardware Devices ****
```

the less /proc/asound/modules
```
 0 snd_hda_intel
```

for the lspci thing i found
```
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
        Subsystem: Toshiba America Info Systems Device ff00
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

what do i do now?

---

### Post by willro on 2009-11-01
> **Arancaytar said:**
> Oh hey, I got it to work. It may have been fixed by one of two things.

1.) I booted straight into graphical mode this time. The last session (actually my first session ever on this system) started in single-user mode (root shell), was bootstrapped to the session level with "telinit 3", and the X session was started with startx. Along the way, it's possible PulseAudio didn't get initialized properly (even though it was running). This matches my earlier experience of sound working on the (non-working, but normally booted) login screen.

2.) I installed linux-backports-modules-alsa-karmic-generic.
i always boot in graphic mode... i don't know what use sound would be if i just had a terminal up.

and i did a sudo apt-get install linux-backports-modules-alsa-karmic-generic and it downloaded and installed them, and fixxed nothing.

---

### Post by willro on 2009-11-01
> **Luisnux said:**
> You may want to try using the hardware drivers, that's worked for me in a lot of situations.  you would need to do System->Administration->Hardware Drivers and let it run to see if it can configure it on it's own.  Or you could try updating the system and then running it.  It's worked when I had "new hardware/installation" issues.

yeah that was the first thing i did.

---

### Post by TheForumTroll on 2009-11-01
Do you get the same error with "alsamixer -c0" ?

---

### Post by TheForumTroll on 2009-11-02
You could give this a try:

open /etc/modprobe.d/alsa-base.conf and [this list]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt"). This is a list of alsa modules for Intel HD Audio (ICH6, ICH7, ICH8, ICH9, ICH10) and some other chips.

Now you need to find your sound chip on the list. Then add:

```
options snd-hda-intel model=MODEL
```

to the file you opened before. Like this:
```
options snd-hda-intel model=toshiba
```

If you can't find it you could give one of these a try:
```
options snd-hda-intel model=auto

```
```
options snd-hda-intel model=ref
```

Hope it helps.

---

### Post by greeezz on 2009-11-02
my laptop Asus G1S.
I had no problem with sound on UBUNTU 9.04.
Now I installed 9.10 and I don't have any sound.

I can see  my hardware:
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC660-VD Digital [ALC660-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


IF right click on sound icon and choose PREFERENCES i cant see anything in hardware tab.

[[IMG]http://pics.kz/s5/12/32/f1/d4/1232f1d429bb08951115a8a9daf661ed_preview.png[/IMG]]("http://pics.kz/viewfull553354")
   
Please help.

---

### Post by willro on 2009-11-02
ok, so all of a sudden, sound is working. i'm guessing one of the fixxes i tried on the first page did it and didn't take affect for a while. thanks to those that helped!

---

### Post by TheForumTroll on 2009-11-02
Did you install a fresh install or did you upgrade from 9.04 greeezz?

---

### Post by willro on 2009-11-02
it was a fresh install.

---

### Post by greeezz on 2009-11-02
> **TheForumTroll said:**
> Did you install a fresh install or did you upgrade from 9.04 greeezz?


it was fresh install

---

### Post by TheForumTroll on 2009-11-02
Glad it worked out willro :)

---

### Post by TheForumTroll on 2009-11-02
greeezz does "alsamixer -c0" in the console work?

---

### Post by greeezz on 2009-11-02
> **TheForumTroll said:**
> greeezz does "alsamixer -c0" in the console work?


yes it starts this:
[[img]http://pics.kz/s5/7e/f9/d5/05/7ef9d505f32123fac9b0bce2bcd4ca0f_preview.png[/img]](http://pics.kz/viewfull553399)

---

### Post by TheForumTroll on 2009-11-02
Well then at least alsa can see it. On the first screen shot, is anything listed in the Output tab?

---

### Post by greeezz on 2009-11-02
> **TheForumTroll said:**
> Well then at least alsa can see it. On the first screen shot, is anything listed in the Output tab?


yes. 

[[img]http://pics.kz/s1/6b/de/a4/87/6bdea487e67d1ed600a8d391b0b244bd_preview.png[/img]](http://pics.kz/viewfull553422)

---

### Post by TheForumTroll on 2009-11-02
how about if you run:

```
gstreamer-properties
```

---

### Post by greeezz on 2009-11-02
i found that if do:

$ sudo killall pulseaudio
$ sudo alsa force-reload


my sound starts working!!!

do you know how to add this to autostart ?

---

### Post by goldencako on 2009-11-02
greeezz, I had exactly the same problem as you did, and the fix worked for me too. Given the fact that I can get sound from using ALSA on various tests (gstreamer-properties, Amarok audio configs, alsamixer shows things correctly), I'm pretty sure this is a purely PulseAudio problem. Let's hope it gets fixed for good.

Now, the weird thing is, after upgrading, it wasn't working. After fresh installing it did. And the just today it stopped working. Must be a bug!

---

### Post by euroknite on 2009-11-05
The same thing happened to me, i could watch videos and music would play but i wouldn't have sound and the only thin that popped up for output was a "dummy stereo"

Anyways i went to a tech at my university and he told me that my kernel had not updated with the new update so here's how I fixed it along with my touchpad not working

[B]After i fixed it, everything works great.
[/B]

                    So... here's how to do it!

first you will need superuser privileges.

open up your terminal, and type either "sudo bash" or "su"

you will be prompted for your password so just enter it.

Afterwards you will want to navigate to boot/grub

so type

cd /
cd boot/grub

Now type in 

gedit menu.lst

Now this is the GRUB boot list with all your distos and Os's that you see when you start up your computer

add this underneath where it says "end of default options"

[B]title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        6f2f6599-29c9-44d1-9a8c-b504f1b57ba0
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=6f2f6599-29c9-44d1-9a8c-b504f1b57ba0 ro quiet splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet[/B]

Then save, and restart and load up the new kernel

Ubuntu 9.10, kernel 2.6.31-14-generic

And everything should work now!

hope this helps some of you like it did me! cheers :)

---

### Post by Tryfon on 2009-11-05
I am currently using kernel 2.6.31-14-generic but it's not working.

---

### Post by goldencako on 2009-11-07
I had been doing the 'killall pulseaudio' followed by 'sudo alsa force-reload' and it had worked for a while. Finally, one day, it stopped. I thought no further: fresh install. Anyways, in a couple of hours I had everything set up like before, and sound working! Then, after I rebooted for the first time, my sound was set to no volume. This had happened after the first time I rebooted, last time. So, another reboot and voilà, my sound was gone again. Doing the pulseaudio + alsa reload again I got my sound back. Now I'm afraid in the future my sound will vanish again. Any improvements so far?? I'm almost sure this is a Gnome thing, so if I lose my sound again, I'm thinking of going with Xfce or KDE, until 10.04 is out and unbugged.

---

### Post by Marc Di Pinto on 2010-03-09
I did the sudo apt-get install linux-backports-modules-alsa-karmic-generic
and then restarted the computer, and it worked. it seems that you just had to restart it.
I have a Toshiba Satellite A135-S2276

---

