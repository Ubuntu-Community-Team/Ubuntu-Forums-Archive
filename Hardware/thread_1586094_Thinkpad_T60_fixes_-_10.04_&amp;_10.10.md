---
title: "Thinkpad T60 fixes - 10.04 &amp; 10.10"
date: 2010-10-01
forum: Hardware
---

### Post by juhaszjozsef on 2010-10-01
Hi all...
I was thinking about starting a topic, describing my fixes for my IBM Thinkpad T60 laptop with ubuntu 10.04 and 10.10 as well.
*(Most of other Thinkpads have the same problems and solution as well)*

Just installed 11.04. Everything works as below:

_**Scrolling with trackpoint:**_
-install gpointing-device-settings and set it up like this:
System -> Preferences -> Pointing Devices -> TPPS/2 IBM Trackpoint
    -tick: use wheel emulation
    -select button 2 (middle button works as wheel :))

UPDATE: *some might noticed that after a suspend-resume cycle, middle button scolling isn't working anymore...*
Here is a fix which I found [here]("http://dlv.blogspot.com/2010/04/udev-xorgconfd-snippet.html")
Create a file eg. from terminal like:
sudo gedit usr/share/X11/xorg.conf.d/20-thinkpad.conf
and the contents of the file should be:
```
Section "InputClass"
    Identifier "Trackpoint Wheel Emulation"
    MatchProduct "TrackPoint"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    Option "EmulateWheel" "true"
    Option "EmulateWheelButton" "2"
    Option "Emulate3Buttons" "false"
    Option "XAxisMapping" "6 7"
    Option "YAxisMapping" "4 5"
EndSection
```


_**Volume notifications:**_
The hardware buttons work out of the box. Unfortunately there is no osd notification feedback...
You can find my original thread about this: [here]("http://ubuntuforums.org/showthread.php?t=1328016")
To sum it up:
-sudo gedit /etc/rc.local
 insert line before exit:
sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

The last lines should look like this:
```
#
# By default this script does nothing.
sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask
exit 0
```

Reboot and you're done. OSD notification works.
Tested on 10.04 and 10.10 as well!

**_Another annoying issue (for me) the Metacity window icons on the left._**
I prefer them on the right (MS style)
To do that:
Alt+F2 (run application)and type: gconf-editor
apps -> metacity -> general -> button_layout (double click to edit value)
 and enter this: ```
menu:minimize,maximize,close
```

Anyone has any more ideas please feel free to tell us about it.

---

### Post by zob on 2010-11-02
Maybe that's just mine. But my T60 wifi (iwl3945) keeps disconnecting on both 10.04 and 10.10. A workaround is:
gksu gedit /etc/default/grub

Change the CMD_LINUX_DEFAULT line to:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0 noplymouth"

sudo update-grub

Now it's stable on both 10.04 and 10.10.


Now on 10.10, everytime I try to shutdown, I only get the login-screen. Anyone has that problem?

---

### Post by Karut on 2010-11-02
your volume notification works fine except when I unmute I have to press either the higher or lower volume button to have sound on again. Any fix for that? Thanks a lot :)

has anyone experience with ubuntu and a thinkpad dockingstation?

---

### Post by keithpeter on 2010-11-15
Hello All

Useful thread, I've just received a T60-1952 model with integrated graphics and a 1024-768 screen, and Ubuntu 10.10 installed fine.

I too find that I need to unmute the volume and then press and up/down button.

I also find that the fan is coming on a lot of the time, even when the CPUs are running at less than 1% each...

I found that laptop-mode-tools were not installed, but they seem to make little difference. Any pointers would be helpful.

---

### Post by Karut on 2010-11-15
I now found the corresponding Launchpad-Bugs for the "unmute problem":

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281732](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/281732)

and here is the one with the OSD notifications:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/357673](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/357673)


About fan control:

The best-to-use fan-control is "Thinkpad Fan Control", as far as I know the only fan control program with a gui for Ubuntu. Unfortunately is doesnt work out-of-the-box with 10.10. But this worked for me:

Download to the desktop

[http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfand/tpfand_0.95-ubuntu1_all.deb](http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfand/tpfand_0.95-ubuntu1_all.deb)

[http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfan-admin/tpfan-admin_0.96-ubuntu1_all.deb](http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfan-admin/tpfan-admin_0.96-ubuntu1_all.deb)

The first package can be installed without problems, with the second package you have to do this:

