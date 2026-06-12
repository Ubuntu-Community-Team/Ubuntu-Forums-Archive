---
title: "Dummy output - No Sound Card Detected / snd-hda-intel - (Karmic)"
date: 2009-11-06
forum: Hardware
---

### Post by TacheDeChoco on 2009-11-06
After so many many attempts to solve my audio problems when upgrading to Karmic, I finally found a working solution  :p !

First, let me decribe what the problem was:
1) no audio card was detected at all
=> cat /proc/asound/cards returned an empty content
=> cat /proc/asound/devices did not include any audio devices
=> 'Hardware' tab in sound preferences was empty
2) the audio tray indicated a "dummy output"


SOLUTION
========

For those who do not have a fresh Karmic install (in other words those who have upgraded their Jaunty install), you should update your Grub BEFORE applying the 2 steps described hereunder:

sudo update-grub



**Step1: make the sound card being recognized**

=> _Purge _alsa-base and pulseaudio, eg:

sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] alsa-base
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload


Now, reboot, you shoud now SEE (but maybe not yet hear) your soundcard.
Give a try to:
cat /proc/asound/cards
and see if any card is listed...


**Step2 : If the sound is crapy, you MAY have to edit the alsa config file:**

sudo gedit /etc/modprobe.d/alsa-base.conf

a) comment (#) the following line:
[COLOR=Red]**#**[/COLOR] options snd-hda-intel power_save=10 power_save_controller=N

b) Add a new line
options snd-hda-intel probe_mask=1 model=[COLOR=DarkGreen]**hp**[/COLOR]

