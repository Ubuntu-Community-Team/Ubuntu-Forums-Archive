---
title: "no sound after upgrading to 9.10"
date: 2009-10-29
forum: Hardware
---

### Post by Rainbowsix on 2009-10-29
There was no sound driver detected after I upgraded to 9.10. I use integrated sound. I have no idea where to start.

---

### Post by dupper on 2009-10-29
same here. had no time to look around, is this common?

---

### Post by zelhar on 2009-10-29
My sound is gone too. Actually I heard the startup tune when first logged in but there is no sound in videos.

---

### Post by drake888 on 2009-10-29
Same problem. Doesn't even see my audio hardware.

---

### Post by poebae on 2009-10-29
The same thing happened to me, and I'm sad to say that the only fix that worked for me (not that I really tried much else) was a fresh install.

---

### Post by Bernardobr on 2009-10-29
Another one for the group! Sound was just fine at 9.04, now broken at 9.10

---

### Post by boro_ on 2009-10-29
Me too. Integrated Realtek AC97 on Gigabyte K8NF9. On 9.04 works fine, after update to 9.10 no audio hardware found:(

---

### Post by peterjakey on 2009-10-29
sound worked fine in 9.04 now broken in 9.10. No device is listed under Hardware in Sound preferences.....disappointed =(

---

### Post by L33tN1nj4 on 2009-10-29
I had this problem with a wubi install to 9.04 then upgraded it to 9.10 i fixed it by downloading an update from the sudo apt-get update command but it must have been a fix that the Ubuntu dev's did not sure i guess just cross your fingers and hope for a fix soon.

---

### Post by Xelfox on 2009-10-29
Hm just a suggestion but I had this problem and I found that I hadn't added my sound driver on to the list of activated drivers to check them go System>Admin>Hardware Drivers try enabling the sound driver.

Just a guess but hope it helps

---

### Post by shwack on 2009-10-29
Same here - SB Audigy 2 worked fine in 9.04 can't get anything after upgrade.  Frustrated.

---

### Post by Kuppster on 2009-10-29
> **peterjakey said:**
> sound worked fine in 9.04 now broken in 9.10. No device is listed under Hardware in Sound preferences.....disappointed =(


Same exact problem :(  this sucks!

---

### Post by InsomniacUK on 2009-10-29
Another one for the list. Sound was working fine in 9.10 beta, but after a clean install of the full release of 9.10 today, no sound at all. The speakers on the laptop will, on occasion, make a popping sound, but nothing more than that.

No drivers are showing up in the hardware drivers menu, but like I said, all worked fine in 9.10 beta.

Sucks. :(

---

### Post by shwack on 2009-10-29
My sound is now working perfectly:


I hope this works for you...

1.) Go to System - Preferences - Sound
2.) Go to the Hardware Tab   -  Make sure you select the correct option - Mine had been switched to my USB audio device
3.)Select the appropriate sound output.
   Note for people with 5.1 speakers - My audio sounded fine with Stereo Duplex and 4.0, but REALLY shitty on 5.1 with stereo input.   If you go to the next tab with the speaker levels, try raising your subwoofer volume,  as this fixed the static and my 5.1 is now perfect.

Edit:   You may need to disable the other device... that or make sure both aren't analog stereo output.

Good Luck

---

### Post by Kuppster on 2009-10-29
> **shwack said:**
> My sound is now working perfectly:


I hope this works for you...

1.) Go to System - Preferences - Sound
2.) Go to the Hardware Tab   -  Make sure you select the correct option - Mine had been switched to my USB audio device
3.)Select the appropriate sound output.
   Note for people with 5.1 speakers - My audio sounded fine with Stereo Duplex and 4.0, but REALLY shitty on 5.1 with stereo input.   If you go to the next tab with the speaker levels, try raising your subwoofer volume,  as this fixed the static and my 5.1 is now perfect.

Good Luck


I went to the hardware tab and nothing even shows up.

---

### Post by TheForumTroll on 2009-10-29
If you upgraded did you keep the old menu.lst when asked (and is now running an old kernel)? I didn't notice I had chosen an old kernel as default by mistake after I upgraded and my sound was gone too. Changing to the correct kernel fixed the problem.

---

### Post by shwack on 2009-10-29
> **Kuppster said:**
> I went to the hardware tab and nothing even shows up.

Damn - That really sucks - sorry man.

---

### Post by josatchell on 2009-10-29
Earlier, I did a fresh install of 9.10 on a Compaq desktop, and there was no sound regardless of what changes I made in the Sound Preferences app, but then  I fumbled around with /usr/bin/alsamixer and hit some setting by chance that left the speakers working.  Now, I just completed an upgrade on an HP dv3 laptop but no amount of tinkering with alsamixer or the Sound Preferences app has gotten any sound from the speakers.  The sound modules are there (see module list below).  Anyone have any ideas?

