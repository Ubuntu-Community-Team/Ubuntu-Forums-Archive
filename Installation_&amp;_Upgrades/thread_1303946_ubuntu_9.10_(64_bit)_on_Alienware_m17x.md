---
title: "ubuntu 9.10 (64 bit) on Alienware m17x"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by niite on 2009-10-28
Well, I've just successfully gotten 9.10 going on my Alienware m17x notebook.  Wanted to just give a summary.

**Clean install vs upgrade from 9.04**

***Clean Install of 9.10***

I attempted a clean install of 9.10 first, not so succsessful.  I have two 500 GB drives, and I'm not running RAID at all with them.  I have them in AHCI Native.  The first drive has win7 running on it, and I have had ubuntu 9.04 running on the second drive.  I wiped the second drive before attempting this clean install.

I dowloaded the iso for the 9.10(AMD64) desktop version. When I ran the install, it would not find my second hard drive.  Nothing I did could get it to see it.  (I had no such problem with the ubuntu 9.04 install).  So I downloaded the alternate AMD64 install version for 9.10.  After some fumbling with it at the partition portion of install (going manual vs automatic) I was able to get it to see and install to the second hard drive.  After that, the install went uneventfully.  A few problems once install was complete:

1.  Grub did not provide an item to boot my vista drive.
2.  No wireless - Broadcom AW1510 WLAN  (this sucked, 9.04 install had given me this out of the box on install - and no propriety driver listed or available for it)
3.  Just generic Video driver (and no propriety drivers available - although the ones available previously for 9.04 never worked any way - 180 and 173)
4.  No proprietary drivers listed when i go to hardware drivers (the funny thing was, for the desktop live cd, it did give me options for these drivers using live).

So instead of fumbling around for a wireless driver, i wiped the drive, put 9.04 back on, and figure i'd get it set to go and upgarde it to 9.10.  Much better luck this way.

***Upgrading to 9.10 from 9.04***

Very painless upgrade - for the most part.  No grub problems like with the clean install.  Also picked up proprietary drivers from the 9.04 no problem, so wireless worked.  Had the following issues, and their resolution:

**Graphics - dual Geforce GTX 260M** .  on my 9.04 installation, I had never succsessfully gotten video drivers from Nvidia to recoginize my graphics (I have two Geforce GTX 260M cards, as well as an integrated Geforce 9400 on the board).  I had just been using the generic driver until 9.10 came out.   I noticed that Nvidia had relased a new certified driver for linux to support my 260M cards - Nvidia driver version 190.42.  So I downloaded the driver before my upgarde.  you can find it here:  [http://www.nvidia.com/object/linux_display_amd64_190.42.html](http://www.nvidia.com/object/linux_display_amd64_190.42.html)

After completing the upgrade to ubuntu 9.10 as expected my graphics driver went crazy, and did not function - got a blank screen that flickered.  I went to command line and installed the new driver from Nvidia, and had no problems on bootup, graphics worked great - recognized both my 260M cards.  *(of note, I needed to disable both hybrid and integrated graphics in bios - or I get a black screen on bootup).*

**Audio** - same problem as 9.04.  Ubuntu doesn't seem to play well with my IDT 92HD73C1.  In order to get this functioning I had to add the following to alsa-base.conf found at /etc/modeprobe.d/

options snd-hda-intel model=dell-m6 enable=1 index=0
options snd-hda-intel enable_msi=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

I don't seem to be getting the full capabilities of the sound card (6channel surround, etc), but I'm getting very decent audio (and much better then 9.04).

So that's what I got for now.  playing around with it and things seem to be working fine..  love the compiz effect which I can finally use.

---

### Post by Tomatosoup on 2009-10-28
Ubuntu 9.04: Wireless via 300N-XR USB: okay, only no N-standard!
Ubuntu 9.10 RC: No wireless connection via 300N-XR: sucks ***!

Want to try the final Karmic Koala version. Let's hope it will do better!

---

### Post by niite on 2009-10-29
Yeah, no kidding..  but they give you the proprietary drivers on the live cd.. go to install and nada.  lol, too funny.

---

### Post by faydout on 2009-11-16
Hi everyone... I was hoping someone much smarter than I am could throw me a bone on this. I've been using Ubuntu for the past month at work and love it so I decided this weekend to make the switch at home. I set up a flash drive to install the OS for me and broke out an old laptop to test with. It worked great and decided it was time to switch the alienware m17x after backing up my important files. I popped in the flash drive and it began the boot process, but after the ubuntu symbol appears for the first time the screen goes black and never does anything. I dont get an error message to diagnose anything from. I'm hoping someone here knows of any workarounds or things I need to do first. I'm thinking to take the new load from the other laptop, load it with ATI drivers and try a restore on the other laptop...

---

### Post by datman on 2009-12-21
Hey all, another M17x Ubuntu user here. Thought I would put my experiences here to help other M17x users up and running.

[B]Graphics
[/B]
I have dual Nvidia GTX260M, ATI installs will be different.

To get graphics working:

First disable integrated and hybrid graphics in the BIOS.

Now install prerequisites:

sudo apt-get install linux-headers-`uname -r` binutils pkg-config build-essential  xserver-xorg-dev

Now you can download the NVIDIA driver from here:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Select the latest version of **Linux AMD64/EM64T** drivers, and then install like this:

chmod +x NVIDIA-Linux-x86_64-190.42-pkg2.run
./NVIDIA-Linux-x86_64-190.42-pkg2

Reboot and your X should be working.[B] Note that if you boot up while on battery, Integrated graphics will be automatically enabled in BIOS and then X will fail to start properly.
[/B]
**Sound**

I followed niite's suggestion to get sound working, which worked OK, but I could only get sound from the headphone socket and not the internal speakers. To fix, I changed the line:

options snd-hda-intel model=dell-m6 enable=1 index=0

to 

options snd-hda-intel model=laptop enable=1 index=0

also i updated ALSA to latest version, see here:

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

Now sound works correctly from the speakers and mutes them when i plug in the headphones.

[B]WiFi

[/B]And to get wifi working took the following steps:

**1. Download and build the STA driver module:**

System > Administration > Hardware Drivers should be able to download and install the modue for you, but it would not work for me. 

So manually download the STA 64 bit driver from here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

then build and install it like this:

cd <path_where_you_downloaded>
sudo cp hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz /usr/local/src
# you might need to change the version above if it does not match your download
cd /usr/local/src
sudo mkdir hybrid_wl
cd hybrid_wl
sudo tar xzf <path>/hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz
sudo make

You should now have a wl.ko file successfully built. You should now copy it to your kernel modules lib folder (substitute your kernel version)

sudo cp wl.ko [FONT=monospace][/FONT]/lib/modules/<kernel-version>/kernel/net/wireless 

**2. Disable other conflicting modules**

Now you have to remove any conflicting modules. To see if any are loaded, type:

lsmod  | grep "b43\|ssb\|wl"

If any of these are installed, remove them:
sudo rmmod b43
sudo rmmod ssb
sudo rmmod wl

To blacklist these drivers and prevent them from loading in the future:
sudo echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
sudo echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

Even though they are blacklisted, ssb will still be loaded in the initramfs. This will prevent wl.ko from loading after booting. To fix this, type:

sudo update-initramfs -u

**3. Enable the new module at boot**

and finally to start the wl module automatically at boot:

sudo echo "wl" >> /etc/modules

Now reboot and set up your wireless password etc in NetworkManager. If you upgrade your kernel in future, you will have to rebuild the module and copy it into the new kernel's lib directory.

---

### Post by [Neurotic] on 2010-01-08
Thanks for all the hard work to those that came before me, it made my life a lot easer when setting up my m17x.

Some extra notes on installing on the m17x.

If you want to install on Raid1, the following guide helped me out a lot.  There are a couple of small pieces missing from the walkthrough, but if you read through the post first, there are some responses from me that should fill in all the details. 
[http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

For the nvidia drivers, its worth noting that there is a nvidia PPA that keeps all the drivers up to date. You can find it here: [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

From there, run ```
sudo nvidia-xconfig
```, and you are good to go.

I'm currently running the 195.30 drivers as I was getting the occasional black screen on boot.  This seems to be a little better now, however I do get the occasional freeze / black screen when booting up, which I can't even seem to ctrl+alt+f1 to a tty terminal to.  Sometimes I get a freeze after the login screen, sometimes this happens before I login, and sometimes after, it is very random. (Anyone else getting this?). I get no problems booting win7.

For sound - all I had to do was upgrade alsa up to 1.0.22 using this guide, [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/). I didn't have to set any special parameters, or anything.  Sound now works like a charm.

---

### Post by datman on 2010-01-08
Good to see another Linux equipped M17x :)

Has anyone had any luck getting a second monitor to work via HDMI yet? I have played around a bit with no luck so far.

---

### Post by [Neurotic] on 2010-01-08
datman - I do right now with HDMI and a second monitor.  I just plug it in, and use the Nvidia config tool to hook up the 2nd monitor. Works like a charm.

The other bug I have had recently, is that if the power cable comes out from the laptop, I get a freeze in Ubuntu. Anyone else get that?

---

### Post by Aikimox on 2010-01-08
So glad that I found this thread!
I'm trying to switch entirely to Ubuntu 9.10 on my M17X and the only remaining obstacle is the SLI support for GTX280M cards.
I did so many re-installs lately and completely out ideas what can be done to fix it.
With the 195.30 drivers I am able to turn the SLI on but the 3D rendering is awefull, even Compiz doesn't run smooth. The cards never hit their max clocks (power level 1 at best). Phoronix lightsmark score is 240FPS on average with SLI on. So far the best option is to switch the SLI Off and play games/run Compiz with a single card...
Will appreciate your help on that one.

P.S> tried installing the 185 driver from the Hardware Drivers; updating the repos and installing the 190 and 195 from there as well; manually installing (185,190,195) on a fresh install; tried running nvidia-xconfig --sli=auto/AFR/SFR/On - all with the same result - choppy compiz and unplayable games with SLI and bearable playing with a single card. 

Thanks in advance.

---

### Post by datman on 2010-01-09
> **'[Neurotic] said:**
> datman - I do right now with HDMI and a second monitor.  I just plug it in, and use the Nvidia config tool to hook up the 2nd monitor. Works like a charm.

OK so I had a bit more of a play around with it.... Using the nvidia-settings applet I was able to get the second monitor working via HDMI. However I have the following issues still:

* No second monitor at all if SLI is enabled (this was my problem before)
* If I enable Xinerama, I get one big desktop and I can move windows from one to another (as expected), but Compiz doesn't work, i.e. no compositor so no transparency or desktop effects.
* If I disable Xinerama, I get two separate desktops, Compiz works, and I can move the mouse from one desktop to another, but I cannot move a window from one desktop to the other.

Ideally I would like to get both monitors working with one desktop (Xinerama), Compiz and SLI. Doesn't seem like this is possible at the moment.

> **'[Neurotic] said:**
> The other bug I have had recently, is that if the power cable comes out from the laptop, I get a freeze in Ubuntu. Anyone else get that?

I don't always get that problem, just gave it a try and it was ok. - edit: Second time I tried it I got a freezeup too :( looks like ubuntu is useless without AC.

One other issue is sometimes the screen brightness buttons work but sometimes they don't so I have to use the Gnome brightness applet instead.

I think nvidia needs to do some more work on their drivers.

---

### Post by Aikimox on 2010-01-09
> **datman said:**
> OK so I had a bit more of a play around with it.... Using the nvidia-settings applet I was able to get the second monitor working via HDMI. However I have the following issues still:

* No second monitor at all if SLI is enabled (this was my problem before)
* If I enable Xinerama, I get one big desktop and I can move windows from one to another (as expected), but Compiz doesn't work, i.e. no compositor so no transparency or desktop effects.
* If I disable Xinerama, I get two separate desktops, Compiz works, and I can move the mouse from one desktop to another, but I cannot move a window from one desktop to the other.

Ideally I would like to get both monitors working with one desktop (Xinerama), Compiz and SLI. Doesn't seem like this is possible at the moment.



I don't always get that problem, just gave it a try and it was ok. - edit: Second time I tried it I got a freezeup too :( looks like ubuntu is useless without AC.

One other issue is sometimes the screen brightness buttons work but sometimes they don't so I have to use the Gnome brightness applet instead.

I think nvidia needs to do some more work on their drivers.

I can confirm all your issues as I get them too.
Are you able to use SLI and Compiz together with no lagging when rotating the cube? I installed additional features for Compiz (like snow) and even they are choppy...
Did you run any tests (phoronix test suite)?

---

### Post by datman on 2010-01-09
> **Aikimox said:**
> I can confirm all your issues as I get them too.
Are you able to use SLI and Compiz together with no lagging when rotating the cube? I installed additional features for Compiz (like snow) and even they are choppy...
Did you run any tests (phoronix test suite)?

Yes I have tried cube rotation with SLI on and off and it is smooth for both. Here is a snippet of my xorg.conf:

    Option         "RendelAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "Triplebuffer" "true"
    Option         "NoFlip" "True"
    Option         "SLI" "Auto"

Maybe one of those options might help.

I have not run phoronix yet, but i will do some tests with that later tonight.

---

### Post by Aikimox on 2010-01-09
> **datman said:**
> Yes I have tried cube rotation with SLI on and off and it is smooth for both. Here is a snippet of my xorg.conf:

    Option         "RendelAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "Triplebuffer" "true"
    Option         "NoFlip" "True"
    Option         "SLI" "Auto"

Maybe one of those options might help.

I have not run phoronix yet, but i will do some tests with that later tonight.

Tried all of them now, no improvement in Compiz and same lightsmark result. :(

---

### Post by Aikimox on 2010-01-09
Could you please post your entire xorg.conf?

---

### Post by k64 on 2010-01-09
What I decided to do is build a computer with Linux-compatible hardware the whole way. This way, I didn't have to deal with hardware issues!

---

### Post by datman on 2010-01-10
> **Aikimox said:**
> Could you please post your entire xorg.conf?
OK So after more testing it seems that SLI is not working properly as you have said. Although the cube rotation (CTRL-ALT mouse click) works OK, the OpenGL screensavers run crap with SLI enabled. Here's my xorg.conf anyway:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Dec 18 18:35:05 PST 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "RendelAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "Triplebuffer" "true"
    Option         "NoFlip" "True"
#    Option         "SLI" "Auto"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by datman on 2010-01-10
> **k64 said:**
> What I decided to do is build a computer with Linux-compatible hardware the whole way. This way, I didn't have to deal with hardware issues!

Did you build a laptop?

---

### Post by Aikimox on 2010-01-10
> **datman said:**
> Did you build a laptop?

:D Let's wish him luck in the endeavor.

Back to our business:
I think that we'll have to wait for better drivers from Nvidia. Meanwhile the best option for me was to switch the SLI off and work with a single card. It's enough for most games. 
Anyway, I'll be searching for ideas/solutions....
Stay tuned.:cool:

---

### Post by [Neurotic] on 2010-01-12
Doing some diggging it seems that twinview is not supported with SLI enabled.

Hopefully they fix that in some driver releases.

---

### Post by dkhajavi on 2010-01-19
I just want to say thanks!!  I have been on Ubuntu (single boot) on my M17X Nvidia SLI260 machine since 8.04 and never had the Nvidia cards working till now.  I had to disable the embedded graphics and use the 195 drivers and 100% working perfect!

I have had sound, WiFi etc... working since 8.04.  

What is left???  Well the small stuff like being able to control the keyboard lighting, setting the hot keys up to work, like the performance button etc...  The keyboard lighting is a big one for me as I am a businessman by day and 'other' at night...so the Reggae coloured pattern my M17X came back with from the repair depot (broke hinge after a drop) is not giving me any high praises around the office.  I dont have windows to boot into to change them then go back again.  Any ideas?

---

### Post by afbase on 2010-01-23
Could somebody explain to me how they got their wifi working?


datman's explanation didn't work for me.

---

### Post by afbase on 2010-01-23
> **afbase said:**
> Could somebody explain to me how they got their wifi working?


datman's explanation didn't work for me.
Ok I figured out the wifi this morning.  Here is my issue:  I followed datman's instructions in this thread in kernel 2.6.31-14-generic.  I upgraded to kernel 2.6.31-17-generic.  My Nvidia drivers won't in 2.6.31-17-generic.  This is the error in my /var/log/xorg.log
```

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```Are there any solutions to my issue?

I see there are two files of interest in the /usr/lib/xorg/modules/drivers/ folder.  I have nvidia_drv.so and nv_drv.so   I'm assuming I want to have Xorg load the nv_drv.so instead of the nvidia_drv.so.  Is this correct? and how can I do it?

---

### Post by [Neurotic] on 2010-02-12
afbase - if you upgrade your kernel, you have to manually recompile your drivers each time.

APT usually takes care of this for you, but if you are setting up manual drivers, then you have to take care of this yourself.

Its a bit of a pain, but it works.

The only thing that is still driving me crazy on the m17x is the random bootup to black screen. Is anyone else getting this?

It seems to be related to a DMESG message of:
```

[  601.040078] Corrupted low memory at ffff8800000017a8 (17a8 phys) = e1b700000000
[  601.040084] Corrupted low memory at ffff880000001e00 (1e00 phys) = e1b700000000
[  601.040087] Corrupted low memory at ffff880000001e58 (1e58 phys) = e1b700000000
[  601.040090] Corrupted low memory at ffff880000002450 (2450 phys) = e1b700000000
[  601.040093] Corrupted low memory at ffff880000002880 (2880 phys) = e1b700000000
[  601.040098] ------------[ cut here ]------------
[  601.040107] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/check.c:134 check_for_bios_corruption+0xe5/0x100()
[  601.040111] Hardware name: M17x          
[  601.040112] Memory corruption detected in low memory

```

And it only happens randomly on first boot. If I shut down the laptop, and then boot again, it comes up just fine. The 2x boot is starting to drive me crazy though.  I would love to have a workaround if anyone has one?

---

### Post by drbcladd on 2010-03-22
This is a fun thread to read; I got most of the elements working (including sound: I purged pulse-audio and updated the alsa drivers and the sound card worked). I, too, am getting the random crashes with low memory corruption. The system log contains
```

Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040149] Corrupted low memory at ffff8800000029e0 (29e0 phys) = e1b700000000
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040171] Corrupted low memory at ffff8800000039e0 (39e0 phys) = e1b700000000
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040188] Corrupted low memory at ffff880000005dc0 (5dc0 phys) = e1b700000000
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040199] Corrupted low memory at ffff880000005e10 (5e10 phys) = e1b700000000
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040210] Corrupted low memory at ffff880000005f80 (5f80 phys) = e1b700000000
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040219] ------------[ cut here ]------------
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040247] WARNING: at /build/buildd/linux-2.6.31/arch/x86/kernel/check.c:134 check_for_bios_corruption+0xe5/0x100()
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040258] Hardware name: M17x          
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040265] Memory corruption detected in low memory
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040273] Modules linked in: binfmt_misc ppdev snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss bridge snd_pcm snd_seq_dummy stp snd_seq_oss snd_seq_midi bnep snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device lib80211_crypt_tkip snd soundcore coretemp wl(P) uvcvideo iptable_filter sdhci_pci videodev ip_tables ricoh_mmc snd_page_alloc psmouse i2c_nforce2 sdhci lib80211 lp btusb v4l1_compat nvidia(P) v4l2_compat_ioctl32 led_class serio_raw x_tables parport joydev dm_raid45 xor usbhid ohci1394 video output ieee1394 forcedeth
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040451] Pid: 15, comm: events/0 Tainted: P           2.6.31-20-server #58-Ubuntu
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040462] Call Trace:
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040484]  [<ffffffff8105e538>] warn_slowpath_common+0x78/0xb0
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040501]  [<ffffffff8105e5cc>] warn_slowpath_fmt+0x3c/0x40
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040517]  [<ffffffff810366a5>] check_for_bios_corruption+0xe5/0x100
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040532]  [<ffffffff810366c0>] ? check_corruption+0x0/0x30
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040545]  [<ffffffff810366c9>] check_corruption+0x9/0x30
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040564]  [<ffffffff810731f5>] run_workqueue+0x95/0x170
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040578]  [<ffffffff81073374>] worker_thread+0xa4/0x120
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040593]  [<ffffffff81078500>] ? autoremove_wake_function+0x0/0x40
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040608]  [<ffffffff810732d0>] ? worker_thread+0x0/0x120
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040621]  [<ffffffff81078116>] kthread+0xa6/0xb0
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040636]  [<ffffffff8101312a>] child_rip+0xa/0x20
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040649]  [<ffffffff81078070>] ? kthread+0x0/0xb0
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040662]  [<ffffffff81013120>] ? child_rip+0x0/0x20
Mar 22 10:04:26 BigRedTwo kernel: [ 5461.040671] ---[ end trace 5362289327b42f7e ]---

```

After this morning's reboot. The crashes seem to trace to the use of the NVidia drivers (may be the SLI). I will try disabling SLI and see if that fixes anything. 

Thanks to everyone who posted progress; happy to pay back if there are any questions.

-bcl

---

### Post by f4ded_glory on 2010-04-04
Has anybody found a fix for the hybrid graphics on the M17x?  Is it possible to boot with all three video card enabled?

---

### Post by [Neurotic] on 2010-04-04
> **f4ded_glory said:**
> Has anybody found a fix for the hybrid graphics on the M17x?  Is it possible to boot with all three video card enabled?

The only way I've found to do it, is disable the nvidia driver :P

Not so great an idea though!

---

### Post by drbcladd on 2010-04-06
Similar results: I can boot with 1 NVidia card running high-resolution graphics, I can boot with the on-board graphics after disabling nvidia drivers, and hybrid graphics always seems to screw things up.

Another question: Has anyone succeeded in turning off the BIOS reset to on-board graphics during a non-plugged in boot? That is, whenever I boot the machine and am NOT on an AC adapter, the BIOS enables the integrated graphics. That is after I explicitly turned OFF the integrated graphics (I don't care about battery life right now!) During the boot I can go to Setup (<F2>), go to Advanced | Graphics Settings and turn it off AGAIN but that is getting a little bit old. Doubles the boot time.

---

### Post by pranaynewton on 2010-04-24
Hi,

I have got SLI working on ubuntu its working pretty well. I am posting my xorg.conf file.
I am using the Nvidia CUDA developer driver. 

You can download it from this site: 

32-bit:
[http://developer.download.nvidia.com/compute/cuda/3_0/drivers/devdriver_3.0_linux_32_195.36.15.run](http://developer.download.nvidia.com/compute/cuda/3_0/drivers/devdriver_3.0_linux_32_195.36.15.run)

64-bit:
[http://developer.download.nvidia.com/compute/cuda/3_0/drivers/devdriver_3.0_linux_64_195.36.15.run](http://developer.download.nvidia.com/compute/cuda/3_0/drivers/devdriver_3.0_linux_64_195.36.15.run)

here's my xorg.conf file:

---

### Post by f4ded_glory on 2010-04-25
I got everything working except the integrated camera, and ofcourse, the hybrid graphics.  I'm not even sure where to begin with the hybrid.  I'm running CUDA so that why I want all three graphics to run so I can run CUDA jobs on the discrete and the display on the 9400M.  I don't need the SLI.  Just all three graphic chips usable by the system.

Any idea on how to get the camera working?

I'm using Lenny 64-bit.

---

### Post by [Neurotic] on 2010-04-30
Just want to check if anyone is running Lucid yet?

Any issues with the graphics cards? I noticed lucid is using the nvidia 185.x driver, and there are issues upgrading to 195.x manually.

Figured it was worth asking the question before I upgraded.

---

### Post by hansdown on 2010-04-30
Hi [Neurotic].

Just to let you know, 
you will get a better answer, if you start a new thread.  

What graphics card are you running?

---

### Post by [Neurotic] on 2010-05-01
Actually, that's a good point. I will do that.

---

### Post by datman on 2010-05-01
> **f4ded_glory said:**
> 
Any idea on how to get the camera working?

I'm using Lenny 64-bit.

FWIW my camera works out of the box on Karmic 64 bit with no tweaks at all.

---

