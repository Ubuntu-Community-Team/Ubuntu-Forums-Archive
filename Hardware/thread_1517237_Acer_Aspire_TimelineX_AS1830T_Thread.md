---
title: "Acer Aspire TimelineX AS1830T Thread"
date: 2010-06-24
forum: Hardware
---

### Post by stillnotcool on 2010-06-24
Has anyone tried installing Ubuntu on the Acer Aspire TimelineX 1830T?  The forums contain discussions of the other new TimelineX models, but I can't find anything related to this one (with its 11.6-inch screen).

Has anyone tried installing Ubuntu on this computer?

---

### Post by demonic_bunny on 2010-06-24
> **SemioticRobotic said:**
> Has anyone tried installing Ubuntu on the Acer Aspire TimelineX 1830T?  The forums contain discussions of the other new TimelineX models, but I can't find anything related to this one (with its 11.6-inch screen).

Has anyone tried installing Ubuntu on this computer?

Id like to know if this laptop plays nice with Lucid too. Would be a nice travel machine...

---

### Post by stillnotcool on 2010-06-25
At the moment I'm seeing listings for two versions of the 1830T: the 1830T-3927 with Core i3 and 3GB DDR3 RAM, and the 1830T-3721 with Core i5 and 4GB DDR3 RAM.

I'd certainly be interested in hearing reports on both models and recommendations on which will offer the most complete, effective, hassle-free Lucid installation (particularly, right out of the box).

Thanks in advance to anyone who can offer advice.

---

### Post by tpdi on 2010-08-31
I have an Acer 1830T-3721.

Apparently, different machines come with different chip sets. I hit the jackpot (not) with the ALPS touchpad, the Atheros ethernet, and the Broadcom wireless, all of which do not work with Kubuntu Lucid out-of-the-box.

Please see my other posts in this forum for the fixes/work-arounds I'm using; long story short, the Touchpad won't do two-finger scrolling until (at earliest) the release of Maverick.

Please post here if you have any advice for me regarding thermal/fan control and power saving.

---

### Post by ubun_two on 2010-08-31
> **tpdi said:**
> I have an Acer 1830T-3721.

Apparently, different machines come with different chip sets. I hit the jackpot (not) with the ALPS touchpad, the Atheros ethernet, and the Broadcom wireless, all of which do not work with Kubuntu Lucid out-of-the-box.

I have the same laptop with pretty much the same hardware.  Like you, I got everything to work except for touchpad, which is continued to be recognized as a generic PS2 mouse.  I installed kernel 2.6.35, but that still didn't help.

---

### Post by tpdi on 2010-09-01
Installing Andrew Skalski's psmouse.ko will give you right-edge vertical scrolling.

Get it here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/152](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/152) (Note that's for 64 bit (k)ubuntu; if you want 32 bit, you'll have to get the source and compile that.)

I'm currently running windows, because 
a) power consumption on the battery is too high in Kubuntu, and
b) temperature is too high too.

---

### Post by schmickey on 2010-09-21
I have the 1830T-3721 with ALPS, Broadcom Wi-Fi and Atheros AR8151 ethernet.

I immediately ditched the Broadcom card and replaced it with an Intel 6200.  Downloaded and installed Atheros ethernet driver from Atheros Partners website.  All networking works well now.

I didn't have sound to the headphone jack until I installed the Alsa Upgrade.  Now that works fine too.  Touchpad issues don't concern me as I always use a mouse.

I haven't tweaked any ACPI settings... I should look into that because, like someone here said, it does run hot and battery life sucks.  I have an Intel Generation 2 SSD installed and realized that TRIM is not enabled in the default kernel.

I'm waiting for Maverick (newer kernel supports TRIM for SSDs).  No Linux on my computer at the moment... only Windows 7.

There is an extensive thread on this model on notebookreview(dot)com.  There are a few Linux tips in there.

This is a great little laptop with plenty of power and it absolutely screams with an SSD. Battery life is longer and it's even lighter with the SSD.  Highly recommended upgrade.  The Intels are more expensive but I think they are worth it because they are designed for longevity (built-in wear-leveling).

---

### Post by scarleo on 2010-10-10
I've installed Ubuntu Lucid on my 1830TZ with a Intel U5400 processor. I'm not really sure about the model number on it but it says MS2296 underneath. Probably some low budget version of yours. Anyway, I'm very pleased with it, even though it has the Broadcom wireless and ALPS touchpad. I'm able to get good battery life out of it, 8-9 hrs if I'm careful and at least 5-7 if I watch a movie or listen to music. Power consumption on battery is about 7-8 W with wireless still enabled and screen active but with some other measures taken, flash is as always a culprit and it shoots up to maybe 12-15 W depending on quality and so on. Still a lot better than my old laptop that never got below 20 W.  When screen goes off I get below 6 W consumption (= over 10 hrs). 