# lsmod
Module                  Size  Used by
michael_mic             2204  8 
arc4                    1660  4 
ecb                     2524  4 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  3 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq_dummy           2656  0 
snd_hwdep               7200  1 snd_hda_codec
snd_seq_oss            28576  0 
snd_pcm_oss            37920  0 
snd_seq_midi            6432  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
uvcvideo               59080  0 
joydev                 10272  0 
lib80211_crypt_tkip     8636  0 
iptable_filter          3100  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              22276  2 snd_seq,snd_pcm
psmouse                56180  0 
hp_accel               11228  0 
lis3lv02d               7452  1 hp_accel
wl                   1272936  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
ip_tables              11692  1 iptable_filter
shpchp                 32272  0 
snd                    59204  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq,snd_pcm,snd_seq_device,snd_timer
lp                      8964  0 
input_polldev           3716  1 lis3lv02d
serio_raw               5280  0 
i2c_piix4               9932  0 
soundcore               7264  1 snd
lirc_ene0100            8096  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lib80211                6432  2 lib80211_crypt_tkip,wl
x_tables               16544  1 ip_tables
lirc_dev               10804  1 lirc_ene0100
parport                35340  2 ppdev,lp
led_class               4096  1 hp_accel
usbhid                 38208  0 
usb_storage            52544  0 
r8169                  32064  0 
mii                     5212  1 r8169
video                  19380  0 
output                  2780  1 video
radeon                636000  1 
ttm                    36212  1 radeon
drm                   159584  3 radeon,ttm
agpgart                34988  2 ttm,drm
i2c_algo_bit            5760  1 radeon

---

### Post by Kuppster on 2009-10-30
> **TheForumTroll said:**
> If you upgraded did you keep the old menu.lst when asked (and is now running an old kernel)? I didn't notice I had chosen an old kernel as default by mistake after I upgraded and my sound was gone too. Changing to the correct kernel fixed the problem.

Yea I kept the same menu.lst because I was thinking that it would mess with grup. How can I fix this?

---

### Post by TheForumTroll on 2009-10-30
```
sudo update-grub
```

should fix it :)

---

### Post by Kuppster on 2009-10-30
I ran sudo update-grub and this is what it sit out at me. is 2.6.31-14 the new kernal?


Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by TheForumTroll on 2009-10-30
Yes that is it :)

---

### Post by josatchell on 2009-10-30
I found the solution to my HP dv3 laptop sound issue:

