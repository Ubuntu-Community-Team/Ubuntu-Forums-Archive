---
title: "Suspend and/or hibernation is broken with fglrx installed"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by Ainvar on 2005-10-14
I have a Dell Inspiron 6000d with an ATI x300 card. If I use the default ati driver and have horrible 3d and such suspend works fine. Now if I install and use the fglrx driver and try to suspend I have a better chance of finding 40 million dollars in the back of my suv.

Is there a fix for this or are they even looking at the bugzilla tickets? I submitted a ticket for this and replied back to everything in the ticket requested of me and then nothing.

Suspend still does not work in final and hibernate does not either. Any suggestions or ideas on how to resolve besides going back to the ati driver?

---

### Post by nacnud on 2005-10-14
The suspend option has disappeared from the logout menu on my dell 600m since upgrading to Breezy.  The fn key combo to suspend also no longer works.

---

### Post by strawman on 2005-10-14
check your new file - /etc/default/acpi-support and uncomment the sleep option; your old configuration might have been over-written.

as far as using the fglrx driver and acpi/suspend does not mix from what i've googled.  having a functioning suspend is more important to me at the moment than frame rates.

---

### Post by jack_tianfan on 2005-10-14
i got a totally new ubuntu intall, my system is with the x300 card. i do have this issue(cannot come back from suspend). do anybody know how to fix it!!??

---

### Post by strawman on 2005-10-14
do you have ati drivers or fglrx?

---

### Post by jack_tianfan on 2005-10-15
yes!! i got the fglrx driver installed

---

### Post by dave9191 on 2005-10-20
Argh, 

I'm just another guy finding out that fglrx and suspend don't mix the hard way. I would like good opengl framerates but suspend is more important to me. So I reverted. Anyone know a work around to have both ? 

Dave

---

### Post by geearf on 2005-11-04
Same here.

---

### Post by GoodPanos on 2005-11-04
Off the subject a bit.  Do the fglrx drivers really work for the ATI X300 as far as 3D accelaration is concerned?  What about the ATI drivers?

---

### Post by dfacto on 2005-11-12
Hibernation works using 8.19.10 drivers.  Suspect suspend will also, although I have not yet succeeded.

---

### Post by geearf on 2005-11-12
Thanks for telling us that, I will try them now.

---

