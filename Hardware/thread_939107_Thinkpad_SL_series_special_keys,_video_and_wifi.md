---
title: "Thinkpad SL series special keys, video and wifi"
date: 2008-10-05
forum: Hardware
---

### Post by maxitaxi on 2008-10-05
Hi all,

Hopefully this thread will catch the attention of Thinkpad SL owners.

Right now, I'm having these problems with my SL400 (these are all with Intrepid Ibex):

1) Video card driver is behaving oddly sometimes. When shutting down it blinks the screen many times. When starting up, a few times it would show everything in a messy de-interlaced way, but rebooting would fix it.

Note: I have the version with Intel GMA 4500.

2) Brightness keys are reversed. Gnome behaves like they are reversed too, i.e. it start up with the screen being on low brightness, and after a period of inactivity it switches to a brighter screen. However, this is a gnome problem, it looks like, because using /proc/acpi/video/VGA/LCDD/brightness behaves correctly.

See [this thread]("http://ubuntuforums.org/showthread.php?t=925959&highlight=sl400") for further information.

3) Wifi currently doesn't work with Ibex, so I need to manually build madwifi-hal-0.10.5.6-r3861 from the website. I need to rebuild it after every kernel update, which isn't a bother for me, but should probably be friendlier.

Note: I have the version with the atheros chipset... Intel WiFi might work better.

4) Sound volume control buttons on the left side don't work. Running 'xev' doesn't show any X events occuring when I press those buttons.

There is a package 'tbp' in Synaptic that talks about thinkpad special keys. However, installing it conflicts with 'ubuntu-desktop' so I didn't date play with it.

Post any information you discover about the SL series!

Max

---

### Post by gl2tosl2 on 2008-10-05
> **maxitaxi said:**
> 
3) Wifi currently doesn't work with Ibex, so I need to manually build madwifi-hal-0.10.5.6-r3861 from the website. I need to rebuild it after every kernel update, which isn't a bother for me, but should probably be friendlier.

Note: I have the version with the atheros chipset... Intel WiFi might work better.


I have the intel wireless 5100 agn.  It works with 8.10 out of the box with the iwlagn driver.

I'll add 
5)  When booting on battery power the computer starts beeping like there's a panic of some kind.  When this happens the beeping doesn't stop until a reboot.  Once ALSA comes on the sound gets muted, but it's still there if I turn the volume up.

---

### Post by maxitaxi on 2008-10-05
> **gl2tosl2 said:**
> 
5)  When booting on battery power the computer starts beeping like there's a panic of some kind.  When this happens the beeping doesn't stop until a reboot.  Once ALSA comes on the sound gets muted, but it's still there if I turn the volume up.

I just checked.. oddly, this doesn't happen for me. Does it happen every time? Did it start only recently?

---

### Post by gl2tosl2 on 2008-10-08
> **maxitaxi said:**
> I just checked.. oddly, this doesn't happen for me. Does it happen every time? Did it start only recently?
It was happening every time.  But it's stopped now.  The last time it happened was on last friday.  It was so annoying that I avoided turning it on in such situations.  It is possible that it has been fixed by one of the updates since then.  I'll keep monitoring it and try various conditions.

---

### Post by gl2tosl2 on 2008-10-11
Okay, the beeping thing has started again.  At this point all I can say is that I did a normal shut down with it plugged in.  Then I booted up on battery power it made the beeping noise.  Then I suspended on battery power.  And resumed after I had plugged it back in, it made the beeping noise then.  I don't know the relative battery levels.

I got an error from the kernel on this one

