---
title: "Sony VAIO VGN-FZ11Z"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by ethan@xmlstandards.org on 2007-06-28
Hello all,

I have just received a new laptop and need to know if anyone out there has successfully installed Ubuntu onto it?

The model is:

[ Sony VAIO VGN-FZ11Z]("http://vaio.sony.co.uk/view/ShowProduct.action?product=VGN-FZ11Z&site=voe_en_GB_cons&category=VN+FZ+Series")

All feedback will be greatly appreciated.

Many thanks

Ethan

---

### Post by kiloxxx on 2007-07-05
Hi Ethan,
I purchased a Vgn-fz11z yesterday and I'm installing kubuntu feisty.

I encountered problems with the live cd (X11 couldn't start), but it seems that now I have found a workaround.

I will give you more informations tomorrow.

Kiloxxx

---

### Post by kiloxxx on 2007-07-09
Well, I finally installed Kubuntu Feisty on Vaio Fz11z, but some problems still persist.

The Kubuntu/Ubuntu live cd hanged while booting, probably in relation with the blu-ray writer, but I'm not sure (I have tried also the alternate cd and Knoppix and they hanged too).
The error message was this: 

> /bin/sh: can't access tty; job control turned off

The solution that worked for me was to remove all booting option (F6 key) and to add "all_generic_ide". For more details see this long thread: [http://ubuntuforums.org/showthread.php?t=415009]("http://ubuntuforums.org/showthread.php?t=415009")

After you have changed the booting options, the live cd works, but X can't start because of some problem with the "nv" driver and Nvidia 8400 card. You have to change in xorg.conf "nv" with "vesa", restart X and you can finally install kubuntu.


WHAT IS WORKING

Synaptics touchpad - fully working
Nvidia 8400 - fully working with latest Nvidia driver ([NVIDIA-Linux-x86-100.14.11-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run"))
Bluethoot - fully working
Media button - fully working (without any configuration)
Ethernet - fully working
Usb - fully working
Fn keys - partially working (only mute key works, bu I have not installed fsfn yet)


WHAT IS NOT WORKING

Blu ray cd/dvd - in /etc/fstab Feisty created a scd0 entry, but /dev/scd0 does't exist 
Motion eye camera - I have found drivers only for older versions
Fn keys, except the mute one
Suspend, hibernate - the pc suspends, but X hangs on resume


All other stuffs are not tested yet. 
Any suggestion is welcomed.

---

### Post by kiloxxx on 2007-07-09
I've forgotten one element: 

Audio is partially working - the audio card is recognized but only builted-in speakers work, the headphones are mute and I suppose that also mic-in is not working (I haven't an external microphone to test it).

---

### Post by ethan@xmlstandards.org on 2007-07-09
Hi there,

Many thanks for replying to my post. So glad that someone is trying to the same with this laptop.

I will post my fixes that work for me as soon as I can.

Ethan

---

### Post by kiloxxx on 2007-07-09
Hi, I've found a temporary solution for the Matshita recorder:

> I have this problem also. Can work it around in this way:
- Open a terminal
- write
sudo modprobe -v ide-generic

you should get /dev/hd(a-b-c-d) (primary/secondary master/slave), /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw depending on your configuration. The drive should also be visible in computer:/// and inserted discs should be automounted.

- If it worked, write in the terminal
sudo gedit /etc/modules

- add this line in it and save
ide-generic

Modifying /etc/fstab accordingly might be needed.
Please notice that ide-generic doesn't give you any DMA mode (and this is bad). This is just a temporary workaround, I think something should be fixed in the kernel...

More informations here: [http://ubuntuforums.org/archive/index.php/t-477516.html]("http://ubuntuforums.org/archive/index.php/t-477516.html")

---

### Post by Cavalier1723 on 2007-07-12
does anyone know if wireless is working? I have a FZ190 CTO configured similarily to the UK FZ11Z. Also, any solution found yet for the headphone audio?

Thanks.

---

### Post by kiloxxx on 2007-07-14
> **Cavalier1723 said:**
> does anyone know if wireless is working? I have a FZ190 CTO configured similarily to the UK FZ11Z. Also, any solution found yet for the headphone audio?

Thanks.


I haven't tested the wireless yet (I use a mobile phone via bluetooth). In regard to the headphone audio, mic and also - I think - modem, the problem is linked with the alsa driver. The latest driver supports the Intel cards till the ICH7 Family ([http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Intel#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Intel#matrix")), while FZ11Z has a ICH8 Family one. I am afraid we have to wait for a new driver.

---

### Post by kaburif on 2007-07-23
I have got a VGN-FZ11S and no problem with the bluetooth,wifi,cd/dvd,media cards,usb,svideo,microphone, but I can't make the motion eye camera working (tried a lot of solution without success), nor the sound correctly. I mean if you add 
```
options snd-hda-intel model=vaio position_fix=0
```
in your /etc/modprobe.d/sound file you can make your headphone work, but even if you have a headphone connected on it, it doesn't cut the sound from the speakers.. I tried a lot of things too to make it work correctly, without success.
The bigger problem i think is that i can't change the brightness of the screen. I don't know how to do it, I tried to install spicctrl, sonypi module.. the fn keys don't work (except mute)..
If someone has got solutions for these problems..

ps : sorry for my english

---

### Post by Cavalier1723 on 2007-07-25
On my laptop, FZ190 CTO (with 8400M), I can adjust the brightness of my screen using nvidia-settings. It is under the "X Server Color Correction" page. Remember to run with gksudo.

---

### Post by lamoni on 2007-07-26
> **Cavalier1723 said:**
> does anyone know if wireless is working? I have a FZ190 CTO configured similarily to the UK FZ11Z. Also, any solution found yet for the headphone audio?

Thanks.
I was able to get wireless working on my fz190 by following the steps at [http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html)

Also, If anyone else runs into the "API mismatch: this NVIDIA driver component has version 100.14.09, but the NVIDIA kernel module's version does not match." error after installing the nvidia driver, check out [http://ubuntuforums.org/archive/index.php/t-468353.html](http://ubuntuforums.org/archive/index.php/t-468353.html)

---

### Post by David A Knight on 2007-07-29
> **kaburif said:**
> I have got a VGN-FZ11S and no problem with the bluetooth,wifi,cd/dvd,media cards,usb,svideo,microphone, but I can't make the motion eye camera working (tried a lot of solution without success), nor the sound correctly. I mean if you add 
```
options snd-hda-intel model=vaio position_fix=0
```
in your /etc/modprobe.d/sound file you can make your headphone work, but even if you have a headphone connected on it, it doesn't cut the sound from the speakers.. I tried a lot of things too to make it work correctly, without success.
The bigger problem i think is that i can't change the brightness of the screen. I don't know how to do it, I tried to install spicctrl, sonypi module.. the fn keys don't work (except mute)..
If someone has got solutions for these problems..

ps : sorry for my english

Tried that on my fz11m, led to horrible noise out of the internal speakers only

options snd-hda-intel model=vaio probe-mask=1 and the headphone socket works for me + I get recording and switches tabs in the volume control now, so I can switch between mic/line in and set capture volume.  Still get sound from the speakers in the laptop though.

---

### Post by CheeseEatingBulldog on 2007-07-29
Don;t know if it helps or has any added value, but I have installed two vaio laptops with ubuntu without too many problems. Only the wifi card had some issues (PCMCIA), and to date can't get a framebuffer to work, so that when switching to alt+F1 terminal I don't get a mini screen.

---

### Post by xtrondo on 2007-07-30
I have a Sony VAIO VGN-FZ11Z, and get camera working in OpenSolaris & Ubuntu 7.04, now Im trying to get microphone from camera working. I test camera on Ekiga with sucess

 Regards,

 CA,

---

### Post by alex_ander1979 on 2007-08-23
I want to buy a new and good notebook.

It should have a good screen: from the notebooks that i have seen in the store only the Sony Vaio VGN-FZ11Z and the latest MacBook pro seems to have good screens.

But i need that linux runs well on the notebook.

What kind of notebook do you recommend (and what is with a ThinkPad or a Dell ?).

And the main question to you is:

**_what runs with linux under the Sony Vaio VGN-FZ11Z and what not ?_**

The X11 system ? Graphic and sound ? DVD ? and behaves the fan correctly and the acpi ? WLAN and Ethernet ?

Thank you !

I had bad experiences with linux on laptops, so I want a good laptop WITH linux.

---

### Post by kiloxxx on 2007-09-10
Hi,
good news on Vaio VGN-FZ11Z and Kubuntu/Ubuntu.
I've made a fresh installation of Kubuntu Gutsy Gibbon Tribe5 and the results are better than Feisty's ones.

1. Live cd: you can now use the live cd without problems, apart from the fact that the X server still doesn't load with the "nv" driver. You have to manually change in "/etc/X11/xorg.conf" "nv" with "vesa", restart X and install Kubuntu/Ubuntu.

2. Driver Nvidia: you can use the nvidia-glx-new packet, but X doesn't load and "/var/log/Xorg.0.log" give an error about a missed "wfb module", you can solve this using the latest driver "[NVIDIA-Linux-x86-100.14.11-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run")".
Here the workaround:
```
$ cd [the directory where you have downloaded the driver]
$ sh NVIDIA-Linux-x86-100.14.11-pkg1.run -x
$ sudo cp -f NVIDIA-Linux-x86-100.14.11-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.100.14.11 /usr/lib/xorg/modules
$ cd /usr/lib/xorg/modules
$sudo ln -s libnvidia-wfb.so.100.14.11 libwfb.so
```


3. What is working without any specific configuration:

Keyboard and Synaptics touchpad - fully working
Matshita blu-ray cd/dvd - fully working 
Nvidia 8400 - fully working (see above)
Ethernet - fully working
Bluethoot - fully working
Wifi - fully working
Media button - fully working
Usb - fully working
Fn keys - partially working (only mute key works)
Sound - partially working (inserting "options snd-hda-intel model=vaio" in "/etc/modprobe.d/sound" works - speakers, headphones, line in and the built in microphone are recognized correctly - but, when you plug in the headphones, the speakers doesn't mute)


4. What is working with specific configuration:

Motion Eye camera - fully working with this driver: "[r5u870-0.10.0.tgz]("http://lsb.blogdns.net/files/r5u870-0.10.0.tgz")" , but you have to change a file before compiling it:

```
$ cd [the directory where you have downloaded the driver]
$ tar xzvf r5u870-0.10.0.tgz
$ cd r5u870-0.10.0
$ vim r5u870_md.c
```

In file  "r5u870_md.c", at line 1196 change ".default_value = 0" with ".default_value = 1" and after line 3015 add "{ R5U870_DEVICE_UVC(0x05CA, 0x1837, R5U870_DI_VGP_VCC4) },". 
Then:

```
$ sudo make
$ sudo make install
$ sudo modprobe r5u870
```

Or, if you want the module loading at startup, add  "r5u870" in "/etc/modules". I've tested the camera with Ekiga, WengoPhone and Kopete and it works (only with Kopete there are some problems with color, but they are caused by Kopete itself).


5. What is not working:

Fn keys, except the mute one (in "Nvidia X server settings" you can change brightness, but I don't think that these changes could affect power saving)
Suspend, hibernate - the pc suspends, but X hangs on resume


All other stuffs are not tested yet.

---

### Post by kiloxxx on 2007-09-11
In addition to point 4 "Motion Eye Camera": I've noticed conflicts between the "r5u870 module" and the "uvcvideo module" preloaded in the Kubuntu/Ubuntu's kernel. The camera sometimes is recognized as "Sony VGP-VCC4" and it works, other times as "UVC Camera (05ca:1837)" and it doesn't work. The solution is to put the "uvcvideo module" in the blacklist, adding "blacklist uvcvideo" to "/etc/modprobe.d/blacklist", and then reboot.

---

### Post by alex_ander1979 on 2007-09-13
Does the fan works correctly ? 

(acpi and so ...).

Thx

---

### Post by kiloxxx on 2007-09-16
The fan works correctly and also the cpu policy is right.
Suspend works, but X hangs on resume.
Hibernate works, X resume correctly but then is quite unstable.
The brightness control doesn't work; apart from this, power management works (you can turn of the screen and it also switch off when you close laptop lid).

---

### Post by TheProgrammer on 2007-10-08
kiloxxx, you said that you can change the brightness from Nvidia X server settings. Does it actually work (e.g. brightness going down) or you just have a drag but no effect?

---

### Post by kiloxxx on 2007-10-08
As Cavalier1723 suggested in a previous message, you can adjust brightness under the "X Server Color Correction" page of "Nvidia X Server Settings". It actually works, brightness goes up and down, but I suppose that acting only on color correction could not affect power sawing.

---

### Post by kiloxxx on 2007-10-12
Hello all,
I've recently read in another [thread]("http://ubuntuforums.org/showthread.php?p=3478299") about some enhancements for Vaio VGN-FZ190, I think they should work also for VGN-FZ11Z.

At the moment I haven't time to test them, but if someone would like to do it...

> **BillShepp said:**
> Further update on VGN-FZ190 after installing 2.6.23rc9 kernel (and reinstalling 100.14.19 Nvidia drivers:[LIST]
[*]Had to install ALSA (1.0.15rc3) after updating kernel.  Doing so **fixed the issue where the internal speakers still played when headphones were plugged in**.  Note that I had to add a line to /etc/modprobe.d/options: "options snd_hda_intel model=vaio"
[*]I was able to suspend successfully once using "/etc/acpi/sleep.sh force".  An additional attempt failed, but I think I may have changed something.  Still working on this.
[*]I discovered that sonypi was being loaded by /etc/init.d/hotkey-setup even though I had blacklisted it in /etc/modprobe.d/blacklist.  I commented out this line in hotkey-setup (leaving sony-laptop).
[*]Most FN keys seem to be recognized now by xev or /var/log/acpid.  Fn-F2 (mute) and the volume keys are not currently working for me; they have worked intermittently, but I've not been able to track down why they sometimes do and sometimes don't.[/LIST]Remaining big issues:[LIST]
[*]Reliable suspend and hibernate support
[*]Ability to adjust screen brightness[/LIST]Note - I used [KernelCheck]("http://ubuntuforums.org/showthread.php?t=556726") to update the kernel, it worked beautifully, makes it very easy to revert back to previous kernel.

Bill

---

### Post by kiloxxx on 2007-10-17
FINALLY SOLVED THE SPEAKERS/HEADPHONES PROBLEM!

I've installed the new version of the Alsa driver (1.0.15) and it works: speakers now mute when headphones are plugged in.

Here a useful howto: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by dracomordag on 2007-10-20
> **kiloxxx said:**
> FINALLY SOLVED THE SPEAKERS/HEADPHONES PROBLEM!

I've installed the new version of the Alsa driver (1.0.15) and it works: speakers now mute when headphones are plugged in.

Here a useful howto: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
i followed these instructions exactly, and my headphone jack still doesnt work.I have a VGN-FZ190

cat /proc/asound/card0/codec#* | grep Codec
returns
Codec: SigmaTel STAC9872AK


any thoughts?

---

### Post by kiloxxx on 2007-10-22
Unfortunately I can't help. The Codec is the same in FZ11Z, I simply upgraded the alsa driver and it works.

Did you put in "/etc/modprobe.d/" the file named "sound", with the following option inside?

```

options snd-hda-intel model=vaio
```

---

### Post by dracomordag on 2007-10-22
isnt it supposed to be /etc/modprobe.d/alsa-base ?

---

### Post by kiloxxx on 2007-10-24
Yes, it should be the same thing. I initially used /etc/modprobe.d/sound, as suggested by a previous post, and then I didn't change it. I think that the use of sound is related with older configurations, but I'm not sure. However for me both methods work.

---

### Post by dracomordag on 2007-10-24
well, neither work for me.

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=auto
options snd-hda-intel model=vaio
options snd-hda-intel probe_mask=1

```

---

### Post by kiloxxx on 2007-10-25
My alsa-base is like yours, except for the last three lines where there is only

```

options snd-hda-intel model=vaio
```

You might delete 

```
options snd-hda-intel model=auto
options snd-hda-intel probe_mask=1
```

---

### Post by isenalim on 2007-10-28
Hi there, I have this laptop and followed the howto  to install alsa 1.0.15 driver but it seems that the card is not recognized.

I get the following error

```

$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory

```

Maybe this can be helpful

```

$ dmesg |grep hda
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   18.036000] snd_hda_intel: Unknown symbol snd_ctl_add
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_new
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   18.036000] snd_hda_intel: Unknow
n symbol snd_pcm_limit_hw_rates
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   18.036000] snd_hda_intel: Unknown symbol snd_card_register
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   18.036000] snd_hda_intel: Unknown symbol snd_card_free
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   18.036000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   18.036000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   18.036000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   18.036000] snd_hda_intel: Unknown symbol snd_component_add
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   18.036000] snd_hda_intel: Unknown symbol snd_card_new
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   18.036000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   18.036000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   18.036000] snd_hda_intel: Unknown symbol snd_device_new
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   18.036000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   18.036000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   18.036000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step


```

Can anyone help me please?
Thanks!
Bye
Beppe

---

### Post by isenalim on 2007-11-02
Hi!
How did you get the driver for the webcam? it is no longer available on the provided link!

Thanks a lot!

---

### Post by isenalim on 2007-11-04
I solved the problems with the audio installing the packages of version 1.0.15 from the Debian Sid repository.

Also the webcam works without problems following the instructions in a previous post in this thread. You can download the source package from the arakhne repository

[http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.10.0-4.tar.gz]("http://download.tuxfamily.org/arakhne/pool/ricoh-webcam-r5u870/ricoh-webcam-r5u870_0.10.0-4.tar.gz")

Have fun!

---

### Post by frunns on 2007-11-06
yeah, I got the audio working too using the debian repository... though I still get sound from the internal speakers. =/ using an vgn-fz11m.

---

### Post by marco_polo99 on 2007-12-02
Running a VGN-FZ240E and a fresh reinstall of alsa according to instructions found in [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+mixer](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+mixer)  followed by also downloading the alsa mixer gui

"sudo apt-get install alsamixergui"

adding the line

"options snd-hda-intel model=vaio position_fix=0"

into /etc/modprobe.d/alsa-base 

This fixed the headphone jack issue--now I hear sound in headphones and it mutes the laptop speakers when jack is installed, although mic in still seems to not be working...

---

### Post by kiloxxx on 2008-05-21
Hi,
I'm trying to configure the internal modem of the fz11z in order to send faxes. I've used ScanModem with no success. It simply doesn't recognize any modem on my machine. Then I tried to find some details on the sony's site, but it gives only general informations. 
Is there someone who still have installed windows and could give me some information on the hardware?
Thank you in advance.

---