[http://ubuntuforums.org/showthread.php?t=1258788](http://ubuntuforums.org/showthread.php?t=1258788)

Specifically, adding the line:
options snd-hda-intel model=hp-m4 enable_msi=1
to the file below and rebooting:
/etc/modprobe.d/alsa-base.conf

---

### Post by Kuppster on 2009-10-30
Alright, I just rebooted and the old kernal is still the one getting loaded. Eariler today I was in the menu.lst changing the name to Karmic Koala. I dont know I i messed that up by doing that. 

I changed the first title from Jaunty to Karmic Koala. thats it. 

Heres what is in my menu.lst


title        Ubuntu 9.10*** Karmic Koala***, kernel 2.6.28-13-generic
uuid        19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-12-generic
uuid        19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-12-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-12-generic (recovery mode)
uuid        19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro  single
initrd        /boot/initrd.img-2.6.28-12-generic

title        Ubuntu 9.04, memtest86+
uuid        19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional CRAP!!!
root        (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by TheForumTroll on 2009-10-30
Are you sure it is still the old kernel after reboot? You can tell with:
```
uname -r 
```

Actually the new grub don't use the /boot/grub/menu.lst but instead files in /etc/grub.d/ to setup the list. How it does when running a dist upgrade i have no idea though.

---

### Post by Kuppster on 2009-10-30
> **TheForumTroll said:**
> Are you sure it is still the old kernel after reboot? You can tell with:
```
uname -r 
```Actually the new grub don't use the /boot/grub/menu.lst but instead files in /etc/grub.d/ to setup the list. How it does when running a dist upgrade i have no idea though.


yup

2.6.28-13-generic

could you tell me what to do next?

---

### Post by TheForumTroll on 2009-10-30
Hmm. What version does grub show in Synaptic? 0.97 or 1.97? I was thinking that I don't know if a upgrade actually installs the new grub at all.

---

### Post by scout4536 on 2009-10-30
My Dell Mini 10, not the 10v, loses sound if I do a reboot.  But if I shutdown completely and boot up again I have sound....weird.  But all in all I love 9.10, it's great.

---

### Post by Kuppster on 2009-10-30
> **TheForumTroll said:**
> Hmm. What version does grub show in Synaptic? 0.97 or 1.97? I was thinking that I don't know if a upgrade actually installs the new grub at all.


it says .97

I also see a grub-pc with 1.97 but those are not installed. Should i just mark all those for installation? all the ones that have the lastest version 1.97?

---

### Post by TheForumTroll on 2009-10-30
Ok it seems upgrading does not install the new grub then. Then you need to update your menu.lst (I don't know why update-grub didn't do it for you) or change to the new grub. I would advice you not to play around with it without advice from someone who know more about it than me unless you feel confident you know how to recover with a live cd. 

That being said here is what I would do. Look in /boot for the newest kernel. Like "vmlinuz-2.6.31-14-generic". Then add it to the menu.lst like this: (Change the X's to fit what you found)

```

title Ubuntu 9.10 Karmic Koala, kernel 2.6.XX-XX-generic
uuid 19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel /boot/vmlinuz-2.6.XX-XX-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic
quiet

title Ubuntu 9.04, kernel 2.6.XX-XX-generic (recovery mode)
uuid 19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro single
initrd /boot/initrd.img-2.6.XX-XX-generic


```

---

### Post by cuyo01 on 2009-10-30
I too upgraded from kubuntu 9.04 to 9.10 and the sound is broken, but somehow manage to make it work again.

first installed pulseaudio driver since seems is not instaled, it not solved the problem, then deleted the ~/.pulse-cookie file and dont work either, the run pulseaudio from terminal and it loads, pop a message that kubuntu can forget hda sound output then clicked yes and in kmix the sound drop to 0, when i changed the sound to 100 i can heard the sound, then restarted and again no sound, then run sudo alsa force-reload and the kmix tray dissapeared but then i get alsa sound output also same popup saying to forget old hda drivers blah blah blah, clicked on yes and restarted, again no sound, then renamed /etc/modprob.d/alsa-base.conf to alsa-base.conf.back, and restarted, now i get no sound and a popup saying no alsa output changing to pulseaudio but again no audio, then restarted and in kmix selected mixer then channel select and selected "IEC958" "IEC958 Default PCM" and "IEC956 Playback Source" one of them was at volume 0 and i changed it to 100 then restart, again no sound then restarted and enter the BIOS and disabled the onboard sound the restart, ovbius no sound but the popup saying to forget all hda drivers clicked yes then restarted; no sound but somthing changed a icon in the tray appeared briefelly saying "rosolving dependencies" then again restarted the PC two more times before changing again the BIOS to enable onboard sound; When i restarted this time i get the sound with no problems, no popups, no nothing.

to test the audio used smplayer.
my mobo is a ECS GF8200 BE

hope this could be a hint at how to solve the problem.

Will be testing restarting the PC several times.

Edit: Restarted the Pc 10 times and no problems with the sound so far; also the alsa-base.conf files has not been recreated.

sorry for the bad english

---

### Post by etal2 on 2009-10-30
Has somewhat similar experience to cuyo. After upgrade I had no sound, the volume icon did not appear in the taskbar and System > Preferences > Sound would not open.

There are several things to do, first right click on the System menu and select Edit Menus, add the Multimedia Systems Selector to the System > Preferences menu. Now open the Multimedia Systems Selector and see if you can play the test sound through the different systems. 

There are two systems that must work in order for Ubuntu to play sound, Alsa and PulseAudio.

To fix alsa problems follow this guide: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

To fix pulseaudio problems follow this guide: 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I had to use both in order to get things working properly.

---

### Post by boro_ on 2009-10-30
> **TheForumTroll said:**
> Ok it seems upgrading does not install the new grub then. Then you need to update your menu.lst (I don't know why update-grub didn't do it for you) or change to the new grub. I would advice you not to play around with it without advice from someone who know more about it than me unless you feel confident you know how to recover with a live cd. 

That being said here is what I would do. Look in /boot for the newest kernel. Like "vmlinuz-2.6.31-14-generic". Then add it to the menu.lst like this: (Change the X's to fit what you found)

```

title Ubuntu 9.10 Karmic Koala, kernel 2.6.XX-XX-generic
uuid 19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel /boot/vmlinuz-2.6.XX-XX-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic
quiet

title Ubuntu 9.04, kernel 2.6.XX-XX-generic (recovery mode)
uuid 19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro single
initrd /boot/initrd.img-2.6.XX-XX-generic


```

After doing this sounds working:p Thanks a lot

---

### Post by zelhar on 2009-10-30
I just have an update that I have sound working now.

I oppenned mixer and unmuted "Internal Audio Analog Atereo (PulseAudio Mixer)"

This option is inaccessible from the normal kubuntu kmix so I used the ubuntu mixer. 

But I did notice one problem- I have this noise coming out of my speakers, even though I muted all the microphones. It is barely noticeable but still I wonder is this normal ?

---

### Post by Kuppster on 2009-10-30
> **TheForumTroll said:**
> Ok it seems upgrading does not install the new grub then. Then you need to update your menu.lst (I don't know why update-grub didn't do it for you) or change to the new grub. I would advice you not to play around with it without advice from someone who know more about it than me unless you feel confident you know how to recover with a live cd. 

That being said here is what I would do. Look in /boot for the newest kernel. Like "vmlinuz-2.6.31-14-generic". Then add it to the menu.lst like this: (Change the X's to fit what you found)

```

title Ubuntu 9.10 Karmic Koala, kernel 2.6.XX-XX-generic
uuid 19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel /boot/vmlinuz-2.6.XX-XX-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic
quiet

title Ubuntu 9.04, kernel 2.6.XX-XX-generic (recovery mode)
uuid 19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro single
initrd /boot/initrd.img-2.6.XX-XX-generic


```


Thanks! the sound works now! the only thing is that it spits out a bunch of errors when booting up and then it load the os so fast i cant read them.

---

### Post by crazedgremlin on 2009-10-30
What I did to fix it is I installed grub2 with ```
sudo apt-get install grub2
``` and took all the default options.  Grub2 lets you try it before you buy it, so to speak, with a testing option that chainloads from your existing menu.lst.

---

### Post by Kuppster on 2009-10-30
so if I do that it should fix my problem with the errors at start up and install grub 2?  Im in class right now but im going to do it right when I get home.

---

### Post by Bernardobr on 2009-10-30
hi guys,
after upgrading to grub 2 the problem was fixed

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2), check section**Installing (Ubuntu 9.04+)**

---

### Post by vex21 on 2009-10-30
Hi everyone,

I also experienced a sound related issue after having upgraded to 9.10 from 9.04 today. I was quite desperate because when I went to System -> Prefs -> Sound and then to the Hardware tab, there was no sound device listed. It was only after I'd tried many various suggestions in all possible ALSA related threads that I noticed the previous kernel from Jaunty was loaded instead of the new Koala one. I must have messed something up during the upgrade process, I guess, so shame on me. Anyway, here's what I did, hope it might help someone

1. check if this is the same problem I had:
```
dpkg --get-selections | grep linux-image
```shows the list of the installed versions. The most up-to-date was linux-image-2.6.31-14-generic but when I ran this command
```
uname -r
```it showed that I had older version 2.6.28-11 loaded in the system. 

2. remedy - quite easy now that you know what is wrong
edit the grub menu file (as always backing the file first by copying it somewhere else is a good idea):
```
sudo vim /boot/grub/menu.lst
```the important part in my file looked like this
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e5985ea6-bb13-40ac-b9d1-470e13278691
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e5985ea6-bb13-40ac-b9d1-470e13278691 ro quiet 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e5985ea6-bb13-40ac-b9d1-470e13278691
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e5985ea6-bb13-40ac-b9d1-470e13278691 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e5985ea6-bb13-40ac-b9d1-470e13278691
kernel        /boot/memtest86+.bin
quiet

```and I only copied the first section (which represents the first item in the GRUB menu) and created another one in the first position, only changed the title and the kernel version number where needed. 
```

 title           Ubuntu 9.10, kernel 2.6.31-14-generic
 uuid            e5985ea6-bb13-40ac-b9d1-470e13278691
 kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=e5985ea6-bb13-40ac-b9d1-470e13278691 ro quiet
 initrd          /boot/initrd.img-2.6.31-14-generic
 quiet
 
 title           Ubuntu 9.04, kernel 2.6.28-11-generic
 uuid            e5985ea6-bb13-40ac-b9d1-470e13278691
 kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=e5985ea6-bb13-40ac-b9d1-470e13278691 ro quiet
 initrd          /boot/initrd.img-2.6.28-11-generic
 quiet
 
 title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
 uuid            e5985ea6-bb13-40ac-b9d1-470e13278691
 kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=e5985ea6-bb13-40ac-b9d1-470e13278691 ro  single
 initrd          /boot/initrd.img-2.6.28-11-generic
 
 title           Ubuntu 9.04, memtest86+
 uuid            e5985ea6-bb13-40ac-b9d1-470e13278691
 kernel          /boot/memtest86+.bin
 quiet
  
```then I saved the file, rebooted and hooray - sound was working perfectly. You may want to polish the GRUB menu further,  this is the gist of it that worked for me.

Cheers

---

### Post by peterjakey on 2009-10-30
Hi 

My sound is working now im loading the new kernel. If you find that 'sudo update-grub' doesn't work, rename menu.lst to something else (/boot/grub/menu.lst) then run 'sudo update-grub' again, it will tell you it cant find a menu.lst file and will rebuild one with the new kernel

Also, There is a nice simple gui tool for managing grub in System-->Administration-->StartUp-Manager

---

### Post by emptymind on 2009-10-30
I installed grub2, which replaces the older grub. During the installation process, I chose to let the script upgrade my /boot/menu.lst to the new version.

Before I rebooted, I checked to see if it has changed to the newer kernel version. It did.

I rebooted and sound is back. :D

---

### Post by dvannatter on 2009-10-30
I have the same issue. The only driver listed in the "Hardware Drivers" is a software modem driver that is already installed.

---

### Post by Morganza on 2009-10-30
Try boot whith old kernel

or see the link:

[http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/)

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

---

### Post by dvannatter on 2009-10-30
installing grub2 fixed the issues for me as well.

---

### Post by egroeg85 on 2009-10-31
> **etal2 said:**
> 
There are two systems that must work in order for Ubuntu to play sound, Alsa and PulseAudio.

To fix alsa problems follow this guide: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

To fix pulseaudio problems follow this guide: 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I had to use both in order to get things working properly.

I had to fix grub first so that any sound card was detected at all.  But the sound was full of static so I ran these to fix that.  I think I might have been able to get by with only the pulseaudio one, but I ran them both.

It would be nice if the upgrading process could react more dynamically to individual settings.  I know grub has that experimental 3-way merge, but I'm afraid to use it since last time I tried it it crashed on me.  

Thanks to everyone here for all the help once again.  As always, one of my favorite things about open source is the great community support.

---

### Post by _rex on 2009-10-31
upgrading grub, no effect.
checked kernel, updated already.
upgraded/tinkered around with ALSA... and got sound. BUT nothing from online sources- youtube, pandora, etc freezing up, won't give video either. this may not belong in the thread anymore, but i'm hoping i can get some help. thanks

edit: fixed video/loading issues...my mistake for using gnash. however, sound from firefox still silent. i suspect something from pulseaudio but after trying to upgrade, reinstall, i'm at a loss.

---

### Post by prj44 on 2009-10-31
Audigy 2 that worked fine with 9.04.  Correct kernal is loading, so not a grub problem.  Sound card is properly identified.

No sounds.

---

### Post by TheForumTroll on 2009-10-31
Great it worked for some with the grub fix :D

Before installing the new grub I would advise you to search launchpad if you dual boot. Some are experiencing grub load times of 1-3 minutes. My grub menu takes ~½-1 minutes to load. It seems it is a problem only when grub is not on the first device. As Windows deletes grub if installed on the device it is on many have Windows on the first device and then selects another device to boot first after a Windows install. That would trigger the slow grub load :(

---

### Post by sevenfloorsdown on 2009-10-31
Just in case your case is similar to mine. My system had sound problems with 8.10 and 9.04 before which required reinstalling both also and pulseaudio. (You can look up sound problems with acer aspire 6935g for context).

Upon installing 9.10 fresh, except for /home (I keep my /home so that I don't have to reconfigure everything). Then I noticed I had no sound. I tried creating another user profile and when I logged into that, there was sound. I went back to my own profile, there was no sound. I looked at the pulseaudio manager and the level meter was pulsing to the sound file I was playing even though I wasn't hearing anything

I figured my previous settings from 9.04 for pulseaudio or alsa was mucking my sound. So, I looked at /home and looked for also or pulseaudio related files that still had dates prior to my 9.10 install and removed them. I also went in .pulse and removed files dated older than the date of install. If you're gonna do this though, you can back up your files first, to be safe.

That fixed my sound.

---

### Post by alonc on 2009-10-31
I fixed it by editing the default.pa file.
[http://ubuntuforums.org/showthread.php?p=8204714&posted=1#post8204714](http://ubuntuforums.org/showthread.php?p=8204714&posted=1#post8204714)

---

### Post by BOZG on 2009-10-31
> **zelhar said:**
> My sound is gone too. Actually I heard the startup tune when first logged in but there is no sound in videos.


Had the same problem in Kubuntu.  Have a quick look at your sound menu. The PCM slider was set to mute on mine which meant video sound was muted.

---

### Post by Logan 1229 on 2009-10-31
> **shwack said:**
> Same here - SB Audigy 2 worked fine in 9.04 can't get anything after upgrade.  Frustrated.

After re-installing fresh, discovered I was missing a driver for my Audigy 4 sound card (drivers for Audigy 2 card are same). Used Synaptic Package Manager to get them.  Then discovered that in 'Sound Preferences', the default setting (under 'Output' tab) was set to my integrated motherboard audio. Switched it to my sound card & had sound back. Note though, that both may integrated audio & the sound card descriptions were the same but were listed separately as two devices.

Lastly, & am I am gloriously happy to say this, my sound quality level increased by 50%!! I was considering going back to Windows to get the sound quality level back but now I don't need to! To all who contributed to this release -- great job & thank you very much!

---

### Post by nelio2k on 2009-11-01
For Dell Mini-9's or A90 uses the following line needs to be added /etc/modprobe.d/alsa-base.conf to fix the sound.

options snd-hda-intel model=dell

After the line is added, then then sound should work after a restart.

---

### Post by cmavr8 on 2009-11-01
I had the same problem, even with the latest kernel.
I just went to synaptic, uninstalled (completely, purged) almost all pulse entries and reinstalled them.

Sound is working now, but no device is listed under hardware, in sound settings.

EDIT: deleted ~/.pulse and restarted pulse, and my sound card is recognized!

---

### Post by vratnica on 2009-11-01
In Alsamixer, Master was set to mute

I tuned it on an that fixed my problem ;-)

---

### Post by ratcheer on 2009-11-01
> **shwack said:**
> Same here - SB Audigy 2 worked fine in 9.04 can't get anything after upgrade.  Frustrated.

Same for me, too. I am still reading through this thread, hoping to find a solution.

Tim

---

### Post by ratcheer on 2009-11-01
> **ratcheer said:**
> Same for me, too. I am still reading through this thread, hoping to find a solution.

Tim

I got mine fixed, but I feel that what I have done is stupid and, I am not at all comfortable that it is correct. I went into the PulseAudio Volume Control app and had to individually select my sound card for each application that needs to play back sound. E.g., so far, I selected it for Firefox (to play sound in Flash videos). Then, thinking the problem was fixed, I tried to play a music CD with VLC and, again, no sound. Going back to the PA Vol Control, there was a new selection for the VLC application and, when I selected my sound card for it, it played, too.

This just doesn't seem right. I never had to do anything like this in Jaunty. Am I going to have to do this individually for every app that needs to play sound?

Tim

---

### Post by Rasheeke on 2009-11-01
I'm not too sure what fixed it.  I reinstalled pulseaudio and alsa following some steps in and around this thread.  

Then, in Sound Preferences I switched profile from 'Analog Stereo Input' to 'Analog Stereo Duplex'.  I made the switch earlier because I couldn't hear my xbox360(line in) unless I did this switch.  Then after a bunch of restarts and reinstalls I switched back to duplex and now everything works.

---

### Post by denisdobrovoda on 2009-11-01
so i have lenovo r500 and i am sick of the sound problems i have all the time.first i had 9.04 and everything was fine, than one day it  randomly stopped playing and i discovered that when i kill and rerun pulseaudio everything goes well. i upgraded to 910 hoping everything will go smoothly now but unfortunately i have no sound at all not even during startup (actually only when I shut the pc down there is a beep). the problem is i have no clue where to start because my soundcard is not recognized at all. in the sound preferences it says dummy output. any ideas? i dont want to do random things so that i dont mess up stuff. i seem to have the .14 kernel. please please help. my sound is driving me crazy i use the pc mainly to listen to and compose music and this is fu***** irritating.

---

### Post by TheForumTroll on 2009-11-01
If you have installed Karmic/9.10 and you haven't got any sound, check if you are running the old Jaunty installed kernel (2.6.**2**x-xx-generic), instead of the new Karmic kernel (2.6.**3**x-xx-generic). At least that is what I got in 64bit Karmic.

Show the running kernel:
```
uname -r
```

If you are running the OLD kernel (like if you updated from Jaunty and said No to updating the menu.lst) you need to update your menu.lst to get the new kernel to show up in the grub menu. There's a number of ways to do this but make sure only to do anything to grub/menu.lst if you you know what you are doing, know how to fix grub if you cannot boot (like using a Live CD) or got someone who knows how to do it handy. _Messing it up can cause your system to stop booting correctly!_ 

Two ways to fix it is running "update-grub" and let it update menu.lst automatically or have a look in /boot and find the new kernel name and add it to menu.lst. It would look something like this:

```

title Ubuntu 9.10 Karmic Koala, kernel 2.6.3x-xx-generic
uuid xxxxxxxx-xxxx-xxxxx-xxxxx-xxxxxx
kernel /boot/vmlinuz-2.6.xx-xx-generic root=UUID=xxxx-xxxxx-xxxxx-xxxxx ro quiet splash
initrd /boot/initrd.img-2.6.3x-xx-generic
quiet

title Ubuntu 9.04, kernel 2.6.XX-XX-generic (recovery)
uuid 19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel /boot/vmlinuz-2.6.xx-xx-generic root=UUID=xxxx-xxxxx-xxxxx-xxxxx  ro single
initrd /boot/initrd.img-2.6.XX-XX-generic
```
Make sure to get the correct filenames from /boot and use whatever UUID/paths is already in there. You can see UUIDs with:
```
sudo blkid
```
If you need more info about fixing Grub there is a good guide [right here]("http://ubuntuforums.org/showthread.php?t=818177").

If you have the new kernel check if your sound is muted:
```
alsamixer
```

and that your soundcard is found:
```
aplay -l
```

or:
```
less /proc/asound/modules
```

or:
```
lspci -v | less
```
The last one will output all PCI devices while the first and the second should output your devices something like this:
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

```
If you are running the new kernel and nothing shows up you properly need to either enable it in your BIOS (if it's integrated in your motherboard) or check if ALSA support it at all. There is a list of supported sound cards [here on the ALSA homepage]("http://www.alsa-project.org/main/index.php/Matrix:Main"). If you a running Ubuntu on a laptop you can have a look [here to see if there is any info on your laptop model]("https://wiki.ubuntu.com/LaptopTestingTeam#Manufacturer%20Sub%20Pages").

---

### Post by astriemer on 2009-11-02
the alsamixer suggestion worked for me. apparently the IEC958 volume control get set to 0 when I upgraded (I had to arrow over to the right quite a way to find it).

thanks!

---

### Post by denisdobrovoda on 2009-11-02
thanks for your help. unfortunately my soundcard was still recognized yesterday in terminal in 9.10 but today even this doesnt work anymore. system cant see it at all no matter which of the commands i tried. do you think it is the bios problem? if so how do i repair it?

---

### Post by UCW181 on 2009-11-02
The upgrade from 9.04 to 9.10 was a breeze!
only problem I had was sound. I had none at all.
I found my solution [here]("http://ubuntuforums.org/showthread.php?p=8218261#post8218261"), posted by TheForumTroll.
Thanks man! your a life saver!

---

### Post by TheForumTroll on 2009-11-03
If it used to work any you didn't change anything in the BIOS i doubt that is the problem. You boot with the new kernel?

---

### Post by gstuart on 2009-11-06
Hi - After upgrading from Ubuntu 9.04 > 9.10 a couple of days ago, my sound (audio) is not working.  My chipset (onboard audio) is Intel, and uses the snd-hda-intel module.

Gnome Alsa Mixer lists "SigmaTel STAC9271D" as the only tab; I have every sound card element there (Master; PCM, etc.) visible, unmuted and set to max volume.  In 9.04 I had more tabs, and I needed IEC958 checked (which I had to do at every boot - annoying) to get sound; none of these check boxes makes any difference (I have all of the IEC958 ones checked - selected - anyway.

I carefully followed these instructions (page 3 of this thread), and everything seems to be  working:

Quote:

There are two systems that must work in order for Ubuntu to play sound, Alsa and PulseAudio.  

To fix alsa problems follow this guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

To fix pulseaudio problems follow this guide:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

(end quote)

i.e.

victoria@victoria:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

victoria@victoria:~$ lspci -v
...
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
...

victoria@victoria:~$ grep 'audio' /etc/group
audio:x:29:pulse,victoria,freevo

victoria@victoria:~$ cat /proc/asound/modules
 0 snd_hda_intel

victoria@victoria:~$ cat .asoundrc
cat: .asoundrc: No such file or directory

victoria@victoria:~$ gedit /etc/modprobe.d/alsa-base
>> opens a blank file

victoria@victoria:~$ gedit /etc/modprobe.d/alsa-base.conf
>> last line is:
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N

Everything also looks right in Pulseaudio (e.g. volume control; I can see that something is playing.

I checked all of the volumes / options in Sound Preferences (the little speaker in the system menubar), Gnome Alsa Mixer, and in a terminal, alsamixer, xfce4-mixer, and xfce4-mixer.  In alsamixer, IEC958 and IEC958 D are at 00 (zero volume; cannot change i.e. increase), and IEC958 P is set to "digital."

My onboard sound is set (enabled) in my BIOS.

I have no "Sound" entry under System > Preferences or Administration, just Volume Control, and Pulseaudio Preferences.  When I use the Control Center to see what Hardware Drivers I have, all I get is a proprietary drivers (NVIDIA) informational / activation window.

The funny thing is that when I am playing songs (Rhythmbox) or watching TV (TV tuner card Hauppauge PVR-500, /dev/video0 via VLC) I can hear the music / voices, just barely, in my speakers.  It's as if everything is working, but there is some switch / volume setting, that is very very low.

Can anyone help?

Thank you so much!

Sincerely, Victoria  :-)

---

### Post by TheForumTroll on 2009-11-06
I don't know what is wrong but it doesn't seem like anything is missing. The "SigmaTel STAC9271D" is listed as card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog].

You didn't change anything when upgrading right? Like the cables? I know it's obvious but I had to ask as it could sound like a line out since it is so low ;)

---

### Post by gstuart on 2009-11-06
Hi - Thanks for your reply. I just upgraded, no harware changes, including cabling.  One thing that I did do during the upgrade (U 9.04 > 9.10) was at each step asked, I kept my original config files, as I wanted to keep/maintain those settings.

Victoria  :-)

---

### Post by gstuart on 2009-11-06
SOLVED:

I uninstalled pulseaudio (including dependent ubuntu-desktop: I was worried about that, as in previous Ubuntu distros it killed my GUI desktop; not a problem here), but no luck.

In frustration, I swapped my speaker cable from one jack to another, and my audio is back.

However, I don't have the multimedia keys working anymore on my Logitech Internet Navigator Keyboard (always *something*!).

If anyone has suggestions, there, that would also be appreciated.

Thanks for the suggestion; it was the cabling, after all.

Victoria  :-)

---

### Post by TheForumTroll on 2009-11-06
If you can hear it playing I have no idea what is wrong unless something is muted. You are running the latest kernel and not the jaunty one right?

You can tell with "uname -r"

Btw. in alsamixer there is green colour around the numbers if they are un-muted. Muted is grey.

---

### Post by TheForumTroll on 2009-11-06
Ah this is what happens when you start posting and doesn't finish it right away ;)

---

### Post by TheForumTroll on 2009-11-06
There's a bug in launchpad with a keyboard like yours:

[https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/46586]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/46586")

Maybe someone there can help you or you might be able to debug the problem with some guidance so someone can fix it :)

---

### Post by gstuart on 2009-11-06
Hi - lol, I guess.  At least I'm (1) actively searching for answers; (2) posting updates.  :-)

I reinstalled pulseaudio, to get my keyboard multimedia key functionality back (vol up / down, play, etc.).

Oddly, the mute button wouldn't work (like before).  I found that if I press the mute button, then quickly press the vol up or down buttons, it mutes (vol up or down to unmute).

Weird, eh?

Victoria  :-)