Windows 7 do run a bit cooler than Lucid so its a bit more quiet in W7, and sadly there are no ways (at least that I know of) to control the fan speed yet. I have been in contact with Peter Feuerer that has made the acerhdf package to control fans on Aspire One and he is looking into a solution, sadly it doesn't look good as far as I understand.

Installing went smooth and without any problem what so ever. Yes, you do need proprietary drivers from Broadcom but everything you need is on the USB-drive once you have Ubuntu 10.04 Lucid Lynx there. I just clicked the networking icon and it suggested itself to install the driver. But do take care too see that you have enabled your wireless (Fn + F3) hardwarewise. If you want to use Bluetooth you first have to activate it in W7, after that it works without problem in Ubuntu. However the Bluetooth button is the same as for wireless so one has to play around with it and hit it numerous times to get either one or both activated. It's pretty easy to figure out, just open your Bluetooth control panel in Ubuntu and see when it's activated and not.  

 Touchpad works out of the box. It is detected as PS/2 Generic Mouse but that is not a problem unless you need to do some mayor changes. Fancy stuff like Pinch Zoom or Two Finger Scrolling won't work for now but after trying that out in W7 I don't want it :). I know there are solutions to get side vertical scrolling to work and that might be the only thing I'm really missing right now but I'm going to wait for a fully working release from Ubuntu (It's really a kernel thing) and I'm hoping for 10.10 to deal with this. Also all my Fn+ buttons work OOTB; switch off screen, brightness, volume and so on.

To reduce power consumption I've made some small changes. I never use my webcam, cardreader and bluetooth, and when activated these do eat a lot of power. I also seldom use my USB ports so I usually have these deactivated. For the rest of all the power saving solutions out there (a lot!) Lucid takes care of nearly everything you need. My philosophy is to not be redundant and risk conflicts, so I have not installed laptop-mode-tools and so on. All I've done is put a small script in /etc/pm/power.d/ and called it 15_savings. Basically it just loads and unloads modules depending on if I'm on AC or Battery. Also take care to go through your Startup applications and deactivate everything you don't absolutely need. And I've also deativated Compiz. Do look at Powertop for consumption but don't activate your power saving measures through it because it's not accurate. When I have my script activated I get no further suggestions from Powertop and I have abt 15 wakeups per second. It's still a lot and I don't know if thats good but it's the best I've seen so far so I'm happy.

 Regarding the circumstances and alternatives I'm more than pleased with this laptop and I would say that Ubuntu Lucid plays really nice with it. I have seen a lot worse and I know that there are many more things that can go wrong than it did on this machine. If you have any more power saving suggestion I'd be glad to here about it, and also if you find a good(!) way to make the ALPS touchpad recognized. Take care!

15_savings:
```
#!/bin/sh

  # Go fast on AC power.
if on_ac_power; then

  # Optional: Activate most of the bluetooth/usb subsystem
  modprobe rfcomm
  modprobe l2cap
  modprobe bluetooth
  modprobe usbhid
 
  # Activate webcam
  modprobe uvcvideo

  # Disable SATA power saving
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo max_performance > $foo;
  done

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  # echo 600 > /proc/sys/vm/dirty_writeback_centisecs 

 # HDA Intel power saving, already done by Lucid
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save
  echo N > /sys/module/snd_hda_intel/parameters/power_save_controller
else # Save power

  # Deactivate webcam
  modprobe -r uvcvideo

  # Optional: Remove the most of the bluetooth/usb subsystem
  sudo killall bluetooth* 
  sleep 5
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
  modprobe -r usbhid
  modprobe -r usb_storage 

  # Set eye-candy options, uncomment for testing purpose
  # metacity --replace &

 # Enable SATA power saving, already taken car of by Lucid
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo min_power > $foo;
  done

  # Set the intel wlan to save power Findings: Doesn't work
  # iwconfig eth0 power on

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  #  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs #Changed in /usr/lib/pm-utils/power.d/powersave-policy-dirty-writeback   instead for testing purpose
  
  # Put down the controller when not in use
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
  echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
fi
```

---

### Post by scarleo on 2010-10-10
Oh, I forgot to tell you, sleep works fine but wireless is disabled after resume. I don't see this as a problem, just right click and choose enable wireless, wait a few seconds and then do Fn + F3 and you're back on track. It's good for powersaving that it's diabled.:P

---

### Post by jacki on 2010-10-12
Hi lucky 1830 owners,

I am also considering to buy this laptop, but wonder which configuration to take; in particular, which CPU. Could someone please report how the Pentium U5400 version performs (1830TZ)?

Do desktop effects and movies run smoothly? Has anyone tried running a recent kde version on this machine? Or do you think getting an i3/i5 version will make a major difference for usage like web browsing, email, digikam, music ... ? How much ram to take .. :confused: 

Any hint is greatly appreciated :P

---

### Post by bungh0l3 on 2010-10-12
Hey dudes,

a friend of mine just recently purchased the 1830tz. When I had set up Lucid for her, almost everything worked fine (except for the vertical scroll on touchpad for some reason). 

But after upgrading to Maverick, suddenly the sound was gone!

'cat /proc/asound/cards' didn't even recognize the soundcard. 

At first I thought maybe something went wrong during the upgrade procedure. But the same issue occurs while running Maverick on Live CD. Vertical scroll doesn't work either, btw.

Now the funny thing is: When a tried a Live CD of Maverick Beta on this very same machine a few weeks ago, vertical scrolling as well as sound worked just fine out of box. So I wonder what went wrong during beta and final release. 

Can anyone of you confirm this issues or better yet, can come up with a solution?

---

### Post by zviangi on 2010-10-15
I got my 1830t i5-470UM couple of days ago. It came with Synaptics touchpad, atheros eth and Broadcomm WiFi.
Installed Maverick yesterday, everything works more or less, Broadcomm works after installing (using LAN cable connection) proprietary drivers, that Maverick detected and installed by itself, touchpad works with regular, one finger vert. scrolling, did some tweaks for two finger scrolling, have to restart to see if it works. I am not sure about internal Mic, will have to research on it...

---

### Post by roach_chris on 2010-10-21
I bought a 1830TZ from Hong Kong a few weeks ago (with the U processor) and tried installing several versions of Ubuntu 64bit and i386 versions without much success. 

First there was the problems getting the graphics working (in the end i had to change the config files to use the vesa option as a work around - the screen still drops out, the resolution is funny, compiz doesn't work), then the current problem is getting the sound and mic to work - seems that the sounds card isn't detected at all! - Still working on this one (any ideas would be appreciated). I still have to manually log on at a prompt then use 'startx' to get the GUI up (no idea why that happens). Hopefully they'll be a kernal update in the future which may fix some of these things... fingers crossed. Maybe i'll try and update the Bios once i get windows back!? Hopefully that will help?

 I've spent days and days trying to get Ubuntu to work and just about ready to go back to Windozzze ?! :( It seems that other people have had more success. It's a bit of a hit and miss with Acer. My old ASUS EEE worked flawlessly....8

---

### Post by hudsong on 2010-12-06
Hey,

You might try following this tutorial:

[https://help.ubuntu.com/community/Aspire1830T](https://help.ubuntu.com/community/Aspire1830T)

Also, It seems like the one with the i5/i7 processor is more problematic than the lower spec i3. It seems the i5/i7 has the ALPS touch pad, Broadcom wireless, etc. So keep that in mind if you buy this. 

I was going for the i5, but then I realized the only difference was intel's "speedboost", a BIOS based overclocking feature. I think that these i5 laptops have shorter battery life and run hotter in Linux because the i5 overclocking is always on by default.

I personally don't feel like messing with it to eek out maybe 10%-15% more performance, but for those who are interested, check this thread out:

[http://www.phoronix.com/forums/showthread.php?t=16111](http://www.phoronix.com/forums/showthread.php?t=16111)

---

### Post by kay_rus on 2010-12-23
Hi everyone.

I have just bought the TimelineX 1830T with Core i3 U380.

My 1830T has all Atheros network cards:
AR9285 Wireless Network Adapter (PCI-Express)
AR8151 v1.0 Gigabit Ethernet

Touchpad was recognized as generic Ps/2 mouse and multitouch doesn't work at all. I have tried all the workarounds I found but no one helped me.

And I have few questions...
1) How to force 802.11n Wifi? Now it works only in 802.11g (my EEEPC can work with the 802.11n when set some option)
2) Does AR9285 work in WiMax?
3) How to enable multitouch?
4) I didn't expect that HDMI will be detected automatically, but I expected that it could work in 1080p mode. But it works only in 640x480 mode (can't remember, possibly there was lower resolution). How can I make autodetect HDMI when I plug notebook to my TV (like in Win7) and how can I fix the resolution?

