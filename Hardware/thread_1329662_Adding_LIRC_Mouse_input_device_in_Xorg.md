---
title: "Adding LIRC Mouse input device in Xorg?"
date: 2009-11-17
forum: Hardware
---

### Post by Blackie_Chan on 2009-11-17
I have Karmic 9.10 install and need advice on configuring lircmd to recognized my mouse pointer in ATI Remote Wonder's remote control.

I used to have the mouse pointer working in Ubuntu 9.04, and I'm using my old /etc/lirc/* files. In 9.04, I had to update /etc/x11/xorg.conf by adding:


```
Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/lircm"
        Option      "Protocol" "MouseSystems"
        Option      "SendCoreEvents"
EndSection
```


In 9.10, there is not xorg.conf, so I don't know how to add the LIRC-Mouse input device. I think the problem is because I didn't add the input device in 9.10, but how can I add it?

Thanks in advance.

---

### Post by sisco311 on 2009-11-17
You have to create a hal config file:
[thread]7680432[/thread] post #8

---

### Post by Blackie_Chan on 2009-11-20
> **sisco311 said:**
> You have to create a hal config file:
[thread]7680432[/thread] post #8

I think you mean [http://ubuntuforums.org/showthread.php?t=1148530](http://ubuntuforums.org/showthread.php?t=1148530)  post #8, It does not work for me.

---

### Post by Blackie_Chan on 2009-11-21
I added the following to 3 different locations (not all at the same time), and no luck.
```

blackie_chan@ubuntu:~$ more lirc_mouse.fdi 
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/lirc_mouse">
      <merge key="info.category" type="string">input</merge>
      <merge key="info.capabilities" type="strlist">input</merge>
      <append key="info.capabilities" type="strlist">input.mouse</append>
      <merge key="input.device" type="string">/dev/lircm</merge>
      <merge key="linux.device_file" type="string">/dev/lircm</merge>
      <merge key="linux.x11_options.Device" type="string">/dev/lircm</merge>
      <merge key="input.x11_driver" type="string">mouse</merge>
      <merge key="input.x11_options.Protocol" type="string">IntelliMouse</merge>
      <merge key="input.x11_options.Buttons" type="string">5</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
    </match>
  </device>
</deviceinfo> 

```

I placed the file in /etc/hal/fdi/policy, then /usr/share/hal/fdi/policy/20thirdparty, then /usr/share/hal/fdi/information/20thirdparty

After each placement, I couldn't find a /dev/lircm device and my LIRC mouse still wasn't working.

---

### Post by Krister Hallergard on 2009-11-29
Have struggled for over a month to install the LIRC-mouse and tried the same places as you for the fdi-file (I now believe that this is not the problem). Also I have no /dev/lircm but I do have a /var/run/lirc/lircm - so I have tried that destination in the fdi-file - but nothing changes.

I also have the lircmd daemon running!  But when it starts it gives this message in /var/log/messages:> lircmd: unknown protocol IntelliMouse#015 My /etc/lirc/lircmd.conf is the one recommended in the lirc package.

I saw a post somewhere re the fdi-file to add this line to /etc/rc.d/rc.local (or in Kubuntu somwhere similar?)
> hal-device --add lirc_mouse < /dev/null > /dev/null Have tried various places to add this line, but it doesn't seem important.

I would very much appreciate if we could help eachother to get the LIRC.mouse working.  My top priority is now the above protocol message and how to solve that!?

---

### Post by Krister Hallergard on 2009-12-03
Blackie_Chan, I would be interested to hear if you have had the same experience as me.

---

### Post by warp99 on 2009-12-12
Well I figured out that the lirc-mouse doesn't want to load until X server is running so with a combination of scripts and Blackie_Chan's fdi file I was able to make this work. The following assumes that you already have a working lircmd.conf file:

Remove any mention of the lirc-mouse remote in your /etc/X11/xorg.conf file and restart x server, ie: exit and login again. 

Next modify Blackie_Chan's fdi file to change the location of lircm:
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/lirc_mouse">
      <merge key="info.category" type="string">input</merge>
      <merge key="info.capabilities" type="strlist">input</merge>
      <append key="info.capabilities" type="strlist">input.mouse</append>
      <merge key="input.device" type="string">**/var/run/lirc/lircm**</merge>
      <merge key="linux.device_file" type="string">**/var/run/lirc/lircm**</merge>
      <merge key="linux.x11_options.Device" type="string">**/var/run/lirc/lircm**</merge>
      <merge key="input.x11_driver" type="string">mouse</merge>
      <merge key="input.x11_options.Protocol" type="string">IntelliMouse</merge>
      <merge key="input.x11_options.Buttons" type="string">5</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
    </match>
  </device>
</deviceinfo>
```
The changes are in bold to reflect the new location of the input. You could put a symlink from /dev/lircm but it has a chance of disappearing once you reboot if you don't have this defined in udev rules. Also make sure that you have lircmd being loaded in your /etc/lirc/hardware.conf file since this is turned off by default:
```

START_LIRCMD=**"true"**

```
Next I used the following script to load lirc_mouse into hal:
```
#!/bin/bash

test -f /etc/lirc/lircmd.conf || exit 0
        
STA=`lshal |awk '/'"lirc_mouse"'/ { ++x } END { print x }'`

    if [ -z "$STA" ]; then
        sudo /usr/bin/hal-device -a /org/freedesktop/Hal/devices/lirc_mouse </dev/null> /dev/null
    fi

exit 0

```
Save the file as lirc-mouse.sh, make it executable with "chmod +x lirc-mouse.sh" and copy the file into /usr/local/bin. If you notice sudo is called within the script so you have to make an exception so anyone with admin privileges can run this particular command without a password. To do this run "sudo visudo" and place the following code in the file:
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
**%admin  ALL = NOPASSWD: /usr/bin/hal-device -a /org/freedesktop/Hal/devices/lirc_mouse**
```

Logout and login again, then run the script. If everything is correct the script should run without a password and the remote mouse should be working

To have the mouse load on startup make a lirc-mouse.desktop file in your ~/.config/autostart directory with the following contents:
```
[Desktop Entry]
Name=LIRC Mouse
Comment=HAL input script to enable the LIRC Mouse
Exec=/usr/local/bin/lirc-mouse.sh
Type=Application
Encoding=UTF-8

```
After this the mouse remote will automatically load once you login to your desktop session.:D

---

### Post by Krister Hallergard on 2009-12-20
warp99, have read your post with great interest.  Have solved one of my problems:> lircmd: unknown protocol IntelliMouse#015  I had edited lircmd.conf in Windows creating Dos line ends rather than Unix line ends.  Fixing that I got the LIRC-mouse working on the Mandriva partition.

On the Kubuntu partition I had the additional problem that there was no recognition of the LIRC-mouse in /var/log/Xorg.0.log.  Applying your script, logging out and then in again to restart X, the LIRC-mouse was recognized in Xorg.0.log!

But I still cannot get the mousie to move, not even after restarting the daemons.  It seems that I am very close to getting it working, but something is still missing.  Any suggestion?

---

### Post by Krister Hallergard on 2009-12-21
It was easier than I thought, but took a bit of tweaking to find.  After applying warp99's script, I just executed:

sudo /usr/sbin/lircmd

Solved!  So I put both as scripts in autostart, and now the mousie is also moving on the Kubuntu partition. Thanks warp99!

---

### Post by Krister Hallergard on 2009-12-21
Just learnt an even easier way from jarajm: to use the new command lircmd --uinput.  Very easy!

---

### Post by Blackie_Chan on 2009-12-26
Thanks warp99, 

I followed your instructions above, rebooted, and everything works - my mouse cursor can be controlled by my remote.

---

### Post by reuben on 2010-02-24
There's an easier (albeit hackier) way to do this, using xautomation. See [http://flavor8.com/index.php/2010/02/24/how-to-control-the-mouse-pointer-with-a-remote-control/](http://flavor8.com/index.php/2010/02/24/how-to-control-the-mouse-pointer-with-a-remote-control/) for the config.

---

### Post by nomiz on 2010-03-11
Thanks warp99! You are an absolute hero! Finally got my mouse pointer working!

---

### Post by mesnyder on 2010-05-22
I've done everything above, but still no luck. lircmd is definitely running, I can see it in the process list. And /var/run/lirc/lircm exists. But I don't see any references to it in Xorg.0.log. I'm running 10.04.

---

### Post by nomiz on 2010-05-26
Same problem here: HAL is no longer installed on Ubuntu.

So should UDEV rules be written somewere??

---

### Post by lank23 on 2010-07-12
> **Krister Hallergard said:**
> Just learnt an even easier way from jarajm: to use the new command lircmd --uinput.  Very easy!

where and how do you use this new command. Been trying a few things, but does not seem to be working for me....

---

### Post by ccd on 2010-08-22
anyone got it working under 10.04? It was all working under 9.10.

---

### Post by nomiz on 2010-11-28
Indeed.. HAL is gone. Now what?

---

### Post by tominsf on 2010-12-03
After following the lirc.org instructions about modifying xorg.conf (which they confusingly call something else) and not getting anywhere, then finding cryptic, instructionless references to uinput on these forums, I did some web research and experimentation and eventually came up with the following method, which works for my Malicious Muskrat (10.10) box:


1.  Add to the file /etc/modules the entry

```
uinput
```

(this file is the list of modules to be loaded, and does what modprobe does)

2. in order to make the file /dev/uinput (created at boot by uinput, above) accessible to user space software, add a new file  /etc/udev/rules.d/uinput with one line:

```
KERNEL=="uinput", MODE="0666"
```

Oddly, this is not needed if I manually modprobe uinput rather than doing step 1, but I couldn't figure out how to modprobe it automatically at boot.  Note that you don't have to call the file uinput; you can call it anything you want.

3. Create a script in your home directory and add that script to System->Preferences->Startup Applications:

```
#!/bin/bash
lircmd --uinput
```

(Don't forget to make the script executable. I used a script because I have other lines in it that do other lirc-related things.   If you have just the one line, you can probably just put that line by itself in Startup Applications.)


4. Add a config file lircmd.conf in /etc/lirc/

---

### Post by lank23 on 2010-12-03
Nice!!!

Works on Ubuntu 10.04 also with 3 minor changes.

1: edit /etc/lirc/hardware.conf to stop the load of lircmd due we have a script to start this module

Line to edit in /etc/lirc/hardware.conf ensure that it is set to "false"
```

START_LIRCMD="false"

```

2:  When creating the udev rule file the line did not work, change to 

```

KERNEL=="uinput", MODE="0666"

```

and also save the file with a name of ##-uinput where the ## is something like 55, if you have a 55 just a the above to the next line in the file.

3:  If you are using Mythtv like I am you might want to use the toggle keyword in your /etc/lirc/lircmd.conf file. like so where the "Advance" is a key on your remote.  This way you can stop the mouse function use Mythtv, and then start it again as needed :)

```

TOGGLE_ACTIVATE * Advance

```

---

### Post by tominsf on 2010-12-05
Glad you confirmed that it works for someone else as well, lank23.

My default hardware.conf file already had the line keeping lircmd off at that stage, but yes, it needs to be there so things happen in the right order.

I've tried the rules file with MODE:= and MODE= and they both seem to work, but I've edited out the colon from my post just in case.  Looking at the man file for udev, I don't see why it should make a difference.

I agree completely with the need to turn off the mouse when you go into MythTV; I have ACTIVATE rather than TOGGLE_ACTIVATE so that when I push the remote button that I've set up to start MythTV I automatically leave mouse mode.

Meanwhile, I've set up a couple of keys to give me keyboard <RETURN> and <ESC> functionality while in mouse mode, using irxevent:

1.I added the line irxevent --daemon /home/myhomedirectory/.lircrc to my startup script 

2. I added lines to ~/.lircrc (that is, begin/end blocks) to evoke irxevent commands (see lirc.org webpage description of irxevent).

---

### Post by lank23 on 2010-12-05
> 
I've tried the rules file with MODE:= and MODE= and they both seem to work, but I've edited out the colon from my post just in case. Looking at the man file for udev, I don't see why it should make a difference.


Maybe it due that I am using 10.04 vs your 10.10 either way it is working.

---

### Post by ant2ne on 2011-03-27
> **lank23 said:**
> Nice!!!

Works on Ubuntu 10.04 also with 3 minor changes.

1: edit /etc/lirc/hardware.conf to stop the load of lircmd due we have a script to start this module

Line to edit in /etc/lirc/hardware.conf ensure that it is set to "false"
```

START_LIRCMD="false"

```

2:  When creating the udev rule file the line did not work, change to 

```

KERNEL=="uinput", MODE="0666"

```

and also save the file with a name of ##-uinput where the ## is something like 55, if you have a 55 just a the above to the next line in the file.

3:  If you are using Mythtv like I am you might want to use the toggle keyword in your /etc/lirc/lircmd.conf file. like so where the "Advance" is a key on your remote.  This way you can stop the mouse function use Mythtv, and then start it again as needed :)

