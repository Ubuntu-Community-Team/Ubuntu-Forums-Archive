---
title: "How to: Karmic Koala on Acer 1410 / 1810T/ 1810TZ"
date: 2009-11-29
forum: Hardware
---

### Post by PatrickVogeli on 2009-11-29
[SIZE=4]**[COLOR=Orange]UPDATED FOR UBUNTU 10.04 LUCID LYNX[/COLOR]**[/SIZE]

This guide was first started at [Notebook Review Forums]("http://forum.notebookreview.com/showthread.php?t=434638"). There are a lot of Acer 1410/1810T/1810TZ users over there.

**Packard Bell / Gateway clones:**
This guide has also been tested on a Packard Bell Dot M/U with bios v3303, and it should also work on the Gateway clone. If you have a 1410/1810 and something doesn't work, please report back.

**What's working after a standard Ubuntu 10.04 install:**
[LIST]
[*]Graphics
[*]Audio out, speaker mutes when pluging in headphones. Good volume.
[*]Networking, both wireless (intel wifi 1000) and wired (the atheros gigabit)
[*]FN +:
[LIST]
[*]F4, suspends fine
[*]F6, monitor goes black
[*]F7, touchpad on / off
[*]F8, mute
[*]F9, Bloq Num
[*]RePag: Home
[*]AvPag: End
[*]Up: increase volume
[*]Down: decrease volume
[*]Righ: increase brightness: skips steps.
[*]Left: decrease brightness: skips steps.
[*]J,K,L, etc: numeric keyboard ok.
[/LIST]
 
[/LIST]
**What's not working:**
[LIST]
[*]Audio in: the integrated mic doesn't work.
[*]FN + F5: not recognised, doesn't toogle displays
[/LIST]
**[SIZE=4]Automated Install [SIZE=1](recommended)[/SIZE]:[/SIZE]**[INDENT] I've done a script that should do it all automatically. In detail:

[SIZE=2]**What the script does:**[/SIZE]