---

### Post by mattwilkes512 on 2011-01-25
I just got an 1830T i5 a few weeks ago and have already tried to dual boot Win 7 with Ubuntu 10.10 but had issues. Ran hot and wifi was not working right were the biggest deal breakers.

Any ideas as to how compatible the 1830T i5 will be with Ubuntu 11.04? Has anyone installed the Alpha release yet?

---

### Post by dmjm on 2011-01-26
Try [https://help.ubuntu.com/community/Aspire1830T](https://help.ubuntu.com/community/Aspire1830T). I've got an 1830T-3712 which is an i5 model with Broadcom Wifi. Is working acceptably in my books once you understand the quirks (e.g. Fn+F3 behaviour).

---

### Post by il1019 on 2011-04-27
I'm running 10.10 for my main install, i5 model (3721). Wifi works with driver, touchpad doesn't have any features (I REALLY miss two finger scroll, or any kind of scroll). Everything else works right (video, audio, suspend, etc).

I've tried the beta for a while now and I can't get wifi to work. It always says 'Wifi is disabled' in the menu. I've tried playing around with FN-F3 a bit and the wifi light never seems to go on. I can get bluetooth working, but the wifi just doesn't work. I've even tried external (USB) wifi adapters and I get the same thing, so I'm guessing there is something weird going on. I tried putting a different mini PCI-E card in and that didn't work either. I put the card that was in the 1830T into a Dell Mini 10 and it worked fine, so it has to be something with the specific way that mini-PCIE slot is activated I think. Anyone else seeing this?

---

### Post by easyfragger on 2011-04-27
Here's how I got wifi working in 11.04 beta on a similar laptop: 

* make sure you have the latest linux-firmware installed (1.52)
* remove all packages with b43 in their names
* remove broadcom-sta-common and broadcom-sta-source
* install bcmwl-kernel-source
* put acer-wmi on the blacklist

Hope it works for you as well!

---

### Post by digisol1 on 2011-05-25
I am running into the exact same thing with the wireless. I cannot use the fn-f3 combo to do anything. I did have the wifi working fine in Windows 7, so honestly I am at a loss for what to do.

BTW, I have tried 11.04(32bit), 10.10(32bit), 10.04(64bit) and backtrack5(32bit) which I think is based on 10.04.

I also switched wifi cards in mine as well. nothing, so I know it is note the card it is the keyboard functionality. BTW, fn-f4 works which is sleep as well as fn-f? the one that turns the trackpad off.




> **il1019 said:**
> I'm running 10.10 for my main install, i5 model (3721). Wifi works with driver, touchpad doesn't have any features (I REALLY miss two finger scroll, or any kind of scroll). Everything else works right (video, audio, suspend, etc).

I've tried the beta for a while now and I can't get wifi to work. It always says 'Wifi is disabled' in the menu. I've tried playing around with FN-F3 a bit and the wifi light never seems to go on. I can get bluetooth working, but the wifi just doesn't work. I've even tried external (USB) wifi adapters and I get the same thing, so I'm guessing there is something weird going on. I tried putting a different mini PCI-E card in and that didn't work either. I put the card that was in the 1830T into a Dell Mini 10 and it worked fine, so it has to be something with the specific way that mini-PCIE slot is activated I think. Anyone else seeing this?

---

### Post by digisol1 on 2011-05-31
I wanted to thank everyone here.. this worked for me..

SUPER SPECIAL THANKS goes out to 
il1019 and EASYFRAGGER:popcorn:


Here's how I got wifi working in 11.04 beta on a similar laptop: 

* make sure you have the latest linux-firmware installed (1.52)
* remove all packages with b43 in their names
* remove broadcom-sta-common and broadcom-sta-source
* install bcmwl-kernel-source
* put acer-wmi on the blacklist

Hope it works for you as well!

---

### Post by tetsuc on 2011-06-06
With a clean install of 11.04 all I needed to do to get the wifi working was to add the following to /etc/modprobe.d/blacklist.conf
```
blacklist acer_wmi
```

I have the 1830T-3730. I also find that the network connection is slow/not aggressive enough sometimes (especially when there are loads of macbooks around...). This also keeps NXclient from timing out.
 
```
sudo iwconfig eth1 power off
```

One thing that I can't figure out how to do, however, is get the fan to slow down/turn off. I know what the temp is and there is no reason that the fan should be on!! I have done a bit of research but haven't yet found a way to control fanspeed. The acerhdf module fails to load because this machine's bios version is not supported. 

This worked on 10.10 (though I am not sure if it was because of the acerhdf module or not)

Any ideas?

---

### Post by tetsuc on 2011-09-19
Bump....

Has anyone found a way to control the fan speed in 11.04? It is driving me a bit crazy!

---

### Post by Saorex on 2011-11-15
Bump!

Anyone has viable solutions for mouse pad vertical scrolling?

Thanks a lot!

---

### Post by scarleo on 2011-11-16
If you want scrolling to work on 1830T you can download and install this .deb: [http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb]("http://people.canonical.com/%7Esforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb")
Then restart. I have tested this with 11.10.

As per: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051)