---

### Post by gstuart on 2009-11-06
Ok, this looks solved, now also:

Solution: I "remapped" / reset my keyboard Mute button function, using gconf:

Applications menu > System Tools > Configuration Editor > apps > gnome_settings_daemon > keybindings > volume_mute (value = XF86AudioMute)

Double-clicked this definition, and deleted this value (hit Enter to leave blank key binding).

Then, double-clicked the volume_mute again (to get a popup window; or simpy click, then click again to edit directly) and added back the  XF86AudioMute value again.

My keyboard mute button now works properly, again!  :-)

---

### Post by rakesh_g on 2009-11-11
This fixed my problem! :


> **vex21 said:**
> hi everyone,

i also experienced a sound related issue after having upgraded to 9.10 from 9.04 today. I was quite desperate because when i went to system -> prefs -> sound and then to the hardware tab, there was no sound device listed. It was only after i'd tried many various suggestions in all possible alsa related threads that i noticed the previous kernel from jaunty was loaded instead of the new koala one. I must have messed something up during the upgrade process, i guess, so shame on me. Anyway, here's what i did, hope it might help someone

1. Check if this is the same problem i had:
```
dpkg --get-selections | grep linux-image
```shows the list of the installed versions. The most up-to-date was linux-image-2.6.31-14-generic but when i ran this command
```
uname -r
```it showed that i had older version 2.6.28-11 loaded in the system. 