```
[ 1197.690695] PM: resume devices took 17.972 seconds
[ 1197.690700] ------------[ cut here ]------------
[ 1197.690702] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x75/0x80()
[ 1197.690704] Modules linked in: ipv6 binfmt_misc af_packet rfcomm bridge stp bnep sco l2cap uinput nvram ppdev acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table cpufreq_powersave cpufreq_conservative pci_slot wmi container sbs sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport joydev arc4 ecb crypto_blkcipher iwlagn iwlcore psmouse uvcvideo evdev pcspkr snd_hda_intel rfkill serio_raw compat_ioctl32 sdhci_pci sdhci led_class mmc_core videodev v4l1_compat ricoh_mmc snd_pcm_oss snd_mixer_oss snd_pcm mac80211 btusb cfg80211 snd_seq_dummy bluetooth nvidia(P) i2c_core snd_seq_oss video ac battery output snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device button intel_agp snd soundcore shpchp pci_hotplug snd_page_alloc ext3 jbd mbcache sd_mod crc_t10dif sr_mod cdrom sg ohci1394 ahci ieee1394 libata scsi_mod dock r8169 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor uvesafb fuse
[ 1197.690757] Pid: 7107, comm: pm-suspend Tainted: P          2.6.27-7-generic #1
[ 1197.690759]
[ 1197.690759] Call Trace:
[ 1197.690764]  [<ffffffff8024e984>] warn_on_slowpath+0x64/0x90
[ 1197.690768]  [<ffffffff80501806>] ? printk+0x6c/0x6e
[ 1197.690771]  [<ffffffff802126b4>] ? mcount_call+0x5/0x31
[ 1197.690773]  [<ffffffff8027e175>] suspend_test_finish+0x75/0x80
[ 1197.690776]  [<ffffffff8027e284>] suspend_devices_and_enter+0x104/0x1b0
[ 1197.690778]  [<ffffffff8027e541>] enter_state+0xe1/0x110
[ 1197.690780]  [<ffffffff8027e62a>] state_store+0xba/0x100
[ 1197.690783]  [<ffffffff803a5b97>] kobj_attr_store+0x17/0x20
[ 1197.690786]  [<ffffffff8034b33a>] sysfs_write_file+0xca/0x140
[ 1197.690789]  [<ffffffff802ebbdb>] vfs_write+0xcb/0x130
[ 1197.690792]  [<ffffffff802ebd35>] sys_write+0x55/0x90
[ 1197.690794]  [<ffffffff8021289a>] system_call_fastpath+0x16/0x1b
[ 1197.690795]
[ 1197.690796] ---[ end trace e18aaa17f025114a ]---
[ 1197.691003] PM: Finishing wakeup.

```

---

### Post by schpet on 2008-11-06
I am running 8.10 on a Lenovo SL300; very similar problems:
* Volume keys do not work, xev shows no response
* Atheros AR242x Wifi works with madwifi ath_pci drivers, have to reload on suspend though -- this was fixed with grytr23's post below
* Brightness keys reversed and buggy; gnome brightness applet reversed
* Having a lot of trouble trying to enable middle button mouse wheel emulation with the "DualPoint Stick" (it seems the "AlpsPS/2 ALPS DualPoint TouchPad" receives the button press', have had no success playing around with .fdi files)
Edit: I found a fix for firefox: navigate to "about:config" in the address bar, change the "general.autoScroll" value to "true"
* When I switch to a virtual terminal (ctrl-alt-F1) the system beeps go off very frequently (e.g. when I backspace and nothing is there) -- fixed by blacklist pcspkr in /etc/modprobe.d/blacklist (thanks garytr23)

---

### Post by garytr23 on 2008-11-08
I also have an SL300 and there's a thread on the lenovo forum dealing with this stuff, too.  

[http://forums.lenovo.com/lnv/board/message?board.id=SL_ThinkPads&thread.id=310](http://forums.lenovo.com/lnv/board/message?board.id=SL_ThinkPads&thread.id=310)

I'm a student, so I can't have my computer beeping willy nilly.  Blacklist the pcspkr module in /etc/modprobe.d/blacklist 

I also have the atheros, and i found i have to rmmod and modprobe ath_pci to get it working after a suspend.

Also, gnome power manager reports 1/2 battery life... however powertop reports the proper battery life so i think this is gnome's fault.

---

### Post by garytr23 on 2008-11-09
I wrote a script for the rmmod and modprobe of ath-pci. g-p-m relies on pm-utils for sleep, and this is one way to do scripting with pm-utils.

put it in /etc/pm/sleep.d/restartatheros and do a chmod +x.

 

 

#!/bin/bash
case $1 in
    hibernate)
        rmmod ath-pci       
    ;;
    suspend)
        rmmod ath-pci
        ;;
    thaw)
        modprobe ath-pci
        ;;
    resume)
        modprobe ath-pci
        ;;
    *)  echo "somebody is calling me totally wrong."
        ;;