[LIST]
[*]Configure gnome-power-manager backlight dim and hard disk power saving
[*]Download, patch, install and setup acerhdf
[*]Install the power saving script
[*]Install the debugging script
[*]If laptop-mode-tools is installed, suggest uninstalling and, if you want, uninstall
[*]Fix the brightness hotkeys issue (jumps 2 levels on every key press)
[*]Disable ethernet Wake on Lan (doesn't enable when on AC)
[*]Disable uneeded services: cron, anacron and atd (they don't enable when on AC)
[/LIST]
[SIZE=2]**What the script doesn't:**[/SIZE]

[LIST]
[*]Add the noatime parameter to the ext2/3/4 partitions in fstab. You'll have to do it manually.
[/LIST]
[SIZE=2]**How it works:**[/SIZE]

[LIST]
[*]In a terminal, run ./InstallAcer_11.6_PowerSaving.sh --help
[/LIST]
[SIZE=2]**Disclaimer:**[/SIZE]

[LIST]
[*]This script comes with no warranty. Use it at your own risk. I won't be responsible for any damage this could do to your system or data.
[/LIST]
[/INDENT][SIZE=4]**Manual Install**[/SIZE]:

**Power saving tips:**[INDENT]**The Script:**[INDENT]By default, an ubuntu install won't take too much care of saving power, which is very important in an ultra mobile laptop. You can easily setup the system to enter some power saving modes, specifically the sata controller and the sound chip.

I've setup a script which will take care of making the devices entering the power saving mode when the laptop is on battery.
```
#!/bin/bash

      ## Disable unnecessary services
      service atd stop
      service cron stop
      service anacron stop
      ## Acer 11.6 brightness hotkey fix
      echo N > /sys/module/video/parameters/brightness_switch_enabled
      ## Disable wake on lan
      ethtool -s eth0 wol d

  if on_ac_power; then
  #### Go fast on AC power.  Similar to default Ubuntu settings
  
      # Remount ext3/4 filesystems to default value: every 5 seconds
      mount -o remount,commit=5, /
      mount -o remount,commit=5, /home

      ## Set swap usage back to default
      echo 60 > /proc/sys/vm/swappiness

      ## Disable Sata Power Saving
      for foo in /sys/class/scsi_host/host*/link_power_management_policy;
        do echo max_performance > $foo;
      done

      ## Disable Intel Wlan Power Saving
      iwconfig wlan0 power off

      ## Disable HD Audio Power Saving
      echo 0 > /sys/module/snd_hda_intel/parameters/power_save
      echo N > /sys/module/snd_hda_intel/parameters/power_save_controller

      ## Set kernel dirty page value back to default
      echo 20 > /proc/sys/vm/dirty_ratio
      echo 10 > /proc/sys/vm/dirty_background_ratio
      echo 500 > /proc/sys/vm/dirty_expire_centisecs
      echo 500 > /proc/sys/vm/dirty_writeback_centisecs 
      
  else 
  #### Save power

      ## Change the ext3/4 commit times to 10 minutes.  Reduces disk activity
      mount -o remount,commit=600 /
      mount -o remount,commit=600 /home

      ## Reduce swap usage as much as possible
      echo 1 > /proc/sys/vm/swappiness

      ## Enable Sata Power Saving
      for foo in /sys/class/scsi_host/host*/link_power_management_policy;
        do echo min_power > $foo;
      done

      ## Enable Intel Wlan Power Saving
      iwconfig wlan0 power on

      ## Enable HD Audio Power Saving
      echo 10 > /sys/module/snd_hda_intel/parameters/power_save
      echo Y  > /sys/module/snd_hda_intel/parameters/power_save_controller

      ## Reduce disk activity by waiting up to 10 minutes before doing writes
      echo 90 > /proc/sys/vm/dirty_ratio
      echo 25 > /proc/sys/vm/dirty_background_ratio
      echo 60000 > /proc/sys/vm/dirty_expire_centisecs
      echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
      
  fi
```To install this power saving script, do the following:
```
gksudo gedit /etc/pm/power.d/15_saving
# Paste the script above into the file, save and close
sudo chmod +x /etc/pm/power.d/15_saving
sudo ln -s /etc/pm/power.d/15_saving /etc/pm/sleep.d/
sudo chown root /etc/pm/power.d/15_saving
sudo chgrp root /etc/pm/power.d/15_saving
```[/INDENT]**gnome-power-manager**:[INDENT]Go the g-p-m preferences, under System -> Preferences -> Power management, and do the following:
[LIST]
[*]Hard drive power saving: in the battery tab tick on "Reduce hard drive revolutions when possible"
[*]Battery tab: tick on reduce brightness and dim display.
[*]AC and Battery tab: configure what to do when closing the lid and what to do on very low battery remaining.
[*]General tab: configure what to do when pressing the power button and sleep button (Fn+f4).
[*]General tab: configure when to show the battery icon.
[/LIST]
[/INDENT]**The “noatime” parameter:**[INDENT]In linux, and in ubuntu it's on by default, the filesystem has 3 types of date information: when the file was created, when the file was modified and when the file was last accessed. This last access information means that _everytime_ a file is accessed (everytime you read a file), it does a file system write, to update the information. In My Honest Opinion, this is not necessary, and I would disable the last access information. How? Editing fstab and adding the noatime paramenter to all ext2/3/4 mounted partitions. You can edit fstab by doing gksudo gedit /etc/fstab and, there, add the parameter noatime to all the ext2/3/4 lines. Example on how the relevant fstab lines look in my machine:
```

UUID=VERY-LONG-NUMBER  /       ext4  errors=remount-ro,noatime   0       1
UUID=VERY-LONG-NUMBER  /home   ext4  defaults,noatime            0       2

```There may be people who  may find the atime parameter interesting, I don't. Hard drives are already the biggest bottlenecks in computers, and doing extra writes won't improves things, so I prefer to avoid them.[/INDENT][/INDENT]**Issues:**[INDENT] **Fan:**[INDENT] **Issue:** the fan is controlled by the BIOS, and is running too loud and too often.
**Solution:** the solution is installing an update acerhdf module. Download the laster version from [here]("http://%22http://piie.net/index.php?section=acerhdf%E2%80%9D"). There's a great chance that it will work without any additional work, skip the next lines and go ahead on to how to install acerhdf.
If after installing acerhdf it doesn't work, you'll have to patch it adding your BIOS version. Open the acerhdf.c file and add the following code above this line: '/* pewpew-terminator */':
```

/* Acer 1410 */
{"Acer", "Aspire 1410", "v0.3108", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1410", "v0.3113", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1410", "v0.3119", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1410", "v0.3117", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1410", "v1.3204", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
/* Acer 1810T(Z) */
{"Acer", "Aspire 1810T", "v0.3108", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810TZ", "v0.3108", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810T", "v0.3113", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810TZ", "v0.3113", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810T", "v0.3117", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810TZ", "v0.3117", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
/* Packard Bell clone */
{"Packard Bell","DOTMU","v0.3108", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Packard Bell","DOTMU","v0.3113", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Packard Bell","DOTMU","v0.3115", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Packard Bell","DOTMU","v0.3117", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Packard Bell","DOTMU","v0.3119", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Packard Bell","DOTMU","v1.3204", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
```Save and close. Let's go on into compiling it:
```

cd /to/the/acerhdf/folder
make
sudo make install

```To make sure the module gets loaded and the fan control is enabled, do the following:
```

echo "acerhdf" | sudo tee -a /etc/modules
sudo touch /etc/modprobe.d/acerhdf.conf
echo "options acerhdf kernelmode=1" | sudo tee -a /etc/modprobe.d/acerhdf.conf
sudo modprobe acerhdf

```That will take care of loading the module when starting the laptop and automatically enable the fan control. After doing that, you should already be enjoying silent fan operation. You can also add, to the /etc/modprobe.d/acerfhdf.conf the values fanon= and fanoff=, followed by a value. For example: fanon=60000 fanoff=52000 will turn the fan on when it reaches 60ºC and will shut it down when it reaches 52ºC.
[/INDENT]**Brightness:**[INDENT] **Issue:** when changing the brightness using the FN+arrow keys, it will jump 2 levels instead of one. 
**Solution:** add the following into /etc/rc.local, **before** exit 0 and without quotes: "echo N > /sys/module/video/parameters/brightness_switch_enabled".
[/INDENT]**Integrated mic:**[INDENT] **Issue:** the internal microphone is not working. Playing with alsamixer doesn't solve this, all you can hear is noise.
**Solution:** None at the moment. There's a thing you can try for Skype, though. Do the following, after installing skype from skype.com:
```

sudo touch /usr/local/bin/skype
sudo chmod +x /usr/local/bin/skype
gksudo gedit /usr/local/bin/skype

```There, paste the following, save and close:
```
#!/bin/sh 

/bin/sh -c "PULSE_SERVER=127.10.10.1 /usr/bin/skype"
```After that, you can play a bit with the mic settings under alsamixer and try skype. It shoud kind of work, but there's still some static noise.
[/INDENT]**Debugging:**[INDENT]In the one of the attachments, you'll find the CheckPowerSaving.sh file. This script should help you debugging and will show you what values are being applied. To run it: cd to the folder where the unzipped file is and then sudo ./CheckPowerSaving.sh. If you need help you can attach the output here.[/INDENT][/INDENT]**Next to be done:**
[LIST]
[*]Enable undervolting (nothing until Lucid comes out AND the phc repos are running for lucid).
[/LIST]

[B]Changelog
[/B]
[LIST]
[*]20/04/2010: added an automated install script
[*]16/04/2010: updated for Lucid. Jaunty, original post: [http://ubuntuforums.org/showpost.php?p=9132302&postcount=91](http://ubuntuforums.org/showpost.php?p=9132302&postcount=91)
[*]29/12/2009: updated version of acerhdf, added blacklist acer-wmi to blacklist (thanks to all who reported)
[*]05/12/2009: acerhdf version 0.5.21 now includes BIOS definitions for acer 1410/1810T(Z) and Packard Bell Dot M/U in v3303 and 3120. Audio alternative solution is now the recommended solution (thanks to iiamjon at notebook review forums, who tried and reported it as working)
[*]02/12/2009: added more acerhdf bios definitions and changed acerhdf enabling. Thanks to teprrr.
[*]29/11/2009: Initial post
[/LIST]

**Thanks** 
[LIST]
[*]tdavis, from Notebook Review Forums, for the wake on lan tip and adding the 11,6" acer series into acerhdf
[*]teprrr, from Notebook Review Forums, for the acerhdf modprobe tip and bios definitions
[*]laramichaels1978: for detecting some errors and suggesting adding the dirty_expire_centiseconds option
[/LIST]

---

### Post by the666pack on 2009-12-01
> **PatrickVogeli said:**
> Hi there all,

**Issues:**
[INDENT]**Fan:**
[INDENT]**Issue:** the fan is controlled by the BIOS, and is running too loud and too often.
**Solution:** we'll patch and install latest acerhdf module. Download the latest version from [here]("http://www.piie.net/index.php?section=acerhdf") (0.5.20 when writing this). Unpack and look for the acerhdf.c file. In this file, look for the acer 1410 section:
```

/* Acer 1410 */
{"Acer", "Aspire 1410", "v0.3120", 0x55, 0x58, {0x9e, 0x9e, 0x00} },

```
We have to add the definitions for the 1810T(Z). Add below the following bellow the Acer 1410 section:
```

/* Acer 1810T(Z) */
{"Acer", "Aspire 1810TZ", "v0.3120", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810T", "v0.3120", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
/* Packard Bell clone */
{"Packard Bell","DOTMU","v0.3120", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
/* Bios v3303 */
{"Acer", "Aspire 1410", "v1.3303", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810TZ", "v1.3303", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810T", "v1.3303", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Packard Bell","DOTMU","v1.3303", 0x55, 0x58, {0x9e, 0x9e, 0x00} },

```
Save and close. Let's go on into compiling it:
```

cd /to/the/acerhdf/folder
make
sudo make install

```
To make sure the module is loaded at boot up: 
```
echo "acerhdf" | sudo tee -a /etc/modules
```
That will take of loading the module when starting the laptop. There's still a step missing: when the module gets loaded, it doesn't enable the kernel fan control. We have to do this manually. To avoid having to do it manually on boot, we'll add it into /etc/rc.local. To do that: gksudo gedit /etc/rc.local and add, before exit 0, the following line (without quotes "): "echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode"

After rebooting, the module will be loaded and will start controlling the fan. Enjoy silent operation![/INDENT]



HELLO!

i hope you can help me.. i tried the suggested method with my acer 1410 but it does not work.the reason therefore is that there does not exist a directory called "thermal_zone0" on my system!

under the subtree of /sys/class/thermal i just have "cooling_device0" and "cooling_device1" but no "mode" file which i could "enable"!

the fan therefore does not change.

also i realized that the fan is just loud as long as the notebook is on the line. as soon as i plug it off, and it goes to battery, the fan gets slower and more silent.

however i would like to have the possibility to change the fan speed as you said.. 

hope someone can tell me where the directory and the file "mode" went to.

system: ubuntu 9.10 karmic koala
kernel: 2.6.31-15-generic

thank you very much for your help!

greetings,

mario

---

### Post by PatrickVogeli on 2009-12-01
hi, 

after booting do the following:

```

cd
sudo modprobe acerhdf
dmesg > dmesg.log

```

After doing that, you'll find a file called dmesg.log in your home, please attach that here.

---

### Post by the666pack on 2009-12-02
hey thanks for your fast reply!


the problem is when i do "sudo modprobe acerhdf" i get the error:

FATAL: Error inserting acerhdf (/lib/modules/2.6.31-15-generic/kernel/drivers/platform/x86/acerhdf.ko): No such device


after all i did compile the acerhdf and the file also exists in the stated directory!

so i dont understand why i cannot insert it into the kernel.

any help is highly appreciated,

thank you very much,

greetings,

mario

---

### Post by PatrickVogeli on 2009-12-02
after doing the modprobe acerhdf, you have to do dmesg and post the output here. Without the output of dmesg, I can't help ;)

---

### Post by the666pack on 2009-12-02
hello,

ok sorry so here the output of "tail dmesg" after the modprobe command:

[  563.500145] wlan0: RX AssocResp from 00:12:80:e1:93:83 (capab=0x421 status=0 aid=6)
[  563.500151] wlan0: associated
[  570.100129] wlan0: no probe response from AP 00:12:80:e1:93:83 - disassociating
[  571.322869] wlan0: authenticate with AP 00:12:80:e1:93:83
[  571.400174] wlan0: authenticated
[  571.400180] wlan0: associate with AP 00:12:80:e1:93:83
[  571.500173] wlan0: RX ReassocResp from 00:12:80:e1:93:83 (capab=0x421 status=0 aid=6)
[  571.500179] wlan0: associated
[  589.825504] acerhdf: Acer Aspire One Fan driver, v.0.5.20
[  589.825514] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 1410/v0.3115, please report, aborting!


it seems to have something to do with the actual version of my bios?

anyway, thank you for helping,

greetings,

mario.

---

### Post by PatrickVogeli on 2009-12-02
Hi, yeah, you are right: your bios version is different from the deffined ones. I don't know if your bios version will work (I'm nearly sure it will, though) but you can try:
Add the following into the acerhdf file:

{"Acer", "Aspire 1410", "v0.3115", 0x55, 0x58, {0x9e, 0x9e, 0x00} },

and then rebuild the module again (make clean, make, sudo make install) and the you can modprobe it and it should report no errors. Maybe a reboot is necessary. Then you can enable it.

Now it works?

---

### Post by the666pack on 2009-12-02
hey thank you man,

YOU MADE MY DAY! :popcorn:

worked and enjoying my netbook much more now!

thanks again.. 

long live the community :guitar:

greetings,

mario

---

### Post by captive on 2009-12-03
Hi,
I'm using your howto on my 1810tz, everything works fine except for the "15_saving" script.
The problem is that it is not invoked wher ac power is disconnected, but it is on ac power connection. I noticed that when I plug off the cable  the battery icon (and its status) change for a few second to fully charged/on ac power (ie a fully charged battery with a thunderbolt on it), then switches to discarging.
May this be an acpi related bug?

edit: this happens on karmic i386 with pae-kernel

---

### Post by PatrickVogeli on 2009-12-03
I think this isn't an acpi bug, or at least not a blocker, since that happens to me too and the scripts work fine. 

Is the script invoked when you are on battery and connect AC?

What happens when you start on battery power?

You can do something really simple to check if it's working and/or when, change the script to the following:

```

#!/bin/sh

/usr/bin/touch /home/YOUR_USER_NAME_HERE/Desktop/script_executed

if on_ac_power; 

/usr/bin/echo "ON AC - $(date)" >> /home/YOUR_USER_NAME_HERE/Desktop/script_executed

else # Save power

/usr/bin/echo "ON BAT - $(date)" >> /home/YOUR_USER_NAME_HERE/Desktop/script_executed

fi

```

After saving the file, unplug or plug AC and check if the file script_executed is being created and if has the expected contents.

You could also try renaming it to 10_saving, there's where I have it.

Make sure the script is executable.

Let's see what we get from that..

---

### Post by the666pack on 2009-12-12
hello,

for me the same happens. script 15_saving is not executed.

also with the follow up script that you proposed, no "script_executed" file is created in the Desktop folder of my user.

thanks for any help,

greetings,

mario

---

### Post by PatrickVogeli on 2009-12-13
I've check and it surely works. Strange..

Could you do check the output of acpi -V both on battery and on AC?

---

### Post by managementboy on 2009-12-14
I finally got the mic to work with my new 1810tz but, only as a work around. I installed the backports package and rebooted. The mic only works if you move the audio output slider all the way to the left or the right. This makes the sound output "mono" and the mic works. If you move the slider slightly to the middle, the mic stops working and you only get noise from the mic.

Does someone know how to fix this? I would love to be able to use the stereo speakers when talking on skype...

---

### Post by originalmike on 2009-12-15
Do you think I can use these tips for my acer timeline 4810TG too?

---

### Post by PatrickVogeli on 2009-12-17
Hi there,

yeah, of course you can. Some things, as fan or mic fixes may be won't work, but it is worth trying.

---

### Post by Venetazzo on 2009-12-18
hi 
any news about su4100 undervolting?

---

### Post by defreng on 2009-12-18
does anybody has an idea how to make the 3G Killswitch working? Pressing it logs 

[15346.153485] atkbd.c: Unknown key pressed (translated set 2, code 0xc4 on isa0060/serio0).
[15346.153491] atkbd.c: Use 'setkeycodes e044 <keycode>' to make it known.

in dmesg

---

### Post by jshane on 2009-12-20
@managementboy
very interesting.  I was having trouble getting the internal mic to work with Skype when I read you post.  I tried moving the output all the way to one side and it works.  Strange thing, to me anyway, is that the mic works fine under Sound Recorder with output set in the middle.  In my case it's only been with Skype that I've needed to move the output slider to one side or the other.  Like you I'd rather be able to use both speakers when talking on Skype but at least it works now.

---

### Post by akannankeril on 2009-12-21
hello, i am having issues with my aspire 4736 and wondering if any one could help me out. i am new to ubuntu 9.10 (i have a KDE desktop)
[HTML]internal mic[/HTML] not working. i have downloaded latest (i believe) realtek driver for linux but i dont know how to install...
my [PHP]screen brightness[/PHP] doesnot work.. its at full brightness!!

can any one help me pleaase?

thank you

---

### Post by the666pack on 2009-12-21
> **PatrickVogeli said:**
> I've check and it surely works. Strange..

Could you do check the output of acpi -V both on battery and on AC?

hello,

thanks for your reply.

i realized the script seems to be executed at startup because then i have the file on my desktop (however, it is empty).

nevertheless, here the data

(battery):
scotty@DWARF:~$ acpi -V
Battery 0: Discharging, 75%, 03:15:08 remaining
Battery 0: design capacity 4400 mAh, last full capacity 4301 mAh = 97%
Adapter 0: off-line
Cooling 0: acerhdf no state information available
Cooling 1: acerhdf-fan 0 of 1
Cooling 2: LCD 0 of 9
Cooling 3: Processor 0 of 7

(AC):
scotty@DWARF:~$ acpi -V
Battery 0: Charging, 75%, 00:00:58 until charged
Battery 0: design capacity 4400 mAh, last full capacity 4301 mAh = 97%
Adapter 0: on-line
Cooling 0: acerhdf no state information available
Cooling 1: acerhdf-fan 0 of 1
Cooling 2: LCD 0 of 9
Cooling 3: Processor 0 of 7


thanks for helping!

cheers,

mario

---

### Post by omne on 2009-12-23
Hello, 
I&#8217;m the owner of the PackardBell dot/mu 020.
All the isue describe here seem&#8217;s the same than mine. Especially the fan control who is realy terrible*!
Do you think I can use your tips ? What is the max température for such a processor*?

[EDIT] :*I tried acerhdf (last version is 0.5.22, you should change it in the first post) and it works great but only when I&#8217;m on battery, nothing change when I&#8217;m on ACPower.

Last question*:*my bios is a v0.3108. Do I need to update it ? Do you know how to upgrade it under linux (i don&#8217;t have windows at all)*? I search a lot but no result, I&#8217;ll be able to catch a update bios for this computer but a windows Vista installer :(
Do you think I can use an acer one ? How*?
Sorry for all this questions but it&#8217;s the first place I found on the net where I can find help.

Regards,
Olivier.

---

### Post by cong06 on 2009-12-24
The script also isn't running for me. I've messed around with several directories in the hopes that I would find one that is actually used:
```

/etc/pm/sleep.d
/etc/pm/power.d
/etc/power/scripts.d
/etc/power/event.d
/usr/lib/pm-utils/power.d
/usr/lib/pm-utils/sleep.d

```
I also went ahead and made the folders
```

/etc/acpi/battery.d
/etc/acpi/ac.d

```
and put my script in there.

My script is set to dump a file in my home dir so I know that it's been run. It hasn't yet. I unplugged and re-plugged my laptop, and the gui displays, showing that it knows the battery state has changed, but the script doesn't run.

(Plugged in)
```

root@phaff:~# acpi -V
Battery 0: Charging, 29%, 02:50:50 until charged
Battery 0: design capacity 4387 mAh, last full capacity 4169 mAh = 95%
Adapter 0: on-line
Thermal 0: ok, 53.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 92.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 82.0 degrees C
Cooling 0: Processor 0 of 7

```
(On Battery)
```

root@phaff:~# acpi -V
Battery 0: Discharging, 29%, 01:10:16 remaining
Battery 0: design capacity 4387 mAh, last full capacity 4169 mAh = 95%
Adapter 0: off-line
Thermal 0: ok, 53.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 92.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 82.0 degrees C
Cooling 0: Processor 0 of 7 

```

---

### Post by omne on 2009-12-24
> **cong06 said:**
> The script also isn't running for me. 
[…]
My script is set to dump a file in my home dir so I know that it's been run. It hasn't yet. I unplugged and re-plugged my laptop, and the gui displays, showing that it knows the battery state has changed, but the script doesn't run.


Can you show us your script ? I’d like to have a dump in order to know if the script run here.

A notice one thing, if I do a :
```
sudo echo 10 > /sys/module/snd_hda_intel/parameters/power_save
```
in my terminal, it return me an error. Is this normal ? Is there something I can do to see the output of the script ?

(Happy Christmas everybody !)

---

### Post by cong06 on 2009-12-24
> **omne said:**
> Can you show us your script ? I’d like to have a dump in order to know if the script run here.

It doesn't need to be too complicated. Something like this:
```
date >> /home/cong06/dump
```
was all I used.

Maybe I'll change it later though, to do this:
```
echo "`date +"%b %d %H:%M:%S"` $HOSTNAME $0 just ran" >> /var/log/messages
```
Basically dumping a properly formmatted "message" log line, kinda like this:
```
Dec 24 13:47:39 phaff /etc/script/path just ran
```

---

### Post by omne on 2009-12-24
> **cong06 said:**
> 
Maybe I'll change it later though, to do this:
```
echo "`date +"%b %d %H:%M:%S"` $HOSTNAME $0 just ran" >> /var/log/messages
```

Ok, I added 
```

echo "`date +"%b %d %H:%M:%S"` $HOSTNAME $0 just ran AC power" >> /home/nemo/dump

```
At the end of the AC power part
and the same with battery in the battery part.
And I don’t even have a « dump » file created in my home. Sad.

The battery icon refrech well.
Do you uncomment the wifi part*? I did it, after installing the last proposed modules from ubuntu.

---

### Post by asme on 2009-12-24
Hi ive tried ur tips and most of them are working well for me. only with the after the fan issue (wich solves the problem oft the loud fan) the left side of my netbook is too hot for my sense. any idea?
thx and merry xmas

---

### Post by n4txo on 2009-12-26
Hi!

I have a new Aspire 1810TZ, i made all the modifications but when i made the "sudo modprobe acerhdf" it returns:

```
.../acerhdf_kmod$ sudo modprobe acerhdf 
FATAL: Error inserting acerhdf (/lib/modules/2.6.31-16-generic/kernel/drivers/platform/x86/acerhdf.ko): No such device
```

The out of the dmesg 

```
[ 1689.601122] acerhdf: Acer Aspire One Fan driver, v.0.5.21
[ 1689.601132] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 1810TZ/v0.3115, please report, aborting!
[ 1768.412328] acerhdf: Acer Aspire One Fan driver, v.0.5.21
[ 1768.412338] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 1810TZ/v0.3115, please report, aborting!
[ 2814.750949] acerhdf: Acer Aspire One Fan driver, v.0.5.21
[ 2814.750960] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 1810TZ/v0.3115, please report, aborting!
[ 3116.541381] acerhdf: Acer Aspire One Fan driver, v.0.5.21
[ 3116.541391] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 1810TZ/v0.3115, please report, aborting!

```

what could i make?


thanks and merry christmas =D

---

### Post by omne on 2009-12-27
> **n4txo said:**
> Hi!

I have a new Aspire 1810TZ, i made all the modifications but when i made the "sudo modprobe acerhdf" it returns:

```
.../acerhdf_kmod$ sudo modprobe acerhdf 
FATAL: Error inserting acerhdf (/lib/modules/2.6.31-16-generic/kernel/drivers/platform/x86/acerhdf.ko): No such device
```

Did you modify the source code of acerhdf to fit your bios as explain in the first post ? You should allso go here*:*[http://www.piie.net/index.php?section=acerhdf](http://www.piie.net/index.php?section=acerhdf) and take the last reales : 0.5.22 (not 0.5.21).

---

### Post by omne on 2009-12-27
Ok, I’ll be able to have the script to run. I found the solution in the Netbook Review forum here :*[http://forum.notebookreview.com/showthread.php?t=434638](http://forum.notebookreview.com/showthread.php?t=434638) (this post : [http://forum.notebookreview.com/showpost.php?p=5594541&postcount=35](http://forum.notebookreview.com/showpost.php?p=5594541&postcount=35))

It seem’s that when one running gnome, the /etc/acpi/power.sh unable all power scripts other than gnome-power.
The solution is to comment the /etc/acpi/power.sh like this*:
```

#!/bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

# . /usr/share/acpi-support/policy-funcs

# if [ -z "$*" ] && [ `CheckPolicy` = 0 ]; then
# exit;
# fi

pm-powersave $*

```

There’s a bug repost here*: [https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/387057](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/387057)

In this thread you can although find a script to check if the script work (didn’t test it yet since I’m not on this forum).

---

### Post by PatrickVogeli on 2009-12-27
Hi there,

sorry for not coming back earlier. As many of you have reported, the script doesn't seem to execute properly, and this is because of the ubuntu kernel. I've been running some custom compiled .31 kernels and all have run fine. My personal guess, is it could be wmi related, the acer-wmi is built as a module and can be blacklisted, but wmi is built into the kernel. It should do no harm, but it seems it does. Not sure why, though.

For the ones who are having troubles with acerhdf, keep in mind the acerhdf that ships with ubuntu won't work, since it lacks definitions for the 1810 and most 1410. Just follow the fan steps carefully, it's just download the acerhdf sources, edit the .c files and make and install as written. It's not hard. If it's not working, it's because of your bios version, do the mod as explained and it will work.

Patrick

---

### Post by PatrickVogeli on 2009-12-27
> **n4txo said:**
> Hi!

I have a new Aspire 1810TZ, i made all the modifications but when i made the "sudo modprobe acerhdf" it returns:

```
.../acerhdf_kmod$ sudo modprobe acerhdf 
FATAL: Error inserting acerhdf (/lib/modules/2.6.31-16-generic/kernel/drivers/platform/x86/acerhdf.ko): No such device
```

The out of the dmesg 

```
[ 1689.601122] acerhdf: Acer Aspire One Fan driver, v.0.5.21
[ 1689.601132] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 1810TZ/v0.3115, please report, aborting!
[ 1768.412328] acerhdf: Acer Aspire One Fan driver, v.0.5.21
[ 1768.412338] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 1810TZ/v0.3115, please report, aborting!
[ 2814.750949] acerhdf: Acer Aspire One Fan driver, v.0.5.21
[ 2814.750960] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 1810TZ/v0.3115, please report, aborting!
[ 3116.541381] acerhdf: Acer Aspire One Fan driver, v.0.5.21
[ 3116.541391] acerhdf: unknown (unsupported) BIOS version Acer/Aspire 1810TZ/v0.3115, please report, aborting!

```

what could i make?


thanks and merry christmas =D

Hi,

as omne already said, it seems you haven't edited the .c file as instructed in the first post. It will work after adding 
```

{"Acer", "Aspire 1810TZ", "v0.3115", 0x55, 0x58, {0x9e, 0x9e, 0x00} },

```
to the acerhdf.c file and then compile and install the module again. After that it should work. Please see first post.

---

### Post by PatrickVogeli on 2009-12-27
Hi all, I might have a solution for the  script not executing: 

gksudo gedit /etc/acpi/power.sh

and there, **below** **"**#!/bin/sh**"** and **above** **"**test -f /usr/share/acpi-support/key-constants || exit 0**"** put the script location. For example: /etc/pm/slee.d/15_saving

Then, save and close and the script should start executing properly.

Can someone confirm that?

I attach the CheckPowerSaving script, unzip it, make it executable (chmod +x CheckPowerSaving.sh) and then, in a terminal, run it: ./CheckPowerSaving.sh

That will output some info about the powersaving features active. If you want, you can save it into a file, by doing: ./CheckPowerSaving.sh > PowerSave.log.

---

### Post by cong06 on 2009-12-28
> **PatrickVogeli said:**
> Hi all, I might have a solution for the  script not executing: 

gksudo gedit /etc/acpi/power.sh

and there, **below** **"**#!/bin/sh**"** and **above** **"**test -f /usr/share/acpi-support/key-constants || exit 0**"** put the script location. For example: /etc/pm/slee.d/15_saving

Then, save and close and the script should start executing properly.

Can someone confirm that?

I attach the CheckPowerSaving script, unzip it, make it executable (chmod +x CheckPowerSaving.sh) and then, in a terminal, run it: ./CheckPowerSaving.sh

That will output some info about the powersaving features active. If you want, you can save it into a file, by doing: ./CheckPowerSaving.sh > PowerSave.log.


Thanks! That helped me figure out what exactly's going on.
A better fix (in my opion) is to comment out those lines before:
```

pm-powersave $*

```

It seems to me that the script is looking for a file, and if it doesn't find it, it exits. Maybe this file comes with acpi-support, but I'm  trying to keep as few power saving tools installed so they don't interfere with each other.

When pm-powersave is run, it runs the files in /usr/lib/pm-utils/ and /etc/pm/
You can even use a true or false passed from pm-powersave (like suggested in the script here: [https://help.ubuntu.com/community/PowerManagement/ReducedPower#Using%20less%20power%20with%20pm-powersave](https://help.ubuntu.com/community/PowerManagement/ReducedPower#Using%20less%20power%20with%20pm-powersave)) to remove dependence on the "on_ac_power" that some people said they were having problems with.

Thanks again. Good find.

Edit: In my opinion this is how it should work, but... it doesn't actually work. The "fix" was found while installing 9.10 over top of 9.04. On a reformat the "fix" failed.
Also, you need acpi-support.

---

### Post by omne on 2009-12-28
But the purpose of this power.sh script is not crazy. In the tuto of the first post, I’m not shure that it’s a good idear to set disk power managment both in the script and in the gnome-power interface.

---

### Post by PatrickVogeli on 2009-12-28
> **cong06 said:**
> Thanks! That helped me figure out what exactly's going on.
A better fix (in my opion) is to comment out those lines before:
```

pm-powersave $*

```

It seems to me that the script is looking for a file, and if it doesn't find it, it exits. Maybe this file comes with acpi-support, but I'm  trying to keep as few power saving tools installed so they don't interfere with each other.

When pm-powersave is run, it runs the files in /usr/lib/pm-utils/ and /etc/pm/
You can even use a true or false passed from pm-powersave (like suggested in the script here: [https://help.ubuntu.com/community/PowerManagement/ReducedPower#Using%20less%20power%20with%20pm-powersave](https://help.ubuntu.com/community/PowerManagement/ReducedPower#Using%20less%20power%20with%20pm-powersave)) to remove dependence on the "on_ac_power" that some people said they were having problems with.

Thanks again. Good find.
the problem with commenting out the lines above pm-powersave is that some user over at notebookreviews forum said the g-p-m would randomly misbehave. 

Ubuntu put that lines because of something, so I'd prefer to leave that untouched. Also, nobody seems to clearly understand what they do, so..

I know the fix is not pretty or whatever, but it seems to work and doesn't break anything (at least, I haven't seen anything breaking).

As for interefere... yeah, I agree. But the standard ubuntu install should be ok.

---

### Post by PatrickVogeli on 2009-12-28
> **omne said:**
> But the purpose of this power.sh script is not crazy. In the tuto of the first post, I’m not shure that it’s a good idear to set disk power managment both in the script and in the gnome-power interface.

In the fist post of this thread, you aren't setting the disk power management. You only remount and change some filesystem options, which should make less read/write accesses to the disk.

I had some hdparm command before, but in Karmic I've removed it, because of g-p-m having that functionaly.

---

### Post by QoSyS on 2009-12-29
Acer 1810T, Bios v0.3113

To compile acerhdf i used this line :
{"Acer", "Aspire 1810T", "v0.3113", 0x55, 0x58, {0x9e, 0x9e, 0x00} },

but 
> 
# modprobe acerhdf
FATAL: Error inserting acerhdf (/lib/modules/2.6.31.6-desktop-1mnb/kernel/drivers/platform/x86/acerhdf.ko.gz): No such device


and dmesq is empty :
> 
acerhdf: Acer Aspire One Fan driver, v.0.5.13
acerhdf: no Aspire One hardware found


How can i solve this?

---

### Post by QoSyS on 2009-12-29
Solved this by removing old **acerhdf.ko.gz** and modprobing again. thanx caps!

---

### Post by beauman on 2009-12-29
Hi! Partly based on this thread, I created a wiki for the 1810TZ. You are very welcome to expand it! 

[Aspire1810TZ/Karmic]("https://help.ubuntu.com/community/Aspire1810TZ/Karmic")

---

### Post by omne on 2009-12-29
> **PatrickVogeli said:**
> 
I had some hdparm command before, but in Karmic I've removed it, because of g-p-m having that functionaly.

Ok, great. Since some people don't use gnome (but xfce, or awesome, for exemple) would'nt it be great to have them in the script, commented by default?

---

### Post by free-martin on 2009-12-29
> **PatrickVogeli said:**
> 
**Next to be done:**
- Enable undervolting


Hmmmm, I think on another forum I saw a post of you stating that you are running an undervolted kernel:

> 
- Custom 2.6.31.5 kernel with PHC undervolting enabled, and quite stripped down without unnecessary things (at least for me )

Maybe you could post the voltage-values you use, so that we have a first guess.

Thx for your tips and scripts,
martin

---

### Post by PatrickVogeli on 2009-12-29
the voltajes I'm using are the lowest possible in the SU4100: 0,9250 V. That's 17 as vids using the phc extensions.

With my girlfriend's SU3500 I can go down to 0,8750 V, thats 13 if I remember correctly.

---

### Post by free-martin on 2009-12-29
> **PatrickVogeli said:**
> the voltajes I'm using are the lowest possible in the SU4100: 0,9250 V. That's 17 as vids using the phc extensions.

With my girlfriend's SU3500 I can go down to 0,8750 V, thats 13 if I remember correctly.

gracias, think I'm trying vid 13 on su7300.
strange though, that the fids are not in order in phc_controls:
70:25 6:15 136:13
:confused:

---

### Post by free-martin on 2009-12-29
> **free-martin said:**
> gracias, think I'm trying vid 13 on su7300.
strange though, that the fids are not in order in phc_controls:
70:25 6:15 136:13
:confused:

13 - so far without any issues, thx again @ Patrick!

---

### Post by ontwerp on 2010-01-03
Any luck getting the right Acer 1820ptz codes? As 1810tz is really close to my future specs... My acer 1820ptz is mine really close and I want to install ubuntu 9.10 full blown...

---

### Post by cong06 on 2010-01-04
> **PatrickVogeli said:**
> the problem with commenting out the lines above pm-powersave is that some user over at notebookreviews forum said the g-p-m would randomly misbehave. 

Ubuntu put that lines because of something, so I'd prefer to leave that untouched. Also, nobody seems to clearly understand what they do, so..

I know the fix is not pretty or whatever, but it seems to work and doesn't break anything (at least, I haven't seen anything breaking).

As for interefere... yeah, I agree. But the standard ubuntu install should be ok.

well, actually. It turns out that the reason it worked for me was something screwy... probably related to doing a 9.04 > 9.10 upgrade.

When I did a full blown install, It failed for me, and I was forced to revert to your fix anyway. It seems pm-powersave isn't working.

Those lines I commented out were related to "acpi-support" which I had uninstalled because I didn't really want to use it, since I thought it was interfering with what I had already set up. It turns out it's acpi-support that actually does the toggling...

---

### Post by Milan Knizek on 2010-01-08
Thanks all for the summary of hints for Ubuntu 9.10 and Acer 1810TZ, it saved me lot of time.

Just two hint:

My notebook came with older BIOS (I do not recall its version now) and while installation looked as being completed okay, the computer just loaded the initrd and then froze (debug displayed errors with SATA disk). Switching to IDE instead of AHCI in BIOS helped, but then the pre-installed MS Windows 7 Home did not boot at all.

Updating BIOS to the most recent version 1.3303 solved the problem and both systems can run with AHCI disk mode now.


Second topic is wifi: while with some APs it works just fine, with others it repeatedly fails:
```

Jan  8 08:22:29 1810tz kernel: [ 1547.860439] wlan0: disassociated from 00:4f:62:1d:d1:01 (Reason: 14)
Jan  8 08:22:29 1810tz wpa_supplicant[1092]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 08:22:29 1810tz wpa_supplicant[1092]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  8 08:22:29 1810tz NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Jan  8 08:22:29 1810tz kernel: [ 1547.890212] wlan0: deauthenticating from 00:4f:62:1d:d1:01 by local choice (reason=3)
Jan  8 08:22:30 1810tz NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  8 08:22:30 1810tz wpa_supplicant[1092]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 08:22:30 1810tz wpa_supplicant[1092]: Trying to associate with 00:4f:62:1d:d1:01 (SSID='garagome' freq=2412 MHz)
Jan  8 08:22:30 1810tz NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan  8 08:22:30 1810tz kernel: [ 1548.414082] wlan0: direct probe to AP 00:4f:62:1d:d1:01 (try 1)
Jan  8 08:22:30 1810tz kernel: [ 1548.416887] wlan0: direct probe responded
Jan  8 08:22:30 1810tz kernel: [ 1548.416892] wlan0: authenticate with AP 00:4f:62:1d:d1:01 (try 1)
Jan  8 08:22:30 1810tz kernel: [ 1548.418798] wlan0: authenticated
Jan  8 08:22:30 1810tz kernel: [ 1548.418818] wlan0: associate with AP 00:4f:62:1d:d1:01 (try 1)
Jan  8 08:22:30 1810tz kernel: [ 1548.420966] wlan0: RX ReassocResp from 00:4f:62:1d:d1:01 (capab=0x411 status=12 aid=1)
Jan  8 08:22:30 1810tz kernel: [ 1548.420971] wlan0: AP denied association (code=12)
Jan  8 08:22:30 1810tz kernel: [ 1548.420986] wlan0: associate with AP 00:4f:62:1d:d1:01 (try 1)
Jan  8 08:22:30 1810tz kernel: [ 1548.423236] wlan0: RX ReassocResp from 00:4f:62:1d:d1:01 (capab=0x411 status=12 aid=1)
Jan  8 08:22:30 1810tz kernel: [ 1548.423240] wlan0: AP denied association (code=12)
Jan  8 08:22:30 1810tz kernel: [ 1548.423253] wlan0: deauthenticating from 00:4f:62:1d:d1:01 by local choice (reason=3)
Jan  8 08:22:34 1810tz NetworkManager: <debug> [1262935354.000568] periodic_update(): Roamed from BSSID 00:4F:62:1D:D1:01 (garagome) to (none) ((none))
Jan  8 08:22:40 1810tz wpa_supplicant[1092]: Authentication with 00:4f:62:1d:d1:01 timed out.
Jan  8 08:22:40 1810tz NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan  8 08:22:40 1810tz NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan  8 08:22:40 1810tz wpa_supplicant[1092]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 08:22:40 1810tz wpa_supplicant[1092]: Trying to associate with 00:4f:62:1d:d1:01 (SSID='garagome' freq=2412 MHz)
Jan  8 08:22:40 1810tz NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
```
Updating wireless modules (neither from backports or compiling ourself) did not help, just made the connection last a bit longer (about half a minute).
The trouble seems to be with NetworkManager's scanning wireless networks -- replacing it with wicd helped a lot, now the connection drops once in 15 minutes or so.

*It may be good to note this on the first post of this thread.*

---

### Post by beauman on 2010-01-09
> **Milan Knizek said:**
> Thanks all for the summary of hints for Ubuntu 9.10 and Acer 1810TZ, it saved me lot of time.



Thanks for contributing to the wiki! I hope more people would dare to touch it! Some sections still have to written, like using an external monitor.

An other thing:
At the [AspireOne Wiki]("https://help.ubuntu.com/community/AspireOne/Ubuntu9.10"), the problem with the fan is solved in a different way. Do you think, this way could also be applied to the 1810t(z)?  It allows to set the temperature hysteresis. Some people complained about getting their hw too hot...

---

### Post by Milan Knizek on 2010-01-09
> **beauman said:**
> An other thing:
At the [AspireOne Wiki]("https://help.ubuntu.com/community/AspireOne/Ubuntu9.10"), the problem with the fan is solved in a different way. Do you think, this way could also be applied to the 1810t(z)?  It allows to set the temperature hysteresis. Some people complained about getting their hw too hot...
Seems to work for 1810TZ, leaving the default values of 65° C to turn fan on almost made my notebook a cooker :-)

---

### Post by stillnotcool on 2010-01-14
Hi everyone,

I've just finished installing Karmic on my new Aspire 1410, and I'm experiencing abnormally slow boot times.  I've used a very unscientific method for clocking my machine's boot sequence: pressing "start" on a stopwatch as I hit the computer's power button.  According to my timer, the boot sequence takes more than a minute!

Most of this time is spent "before" the first splash screen (the pulsating logo), where a cursor at the top of the screen just blinks.  When the pulsating logo loads, the computer stalls for a while, then reveals the blinking cursor again, then moves into the second boot screen.

I've noticed that this long boot time does not occur when I'm booting into my Karmic Live CD (which I'm actually using via flash drive, thanks to UNetbootin) and the hard disk is formatted as "Free Space."  It only occurs when I try to boot into Ubuntu from the computer's hard disk (even the first boot on a fresh install).  After Ubuntu is loaded onto the hard drive, I even experience these long load times when booting to my USB flash drive again.

Can anyone offer help with these issues?  The wait is interminable.  Thanks!

---

### Post by Milan Knizek on 2010-01-15
> **SemioticRobotic said:**
> 
I've noticed that this long boot time does not occur when I'm booting into my Karmic Live CD (which I'm actually using via flash drive, thanks to UNetbootin) and the hard disk is formatted as "Free Space."  It only occurs when I try to boot into Ubuntu from the computer's hard disk (even the first boot on a fresh install).  After Ubuntu is loaded onto the hard drive, I even experience these long load times when booting to my USB flash drive again.

Check the logs.
In grub, press E to edit the boot commands, delete "quiet" and "splash" from the kernel line and add there "debug" instead. Then press ctrl+x to boot and watch the messages.

I would assume these are troubles with AHCI mode for the SATA harddrive. Change in BIOS to IDE compatibility (but then, the MS Windows may not boot). Alternatively, update BIOS to 1.3xxx version. It helped on 1810TZ.

---

### Post by stillnotcool on 2010-01-15
Thanks!  I'll try these suggestions and report my progress.

---

### Post by Milan Knizek on 2010-01-19
On my 1810TZ gnome power manager fails to hibernate the notebook on low battery and just powers off suddenly. The same happens when notebook is suspended to RAM and battery gets empty - the session is lost...

After a quick search on google it turned out a common issue with notebooks.

Workaround which helped: disable "time" counting of remaining battery life and instead use relative measure (percents).

In gconf-editor, select [FONT="Courier New"]apps / gnome-power-manager / general[/FONT] and de-select [FONT="Courier New"]use_time_for_policy[/FONT].

---

### Post by alexander1 on 2010-01-23
Has anyone the 1820ptz and could write a small report what's working and what isn't?
I'm considering to buy it too (and of course put k/ubuntu 9.10 on it) and the report would be really helpful!

Does the pen work? Does multitouch work?

---

### Post by Gemnoc on 2010-02-24
Hey y'all,

I'm just now discovering this thread. I have a Gateway EC1803h, which is a clone of the 11.6" Aspire 1410 first generation. It was sold in Canada from August 2009 to right before the Windows 7 release.

Specs are:
Intel Core 2 Solo SU3500@1.4GHz
3GB RAM, 250GB Hitachi HTS54322 HDD

For almost two weeks I struggled to install Ubuntu Netbook Remix 9.10, first the Beta then the RC. Part of the trouble was dual-boot setup with Vista using EasyBCD. That part got solved when the developer released a version with grub2 and ext4 support.

One thing that is not mentioned here or in **beauman**'s Aspire1810TZ/Karmic wiki: in my case, for UNR to work, I needed to modify grub with option **libata.force=noncq**. I think I found this tip on the AcerAspireTimeline wiki page. I'm curious to know if I'm the only one in this case. And I wonder if it would get solved by updating the BIOS. Mine is pretty old, the problem is Gateway's site doesn't offer BIOS updates. I'm assuming Acer's would be compatible.

---

### Post by PatrickVogeli on 2010-02-25
Hi,

the libata.force=noncq depended on the hard drive it has. When I installed Ubuntu 9.04 on my girfriend's Packard Bell clone, I had to add that line too.

But then I installed Win 7 and updated the Bios (using the latest acer 1410 bios) and after that I installed Ubuntu 9.10 and I hadn't to add the libata quirk anymore. I'd say the Bios update solved, since the problem seemed to be the drive (or the bios) was misdetecting an ncp capable hard drive.

Also.. are you sure you prefer the Netbook remix? I wouldn't say ours is a netbook, but rather an ultraportable notebook. It moves gnome just fine.. fast.

---

### Post by Gemnoc on 2010-02-25
Thanks for the info. I may give the BIOS upgrade a try. I'd like to replace the HDD with a SSD at some time (don't need that much storage), but those still cost way more than what I'm willing to pay.

So you updated the Packard Bell's BIOS with the Acer firmware without trouble then?
> Also.. are you sure you prefer the Netbook remix? I wouldn't say ours is a netbook, but rather an ultraportable notebook. It moves gnome just fine.. fast.
Funny you would ask, I was getting tired of UNR, so today I followed some tips from ohiomoto on another thread and enabled the GNOME desktop, disabled Maximus and replaced the go-home-applet with the Ubuntu principal menu. But I kept UNR's window-switcher-applet, as I think it's better suited to a single panel than the traditional list of windows. This portable may have a bigger screen resolution than a regular netbook, but 1366 pixels in width is still not that much when you're used like me to a 24" 1920x1200 desktop LCD. :P

---

### Post by Lars on 2010-03-10
I tried installing Karmic on my Aspire 1410, and the install went fine..
But the laptop halts on the pulsating logo, and one of the leds start blinking (iirc it's the caps led).. :(

I've tried reinstalling several times, but it's just the same everytime.

I can run the live cd though, so I don't have a clue what's wrong.. :(

(note, I did a dual boot install, because I've also got Win7 on it)

---

### Post by stillnotcool on 2010-03-10
> **Lars said:**
> I tried installing Karmic on my Aspire 1410, and the install went fine..
But the laptop halts on the pulsating logo, and one of the leds start blinking (iirc it's the caps led).. :(

I've tried reinstalling several times, but it's just the same everytime.

I can run the live cd though, so I don't have a clue what's wrong.. :(

(note, I did a dual boot install, because I've also got Win7 on it)

Reading this reminded me that I forgot to report my progress with my own 1410, which was experiencing problems similar to this.  Unfortunately, in my case the symptoms stemmed from a faulty hard disk -- so I wouldn't rule out that possibility when troubleshooting your machine.  However, if you're already successfully running Windows 7, then your problems with Karmic may be something else entirely.

---

### Post by PatrickVogeli on 2010-03-10
the blinking logo problem.. maybe you can boot adding the parameter libata.force=noncq

---

### Post by Lars on 2010-03-11
I tried booting again last night, using the recovery mode.
From what I can tell, it can't mount the filesystem/harddrive partition (ext4), so that's why nothing is working..

But seeing as windows 7 works just fine, and I've tried reformatting the drive every time I tried reinstalling, I'm not sure what goes wrong..

Would it help if I tried to repartition the drive? (ie. give it abit more or less space on sda5)?

---

### Post by Gemnoc on 2010-03-11
Have you tried what PatrickVogeli said?

I had no problem with booting from a Live USB key, but I was getting the same problem as you after the install.

In the Grub menu, with the Ubuntu entry selected, press "e" to enter edit mode; in the edit screen, use the arrow keys to navigate at the end of this line:
```
linux /boot/vmlinuz-2.6.31-20-generic root=UUID=(series of numbers)\(another series of numbers) ro quiet splash
```
Add a space, and this:
```
 libata.force=noncq
```

Then press CTRL+X to boot. (not ESC to return to main menu, as this will discard changes)

This setting will be purged after a reboot, but if it works, we can tell you how to put it permanently into your grub settings.

P.S. Have you installed EasyBCD 2.0 beta in Windows 7 to chain the bootloader to Ubuntu's Grub?

---

### Post by Lars on 2010-03-11
I will try when I get home.. thanks guys.. :)
and no, I haven't installed any other bootloaders..

---

### Post by Lars on 2010-03-11
Wow... it worked.. posting this from Ubuntu now.. :)

now, let's see if I can find a config file for grub...

also.. did I understand correctly that there was a bios update that might make the it run on the normal grub loader?

last thing; what exactly does the added libata.force=noncq mean?

---

### Post by Gemnoc on 2010-03-11
> **Lars said:**
> Wow... it worked.. posting this from Ubuntu now.. :)
Great!!! :D

> now, let's see if I can find a config file for grub...
You have to go in /etc/default and open the file named grub, and put the same command at the end of this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **libata.force=noncq**"
```
Then, in a terminal you have to update Grub by running sudo update-grub.

And you should be set!:)
> also.. did I understand correctly that there was a bios update that might make the it run on the normal grub loader?
Yes. I've been a little afraid of updating mine since this procedure presents some risk. You can download the BIOS update from Acer's website. You have to run it in Windows though.

> last thing; what exactly does the added libata.force=noncq mean?
It deactivates NCQ, which is "[Native Command Queuing]("http://en.wikipedia.org/wiki/NCQ")". It's a technology that speeds up access on SATA drives. For some reason, this function is not supported by the original BIOS on some Acer machines, and Karmic assumes wrongly it does, hence the hang.

---

### Post by Gemnoc on 2010-03-11
> **Lars said:**
> and no, I haven't installed any other bootloaders..
Cool, that means I can avoid using EasyBCD if/when I switch from Vista to Windows 7. I got my upgrade disk a few months ago, but I'm thinking of wiping my drive and installing Ubuntu only when 10.04 comes out. I booted in Vista this week for the first time in 3 months!

---

### Post by Lars on 2010-03-11
You are great, guys.. I'm really thankful for all the help you are giving..

A little update.. I got the usual update instance after running a few minutes... and after the updates, I noticed there was a new kernel version, .30 or something..
And after rebooting using the new kernel update, I didn't need the added noncq command in grub.. it just booted right up.. :)

I'm not sure what's happened in detail, but here's hoping it keeps working!! :D

Cheers.. :)

---

### Post by element42 on 2010-03-21
I've just (succesfully) installed the lucid beta on my new 1810tz. Early days, but everything seems fine, except the wireless light on the front continually blinks on and off (~3 times per second) while I'm connected to my wireless network. Does anyone have any ideas how to stop this? It's quite distracting :neutral:

Incidentally, the newest [acerhdf]("http://www.piie.net/files/acerhdf_kmod-0.5.23.tar.gz") (0.5.23) has definitions for the 1810tz already included.

---

### Post by yelvington on 2010-03-21
> **element42 said:**
> I've just (succesfully) installed the lucid beta on my new 1810tz. Early days, but everything seems fine, except the wireless light on the front continually blinks on and off (~3 times per second) while I'm connected to my wireless network.

Wireless light on my Acer 1410 blinks based on traffic. Is that what you're seeing?

At any rate, I put the Lucid beta on a thumb drive and tried it. Video is disastrously bad; Xorg was using 67% of CPU (dual-core Celeron SU2300). Objects on the screen redrew themselves erratically.

---

### Post by yelvington on 2010-03-21
Ubuntu Lucid Lynx bug filed:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/543808](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/543808)
blinking display, high CPU utilization by xorg

---

### Post by element42 on 2010-03-22
> **yelvington said:**
> Wireless light on my Acer 1410 blinks based on traffic. Is that what you're seeing?No, it just blinks continuously regardless of usage. I've seen some a bug report about this in launchpad with some other laptops so now I think it's a known issue...

---

### Post by ohiomoto on 2010-03-24
2 things with Ubuntu on my 1410.

1)  Ubuntu does a crappy job handling my hidden network.  Sometimes it connects fairly fast but most of the times it either takes too long or doesn't find it all all.

2)  The lid can hit the space bar on the keyboard causing the computer to resume from suspend: [http://forum.notebookreview.com/showthread.php?t=470111](http://forum.notebookreview.com/showthread.php?t=470111)  Is there a way to keep the keyboard form waking the system? 

Thanks in advance.

---

### Post by miegiel on 2010-03-24
> **ohiomoto said:**
> 2 things with Ubuntu on my 1410.

1)  Ubuntu does a crappy job handling my hidden network.  Sometimes it connects fairly fast but most of the times it either takes too long or doesn't find it all all.

2)  The lid can hit the space bar on the keyboard causing the computer to resume from suspend: [http://forum.notebookreview.com/showthread.php?t=470111](http://forum.notebookreview.com/showthread.php?t=470111)  Is there a way to keep the keyboard form waking the system? 

Thanks in advance.

[LIST=1]
[*]On my 3810T wifi has improved in lucid. In karmic there should be a *linux-backports-modules.....* package for wifi that might improve your connection. Try entering ```
sudo apt-get -s install linux-backports-modules
``` in a terminal and hitting the ***Tab*** key a couple of times (lists a *linux-backports-modules-wireless-lucid-generic* here in lucid).
[*]That's a common problem, especially with thin laptops. If you're going to put your laptop in a bag you really shouldn't use suspend and hibernate or shutdown instead. Though I would appreciate knowing how to wake from suspend with a tap on the touchpad or key combination instead of the spacebar.
[/LIST]

---

### Post by ohiomoto on 2010-03-25
Thanks.  I already have backports installed.  Wifi works great, it just doesn't handle hidden networks very well, even if that hidden connection is the only one I have saved.

---

### Post by blackomegax on 2010-03-25
For the video issue in 10.04

set i915.modeset=0 in grub.

---

### Post by blackomegax on 2010-03-25
Also, possible bug.
on 802.11n networks with 10.04 beta1, with wifi power save on, browsing the internet is dead slow.
10-20 seconds lag time to start loading each page, then fast load, rinse, repeat for each link. (it's almost as if powersave knocks the connection out and it has to auth, dhcp, and reroute everything anytime there is traffic)

11g networks perform fine.

---

### Post by omne on 2010-03-30
Under lucid lynx, my computer don&#8217;t go to sleep when I close the screen. The strange thing is that I can sleep it with the session menu&#8230;

Other thing, I used to launch this command to have two finger defil at  boot*: ```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 40 
```
It don&#8217;t work under lucid with this error*:

```
unable to find device SynPS/2 Synaptics TouchPad
```
Strange too because ```
xinput list
``` show me*: 

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; "SynPS/2 Synaptics TouchPad"            	id=12	[slave  pointer  (2)]
&#9116;   &#8627; "Macintosh mouse button emulation"      	id=13	[slave  pointer  (2)]

```

So I don&#8217;t understand where the problem is.

---

### Post by miegiel on 2010-03-30
> **omne said:**
> Under lucid lynx, my computer don’t go to sleep when I close the screen. The strange thing is that I can sleep it with the session menu…

Other thing, I used to launch this command to have two finger defil at  boot*: ```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 40 
```
It don’t work under lucid with this error*:

```
unable to find device SynPS/2 Synaptics TouchPad
```
Strange too because ```
xinput list
``` show me*: 

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; "SynPS/2 Synaptics TouchPad"            	id=12	[slave  pointer  (2)]
&#9116;   &#8627; "Macintosh mouse button emulation"      	id=13	[slave  pointer  (2)]

```

So I don’t understand where the problem is.

try :
```
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 40
```
also see : [http://ubuntuforums.org/showthread.php?t=1419833](http://ubuntuforums.org/showthread.php?t=1419833)

---

### Post by omne on 2010-03-30
> **miegiel said:**
> try :
```
xinput --set-prop --type=int --format=32 '"SynPS/2 Synaptics TouchPad"' "Synaptics Two-Finger Pressure" 40
```
also see : [http://ubuntuforums.org/showthread.php?t=1419833](http://ubuntuforums.org/showthread.php?t=1419833)

Thank’s a lot.
I used the scipt in the link, seems to work great. I need to solve the hibernate problem, now…

---

### Post by kwstas on 2010-03-31
hi guys,

very useful post patrick even though i'm on an acer 4810t.

i wonder if i could use somehow your script below as an on/off switch and place it on my desktop.
is it possible?

 
     ```
#!/bin/sh
  # Make sure brightness switch enabled stays on N, even on resume.
  echo N > /sys/module/video/parameters/brightness_switch_enabled
  # Disable wake on lan
  ethtool -s eth0 wol d

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then
  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds. This reduces disk activity.
  mount -o remount,commit=5,atime,diratime /
  mount -o remount,commit=5,atime,diratime /home

  # Set SATA back to normal operation
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo max_performance > $foo;
  done

  # Manually set the wifi driver to no power savings.
  # broken in 2.6.31 kernel
  # iwconfig wlan0 power off

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 600 > /proc/sys/vm/dirty_writeback_centisecs 

  # Disable Intel HD audio power saving:
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save

else # Save power
  
  # Change the ext3 commit times to 10 minutes.  Reduces disk activity
  # disable disk writes when reading
  mount -o remount,commit=600,noatime,nodiratime /
  mount -o remount,commit=600,noatime,nodiratime /home
  
  # Set SATA to save power
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo min_power > $foo;
  done

  # Manually set the iwl3945 driver to power savings.
  # broken in 2.6.31 kernel
  # iwconfig wlan0 power on

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Enable Intel HD audio power saving:
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
fi
```

---

### Post by ebro173 on 2010-04-02
Great info here.  I recently got an Acer Aspire 1410.  

CPU is Intel Celeron 743.  
Graphics Card is Intel GMA 4500MHD.  
2GB RAM.  
250GB HD. 
Windows 7
BIOS 0.3113

I'm running Ubuntu Netbook Remix on it from a usb drive.  It seems to me to run cooler in UNR than when I run Windows 7 on it.

I'm anxiously waiting for the 10.04 LTS.  I am planning to install the UNR version.  I expected that UNR would be better suited for longer battery life power management etc.  Not sure.  

I am wondering about the install/partitioning process.  With all the default psqservice, system reserved, and acer partitions already on there, how am I going to be able to set up the /, swap, /home, etc partitions?

---

### Post by bruceliz on 2010-04-02
> **ebro173 said:**
> I am wondering about the install/partitioning process.  With all the default psqservice, system reserved, and acer partitions already on there, how am I going to be able to set up the /, swap, /home, etc partitions?

It's a good idea to resize (shrink) the Windows and Acer Recovery partitions from _within_ Windows, first defragmenting then resizing using the Windows tools provided.

Then Windows will still be aware of the UUIDs (and thus remain bootable) after you partition the newly-created free space with gparted and install Ubuntu.

---

### Post by Gemnoc on 2010-04-03
Why resize the recovery partition? It's only 10GB, and I think it's used at 75% capacity. Not much to gain there.

To my knowledge, UNR isn't better than Ubuntu over power management. I get 4-4.5 hours out of my 4400mAh battery, while it was 6hrs for Vista. Although, I haven't tried PatrickVogeli's power management script.

I used the free EASUS Partition Master on Vista to shrink the Windows partition and create a second partition D: for user data. Then on the LiveCD, I created extended partitions in the remaining space without trouble.

---

### Post by ebro173 on 2010-04-04
Thanks for the replies.  My concern is based on the assumption that I can only have four primary partions.  An extended partition will count as one of the partitions.  Then I could split that up into a swap, /home, and /data.  But, I thought that the linux / (root) partition has to be a true primary partition.  So my concern is based on this:

These first three partitions are already on there.
PQSERVICE (Primary) - I think this is the backup partition.
SYSTEM RESERVED (Primary) - In gparted this says boot.
ACER (Primary) - This is where windows 7 is.

I need to create at least two more primaries to do a basic Ubuntu install:
/ (Primary)
Extended (Primary)

Then I could split up the Extended...

So that would be five partitions and I'm thinking that won't work.

---

### Post by miegiel on 2010-04-04
> **ebro173 said:**
> Thanks for the replies.  My concern is based on the assumption that I can only have four primary partions.  An extended partition will count as one of the partitions.  Then I could split that up into a swap, /home, and /data.  But, I thought that the linux / (root) partition has to be a true primary partition.  So my concern is based on this:

These first three partitions are already on there.
PQSERVICE (Primary) - I think this is the backup partition.
SYSTEM RESERVED (Primary) - In gparted this says boot.
ACER (Primary) - This is where windows 7 is.

I need to create at least two more primaries to do a basic Ubuntu install:
/ (Primary)
Extended (Primary)

Then I could split up the Extended...

So that would be five partitions and I'm thinking that won't work.

No need to be concerned. ;) Check my partitions, all my linux partitions are in the extended partition.

```
user@machine:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044a80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8355    67111506    7  HPFS/NTFS
/dev/sda2            8356       38913   245457135    5  Extended
/dev/sda5            8356        8877     4192933+  82  Linux swap / Solaris
/dev/sda6            8878       10444    12586896   83  Linux
/dev/sda7           10445       12011    12586896   83  Linux
/dev/sda8           12012       38913   216090283+  83  Linux
```

---

### Post by Gemnoc on 2010-04-04
Same for me. Got 2 primary partitions for PQService and the Vista system, then one extended that includes 5 logical partitions as such: 1 ntfs, 2 ext4, 1 swap and 1 ext3.

Vista and UNR 9.10 run fine.

I was planning to install a second Linux distro but never got the time.

---

### Post by ebro173 on 2010-04-05
Thanks for the info miegiel and Gemnoc.  More questions.  Did either of you set up a partition that you can access from linux and windows? This shared partition can be inside an extended partition?  Also, neither of your Acers had a small partition like the one I see called SYSTEM RESERVED?

---

### Post by miegiel on 2010-04-05
> **ebro173 said:**
> Thanks for the info miegiel and Gemnoc.  More questions.  Did either of you set up a partition that you can access from linux and windows? This shared partition can be inside an extended partition?  Also, neither of your Acers had a small partition like the one I see called SYSTEM RESERVED?

Killed my acer partitions by accident :twisted: that's why I don't have a *SYSTEM RESERVED* partition. I installed win7 when I got the upgrade CD from acer. I don't use a separate partition for both linux and windows (use 1 home for both linuxes though). I just copy what I need, too and from the windows partition. It's no problem to access it from ubuntu.

---

### Post by alok_anil on 2010-04-07
i am having **Dell inspiron 14** with **core i3 **processor and 4 GB DDR3 RAM and i want to install ubuntu 9.10 on it but i am not able do so,

while installing it from graphics mode it stuk after 2nd step which is 
"select installation type "
which consists of 
try ubuntu without making change to system
install ubuntu 
and so on...

any one of these option is not working and i had also tried text based installation but it also not working is the processor is compatible with the ubuntu 9.10

when i was tried text based it get completed but while i choose ubuntu to boot or to run it does not work.

give me some help to fix this problem..

thank you!

---

### Post by miegiel on 2010-04-07
> **alok_anil said:**
> i am having **Dell inspiron 14** with **core i3 **processor and 4 GB DDR3 RAM and i want to install ubuntu 9.10 on it but i am not able do so,

while installing it from graphics mode it stuk after 2nd step which is 
"select installation type "
which consists of 
try ubuntu without making change to system
install ubuntu 
and so on...

any one of these option is not working and i had also tried text based installation but it also not working is the processor is compatible with the ubuntu 9.10

when i was tried text based it get completed but while i choose ubuntu to boot or to run it does not work.

give me some help to fix this problem..

thank you!

This thread is about the acers 1410 / 1810T/ 1810TZ, so it's pretty much off-topic. ;) I'll see if I can help you in the[ thread you started here]("http://ubuntuforums.org/showthread.php?t=1448817").

---

### Post by PatrickVogeli on 2010-04-16
Just for reference:

> **PatrickVogeli said:**
> Hi there all,

I start this thread hoping to help everyone who uses ubuntu in setting up their little timeline to work as good as possible and optimize battery life. I run ubuntu 9.10 64 bits nearly trouble free. 

This guide was first started at [Notebook Review Forums]("http://forum.notebookreview.com/showthread.php?t=434638"). There are a lot of Acer 1410/1810T/1810TZ users over there.

**Packard Bell / Gateway clones:**
This guide has also been tested on a Packard Bell Dot M/U with bios v3303, and it should also work on the Gateway clone. If you have a 1410/1810 and something doesn't work, please report back.

**Working after a standard Ubuntu 9.10 install:**[INDENT] - Graphics
- Audio out, speaker mutes when pluging in headphones. Good volume.
- Networking, both wireless (intel wifi 1000) and wired (the atheros gigabit)
- FN +:
· F4, suspends fine
· F6, monitor goes black
· F7, touchpad on / off
· F8, mute
· F9, Bloq Num
· RePag: Home
· AvPag: End
· Up: increase volume
· Down: decrease volume
· Righ: increase brightness: skips steps.
· Left: decrease brightness: skips steps.
· J,K,L, etc: numeric keyboard ok.

[/INDENT]**What's not working:**[INDENT]- Audio in: the integrated mic doesn't work.
- FN + F5: not recognised, doesn't toogle displays
- Wireless power saving
- Hibernate / suspend: won't resume properly.

[/INDENT]**Power saving tips:**[INDENT]By default, an ubuntu install won't take too much care of saving power, which is very important in an ultra mobile laptop. You can easily setup the system to enter some power saving modes, specifically the sata controller and the sound chip.

I've setup a script which will take care of making the devices entering the power saving mode when the laptop is on battery.
```

#!/bin/sh
  # Make sure brightness switch enabled stays on N, even on resume.
  echo N > /sys/module/video/parameters/brightness_switch_enabled
  # Disable wake on lan
  ethtool -s eth0 wol d

# Go fast on AC power.  Similar to default Ubuntu settings
if on_ac_power; then
  # Remount ext3 filesystems so the journal commit only happens every 60
  # seconds. This reduces disk activity.
  mount -o remount,commit=5,atime,diratime /
  mount -o remount,commit=5,atime,diratime /home

  # Set SATA back to normal operation
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo max_performance > $foo;
  done

  # Manually set the wifi driver to no power savings.
  # broken in 2.6.31 kernel
  # iwconfig wlan0 power off

  # Set kernel dirty page value back to default
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio
  echo 600 > /proc/sys/vm/dirty_writeback_centisecs 

  # Disable Intel HD audio power saving:
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save

else # Save power
  
  # Change the ext3 commit times to 10 minutes.  Reduces disk activity
  # disable disk writes when reading
  mount -o remount,commit=600,noatime,nodiratime /
  mount -o remount,commit=600,noatime,nodiratime /home
  
  # Set SATA to save power
  for foo in /sys/class/scsi_host/host*/link_power_management_policy;
    do echo min_power > $foo;
  done

  # Manually set the iwl3945 driver to power savings.
  # broken in 2.6.31 kernel
  # iwconfig wlan0 power on

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Enable Intel HD audio power saving:
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save
fi

```To install this power saving script, do the following:
```

gksudo gedit /etc/pm/sleep.d/15_saving
# Paste the script above into the file, save and close
sudo chmod +x /etc/pm/sleep.d/15_saving
sudo ln -s /etc/pm/sleep.d/15_saving /etc/pm/power.d/

```Next, let's configure gnome-power-manager, under System -> Preferences -> Power management:

- Hard drive power saving: in the battery tab tick on "Reduce hard drive revolutions when possible"
- Battery tab: tick on reduce brightness and dim display.
- AC and Battery tab: configure what to do when closing the lid and what to do on very low battery remaining.
- General tab: configure what to do when pressing the power button and sleep button (Fn+f4).
- General tab: configure when to show the battery icon.

Lm-profiler:
Last, but not least, we'll run lm-profiler to start / stop services when running on battery. To do that, disconnect from the mains and open a terminal (Aplications -> Accessories -> Terminal) and run sudo lm-profiler. It will run for 10 minutes and, when finished, it will ask what services to disable / enabled. You can safely disable cron, anacron and atd, if you don't use them. If you don't know what those are, you can dissabled them. If you never use a printer, or you only use it when connected to the mains, you can also disable cups. If in doubt, don't disable and ask here.

[/INDENT]**Issues:**
[INDENT] **Hibernate/resume:**[INDENT] **Issue:** after hibernating or suspending, the computer won't wake up properly.
**Solution:** gksudo gedit /etc/modprobe.d/blacklist.conf to edit the file and add the following (without quotes): "blacklist acer-wmi"[/INDENT]**Fan:**[INDENT] **Issue:** the fan is controlled by the BIOS, and is running too loud and too often.
**Solution:** the solution is installing an update acerhdf module. Download the laster version from [here (0.5.22)]("http://www.piie.net/files/acerhdf_kmod-0.5.22.tar.gz"). If you are using BIOS version 3120 or 3303, you can skip patching the module and can directly go on how to install and activate. If you have a BIOS different from that, you'll have to patch it adding your BIOS version. Unpack and look for the acerhdf.c file. In this file, look for the acer 1410 section:
```

/* Acer 1410 */
{"Acer", "Aspire 1410", "v0.3120", 0x55, 0x58, {0x9e, 0x9e, 0x00} },

```We have to add definitions for the Acer 1810T(Z), and also will add some more BIOS versions for the 1410:
```

{"Acer", "Aspire 1410", "v0.3108", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1410", "v0.3113", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1410", "v0.3115", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1410", "v0.3117", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
/* Acer 1810T */
{"Acer", "Aspire 1810T", "v0.3108", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810T", "v0.3113", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810T", "v0.3115", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810T", "v0.3117", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
/* Acer 1810TZ */
{"Acer", "Aspire 1810TZ", "v0.3108", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810TZ", "v0.3113", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810TZ", "v0.3115", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Acer", "Aspire 1810TZ", "v0.3117", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
/* Packard Bell clone */
{"Packard Bell","DOTMU","v0.3108", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Packard Bell","DOTMU","v0.3113", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Packard Bell","DOTMU","v0.3115", 0x55, 0x58, {0x9e, 0x9e, 0x00} },
{"Packard Bell","DOTMU","v0.3117", 0x55, 0x58, {0x9e, 0x9e, 0x00} },

```Save and close. Let's go on into compiling it:
```

cd /to/the/acerhdf/folder
make
sudo make install

```To make sure the module gets loaded and the fan control is enabled, do the following:
```

echo "acerhdf" | sudo tee -a /etc/modules
sudo touch /etc/modprobe.d/acerhdf.conf
echo "options acerhdf kernelmode=1" | sudo tee -a /etc/modprobe.d/acerhdf.conf
sudo modprobe acerhdf

```That will take care of loading the module when starting the laptop and automatically enable the fan control. After doing that, you should already be enjoying silent fan operation.

[/INDENT]**Brightness:**[INDENT] **Issue:** when changing the brightness using the FN+arrow keys, it will jump 2 levels instead of one. 
**Solution:** add the following into /etc/rc.local, **before** exit 0 and without quotes: "echo N > /sys/module/video/parameters/brightness_switch_enabled".

[/INDENT]**Wireless power saving:**[INDENT] **Issue:** in kernels from the 2.6.31 series, wireless power saving in intel wireless drivers was dissabled.
**Solution:** *(please, first look at the Alternative Solution below)* install updated drivers. the method I used, is compiling and installing the latest intel wireless drivers from the 2.6.32.2 kernel. To do this, download the latest wireless backports drivers from [here]("http://linuxwireless.org/en/users/Download/stable/#Stable_compat-wireless_releases") (compat-wireless-2.6.32.2.tar.bz2, updated). Unpack them and, to compile and install:
```

cd /to/compat/wireless/folder
scripts/driver-select iwlwifi
make
sudo make install
sudo make unload
sudo modprobe iwlagn

```**Alternative solution:** not tested by me. Install the linux-backports-modules-wireless-karmic-generic package and reboot. If it doesn't work, uninstall all linux-backports-modules-wireless packages using Synaptic and reboot. 

Now you'll be using the newest available intel wireless driver, where power saving works again. You can enable power saving by doing "sudo iwconfig wlan0 power" on or disable doing "sudo iwconfig wlan0 power off".

Now you can also uncomment the power saving lines in /etc/pm/sleep.d/15_saving script, so that the wireless enters power saving automatically when on battery and exits when pluging in the laptop again.

[/INDENT]**Integrated mic:**[INDENT] **Issue:** the internal microphone is not working. Playing with alsamixer doesn't solve this, all you can hear is noise.
**Solution:** Install the linux-backports-modules-alsa-karmic-generic packages. This package *should* include the fix too, but I don't know exactly which alsa version it provides. Using this solution, when a new kernel appears, it will also take care of reinstalling the newer alsa modules. Should it not work and/or you want to revert changes, uninstall all the linux-backports-modules-alsa packages using synaptic and reboot.
**Alternative solution:** download, compile and install a newer Alsa driver. Using this solution, everytime a new kernel is installed, you'll have to repeat this for the new kernel. Go to the [Alsa project webpage]("http://www.alsa-project.org/main/index.php/Main_Page") and download the lastest available alsa-driver. At the time of writing (29/11/09), that's 1.0.21. Once you have it, uncompress it and do the following:
```

cd /to/alsa/driver/folder
./configure --with-cards=hda-intel --prefix=/usr
make
sudo make install

```After rebooting, your internal microphone should be working. I've tried it with the sound recorder program under Aplications -> Sound & Video menu. Quality doesn't seem to be great, maybe playing with settings will help. *If someone has some tested tips (same fix, same machine), I'll add them. Thanks.*

[/INDENT][/INDENT]**Next to be done:**
- Enable undervolting

**Changelog**
29/12/2009: updated version of acerhdf, added blacklist acer-wmi to blacklist (thanks to all who reported)
05/12/2009: acerhdf version 0.5.21 now includes BIOS definitions for acer 1410/1810T(Z) and Packard Bell Dot M/U in v3303 and 3120. Audio alternative solution is now the recommended solution (thanks to iiamjon at notebook review forums, who tried and reported it as working)
02/12/2009: added more acerhdf bios definitions and changed acerhdf enabling. Thanks to teprrr.
29/11/2009: Initial post

**Thanks** 
tdavis, from Notebook Review Forums, for the wake on lan tip and adding the 11,6" acer series into acerhdf
teprrr, from Notebook Review Forums, for the acerhdf modprobe tip and bios definitions

---

### Post by baleks on 2010-04-17
Is there a way to reduce CPU Mhz ? When fan is off in a room (~25-28Celsius) core temp (shown by acerhdf) is ~58C on almost idle and up to 70C on load (at 67C i start the fan to not overheat cpu)

Question about idle states - when i reading something from notebook, it is still very hot (~58C), and even with fan (53C and more)

I trying do this via gnome-panel applet (like i do on my home big computer) but applet can't do anything...

---

### Post by PatrickVogeli on 2010-04-17
The lowest values possible, depending on the processor you have are:

-Su3500: 800Mhz
-SU7300: 800Mhz
-SU9400: 800Mhz
-SU4100: 1200Mhz
-SU2300: 1200Mhz
-SU2700: 1200Mhz

You can't go lower than that, it's hardware limited.

---

### Post by PatrickVogeli on 2010-04-18
Hi there!

I've done a script that should make it all automatically. In detail:

[SIZE="4"]**What the script does:**[/SIZE]
[LIST]
[*]Configure gnome-power-manager backlight dim and hard disk power saving
[*]Download, patch, install and setup acerhdf
[*]Install the power saving script
[*]Install the debugging script
[*]If laptop-mode-tools is installed, suggest uninstalling and, if you want, uninstall
[*]Fix the brightness hotkeys issue (jumps 2 levels on every key press)
[*]Disable ethernet Wake on Lan (doesn't enable when on AC)
[*]Disable uneeded services: cron, anacron and atd (they don't enable when on AC)
[/LIST]

[SIZE="4"]**What the script doesn't:**[/SIZE]
[LIST]
[*]Add the noatime parameter to the ext2/3/4 partitions in fstab. You'll have to do it manually. 
[/LIST]

[SIZE="4"]**How it works:**[/SIZE]
[LIST]
[*]In a terminal, run ./InstallAcer_11.6_PowerSaving.sh --help
[/LIST]

[SIZE="4"]**Disclaimer:**[/SIZE]
[LIST]
[*]This script comes with no warranty. Use it at your own risk. I won't be responsible for any damage this could do to your system or data.
[/LIST]
[B]
[SIZE="3"]Feedback is welcome, thanks![/SIZE][/B]

**EDIT (2010/04/19):** Script updated. Thanks to laramichaels1978 for pointing out some errors!
**EDIT (2010/04/20):** Script updated & removed. You'll find the most up to date script in the first post.

---

### Post by laramichaels1978 on 2010-04-19
Hi Patrick,

Thank you for your excellent guide! Happily running 10.04 on my 1810TZ.

Two brief questions: 

1- I noticed that you are setting

on AC

  echo 40 > /proc/sys/vm/dirty_ratio
  echo 10 > /proc/sys/vm/dirty_background_ratio

on battery

  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio

Based on this page [["]http://www.westnet.com/~gsmith/content/linux-pdflush.htm]]("http://www.westnet.com/%7Egsmith/content/linux-pdflush.htm), I would have guess you would be increasing *both* ratios when moving form AC -> battery. However, in the script you lower dirty_background_ratio from 10 to 1 when going from AC to battery. I guess I am missing something. : )

2- The remounting of the root/home partitions with a higher commit time when on battery is no longer present in the most recent version of the script; is there a reason for that? Or can I safely include those mount -o remounte,commit=XXX commands?

thanks for clarifying these two!
~lara

---

### Post by PatrickVogeli on 2010-04-19
> **laramichaels1978]Hi Patrick,

Thank you for your excellent guide! Happily running 10.04 on my 1810TZ.

Two brief questions:

1- I noticed that you are setting

on AC

echo 40 > /proc/sys/vm/dirty_ratio
echo 10 > /proc/sys/vm/dirty_background_ratio

on battery

echo 90 > /proc/sys/vm/dirty_ratio
echo 1 > /proc/sys/vm/dirty_background_ratio

Based on this page [[http://www.westnet.com/~gsmith/content/linux-pdflush.htm]](http://www.westnet.com/~gsmith/content/linux-pdflush.htm]), I would have guess you would be increasing *both* ratios when moving form AC -> battery. However, in the script you lower dirty_background_ratio from 10 to 1 when going from AC to battery. I guess I am missing something. : )

2- The remounting of the root/home partitions with a higher commit time when on battery is no longer present in the most recent version of the script said:**
> 

Hi,

You aren't actually missing anything. I once saw those values in a power saving script and never actually looked for their meaning. You are absolutely right: 
[QUOTE=http://www.westnet.com/~gsmith/content/linux-pdflush.htm]
/proc/sys/vm/dirty_background_ratio (default 10): Maximum percentage of active that can be filled with dirty pages before pdflush begins to write them

You are right, so I'll put 25 there once I get home and edit posts.

As for the 2nd question: my fault. In my case, I turned off the noatime parameter and then removed the remount stuff.. The correct thing would have been removing the noatime and nodiratime paramenters only, and remounting only with a higher commit.

Once I arrive home I'll fix everything and post the corrected guide and script again

Thanks a lot for pointing me in the right direction :)

---

### Post by PatrickVogeli on 2010-04-19
Script updated!

Thanks to laramichaels1978 for pointing out some errors!

**EDIT (2010/04/20):** script removed. You'll find the most up to date version in the first post.

---

### Post by ohiomoto on 2010-04-19
And thank you for starting and maintaining this topic!

---

### Post by Muskoka on 2010-04-19
Hi Patrick,

Getting an error when I try to run the new script, after installing the other one first:

sudo ./InstallAcer_11.6_PowerSaving.sh --install_all

I then enter my password, then I get this:

 ##################################################################

	This script comes with no warranty. Proceed under your own
	responsability and risk. If unsure, abort.
	It has been tested under an Acer 1810TZ, but should work with
	a wide range of intel chipset machines

      ##################################################################

	Enter your root password:
	Password OK, proceed:

	Unrecognised option, aborting...

	patrick.voegeli @ gmail dot com
	PatrickVogeli at ubuntuforums.org and forum.notebookreview.com

It doesn't ask for my password, this screen just comes up. What might the "Unrecognized option, aborting..." be?

Thanks for any help....Glen

Acer 1810t

---

### Post by ohiomoto on 2010-04-19
You are saying that you didn't type in your password?  And the script kept running?

---

### Post by Muskoka on 2010-04-19
Hi, yes that's correct. I put in my password when I run the script and that's it.

Glen

---

### Post by laramichaels1978 on 2010-04-20
Glad I could help! :) And thank YOU for curating this thread. : )

~lara

---

### Post by laramichaels1978 on 2010-04-20
To build on the earlier discussion of dirty_* values, I am thinking that perhaps what really matters for avoiding spurious disk access when on battery might be dirty_background_ratio and dirty_writeback_centisecs. The former controls when (in terms of how much of total memory is dirty pages) the background kernel threads that flush stuff to disk kick in, while the latter controls how often those same threads wake up. I am guessing these two should take care of the hard drive being brought back to life every N seconds when there is "nothing much going on" (from the perspective of the user).

Of course, I know nothing about this stuff. I just read these three pages:

[http://www.westnet.com/~gsmith/content/linux-pdflush.htm](http://www.westnet.com/~gsmith/content/linux-pdflush.htm)

[http://communities.vmware.com/thread/146002;jsessionid=664AFFE4A1DADDBB743B4239521977B6](http://communities.vmware.com/thread/146002;jsessionid=664AFFE4A1DADDBB743B4239521977B6)

[http://www.gossamer-threads.com/lists/linux/kernel/1017204](http://www.gossamer-threads.com/lists/linux/kernel/1017204)

dirty_ratio, on the other hand, does not seem to me to be something that triggers disk activity if the computer is largely idle; instead, it seems to be a "hard" limit that kicks in when there is so much writing going on that the background flushing mechanisms are not coping with it. When those situations happen and the system hits the value of dirty_ratio in terms of how much memory is "dirty pages", then the kernel forces that process to start syncing/flushing to disk everything it writes. This seems to be something that would happen in high-intensity scenarios, rather than a reason for the hard drive to periodically spin up while the system is mostly idle.

again, these are just uninformed guesses based on reading the above.

~l

---

### Post by PatrickVogeli on 2010-04-20
> **Muskoka said:**
> Hi Patrick,

Getting an error when I try to run the new script, after installing the other one first:

sudo ./InstallAcer_11.6_PowerSaving.sh --install_all

I then enter my password, then I get this:

 ##################################################################

	This script comes with no warranty. Proceed under your own
	responsability and risk. If unsure, abort.
	It has been tested under an Acer 1810TZ, but should work with
	a wide range of intel chipset machines

      ##################################################################

	Enter your root password:
	Password OK, proceed:

	Unrecognised option, aborting...

	patrick.voegeli @ gmail dot com
	PatrickVogeli at ubuntuforums.org and forum.notebookreview.com

It doesn't ask for my password, this screen just comes up. What might the "Unrecognized option, aborting..." be?

Thanks for any help....Glen

Acer 1810t
./InstallAcer_11.6_PowerSaving.sh --help

as for not asking the password, it's because you are running it directly as sudo: it already has sudo privileges, so, why sould it ask for the password?. You can launch it as a regular user and it will then ask you the sudo password.

---

### Post by laramichaels1978 on 2010-04-20
Finally : )

Based on the westnet.com page, I would guess that we might be msising one important parameter to avoid that constant background flushing to disk:

> 
 The first thing pdflush works on is writing pages that have been dirty  for longer than it  deems acceptable.  This is controlled by: 
  **/proc/sys/vm/dirty_expire_centiseconds** (default 3000):  In  hundredths of a second, how long  data can be in the page cache before it's considered expired and must be  written at the  next opportunity.  Note that this default is very long:  a full 30  seconds.  That means  that under normal circumstances, unless you write enough to trigger the  other pdflush  method, Linux won't actually commit anything you write until 30 seconds  later. 





So, it seems that increasing this value will be a good way to keep the flushing to disk from happening every couple of seconds.

~l

---

### Post by PatrickVogeli on 2010-04-20
Hey there,

you are good!

I'll look into it later and see if there are some scripts that already use that, so that I can get some reference values. Maybe we could set that to 30000 (5 mins)? Or should we perhaps set it at 60000 as the Dirty writeback centisecs parameter?

Your opinion is very welcome!

I'll look into this again in 12 hours.. I must go working now :(

---

### Post by Muskoka on 2010-04-20
Hello Patrick,

I wasn't really worried/concerned with the password. I asked in my original post, why does the script quit with "Unrecognised option, aborting..."?

Thanks Glen

---

### Post by PatrickVogeli on 2010-04-20
> **PatrickVogeli said:**
> ./InstallAcer_11.6_PowerSaving.sh --help

Look at my post.. you probably read the post and didn't download the script, then a bit later, you downloaded the script and didn't read the post again. Am I wrong?

./InstallAcer_11.6_PowerSaving.sh --install
./InstallAcer_11.6_PowerSaving.sh --install all
./InstallAcer_11.6_PowerSaving.sh --install acerhdf
./InstallAcer_11.6_PowerSaving.sh --install scripts

Run with --help to get an explanation about every option. Basically, you want to run with --install or --install all (install everything, both are the same)

---

### Post by PatrickVogeli on 2010-04-20
> **laramichaels1978 said:**
> Finally : )

Based on the westnet.com page, I would guess that we might be msising one important parameter to avoid that constant background flushing to disk:



So, it seems that increasing this value will be a good way to keep the flushing to disk from happening every couple of seconds.

~l
after reading a bit.. I've set it to 60000 (ten minutes), so that the commit, the dirty expire and the dirty writeback all are set to ten minutes.

Thanks again :)

---

### Post by miegiel on 2010-04-20
> **PatrickVogeli said:**
> after reading a bit.. I've set it to 60000 (ten minutes), so that all the commint, the dirty expire and the dirty writeback are set to ten minutes.

Thanks again :)

I've got the 3810T so you might want to verify it for yourself, but when I unplug the power dirty_expire_centisecs drop from 3000 to 60000 and dirty_writeback_centisecs drop from 500 to 60000 automatically.

---

### Post by PatrickVogeli on 2010-04-20
You probably have laptop-mode-tools installed, which I don't. Further, in the guide I recommend to uninstall it.

Could you please check if you have laptop-mode-tools installed?

---

### Post by miegiel on 2010-04-20
> **PatrickVogeli said:**
> You probably have laptop-mode-tools installed, which I don't. Further, in the guide I recommend to uninstall it.

Could you please check if you have laptop-mode-tools installed?

Yes I do :D sorry. Why do you recommend not using it?

---

### Post by Gotit on 2010-04-25
Great post Patrick!!

I was wondering if anyone has had luck in getting **hibernate** to work an a 1410?  
Even when I select hibernate from the shutdown menu the system goes into suspend, not hibernate.

Thanks all.......

---

### Post by baleks on 2010-04-25
> **Gotit said:**
> Great post Patrick!!

I was wondering if anyone has had luck in getting **hibernate** to work an a 1410?  
Even when I select hibernate from the shutdown menu the system goes into suspend, not hibernate.

Thanks all.......

Hibernate works but very bad for me :(

AFAIK gnome power management uses pm-utils
i configured it to use s2disk utility, but after resume strange hang up **** happens :(

---

### Post by ohiomoto on 2010-04-27
??? Hibernate works fine on my 1410.  My I used UNR, but I doubt that make any difference.

---

### Post by PatrickVogeli on 2010-04-27
hi,

for those with hibernate issues, are you using Jaunty? If so, have you added acer-wmi into /etc/modprobe.d/blacklist?

---

### Post by ebro173 on 2010-04-27
Still a great post.  I was reading over the recent discussion of the pdflush parameters.  So I'm doing research to see how my current configuration is working.  As Patrick mentioned, wit the standard installed config nothing changes in regards to the pdflush parameters when I unplug from AC.

Something like this may already have been posted here.  It is a short script to print out the current values of those four pdflush parameters.  Useful if you want to plug/unplug/replug... and check the parameters in one shot each time.

I saved the following in a text file named pdflush_params.

```

#!/bin/bash

echo 
echo ---------------------------------------
echo /proc/sys/vm/dirty_ratio
cat /proc/sys/vm/dirty_ratio
echo /proc/sys/vm/dirty_background_ratio
cat /proc/sys/vm/dirty_background_ratio
echo /proc/sys/vm/dirty_expire_centisecs
cat /proc/sys/vm/dirty_expire_centisecs
echo /proc/sys/vm/dirty_writeback_centisecs
cat /proc/sys/vm/dirty_writeback_centisecs
echo ---------------------------------------
echo 

```

 I made that file executable for myself.  Then ran it in a terminal with:

```

$./pdflush_params 

```

Once cd into the directory where the file was located.

Trivial I know. But I want more beans.

---

### Post by Gotit on 2010-04-27
> **PatrickVogeli said:**
> hi,

for those with hibernate issues, are you using Jaunty? If so, have you added acer-wmi into /etc/modprobe.d/blacklist?

No, my 1410 is running Karmic and I do have acer-wmi added to the blacklist.

Some other "power configurations" seem to be a little screwy too:
[INDENT]Setting the "Put computer to sleep when inactive" for x min on battery (Preferences > Power Management Preferences > On Battery Power tab) seems to be ignored when running on the battery in favor of the same setting on the "On AC Power" tab.[/INDENT]

[INDENT]Setting the system to suspend on low battery seems to be ignored and when the battery runs dry the system just crashes down.  In gconf-editor>gnome-power-manager>thresholds>percentage_action 2.  Maybe that's too low?  However, the system reports the battery at 0 and still runs for 15 min or so.[/INDENT]

However, the good news is that suspend will work when selected and the fan is now under control!!!

---

### Post by Gotit on 2010-05-01
Well, last night I made the leap to Lucid from an install and all seems to have gone pretty smooth.  However, there is one exception with the system fan.  

After installing Lucid, the fan was seeming to behave itself and would cycle on/off as appropriate (~63/56 C).  But it seemed to be set a little high for my taste as I prefer fan on/off at 60/52 C respectively.  So, I followed Patrick's instructions on installing the latest acerhdf (0.5.23) and all seemed to go well.  I modified /ect/modprobe.d/acerhdf.conf to have a second line of:```
fanon=60000 fanoff=52000
``` This all worked great in Karmic, but in Lucid that seems to have no affect on triggering the fan.

I did see in Synaptic Package Manager that Lucid had installed fancontrol and lm-sensors, or maybe I did that in trying to get the temp sensor to work :) .  Removing those two packages didn't seem to have any affect on the fan settings.

Is there some other way in Lucid to control the fan setting?

Thanks again!

---

### Post by ebro173 on 2010-05-03
Thanks again for this.  I've read through all the posts here at one time or another.  Not in the last few minutes however, so I don't know if you've already addressed these points from someone else asking about it.

I finally installed 10.04 on my Aspire 1410.  I ran the PowerSaving script with "--install scripts."  (I haven't really noticed any trouble with the fan.  I think I'll leave it alone.)

One problem is with the Dirty Writeback Centisecs. When on battery power we're expecting it to be set to 60,000 centisecs (10 minutes). Correct?  I looked in the install script and this is the value specified.

When on battery power and I run the CheckPowerSaving command, this parameter is set to 6,000.  (I get the same when running my trivial script that I posted a few days ago.)  Not sure why this is the case.

Another problem is that the results of the "dpkg -s laptop-mode-tools" command whether in the script or executed by me at the command prompt says that I do not have it installed.  However the install script and the CheckPowerSaving both still behave/indicate as if it is installed.  

One of the first things I did after installing 10.04 was to run "sudo sensors-detect" so I can check the temp of the processor.  Maybe that is causing the install script to think that I have laptop-mode-tools installed?  Just a guess.

Another thing I find a little strange.  When running "CheckPowerSaving" the expected results always appear to be the results we want for when on battery power.  When on AC power the expected results are still for battery. ?

I'd like to iron out the first point but these last two are basically just aesthetic.

---

### Post by ebro173 on 2010-05-03
Not sure if this is relevant to the things I mentioned above.  But, I do not have acpi installed.  Off I go to investigate what that is and install if needed.

---

### Post by PatrickVogeli on 2010-05-03
Hi, thanks for trying, that first.

I had the problem with the script reporting 6000 too... but that was when laptop-mode-tools was installed. Could you please open synaptic and check? If it's not, we'll have to look into what's changing the value. 

If you run the script manually (sudo /etc/pm/power.d/15_saving), does it work? Do you get the expected values?

And yes... the script return the expected values for on battery.. maybe I'll correct that one.. who knows ;)

Thanks

---

### Post by ebro173 on 2010-05-03
Alright, it appears to me that the acpi package is a tool for looking at the status of the acpi daemon.  I had the daemon installed (acpid) but not the acpi package. I installed acpi now.

Checked synaptic for laptop-mode-tools.  It is not installed.

After the above activity, I ran CheckPowerSaving and got actual expected results for performance parameters for on AC power (not checked for battery yet).  Still getting message about laptop-mode-tools and expected parameters for battery power even when I'm on AC.  The acpi part works now.

Next, when I ran, "sudo /etc/pm/power.d/15_saving" I got an error.  I did not have the ethtool installed.  In addition to that I get three lines saying, "stop: unknown instance."

I installed ethtool. Next ran CheckPowerSaving and got all the same results.  Also re-ran "sudo /etc/pm/power.d/15_saving," and still get those three lines. For everything I've done here I've been on AC.

Well, from 15 seconds to 60 seconds for the dirty writeback centisecs is already four times less frequent when on battery.  That should already be helping.

---

### Post by PatrickVogeli on 2010-05-03
You are running ubuntu, right? which version and so on?

The unkwon instances are cron, anacron and atd, services usually not needed in a laptop. I doesn't matter 

Could you please run dpkg -s laptop-mode-tools > lmt.log and attach the file lmt.log here? Probably you are getting a different output than me.

Also, I'll include install acpi and ethtool in the script.

Another question, do you have acpi-support installed?

Thanks

---

### Post by ebro173 on 2010-05-03
Yes. I'm running a brand new install of Ubuntu Netbook Edition 10.04 - this is the version based on gnome.

Check on the three unknown instances.

The contents of the attached file, lmt.log, were copied in from the terminal output.

Also, acpi-support is installed.  

Thanks for looking into it.  I think I'm already seeing some improvement in the battery life.

---

### Post by PatrickVogeli on 2010-05-04
> **ebro173 said:**
> Yes. I'm running a brand new install of Ubuntu Netbook Edition 10.04 - this is the version based on gnome.

Check on the three unknown instances.

The contents of the attached file, lmt.log, were copied in from the terminal output.

Also, acpi-support is installed.  

Thanks for looking into it.  I think I'm already seeing some improvement in the battery life.
you forgot to attach the file

---

### Post by greginak on 2010-05-04
Hi
I just upgraded my 1810TZ to Lucid. I have been running Koala with no problem. I use Powertop to monitor my power and keep it efficient. However since the upgrade i have been having odd readings. I am getting a fairly constant display on Powertop saying:

The program X is writing to to file Y on Z. This prevents the disk from going to powersave mode.

Z is either my root or home partition.
X is a variety of different programs 
Y is a variety of different files

some examples

X                        Y

flush-8.0           

amarok                 plasma-theme-amarok-mockup

network manager            

firefox-bin             places-sqlite-journal or urlclassifier3

virtuiso                soprano-virtuoso

plasma-desktop  to       kde-icon-cache.updated or        
                         plasma_theme-customized.lock


Any ideas what is happening?

---

### Post by ebro173 on 2010-05-05
I didn't pay attention the first time.  I guess you can't attach a .log file.

---

### Post by PatrickVogeli on 2010-05-05
make a zip file containing the log file and attach that one.

---

### Post by ebro173 on 2010-05-05
See the post above where I should have put it in the first place.

---

### Post by PatrickVogeli on 2010-05-05
yeah, sorry.. could you please attach the file /etc/apt/sources.list? I guess you don't have the universe repo enabled..

---

### Post by ebro173 on 2010-05-05
Here's what I got.

---

### Post by PatrickVogeli on 2010-05-05
how strange.. if you do sudo apt-get install laptop-mode-tools, what do you get? Can you install it?

---

### Post by ebro173 on 2010-05-05
Yes that command line will let me install it.  I didn't finish the install however. I entered "n" when apt-get asked if I wanted to proceed.

---

### Post by ebro173 on 2010-05-06
Did I misunderstand?  Did you want me to go ahead and install laptop-mode-tools?  I didn't think so because the PowerSaving install script tries to make sure it isn't installed.

---

### Post by PatrickVogeli on 2010-05-06
errr no, you didn't misunterstand. Later I'll check something... I don't know why your status output for laptop-mode-tools is different from mine :S

---

### Post by miegiel on 2010-05-06
> **PatrickVogeli said:**
> how strange.. if you do sudo apt-get install laptop-mode-tools, what do you get? Can you install it?

*off-topic:*
A better way to check is
```
user@machine:~$ aptitude search laptop-mode-tools 
i   laptop-mode-tools                                          - Tools for Power Savings based on battery/AC status
```
**i** means installed, **p** means not-installed.
there is also
```
aptitude show laptop-mode-tools
```
but it spews out a lot more info than you need.

---

### Post by PatrickVogeli on 2010-05-06
thanks, I'll put the following into the script:
```

sudo aptitude search laptop-mode-tools | grep "p   laptop-mode-tools"

```
that should do it, I think. Still, ebro's problem is still weird...

---

### Post by kamiokande on 2010-05-07
I just received my Acer 1810T laptop today, I'm excited to install 10.04 on it!!....but before I do, I have a question about whether or not I should update the BIOS via windows.

I read the first post in this thread, and also this documentation ([https://help.ubuntu.com/community/Aspire1810TZ/Karmic](https://help.ubuntu.com/community/Aspire1810TZ/Karmic)), and the latter seemed to indicate it's best to update the BIOS while Windows is still on the machine. 

That being said, I am planning to:

1) Update BIOS in Windows 7

2) Do a fresh install of 10.04 (no dual boot, so Windows would be wiped out)

3) Run the script in the first post of this thread.

Can anybody who has gone through this confirm that this is a safe sequence to get Lucid Lynx up and running?

Thanks!

---

### Post by gabbroo on 2010-05-08
Hello everyone,

So yesterday I gave the automated script a try to prolong usage on battery power. However, on ac power I notice that the left hand side gets really warm, as others have mentioned, and the HD temp. indicator shows 50 C, even when I only have firefox on and nothing else. The two core temps. remain almost steady at 41 C.

So have any of you resolved this issue yet?

I am running Lucid on aspire 1810T with centrino core 2 duo.

Thanks.

---

### Post by Stovey on 2010-05-09
I installed 10.04 today on my new Acer 1810T.

The 64 bit version gave a hard disk write error after the installation was 43% complete.  I tried 2 times, same thing  I changed the hard drive controller to IDE and tried again, same thing.  Then I tried the 32 bit version, which hung at the opening Ubuntu screen, the dots just kept scrolling.

So I installed 9.10 Karmic Koala and it worked fine, and then I upgraded to 10.04.

I then ran these scripts, many thanks!  Also installed chromium and Ubuntu restricted extras.

2 questions - why doesn't my internal mic work?  And why does the webcam suck soooooo bad?  I can't record video on this thing with any kind of resolution at all (and no sound to boot.)

---

### Post by miegiel on 2010-05-09
> **Stovey said:**
> I installed 10.04 today on my new Acer 1810T.

The 64 bit version gave a hard disk write error after the installation was 43% complete.  I tried 2 times, same thing  I changed the hard drive controller to IDE and tried again, same thing.  Then I tried the 32 bit version, which hung at the opening Ubuntu screen, the dots just kept scrolling.

So I installed 9.10 Karmic Koala and it worked fine, and then I upgraded to 10.04.

I then ran these scripts, many thanks!  Also installed chromium and Ubuntu restricted extras.

2 questions - why doesn't my internal mic work?  And why does the webcam suck soooooo bad?  I can't record video on this thing with any kind of resolution at all (and no sound to boot.)


Assuming it's the same problem as with all the other timelines:
> **miegiel said:**
> In a terminal do :
```
alsamixer
```
press F4 and set the sliders like this (left channel softer than the right):
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: Intel G45 DEVCTG                               F2:  System information &#9474;
&#9474; View: F3: Playback  F4:[Capture] F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Front Mic Boost                                Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;                    &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;             &#9484;&#9472;&#9472;&#9488;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474; [COLOR="Red"]&#9618;[/COLOR]&#9474;             &#9474;  &#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474; [COLOR="red"]&#9618;[/COLOR]&#9474;             &#9474;  &#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;  &#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;&#9618;&#9618;&#9474;             &#9474;&#9618;&#9618;&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9474;  &#9474;             &#9474;[COLOR="Lime"]&#9618;&#9618;[/COLOR]&#9474;             &#9474;[COLOR="lime"]&#9618;&#9618;[/COLOR]&#9474;                    &#9474;
&#9474;                    &#9492;&#9472;&#9472;&#9496;            L&#9492;&#9472;&#9472;&#9496;R            &#9492;&#9472;&#9472;&#9496;                    &#9474;
&#9474;                                   CAPTURE                                    &#9474;
&#9474;                    0<>0            80<>100          72<>72                   &#9474;
&#9474;             <Front Mic Boost >    Capture          Digital                   &#9474;
&#9474;                                                                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```
Use the arrow keys to move the sliders up and down and move to the next slider. Use Q Z E and C to move only the right or left channel slider up or down.

---

### Post by Stovey on 2010-05-09
Hey Miegel, that worked!!  Many thanks.

It's crazy that it would only work with those settings.  There's a little static so I tried reducing the input a bit but no go.

Is *anyone* able to capture decent video?

---

### Post by Gotit on 2010-05-09
Hi Patrick,

Quick question on the **acerhdf** file, is there a way to make it install automatically when the kernel is updated?  
I installed Lucid and patched the kernel with the acerhdf file.  A week later the kernel was updated and my fan was running often/loud so I reinstalled the acerhdf patch and that took care of it.

Also, in Lucid it seems the /ect/modprobe.d/acerhdf.conf file has no control over the temp limits for the fan's on/off settings the way it did in KK.  Is there another way to set the temp limits in Lucid?

Thanks for the great work!!

---

### Post by ebro173 on 2010-05-15
Finally decided to try to get the microphone working for Skype.  I have read in posts on this forum that the issue is ALSA/Pulse Audio treats the mic as a stereo device - with a left and right channel.

I'm not really clear on Pulse Audio. Does it perform the same function as ALSA?  Is it something that works with ALSA?

Anyway, I did install another software from the Software Center - padevchooser (Pulse Audio Device Chooser).  I didn't use it.  I gather this installed Pulse Audio and some other stuff.  I don't think PA was already installed.

Next, I opened Pulse Audio Volume Control (this being the "other stuff").  I went to the Input Devices tab.  I clicked the icon to lock/unlock the channels together.  I moved the slider of one of the channels down to silent.  Actually, as soon as I moved the one slider below 100% the bar showing the mic activity started bouncing left and right.

I did this while Skype was open but I'm not sure that made a difference.

I did a Skype test call and the mic was working.

---

### Post by kamiokande on 2010-05-15
I was able to successfully complete the installation, without any hitches, of 10.04 64-bit on my new Acer 1810T (bios v1.3308).

I was also able to successfully run the script - thanks!

I haven't yet tried the internal mic or webcam yet, but I'll get Skype sometime soon and give it a shot.

---

### Post by Stovey on 2010-05-15
Please let me know how your webcam works for you.  The best resolution I can get is 352 x 288 in Cheese.  And it's choppy for a few seconds before it wakes up.

---

### Post by tripkick on 2010-05-16
> **PatrickVogeli said:**
> 
[SIZE=4]**What the script does:**[/SIZE]
[LIST]
[*]Disable uneeded services: cron, anacron and atd (they don't enable when on AC)
[/LIST]

[SIZE=4]**What the script doesn't:**[/SIZE]
[LIST]
[*]Add the noatime parameter to the ext2/3/4 partitions in fstab. You'll have to do it manually.
[/LIST]
 

It's not a good idea to shut down cron and anacron altogether. You might try ```
ls /etc/cron.*
``` in order to see, what programs are started by the daemon. Therefore I moved the statements stopping the services to the battery section of the script and added a conditional start of the services when on ac power.

```

for daemon in atd cron anacron; do
    result=`service "$daemon" status | cut -f2 -d" "`
    if [ $result = "stop/waiting" ]; then
        service $daemon start
    fi
done

```There's no need to add the "noatime" parameter in the fstab entries. Instead it would be a good idea, I think, to change the mount statement in the battery section to

```
mount -o remount,noatime,nodiratime,commit=600 /
```It was already mentioned somewhere in the thread.

Thanks for the script.

---

### Post by ebro173 on 2010-05-19
Just thought I'd mention for anyone considering buying an Acer 1410...  I mostly plan to use mine (my Acer 1410) to browse the internet, do some word processing, and import/store/organize/upload photos (maybe some processing of photos, but this is pretty slow).  

Last night I was watching some soccer on ESPN3 (on the computer).  It worked fine, which is new.  I didn't used to be able to watch a lot of online streams in linux - always needed to boot into windows for that.  

But, I noticed that the bottom of the laptop was much hotter than it usually is.  I checked the processor temp with the sensors command.  It was 33 degrees C.  This is a bit warmer than usual but not out of control.  I didn't check the HD temp.  I wish I had.  But the heat on the bottom of the shell would have been unbearable if it were on my lap. 

So, possibly steer clear if your main use will be watching online video.  I'm not sure if this is what caused the heat or not.  I suppose it could have been something else.  The ambient temp in the house was about 85 degrees F.

---

### Post by ohiomoto on 2010-05-19
Did you have it plugged in?  Mine gets hot (and the fan runs like hell) when it's plugged in.  Runs fine on battery power.

---

### Post by ebro173 on 2010-05-19
> Did you have it plugged in?  Mine gets hot (and the fan runs like hell)  when it's plugged in.  Runs fine on battery power.

Yep, I did have it plugged in.  And in general it does run hotter plugged in.  But under other normal circumstances it doesn't get that hot even plugged in.  Also, the fan has not ever run really high.

---

### Post by hewbert on 2010-05-25
Has anyone noticed weirdness after a resume or opening the lid since upgrading to 10.04?

It's an intermittent issue and can do a couple of different things (at least for me).  Sometimes the resolution will jump around non-stop after a resume/or lid open.  Sometimes, the screen will just be black (backlight is on, though).  Both of these issues generally require a hard reset.  

I know at least one other user has the same issue: [http://ubuntuforums.org/showthread.php?t=1474437](http://ubuntuforums.org/showthread.php?t=1474437)

This is an upgrade from 9.10.  All packages are current.

---

### Post by ohiomoto on 2010-05-25
I had a similar issue recently with 9.10.  Problems with the display and then the track pad. Rebooted, booted to USB 10.04 and windows with the same result._ Pulled the battery, rebooted and the problems were gone._

---

### Post by hewbert on 2010-05-26
> **ohiomoto said:**
> I had a similar issue recently with 9.10.  Problems with the display and then the track pad. Rebooted, booted to USB 10.04 and windows with the same result._ Pulled the battery, rebooted and the problems were gone._

Thanks for the response.  I've done this, but I don't think it'll fix it.  It hasn't done it yet, but I haven't closed the lid much since doing it.  It can go a day or so before doing it again.  I'm still getting a bunch of flashes/redraws when opening the lid (new since 10.04), which seems to relate the the problem at hand.  I'm convinced that it's a software issue, just not sure where.  Drivers? Kernel? power management?

Desktop environment doesn't seem to matter - I've had it happen with compiz and with a minimal non-compiz environment.

---

### Post by bruceliz on 2010-05-27
> **hewbert said:**
> I'm still getting a bunch of flashes/redraws when opening the lid (new since 10.04), which seems to relate the the problem at hand.  I'm convinced that it's a software issue, just not sure where.

I haven't seen these problems, either under 9.10 or after upgrading to 10.4. I've probably got pretty much the same install as you -- the only obvious area of potential difference being that I'm updating to lucid-proposed (in case you're not).

The behaviour of my 1810TZ on resuming and restarting seems to have remained consistent, including even identical-looking video rubbish appearing briefly when waking from hibernation.

---

### Post by kesman on 2010-06-05
Hey people and thanks for a great(est) thread!

I'm a proud owner of a 1810TZ, 413G32n to be exact, and running Ubuntu 10.04 32bit version smoothly. I've flashed the bios to v1.3310 and am running acerhdf to reduce the fan noise. ( Was quite a struggle to flash the bios without a windows installation. Installed bootable DOS to a usb stick and made the magic with it :D )

I recently discovered a socket for a mobile phone SIM-card underneath the battery, but can't seem to insert any there. I also couldn't find any information about a HSDPA -modem in this model, so maybe it's only the entry hole but no device or something.

Also I think my Bluetooth is _broken_ since the last owner told me he couldn't get it to work under windows, and I can't get it to work under ubuntu. The kill switch next to wlan switch does nothing. Luckily the warranty is still valid, so I might replace this laptop with a new one or just get the bluetooth fixed.

One more thing; I can't seem to control the temperature limits with /etc/modprobe.d/acerhdf.conf, which looks like this now:
```

options acerhdf kernelmode=1 fanon=55000 fanoff=50000

```
since the fan doesn't start even when reaching over 60 degrees celsius temperatures.

Cheers!

---

### Post by Gotit on 2010-06-06
FYI, I just took kernel update to 2.6.32-22-generic (x86_64) which meant I needed to reload piie's acerhdf_kmod.  Until I did, I didn't have trouble with fan noise, in fact, quite the contrary, my fan didn't seem to go above "slow" at all and the processor got quite warm!! Guessing by the air that was circulating out of the vent I would say the processor made it to around 68c.

Once I reinstalled acerhdf_kmod (first post) the fan behaved better and on/off is now 63/58c respectively.  Still no luck in getting the kernel to pay attention to my lower settings in /etc/modprobe.d/acerhdf.conf

It seems like the kernel has evolved from keeping the fan always on "high" to always on "low".  Maybe the next one will be the Goldilocks release and be "just right" :)

---

### Post by Flakker on 2010-06-19
thank you Patrick, well written information and very useful scripts!

Interestingly, the auto script failed slightly in that it also returned

"FATAL: Error inserting acerhdf (/lib/modules/2.6.32-22-generic/kernel/drivers/platform/x86/acerhdf.ko): No such device"

However, using the manual steps I was able to complete that part myself.:p

---

### Post by Gotit on 2010-06-19
Hi all, I just had a conversation with the developer for the acerhdf module that deals with fan control.  I was having trouble setting the on/off temps in the /etc/modprobe.d/acherhdf.conf file.  It seem if you want to change the on/off setting it needs to be on the same line as the "options" like this
```
options acerhdf kernelmode=1 fanon=60000 fanoff=53000
```

I had it in 2 lines with the fan settings being the second line and it was disregarded by the system.  

Also,the developer said he submitted his module v0.5.24 for inclusion in the kernel so hopefully soon we won't have to load this separately.  But, until then we need the fan control!

If you would like to buy him a beer for all his efforts you can do so here: [http://piie.net/index.php?section=home](http://piie.net/index.php?section=home) I say it's well worth it and I did!! :p

---

### Post by lunatik_ru on 2010-07-04
> **ebro173 said:**
> Yep, I did have it plugged in.  And in general it does run hotter plugged in.  But under other normal circumstances it doesn't get that hot even plugged in.  Also, the fan has not ever run really high.
Did you solve this problem? Mine gets hot like hell when plugged in. Dunno what's causing it - hdd temp is always about 50 degrees. Under windows it never gets above 40 degrees.

---

### Post by tonic75 on 2010-07-12
Can I do a bios update in a 1810tz using a Memory Stick Pro Duo with freeDos?


Edit: I found it:

[http://forum.notebookreview.com/acer/434638-linux-acer-1410-1810tz-1810t-18.html](http://forum.notebookreview.com/acer/434638-linux-acer-1410-1810tz-1810t-18.html)

---

### Post by brokenromeo on 2010-07-13
I've got a 1410 running 10.04 64 bit, I have noticed that my wifi network performance gets very slow when I run on battery since I installed these utilities...delays in resolving names, connecting, etc...plug back into AC power all is fine...my 1410 also runs a bit hotter than I am comfortable with, although it did increase battery life over the straight Ubuntu install...any one have luck changing the fan on off thresholds...

---

### Post by Gotit on 2010-07-13
> **brokenromeo said:**
> ...any one have luck changing the fan on off thresholds...

See post #159 this same thread.
Also, the developer said the stock acerhdf module uses degrees Fahrenheit instead milli-degrees Celsius. So if you are not using the acerhdf module from piie you could try something like:

```
options acerhdf kernelmode=1 fanon=110 fanoff=100 
```

---

### Post by brokenromeo on 2010-07-14
Anyone know if I add the Bluetooth module to my 1410, will it be auto detected at boot and function, or will a special driver install be required...Ubuntu 10.04 64 bit.

---

### Post by brokenromeo on 2010-07-16
Disable touchpad while typing doesn't appear to be working on my 1410 running 64 bit 10.04...any tips?

---

### Post by a02dami on 2010-09-04
Hi!! Anyone tried acer 1810tz on ubuntu 10.10 64 bit? and if works "automatic installation scripts" .. I mean this one = [http://ubuntuforums.org/showthread.php?p=8409272](http://ubuntuforums.org/showthread.php?p=8409272)

Bye and thanks very much to everybody!

---

### Post by trazalca on 2010-10-18
Hi to all, i installed a fresh maverick, sensor-applet cant find any sensor, was good on lucid, someone has some fix for this? thanks in advance

---

### Post by asme on 2010-10-25
how do i undo the script? because i hate that my laptop goes black after 1min... i tried change in settings, but it didnt work..

---

### Post by PatrickVogeli on 2010-10-25
what do you mean to go black? If it's only the screen that dims, you can use gconf-editor for that, under apps > gnome-power-manager > backlight and uncheck enable, idle-dim-battery and battery-reduce. I think that should take care of that.

---

### Post by EdyStauch on 2010-10-31
Its safe to run this script on 1810TZ and Ubuntu 10.10 64 bits?

I need to increase battery time on Ubuntu 10.10.

On Win7 run more than 7 hours on battery, while on Ubuntu only 5 hours.

Thank you.

---

### Post by Alex S. on 2010-11-01
Hi Patrick, 
Have you made any experiences when upgrading from Ubuntu 10.04 to 10.10? I've appreciated your posts very much, they really helped me to get 10.04 started on my Acer 1810TZ. I'm wondering whether issues might occur when doing the upgrade in the next days. 
Best regards, Alex

---

### Post by PatrickVogeli on 2010-11-01
Hi, 

I usually always did a clean install, but this time I haven't. I upgraded to 10.10 using the update manager. Everything works fine, as expected, no problems.

I now use a different version of the script, which you may want to try. Basically, the biggest changes are some minor bug fixes and, the most important one, it now gets your model (1410, 1810t, 1810tz) and bios version and patches the module if it has to.

Patrick

---

### Post by tripkick on 2010-11-26
Hi!

Recently I noticed that the lifetime of the battery went down. As this might have to do with the upgrade to maverick (10.10) I had a closer look at what was happening to the various adjustments the latest version of the script attempts to make. 

According to the logs (var/log/pm-powersave.log) the script is called rather early by pm-utils and some of the other scripts run later by pm-utils revert the settings, notably "mount" (options), "Sata Power Saving" and "Wlan Power Saving". 

As pm-utils runs the scripts in "C sort order" (according to documentation) I simply renamed the generated script to "z15_saving" (instead of "15_saving"). Now it's called as the last script and the adjustments are not overwritten. 

Thanks for the good work!

---

### Post by PatrickVogeli on 2010-11-26
Hi,

I had already seen how some of the options that apply to the hard drive were being overwritten but, honestly, the change wasn't that big so I didn't care much.

After your post, I've checked what you say, and it doesn't work as yours: Wifi, Sata and HD audio powersaving are fine, the same as the mount options. The only thing that hasn't the expected value is "Dirty background ratio", which is 25 instead of 40 the script puts that.

EDIT: just tried, and putting z15_saving works 100% fine. I get 25 again. 

Thank you!

---

### Post by ralemi on 2010-11-28
Thank you Patrick, the guide and the scripts are very useful. I just installed Maverick on Acer 1410 for a friend of mine.

for what it is worth, I wanted to report that to enable the internal microphone I used the alsamixer and in the capture section, I muted the left channel while putting the volume of the right channel to max. that made the microphone work, albeit with the background noise that you mentioned in the first post of this thread of course.

then I installed skype from its website and noticed that it works without the need to do the PULSEAUDIO tweak any more.

The computer is running 10.10 64bit now and my friend is very happy with it.

Thanks again and Cheers,
Rex

---

### Post by miegiel on 2010-11-28
> **ralemi said:**
> Thank you Patrick, the guide and the scripts are very useful. I just installed Maverick on Acer 1410 for a friend of mine.

for what it is worth, I wanted to report that to enable the internal microphone I used the alsamixer and in the capture section, I muted the left channel while putting the volume of the right channel to max. that made the microphone work, albeit with the background noise that you mentioned in the first post of this thread of course.

then I installed skype from its website and noticed that it works without the need to do the PULSEAUDIO tweak any more.

The computer is running 10.10 64bit now and my friend is very happy with it.

Thanks again and Cheers,
Rex

You don't need to completely mute the left channel, it's enough if there is a difference. On this laptop (many laptops have this mic problem, not just the acer timelines) I have the left channel at about 50%, it seems to help a bit against the background noises.

---

### Post by PatrickVogeli on 2010-12-02
Hello everyone!

I'm having a very weird issue with my 1810tz and Ubuntu 10.10: suspend isn't working properly. It has always worked fine, but I think one of the latest updates broke it.

I've already tried reverting to an older kernel (I'm running 2.6.35-23-generic, tried 22-generic) and it didn't fix the issue.

What happens is, everytime I click suspend, it takes very long to suspend. I haven't timed it, but I think it takes minutes to do.. Also, after resume, the wireless doesn't come on automatically, it delays quite a bit to come up again.

Anybody is seeing the same issue? It has always worked fine, wether 9.10, 10.04 or 10.10 until now.

Ideas are welcome!

---

### Post by miegiel on 2010-12-02
> **PatrickVogeli said:**
> ... after resume, the wireless doesn't come on automatically, it delays quite a bit to come up again ...

I have no idea, but it could be your laptop is giving you a hint in what direction to look. Try suspending after you turned wireless off and/or try suspending after you closed every app that uses the network.

---

### Post by PatrickVogeli on 2010-12-03
Hi, thanks for replying!

I did a bit of investigation and it had not to do with wireless ON/OFF, nor with network-manager: it would always do the same.

I happens that a week ago or so I modified my Power Saving script to include a line to set the CPU scaling governor to On Demand. I had completely forgot about that change and hadn't used suspend since.. That line was causing the pain. I've fixed that using echo ondemand > /sys/.... blablabla and now it works.

Should be more carefull changing "critical" lines eh?

Patrick

---

### Post by carbon512 on 2011-01-06
Several issues related to  acerhdf, fan control, temperature and powersaving. They might(?) be related, so I am putting them all in     this same post, apologies for long multi-issue post.

Very new to Ubuntu or anything command-based, started from scratch last year. Learning by doing, jumping in, and     searching a lot, but I am stuck. Not lazy -- read most of this thread -- just     old...after I do figure out things, I     forget what I did. Grrr. Ready to ask for some help from you guys.
     
     Running 10.04 Lucid on an Aspire 1410 11.6" (U2300 processor). Kernel     2.6.32-27.generic. I updated the BIOS and installed acerhdf module. Also     ran the powersaving script from the     InstallAcer_11.6_PowerSaving_v2010_04_20.zip download. 
     
     PROBLEM: On battery power, fan still cycling off and on (quietly)     about every 15 seconds
     Added the fanon=60000 fanoff=50000 parameters to     /etc/modprobe.d/acerhdf.conf on the same line as described above     somewhere. Rebooted. Fan seems the same -- seems like it is kicking     in at 50 C or so and then cycling within just a few degrees range... still quiet though. And on reboot, there was a new problem:
     
     NEW PROBLEM: Now gnome temperature applet 2.2.3 will not read a     sensor it was formerly reading. Returns: "an error occurred while trying to     update the value of sensor temp1 located at     sensor://acerhdf-virtual-0/0" and "temp1 - chip not found." I     have assumed "temp1" was the HD temp, since the other two are labeled     core0 and core1. Seems wrong that this one change would cause     that... how can I track down what else I did and fix this? I want to     monitor all the temps because of the last most exciting and     complicated problem (suspense, wait for the end)
     
     NEXT PROBLEM: powersaving script debugging:
 - LOWER FILE SYSTEM ACCESS:
Dirty Writeback Centisecs at 6000 as opposed to     60,000, as in post #120. Running the script manually returns: "mount: can't find /home in /etc/fstab or /etc/mtab" but does set the 6000 back to 60,000.   So how do I make it do that automatically? I know I don't     have laptop-mode-tools installed because it took me much digging to     discover its "not installed (residual config)" status, which I then     fully uninstalled.
 - also this:
SATA POWER SAVING:
Expected result: min_power (most of them)
    min_power
    max_performance
    min_power
    min_power
    max_performance
    max_performance

Which three are still on max and how can I change that?
     
     EXCITING CONFUSING PROBLEM: Running hot, and a new? fan issue:
     As someone else mentioned in post #[can't find it anymore], my 1410 gets very hot     playing HD video. I only played Divx videos for months, and it felt     warm but I didn't monitor temps back then.
     
     Then I did the acerhdf and powersaving installs. Then decided to     boot into Windows7 to stream Netflix. Cutting to the chase here: In     Windows, fan will not reliably kick in on battery power. Streaming     Netflix HD video can cause computer to shut down if I     don't monitor temp and stop before it gets over 90+C.  Fan operates     normally (high, LOUD) on AC power. Never tried watching HD videos in     Win before, so don't know if this is a new development since the BIOS     upgrade and fan driver install, or if it was always there. (That's     the fun exciting part.) 

Fan operates normally on AC or battery in Ubuntu (high, loud while playing HD video, but it keeps the notebook cool)
     
     I have a temp monitor running in Ubuntu and in Windows and my normal     operating temps are around 50C. Playing videos sends them up to 70C     or so (except for Windows battery problem above). This is not really  Ubuntu so I am slogging through Windows laptop forums looking for  solutions but thought maybe someone here might have an idea.

Thanks.

---

### Post by PatrickVogeli on 2011-01-06
the /home stuff... if you don't have a separate home partition then it fails, it's normal.

The sata power saving stuff.. it's normal that some remain at high performance, you can't change those. I don't know why.

The temperature stuff.. I think it's a bug in the applet. The acerhdf developer at least thinks so. As for the fan settings.. you may want to make some tries yourself to see if it changes.

Windows: I don't know anything about that.

---

### Post by carbon512 on 2011-01-06
Thanks! One more --

What would cause the acerhdf.conf file to be re-written in a crash? My touchpad froze, and after a reboot into Windows and then two reboots into Ubuntu to get control back, acerhdf.conf had reverted to 

```
options acerhdf kernelmode=1 options acerhdf kernelmode=1
```so the module would not load. 

During the install and checking process, I had the above in the acerhdf.conf file, but I had previously fixed it and saved the file to read

 ```
options acerhdf kernelmode=1
```and then later added the fanon fanoff so it read

```
options acerhdf kernelmode=1 fanon=60000 fanoff=53000 
```I did a very messy install as I was trying to understand what I was doing originally -- installed the wrong driver for my new BIOS version and who knows what else. I would like to clean all that up if it is causing problems -- I don't know what I did to make that second "options acerhdf kernelmode=1" happen in the first place, or why it came back.

---

### Post by carbon512 on 2011-01-31
Still new to Ubuntu -- trying though...

After updating to kernel 2.632-28-generic, acerhdf not working...

```
xxx@xxxxxx:~$ sudo modprobe acerhdf
FATAL: Error inserting acerhdf (/lib/modules/2.6.32-28-generic/kernel/drivers/platform/x86/acerhdf.ko): No such device

```There is an acerhdf.ko file in the /lib/modules/2.6.32-28-generic/kernel/drivers/platform/x86/ folder. But it is a different size from the one in /lib/modules/2.6.32-27-generic/kernel/drivers/platform/x86/ (that is the kernel I was on when I compiled and installed it originally)

Should I just replace this one in the new kernel folder with the one from the /lib/modules/2.6.32-27-generic/kernel/drivers/platform/x86 folder? Can I just do this with a simple file copy/rename (backing up old one first of course) or does it need some other install-related juju?

I do still have all the original files in the /usr/src/acerhdf_kmod folder...

Thanks.

---

### Post by PatrickVogeli on 2011-02-01
you have to run the script again, doing the following:
```

./script_name --reinstall_acerhdf

```

this should care of it

---

### Post by carbon512 on 2011-02-03
Ah, thanks. Sorry for late reply -- have been stranded/traveling through crazy storm ice stuff for days; the importance of my laptop fan issue faded. But it will be bother me again as soon as I finally get back home, so I am glad to know I can re-install to fix it.

Such a helpful resource here, really appreciate your assistance.

---

### Post by carbon512 on 2011-02-08
New issue (not fan or power saving related, phew.)

My internal speaker on the 1410 no longer mutes when I plug in headphones or external speakers. The external analog audio output works, but the internal speaker continues to play at regular volume as well. This used to mute when a jack was plugged in, but I don't know at what point it stopped working.. which update broke it...

I found an older bug report on this: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/477154](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/477154). I am running 2.6.32-28-generic and I do have linux-backports-modules-alsa-2.6.32-28-generic installed. Also have linux-backports-modules-alsa-lucid-generic installed. 

Any tips about what to try to troubleshoot and fix this? I'm reading through the bug report but it is a little thick for me yet. Already tried playing around with sound preferences: internal audio set to Analog Stereo Output profile but Analog Stereo Duplex does the same thing; under "output", the connector is set to Analog Output. changing this to Analog Headphones silences the built-in speaker and the headphones.

thanks

---

### Post by dustrho on 2011-02-25
> **lunatik_ru said:**
> Did you solve this problem? Mine gets hot like hell when plugged in. Dunno what's causing it - hdd temp is always about 50 degrees. Under windows it never gets above 40 degrees.

My computer is running hot as hell with or without running this script. I'm running Ubuntu 10.04 amd64, and I don't understand why it's running so damn hot. Would I be better off running 10.10 amd64 or go with a 32-bit version of one of those? Not sure what BIOS version I have, but I can easily find that out if needed.

Thoughts?

---

### Post by Gotit on 2011-02-27
@dustrho
I too am running 10.04 64bit without problems, so I don't think it's the Ubuntu version.
> My computer is running hot as hell with or without running this script.
Not sure which script you are referring to here.  If it's the how to minimize power usage on battery, I didn't attempt that.  I just did the "fan fix" from the first post where you need to install the acerhdf module and then do the bit to make sure it loads on each boot.

Does you fan run at all?  If not, maybe try loading the acerhdf module again and be sure to set the fan speed correctly, as I had trouble with that at one point, see here: [http://ubuntuforums.org/showthread.php?p=9484311&highlight=line#post9484311]("http://ubuntuforums.org/showthread.php?p=9484311&highlight=line#post9484311")

---

### Post by trazalca on 2011-04-08
i upgraded skype version to 2.2 beta, now the internal microphone no longer works... there's someone that can help me please?? thanks in advance

---

### Post by bruceliz on 2011-04-08
> **trazalca said:**
> i upgraded skype version to 2.2 beta, now the internal microphone no longer works.

Same here. The workaround of starting it with the string

```
/bin/sh -c "PULSE_SERVER=127.0.0.1 skype"
```

doesn't work with this new version, and  the manual workaround of setting the output volume balance to the left or right for each Skype session is really inconvenient (though it does work).

I 'solved' the problem by uninstalling the 2.2 beta and reverting to the previous version, thankfully having kept the old .deb package.

---

### Post by nab on 2011-04-09
I'm on an 1810tz with ubuntu 10.04 64bit and Skype 2.2.025-1lucid1 and Skype is working fine.

I solved my mic problems with:

I think the main problem was that my internal mono mic is recognised as a stereo mic and the default setting cancel the signal out.

I installed pavucontrol with Synaptic and started it in a terminal.
In output devices I set the front left to 90% and the front right to 10%. (This way the mic doesn't cancel the signal out) You have to play with the buttons to be allowed to change both value independently.

(I'm pretty sure I found this solution somewhere on the net, but at the moment I don't remember where ... )

---

### Post by bruceliz on 2011-04-09
> **nab said:**
> I think the main problem was that my internal mono mic is recognised as a stereo mic and the default setting cancel the signal out.

I installed pavucontrol with Synaptic and started it in a terminal.
In output devices I set the front left to 90% and the front right to 10%. (This way the mic doesn't cancel the signal out) You have to play with the buttons to be allowed to change both value independently.

Yup, that works -- thanks!

One correction, however: you can set the INPUT device Left and Right channels separately after unlocking pavucontrol's linking of the two by clicking on the appropriate button. I set one channel to zero and the other to 80% and the mike seems to work decently enough (even if there's still a fair bit of  background noise when using Sound Recorder). But this workaround leaves the OUTPUT settings in stereo balance -- and that's a good thing.

NOTE: if using a version of Skype whose options include a checkbox enabling Skype to take over the volume setting, make sure it's unchecked. Otherwise Skype will immediately screw up the input volume settings you've just taken the trouble to configure in pavucontrol (which, BTW, shows up as 'Pulseaudio Volume Control' in Ubuntu's Applications -> 'Sound & Video' menu).

---

### Post by Alex S. on 2011-04-28
Hi, 
Has anybody  made any experience with Ubuntu 11.04? Currently I'm running Ubuntu 10.10 and would like to upgrade. 
Thanks!
Regards, Alex

---

### Post by Gotit on 2011-04-28
I'm not on 11.04 but I did get word from piie (Fan fix patch author) and he said his patch was merged into kernel 2.6.36.  Since 11.04 is shipping with kernel 2.6.38 (last I saw) the fan problem should be gone.

---

### Post by PatrickVogeli on 2011-04-29
it depends on the bios... I have the latest one and I have to compile it. The laptop is working fine, all excepte compiz, which crashes a lot.

---

### Post by carbon512 on 2011-10-06
Finally upgraded to Natty. Despite now being on kernel 2.6.38-11-generic, which should include the fan module, the fan is now running high again. So I tried to re-install acerhdf, but get this message:

```
xxx@xxx:~/Downloads/acerhdf_kmod$ sudo modprobe acerhdf
FATAL: Error inserting acerhdf (/lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/acerhdf.ko): Invalid argument
```so I tried to run the whole powersaving script InstallAcer_11.6_PowerSaving.sh again, but get this after the disclaimer about warranty, etc...

```
Unrecognised option, aborting...

    patrick.voegeli @ gmail dot com
    PatrickVogeli at ubuntuforums.org and forum.notebookreview.com
```What mistake am I making here? Have I  forgotten a step (or two) in the install? (very possible since I had locked down my last version of Lucid and not done anything in Ubuntu (except use it) for a long time. Or does the script simply not work for 11.04 since it shouldn't be needed?

thanks.

---

### Post by Gotit on 2011-11-19
Has anyone had trouble compiling the acerhdf module on lucid 64 bit with the latest kernel update (2.6.32-35-generic)?  I get this error on make:
```
gotit@Ubuntu-Netbook:~/ACER Fan Control/acerhdf_kmod$ make
make -C /lib/modules/2.6.32-35-generic/build  SUBDIRS=/home/gotit/ACER Fan Control/acerhdf_kmod modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-35-generic'
make[1]: *** No rule to make target `Fan'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-35-generic'
make: *** [default] Error 2
```
I'm booting to kernel 2.6.32-34 until I can get this resolved.  Thanks!

---

### Post by bruceliz on 2011-11-19
> **Gotit said:**
> Has anyone had trouble compiling the acerhdf module on lucid 64 bit with the latest kernel update (2.6.32-35-generic)?  I get this error on make:
```
gotit@Ubuntu-Netbook:~/ACER Fan Control/acerhdf_kmod$ make
make -C /lib/modules/2.6.32-35-generic/build  SUBDIRS=/home/gotit/ACER Fan Control/acerhdf_kmod modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-35-generic'
make[1]: *** No rule to make target `Fan'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-35-generic'
make: *** [default] Error 2
```
I'm booting to kernel 2.6.32-34 until I can get this resolved.  Thanks!

Looks like 'make' doesn't like spaces in filenames (as in the case of your directory "ACER Fan Control". Remove those spaces!:)

---

### Post by Gotit on 2011-11-20
@bruceliz
Ah, yes, must remember the basics...
That was it, thanks much.

---

### Post by PatrickVogeli on 2011-11-22
Hi there all,

I just wanted to say that I no longer use or develop that script. I've recently switched to Debian Squeeze and have also started working, so I don't have much free time and I'm not planning to do any further fixing or improvements to the script.

Of course, if somebody wants to continue developing, fixing or improving it, feel free to do so, be it in this thread or starting from zero in a new one. I'll be glad if the existing one can serve as a base to do even a better one.

Patrick

---

### Post by Janghou on 2011-12-01
Thanks Patrick, for all your good work. This thread has been a major source of info for me. 

I have updated to Ubuntu 11.10 and, it runs quite well on the 1810tz, although Unity has it quirks: Unity2D seems to have a better app switcher.

I still use your script: I used it yesterday after the latest Linux headers update I noticed the noisy fan. 

After running your script it's quiet again. :)

Thx again and good luck!

---

### Post by sitic on 2012-01-21
> **carbon512 said:**
> Finally upgraded to Natty. Despite now being on kernel 2.6.38-11-generic, which should include the fan module, the fan is now running high again. So I tried to re-install acerhdf, but get this message:

```
xxx@xxx:~/Downloads/acerhdf_kmod$ sudo modprobe acerhdf
FATAL: Error inserting acerhdf (/lib/modules/2.6.38-11-generic/kernel/drivers/platform/x86/acerhdf.ko): Invalid argument
```


A little late response:
Try this command:
```

sudo -s
modprobe acerhdf force_bios=v1.3310
echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode
```

If it works do this:

```

echo "options acerhdf verbose=0 fanon=60000 fanoff=55000 interval=5 kernelmode=1 force_bios=v1.3310" | sudo tee -a /etc/modprobe.d/acerhdf.conf

```

and put 

```

echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode

```

before the "exit 0" line in /etc/rc.local

---