2. Remedy - quite easy now that you know what is wrong
edit the grub menu file (as always backing the file first by copying it somewhere else is a good idea):
```
sudo vim /boot/grub/menu.lst
```the important part in my file looked like this
```

title        ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e5985ea6-bb13-40ac-b9d1-470e13278691
kernel        /boot/vmlinuz-2.6.28-11-generic root=uuid=e5985ea6-bb13-40ac-b9d1-470e13278691 ro quiet 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e5985ea6-bb13-40ac-b9d1-470e13278691
kernel        /boot/vmlinuz-2.6.28-11-generic root=uuid=e5985ea6-bb13-40ac-b9d1-470e13278691 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        ubuntu 9.04, memtest86+
uuid        e5985ea6-bb13-40ac-b9d1-470e13278691
kernel        /boot/memtest86+.bin
quiet

```and i only copied the first section (which represents the first item in the grub menu) and created another one in the first position, only changed the title and the kernel version number where needed. 
```

 title           ubuntu 9.10, kernel 2.6.31-14-generic
 uuid            e5985ea6-bb13-40ac-b9d1-470e13278691
 kernel          /boot/vmlinuz-2.6.31-14-generic root=uuid=e5985ea6-bb13-40ac-b9d1-470e13278691 ro quiet
 initrd          /boot/initrd.img-2.6.31-14-generic
 quiet
 
 title           ubuntu 9.04, kernel 2.6.28-11-generic
 uuid            e5985ea6-bb13-40ac-b9d1-470e13278691
 kernel          /boot/vmlinuz-2.6.28-11-generic root=uuid=e5985ea6-bb13-40ac-b9d1-470e13278691 ro quiet
 initrd          /boot/initrd.img-2.6.28-11-generic
 quiet
 
 title           ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
 uuid            e5985ea6-bb13-40ac-b9d1-470e13278691
 kernel          /boot/vmlinuz-2.6.28-11-generic root=uuid=e5985ea6-bb13-40ac-b9d1-470e13278691 ro  single
 initrd          /boot/initrd.img-2.6.28-11-generic
 
 title           ubuntu 9.04, memtest86+
 uuid            e5985ea6-bb13-40ac-b9d1-470e13278691
 kernel          /boot/memtest86+.bin
 quiet
  
```then i saved the file, rebooted and hooray - sound was working perfectly. You may want to polish the grub menu further,  this is the gist of it that worked for me.