1. creative the folder "**tpfan-admin-new" **extract the package to that folder
2. in the extracted folder go to folder "Debian" open the file "controls"
3. replace "**python-gnome2-desktop" [B]with** [/B]**"python-gnome2-desktop-dev**"
4. open up a terminal and type
> cd Desktop
cd tpfan-admin-new
dpkg-deb -D --build tpfan-admin_0.96-ubuntu1_all5. now install the **tpfan-admin_0.96-ubuntu1_all.deb** in the folder "[B]tpfan-admin-new"

[/B] 6. open up a terminal and type: sudo gedit /usr/lib/python2.6/dist-packages/tpfand/settings.py7. Replace the lines 170-174

> self.product_id = None
self.product_name = None
self.product_pretty_vendor = None
self.product_pretty_name = None
self.product_pretty_id = Nonewith the lines

> self.product_id = ""
self.product_name = ""
self.product_pretty_vendor = ""
self.product_pretty_name = ""
self.product_pretty_id = ""8. then: sudo /etc/init.d/tpfand restart


Credit for this has to go: 

[http://www.thinkpad-forum.de/software/linux/p962212-tpfan-admin-ubuntu-10-10/#post962212](http://www.thinkpad-forum.de/software/linux/p962212-tpfan-admin-ubuntu-10-10/#post962212)

---

### Post by T3ddyjunior on 2010-11-15
The desktop wont even show for my laptop, just the background screen and I have a IBM think-pad t43 what should I do? I just installed ubuntu 10.10

---

### Post by sunnynice on 2010-11-15
> **T3ddyjunior said:**
> The desktop wont even show for my laptop, just the background screen and I have a IBM think-pad t43 what should I do? I just installed ubuntu 10.10
 That's might not be hard prob to solve.

---

### Post by T3ddyjunior on 2010-11-15
yeah I figured 10.4 works but 10.10 doesn't so it must not be compatible.

---

### Post by tgalati4 on 2010-11-15
Perhaps you need a kernel switch to turn kernel mode-setting off.

---

### Post by keithpeter on 2010-11-17
> **Karut said:**
> 

About fan control:

The best-to-use fan-control is "Thinkpad Fan Control", as far as I know the only fan control program with a gui for Ubuntu. Unfortunately is doesnt work out-of-the-box with 10.10. But this worked for me:

Download to the desktop

[http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfand/tpfand_0.95-ubuntu1_all.deb](http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfand/tpfand_0.95-ubuntu1_all.deb)

[http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfan-admin/tpfan-admin_0.96-ubuntu1_all.deb](http://ppa.launchpad.net/tp-fan/ppa/ubuntu/pool/main/t/tpfan-admin/tpfan-admin_0.96-ubuntu1_all.deb)

Thanks Karut

I had to rename the temp folder to the name of the second deb file to get it to build a deb

When I installed the deb, I got a lot of dependency errors.

Investigating....

---

### Post by Karut on 2010-11-17
hmm...the dependency problem were the exact thing that we wanted to avoid...

which temp folder do you mean? Are you sure that you tried to install the edited package?

---

### Post by keithpeter on 2010-11-20
> **Karut said:**
> hmm...the dependency problem were the exact thing that we wanted to avoid...

which temp folder do you mean? Are you sure that you tried to install the edited package?

Hello Karut

On a fresh install of Ubuntu 10.10 on this T60 type 1952 (integrated graphics, 1024 by 768) I get the following...

Installing the first .deb

```
keith@T60:~/Desktop$ sudo dpkg -i tpfand_0.95-ubuntu1_all.deb
[sudo] password for keith: 
Selecting previously deselected package tpfand.
(Reading database ... 155433 files and directories currently installed.)
Unpacking tpfand (from tpfand_0.95-ubuntu1_all.deb) ...
Setting up tpfand (0.95-ubuntu1) ...
Installing default configuration file /etc/tpfand.conf
Reloading thinkpad_acpi module...
 * Starting ThinkPad fan control daemon tpfand                           [ OK ] 
Warning: unable to get your system model from HAL.
Traceback (most recent call last):
  File "/usr/sbin/tpfand", line 22, in <module>
    tpfand.control.main()
  File "/usr/lib/python2.6/dist-packages/tpfand/control.py", line 362, in main
    start_fan_control(quiet)     
  File "/usr/lib/python2.6/dist-packages/tpfand/control.py", line 314, in start_fan_control
    daemonize()
  File "/usr/lib/python2.6/dist-packages/tpfand/control.py", line 354, in daemonize
    daemon_main()   
  File "/usr/lib/python2.6/dist-packages/tpfand/control.py", line 254, in daemon_main
    act_settings = settings.Settings(system_bus, '/Settings')
  File "/usr/lib/python2.6/dist-packages/tpfand/settings.py", line 61, in __init__
    self.load()
  File "/usr/lib/python2.6/dist-packages/tpfand/settings.py", line 97, in load
    self.load_profile()
  File "/usr/lib/python2.6/dist-packages/tpfand/settings.py", line 102, in load_profile
    profile_file_list, self.loaded_profiles, self.id_match = self.get_profile_file_list()
  File "/usr/lib/python2.6/dist-packages/tpfand/settings.py", line 136, in get_profile_file_list
    product_path = product_name_dir + self.product_name
TypeError: cannot concatenate 'str' and 'NoneType' objects
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for python-central ...
```

Pressing on and making the folder you suggested on the desktop, and extracting the contents of the second deb, I found it necessary to make a folder with the name of the deb, and move the DEBIAN and usr folders to that, otherwise the command to build the deb failed. Below is what I got when I ran the command to make the deb file within the admin-temp directory

```
keith@T60:~/Desktop/tpfan-admin-new$ dpkg-deb -D --build tpfan-admin_0.96-ubuntu1_all 
dpkg-deb: warning: 'tpfan-admin_0.96-ubuntu1_all/DEBIAN/control' contains user-defined field 'Python-Version'
dpkg-deb: building package `tpfan-admin' in `tpfan-admin_0.96-ubuntu1_all.deb'.
dpkg-deb: warning: ignoring 1 warnings about the control file(s)
```

Finally, when installing the modified deb, I got this

```
keith@T60:~/Desktop/tpfan-admin-new$ sudo dpkg -i tpfan-admin_0.96-ubuntu1_all.deb
Selecting previously deselected package tpfan-admin.
(Reading database ... 155458 files and directories currently installed.)
Unpacking tpfan-admin (from tpfan-admin_0.96-ubuntu1_all.deb) ...
dpkg: dependency problems prevent configuration of tpfan-admin:
 tpfan-admin depends on python-gnome2-desktop-dev (>= 2.22); however:
  Package python-gnome2-desktop-dev is not installed.
dpkg: error processing tpfan-admin (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 tpfan-admin
```

And attempting to install the missing library lead to this...

```
keith@T60:~/Desktop/tpfan-admin-new$ sudo apt-get install python-gnome2-desktop-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 python-gnome2-desktop-dev : Depends: python-brasero (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-bugbuddy (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-evince (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-evolution (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-gnomedesktop (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-gtop (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-mediaprofiles (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-metacity (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-rsvg (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-totem-plparser (>= 2.30.0-1ubuntu5) but it is not going to be installed
                             Depends: python-gnome2-dev but it is not going to be installed
                             Depends: python-gtk2-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

After which I gave up. Any further tests I can do let me know, but I'm removing the first deb for now...

I noticed that on the second install of 10.10, the rear (noisy) fan isn't quite as aggressive, it isn't always on. The fan by the front right of the laptop under the right palm rest is always spinning but slowly and quietly.

---

### Post by Karut on 2010-11-24
[FONT=Verdana]Does the line below exist in your /etc/modprobe.conf ?
[/FONT]
[PHP]

  options thinkpad_acpi experimental=1 fan_control=1
[/PHP][FONT=Verdana]
[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]From what I heard the package that tpfand needs was called "python-gnome2-desktop" 10.04 and in 10.10 its called "[/FONT][FONT=Verdana]python-gnome2-desktop-dev". Thats why its only necessary to change the line in the controls file and not install another package.
[/FONT]


[FONT=Verdana]Try to install "python-rsvg" separately - thats the package tpfand needs, but its usually included in [/FONT][FONT=Verdana]"python-gnome2-desktop-dev".[/FONT]


[FONT=Verdana]Or try [/FONT]

sudo apt-get -f install ubuntu-desktop[FONT=Verdana]
[/FONT]
[FONT=Verdana]I will check tomorrow if I installed "python-gnome2-desktop-dev"[/FONT]


[FONT=Verdana]I have no idea why [/FONT][FONT=Verdana]"python-gnome2-desktop-dev" isnt installed [/FONT]:confused:
 







[FONT=Verdana]Or you just have to wait for an update of tpfand...
[/FONT]

---

### Post by Haim on 2010-11-24
@kamut

Cheers, your instructions worked perfectly!

I don't really know what I'm doing with the fans, so I probably frazzle my machine, but hey, at least it's quiet right? :)

---

### Post by Karut on 2010-11-25
@keithpeter: [FONT=Verdana]"python-gnome2-desktop-dev" is installed on my machine

@haim: yes I am also not sure yet where I will set my trigger points

And I also dont know exactly which sensor belongs to which part of the notebook even though I found this:

[http://www.thinkwiki.org/wiki/Thermal_sensors](http://www.thinkwiki.org/wiki/Thermal_sensors)

Does anyone know more and how warm i.e. the battery can get?
[/FONT]

---

### Post by Fafler on 2010-11-26
I have a T60p with 10.10. I just added the 2.6.37 kernel from the mainline PPA in the eternal quest for a better Ubuntu experience. Now powersaving works on the Radeon chip and i'm able to powersaving using this method: [http://www.phoronix.com/forums/showpost.php?p=145320&postcount=143](http://www.phoronix.com/forums/showpost.php?p=145320&postcount=143)
Set it to mid speed, as low makes the display jitter. Gaming performance seems unaltered and the un-ubuntunized kernel behaves slightly different, but i havent expereinced any actual problems.

The GPU temperature dropped from 88 to 65 degrees celcius idle and it doesn't boil my potatoes anymore. As for battery life, i havent tested it yet, but i expect a real improvement.

---

### Post by Karut on 2010-11-26
do you have to link to that kernel?

Whats interests me it your actual power consumption, for that install powertop, run it and switch to your battery. Thanks :)

I dont go under 13W with no WLAN, USB_Suspend, lowest brightness level and c4...

---

### Post by Fafler on 2010-11-27
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/)
Just download the kernel and dpkg -i it. Remember to get headers and stuff if you depend on it.

Didn't know powertop could do that. Nice :-)
It uses 23 watts, but i haven't taken any other measures to improve battery life, except speedstepping and now this.

Does anyone know it theres a usable internal USB connector somewhere inside the T60p? Is the PCIe slots completely wired or do they come without the USB part? Using a fast flashdrive for the OS and the HDD for secondary file storage would be a good improvement.

Any other tricks i need to know to improve battery life?

---

### Post by keithpeter on 2010-11-27
> **Karut said:**
> @keithpeter: [FONT=Verdana]"python-gnome2-desktop-dev" is installed on my machine

@haim: yes I am also not sure yet where I will set my trigger points

And I also dont know exactly which sensor belongs to which part of the notebook even though I found this:

[http://www.thinkwiki.org/wiki/Thermal_sensors](http://www.thinkwiki.org/wiki/Thermal_sensors)

Does anyone know more and how warm i.e. the battery can get?
[/FONT]

Hello Karut

Installing the python-gnome2-desktop-dev package brought down around 30Mb of stuff, and then the rest of the recipe worked and I have the tpfan in the system menu now. Thanks for taking the time to check your installation.

I'll be trying various settings, and I'd like to sort something out for the front right fan as well as the really loud one at the back left! I get the 'could not get system name from hal' type warning.

Hello Fafler & Karut

On this T60-1952 with intel integrated graphics, powernod is claiming 12.6 watts having turned bluetooth off and agreed to wifi saving, compared with about 16 to 18 watts when the rear fan was blowing cold air. The screen is down low. I get an error message about 'screen brightness interface' when booting the laptop and there are only 4 stages of screen brightness.

---

### Post by Karut on 2010-11-28
> Hello Karut

Installing the python-gnome2-desktop-dev package brought down around  30Mb of stuff, and then the rest of the recipe worked and I have the  tpfan in the system menu now. Thanks for taking the time to check your  installation.

No problemo. So you just tried to install the entire package a second time?


About saving power: 12,6W isnt that bad with WiFi on, did you leave your T60 idle for about 5-10Min and then checked? On Win XP I get down to 7,5W without any major changes in files - just Wifi/Bluetooth off, lowest brightness and lowest power consumption profile on. And this is something that is really making me turn my back on Ubuntu...
But this as well as the many wakeups in powertop is a know issue for the current kernels. I might have to try Fafler's kernel or wait for the next official update.

---

### Post by keithpeter on 2010-11-28
> **Karut said:**
> No problemo. So you just tried to install the entire package a second time? 

Yup

Power use

With networking disabled and wifi off using the hardware switch, I got 10.4w on powertop with sensor 0 around 43 deg C

With wifi on and firefox & dropbox loaded with two tabs in firefox (no videos) I get 13.3 to 14 watts

Watching a video on the bbc news pops the power up to 20.8 watts and the fan starts (I set an initial 15% trigger at 50 deg C)

Trying the new kernel does not seem to make much difference, I did get down to 9.9 watts with wifi off &c. However, the headers would not install (dependencies) so I'll take the new kernel off I think as I don't want problems upgrading.

Sensor 4 has been stuck to exactly 50 deg C all day and was at that temperature when I first booted the computer so I suspect its a dummy entry as this T60-1952 has integrated graphics.

Anyone any ideas about the brightness adjustment? Just 4 levels instead of 7 on the T42 and on this machine on Windows

---

### Post by The_Aegidius on 2011-02-14
I have got this laptop with Ubuntu 10.10 and everything works perfectly, except the sound that give me some problem when I reproduce movies.

[That]("http://www.egidiocaprino.it/Untitled.ogg")'s how sounds a tv-series intro song.

I can listen to music and internet videos/songs perfectly, but not local movies. I tried with different movies and I got the same problem with all of them.

Can I do something to solve it?

---

### Post by zob on 2011-02-15
I don't think that is a T60 related problem as such. I don't get that problem.

For better support I suggest you open a thread in category mutimedia and video: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

Remember to tell them the stuff you left out here. What player is affected? Is it totem? Did you try another player? Same problem?

You could try VLC if you didn't.
```
sudo apt-get install vlc
```

---

### Post by The_Aegidius on 2011-02-15
Thanks for the answer and for the advice.

I just use VLC.

---

### Post by dave2001 on 2011-03-06
Info on Thinkpad Fan Control -aka tpfan

I use two Thinkpads, a T60 and an ancient A20m. Ever since 8.04 tpfan is the only thing I've found which keeps my Thinkpads from getting hot enough to burn my thighs. The creator stopped updating them a few versions ago. The bugs have been identified, so you could modify the code yourself as described earlier in the thread, but...

Good news for the lazy! Someone else has updated tpfand and tpfand_admin for lucid 10.04 and maverick 10.10.

I've been using these since installing 10.04. No problems yet.

The launchpad ppa for the deb packages is: [https://launchpad.net/~jcollins/+archive/jaminppa]("https://launchpad.net/%7Ejcollins/+archive/jaminppa")

Note: Make sure to install tpfand first, followed by tpand_admin. Use sudo commands to install these debs, as I've encountered problems if they are not installed with root authority. As someone earlier mentioned, make sure you have acpi fan control enabled however your Ubuntu version requires.

ALSO, just a reminder: Read up on Thinkpads, thermosensors, and how to use tpfan before setting your temperature thresholds. You can fry your hardware if your settings are too high.

---

### Post by The_Aegidius on 2011-03-13
That's for the temperature control?

I think it's a problem of drivers.

---

### Post by dave2001 on 2011-03-14
> **Karut said:**
> your volume notification works fine except when I unmute I have to press either the higher or lower volume button to have sound on again. Any fix for that? Thanks a lot :)

has anyone experience with ubuntu and a thinkpad dockingstation?

Hi Karut, not sure if anyone else has mentioned this. I just wanted to point out the mute button on the Thinkpad T60 keyboard is not a toggle. It is only a mute button. Thus you must hit a volume up/down key to unmute. The mute button also functions this way with an oem windows install. Since this is the built-in functionality of the button, there may not be a "fix" for it. 

Cheers to fellow Thinkpuntu users!

---

### Post by Sudhan65 on 2011-03-16
Hi,

I am new to linux and trying to install ubuntu on my IBM T60 laptop. I alrelady have windows XP installed on it. Tried some googling to find but can't find proper instructions :(Can anyone guide me an appropriate url or manual to install it

---

### Post by dave2001 on 2011-03-21
Sudhan65-
What exactly would you like to do? Are you planning on getting rid of windows XP entirely and using ubuntu instead? Or are you more interested in having a dual-boot system (with either XP or Ubuntu available at startup)? These would be different installation processes.

---

### Post by juhaszjozsef on 2011-04-02
Just installed Ubuntu 11.04 beta.

Same bugs:
-OSD notifications
-Ultranav scrlolling

Same fixes work as described on thread #1.

---

### Post by dre12b on 2011-04-02
Anyone know what the best trackpoint sensitivity adjustment method is on 11.04 or 10.10?  

I hay to try several until I found one that worked on 10.04, but I unwisely did not make notes.  Had to reinstall my system recently (disastrous gnome3 experiment) and would like to get the trackpoint back to where I like it without half an hour of trial and error.  Thanks for the helpful thread.

I spent a lot of time getting my power consumption down in W7 (undervolting, tpfancontrol, etc) before making the switch to Ubuntu, but I just don't have the time or energy to repeat.  When I do, I'll definitely be back here to check out the advice.  Thanks for the detailed sharing.

---

### Post by juhaszjozsef on 2011-04-02
I would try installing **gpointing-device-settings** from synaptic, then you'll have additional options in the Pointing devices settings.

Maybe it helps.

---

### Post by dre12b on 2011-04-03
Thanks for the reply, but what I'm interested in editing are the speed and sensitivity of the trackpoint.  

There are several methods outlined here, but I can't keep track of what methods are deprecated (HAL, ?).  That's why I'm wondering what other folks here use to adjust speed and sensitivity.

---

### Post by dre12b on 2011-04-03
Reporting back...

The method listed [here]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Sensitivity_.26_Speed") worked for me to adjust the speed and sensitivity of the trackpoint in 11.04 beta, with one caveat.  For some reason, using sudo from the command line did not allow me to echo the new speed and sensitivity values into the respective files.  Strange, because I remember doing this in previous versions of Ubu.  However, sudo nano did allow me to directly edit the files for live testing.  Adding the echo commands to /etc/rc.local did make them persistent.

---

### Post by dave2001 on 2011-04-07
To dre12b -

This is the method I use for trackpoint sensitivity in 10.04, it works great.

create a new file:
 
[gksudo gedit /etc/udev/rules.d/trackpoint.rules]

and put the following in it:

 [SUBSYSTEM=="serio", DRIVERS=="psmouse", WAIT_FOR="/sys/devices/platform/i8042/serio1/serio2/sensitivity", ATTR{sensitivity}="225", ATTR{speed}="120"]

Note: The numerical values for speed and sensitivity can be anything between 0 and 255 to adjust responsiveness.

---

### Post by mufakir on 2011-04-09
Hi, just installed 10.10 on my t60p and I can't see the desktop. Tried uninstalling mutter but no go. Need help. Its dual booting with windows 7. Is it a graphics card driver problem? Please help.

---

### Post by pjman on 2011-04-10
> **mufakir said:**
> Hi, just installed 10.10 on my t60p and I can't see the desktop. Tried uninstalling mutter but no go. Need help. Its dual booting with windows 7. Is it a graphics card driver problem? Please help.

It's a bug that I hope gets fixed soon :) I've been using Unity 2d in the meantime.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/745996](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/745996)

---

### Post by mufakir on 2011-04-10
> **pjman said:**
> It's a bug that I hope gets fixed soon :) I've been using Unity 2d in the meantime.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/745996](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/745996)

Thanks PJMan, I'm pretty new to Ubuntu, so can you tell me what's unity 2d? I think it's a package but I am not sure. What do you suggest that I do right now? I want to move from Windows to Ubuntu.

---

### Post by dave2001 on 2011-04-12
@mufakir

If you have an ati graphics card in that T60, then it may very well be a driver issue. I have a radeon mobility x1400 in mine, and the driver that ubuntu automatically uses for it causes problems.
If you do indeed have the an ati card, this may fix the problem enough to get into your desktop:
At the Grub2 boot menu, select your newest kernel line, and press 'e'. (If you see no menu during boot, hold the shift key while you boot to enter it). Pressing the 'e' key will allow you to add a one-time boot parameter to your currently selected kernel line. 
Add the option "radeon.modeset=0" at the end of the line
If this fixes the problem, you can make it happen automatically every bootup by typing in terminal:
gksudo gedit /etc/grub/default
This brings up a text file, Add the same option as above to the file, at the end of the line: CMDLINE_LINUX_DEFAULT

If you don't have an ati graphics card in your T60, or you do but this doesn't help, perhaps it's the bug mentioned earlier. I don't have any experience with that particular bug.

---

### Post by kear123 on 2011-04-14
i get that problem too when i try to login as root,but when login as other user,no such problem....:confused:

---

### Post by juhaszjozsef on 2011-07-08
Updated the first post with a fix for middle button scrolling after suspend / resume...

---