### Post by geearf on 2005-11-12
still no sleep support out of the box :(

---

### Post by André on 2005-11-15
Hi, which error do you get? I have the newest version of the ATI drivers installed but suspend just gives me a black screen when i recover :-( At least the screen isn't "melting" anymore ;-) Any ideas? Greetings Andr&#233;

---

### Post by Donnut on 2005-11-15
Andre, I saw this post, and it perked my interest.  I have the latest (8.18.8) drivers installed on a laptop, and I don't even see an option to suspend.  Is this the Ubuntu operation "hibernate"?

---

### Post by André on 2005-11-16
Hi Donnut,

the latest drivers are 8.19.10. They have "initial" supsend/resume support included but it it not working for me right now.

Best would be to hit that thread for more infos: [http://www.rage3d.com/board/showthread.php?t=33834873&highlight=8.19.10](http://www.rage3d.com/board/showthread.php?t=33834873&highlight=8.19.10)

I am SO waiting for ATI drivers which support suspend and i really hope that i can fix my errors.

Greetings
André

---

### Post by chele on 2005-11-16
Norbert Tretkowski reports that 8.19.10 works on Debian on a IBM T42 
[http://www.inittab.de/blog/2005/11/15#20051115_new-ati-driver](http://www.inittab.de/blog/2005/11/15#20051115_new-ati-driver)

---

### Post by geearf on 2005-11-16
[QUOTE=André]Hi, which error do you get? I have the newest version of the ATI drivers installed but suspend just gives me a black screen when i recover :-( At least the screen isn't "melting" anymore ;-) Any ideas? Greetings André[/QUOTE]
Hello,

exactly the same here.

---

### Post by André on 2005-11-16
[QUOTE=chele]Norbert Tretkowski reports that 8.19.10 works on Debian on a IBM T42 
[http://www.inittab.de/blog/2005/11/15#20051115_new-ati-driver](http://www.inittab.de/blog/2005/11/15#20051115_new-ati-driver)[/QUOTE]


I tried these drivers and they give me:

```

(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

in /var/log/Xorg.0.log

There was a workaround with another libdri.something and i tried it. But still the same error.

Any ideas how to fix that?

Greetings
André

---

### Post by geearf on 2005-11-17
Well yesterday I changed my xorg.conf to the one gave by fglrxconfig, and then I reboot and at the kde login screen I went to suspend to ram, and then resume and it was perfect.

Today after an acpi-support update I've tried it within kde, not working, I've tried it at the login screen, not working.

I've tried changing some options of acpi-support and calling sleep.sh instead of pressing the sleep button, not working :(

---

### Post by Donnut on 2005-11-17
[QUOTE=André]Hi Donnut,

the latest drivers are 8.19.10. They have "initial" supsend/resume support included but it it not working for me right now.

Best would be to hit that thread for more infos: [http://www.rage3d.com/board/showthread.php?t=33834873&highlight=8.19.10](http://www.rage3d.com/board/showthread.php?t=33834873&highlight=8.19.10)

I am SO waiting for ATI drivers which support suspend and i really hope that i can fix my errors.

Greetings
André[/QUOTE]

Does anyone know how I would get a copy of these drivers?  Aside from suspend support, do they have any performance features for gaming?

---

### Post by GoodPanos on 2005-11-17
Yep, same here.  Suspend does not work.  Hibernate though works :rolleyes: 
Does any one have instructions on how to remove the drivers and have everything working back to normal?

---

### Post by cbudden on 2005-11-17
Confirmation, with the new drivers, hibernate DOES work.  Yay!

---

### Post by GoodPanos on 2005-11-18
Well, I guess it isn't so bad.  I gained two things but lost one.

I gained 3D Accelation and now I can also see the bootup and shutdown process (vga=771).

And I lost Suspend mode.  At least now when I do Fn + Esc I can lock the laptop (ACPI_SLEEP_MODE=standby).

I still have Hybernate but I would prefer to have Stand By instead.

Still, I would like to know how to remove the drivers just in case I change my mind.

---

### Post by shizow on 2005-11-23
it seems that since installing this new driver version, the first time suspend to ram and to disk are working with my T43 (SerialATA)

---

### Post by jpkotta on 2005-11-25
*Sweet.*  Once the kernel supports DMA with my DVD drive, I'll be set (well, it does, but I'm not going to waste my time configuring it -- yet).

I have a Latitude D610, and I now have 3D acceleration and suspend.  No hibernate, that broke moving from hoary to breezy.  I don't miss it.

[QUOTE=chele]Norbert Tretkowski reports that 8.19.10 works on Debian on a IBM T42 
[http://www.inittab.de/blog/2005/11/15#20051115_new-ati-driver](http://www.inittab.de/blog/2005/11/15#20051115_new-ati-driver)[/QUOTE]

On that page is a link to [instructions]("http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html") and [downloads]("http://xoomer.virgilio.it/flavio.stanchina/ubuntu-fglrx-breezy/index.html").  I just got the kernel sources and the driver.  I followed the instructions, and now I have suspend and DRI!

---

### Post by GoodPanos on 2005-11-28
[QUOTE=jpkotta]On that page is a link to instructions and downloads.  I just got the kernel sources and the driver.  I followed the instructions, and now I have suspend and DRI![/QUOTE]

In the instructions mentioned above, on step **4. Install packages and compile the kernel module**, there is a link to some pre-bluilt [kernel packages]("http://xoomer.virgilio.it/flavio.stanchina/debian-fglrx-modules/index.html").  Can those be used for Ubuntu Breezy?

---

### Post by Flopy on 2005-12-08
To remove the fglrx driver simply do:
$ cd /etc/X11
$ sudo cp xorg.conf xorg.conf_backup
$ sudo gedit xorg.conf

Then in this section:

Section "Device"
        Identifier      "ATI Technologies blah blah..."
        Driver          "fglrx" <---------- change "fglrx" to "ati"
        BusID           "PCI:1:0:0"
EndSection

---

### Post by geearf on 2005-12-08
here's a link I just found, if anyone wants to try this out :
[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2005-November/030323.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2005-November/030323.html)

---

### Post by GoodPanos on 2005-12-11
Thank you **Flopy** for the instructions.  I was waiting for that a long time. 

Has any one figured out the below yet?
[QUOTE=GoodPanos]In the instructions mentioned above, on step **4. Install packages and compile the kernel module**, there is a link to some pre-bluilt [kernel packages]("http://xoomer.virgilio.it/flavio.stanchina/debian-fglrx-modules/index.html").  Can those be used for Ubuntu Breezy?[/QUOTE]

---

### Post by jpkotta on 2005-12-15
[QUOTE=GoodPanos]Thank you **Flopy** for the instructions.  I was waiting for that a long time. 

Has any one figured out the below yet?[/QUOTE]

I didn't try the prebuilt modules.  The instructions [here]("http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html") (compling modules) worked just fine, and was easy enough.  Those instructions are kind of long, though, so I'll run through what I did.

[Download]("http://xoomer.virgilio.it/flavio.stanchina/debian-fglrx-xorg/index.html") the "driver" and "kernel-src" packages.  Install them with ```
sudo dpkg -i <.deb files>
```  There should now be a bunch of tools like fglrxinfo and libraries like libGL from the driver package, and a tarball in /usr/src from the kernel-src package.  Untar the tarball ```
cd /usr/src ; tar zxvf fglrx.tar.gz
``` Build the module with ```
cd /usr/src/modules/fglrx ; ./make.sh
```  After compiling, it will tell you where to copy the kernel module, and how to load it.

I did this a while ago, so let me know if there are any points I missed.


Here's another tip:

After rebooting, everything works perfectly.  After suspending and waking up,  xine video playback doesn't work.  The default video output driver seems to die.  I switched to the opengl driver ```
xine -V opengl
``` and it worked again.  To see a list of possible drivers, ```
xine --help
```

---

### Post by GoodPanos on 2005-12-16
I get an error on both packages when I run *sudo dpkg -i <.deb files>*.  That's because the previous version is there.  Is there way to remove those files?

---

### Post by pointym5 on 2005-12-31
Running with a fresh Breezy install on my old Dell CPt laptop, with the "ati" driver configured into xorg.conf, no suspend, standby, or hibernate functions work at all (and yes that's after editing the file in /etc/defaults).  Well, more precisely, the suspension works, but resuming after suspend never does - the laptop ends up in a weird limbo state.

The same laptop has had suspend/resume working flawlessly for a long time with never a need for any configuration changes while it ran Fedora Core 2.

---

### Post by pointym5 on 2006-01-01
[QUOTE=pointym5]Running with a fresh Breezy install on my old Dell CPt laptop, with the "ati" driver configured into xorg.conf, no suspend, standby, or hibernate functions work at all (and yes that's after editing the file in /etc/defaults).  Well, more precisely, the suspension works, but resuming after suspend never does - the laptop ends up in a weird limbo state.

The same laptop has had suspend/resume working flawlessly for a long time with never a need for any configuration changes while it ran Fedora Core 2.[/QUOTE]

I got everything to work by switching to APM instead of ACPI.  That laptop doesn't seem to have adequate ACPI support; I was able to get it to work erratically, but APM works all the time.

Boot flags: apm=on acpi=off

---

### Post by jpkotta on 2006-01-03
[QUOTE=GoodPanos]I get an error on both packages when I run *sudo dpkg -i <.deb files>*.  That's because the previous version is there.  Is there way to remove those files?[/QUOTE]

```
man dpkg
```

>        dpkg -r | --remove | -P | --purge package ... | -a | --pending
              Remove  an  installed  package.  -r or --remove remove everything except configuration files.  This may
              avoid having to reconfigure the package if it is reinstalled later.  (Configuration files are the files
              listed  in  the debian/conffiles control file).  -P or --purge removes everything, including configura&#8208;
              tion files.  If -a or --pending is given instead of a package name, then  all  packages  unpacked,  but
              marked to be removed or purged in file /var/lib/dpkg/status, are removed or purged, respectively.

---

### Post by jakemikey on 2006-02-22
I followed the steps in post #30 and I got an fglrx driver that allows suspend to work, but now I have no acceleration.  glxgears performs as if I have no DRI.  I got the exact same effect previously by just using the regular fglrx driver and disabling DRI in xorg.conf.

Anyone know how I can troubleshoot this so I can figure out why I now have no acceleration?

---

### Post by neuweiler on 2006-03-14
Latest fglrx 8.22.5-1 for xorg 6.8.0 works fine with suspend-to-disk and suspend-to-ram on my hp NC8000

suspend-to-ram didn't work for a long time and the screen was blank after re-start (with fglrx and radeon) but the cause for this was the WLAN configuration as reported by strawman: 
[http://www.ubuntuforums.org/showthread.php?t=106564]("http://www.ubuntuforums.org/showthread.php?t=106564")

neuweiler

---

### Post by misha680 on 2006-06-23
So I had a similar problem with suspend to ram broken using fglrx but not using the ati default driver (worked beautifully). I installed the latest version of the ATI driver from the ATI website (8.25.something I think, doesn't matter) and it still
didn't work (oh yeah I am using a Dell 600m). Finally, I got suspend to work by hacking my /etc/default/acpi-support file
based on stuff I read on these forums. To get it to work, I had to change the following options:

POST_VIDEO=false
USE_DPMS=false
SAVE_VBE_STATE=false

Initially, I also whitelisted fglrx, but this caused problems with ACPI power management in 8.28.16 ati driver, so I removed it and it works fine.

---

### Post by quini on 2006-06-30
[QUOTE=misha680]So I had a similar problem with suspend to ram broken using fglrx but not using the ati default driver (worked beautifully). I installed the latest version of the ATI driver from the ATI website (8.25.something I think, doesn't matter) and it still
didn't work (oh yeah I am using a Dell 600m). Finally, I got suspend to work by hacking my /etc/default/acpi-support file
based on stuff I read on these forums. Here is my file that NOW WORKS for fglrx! So I have both acceleration and suspend:[/QUOTE]

Thanks for that information, it seems to work fine in my Benq JB7000 (not tested extensively), but...

I use to have 2 users at the same time, so first user uses VT7, second uses VT8 (in Kde right button -> change user / change user).  It crashes immediately if done after a resume.

Shame.  I'm using latest driver ( 8.26.18 ) and a selfcompiled kernel.

Thanks anyway  :wink:

---