Might still have a few issues as reported but I find it works fine and am so happy with finally having two finger scrolling! And you can also choose edge scrolling in Touchpad settings as of now.

---

### Post by scarleo on 2011-11-26
I just wanted to share these power saving tweaks as I've been testing out various combinations to lower power to get longer battery and more quiet fan. I got the info from here: [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

The problem was I was seeing a idling power consumption of around 10-14W on my 1830TZ which was much higher than when I first got Ubuntu on it. I remember seeing battery times of around 8 hours on idling and I wanted it back! Before these tweaks I had abt 4 hours. I know it can be tweaked even more but I'm no fanatic, just want a reasonable time and not waste power on unnecessary things but without lowering the usability.

Background is there was a power regression in the Linux kernel starting some time ago, read more on the link I gave if you're interested. This affects also Ubuntu 11.10. The biggest problem is  [PCI  Express Active-State Power Management (PCI-E ASPM)]("http://www.phoronix.com/scan.php?page=news_item&px=OTYwNA") that can again be activated, it's probably not active in your kernel. The reason it was removed by default was some hardware incompatibility so these tweaks may or may not work on your laptop. I don't know what different hardware spec the 1830 comes with but I'll share mine and if yours are the same you should see the same gain as I have seen. If yours is not the same it might still work or you should try any combination of the kernel parameters.

