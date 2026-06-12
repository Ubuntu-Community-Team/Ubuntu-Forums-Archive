---
title: "Help Needed on a lot of stuff!!!"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by r3d33m3r on 2005-05-07
I installed ubuntu for only one reason the Intel Centrino Wireless Connectivity which worked fine. 
Firstly rythmbox and totem movie player dont play any mp3s. i installed xmms and that just got stuck the moment u clicked on play. i had to killl the application to make it work. 

Secondly My Intel Centrino processor supports CPU throttling. I want to use this and the Software suspend option but i have no idea how to go abt it. 

 ](*,) 
cheers 
r3d33m3r

---

### Post by kvidell on 2005-05-07
[QUOTE=r3d33m3r]I installed ubuntu for only one reason the Intel Centrino Wireless Connectivity which worked fine. 
Firstly rythmbox and totem movie player dont play any mp3s. i installed xmms and that just got stuck the moment u clicked on play. i had to killl the application to make it work. 

Secondly My Intel Centrino processor supports CPU throttling. I want to use this and the Software suspend option but i have no idea how to go abt it. 

 ](*,) 
cheers 
r3d33m3r[/QUOTE]
 XMMS might be crashing because something else is using the audio device.
try this to see if anything (namely esd) is doing so:
```
you@yourhost% lsoof | grep dsp
```
When I do it I see this:
```
beep-medi 10765    kvidell    9w      CHR       14,3                7431 /dev/dsp
```because I'm currently using BMP(Beep-Media-Player (A slightly optomized and upgraded XMMS, I recomend it unless you're really in love with XMMS)) to play some MP3s.

If you do get something, try kill'ing the PID (In my case, I'd want to kill 10765), then try playing MP3s in your media player again.

As for Totem and such not playing MP3s, well.. it should, try this:
sudo apt-get install w32codecs
and see if that makes a difference.

As for suspending...
[http://www.ubuntulinux.org/wiki/FrontPage/searchwiki?expr=suspend&submit=Search](http://www.ubuntulinux.org/wiki/FrontPage/searchwiki?expr=suspend&submit=Search)
Have a look through those and see if anything helps you.

I don't know what kind of hardware you're using, but to get my laptop suspend I had to modify the KERNEL line in my /boot/grub/menu.lst
```
title       Ubuntu, kernel 2.6.10-5-386
root        (hd0,0)
kernel      /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash apm=on acpi=off nolapic
initrd      /boot/initrd.img-2.6.10-5-386
savedefault
boot
```is what that section now looks like.

What I added:
```
apm=on acpi=off nolapic
```That allowed me to use my ThinkPad's Fn key-combo (Fn+F4) to send the system in to a software/ram suspend.

I'm not sure about CPU throttling though.
Again, look through this:
[http://www.ubuntulinux.org/wiki/FrontPage/searchwiki?expr=cpu+throttling&submit=Search](http://www.ubuntulinux.org/wiki/FrontPage/searchwiki?expr=cpu+throttling&submit=Search)
and see if anything helps.

Best of luck!
- Kev

---

### Post by Buffalo Soldier on 2005-05-07
[QUOTE=r3d33m3r]Firstly rythmbox and totem movie player dont play any mp3s.[/QUOTE]Try the guide at [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) on how to install additional codecs.

---

### Post by QuantumCowboy on 2005-05-09
XMMS will do that sometimes when you don't have the proper output driver selected.  Try messing with selection of output driver from the preferences menu.  OSS is depreciated but mostly still works, generally ALSA and eSound have worked better for me.  IIRC, alsa does not work until you configure it for the first time:

$: alsamixer
[set some volumes]
$: sudo alsactl store

Also in my experience if you're using KDE you sometimes need to turn off the thing where it hogs the sound card.  In the KDE control center under sounds there should be a slider to select how long KDE should hang onto the sound card after it plays a sound.  This should be reduced to 3 seconds or less.

Old versions of gAIM sometimes hog the card as well.

I hope at least some of this helps.

-QC

---

### Post by mohaham on 2005-05-09
CPU throttling is enabled by default on Centrino Processors in Ubuntu Hoary...

---

### Post by r3d33m3r on 2005-05-09
thanks for all your help. I figured out that the MP3 and other libraries were not installed and did that thru synaptic. I still cant make head or tail of how to get cpu throttling. Rythmbox is now working fine. 
Thanks alot once more
take care
cheers
 O:)

---

### Post by r3d33m3r on 2005-05-09
I forget to mention one more thing. I just wanted to know how to install the kernel source tree for KERNEL version 2.6.10-2-686. thanks.
cheers

---

### Post by kvidell on 2005-05-09
[QUOTE=r3d33m3r]I forget to mention one more thing. I just wanted to know how to install the kernel source tree for KERNEL version 2.6.10-2-686. thanks.
cheers[/QUOTE]
 ```
sudo apt-get install kernel-tree-2.6.10
```
That should do ya :)
- Kev

---

### Post by r3d33m3r on 2005-05-11
[QUOTE=kvidell]```
sudo apt-get install kernel-tree-2.6.10
```
That should do ya :)
- Kev[/QUOTE]
 thanks alot dude.

---

### Post by Zingam on 2005-05-11
[QUOTE=mohaham]CPU throttling is enabled by default on Centrino Processors in Ubuntu Hoary...[/QUOTE]
 What about Mobile Pentium 4?
How can I enable it and how can I see if it works? There is an applet that should display the CPU frequency but it does not show anything.

---

