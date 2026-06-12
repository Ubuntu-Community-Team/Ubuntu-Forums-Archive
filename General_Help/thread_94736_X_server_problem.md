---
title: "X server problem"
date: 2005-11-24
forum: General Help
---

### Post by Fittersman on 2005-11-24
I am having much trouble with installing Ubuntu 5.04. It installs fine but when I'm required to reboot and finish installing it gives me a black screen that is the terminal. The problem is that the screens are found but dont have a usable configuration or something. My video card is a radeon 7500, monitor is an optiquest something, computer is a compaq presario. There could be a problem with my intel(R) 82845G/GL/GE/PE/GV Graphics Controller because on my windows operating system I had to disable it because the cursor when moved to the left side of the screen it disappeared and kept going off the screen and disabling it seemed to fix the problem. 


when its installing and oking everything this fails: temporary failure in name resolution

and this is the warning thing i get after:

I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

and when i select yes i get this:

(a bunch of stuff that isnt important)

(==) using config file: /etc/X11/xorg.conf

skipping

/usr/X11R6/Lib/modules/extensions/LibGLcore.aim_debug_clip.0: No symbols found

skipping

/usr/X11R6/lib/modules/extension/libGLcore.aim_debug_norm.0: No symbols found

(EE) I810(0): cannot read V_BIOS 

(EE) I810(0): UBE initialization failed

(EE) Screen(s) found, but none have a usable configuration.

Fatal server error: no screens found

Then you click OK and it goes back to the other menu i gave you at the start
and when you click NO it says "I will disable this X server for now. Restart GDM when it is configured correctly.

After that instead of having the nice login screen and all that stuff all i receive is the terminal on a black screen.


this is the etc/X11/xorg.conf file (part of it anyway)

Section "Device"
Identifier "Intel corporation 82845G/G[Brookdale-G]/GE Chipset Inset Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
Endsection

Section "Monitor"
Identifier "Q71B-8"
Option "DPMS"
Endsection

Section "Screen"
Idenifier "Default Screen"
Device "Intel corporation 82845G/G[Brookdale-G]/GE Chipset Inset Integrated Graphics Device"
Monitor "Q71B-8"
Default Depth 24
Subsection "Display"
Depth 1
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubsection

Subsection "Display"
Depth 4
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubsection

Subsection "Display"
Depth 8
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubsection

Subsection "Display"
Depth 15
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubsection

Subsection "Display"
Depth 16
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubsection

Subsection "Display"
Depth 24
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubsection

Section "Serverlayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

Section "DRI"
Mode 0666


i hope someone in here can help me nothing i try seems to work.
i do konw the bare minimum to navigate in the terminal also.

---

### Post by RAOF on 2005-11-24
The X server is trying to use your Intel graphics chip.  Since I presume you don't have a monitor plugged in to that, when it scans for a monitor (to check that you won't possibly damage it by setting a way-too-high resolution), it can't find one and so does what you see.  (I think that's what the "cannot read v_bios means).

Now, the solution would be to disable your Intel graphics (which I presume is an integrated-on-the-motherboard thing) and get the X server to use your Radeon card.  To do this:
[LIST]
[*]Disable the "integrated video" in the BIOS (before the computer boots) if possible.  This will stop the X server automatically detecting your Intel graphics.
[*]Reconfigure the X server to use your ATI card.  To do this, login at the terminal, and run "sudo dpkg-reconfigure xserver-xorg".  When it asks what driver to use (there will be a big, long, list), select "ati"
[/LIST]
Then you should be able to login to the GUI by running
"sudo /etc/init.d/gdm restart"

---

### Post by RAOF on 2005-11-24
Ok, more step-by-step.

Disabling the integrated Intel video:
When you turn on your computer, there'll be some time where it says "Press <somekey> to enter setup" (or something like that) where <somekey> is generally ESC, F1, DEL or something similar.  You'll get into your BIOS setup, and there'll be a number of options: things like "basic setup", "integrated peripherals", etc.  Just go through each of those untill you find something marked "integrated video" or "integrated graphics" or similar, and set it to "disable"/"off".  Then save & exit your changes, and the Intel graphics should be disabled.