So, here we go. My hardware first:

```

System Information
    Manufacturer: Acer
    Product Name: Aspire 1830T
    Version: V1.11
    Wake-up Type: Power Switch
    SKU Number: Calpella_CRB
    Family: Intel_Mobile
BIOS Information
    Vendor: INSYDE
    Version: V1.11
    Release Date: 06/04/2010
    ROM Size: 2048 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 11.240
Processor Information
    Socket Designation: CPU
    Type: Central Processor
    Family: <OUT OF SPEC>
    Manufacturer: Intel(R) Corporation
    ID: 55 06 02 00 FF FB EB BF
    Version: Intel(R) Pentium(R) CPU        U5400  @ 1.20GHz
    Voltage: 0.0 V
    External Clock: 1066 MHz
    Max Speed: 1200 MHz
    Current Speed: 1193 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    L1 Cache Handle: 0x0031
    L2 Cache Handle: 0x0030
    L3 Cache Handle: 0x002E
    Serial Number: Not Specified
    Asset Tag: FFFF
    Part Number: Not Specified
    Core Count: 2
    Core Enabled: 2
    Thread Count: 2
    Characteristics:
        64-bit capable

```If you want to read more about the options before you try just click the link to Phoronix above.
To test these changes out press 'e' when you see grub. move to the line (kernel boot) that ends with 'silent splash' and add:

```
pcie_aspm=force i915.lvds_downclock=1 i915.i915_enable_rc6=1
```These are the options that works best with my setup. I know a lot of 1830 comes with iX processors. If you have one of these you could also try adding:
```
i915.i915_enable_fbc=1
```I did not have any luck with this option, it worked but froze my screen after a while. I believe if you have an iX proccessor you will have better luck with this option but I have not tested it since I don't have that processor. 

If the computer seems unstable after adding any or all of these options you can just reboot and everything will be back to normal. If you have freezes like I had you can try pressing ctrl+alt+F1, login at the prompt and do either 'skill -KILL -u username' or just 'reboot' or 'sudo reboot'. If it seems unstable you can try adding just one or any combination of the boot options.

If you decide that you want to make the changes permanent you can edit /etc/default/grub and edit the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash". Add the options that works for you, save and then run 'sudo update-grub'.

My result, idling is with WiFi enabled and connected and Firefox started with 5 tabs open but not touching anything:
Idling before tweak: 12-14W
Idling after tweak: ~7W

Idling without Firefox and wifi:
Before: ~11W
After: 5.8W

The results are pretty amazing, it's up to 50% power save. And it runs much cooler and is finally quiet again. If you have any other tweaks or suggestions I'm all ears.

EDIT: I forgot to say that I have also ran PowerTop before measuring my power consumption, and enabled all the tunables, it does quite a difference as well.

---

