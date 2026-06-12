---
title: "Won't boot after 9.04 --&gt; 9.10 upgrade. Blank screen"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by kwqd on 2009-11-01
I upgraded from 9.04 to 9.10 and now boot to a blank screen. I have a Lenovo G550 that was purchased in August. I loaded 9.04 on it then and have not been having any major problems.

When I boot now, the kernel choices in order are:

9.10 kernel 2.6.31-14-generic
9.10 kernel 2.6.31-14-recovery mode
9.10 kernel 2.6.28-16-generic
9.10 kernel 2.6.28-16-recovery mode
memtest86+

The first two choices boot to a blank screen and I am not able to switch to a console using ctl-alt-f3.

The third choice lets me boot to a desktop, but I have no audio and everything is running extremely (extremely) slowly. Updates to the display are very slow. Output of lsmod at end of post. Looks like I am now booting back to 9.04 from what I have read on the forum. I really want to fix this problem and boot to 9.10, but if I have to boot to the 2.6.28-16-generic kernal in the mean time, I will. I'm taking an on line college course and need audio to do so. :(

Where I am at now is:

I do glimpse an error message about something in /etc/fstab not being mountable during boot, but it goes by too fast to really see it. I looked at /etc/fstab and don't see anything that looks wrong and mount -a does not generate any errors.

I ran grep -i  error * under /var/log and found the following error"

user.log:Oct 29 18:43:02 kwd-laptop pulseaudio[3221]: module-alsa-sink.c: Error 
opening PCM device front:0: Device or resource busy

I have seen some references to pulseaudio problems in posts.

I also puttered through /var/log/messages and nothing screams out at me.

The only driver listed when I check for installed hardware drivers is my Broadcom wireless. 

Thought it was time to ask for insights before proceeding. Any help would be appreciated.

Thanks.

Output of lsmod

Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
i915                   67844  0 
drm                    96424  1 i915
joydev                 18368  0 
snd_hda_intel         435252  0 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
uvcvideo               63368  0 
snd_timer              29704  2 snd_pcm,snd_seq
compat_ioctl32          9344  1 uvcvideo
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
ieee80211_crypt_tkip    16896  0 
psmouse                61972  0 
lp                     17156  0 
video                  25872  0 
wl                   1279944  0 
snd 62756 9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_de vice
videodev               41600  1 uvcvideo
iptable_filter         10752  0 
soundcore              15200  1 snd
v4l1_compat            21764  2 uvcvideo,videodev
serio_raw              13444  0 
output                 11008  1 video
parport                42220  2 ppdev,lp
ip_tables              19600  1 iptable_filter
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
x_tables               23044  1 ip_tables
usbhid                 42336  0 
tg3                   131204  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp

---

### Post by bartvdm75 on 2009-11-01
hey,

i guess i have the same problem...
i upgraded from 9.04 to 9.10..
i have to boot from the third kernel as well..
and all went extremely slow and i had no sound..
the next day i went for a fresh install..
but after the first 'Ubuntu' screen to install all went blank again..
so no install possible..
so now i have the 9.04 again..
i have an Acer Aspire 5783Z laptop with 4Gb DDR3, Intel T4200 processor
an Intel GMA 4500M video and a 15.6" HD LED LCD

i installed 9.10 on an old desktop computer without problems...

can anyone help ??

---

### Post by bartvdm75 on 2009-11-02
who has the same problem ?

---

### Post by vivekanands on 2009-11-02
Me!
Upgraded from 9.04 Kubuntu to 9.10
1> My Laptop config is as under
Thinkpad R52, Intel Pentium M 1.7 Ghz. 512 MB Ram - mostly DDR2, IBM Thinkpad 17" LCD panel with an Intel 915GM/GMS display capable of supporting 1024x768 @ 85 hz.
2> I am not a fundoo user, so please elucidate as much as possible

