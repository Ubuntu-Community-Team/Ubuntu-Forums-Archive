---
title: "Sentelic Touchpad Configuration is Not Possible"
date: 2010-06-05
forum: Hardware
---

### Post by Gretha on 2010-06-05
Most MSI Netbooks come with a touchpad manufactured by Sentelic (Sentelic Finger Sensing Pad).  It appears that Ubuntu 10.4 offers some native support for Sentelic Touchpads, because on installed systems there is basic touchpad cursor moving and clicking functionality.

However, these Sentelic touchpads are wrongly recognized as a PS/2 Mouse.  (See eg the FSPPS/2 Sentelic FingerSensingPad listing in gconf-editor, or use the GPointing mouse and touchpad configuration application).  These Sentelic touchpads are also not listed as a tab in System > Preferences > Mouse.

As a consequence, these Sentelic touchpads cannot be configured.  This includes, for example, the absense of elementary options regarding touchpad sensitivity (Sentelic touchpads are by default hyper-sensitive, leading to many input errors), tap-to-click, de-activate while typing, horizontal and vertical scroll, etc.

It appears that this issue is addressed on [http://sourceforge.net/projects/fsp-lnxdrv/](http://sourceforge.net/projects/fsp-lnxdrv/).  However, this sourceforge page lacks any form of documentation, and it is entirely unclear what to do with the downloads available there.  And even if one would be able to get these downloads working, it is likely that the whole process needs redoing every time after a kernel update.

Also, [http://ubuntuforums.org/showthread.php?t=961324](http://ubuntuforums.org/showthread.php?t=961324) makes reference to some aspects of this issue.  However, the cryptic console instructions given there do not encourage non-tech users who rely on the Gnome GUI.  And, in addition, these instructions appear to be volatile, needing repeating after every reboot.  Besides, these console commands address only two of the several configurable touchpad settings.

Thus, there is an urgent need for Ubuntu to incorporate a native GUI configuration panel which allows the user transparently to configure all user-configurable settings of the Sentelic Touchpads.

What are the solutions for the non-tech user?

---

### Post by mzecher on 2010-06-13
+1

---

### Post by prytoluk on 2010-07-17
Dudes, i've found the solution!

I'm a new linux-user, so i've spent a couple hours trying to find out the solution, and nothing was working, til' i found something:

That "patched kernel" solution consists of installing the driver trough patching the kernel, so it would recognize the touchpad, and then using the configuration utility provided by Sentelic.

The awesome part is: The Ubuntu team has included the drivers for the Sentelic Touchpad in the current kernel for 10.04 version! So all you have to do is install the configuration utility.

Download FSPC through this link: 
[http://sourceforge.net/projects/fsp-lnxdrv/](http://sourceforge.net/projects/fsp-lnxdrv/)

Install the software and run with the following command:
sudo fspc
(if you don't do the sudo it won't save your preferences in the utility).
With this you can get the same thing the kernel compillers get without doing anything complicated!

Good Luck guys!

EDIT: If you did those steps, you can realize that after you reboot, it won't save your preferences, so here's a tutorial to fix this issue. After you install FSPC as above do the following steps:
#1- Open Gedit Text Editor and copy-paste the following (in red):
[COLOR=Red]EnableOnPadClick=0
EnableVScr=1
EnableHScr=1
Acceleration=2[/COLOR]

Note that you can change this settings, as "0" means "off" and "1" means "on", except for "acceleration", because the number means how much sensible it is. This are my settings (no click on touchpad, vertical scroll, horizontal scroll, and sensibility 2).

#2 - Save your preference file as "fspc.ini", in the following directory:
[COLOR=Red][username]/fspc/[/COLOR] - Just create a fspc folder in you personal folder.

#3 - Rename you "fspc" folder to ".fspc" - It should make the folder dissapear after you press F5 key, but that's the way, ".something" makes the folder invisible.

#4 - Open Gedit again and now you paste the following:[COLOR=Red]
#! /bin/bash
sudo fspc -t -l ~/.fspc/fspc.ini

[COLOR=Black]#5 - Save this new file as "start-touchpad" in your personal folder (the one that has your user name).

#6 - Right-button click your new created file -> properties -> permissions; and check the "execute as a program" 'or something like that' box (sorry, my ubuntu is in portuguese), now you close the properties.

#7 - Open up a new terminal and do the following commands:
[COLOR=Red]sudo cp start-touchpad /usr/bin[/COLOR]/
[COLOR=Red]sudo visudo

[COLOR=Black]#8 -  After the "sudo visudo" command, it should open an "in terminal" text editor, and you should paste the following line at the END of the file (it should be the last line):
[COLOR=Red][username] ALL=(ALL) NOPASSWD: /usr/bin/fspc[/COLOR]
Change the "[username]" thing to your actually username. As in my example:
miguel ALL=(ALL) NOPASSWD: /usr/bin/fspc

#9 - Now you press Ctrl+S to save your file and don't save the file as sudoers.tmp! Remove the TMP extension, so the file will be "/etc/sudoers", and confirm as it asks you to do.

Now for the grand finale:
#10 - In the top of your screen go to System->Preferences->Startup Applications (or Sessions, depending on your ubuntu version). Add a new program: as the following:
NAME: [COLOR=Red][COLOR=Black]Anything...[/COLOR]
[COLOR=Black]COMMAND: [COLOR=Red]start-touchpad
[COLOR=Black]COMMENTARY: [COLOR=Black]it doesn't matter[/COLOR][/COLOR]

[COLOR=Black]Now, when you reboot your pc, the touchpad will be exactly as you configured!
If you want to see the future results without rebooting do the following command in the terminal:
[COLOR=Red]start-touchpad

[COLOR=Black]Good look to you guys! And cheers to linux![/COLOR]
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by Jimmy S on 2010-08-06
Prytoluk, that worked! It wasn't in the Synaptic Package Manager, but it downloaded and installed very easily. And now I don't have that damn tap-click anymore! Thanks so much!

---

### Post by prytoluk on 2010-08-21
I add a long tutorial to my last post, i hope it will help somebody!

---

### Post by Liam O on 2010-08-26
Prytoluk, you're a new linux user? I'm scared to see what you'll be able to do when you're experienced.

---

### Post by Jimmy S on 2010-08-31
Prytoluk, thanks again, I was gonna figure out how to script it so I didn't have to fspc every time I turned my machine on but you beat me to it. Thanks! And thanks for the message telling me that you'd done it.

Jim

---

### Post by zecapistolas on 2010-09-01
That solution work with **Synaptics** Touchpad?! :confused:

---

### Post by prytoluk on 2010-09-01
> **Liam O said:**
> Prytoluk, you're a new linux user? I'm scared to see what you'll be able to do when you're experienced.
Yes, i've been using linux for almost 2 months.:D
You know, i've been really into it and searched a lot, i didn't really made nothing up from scratch. ;)

> **Jimmy S said:**
> Prytoluk, thanks again, I was gonna figure out  how to script it so I didn't have to fspc every time I turned my machine  on but you beat me to it. Thanks! And thanks for the message telling me  that you'd done it.

Jim
Nah, i were the lazy guy... I did the steps but i forgot to put them on this topic. It was only fair to help the community that helped me doing this steps.;)

> **zecapistolas said:**
> That solution work with **Synaptics** Touchpad?! :confused:
Dude, in the last ubuntu version (10.04) you should be able to configure your Synaptics Touchpad by going to System (next to "applications" and "places")->Preferences->Mouse and on the Touchpad section.
Synaptics Touchpads have integrated configuration utilities in Ubuntu (as far as i know).

If this doesn't work you should search for propper tutorials on google, like this one:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)


):P