Cheers

---

### Post by TheForumTroll on 2009-11-11
As already stated [here]("http://ubuntuforums.org/showpost.php?p=8218261&postcount=60") ;)

---

### Post by Jordanwb on 2009-11-11
> **TheForumTroll said:**
> If you upgraded did you keep the old menu.lst when asked (and is now running an old kernel)? I didn't notice I had chosen an old kernel as default by mistake after I upgraded and my sound was gone too. Changing to the correct kernel fixed the problem.

On a computer I'm using the latest kernel avaailable to 9.04 because the nvidia drivers won't work with the 9.10 kernel.

---

### Post by Kypdurron5 on 2009-11-17
> **TheForumTroll said:**
> Ok it seems upgrading does not install the new grub then. Then you need to update your menu.lst (I don't know why update-grub didn't do it for you) or change to the new grub. I would advice you not to play around with it without advice from someone who know more about it than me unless you feel confident you know how to recover with a live cd. 

That being said here is what I would do. Look in /boot for the newest kernel. Like "vmlinuz-2.6.31-14-generic". Then add it to the menu.lst like this: (Change the X's to fit what you found)

```

title Ubuntu 9.10 Karmic Koala, kernel 2.6.XX-XX-generic
uuid 19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel /boot/vmlinuz-2.6.XX-XX-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro quiet splash
initrd /boot/initrd.img-2.6.28-13-generic
quiet

title Ubuntu 9.04, kernel 2.6.XX-XX-generic (recovery mode)
uuid 19221e56-9d5c-43d9-afe1-81ed29ccb5cb
kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=19221e56-9d5c-43d9-afe1-81ed29ccb5cb ro single
initrd /boot/initrd.img-2.6.XX-XX-generic


```

This solved my problem....  It was loading the old kernel, 2.6.28-15.  The new one is 2.6.31-14.  I had to manually add the entry in the /boot/grub/menu.lst because update-grub FOUND the kernel, but didn't ADD the kernel to the boot list.  Go figure.  And for me also 9.10 didn't update grub, so I'm still using .97.  

It's been just one thing after another with linux, I swear!  I don't know what I'd do without this community :).

---

### Post by w3ath3rman on 2009-11-17
Placing the correct kernel entry into /boot/grub/menu.lst also fixed a non-functioning touchpad on my Compaq.

Many thanks to kypdurron5.

---

### Post by bostonian95 on 2009-11-17
Checked your drivers?

---

### Post by zzexezz on 2009-11-25
This worked for me with an HP-HDX:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)


apt-get install linux-backports-modules-alsa-karmic-generic

Hope this helps

---

### Post by arturic on 2009-11-25
My solution was to turn off a propietary software modem driver, for details please check my post here: [http://ubuntuforums.org/showpost.php?p=8388139&postcount=7]("http://ubuntuforums.org/showpost.php?p=8388139&postcount=7")

Cheers ! ;)

---

### Post by egghead32 on 2010-03-30
I don`t know if this is relevant as I haven`t read all the blog yet, But after going through the various software fixed via the shell terminal, I activated the Gnome ALSA Mixer and found out everything had been bloody muted!!!

Sound is on now TF!!

---