Replace "[COLOR=DarkGreen]**hp**[/COLOR]" with appropriate computer model. See [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt")

Good luck !

Bernard.

---

### Post by StudioCascade on 2009-11-07
Thank you for your clear explaination.
I followed the above instructions step by step,
but it didn't solve my "dummy output" problem directly.

But then I figured out that my kernel was incorrect.
So if anyone still keeps having this problem, look if you've got the right kernel.
(there's another topic where this is clearly explained)

---

### Post by sgleo87 on 2009-11-09
I followed all your steps and my card shows up when running cat /proc/asound/cards, but I still had a dummy output in the gnome sound preferences. But after editing /etc/modprobe.d/alsa-base.conf and adding options snd-hda-intel probe_mask=1 model=asus-v1s it finally worked!!! Thanks so much!

---

### Post by linnovice on 2009-11-09
Can any of you guys help me? Im new to linux and I still have no sound on  Jaunty. I love the OS but if I cant get no sound im off back to Windows. Ive left loads of messages for help on here but so far not one reply.

Could someone spare some time to talk me through what to check etc?

Many thanks

---

### Post by Xpire on 2009-11-09
I tried following this guide but it didn't work for me. 

I found this guide, [upgrade-alsa]("http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/") and noticed that it failed when I tried to do 

sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev

while it was trying to look for the drivers for version 16 of the kernel. 

Rebooted back to version 14, and the sound worked!

Is there any way I can get that linux-header installed for version 16?

---

### Post by chayon on 2009-11-10
Hey Bernard!

You are a life saver! :D I followed your instructions and it worked! 

I am using a HP pavillion DV6500, by the way.

- Chayon

---

### Post by joelswanson on 2009-11-10
I have an Intel sound card and was having trouble getting the sound to work.  My card had been detected, but I was still having problems.  Removing and reinstalling alsa and pulseaudio worked for me.  So if your having trouble, even if your card is detected, the above instructions could still help.

---

### Post by Surrendermonkey on 2009-11-10
> **sgleo87 said:**
> I followed all your steps and my card shows up when running cat /proc/asound/cards, but I still had a dummy output in the gnome sound preferences. But after editing /etc/modprobe.d/alsa-base.conf and adding options snd-hda-intel probe_mask=1 model=asus-v1s it finally worked!!! Thanks so much!

The exact same happened here, the card showed up but was still dummy output, editing /etc/modprobe.d/alsa-base.conf did the trick for me.

---

### Post by M03BIUS on 2009-11-10
I've tried everything on this thread and still no luck getting this to make sound...  someone please help.

---

### Post by mammoth23 on 2009-11-11
Thanks for the perfect hint. I followed all your steps even though my sound card was identified from the very first. Nevertheless, I didn't hear anything and only a dummy output showed up in pulseaudio.

My configuration: Acer Travelmate 8100, Soundcard: HDA Intel, Chip: Realtek ALC880.
using **options snd-hda-intel probe_mask=1 model=auto** did the job.

Many thanks!

---

### Post by HuaiDan on 2009-11-13
Bummer

---

### Post by HuaiDan on 2009-11-13
Finally got it, here.s what I had to do:

Purged pulseaudio, didn't reinstall it throughout the whole procedure.

Whenever I force reloaded alsa, I noticed my compositing flickered and my cairo dock did funny things. Digging into that problem revealed that I had the old NVidia driver still trying to load for the old kernel, and my menu.lst wasn't loading the new kernel, which was trying to load the new Linux video driver (phew!)

Edited my menu.lst to load the new kernel, removed new linux video driver, the installed the new NVidia driver from the Nvidia website (190 version). Rebooted. Now I had beautiful compositing, still no sound.

Then I edited /etc/modprobe.d conf files.
Removed the modem blacklist entries there.
Two files there I didn't quite understand: alsa-base-conf and als-base.conf
Made sure these two files had the same content. Not sure if this was necessary, but...
Put this entry into both :
options snd-hda-intel model=3stack 

Completely deleted the power saving entry, because I have had suspicious results before trying to comment out lines in .conf files.


Did a hard reboot, checked system/preferences/multimedia systems selector (you may need to add this to the menu, but it's there), selected ALSA and default for everything (dare not experiment there because...)

Got tone when I tested. Music in Amarok. Finally.


It really sucks having gone through all that. Kind of a psychological mind f*** if you ask me.

---

### Post by bjorn_huang on 2009-11-14
I had the same problem. I used to force reload alsa as described above to get the sound, but today I also found a simpler solution from this post

[https://bugs.launchpad.net/system76/+bug/463874](https://bugs.launchpad.net/system76/+bug/463874)

after removing the software modem driver I finally got the sound back.

---

### Post by tangled on 2009-11-14
> **mammoth23 said:**
> Thanks for the perfect hint. I followed all your steps even though my sound card was identified from the very first. Nevertheless, I didn't hear anything and only a dummy output showed up in pulseaudio.

My configuration: Acer Travelmate 8100, Soundcard: HDA Intel, Chip: Realtek ALC880.
using **options snd-hda-intel probe_mask=1 model=auto** did the job.

Many thanks!

"model=auto" did it! Thanks

---

### Post by HuaiDan on 2009-11-14
Addendum:

Reinstalled Pulseaudio, got my sound controls back.

re-edited my alsa-base.conf and alsa-base-conf to read:

options snd-hda-intel model=6stack-dig

Don't know if that last one made a difference, but that's what I have.

---

### Post by Fo-fo on 2009-11-14
removing software modems from system>hardware drivers worked for me too

---

### Post by HuaiDan on 2009-11-15
Addendum:


Use this webpage to get the model number for the conf files, based on your sound chipset info you get from sudo lspci. That should really narrow the field.

[http://forumubuntusoftware.info/viewtopic.php?f=7&t=3398](http://forumubuntusoftware.info/viewtopic.php?f=7&t=3398)

I then aliased the soundcard paths in alsa-base.conf and alsa-base-conf as follows, and added index=0:
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=6stack-dig index=0



Doing this really fine tuned the audio options. Whereas before I had one default option under sound preferences/hardware/Settings for the selected device:, now I have several for surround, digital, analog, stereo, which upon testing work as intended. Truly functional at this point.

Think I've reached a good stopping point, audio  has been optimized. Thanks to all for contributing their valuable input.

---

### Post by jac0117 on 2009-11-18
> **tangled said:**
> "model=auto" did it! Thanks



Yeah this did it for me too.

---

### Post by ToshibaLaptoplinux on 2009-12-16
Removing software modems fixed it for me too.

---

### Post by rumentab on 2009-12-23
Thank you very much for this solution. I've tried lots of attempts to make my sound work, but this only worked. One more time THANK YOU!!!!

---

### Post by Kallewoof on 2009-12-26
> **tangled said:**
> "model=auto" did it! Thanks

Same here. Thank you muchly!!:D

---

### Post by kurtisnathan on 2010-01-07
I was going crazy thinking I wouldn't find an answer to this problem. Thank you so much! Worked like a charm.

---

### Post by T0rch on 2010-01-08
Thanks very much it works now ;)

---

### Post by la1234uk on 2010-01-15
Exactly same problem to me: upgraded from 9.04, and no sound card in cat /proc/asound/cards. No way to hear any sound. 

I SOLVED it as follows:

INTRO : 

If you upgraded from previous versions, during installation you were asked several questions... if you answer with the DEFAULT to most of them, your GRUB menu list may be the old one !

This means that you are running the old kernel against the new software packages of Karmic Koala... this is presumably the reason of alsa driver messing up.

PROCEDURE :

open two terminal window and place them side to side. 
On the first one type 

ls /boot/ -all

search for the LAST version of the kernel, in my case was
vmlinuz-2.6.31-17-generic

on the other window type 

sudo nano /boot/grub/menu.lst

go down and search for your boot section: it should look something like this:

title           Ubuntu 9.04 
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=922c9$
initrd          /boot/initrd.img-2.6.31-17-generic
quiet

now: the point here are the numbers after vmlinuz. They represent your kernel version. Using the adjacent other terminal window, look at the dates and VERIFY that your current vmlinuz version is actually the last one.

If not EDIT the kernel and initrd lines accordingly. You have just to change the numbers of vmlinuz-2.6.xx-yy-generic and initrd.img-2.6.xx-yy-generic. Make it match the last version you have.

=====================================

After you fix this SAVE and close the file. Then do in terminal:

sudo update-grub

THEN remove all alsa and pulseadio and install them again. To do this go in terminal and do:

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base 
sudo apt-get install pulseaudio

then reset, your sound should be OK now.

This is the way I fixed my system after an update from 9.04 to 9.10. Cross your fingers and everything should work for you too.

Greg Ruo

:popcorn:

---

### Post by wild_ecstasy1985 on 2010-01-17
Thanks a ton! that worked!

Procedure:
1. check the kernel [thanks la1234uk]
2. then continue from sudo update-grub --- [thanks TacheDeChoco]

Note: while editing the alsa-base-conf, model = **auto**  worked for me too [thanks mammoth23]


-- Sagar Hatekar  :D

---

### Post by CRMR on 2010-01-30
Thankx buddy... 
I am using ASUS-F3e notebook. My sound card was detected, but still there is "Dummy output".
It was solved after adding 
   options snd-hda-intel probe_mask=1 model=asus-laptop
               to  /etc/modprobe.d/alsa-base-conf

Thankx a lot buddy... :D :D :D

---

### Post by mpwh on 2010-02-08
THanks a lot!.. works like a charm.. this really helped me out..

---

### Post by jintachi on 2010-02-10
This didn't work for me unfortunately but I did manage to solve my problem. I'm on an Inspiron 1525 my sound card is an Intel Corporation 82801H (ICH8 Family) Sigmatel 9205. I've posted the fix instructions here:

[http://ubuntuforums.org/showpost.php?p=8806349&postcount=12](http://ubuntuforums.org/showpost.php?p=8806349&postcount=12)

---

### Post by clint0n on 2010-02-26
thank you so much worked liked a charm, had black screen when starting up. had to boot into recovery, login, do 'startx' and then follow your guide. thanks again.

---

### Post by netopalis45 on 2010-03-01
i have followed all the steps but am still not able to get any sound. when i run the cat /proc/asound/cards i can see the cards that i have installed but when i try to use sound preferences to set up the cards so i will actually get sound, it says that there are no hardware devices. the same thing happens when i use pulseaudio.

output for cat /proc/asound/cards
0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xcca0 irq 18
 1 [S51            ]: USB-Audio - SB X-Fi Surround 5.1
                      Creative Technology SB X-Fi Surround 5.1 at usb-0000:00:1d.7-6.1, full speed
 2 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xefffc000 irq 16
 3 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xefdec000 irq 17


please help!

---

### Post by lulled on 2010-03-14
Thank you very much. It worked like a charm. :D

---

### Post by dgavenda on 2010-03-16
auto worked for me too.  I did try dell-m22 b/c I have a Dell Latitude 620 but that did not work.

---

### Post by Silent_Voice on 2010-03-21
It worked for me, thank you very much for the detailed instructions!

---

### Post by gux2k3 on 2010-04-18
Thanks a lot guys I was using an older kernel thanks to my lazynes when upgraded to karmic

special thanks
TacheDeChoco
la1234uk

:guitar:

---

### Post by lidex on 2010-04-18
*_[SIZE="4"][COLOR="Blue"]Karmic issues go here first:[/COLOR][/SIZE]_*
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by jazzderry on 2010-05-31
> **TacheDeChoco said:**
> After so many many attempts to solve my audio problems when upgrading to Karmic, I finally found a working solution  :p !

First, let me decribe what the problem was:
1) no audio card was detected at all
=> cat /proc/asound/cards returned an empty content
=> cat /proc/asound/devices did not include any audio devices
=> 'Hardware' tab in sound preferences was empty
2) the audio tray indicated a "dummy output"


SOLUTION
========

For those who do not have a fresh Karmic install (in other words those who have upgraded their Jaunty install), you should update your Grub BEFORE applying the 2 steps described hereunder:

sudo update-grub



**Step1: make the sound card being recognized**

=> _Purge _alsa-base and pulseaudio, eg:

sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] alsa-base
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload


Now, reboot, you shoud now SEE (but maybe not yet hear) your soundcard.
Give a try to:
cat /proc/asound/cards
and see if any card is listed...


**Step2 : If the sound is crapy, you MAY have to edit the alsa config file:**

sudo gedit /etc/modprobe.d/alsa-base-conf

a) comment (#) the following line:
[COLOR=Red]**#**[/COLOR] options snd-hda-intel power_save=10 power_save_controller=N

b) Add a new line
options snd-hda-intel probe_mask=1 model=[COLOR=DarkGreen]**hp**[/COLOR]

Replace "[COLOR=DarkGreen]**hp**[/COLOR]" with appropriate computer model. See [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt")

Good luck !

Bernard.
thank you for the great easy tip! i'm using ubuntu 10.04 Lts, came home from w/e away to find my sound gone-everything missing- no idea why but i reinstalled everything like you said(above) rebooted and the sound was back! so whatever the problem/bug is- its still there in Lucid.

---

### Post by TacheDeChoco on 2010-06-15
It's me again:p

Just to confirm that the problem seems to still exist in Lucid (even with a complete brand new/fresh install).

This time, my card was recognized (nice progress ;-) ! ), 
but i still had to add the line:

options snd-hda-intel probe_mask=1 model=hp

in my alsa-base-conf file...

---

### Post by paintedfaceless on 2010-07-02
Just to add to this. This fix did work out for my hp dv6500 in lucid linx. However, I've noticed that this problem seems to emerge again only when I shutdown my computer and forget I have an audio program (in my case Banshee) open. It also seems to come tagged along with an issue of not wanting to reboot correctly when I shutdown or restart using the menu, it pretty much just logs me out and there's no sound.

A simple hard reboot (holding the power button until it forces itself to shutdown) fixes both problems. hopefully this helps someone else, since this has been working for me.

---

### Post by DarkAmbient on 2010-07-16
> **TacheDeChoco said:**
> 
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] alsa-base
sudo apt-get remove [COLOR=Red]**--purge**[/COLOR] pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload

Now, reboot

Thank you! Ive only had 2 channel sound with Ubuntu 10.4. Doing this, not only I got my sound back (for some reason i got that dummy thing you mentioned an hour ago and no sound) but i got 5.1 surround to work aswell with this :D I'm really pleased!

---

### Post by edpare on 2010-07-22
Thanks Bernard!  I had the exact same symptoms and urging/preloading alsa did the trick!

Ed

---

### Post by Yumi on 2010-09-04
The described problem still exists in Maverick (Ubunut 10.10) and the cure works here too.

Thanks,
Michael

---

### Post by 5oak on 2010-09-07
I don't understand. Where should I put the model=auto part? There's nothing like it in my config file:
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```

For me the problem only occurs sometimes. It could have something to do with hibernation. By the way, I'm on lucid and use only the snd_usb_audio card.

---

### Post by 5oak on 2010-09-22
Bump. This is not solved for me...

---

### Post by lkjoel on 2010-09-24
For everyone reading this thread who do not have their sound problems fixed:
Go to Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by kazza_nz on 2010-10-31
Thanks Step 2 done the trick for the sound on my hp touchsmart to get it working on ubuntu 10.10.


> **TacheDeChoco said:**
> 
**Step2 : If the sound is crapy, you MAY have to edit the alsa config file:**

sudo gedit /etc/modprobe.d/alsa-base-conf

a) comment (#) the following line:
[COLOR=Red]**#**[/COLOR] options snd-hda-intel power_save=10 power_save_controller=N

b) Add a new line
options snd-hda-intel probe_mask=1 model=[COLOR=DarkGreen]**hp**[/COLOR]

Replace "[COLOR=DarkGreen]**hp**[/COLOR]" with appropriate computer model. See [here]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt")

Good luck !

Bernard.

---

### Post by kazza_nz on 2010-10-31
5oak 

I would assume the model=auto would refer to step 2b of the original post.

---

### Post by drinkleadsoup on 2011-01-11
This is what worked for me.  

Open Terminal.

Type:
[HTML]gstreamer-properties[/HTML]

On the audio tab, 
Below ouput,
click the plug-in button.

Choose ALSA

click the device button.

Choose "your soundcard"

Repeat for input.

You're done.

Test if you wish.

---

### Post by Issou92 on 2011-02-05
Thanks alot for the great guide, but here's what I get:

sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/issrar/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/issrar/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

I don't understand, my sound card is no longer detected, no hope of a sound from my laptop. I tried uninstalling/reinstalling pulseaudio and ALSA too :-/ Nothing ! The sound works fine with Windows :-/ 
I'd seriously appreciate some help please !

---

### Post by francis2795 on 2011-02-05
works, except the sound icon is now gone, but i can just use the volume buttons on my laptop. so how to put volume icon back in tray?

---

### Post by lkjoel on 2011-02-05
> **Issou92 said:**
> Thanks alot for the great guide, but here's what I get:

sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/issrar/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/issrar/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

I don't understand, my sound card is no longer detected, no hope of a sound from my laptop. I tried uninstalling/reinstalling pulseaudio and ALSA too :-/ Nothing ! The sound works fine with Windows :-/ 
I'd seriously appreciate some help please !
In a Terminal window type in:
```
aplay -l
```
and give us the results.
If you see "no soundcards found" then try:
```
alsaconf
```

---

### Post by lidex on 2011-02-09
Try this re-install method. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by exra82 on 2011-03-02
> **lidex said:**
> Try this re-install method. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

hmmmmm it seemed to work but when i rebooted it did nothing

---

### Post by exra82 on 2011-03-02
> **exra82 said:**
> hmmmmm it seemed to work but when i rebooted it did nothing



steven@steven-Compaq-Presario-CQ60-Notebook-PC:~$ sudo aplay -l
aplay: device_list:235: no soundcards found...
steven@steven-Compaq-Presario-CQ60-Notebook-PC:~$ 


tired that too

---

### Post by exra82 on 2011-03-02
> **lidex said:**
> Try this re-install method. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**



[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly. 

(1) Remove these packages
Code:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall those same packages
Code:
sudo apt-get install linux-sound-base alsa-base alsa-utils
[LIST][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:
sudo apt-get install gdm ubuntu-desktop

(3) Reboot
[*][LEFT]
VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:
sudo apt-get install gdm xubuntu-desktop

(3) Reboot
Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.
(4) At this point, try using
Code:
 aplay -l
you should get your soundcard listed.
Success - Your soundcard is detected. Go onto the Using alsamixer section, then try playing something on your music or media player.
Failure - Your card was not detected. You should try compiling your driver, so go onto ALSA drive Compilation.




this is what helped me!

---

### Post by SergeantBuck on 2011-03-23
Bernard,

You are both a god among men and my hero. I have an HP Pavillion dv6000 laptop and your instructions worked perfectly. I'm a linux n00b and I didn't understand any of it, but that's why linux and ubuntu are so awesome. The uneducated have awesome guys like you to fall back on.

Thanks again

Thanks

---

### Post by Unneoetech on 2011-05-16
I used this method successfully to get my sound back working again. Problem now is that my sound applet in Unity is gone... Is there a simple way to get it back again?

---

### Post by cmol on 2011-05-20
> **lidex said:**
> Try this re-install method. Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

Worked for me after upgrading from 10.10 to 11.04 with only a dummy sound output. Thanks :)

---

### Post by Neoracu on 2011-09-24
Works for me. I had my sound down for over two months already thought it was a hardware issue, but thanks to this post I have my sound back again.

Thank You very much.

---

### Post by Neoracu on 2011-09-27
Nope, not for too long, after 4 time I have rebooted the computer is again mute, no sound, I have repeated the steps, but is not working anymore the same steps, weird isn't it?.
Thank You anyway.

---

### Post by lidex on 2011-09-27
> **Neoracu said:**
> Nope, not for too long, after 4 time I have rebooted the computer is again mute, no sound, I have repeated the steps, but is not working anymore the same steps, weird isn't it?.
Thank You anyway.
Have a look here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by jrzabott on 2011-10-29
I know this thread is a little old, but it worked fine for me... but I did it in synaptic package manager, selected all find in "alsa" search, then mark for reintallation, and so.... Everything is right again!!!

Thank you very much.

---