---

### Post by joham34 on 2010-10-09
hi all ! I had the same problem, could not deactivate touchpad , even disabling it with FSPC I got a nicely working touchpad getting me on the nerves while typing . I found the solution here:[http://us.generation-nt.com/answer/cant-disable-touchpad-lucid-hp-pavilion-help-199430071.html](http://us.generation-nt.com/answer/cant-disable-touchpad-lucid-hp-pavilion-help-199430071.html) 
In asnwer 3 by J G  Miller who describes how to blacklist psmouse (the kernel module responsible for the touchpad function) 
It worked for me nicely , the only problem is that to activate it again I have to restart after commenting the line "blacklist mouse" in /etc/modprobe.d/blacklist-touchpad.conf
Good luck

---

### Post by linuxrev on 2011-11-28
Thanks for your help, prytoluk! Unfortunately, the Sentelic driver is not only Made in Taiwan, but also made for i386 architecture only. So I was out of luck with my nice i686/64bit system...

---

### Post by Limator on 2012-04-24
Hi prytoluk,

is your solution still working with current ubuntu 11.10/12.04?

thanks.

kind regards

---

### Post by GugaLG1974 on 2013-03-26
> **Limator said:**
> Hi prytoluk,

is your solution still working with current ubuntu 11.10/12.04?

thanks.

kind regards

Hi Limator,
Did u trie it? Did it work?
Tks

---

