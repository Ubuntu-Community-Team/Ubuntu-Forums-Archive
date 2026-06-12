---
title: "Installin 9600 GT?"
date: 2009-07-08
forum: Hardware
---

### Post by ROY.G.BIV on 2009-07-08
I just got a NVIDIA 9600 GT to replace a non-linux compatible ATI card. Now I need to install the driver, which scares the holy hell out of me. Last time i tried that with my ATI card, my whole systam crashed and I had to re-install. So, I have the current driver. Now I need to install it, and I'm guessing it isb't as easy as just running it. So I need instructions that work. I saw the article that Starcannon made(in the thread below this one), but they didn't work for me. Help please? I really want a working GPU in ubuntu. Thanks in advance.

EDIT: found the actual manufacturer instructions, but they didn't work either... please tell me that I didn't just waste more money on a GPU. 

```
sh NIVIDIA-linux-x86-185.18.14-pkg1.run
```I typed that in, as per the NVIDIA site and it says "cannot open" the said file. If I double click on the driver- nothing.

---

### Post by RJARRRPCGP on 2009-07-08
> **ROY.G.BIV said:**
>  

```
sh NIVIDIA-linux-x86-185.18.14-pkg1.run
```I typed that in, as per the NVIDIA site and it says "cannot open" the said file. If I double click on the driver- nothing.

You must use ```
sudo
``` and try again. 

(Permission likely was denied.)

---

### Post by ROY.G.BIV on 2009-07-08
Tried that already, same result. This can't be this hard...

---

### Post by bl4hbl4hbl4h on 2009-07-08
Did you stop the X-server first?

---

### Post by ROY.G.BIV on 2009-07-09
Yes, I did... or tried to. It shut down the gdm, but then when I typed in commands, nothing happened. I had to ctrl+alt+delete restart my comp because it wouldn't do anything. I even tried to re-start X-server; nothing.

Can I install this driver with envy? I haven't tried that yet because i was thinking it wouldn't be as effective. Plus, I would like to do it manually, I'm trying to learn this stuff.

---

### Post by kelvin spratt on 2009-07-09
You should be able to enable resricted drivers for your card that will download and install the correct driver but remember you have to remove all traces of failed installs first that also applies to the methods you are trying as well video drivers will only compile to a clean system, They will build against a successful previous  build

---

### Post by Yellow Pasque on 2009-07-09
I think you're spelling "nvidia" incorrectly. Use the tab key (auto-complete).

---

### Post by kelvin spratt on 2009-07-09
If you really want to build yourself the nvidia way I wrote this for parsix but it more or less the same and always works for me on most distros

**Howto 2: Install Nvidia Drivers on Parsix 64bit, 32bit, + 32bit on a 64bit machine. **

  
This howto is for 6,xxx/7,xxx/8,xxx Nvidia Graphic cards.

1) Go to [Nvidia driver download page]("http://www.nvidia.com/Download/index.aspx?lang=en-us")&#8734; and download it to your home folder.

2) Logout and press CTRL ALT DELETE to restart X.

3) When the log in screen appears press CTRL ALT F2 to get command line prompt.

4) Type following to login as root, and press ENTER after each line.

[FONT=monospace] user: root

password: (root password here)[/FONT]


5) Type following on the left command column and press ENTER after each line.

            
       NOTES AND ADDITIONAL INSTRUCTIONS                init 2        note: sometimes if you just init 3 it does not stop the xserver                init 3        note: now you are in level 3 and ready to install Nvidia drivers                cd /home/**username**/        change to your username                sh NVI        after that press TAB to use command line completion for long filename                
       
    

6) The installer will now start, follow the prompts. If you get unable to build kernel (ok) or cancel, press cancel, it should carry on anyway, ignore any errors.

7) Press ok to allow to configure settings. When it completes, type:
[FONT=monospace] init 5[/FONT]

this will start X and take you back to the login screen.

8) Login with your username and password.

9) You should now be using the Nvidia driver.

10) Now settings needs to be saved. Press ALT F2 to show command prompt and type:

[FONT=monospace] gksu nvidia-settings[/FONT]


This will start the nvidia settings manager.

11) Select X server display configuration, you can now change the settings, click [Apply], then if you are happy click [Save to x configuration file] and follow prompts.

12) Finally in the terminal type:

[FONT=monospace] glxgears[/FONT]


You should have good speed without any jerkyness. Compiz works without any alterations to your xorg file.

---

### Post by dfreer on 2009-07-09
You probably need to make sure the file is executable.

---

### Post by WildeBeest on 2009-07-09
This guide worked for me.
 
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

---

### Post by CLomax on 2009-07-09
For my 9600GT there are proprietary drivers in **System -> Administration -> Hardware Drivers**.

---

### Post by ROY.G.BIV on 2009-07-09
> **Temüjin said:**
> I think you're spelling "nvidia" incorrectly. Use the tab key (auto-complete).

Lol. no I just typed it wrong on my OP...

