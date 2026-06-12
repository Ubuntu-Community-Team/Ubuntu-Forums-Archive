---
title: "Acer Timeline 4810T"
date: 2009-07-12
forum: Hardware
---

### Post by mopay on 2009-07-12
I bought the acer Timeline 4810T and not work  the CD/DVD recorder.

Recognized but when you insert a cd or dvd says there is no medium.
This is the dmesg output

[I][   20.210145] sd 1:0:0:0: [sda] Attached SCSI disk
[   20.210190] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   20.212379] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-U633A  AC01 PQ: 0 ANSI: 5
[   20.217927] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   20.217931] Uniform CD-ROM driver Revision: 3.20
[   20.218017] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   20.218057] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   20.218702] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   20.218721] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   20.218736] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[   20.218740] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   20.218801] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1[/I]

and this when trying to mount it manually

me@me-laptop:~$ sudo mount -t iso9660 /dev/sr0 /media/cdrom0
[sudo] password for me: 
montar: no se encontro medio en /dev/sr0
me@me-laptop:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom0
montar: no se encontro medio en /dev/sr0  [no medium found]

---

### Post by miegiel on 2009-07-22
According to [_this thread_]("http://ubuntuforums.org/showthread.php?t=1165087") most problems with the 3810T are solved by installing ubuntu 9.10 which will be released in october. It might solve your problem too.

[s]You can get 9.10 alpha2 [_here_]("http://cdimage.ubuntu.com/releases/9.10/alpha-2/"). Beware, 9.10 is still in development.[/s]
You can get 9.10 alpha3 [_here_]("http://cdimage.ubuntu.com/releases/karmic/alpha-3/"). Beware, 9.10 is still in development.

**Edit:** alpha2 has just been succeeded by alpha3 ;)

---

### Post by OrnithO on 2009-07-24
> **miegiel said:**
> According to [_this thread_]("http://ubuntuforums.org/showthread.php?t=1165087") most problems with the 3810T are solved by installing ubuntu 9.10 which will be released in october. It might solve your problem too.

Nice try but unfortunately the 3810t doesn't have a optical drive... so I'm not sure it will solve the problem but it could.
Personally I bought the Timeline 4810TZ-4011 and almost everything is working very well, including wifi and fn keys. I had to install a driver for the Ethernet RJ-45 port. THe two things that refuse to work are the touchpad lock (it locks correectly but then I am not able to unlock it and have to reboot.) and the internal mic (the external mic works).

For your problem, check the integrity of the cd you used for the installation on your laptop (If you still have it).
To do so put the cd in your drive at boot (as if you wanted to install ubuntu) and then select " Check CD for defects" or " Check the integrity of the CD" or something like that. I had an error and didin't saw it first...
I had something like you, a kind of weird error when I eject a DVD and I was only able to read DVD's which were already in the drive before booting (otherwise it tells me there is no media in the drive) and then I check the Cd which I used to instal LinuxMint (wich is almost the same as Ubuntu) and saw there was a corrupted file.

If you have an error I think you should reinstall Ubuntu, at least I don't know any other ways...

Hope it helps and sorry for my bad english, I hope you understood me. (It isn't my first language.)

Ps. If anybody has a solution for my problems (the touchpad lock and the internal mic) I would be grateful, thanks

---

### Post by miegiel on 2009-07-25
> **OrnithO said:**
> Nice try but unfortunately the 3810t doesn't have a optical drive... so I'm not sure it will solve the problem but it could.
Hmm ... yeah ... I should have motivated my post a bit more :)

My reasoning for trying the up coming ubuntu was, that sometimes new hardware isn't supported in the latest ubuntu yet, but is supported in the next ubuntu.

> Personally I bought the Timeline 4810TZ-4011 and almost everything is working very well, including wifi and fn keys. I had to install a driver for the Ethernet RJ-45 port. THe two things that refuse to work are the touchpad lock (it locks correectly but then I am not able to unlock it and have to reboot.) and the internal mic (the external mic works).

...

Regarding the touchpad lock, there are some posts on it in [_the thread I mentioned above_]("http://ubuntuforums.org/showthread.php?t=1165087"). Posts #108 #118 in the thread claim the touchpad lock works correctly in 9.10 alpha2.

Regarding the internal mic, you probably need to select which mic you want to use in the volume control pannel.

Since a few days, there is also an Acer Timeline page on the Ubuntu Documentation pages (with a link to some fixes).
[https://help.ubuntu.com/community/AspireTimeline](https://help.ubuntu.com/community/AspireTimeline)

---

### Post by OrnithO on 2009-07-26
> **miegiel said:**
> Hmm ... yeah ... I should have motivated my post a bit more :)

My reasoning for trying the up coming ubuntu was, that sometimes new hardware isn't supported in the latest ubuntu yet, but is supported in the next ubuntu.
You are right I didn't tought about that :)

> **miegiel said:**
> Regarding the touchpad lock, there are some posts on it in [_the thread I mentioned above_]("http://ubuntuforums.org/showthread.php?t=1165087"). Posts #108 #118 in the thread claim the touchpad lock works correctly in 9.10 alpha2.
It is a solution indeed but I prefer to have something more stable even if one small button is not working...
If there are no other solutions, it think i will wait until october then...
However I am getting close to something that looks like a solution (see [my new thread]("http://ubuntuforums.org/showthread.php?t=1223355") for more info)

> **miegiel said:**
> Regarding the internal mic, you probably need to select which mic you want to use in the volume control pannel.
Indeed, I should have seen that but selecting HDA Intel (Alsa Mixer) in the volume control then under options I just changed Front Mic by Int Mic I don't know I could have missed that... :confused: 

Thanks a lot for all the answers in such a short time.

---

### Post by exosyst on 2009-08-05
Hey there, received my acer yesterday and I'm impressed! I had to use the libata.force=noncq thing and installed the wireless drivers but it seems to have gone well so far.

Out of the box:
Suspend/Hibernate, Wifi, Sound, Webcam, correct resolution

Fixed:
libata setting, installed wired ethernet driver as per wiki. CD-Rom was an odd one, wasn't showing initially and then i tapped eject during a boot and it has worked ever since (HW detection?).