esac

---

### Post by gl2tosl2 on 2008-11-17
> **maxitaxi said:**
> I just checked.. oddly, this doesn't happen for me. Does it happen every time? Did it start only recently?
Update.

It's still happening.  I've caught it happening with an error like the following:
```
proc_dir_entry 'video/VGA' already registered
```

Then it gives a call trace:
```
proc_dir_entry 'video/VGA' already registered
Pid: 2589, comm: modprobe Not tainted 2.6.27-7-generic #1
Nov 17 20:18:54 peacock kernel: [   14.829083]
Call Trace:
 [<ffffffff8033dea8>] proc_register+0x1e8/0x220
 [<ffffffff8033e102>] proc_mkdir_mode+0x42/0x60
 [<ffffffff8033e136>] proc_mkdir+0x16/0x20
 [<ffffffffa023be99>] acpi_video_bus_add_fs+0x2d/0x199 [video]
 [<ffffffffa023d251>] acpi_video_bus_add+0xe8/0x2f7 [video]
 [<ffffffff803ee550>] acpi_device_probe+0x4e/0x91
 [<ffffffff80430552>] really_probe+0x72/0x1a0
 [<ffffffff804306d0>] driver_probe_device+0x50/0x60
 [<ffffffff8043076b>] __driver_attach+0x8b/0x90
 [<ffffffff804306e0>] ? __driver_attach+0x0/0x90
 [<ffffffff8042fcdb>] bus_for_each_dev+0x6b/0xa0
 [<ffffffff802e1ecb>] ? kmem_cache_alloc+0x8b/0xd0
 [<ffffffffa0092000>] ? acpi_video_init+0x0/0x63 [video]
 [<ffffffff804303b1>] driver_attach+0x21/0x30
 [<ffffffff8042f548>] bus_add_driver+0x1f8/0x270
 [<ffffffffa0092000>] ? acpi_video_init+0x0/0x63 [video]
 [<ffffffff80430965>] driver_register+0x75/0x170
 [<ffffffffa0092000>] ? acpi_video_init+0x0/0x63 [video]
 [<ffffffff803ee8a6>] acpi_bus_register_driver+0x43/0x45
 [<ffffffffa0092041>] acpi_video_init+0x41/0x63 [video]
 [<ffffffff8020a041>] do_one_initcall+0x41/0x170
 [<ffffffff8026c261>] ? __blocking_notifier_call_chain+0x21/0x90
 [<ffffffff8027d085>] sys_init_module+0xb5/0x1f0
 [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b

```

---

### Post by evilg33k on 2008-12-12
> **gl2tosl2 said:**
> I have the intel wireless 5100 agn.  It works with 8.10 out of the box with the iwlagn driver.

I'll add 
5)  When booting on battery power the computer starts beeping like there's a panic of some kind.  When this happens the beeping doesn't stop until a reboot.  Once ALSA comes on the sound gets muted, but it's still there if I turn the volume up.

It indeed works out of the box but my bandwith seems limited... to about 80KB/s. Anybody else experience this?

Greetings,
Philippe.

---

### Post by amosbatto on 2008-12-21
I just updated the BIOS on my Thinkpad SL300 and then installed Ubuntu AMD64 8.10. Contrary to what others report I see no problem with battery applet in GNOME. Powertop, the default GNOME battery applet in the announcements part of the panel and the applet that you can add to the GNOME panel all work. Still they all display different estimates of remaining battery time (presumably because they calculate it differently). Right now the default GNOME applet shows 2 hours 10 minutes remaining on my battery, while powertop shows 2.9 hours.

---