Also posted here [http://ubuntuforums.org/showthread.php?t=1309354]("http://ubuntuforums.org/showthread.php?t=1309354")


Please help... If I'd known that it'd be like this, I'd never have upgraded... I will die without my ultra-comfortable settings in Kubuntu!

---

### Post by bartvdm75 on 2009-11-02
i know the feeling :(

---

### Post by goldshirt9 on 2009-11-02
me also.
i upgraded ok and today when i go past the grub screen it fails to load .
i get a user name
password 
then a sudo line.
thats all .
all the links i've looked at point to a graphic card. but i havent 1 , only onboard graphics.
i cannot get by the sudo screen no matter what i try..
could it be that i installed compix and screenlets ?

could i go in via xp and remove one of these prog if it is at error

i am dual booting 
xp ok but ubuntu fails.

sod it have installed xp load up screen and formated ubuntu karmic.

may go back to jaunty and wait until koala settles done.

---

### Post by toller on 2009-11-02
Same problem to me! I have an Acer Extensa 5635Z with Intel Graphics Media Accelerator 4500M, 4GB and was running 9.04 in dual boot with Vista. That was going well. 
On 9.04 as host I had the 9.10 beta and RC running in Virtualbox 3.0 without problems. All this encouraged me to upgrade from 9.04 to 9.10 with same result: blank screen. So I tried new installation from the 9.10 installation CD: blank screen. Now I am running 9.04 again.
There was a lot information around about problems with Intel graphics in version 9.04 which should be solved in V. 9.10. For me it seems to be the other way round.
Hope there will be a solution?!:p
Regards from Germany
toller

---

### Post by michillin212 on 2009-11-02
I had with the same problem with my laptop but if you boot up with a live cd you can Back up all your data.  You can probably back up all your programs and things too.  So no worries.  =)

---

### Post by NHElnath on 2009-11-02
How do you backup the data from a Live CD???  I've got the same issue and want to get some data off of the machine, Live CD works fine, but I don't have access to data from old install.

---

### Post by F_C on 2009-11-02
[[IMG]http://brainstorm.ubuntu.com/idea/22223/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22223/)

---

### Post by vivekanands on 2009-11-03
> **goldshirt9 said:**
> me also.
i upgraded ok and today when i go past the grub screen it fails to load .
i get a user name
password 
then a sudo line.
thats all .
all the links i've looked at point to a graphic card. but i havent 1 , only onboard graphics.
i cannot get by the sudo screen no matter what i try..
could it be that i installed compix and screenlets ?

could i go in via xp and remove one of these prog if it is at error

i am dual booting 
xp ok but ubuntu fails.

sod it have installed xp load up screen and formated ubuntu karmic.

may go back to jaunty and wait until koala settles done.

How do you go back to Jaunty, and get back the old settings???
Please enlighten me with the detailed procedure.

Cheers,
Vivek

---

### Post by goldshirt9 on 2009-11-03
well you could reload the xp grub so you can use that system.
then format the hdd partionions.
then reload jaunty via a disc , using the free space.
 the settings you just have to install as normal

---

### Post by vivekanands on 2009-11-03
> **goldshirt9 said:**
> well you could reload the xp grub so you can use that system.
then format the hdd partionions.
then reload jaunty via a disc , using the free space.
 the settings you just have to install as normal

No no... I don't want to reinstall everything, isn't it possible to restore the system to the state prior to the installation?

---

### Post by ggeorgee on 2009-11-03
Same thing happened to me. Toshiba satellite 1105 was working properly with 9.04 and after apt-get dist-upgrade it halts after grub.
I can only boot it in jaunty in the recovery mode. Gnome halts even in 9.04 where i cannot change to console to do anything.

any ideas???

---

### Post by bartvdm75 on 2009-11-03
how will we know when they have a solution for this ?

---

### Post by vivekanands on 2009-11-04
Guess there's no point in irrational hope. It is insanely amazing that Ubuntu provides us a way of upgrading the entire OS, while big brother Gates fleeces us Rs. 12,000 (US$ 220) without even offering a simple download and upgrade facility to!
Will back up all the data from live dvd and go back to the LTS version 8.04 worked really well for me.

Cheers,
Vivek

PS: Jaunty worked fine too, however, I'll don't have it in DVD... So won't go through the trouble of upgrading to it after installing Hardy

---

### Post by dhj1974 on 2009-11-05
For the record I had the same problem with a Compaq 910us laptop.  I had installed 8.04 or 8.10, upgraded on line when 9.04 came out and then when I did an online update to 9.10 this week and got the blank screen after the initial boot up stuff.  

So I downloaded 9.10 iso and burned a CD.  I tried to do a "run from CD" thing and got a blank screen again.  It seems like there's a problem with the video drivers for my laptop (and by the looks of the postings, a lot of others). 

I did try to do an install from the CD with the same blank screen after it went from text to graphical screens.  I did notice the CD stopped moving once the blank screen came up.  

Finally I downloaded the 9.04 iso and burned another CD and installed that.  Unfortunately I blew everything away and started fresh.  It works fine again but I lost a little bit of data and will have to configure some stuff again.  bummer.  I'm afraid to upgrade Ubuntu versions now.

---

### Post by bartvdm75 on 2009-11-05
yeah, i hope that Ubuntu's 10.04 will be better ;)

---

### Post by scottiw2000 on 2009-11-05
There has been discussion of this problem since at least the beta stage here: [https://bugs.launchpad.net/ubuntu/karmic/+source/initramfs-tools/+bug/431812](https://bugs.launchpad.net/ubuntu/karmic/+source/initramfs-tools/+bug/431812). I don't know why it hasn't been fixed yet. It seems to be a problem with Intel integrated graphics chipsets. The irony is that the Intel graphics problems *are* fixed once you get into the desktop. It's strictly a boot problem.

The workaround suggested there is to do the following:
- press esc at the grub boot stage to get the boot options
- press e to edit the boot commands
- select the boot command that starts with "kernel" and press e again
- add the following text to the end of that command: i915.modeset=0 (**edited: I had a typo in the original post**)
- press enter and then press b to boot with the modified grub command

On my hp pavilion dv2000 this worked a couple of times. You can then add the i915-modeset=0 to one of the grub files (as described near the bottom of the launchpad bug discussion) to avoid having to manually change the grub command every time you boot the machine.

Hope this helps! I for one wish that Canonical had waited until this was fixed to push out the final 9.10 release.

---

### Post by pdoes on 2009-11-05
I have had a similar issue, except it wasn't a blank screen, it was the famous flickering screen.

But i also saw problems with my fstab, someting about my swap partition being bad or something.

Try my steps posted here:
[http://ubuntuforums.org/showpost.php?p=8251946&postcount=122](http://ubuntuforums.org/showpost.php?p=8251946&postcount=122)

---

### Post by goldshirt9 on 2009-11-05
it cannot be a graphic card issue only.
my lappy has onboard  graphics .

interesting though i found out after the black screen 
enter user name
enter password
i had a sudo line..

i found out this was at the command line environment. 
all i had to do was type startx to start up the gui .

or press Alt-F7 or Alt-F8.

---

### Post by pdoes on 2009-11-06
It seems gdm doesn't start automatically.

To check if you have the upstart configuration open a terminal
```
initctl list| grep gdm
```

You should see something like:
```
gdm start/running, process 1211
```

If you don't see this, check if you have the job in the right place:
```
ls /etc/init/gdm.conf
```
The file should exist.

---

### Post by scottiw2000 on 2009-11-06
Yeah, there are actually a couple of different bugs here that create blank screens at different stages. The i915.modeset=0 workaround is for a problem related to Intel onboard graphics chipsets (not graphics cards, but the onboard chipsets) where you don't even get to a command prompt. I couldn't use ctrl+alt+f7 or ctrl+alt+f3 because there would be no response. But adding that command to my grub boot options works consistently.

If you're getting a command prompt but not getting past it, then that's a separate bug that is also discussed on launchpad.

---

### Post by CaptainMorganNZ on 2009-11-07
I had the same problem, finally managed to get the problem solved! 

When the GRUB is loading press ESC, then go into the netroot option. 
Type in your username and password.
If you have any fglrx programs installed, remove them via aptitude or apt-get. If you don't, move onto the next step.
Install xserver-xorg-video-ati (sudo apt-get install xserver-xorg-video-ati)

reboot (press b)

Hope that this works for you! I'd already tried adding i915.modeset=0 to the kernal lines in the boot command AND starting "startx" from netroot.

---

### Post by sonnemonster on 2009-11-07
> **scottiw2000 said:**
> There has been discussion of this problem since at least the beta stage here: [https://bugs.launchpad.net/ubuntu/karmic/+source/initramfs-tools/+bug/431812](https://bugs.launchpad.net/ubuntu/karmic/+source/initramfs-tools/+bug/431812). I don't know why it hasn't been fixed yet. It seems to be a problem with Intel integrated graphics chipsets. The irony is that the Intel graphics problems *are* fixed once you get into the desktop. It's strictly a boot problem.

The workaround suggested there is to do the following:
- press esc at the grub boot stage to get the boot options
- press e to edit the boot commands
- select the boot command that starts with "kernel" and press e again
- add the following text to the end of that command: i915.modeset=0 (**edited: I had a typo in the original post**)
- press enter and then press b to boot with the modified grub command

On my hp pavilion dv2000 this worked a couple of times. You can then add the i915-modeset=0 to one of the grub files (as described near the bottom of the launchpad bug discussion) to avoid having to manually change the grub command every time you boot the machine.

Hope this helps! I for one wish that Canonical had waited until this was fixed to push out the final 9.10 release.

Thank you very much, scotti,

i had the same problem on my ASUS K50IJ, but your workaround fixed the problem. Now my Laptop feels incredebly fast and sound is just working perfect! Thank you!

---

### Post by mukul_d on 2009-11-10
I had the same problem on my VirtualBox machine. To fix this I:
[LIST=1]
[*]Pressed escape at the boot screen to get the grub
[*]Selected the "Recovery" mode
[*]Selected Continue to boot normally
[/LIST]
This brought me to a login screen where I logged in with my userid.

I traversed to /etc/X11 and renamed xorg.conf to xorg.conf.corrupt (You can call it anything you want) and rebooted.

The instance booted just fine. I can reproduce the issue by renaming the xorg.conf.corrupt file to xorg.conf.

I know this is not very elegant. But it is a quick and dirty solution.

---

### Post by hokasch on 2009-11-15
Please check this bug report:
[https://bugs.launchpad.net/fedora/+source/linux/+bug/425165](https://bugs.launchpad.net/fedora/+source/linux/+bug/425165)

---

### Post by raikou on 2009-12-22
> **scottiw2000 said:**
> There has been discussion of this problem since at least the beta stage here: [https://bugs.launchpad.net/ubuntu/karmic/+source/initramfs-tools/+bug/431812](https://bugs.launchpad.net/ubuntu/karmic/+source/initramfs-tools/+bug/431812). I don't know why it hasn't been fixed yet. It seems to be a problem with Intel integrated graphics chipsets. The irony is that the Intel graphics problems *are* fixed once you get into the desktop. It's strictly a boot problem.

The workaround suggested there is to do the following:
- press esc at the grub boot stage to get the boot options
- press e to edit the boot commands
- select the boot command that starts with "kernel" and press e again
**[COLOR="DeepSkyBlue"]- add the following text to the end of that command: i915.modeset=0[/COLOR]** (**edited: I had a typo in the original post**)
- press enter and then press b to boot with the modified grub command

On my hp pavilion dv2000 this worked a couple of times. You can then add the i915-modeset=0 to one of the grub files (as described near the bottom of the launchpad bug discussion) to avoid having to manually change the grub command every time you boot the machine.

Hope this helps! I for one wish that Canonical had waited until this was fixed to push out the final 9.10 release.

You sir, are a genius!

Thank you!!!

---

### Post by gnarfle on 2010-01-30
For anyone else, I just picked up a Core i3 Acer laptop and it has this same problem with 9.10. The i915 modeset did fix it (although I had to install in safe mode), however it seems for me at least the splash is what was causing the problem. I edited /etc/default/grub and removed splash from the CRUB_CMDLINE_LINUX_DEFAULT entry, ran update-grub, rebooted and it works now.

Unfortunately I'm stuck at 800x600...

---

### Post by scottiw2000 on 2010-04-20
In case anyone is still struggling with this bug on Karmic, I thought I'd let you know that the problem disappeared when I upgraded to Lucid (10.04) Beta 2. The official Lucid release is only a few days away and so far it seems to be a good step forward as far as handling graphics and boot problems.

---

### Post by Deluxe0427 on 2010-04-30
Ughhh I'm having a similar problem and im a total noob to linux period. Got completely fed up with Wind*** and now im having issues with what i was hoping would be my god sent cure lol. Anyways back to what i was saying. I have ubuntu 9.1 on my desktop and it works like a charm ;). However, I figured I'd try some of the other versions to be fair "Kubuntu v9.1" 10.04 LTS was still in beta when i downloaded. So I installed Kubuntu on my laptop "should i say tank" it's a dell xps m2010, it worked great the first day than the next, it wont startup... i didnt change any settings, i didnt enter the terminal make myself the su or anything of that nature just opened up the os, checked it out got a little feel for it than shut down. Can anyone help me??? I would've posted my own thread but idk how lol like i said im a noob. and i dont really ever use forums or blongs or anything.

---