Broken:
FN keys for brightness (triggers the popup and shows 'alleged' status but doesn't actually change it - any ideas?
The mouse lock/unlock thing is only currently solvable by suspend/wake or logout/login. Something is wrong here but I am going to play with it to see what i can do.

This is all with the 4810T (not the TG) and Ubuntu 9.04.

---

### Post by OrnithO on 2009-08-05
> **exosyst said:**
> 
Broken:
FN keys for brightness (triggers the popup and shows 'alleged' status but doesn't actually change it - any ideas?

Yes, you can fix it. the solution is shown [here]("http://ubuntuforums.org/showthread.php?t=1217421&highlight=4810t").

> **exosyst said:**
> 
The mouse lock/unlock thing is only currently solvable by suspend/wake or logout/login. Something is wrong here but I am going to play with it to see what i can do.

I'm also working on it. [See my post]("http://ubuntuforums.org/showthread.php?t=1223355").
For now you can active the touchpad again by entering this in a terminal and your password.
```
sudo modprobe -r psmouse && sudo modprobe psmouse
```

---

### Post by exosyst on 2009-08-06
Thanks loads for that xrandr - i've put it into /etc/gdm/Xsession for want of a better location :D

 I tried an xrandr command before but perhaps it was wrong. I also saw someone recommend xbacklight which also failed to work.

One thing I noticed yesterday was that bluetooth is linked to an Fn key - Any ideas on enabling it as it doesn't seem to show in dmesg either.

---

### Post by Sashin on 2009-08-08
I have this laptop, no idea on how to get internet working though

---

### Post by exosyst on 2009-08-08
You mean wireless didnt work out of the box?

To get wired working you need to follow the steps on the community help wiki here [https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

Hope that helps.

---

### Post by Sashin on 2009-08-10
Which file do I download, the same one isn't there?

---

### Post by TexLogic on 2009-08-10
> **exosyst said:**
> Hey there, received my acer yesterday and I'm impressed! ...

Broken:
FN keys for brightness (triggers the popup and shows 'alleged' status but doesn't actually change it - any ideas?

I fixed this on my 5810T by installing a 2.6.30 kernel as per the instructions here:

[http://ubuntuforums.org/showpost.php?p=7484088&postcount=39](http://ubuntuforums.org/showpost.php?p=7484088&postcount=39)

TexLogic

---

### Post by LindsayD on 2009-08-10
RE: DVD drive not mounting.

I also have an Acer Timeline 4810T, and I am dual booting with Windows Vista. Everything is working fine in Vista, so the issues are definitely not hardware related. 

I did have one instance when the dvd rom drive worked - and that was after I had booted up but had left (in error) the Ubuntu 9.04 cd in the tray. The media was recognised, I unmounted and ejected it and then other cd's were recognised - for that session only. 

On advice of the forum, I upgraded to 9.10 (did the web upgrade), and now, again, the dvd rom drive reports no media present. I have tried audio cd's, data cd's and dvd movies. The audio cd's and dvd movies are purchased products (not ripped)

So, what now?? Is this a bug in Ubuntu?? 
I've looked at the fstab and it looks the same as one on the ubuntu guide.

---

### Post by TexLogic on 2009-08-10
> **LindsayD said:**
> RE: DVD drive not mounting.

I also have an Acer Timeline 4810T, and I am dual booting with Windows Vista. Everything is working fine in Vista, so the issues are definitely not hardware related. 

I did have one instance when the dvd rom drive worked - and that was after I had booted up but had left (in error) the Ubuntu 9.04 cd in the tray. The media was recognised, I unmounted and ejected it and then other cd's were recognised - for that session only. 

On advice of the forum, I upgraded to 9.10 (did the web upgrade), and now, again, the dvd rom drive reports no media present. I have tried audio cd's, data cd's and dvd movies. The audio cd's and dvd movies are purchased products (not ripped)

So, what now?? Is this a bug in Ubuntu?? 
I've looked at the fstab and it looks the same as one on the ubuntu guide.

It is pretty obviously a bug, and a pretty annoying one.  And the /etc/fstab solution that worked for me above, it turns out, has only improved the situation; Ubuntu still intermittently will not be able to mount the CD/DVD drive.

A very ugly workaround that works for me (so far) is to suspend the machine and wake it back up.  Upon waking up Ubuntu reliably (so far) reads the CD/DVD in the tray.

TexLogic

---

### Post by LindsayD on 2009-08-10
OK, I tried your suspend trick, and it does work. It also automatically mounts the media in the drive.
 If I unmount, it asks for authentication - with a message that it has been mounted by another user. Don't understand that one really.

After this has happened once, it seems to recognise other media, but still haven't got dvd's to play - tried Totem, Gnome Player and VLC. I either get the message that the media could not be recognised or that it has stopped. 

Still working on that one!! Please let me know what you have configured to get dvd's to play (I've only tried purchased ones). I used Mandriva before on a much older laptop with an Intel graphics card, had to configure the players for X11 only and also had to change one of the config files (can't remember which one). 


BTW, have you noticed anything about your battery on your Timeline? I've only had mine for a couple of weeks, and it is now reporting fully charged at around 96% - this is the same in Vista and Ubuntu.

---

### Post by Sashin on 2009-08-11
I can't seem to compile the lan card drivers on my machine, I followed the instructions but to no avail.

Does anyone know what this means?

```
sashin@Laptop:~/src$ make
make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/sashin/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630-generic'
  CC [M]  /home/sashin/src/at_common_main.o
  CC [M]  /home/sashin/src/atl1e_main.o
/home/sashin/src/atl1e_main.c: In function ‘atl1e_request_irq’:
/home/sashin/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
  CC [M]  /home/sashin/src/atl1c_main.o
/home/sashin/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/sashin/src/atl1c_main.c:1635: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1649: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1673: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1703: warning: ‘return’ with a value, in function returning void
/home/sashin/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/sashin/src/atl1c_main.c:2345: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/sashin/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/sashin/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630-generic'
make: *** [default] Error 2
sashin@Laptop:~/src$ sudo make install
[sudo] password for sashin: 
make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/sashin/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630-generic'
  CC [M]  /home/sashin/src/atl1c_main.o
/home/sashin/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/sashin/src/atl1c_main.c:1635: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1649: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1673: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1703: warning: ‘return’ with a value, in function returning void
/home/sashin/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/sashin/src/atl1c_main.c:2345: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/sashin/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/sashin/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630-generic'
make: *** [default] Error 2
```

---

### Post by Sashin on 2009-08-11
Problem solved, I was installing the wrong drivers.

---

### Post by LindsayD on 2009-08-11
RE: The dvd drive problem. 
It seems that it might be a problem with Gnome??? I am trying Fedora 11 booted from a USB (so the dvd rom drive is free) and have the identical problem that I have in Ubuntu. 

This seems to be a bug that has not yet been resolved.

---

### Post by BluJai on 2009-08-12
The brightness issue has a fix:
[http://ubuntuforums.org/showpost.php?p=7673757&postcount=2](http://ubuntuforums.org/showpost.php?p=7673757&postcount=2)

I'm experiencing the CD/DVD problem also. It is now reported on Launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/412527](https://bugs.launchpad.net/ubuntu/+bug/412527)

---

### Post by Incompetnce on 2009-08-14
I have a 4810T and I'm having similar problems:
Mousepad lock button doesn't work. Haven't tried workarounds yet.
Screen brightness. (Fixed. See [this thread]("http://ubuntuforums.org/showthread.php?t=1217421&highlight=4810t"))
Battery life not as long as with Windows (Haven't actually done tests, but it seems to be slightly shorter...)
And optical drive doesn't work. I have tried the fstab workaround and hibernating with disc in drive. No luck.

Other than that everything works fine. (I haven't tried the in built microphone so I don't know about that...)
The Webcam worked once I did something or other I saw on the 3810 thread...

---

### Post by Sashin on 2009-08-15
Everything seems to work for me 'cept the microphone, touch pad lock and the battery life is far too low and the estimation is no good.

---

### Post by LindsayD on 2009-08-15
DVD mounting problem:
I received a fix from someone else for mounting, which is a bit better than the suspend issue and is a similar problem to the touch pad:
Instead of using the button to open the dvdrom drive, use the console and type (without the quotes):
"eject cdrom"

So, clearly, the problem is related to how Ubuntu is "talking" to the buttons on the Acer - both the dvd drive open button and the touchpad disable button. 

This workaround is great and I am now able to play audio cd's on rythmbox without any problems. 

The only problem I have encountered is when I try to eject a cd or dvd without dismounting it first - for that I have to reboot!!!!

Still haven't got dvd's to play yet - I get the message that the media is not recognised. 
I've reported a bug for this

---

### Post by mopay on 2009-08-16
This fix work for me with cd/dvd:

Tipe "eject cdrom" (without the quotes) in the console.

I find it [here]("https://bugs.launchpad.net/ubuntu/+bug/412527")
:guitar:

---

### Post by miegiel on 2009-08-16
The touchpad switch works in karmic, so in 2 months and a week .... :) Karmic still has a lot of bugs to be ironed out, it's probably bet to be patient.

Do you guys have two finger scrolling yet? I managed to get it working with help of [_this post_]("http://ubuntuforums.org/showthread.php?p=7253159#post7253159").

---

### Post by Incompetnce on 2009-08-17
Is there a permanent fix for the screen brightness? I found a fix that I thought worked, but it has reverted to not working after a reboot...

---

### Post by Incompetnce on 2009-08-18
Can anyone confirm/disconfirm that the [CD/DVD drive bug]("https://bugs.launchpad.net/ubuntu/+bug/412527") affects the latest Karmic build? I would but I'm in the middle of a big writing project and I want to avoid unstable software for the moment...

---

### Post by quail-linux on 2009-08-18
Hi All,

For the people that are interested I have done a bit of a write up about the 4810T laptop [here]("http://quail.southernvaleslug.org/debian_acer_aspire_timeline_4810t.html"). I'm running Debian on it but some the info there should be useful ie getting suspend and hibernate working correctly.

---

### Post by LindsayD on 2009-08-19
RE: Playing DVD's with VLC.
To recap:
I upgraded to karmic koala, and could get audio cd's to play using the "eject cdrom" in the console fix. 
Recently I did an update (from karmic koala) and tried again.

I could then play all region 2 dvd's (the region my dvd player has been set to), but could not play region 1 dvd's. 

I have now followed the instructions from [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) about installing libdvdcss.

Now everything is working perfectly. However, I have not tried to "automatically" open movies from the menus. Instead I open VLC player, and choose the option Media/Open disc. 
From the menu, where it says disc device, I have browsed and selected the mounted dvd - this automatically points to the mount point. 

Hope this is of some help.

---

### Post by Salixman on 2009-08-27
hey incompetnce,
I was having issues with the brightness (I couldn't change it at all), and I had some issues with the networking (it was really patchy). So, I updated the kernel to 2.6.30. It's really easy, took five minutes. Here's a link: [http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/ ]("http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/")and guess what? both were fixed! I don't know if this will help, but it's stable so far so it's worth a shot.

---

### Post by quail-linux on 2009-08-28
> **Salixman said:**
> hey incompetnce,
I was having issues with the brightness (I couldn't change it at all), and I had some issues with the networking (it was really patchy). So, I updated the kernel to 2.6.30. It's really easy, took five minutes. Here's a link: [http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/ ]("http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/")and guess what? both were fixed! I don't know if this will help, but it's stable so far so it's worth a shot.

Your comment here does not seem right to me as I am using '2.6.30-1-amd64 #1 SMP Sat Aug 15 18:09:19 UTC 2009 x86_64 GNU/Linux' Kernel and my Brightness controls for backlight is still borked(not working) and I have to compile the drivers for my Ethernet.

Are you sure you not referring to 2.6.31-rcX kernels?

---

### Post by miegiel on 2009-08-28
Regarding the 2.6.30 kernels, there are 6 already :
[LIST]
[*]v2.6.30/	10-Jun-2009 11:27
[*]v2.6.30.1/	20-Jul-2009 17:37
[*]v2.6.30.2/	20-Jul-2009 19:03
[*]v2.6.30.3/	25-Jul-2009 12:38
[*]v2.6.30.4/	31-Jul-2009 12:40
[*]v2.6.30.5/	17-Aug-2009 12:09
[/LIST]
see also : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by TwiceOver on 2009-09-03
Thanks everyone for this thread.  I have been able to get all the functions of my 4810tz to work with the following issues remaining:

Touchpad on/off button.  No big deal here, I can wait for 9.10

Multi-Touch - Really wish I could get this to work as my palm keeps hitting the scroll up section of the pad and it is getting annoying.

Random lockups...  For some reason I have had to hard power it off three times now.  This is always during heavy Wireless use.

Pause during grub startup.  Right after it shows what disk is booting and says "Starting Up" there is a 5-10 second pause.

No big problems here.  I'm hoping 9.10 will be perfect for this laptop.

---

### Post by TexLogic on 2009-09-03
> **TwiceOver said:**
> Thanks everyone for this thread.  I have been able to get all the functions of my 4810tz to work with the following issues remaining:

Touchpad on/off button.  No big deal here, I can wait for 9.10

Multi-Touch - Really wish I could get this to work as my palm keeps hitting the scroll up section of the pad and it is getting annoying.

Random lockups...  For some reason I have had to hard power it off three times now.  This is always during heavy Wireless use.

Pause during grub startup.  Right after it shows what disk is booting and says "Starting Up" there is a 5-10 second pause.

No big problems here.  I'm hoping 9.10 will be perfect for this laptop.

I upgraded to (64 bit) Karmic (alpha 3 I believe) the other day on my 5810T in hopes of solving some (relatively minor) problems, including some of the above.  Very smooth upgrade, no difficulties.  I've experienced no lockups.  As for the problems:

Hibernation and suspension now work, though about half the time I have to restart compiz after the wake up.  (I simply stuck a custom application launcher on the panel so can do that with a single click.)

The brightness hotkey now works, although this required adding "nomodeset" to the boot parameters.  The hotkey often ceases to work after waking up from hibernation or suspension but can be resurrected from a terminal with the command
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```
which I've simply aliased to "br".

The touchpad on/off key still does not work properly for me; it successfully deactivates the touchpad but pushing it again does not reactivate it.  As with brightness, it can be reactivated from the command line:
```
sudo modprobe -r psmouse && sudo modprobe psmouse
```
And again I've added an appropriate alias.

I am *still* unable to get the cd/dvd drive to read a cd/dvd that I put into the drive.  I have to say: How hard can this be?  Evidently harder than I think.

Anyway, overall some reasonably good improvements for the Acer line with Karmic, esp considering it is still alpha.  Hopefully we can look forward to more in the release version.

TexLogic

---

### Post by bouyang on 2009-09-03
I am so happy to find this thread. I was able to fix the wired network problem :D

But I still have a strange problem with my wireless network. Whenever I go to suspend mode and come back, I lost the wireless connection. Only way for me to bring it back was to reboot.

Did anyone else experienced the same symptom?

Thanks.

---

### Post by quail-linux on 2009-09-04
> **TwiceOver said:**
> Thanks everyone for this thread.  I have been able to get all the functions of my 4810tz to work with the following issues remaining:

Touchpad on/off button.  No big deal here, I can wait for 9.10

Multi-Touch - Really wish I could get this to work as my palm keeps hitting the scroll up section of the pad and it is getting annoying.

Random lockups...  For some reason I have had to hard power it off three times now.  This is always during heavy Wireless use.

Pause during grub startup.  Right after it shows what disk is booting and says "Starting Up" there is a 5-10 second pause.

No big problems here.  I'm hoping 9.10 will be perfect for this laptop.

To get around the hard power off when your machine locks up all you have to is this:
While holding down Alt + SysRq (print screen key) type R E I S U B

Refer to this [link]("http://quail.southernvaleslug.org/webblog/archives/42") for more info
```

```

---

### Post by tty on 2009-09-05
-

---

### Post by Migou67 on 2009-09-14
Hello ,

Just brought a 4810T Core 2 Solo SU3500 last Friday an playing around with it this week end :razz:

I started the windows installation just to flash the laptop to the latest 1.28 bios
and checked the hardware. (You can do that also without windows)

Downloaded the Ubuntu 9.10 Alpha 5 32 Bits and created a USB startup disk with the ISO.

Removed everything on the disk and installed Ubuntu with default partition's.

A full update of the Ubuntu as been done after.

I don't have changed the BIOS parameter for the disk to IDE, as by default is AHCI
and I have no problem whit that on my Hitachi 320 Gigas.

Working out of the box :
Wifi, Bluetooth, Video card, Sound, Touch pad, sensor key's and FN, Gnome Power save (CPU scaling),DVD, Batterie indicator, Lan Gigabit, USB, WEB CAM.

Not tested :
Card reader.

Not working for the moment for me :
-Microphone recording.
-FN key for brightness , it work but Ubuntu stop responding !
I put my preferred setup in /etc/rc.local -> setpci -s 00:02.0 F4.B=50
-Suspend some time work another time not.
-Button for disabling the touch pad work but you never get it back :)

Comments :
Compiz Fusion run smoothly on this machine, performance are very good for this
tiny laptop and is running very cold and without noise. Cairo Dock run very good
in OpenGL mode.

Tips:
I added Firefox flash blocker  to increase batteries life and decrease CPU load :smile:
Changed the default fonts for X and Firefox using truetype freetype and Msttcorefonts.

I'm very happy with my choice , a nice laptop for running Linux on it !

Regards.
Pat.

---

### Post by balagosa on 2009-09-15
I have a problem with my wireless connection.

I already did the correct setup for my wired Ethernet but then my wireless is not present.

Only a) localhost, and b) eth0 show up when i do ```
ifconfig
```

---

### Post by Arlanthir on 2009-09-24
> **Migou67 said:**
> 
-FN key for brightness , it work but Ubuntu stop responding !


Same here, it's because of the BIOS update :S

---

### Post by miegiel on 2009-09-24
> **Arlanthir said:**
> Same here, it's because of the BIOS update :S

Good to know. I'll pass on the new BIOS then :twisted: It would be nice if acer supplied some more information on what's changed with their BIOSes.

---

### Post by Arlanthir on 2009-09-24
> **miegiel said:**
> Good to know. I'll pass on the new BIOS then :twisted: It would be nice if acer supplied some more information on what's changed with their BIOSes.

Damn. I tried regressing the BIOS to 1.10 and bricked it. Damn.

---

### Post by quail-linux on 2009-09-27
> **Arlanthir said:**
> Damn. I tried regressing the BIOS to 1.10 and bricked it. Damn.
Sorry to here you bricked you timeline :(

What was the BIOS version you downgraded from?

---

### Post by Arlanthir on 2009-09-27
> **quail-linux said:**
> Sorry to here you bricked you timeline :(

What was the BIOS version you downgraded from?

I got my money back but now it's sold out, and knowing Portugal, they'll come back double the price...

I downgraded from 1.28 to 1.10, the version that came by default, I think.

I did that because on 1.10 the brightness keys didn't work with the latest karmic, but on 1.28 they worked and hung Ubuntu. So I was pretty afraid that it would hang everytime Ubuntu tried to dim the screen. 

So, you've been warned, always flash them on a DOS live usb, crossing your fingers wishing upon a star holding a four leaf clover. :|

---

### Post by Arlanthir on 2009-09-29
Got the Acer back :)

The xrandr fix for backlight issues doesn't seem to work for me.
I have a LVDS1 output instead of LVDS and xbacklight says no outputs support backlight property, confirming the xrandr output:

```

X Error of failed request: BadName (named color or font does not exist)
  Major opcode of failed request: 149 (RANDR)
  Minor opcode of failed request: 11 (RRQueryOutputProperty)
  Serial number of failed request: 31
  Current serial number in output stream: 31

```

---

### Post by coolvibe on 2009-09-30
> **Arlanthir said:**
> Got the Acer back :)

The xrandr fix for backlight issues doesn't seem to work for me.
I have a LVDS1 output instead of LVDS and xbacklight says no outputs support backlight property, confirming the xrandr output:

```

X Error of failed request: BadName (named color or font does not exist)
  Major opcode of failed request: 149 (RANDR)
  Minor opcode of failed request: 11 (RRQueryOutputProperty)
  Serial number of failed request: 31
  Current serial number in output stream: 31

```

Turn KMS off (if you have it enabled), and set acpi_backlight=vendor in the kernel commandline in your grub config. This made my backlight behave on my 5810T, it might work for you.

---

### Post by Arlanthir on 2009-09-30
> **coolvibe said:**
> Turn KMS off (if you have it enabled), and set acpi_backlight=vendor in the kernel commandline in your grub config. This made my backlight behave on my 5810T, it might work for you.

Won't turning KMS off disable the graphical boost of the new driver plus net me a text-only boot? O.o
EDIT: I got a few more lines during boot but it works ;) Thanks a bunch

---

### Post by coolvibe on 2009-10-02
> **Arlanthir said:**
> Won't turning KMS off disable the graphical boost of the new driver plus net me a text-only boot? O.o
EDIT: I got a few more lines during boot but it works ;) Thanks a bunch

Well, usplash takes over, but performance in X shouldn't be affected. ANd you get better battery life since with KMS disabled you also get Framebuffer Compression.

---

### Post by Arlanthir on 2009-10-02
> **coolvibe said:**
> Well, usplash takes over, but performance in X shouldn't be affected. ANd you get better battery life since with KMS disabled you also get Framebuffer Compression.

Ok, for now I'll keep these settings :)
Thanks!

---

### Post by executorvs on 2009-10-03
do any of you think we stand a chance of getting the cdrom drive fixed before karmic final? I would love to be able to reliably and easily use my drive.

---

### Post by Sashin on 2009-10-03
> **coolvibe said:**
> Turn KMS off (if you have it enabled), and set acpi_backlight=vendor in the kernel commandline in your grub config. This made my backlight behave on my 5810T, it might work for you.

1. How do I do this?

2. Will anything bad happen if I turn kernel mode setting off?

---

### Post by quail-linux on 2009-10-04
> **Sashin said:**
> 1. How do I do this?

2. Will anything bad happen if I turn kernel mode setting off?


1. have a read here:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

2. in theory nothing bad should happen. :-)

Good Luck

---

### Post by TwiceOver on 2009-10-05
Wow... The beta is disappointing on the 4010t.

Brightness workaround no longer works.
Touchpad On/Off doesn't work
Neither Suspend or Hibernate work.
DVD Drive still funky

Hopefully it'll all be ironed out in the final.

---

### Post by Urb on 2009-10-07
Many thanks for this thread.
I have the 4810TZ and am running with 9.10 beta (updated today october 7th).

What works:
-Wired network
-Wireless network
-Compiz
-Brightness adjustment (Fn keys)
-CD/DVD drive
-Sound

What does not work:
-Opera web browser (I'll wait for them to make a version for 9.10)
-Double click touchpad (I've seen fixes for this, but don't really need it anyway)


Just wanted to share:
I had some trouble with the CD/DVD drive not recognizing a data CD. This was fixed by editing the last line in the fstab file. From your root folder:

sudo gedit etc/fstab

Somewhere in the last line of that file I found "udf,so9660" (Googled my way to this). Changed it to "udf,iso9660", and now the computer can recognize a data CD. I still have to use the "eject" command in terminal to make the drive work though. Hope that helps.

---

### Post by v1ad on 2009-10-07
i had my wireless button turn on my wireless card not it just stopped does not light up when i press fn + wireless button it did work perfect in windows and a couple days into ubuntu it just stopped tried everything ......:(

---

### Post by Arlanthir on 2009-10-07
> **v1ad said:**
> i had my wireless button turn on my wireless card not it just stopped does not light up when i press fn + wireless button it did work perfect in windows and a couple days into ubuntu it just stopped tried everything ......:(

Fn + wireless? My 4810t doesn't have that button.
Instead, the wireless light is touchable. Can you try that instead?

---

### Post by v1ad on 2009-10-07
> **Arlanthir said:**
> Fn + wireless? My 4810t doesn't have that button.
Instead, the wireless light is touchable. Can you try that instead?

tried both :[ i just screwed it up . booted it off usb now booted it on normal works good.

---

### Post by gazambuja on 2009-10-09
Hi, I make a fresh install of Karmic 9.10 beta, with bios 1.10:
[LIST]
[*]Integrate Mic not work
[*]Bright keys, also not work (no do anything)
[*]Every else work fine.
[/LIST]

Now, im update bios to 1.30
[LIST]
[*]Integrate mic keep without work
[*]Bright keys, now work, but freez my gnu/linux.
[/LIST]

Acer Aspire 4810TZ-4011
Ubuntu Karmic 9.10 with all updates.

---

### Post by Sashin on 2009-10-09
What about the touchpad on/off button?

---

### Post by quail-linux on 2009-10-09
> **gazambuja said:**
> Hi, I make a fresh install of Karmic 9.10 beta, with bios 1.10:
[LIST]
[*]Integrate Mic not work
[*]Bright keys, also not work (no do anything)
[*]Every else work fine.
[/LIST]

Now, im update bios to 1.30
[LIST]
[*]Integrate mic keep without work
[*]Bright keys, now work, but freez my gnu/linux.
[/LIST]

Acer Aspire 4810TZ-4011
Ubuntu Karmic 9.10 with all updates.

I just noticed that there is a 2.30 bios available as of the 2009/10/09 for the 4810T/TG/TZ models.

---

### Post by quail-linux on 2009-10-10
> **gazambuja said:**
> Hi, I make a fresh install of Karmic 9.10 beta, with bios 1.10:
[LIST]
[*]Integrate Mic not work
[*]Bright keys, also not work (no do anything)
[*]Every else work fine.
[/LIST]

Now, im update bios to 1.30
[LIST]
[*]Integrate mic keep without work
[*]Bright keys, now work, but freez my gnu/linux.
[/LIST]

Acer Aspire 4810TZ-4011
Ubuntu Karmic 9.10 with all updates.

have a read here[1] and let me know if it fixes your freezing problem

[1] [http://ubuntuforums.org/showpost.php?p=8081724&postcount=382](http://ubuntuforums.org/showpost.php?p=8081724&postcount=382)

---

### Post by gazambuja on 2009-10-10
Im sorry, im testing now touchpad on/off, and not work (same problem, cant activate again after desactivate).

Im update to 2.30 bios:
[LIST]
[*]Integrate mic keep without work
[*]Touchpad on/off not work
[*]Bright keys, now work, but freez my gnu/linux.
[/LIST]

The command in console to make work bright keys not work: 
```
gustavo@gustavo-laptop:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL kernel
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30
```

Also, some times, my wireless stop working, and only rebooting my laptop can be work again, in syslog apper:
```
Oct 10 08:43:26 gustavo-laptop kernel: [  165.496232] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
Oct 10 08:43:26 gustavo-laptop kernel: [  166.524219] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
Oct 10 08:44:26 gustavo-laptop wpa_supplicant[1190]: CTRL-EVENT-SCAN-RESULTS
```


> **quail-linux said:**
> have a read here[1] and let me know if it fixes your freezing problem

[1] [http://ubuntuforums.org/showpost.php?p=8081724&postcount=382](http://ubuntuforums.org/showpost.php?p=8081724&postcount=382)

---

### Post by gazambuja on 2009-10-10
Only to information, with Karmica 9.10 beta with all updates, and bios 2.30, my 4810TZ-4011, using wifi, google chrome, bright to max, playing music, and compiling software, and a lot of other thing, my batery work for 4h and 30m

---

### Post by quail-linux on 2009-10-11
> **gazambuja said:**
> Im sorry, im testing now touchpad on/off, and not work (same problem, cant activate again after desactivate).

Im update to 2.30 bios:
[LIST]
[*]Integrate mic keep without work
[*]Touchpad on/off not work
[*]Bright keys, now work, but freez my gnu/linux.
[/LIST]

The command in console to make work bright keys not work: 
```
gustavo@gustavo-laptop:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL kernel
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30
```

Also, some times, my wireless stop working, and only rebooting my laptop can be work again, in syslog apper:
```
Oct 10 08:43:26 gustavo-laptop kernel: [  165.496232] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
Oct 10 08:43:26 gustavo-laptop kernel: [  166.524219] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
Oct 10 08:44:26 gustavo-laptop wpa_supplicant[1190]: CTRL-EVENT-SCAN-RESULTS
```

**[*]Integrate mic keep without work**
Only things I can suggest is to look at your settings under your mixer and check to that your mic is not muted and that the capture is enabled. The internal mic works on my laptop and always has.

**[*]Touchpad on/off not work**
The touchpad on/off key has never worked for me but as a workaround in terminal do```
# modprobe -r psmouse ; modprobe psmouse
```

**[*]Bright keys, now work, but freez my gnu/linux.**
I will have to load the Ubuntu LiveCD when got time to see what is going on with xrandr, so in theory it should work but have to check it out.

---

### Post by quail-linux on 2009-10-11
> **gazambuja said:**
> Only to information, with Karmica 9.10 beta with all updates, and bios 2.30, my 4810TZ-4011, using wifi, google chrome, bright to max, playing music, and compiling software, and a lot of other thing, my batery work for 4h and 30m

Sounds like you are working the system pretty hard, so that might be correct.

---

### Post by PatrickVogeli on 2009-10-11
Hi there,

I'm looking into buying a new laptop, and I've seen a packard bell butterfly, with 13,3" screen. That laptop has an ATI Mobility Radeon HD4330 and should be, basically, an acer timeline.

Since the card is the same, and the laptop has the same hardware as the Timeline, I'm very interested in hearing from you 4810t users about the Ati card (the packard bell doesn't feature dual Intel / Ati graphics). I've opened a thread here [http://ubuntuforums.org/showthread.php?t=1288722](http://ubuntuforums.org/showthread.php?t=1288722) if you'd like to drop-in, I'd be glad.

Thanks

---

### Post by TexLogic on 2009-10-11
> **gazambuja said:**
> 

Im update to 2.30 bios:
[LIST]
[*]Integrate mic keep without work
[*]Touchpad on/off not work
[*]Bright keys, now work, but freez my gnu/linux.
[/LIST]

The freezing problem seems to be due to a Compiz bug.  The current workaround is to set Visual Effects (in Preferences -> Appearance) to "None".

> 
The command in console to make work bright keys not work: 
```
gustavo@gustavo-laptop:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL kernel
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30
```
Try adding "nomodeset" as a boot parameter.

TexLogic

---

### Post by gazambuja on 2009-10-13
The erro in wifi connection has a bug in lunchpad:

I have the same problem: Acer 4810TZ:
 02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

In dmesg, I can see:
Oct 10 08:43:26 gustavo-laptop kernel: [ 166.524219] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
Oct 10 08:44:26 gustavo-laptop wpa_supplicant[1190]: CTRL-EVENT-SCAN-RESULTS

to see details:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040)

---

### Post by v1ad on 2009-10-14
hey i installed ubuntu 9.10 and got rid of windows. how can i now upgrade the bios

---

### Post by miegiel on 2009-10-14
> **v1ad said:**
> hey i installed ubuntu 9.10 and got rid of windows. how can i now upgrade the bios

[https://help.ubuntu.com/community/AspireTimeline/Using](https://help.ubuntu.com/community/AspireTimeline/Using)

See bottom of the page.

---

### Post by Sashin on 2009-10-15
You probably should have upped the bios then got rid of windows.

---

### Post by Arlanthir on 2009-10-15
What about mkv playback, is it slow for everyone? :S

---

### Post by miegiel on 2009-10-15
> **Arlanthir said:**
> What about mkv playback, is it slow for everyone? :S

It depends on the .mkv and on the player you use. On my 3810T (core 2 duo version) I normally use VLC because it's more versatile, flexible and doesn't need any codecs. But with 1080i and 1080p HD .mkv's it struggles or the playback gets so bad it's not worth watching any more. VLC is just not the most resource friendly player. Playing the same vid in kaffeine gives better playback. But in general if it doesn't play properly in VLC I just boot windows and watch it in [_XBMC_]("http://en.wikipedia.org/wiki/XBMC"), which is as good as it gets regarding playback performance. 1080i and 1080p HD are on the edge of what this machine can handle, 720p HD should play without issues.

---

### Post by sandybuchan on 2009-10-15
Hi!
I have an Aspire 5810T, 4GB, 500GB, etc. I screwed up my default Vista (Pishta) installation, the only thing that would install "Out of the box" from a boot CD was Ubuntu. I now know that was because only Linux and the very latest M$ stuff understand AHCI from boot.
I've since got a copy of Win7, and reluctantly deleted my Linux partition - Win 7 is just too good to keep playing about.
I was really worried about extending my Win partition to extend into the space I had parted for Linux - but it didn't even need a re-boot, and did it 10 times quicker than GParted.

My Acer Aspire One netbook 8GB SSD machine gave up after I installed too much heavy-duty stuff on it - too many read-write cycles. I naively expected this to take a few years - but eBay to the rescue, 20 pounds UK and it was sorted.
To look on the bright side though we have just installed a suite of Ubuntu "internet cafe" computers on an oil platform in West Africa, 'cos no-one knows how to screw with them' (after a heap of virus problems).
Just my 2 pence worth.

Cheers,
Sandy

---

### Post by gazambuja on 2009-10-30
Some news to make work internal mic? (4810TZ with Ubuntu 9.10)

And yes, in my notebook, mkv files in 720p run very slow...

---

### Post by v1ad on 2009-11-01
hey does any1 else has  a wireless issue where when connected to a secure network it kicks u off at heavy load and random disconnects. at times the wireless signal goes down to a bar for 3 or 4 bars. the problem seems only on secure networks

---

### Post by Weeble818 on 2009-11-01
So karmic is out, anyone try it yet? I'm pretty set on getting this laptop I just wanna know if I'll be able to put ubuntu on it. Is battery life still a deal breaker? Are there still the same annoying bugs in 9.10?

---

### Post by v1ad on 2009-11-01
the battery life is considerably better than any other laptop. i would recommend it

---

### Post by miegiel on 2009-11-01
> **v1ad said:**
> hey does any1 else has  a wireless issue where when connected to a secure network it kicks u off at heavy load and random disconnects. at times the wireless signal goes down to a bar for 3 or 4 bars. the problem seems only on secure networks

(I've got the 3810T) I'm only having problems with disconnections with a secure (WPA2 enterprise PEAP MSCHAPv2) network here when I'm within reach of 2 access points. I blame they way the access points are setup, something I have no influence over.

> **Weeble818 said:**
> So karmic is out, anyone try it yet? 
yes

> I'm pretty set on getting this laptop I just wanna know if I'll be able to put ubuntu on it. 
yes

> Is battery life still a deal breaker? 
Can't say, it really depends on your battery requirements. Keep in mind that batteries loose capacity over their lifetime (even if you shelf them). For example if you have a 1 hour daily commute and want to use your laptop on your way to work (school) and home, get a laptop with a 2-3 hour real battery life or a 4-6 hour idle (marketing) battery life. Also keep in mind that idle power use is higher in ubuntu than in windows. If your laptop is idle a lot while you use it you can get an extra 25% hit compared to windows and marketing battery life claims.

> Are there still the same annoying bugs in 9.10?
Internal mic and suspend to RAM still don't work for me.

**ps** I consider these timelines cheap pieces of plastic crap. A decent laptop in this weight/batterylife/performance class costs twice as much or more. It lacks BIOS options, build quality is horrible (screws with damaged +'s, keyboard pops out, ect.) Still, for me it was a conscious choice to go for cheapness instead of quality, so I'm not complaining :D

---

### Post by netimen on 2009-11-01
DVD is not working on 9.10. It doesn't mount the disk when I insert it, and when I try to mount it manually, the command in the terminal just freezes, giving no output and not finishing.

How can I check whether DVD drive is detected?

---

### Post by Arlanthir on 2009-11-01
> **netimen said:**
> DVD is not working on 9.10. It doesn't mount the disk when I insert it, and when I try to mount it manually, the command in the terminal just freezes, giving no output and not finishing.

How can I check whether DVD drive is detected?

This is a known bug.
Reboot and then every time you want the disc tray to pop out, execute "eject cdrom" instead of pressing the hardware button.

Just make sure you don't press that button, as it somehow makes Ubuntu forget about the drive ;)

---

### Post by netimen on 2009-11-01
I see. So there is no fix to make the hardware button work?

---

### Post by Arlanthir on 2009-11-01
> **netimen said:**
> I see. So there is no fix to make the hardware button work?

Apart from that, I'm not aware of any fix :S

---

### Post by netimen on 2009-11-01
I see, thx )

---

### Post by v1ad on 2009-11-01
im using 9.10 my cdrom drive works fine

---

### Post by exosyst on 2009-11-05
Just done the upgrade to Karmic and installed cheese (great app) only to find that the internal webcam is no longer detected. Is there a fix available?

I tried the `sudo modprobe uvcvideo` but no joy and running it within a console I get:

** (cheese:4815): WARNING **: Could not initialise connection to hald.
Normally this means the HAL daemon (hald) is not running or not ready

So yeah, any ideas?

---

### Post by exosyst on 2009-11-05
Ok, so here's where I feel silly.

The 'solution' for me was to execute:
sudo hald

No idea why it wasn't running after a fresh install but after doing that I now get my beautiful mug showing up in Cheese again.

Hope that helps anyone else with a similar problem!

---

### Post by krychek on 2009-11-13
Were any of you be able to make the hdmi port working?

---

### Post by Sashin on 2009-11-13
Mine works, just connect while its off then turn it on. For me it worked automagically.

---

### Post by krychek on 2009-11-14
> **Sashin said:**
> Mine works, just connect while its off then turn it on. For me it worked automagically.

OK, mine is working as well after changing the Display setting in BIOS. I have a 4810TG with an Ati card.

BTW, is the cdrom eject button problem reported on launchpad? I couldn't find it.
Edit: here it is: [https://bugs.launchpad.net/ubuntu/+bug/412527](https://bugs.launchpad.net/ubuntu/+bug/412527)

---

### Post by originalmike on 2009-12-15
Hello, I have a 4810TG, what's the best BIOS for my laptop? The last one is ok?

---

### Post by aioan on 2009-12-28
> **v1ad said:**
> hey does any1 else has  a wireless issue where when connected to a secure network it kicks u off at heavy load and random disconnects. at times the wireless signal goes down to a bar for 3 or 4 bars. the problem seems only on secure networks

I am experiencing the same problem in my acer 4810T bios v1.31

I haven't realized that it only happens on secure networks, I will check and get back at you.

It makes it impossible to download torrents or anything using multiple connections...

---

### Post by aioan on 2009-12-28
> **quail-linux said:**
> have a read here[1] and let me know if it fixes your freezing problem

[1] [http://ubuntuforums.org/showpost.php?p=8081724&postcount=382](http://ubuntuforums.org/showpost.php?p=8081724&postcount=382)

I tried the instructions on that thread but they don't seam to work on my 4810T.

I was thinking to downgrade to BIOS v1.10 but I saw some posts of people trying that and failing. I also noticed that there is no dos utility for BIOS v1.10 in acer website but there is for v1.28, v1.30 or v1.31...

Regards

---

### Post by borg310 on 2010-01-17
Hello together,

I am using Karmic on a 4810TZ and have the following problems:

[LIST]
[*]display remains turned on in standby mode
[*]choosing hibernate in the logout menu doesn't work - when I close the laptop it does work
[*]I can't listen to audio CDs. I use "eject cdrom" to open the drive. Any data CD is recognized but when I insert an audio CD I get the error "Cannot mount audio CD:  DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus) "
[/LIST]
Are there any solutions to these probs, most urgent is the last.

Thanks for help,

Björn

---

### Post by executorvs on 2010-03-10
Has anyone here checked for these problems under Lucid? I assume they're still there as I still have them on my 5810TZ. Just thought I would check.

---

### Post by kwstas on 2010-04-02
karmic 9.10


in my /etc/default/grub file i have only added the "nomodeset"
and i have placed this command "xrandr --output LVDS --set BACKLIGHT_CONTROL native" in the "startup apps" even though i have no clue of what it means.
i tried this also "acpi_backlight=vendor" but has no difference.

i have noticed these:

before using this command  "xrandr --output LVDS --set BACKLIGHT_CONTROL native" i had 9 levels(1 2.. 9) of brightness(as in windows).
*i guess blank screen is considered as "0" *
Since i couldn't change brightness's level though i now use the above "xrandr" command which gives me 20 working brightness levels!

in my /sys/class/backlight/acpi_video0
the "max brightness" file says 9 and when i change the brightness the file "brightness" changes but only from 1 to 9. the rest 11 levels are ignored on these files but not visually on my screen.
so when i'm in 20th level and decrease by one, the "brightness file will show 8.
when i'm on 10th level, the "brightness" file will show 1.  !!!
when i'm on 1st level, the "brightness" file of course still shows 1 but when i now increase to 2nd level the "brightness" file starts to count again(!) and stops on 9th level.

in my /proc/acpi/video/OVGA/DD02  there is also a "brightness" file with changeable values.
it has 10 levels!!! (10 20.. 100)
so similar things happen here BUT the blank screen is considered as the value "10" here so when the "brightness" file of "/sys/class/backlight/acpi_video0" shows "1" , the
"brightness" file of "/proc/acpi/video/OVGA/DD02" shows "20"  !!!



it seems that the above cause a bug when i switch from AC cable to battery!
when i'm on battery brightness reduces by 75% correctly as configured in power management but if i plug in AC power it increases only by 1 scale! (i have configured it to 100 in power management)

anyone has any idea about this?

---

### Post by tuxx on 2010-04-03
Hi ppl,

Been running Karmic with 'nomodeset' in Grub to enable my Brightness-keys. However that, obviously, disables KMS and renders an ungly boot-screen.

With Lucid I thought I wouldn't need it - however sadly I do, hence I have an even uglier boot-screen with no Plymouth, no everything. 

What is the technical issue behind the brightness not working in KMS-mode?

---

### Post by miegiel on 2010-04-03
I've been a bit curious what all these kernel parameters do. For those of you who are curious about what *nomodeset* does, [read this]("http://wiki.sugarlabs.org/go/Nomodeset").

---

### Post by Sashin on 2010-04-04
So there is no way to get the actual brightness keys working without it?

---

### Post by TechnoCog on 2010-05-30
Does anyone know how the new 10.4 Lucid Linux? What about things like power? 

What works and what doesnt? the documentation page for acer timelines doesnt say much?

---

### Post by Sashin on 2010-06-02
So far all I've noticed is that brightness key problem. Can someone else please test it with the new 2.6.35 rc1 kernel? I don't have a non production machine or one I'm willing to risk.

---

### Post by TechnoCog on 2010-06-15
I recently (foolishly) updated to lucid and since then the lenenvo work around has gone, I now get less than 3 hours from my battery when before I was getting almost 8. 

Anyone know a fix? I've got powertop already and thats not helping much.

Also seems to be running allot hotter than before.

---

### Post by executorvs on 2010-06-15
I'm getting better time than that on my 5810. what kernel are you using and have you run dmesg in terminal after boot to look for any problems there?

---

### Post by executorvs on 2010-06-15
it should also be noted that the brightness key error (in karmic and lucid at least) appears to be a compiz bug and doesn't happen with metacity compositing or when compositing is disabled.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/446717)

---

### Post by TechnoCog on 2010-06-20
@[executorvs]("http://ubuntuforums.org/member.php?u=476586") Im running Kernal 2.6.32 - 22 generic, I havent run dmesg. to be honest I'm an utter linux noob so wouldnt know what to look for.

I've got win7 dual boot by the way to

---

### Post by executorvs on 2010-06-22
there is a kernel PPA which would allow you to try 2.6.34 and the maverick builds of 2.6.35 if you want to see if one of them works better. As for checking dmesg, I normally just scroll through it looking for jumps in the time stamps and then if there is a jump (i.e. a few seconds vs a fractions of a sec) I look for an error message of some sort and run to google with it.

---