Kevin: How would I do the first thing you said? Enable the restricted drivers and removing all traces of previous install attempts? I see the Nvidia drivers in synaptic, but not the one I want.

Dfreer: it should be... I downloaded it from the site.

---

### Post by ROY.G.BIV on 2009-07-09
Deleted

---

### Post by ROY.G.BIV on 2009-07-09
Deleted

---

### Post by ROY.G.BIV on 2009-07-09
Well, I got it.... turns out the driver I downloaded was just a bad copy. Ran another install, and I got it to work using instructions that I had already tried...

So, driver's installed. But now, I have a problem with xorg. After I installed, I was told that I needed to configure it, and nvidia said to run "nvidia-xconfig" to do this. However, this is what it gave me:

```
Data incomplete in '/etc/X11/xorg.conf'. At least one device section is required.

ERROR: Unable to to map source file '/etc/X11/xorg.conf' for copying(No such file or directory)
```

I think that by trying to install the driver using so many different methods, I messed up my xorg.conf file or something... it does exist, because I tried to make it and it said that it already existed.

What do I do to fix this? I'm so close..

---

### Post by Yellow Pasque on 2009-07-09
```
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig
```

---

### Post by ROY.G.BIV on 2009-07-10
```


$ sudo dpkg-reconfigure xserver-xorg

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  At least one Device section is required.


ERROR: Unable to map source file '/etc/X11/xorg.conf' for copying (No such
       device)

$ grep -n "^(EE)" /var/log/Xorg.*.log

380:(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

$ grep -i "nvidia\|NVRM" /var/log/syslog

Jul  9 17:18:49 Lillith kernel: [11737.499220] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul  9 17:18:49 Lillith kernel: [11737.499232] nvidia 0000:01:00.0: setting latency timer to 64
Jul  9 17:18:49 Lillith kernel: [11737.499791] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.14  Wed May 27 02:23:13 PDT 2009
Jul  9 17:24:24 Lillith kernel: [    8.489459] nvidia: module license 'NVIDIA' taints kernel.
Jul  9 17:24:24 Lillith kernel: [    8.771127] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul  9 17:24:24 Lillith kernel: [    8.771140] nvidia 0000:01:00.0: setting latency timer to 64
Jul  9 17:24:24 Lillith kernel: [    8.771946] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.14  Wed May 27 02:23:13 PDT 2009
Jul 10 11:48:25 Lillith kernel: [    8.505249] nvidia: module license 'NVIDIA' taints kernel.
Jul 10 11:48:25 Lillith kernel: [    8.773535] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 10 11:48:25 Lillith kernel: [    8.773615] nvidia 0000:01:00.0: setting latency timer to 64
Jul 10 11:48:25 Lillith kernel: [    8.774532] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.14  Wed May 27 02:23:13 PDT 2009
Jul 10 12:46:35 Lillith kernel: [    8.825022] nvidia: module license 'NVIDIA' taints kernel.
Jul 10 12:46:35 Lillith kernel: [    9.084300] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul 10 12:46:35 Lillith kernel: [    9.084312] nvidia 0000:01:00.0: setting latency timer to 64
Jul 10 12:46:35 Lillith kernel: [    9.086667] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.14  Wed May 27 02:23:13 PDT 2009


```

Also see attachment.

---

### Post by Yellow Pasque on 2009-07-10
Sigh... did you have Synaptic open or something? Okay, more brute force.

```
gksudo gedit /etc/X11/xorg.conf
```

Paste this:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Save it. Quit gedit and try nvidia-xconfig again.

---

### Post by ROY.G.BIV on 2009-07-10
Yeah, I tried that once before... this is what it gives me when I run that: *Big red sign with a white dash through it* followed by: "/etc/Xll/xorg.conf is a directory. Please check that you typed the location correctly and try again."

if I navigate there manually, however, it lets me in but only shows a backup xorg file(xorg.conf.backup) that I made, but I can't access it or delete it(product of previous attempts, I think). It tells me it's of an unknown type.

Should I just delete all of it and re-install from fresh? Seems like the best solution to me.

---

### Post by Yellow Pasque on 2009-07-10
Before reinstalling, try:
```
sudo rm -rf /etc/X11/xorg*
```

Then try the stuff in my last post again.

---

### Post by ROY.G.BIV on 2009-07-10
Oops, too late... I figured out how to download it via package via synaptic, so I went with that. Still downloading, so I'll see how it goes. Hopefully good.

---

### Post by ROY.G.BIV on 2009-07-10
Lol, I figured out the problem. And it was something that I did following a different method... I knew it! 

The problem was in this: gksudo gedit /etc/default/linux-restricted-modules-common

At the bottom, where "disabled_Modules" is, I had "nv"l listed. I took that part out, ran Xconfig again and voila! After resetting X, I logged back in and presto! I now have a working graphics driver! 

Now to mess with the settings and see what this baby can do!

Thanks everyone for the help!

---

### Post by Yellow Pasque on 2009-07-10
> why won't xconfig run?
It looks like it ran to me :P

---