```

TOGGLE_ACTIVATE * Advance

```irw shows output of my remote.```
ant2ne@leno-buntu:~$ irw
000000000000000b 00 SELECT XboxDVDDongle
000000000000000b 01 SELECT XboxDVDDongle
00000000000000cd 00 2 XboxDVDDongle
00000000000000cd 01 2 XboxDVDDongle

```But I can't get it to move my mouse or other actions in X. 
These steps aren't working for me. Is there some steps you had to perform before this?

---

### Post by lank23 on 2011-03-28
First let us know what version of Ubuntu you are using, this has only been proven on 10.04 and 10.10

I followed the step provided in post 19 and then I added in the edit's that I listed in my post 20.  This works fine for a Ubuntu 10.04 install and should work fine for 10.10 using only post 19 steps.

Post the output of these commands so we can help find the issue

```

cat /etc/lsb-release

```

```

uname -a

```

```

cat /etc/modules

```

```

lsmod | grep uinput

```

```

cat /etc/lirc/hardware.conf

```

```

cat /etc/udev/rules.d/*uinput*

```

```

cat /etc/lirc/lircmd.conf

```

lank23

---

### Post by rileyp on 2011-04-28
Hi
It works great for me 
This is what I did from go to woe.
1. Add this to xorg.conf
```
Section "InputDevice"
      Identifier "Remote"
      Driver "mouse"
      [COLOR=Red]#[/COLOR]Option "Device" "/dev/lircm"
      Option "Protocol" "IntelliMouse"
      Option "SendCoreEvents"
      Option "Buttons" "5"
      Option "ZAxisMapping" "4 5"
EndSection
```2.  Add to the file /etc/modules the entry
```
uinput
```3. Add a new file   /etc/udev/rules.d/uinput with one line:
     ```
KERNEL=="uinput", MODE="0666" 
```4. Add to /etc/rc.local ```
lircmd --uinput 
```5. create a lircmd.conf in /etc/lirc/ like this one: ```
#UNCONFIGURED
# To find out how to get a proper configuration file please read:
#    /usr/share/doc/lirc/README.Debian
PROTOCOL IntelliMouse
ACCELERATOR 2 30 5
TOGGLE_ACTIVATE * DVD
MOVE_N * Two
MOVE_NE * Three
MOVE_E * Six
MOVE_SE * Nine
MOVE_S * Eight
MOVE_SW * Seven
MOVE_W * Four
MOVE_NW * One
MOVE_N * Up
MOVE_E * Right
MOVE_S * Down
MOVE_W * Left
MOVE_IN * Chanup
MOVE_OUT * Chandown
BUTTON1_TOGGLE * Five
BUTTON2_TOGGLE * Zero 
BUTTON3_TOGGLE * Clear
BUTTON1_CLICK * OK
BUTTON1_CLICK * Mute
BUTTON3_CLICK * Pause
# BUTTONx_CLICK, BUTTONx_UP, BUTTONx_DOWN are also possible
```and modifying it to suit your particular remotes lircd.conf
I would like to confirm in xorg.conf the line```
 Option "Device" "/dev/lircm"
```Is this  line required ?
Edit I have removed this line and everything still works so its not required.
Rather than create a script  to start lircmd --uinput.   I simply added it to /etc/rc.local.   Others may like to do the same.

Thanks to everyone that helped with this:)
cheers rileyp

---