### Post by amosbatto on 2008-12-22
It really bugs me that the brightness and volume keys on my Thinkpad SL300 don't work properly. It should be really simple to switch the position of the Brightness Up(Fn+End) and Brightness Down(Fn+Home) keys with Xmodmap. For instance to switch the position of the A and S keys, you can add the following lines to your .bashrc file:
```
Xmodmap –e ‘keycode 91 = a A’ 
Xmodmap –e ‘keycode 73 = s S’ 

```
Unfortunately this doesn't seem to work, because the Brightness keys don't seem to have normal keycodes assigned to them like other keys (at least I can't see any using xev). Any ideas?

Since I couldn't figure out how to switch the keys, I wrote a script to manually set the LCD screen brightness. Create a file **/usr/local/bin/bright** with the following text: 
```

#!/bin/bash

let current=`awk '/current/ {print $2}' /proc/acpi/video/VGA/LCDD/brightness`

if [ $# -eq 0 ]; then
	echo $current
	exit
fi

if [ $1 = "up" ]; then
	let new=$current+5
	if [ $new -eq 95 ]; then
		let new=100
	fi
elif [ $1 = "down" ]; then
	let new=$current-5
	if [ $new -eq 95 ]; then
		let new=90
	fi
elif [ $1 = "max" ]; then
	let new=100
elif [ $1 = "min" ]; then
	let new=20
elif [ $1 = "middle" ]; then
	let new=60
else 
	echo "bright reports the current LCD brightness level or sets new level."
	echo "  Usage: bright up|down|min|max|middle"
	echo "For example \"bright\" reports current brightness and \"bright up\"" 
	echo "increases LCD brightness by one notch"
	exit
fi

#check bounds
if [ $new -ge 95 ]; then
	let new=100
elif [ $new -le 20 ]; then
	let new=20
fi

echo $new > /proc/acpi/video/VGA/LCDD/brightness

```
 
Set the file so it is executable:
```
sudo chmod +x /usr/local/bin/bright

```

Add bright to /etc/sudoers, so anyone can change the screen brightness. Use the visudo command to safely edit the sudoers file:
```
sudo visudo
```

Add the line:
```
ALL ALL=NOPASSWD: /usr/local/bin/bright
```

Now the screen brightness can be increased and decreased with the commands "sudo bright up" and "sudo bright down". The current brightness can be displayed with the command "bright".

I wanted to bind these commands to the Brightness Up(Fn+End) and Brightness Down(Fn+Home) keys, but I couldn't figure out how to do it. In the end, I bound them to Ctrl+Alt+Home and Ctrl+Alt+End instead. Now I have to remember to press Ctrl+Alt instead of Fn. 

To bind the keys, open gconf-editor
```

gconf-editor

```
Go to **Apps > Metacity > keybinding_commands**. Right click on **Command_1** and select **Edit** from the drop down menu. Enter "sudo /usr/local/bin/bright up". In the same way, go to **Command_2** and set it to "sudo /usr/localbin/bright down". 

Now, bind keys to Command_1 and Command_2. Go to **Apps > Metacity > global_keybindings**. Right click on **run_command_1** and select **Edit Key**. Enter "<Control><Alt>End" (or whatever key combination that you want). Then go to **run_command_2** and set it to "<Control><Alt>Home".

Now the screen brightness should increase and decrease whenever you press Ctrl+Alt+Home or Ctrl+Alt+End. 

Still the default brightness level is the opposite of what it should be and it is a pain to have to press the new brightness keys after every boot, suspend, or hibernation or after plugging or unplugging your laptop. I went to System > Preferences > Power Management. In the On AC Power tab, under "Set Display Brightness to", I moved the slider bar to 0%. Since its really the opposite value, this should give me 100% brightness, but for some reason GNOME thinks that 80% is the maximum brightness. 80% is plenty bright with the LED backlight on the SL300, but it might not be enough on the SL400 and SL500 models which have a normal CCFL backlight. Then I went to the "On Battery Power" tab and unchecked the option "Reduce Backlight Dimness", so the screen won't grow lighter everytime you unplug the laptop and run on battery power. 

There is probably a better way to do this after resuming from suspend or hibernation or unplugging and plugging the power cord, but I don't know how APCI configuration files work in GNU/Linux. Any suggestions?

The other problem with the Thinkpad SL is the fact that the special audio volume keys don't work. You can get around this problem by binding Volume Mute, Volume Up and Volume Down to standard keys. Go to **System > Preferences > Keyboard Shortcuts** and click on **Volume Mute** and enter any key combination which you want toggle the audio on and off. Do the same for **Volume Up** and **Volume Down**. I used Ctrl+Alt+0 for mute, Ctrl+Alt+= for Volume Up and Ctrl+Alt+- for Volume down.

---

### Post by amosbatto on 2008-12-22
The Alps touchpad on my SL300 generally sucks. I hear that the SL400 and SL500 have good Synaptics touchpads, but the SL300 is stuck with a really crappy Alps unit. I figured out how to improve it a little bit under Ubuntu. By default, the mouse pointer will only move a very short distance across the screen, before you reach the edge of the touchpad. It generally takes 3 or 4 strokes to cross the screen, which is extremely tedious.

To fix this install gsynaptics:
```
sudo apt-get install gsynaptics
```

Now enable SHMConfig. If using Ubuntu 8.04, you can just add the line: 
```
Option "SHMConfig" "on"
``` 
in the synaptics section of your xorg.conf file. See: [https://help.ubuntu.com/community/SynapticsTouchpad/Hardy](https://help.ubuntu.com/community/SynapticsTouchpad/Hardy)

Unfortunately this doesn't work with Ubuntu 8.10 and later because all of the configuration has been removed from xorg.conf, so you need to edit a .fdi file to enable SHMConfig. 
See: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

I added the file /etc/hal/fdi/policy/alpstouchpad.fdi with the contents:

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">On</merge>
  </match>
 </device>
</deviceinfo>

```
 
The fdi settings are supposed to take effect whenever the device is plugged in again, but I couldn't figure out how to unplug and replug a touchpad, so I just rebooted with "sudo shutdown -r now".

If SHMConfig still isn't enabled when you reboot, you might try adding the line: 
```
<merge key="input.x11_options.SHMConfig" type="string">On</merge>

```
to the file /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

   
After enabling SHMConfig, go to **System > Preferences > Touchpad** to run gsynaptics. In the "Acceleration" tab, move the slider bars for "Max Speed", "Min Speed", and "Acceleration" to higher values possible. Now the Alps Touchpad should work better (although it still sucks in my opinion). 

If you want to set the touchpad properties so you don't loose your setting everytime you reboot, you can to set them in a .fdi file. Here is my /etc/hal/fdi/policy/alpstouchpad.fdi file:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">On</merge>
   <merge key="input.x11_options.MaxSpeed" type="string">1.00</merge>
   <merge key="input.x11_options.MinSpeed" type="string">0.60</merge>
   <merge key="input.x11_options.AccelFactor" type="string">0.80</merge>
  </match>
 </device>
</deviceinfo>

```

The other problem with the touchpad is the fact that the cursor keeps jumping around whenever I brush the touchpad when typing. Unfortunately I see the following error when I try to use **syndaemon** to disable the touchpad when I am typing:
```

$ syndaemon -d -i 1 
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  146 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Any ideas how to solve this?

---

### Post by UbuWu on 2008-12-26
Some good news: on Jaunty, on the SL300, the atheros wifi card works great out of the box. The other problems remain so far.

---

### Post by UbuWu on 2008-12-26
Here is a link to all bug reports related to the thinkpad SL series (5 currently):
[https://launchpad.net/ubuntu/+bugs?field.searchtext=sl300+OR+sl400+OR+sl500](https://launchpad.net/ubuntu/+bugs?field.searchtext=sl300+OR+sl400+OR+sl500)

---

### Post by UbuWu on 2008-12-26
Also on Jaunty, the SL300 webcam works perfectly.

---

### Post by jfr1tz on 2009-01-02
i just installed ubuntu 64 intrepid on my sl300

the following works
Camera (tested via gstreamer-properties)
wireless (intel5100) 
graphics (intel), i dont have the nvidia chip.
card reader and cd also work properly.
suspend/hibernate works and the cpu scaling also works.

stuff that doesnt work
volume keys
hdaps, the hdaps driver doesnt recognize the model, i could not find a bug report about this.
and the touchpad here is really slow, i havent tried the described fix above yet, will try that :P
The brightness levels are messed up, but i think for that a fix is already in the works or in a newer kernel.

I didnt change much of the settings after installation, except enabling laptop-mode , apparently that helps to reduce load/unload cycles.

i checked with a recent alpha of the next release, but it has the same problems.

---