Now, for the reconfiguring of xorg.  When you boot into Ubuntu, you'll end up at a terminal (it'll say "xserver failed to start" blah) and it will say:
<yourcomputernname> login:
Type the user name that you set up when you installed Ubuntu.
It will then say
password:
Type your password.  You won't get any feedback (little *s instead of letters), but that's normal.
Then you should get a prompt like:
<username>@<yourcomputername>$
It is at that point that you want to type
```
sudo dpkg-reconfigure xserver-xorg
```
It will ask you for your password again.
Then it will go through the process of configuring X for you.  Since you've disabled the integrated Intel graphics, it should default to the ati driver for you.  **Check** that.  It will also ask a bunch of other questions (how much video ram do you have, keyboard layout).  The defaults (just pressing "enter") should do fine for almost all of these.
Once you've answered all of those questions, you'll go back to a terminal-prompt.  Type
```
sudo /etc/init.d/gdm restart
```]
and enter your password.  It should now load the GUI, and you're done.

---

### Post by Fittersman on 2005-11-24
thanks alot man im guna go and try it right now like you mean startup as in grub loader?

---

### Post by RAOF on 2005-11-24
I mean "startup" as in **before** the grub boot loader.  After you turn the computer on, before you get to the boot loader.

---

### Post by Fittersman on 2005-11-25
here is what is in my bios settings list thinger, one of my teachers recomended updating my motherboard but im not sure if i should do that or not.


MAIN

---System Time
---System Date
---Language
---Floppy Diskette A

--->Priamary master     [ST3120026A]
--->Primayy slave       [Auto]
--->Secondary Master    [Samsung DVD-ROM SD-616E]
--->Secondary Slave     [Lite-on LTR 482475]


ADVANCED

---Plug and play OS              [Yes]       (no)
---Reset Configuration data    [No]        (yes)
---Onboard Video memory      [8MB]       (1MB)
---Primary video adapter        [PCI]       (onboard)
---PS/2 Mouse                  [enabled]   (auto, disabled)
---USB Legacy Mode support     [enabled]   (disabled, auto)
---Supervisor password         [enter]
---Local Bus IDE adapter       [both]      (primary, secondary, disabled)
---onboard LAN                 [enabled]   (disabled)
---onboard Audio               [Auto]      (disabled, enabled)

--->Hardware Monitor
--->I/O Device Configuration

---

### Post by Fittersman on 2005-11-25
whenever i use sudo nano or pico or something like that with sudo in it i get a error 

sudo: unable to lookup (my computer name) via gethostbyname()

---

### Post by Mustard on 2005-11-25
[QUOTE=Fittersman]whenever i use sudo nano or pico or something like that with sudo in it i get a error 

sudo: unable to lookup (my computer name) via gethostbyname()[/QUOTE]

It sounds like you may need to edit your 'hosts' file which is found at /etc/hosts.  My guess would be it is misconfigured atm, for some reason.  After you have edited it you should be able to use 'sudo'  from your normal user login again.

I would think to do this that you need to login as root, since sudo is not functioning.  Possible methods of logging in as root are using the recovery mode option in your grub menu at startup (or possibly using your liveCD to log in as root in terminal).  An example of a hosts file is below;

```
127.0.0.1	localhost.localdomain	localhost	slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

The word 'slave' in the above file is what I call my computer.  You would need to subsitute the name that you gave your computer.  If you just chose the default option when installing, it is most likely called 'ubuntu'.

If you manage to work out how to log in as root through terminal, then you can use one of these commands to edit your /etc/hosts file;

```
nano /etc/hosts
or
pico /etc/hosts
```

If you are not sure what your hostname is there is a file called /etc/hostname as well.  The value contained in this file can be changed with the 'hostname' command, or you could simply view the file, determine what your hostname is from contents of the file and edit the /etc/hosts file to include the correct hostname.

For more detailed explanations of the commands mentioned above these commands below will allow you to view the manual for each command in terminal;

```
man hosts
man hostname
man nano
man pico
```

---

### Post by Fittersman on 2005-11-25
i cant edit without sudo though i can see whats in it but i cant edit it because my permission is denied.

and my hosts file only has:

127.0.0.1        localhost



thats it

you think reinstall ubuntu see if fix problem and what do you thnk about the whole updating motherboard thinger?

---

### Post by Fittersman on 2005-11-25
I thank you guys so much but now i need an internet connection to get set up so i dont have to switch between windows and ubuntu to see what you have to say

---

### Post by syntaxtothe on 2005-12-07
Thank God, I thought I had to reinstall ubuntu again -_-

---

