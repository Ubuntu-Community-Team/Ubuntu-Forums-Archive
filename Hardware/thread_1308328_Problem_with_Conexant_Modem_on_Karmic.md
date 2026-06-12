---
title: "Problem with Conexant Modem on Karmic"
date: 2009-10-31
forum: Hardware
---

### Post by habib_seif on 2009-10-31
Hi all,

As you may know, Dell has written a good driver for Conexant modems installed on its laptops. The driver works good in older versions of Ubuntu, but in karmic, after installing the package, I encounter to the following problem after issuing the "sudo hsfconfig" command:
```
Building modules for kernel 2.6.31-14-generic, using source directory
/lib/modules/2.6.31-14-generic/build. Please wait...

ERROR: Module build failed!
Please examine the log file "/tmp/hsfconfig-buildlog.txt" to determine why.

```

and here is contents of /tmp/hsfconfig-buildlog.txt file:
```
(cd /lib/modules/2.6.31-14-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-14-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
(cd /lib/modules/2.6.31-14-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-14-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.31-14-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers
(cd /lib/modules/2.6.31-14-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-14-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from <command-line>:0:
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:244:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:265:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:286:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:304:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:322:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:343:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:366:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:388:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:406:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:425:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:447:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:469:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:490:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:508:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:526:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:548:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:570:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:593:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:614:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:645:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:667:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:688:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:712:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:736:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:757:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:9:
/usr/lib/hsfmodem/modules/GPL/oscompat.h:95:34: error: linux/byteorder/swab.h: No such file or directory
In file included from /usr/lib/hsfmodem/modules/mod_engine.c:10:
/usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: error: string.h: No such file or directory
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2

```

Can anyone help in solving the problem? Does anyone know if Dell still supports its conexant drivers?

Cheers,
Habib

---

### Post by sheperson on 2009-11-01
Hi,

I have the same problem.
Please someone help.
Thanks.

---

### Post by diaco on 2009-11-02
Same problem here
there was a solution here:
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)
it works for older kernels but doesn't work in karmic
can anybody fix it?

---

### Post by sheperson on 2009-11-02
> **diaco said:**
> Same problem here
there was a solution here:
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)
it works for older kernels but doesn't work in karmic
can anybody fix it?
I have the same problem on Fedora 11.
So, both my Linux OSs can't access the net. I tired of restarting my PC to get into the net. :(

---

### Post by diaco on 2009-11-02
I got it work on karmic right now! ;)
I'm configuring the old package to run without need any modification.
I'll upload it tommorow. sorry for delay!

---

### Post by habib_seif on 2009-11-02
Thanks a lot,
We're waiting....

Can't wait ;)
Habib

---

### Post by sheperson on 2009-11-02
> **diaco said:**
> I got it work on karmic right now! ;)
I'm configuring the old package to run without need any modification.
I'll upload it tommorow. sorry for delay!

Really! I can't wait for it. Please upload it soon. We are starving!


:guitar: =D>

---

### Post by dy1986 on 2009-11-02
My Too :(

---

### Post by diaco on 2009-11-03
First, download this zip file:
*[http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip](http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip)*
If you now how to build DELL's driver, or if you are at the point that [habib_seif]("http://ubuntuforums.org/member.php?u=82830") is, just simply use this package instead of old DELL driver.
Edited: some users have sound problems after installing this driver. Take a look at [this post]("http://ubuntuforums.org/showpost.php?p=8258559&postcount=21") for a solution.

If you are a newbie or don't have any experience with conexant modems, go to the next post!

---

### Post by diaco on 2009-11-03
Edited: some users have sound problems after installing this driver. Go to [this post]("http://ubuntuforums.org/showpost.php?p=8258559&postcount=21") for a solution.

This driver will enable Conexant modems installed on Vaio, DELL & ... laptops in ubuntu karmic (and other linux distributions with kernel version later than 2.6.30).

1. Preparation 
Note: If you first install the limited 14kbps driver from linuxant.com using their automatic installer, then you can skip preparation section and jump to step 2

Note: Ubuntu Karmic (9.10) Jaunty (9.04), Hardy (8.04) and SUSE (11.0, 11.1) users with HDA modems: Installing the latest alsa-driver-linuxant package is necessary before installing this driver.

Installing Generic alsa-driver-linux package with source:

Note: Before installing this package, make sure that you have the build-essential installed (for gcc and make are required). Additionally, the kernel headers are also needed, this is the linux-headers package. 

    wget _*[COLOR=Sienna][http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip)[/COLOR]*_
    unzip *.zip
    dpkg -i alsa-driver-linuxant_1.0.20.3_all.deb

2. Download this file:
    [COLOR=Sienna]_[*http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip*]("http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip")_[/COLOR]
3. Extract the archive to a folder, open a terminal window there and install it: "sudo make install"
4. Run command "hsfconfig" in terminal. Do not answer questions. Just type "enter" key and accept the default answers.
5. Finished! Your modem is ready at /dev/ttySHSF0. Full speed (56K). You can use gnome-ppp or kppp (as root) for dialup.
Please let me now if you had a successfull installation or if you encounter any problem.
This modem dirver includes files from DELL's oem driver and the limited (14K) Driver available at linuxant.com. and the preparation section is taken from: [COLOR=Sienna]_*[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)*_[/COLOR]

---

### Post by habib_seif on 2009-11-03
You're like a Herkul!!!

It works perfectly for me ;)

Thanks,
Habib

---

### Post by Paul S on 2009-11-04
Can you list the changes you made to get it to compile on karmic.  I'm trying to get the 64 bit version working.  I get the same error that habib was getting on 32 bit when running hsfconfig.  I tried all the stuff listed in the conexant help page, including linux/string.h, but still get that same error.

tia

---

### Post by Paul S on 2009-11-04
OK, I see you have to use the new version of modules/imported/include/framewrk.h in the build.

I'm connected now, but don't have any sound.  Installed the alsa-driver-linuxant .. any ideas?

---

### Post by mikilion on 2009-11-05
Even me on Karmic, after installing Generic alsa-driver-linux package with source and rebooted, sound is broken.
This is a part of logs messages:
snd_hda_codec: Unknown symbol snd_ctl_add
snd_hda_codec: Unknown symbol snd_card_register
snd_hda_codec: Unknown symbol snd_card_proc_new
snd_hda_codec: Unknown symbol snd_add_device_sysfs_file
snd_hda_codec: Unknown symbol snd_ctl_remove...

---

### Post by Paul S on 2009-11-05
I had a full system freeze after a short while running the modem on 64 bit karmic.  I've had freezes on all 64 bit conexant drivers on previous versions of ubuntu.  So, that problem continues.

Therefore, I switched over to 32 bit karmic and now sound works and modem works.  So far, no freeze up either.

I think 64 bit support is missing.

regards,

---

### Post by diaco on 2009-11-06
the changes are:
1. changes that are described *[here]("https://help.ubuntu.com/community/DialupModemHowto/Conexant")*
2. use the new version of /imported/include/framewrk.h
3. editing the file modules/imported/include/osservices.h to avoid string.h error

---

### Post by diaco on 2009-11-06
it appears that it causes sound problems on several machins. i think linuxant's alsa dirver must be patched too. can anybody take a look at this dirver?
*[http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip)*

---

### Post by Paul S on 2009-11-06
> **Paul S said:**
> I had a full system freeze after a short while running the modem on 64 bit karmic.  I've had freezes on all 64 bit conexant drivers on previous versions of ubuntu.  So, that problem continues.

Therefore, I switched over to 32 bit karmic and now sound works and modem works.  So far, no freeze up either.

I think 64 bit support is missing.

regards,

oops, I was wrong.  After a reboot sound is broken here even on 32 bit karmic.  But the modem does work and there is no freeze up.

---

### Post by Paul S on 2009-11-06
> **diaco said:**
> it appears that it causes sound problems on several machins. i think linuxant's alsa dirver must be patched too. can anybody take a look at this dirver?
*[http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip)*

Yes, that's the alsa driver I was using, and my sound is now broken.  However, when I first installed that linuxant alsa deb and rebooted, sound still worked.  Only after I installed the hsfmodem and rebooted did sound fail.

I recall that linuxant came out with a alsa debian a few weeks after jaunty was released.  Maybe we need to wait for a new one now that karmic is out.

regards,

---

### Post by Paul S on 2009-11-06
I installed kubuntu and am trying kde.  The sound works on kde.

Maybe the problem is a conflict with pulseaudio.

regards,

---

### Post by Paul S on 2009-11-06
there is indeed a pulseaudio bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500)

A temporary fix to our problem is to edit /etc/pulse/default.pa and change this:

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

to this:

### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
#.endif

than reboot.  One problem remains is that sound preferences still does not show card listing.

hth

---

### Post by maratonman on 2009-11-07
I have same problem,and I did what you wrote,and now it can`t initialize sound device.
I`m  running 32bit karmic koala.

---

### Post by maratonman on 2009-11-09
does anybody knows what is the problem?

---

### Post by amp3030 on 2009-11-09
> **Paul S said:**
> there is indeed a pulseaudio bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500)

A temporary fix to our problem is to edit /etc/pulse/default.pa and change this:


Thanks a lot! This worked for me just as you said. But now I have to 'sudo gnome-ppp' (run it as root) to connect. Someone suggested to add my username to 'dip' (via Users and Groups) but it didn't work either.

---

### Post by habib_seif on 2009-11-09
> **amp3030 said:**
> Someone suggested to add my username to 'dip' (via Users and Groups) but it didn't work either.

I have the same problem...

---

### Post by kaos_frack on 2009-11-15
> **diaco said:**
> Edited: some users have sound problems after installing this driver. Go to [this post]("http://ubuntuforums.org/showpost.php?p=8258559&postcount=21") for a solution.

This driver will enable Conexant modems installed on Vaio, DELL & ... laptops in ubuntu karmic (and other linux distributions with kernel version later than 2.6.30).

1. Preparation 
Note: If you first install the limited 14kbps driver from linuxant.com using their automatic installer, then you can skip preparation section and jump to step 2

Note: Ubuntu Karmic (9.10) Jaunty (9.04), Hardy (8.04) and SUSE (11.0, 11.1) users with HDA modems: Installing the latest alsa-driver-linuxant package is necessary before installing this driver.

Installing Generic alsa-driver-linux package with source:

Note: Before installing this package, make sure that you have the build-essential installed (for gcc and make are required). Additionally, the kernel headers are also needed, this is the linux-headers package. 

    wget _*[COLOR=Sienna][http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip)[/COLOR]*_
    unzip *.zip
    dpkg -i alsa-driver-linuxant_1.0.20.3_all.deb

2. Download this file:
    [COLOR=Sienna]_[*http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip*]("http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip")_[/COLOR]
3. Extract the archive to a folder, open a terminal window there and install it: "sudo make install"
4. Run command "hsfconfig" in terminal. Do not answer questions. Just type "enter" key and accept the default answers.
5. Finished! Your modem is ready at /dev/ttySHSF0. Full speed (56K). You can use gnome-ppp or kppp (as root) for dialup.
Please let me now if you had a successfull installation or if you encounter any problem.
This modem dirver includes files from DELL's oem driver and the limited (14K) Driver available at linuxant.com. and the preparation section is taken from: [COLOR=Sienna]_*[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)*_[/COLOR]

THANK YOU!
it worked! sound is also working!

---

### Post by Paul S on 2009-11-16
> **kaos_frack said:**
> THANK YOU!
it worked! sound is also working!

But, although it works sometimes, it still fails sometimes.  I missed most of a flash broadcast because it just stopped working.  I have the hda intel sound, so maybe it's still problematic.

Anyway, I took the more drastic step of removing pulseaudio altogether, following this thread [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4)

After it's removed, the mixer is broken.  So there's a great solution in this thread [http://ubuntuforums.org/showpost.php?p=8130297&postcount=25](http://ubuntuforums.org/showpost.php?p=8130297&postcount=25) , especially the post about alsa_volume.tar.bz2.

Then to fix aptitude dependencies, I installed equivs and created and installed an equivs-deb from this equivs control file:

Section: misc
Priority: optional
Standards-Version: 3.6.2
Package: equivs-pulseaudio
Provides: gstreamer0.10-pulseaudio, pulseaudio, pulseaudio-esound-compat
Description: fix pulseaudio dependencies after removing it


hth

---

### Post by Paul S on 2009-11-16
> **maratonman said:**
> does anybody knows what is the problem?

You may want to remove pulseaudio altogether, as explained in my last post.

hth

---

### Post by habib_seif on 2009-11-17
> **amp3030 said:**
> But now I have to 'sudo gnome-ppp' (run it as root) to connect. Someone suggested to add my username to 'dip' (via Users and Groups) but it didn't work either.

It also was solved for me....
After adding my current user to dip group, I had to dial by root once. After that, I can connect by normal user, too

Cheers,
Habib

---

### Post by mikilion on 2009-11-17
> **Paul S said:**
> there is indeed a pulseaudio bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500)

A temporary fix to our problem is to edit /etc/pulse/default.pa and change this...

I confirm, the sound works also for me.

---

### Post by amp3030 on 2009-11-21
> **habib_seif said:**
> It also was solved for me....
After adding my current user to dip group, I had to dial by root once. After that, I can connect by normal user, too

Cheers,
Habib

I removed the 'sudo' and now it works! Thanks! 

But I have to re-run 'sudo hsfconfig' occasionally to make my modem work again. Does anybody have the same problem?

---

### Post by Orion2000za on 2009-11-23
Seems to work perfect, lots of thanks for us still on dial-up!

:P

---

### Post by markc on 2009-11-29
DELL Inspiron 640m works with this method using Kubuntu Karmic, many thanks for the tip.

FWIW this lappie now connects via ethernet (naturally), normal wifi, Optus 3G mobile wireless and now 56K internal modem as well. Mind you, it took me 3 fairly long days to get it all working. Ironically, following these instructions was a breeze compared to getting the normal wifi to work!

---

### Post by maratonman on 2009-12-05
Paul S
I have tried this and this is what I get:
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open audio device for playback. [gstalsasink.c(690): gst_alsasink_open (): /GstPipeline:pipeline1/GstAlsaSink:alsasink4:
Playback open error on device 'default': No such file or directory]

---

### Post by maratonman on 2009-12-05
It works all fine!!!!!!!
Thanks a lot!!
I forgot that I installed new kernel,after updating alsa driver linuxant and running hsfconfig,it all works now modem and sound too.

---

### Post by unndreay on 2009-12-06
Hello,

tried it, too. But could not dial properly. I do not hear anything when calling a number (ATM2 and L2 are set), it just ends with NO CARRIER after a while and the calling cell phone never rings. The other way round, calling the modem and then answering the incoming call by an ATA command, works - but not the way I would call 'fine': there is no RING RING shown in the tty-connection and just a slight noise in my cell phone then, no specific answer tone as in windows. There everything works fine... It's annoying!

I really messed up my ubuntu when trying to get my modem working by this and that description. So I'd like to reinstall my kernel and then try it again. Could you tell me how to get there? I tried different things I found in this forum and elsewhere, but in the meantime my sound doesn't work either.

I tried to get the modem working by running [FONT=Courier New]hsfconfig[/FONT] and the proposed ALSA deb package. For getting rid of it I have run [FONT=Courier New]hsfconfig --uninstall[/FONT], [FONT=Courier New]hsfconfig -r[/FONT], reinstalled the kernel by [FONT=Courier New]apt-get reinstall[/FONT] and [FONT=Courier New]apt-get purge[FONT=Verdana]  -and[/FONT]- [/FONT][FONT=Courier New]apt-get [/FONT][FONT=Courier New]install linux-sound-base alsa-base alsa-utils[/FONT]. But now, sound is broken, just a Dummy exists in the applet.

Is there a way to completely reinstall the kernel now, without doing it to the whole system? I'm posting here, because you may have a sketchy idea of what i've done!?

Thank you for any hint!

unndreay

---

### Post by Audiossis on 2009-12-10
I know these are Ubuntu forums but this is the only solution I have yet found to using linuxant with 2.6.31 kernels. But in my experience solutions posted in Ubuntu forums are usually good for Gentoo as well.

I recently updated my Gentoo kernel to 2.6.31. I downloaded your package and followed your instructions.

Unfortunately it doesn't work for me. The build appears to complete successfully and the modules load without error BUT when I try to use wvdial to dial out on /dev/ttySHSF0, it returns the error message:

--> Cannot open /dev/ttySHSF0: Input/ouput error.

/dev/ttySHSF0 does exist as does ttySHSF1 etc to ttySHSF7.

I have also noticed that ALL the driver modules are loaded, even the ones that I don't need (hsfmc97sis, ati, ali, via etc) I should only need hsfmc97ich. I tried loading only hsfmc97ich but all the others are loaded as well.

I should point out that I used to use a cracked version of hsfmodem-7.68.00.14 and it worked fine until I updated my kernel for compatability with other packages.


Does anyone have any clues as to why this error is occuring?

**** EDIT ****

Also, what happened to the slamr and ungrab-winmodem module??? There is no mention of these changes on the linuxant web site that I can find!

---

### Post by unndreay on 2009-12-13
> **unndreay said:**
> Hello,

tried it, too. But could not dial properly. I do not hear anything when calling a number (ATM2 and L2 are set), it just ends with NO CARRIER after a while and the calling cell phone never rings. The other way round, calling the modem and then answering the incoming call by an ATA command, works - but not the way I would call 'fine': there is no RING RING shown in the tty-connection and just a slight noise in my cell phone then, no specific answer tone as in windows. There everything works fine... It's annoying!

I really messed up my ubuntu when trying to get my modem working by this and that description. So I'd like to reinstall my kernel and then try it again. Could you tell me how to get there? I tried different things I found in this forum and elsewhere, but in the meantime my sound doesn't work either.

I tried to get the modem working by running [FONT=Courier New]hsfconfig[/FONT] and the proposed ALSA deb package. For getting rid of it I have run [FONT=Courier New]hsfconfig --uninstall[/FONT], [FONT=Courier New]hsfconfig -r[/FONT], reinstalled the kernel by [FONT=Courier New]apt-get reinstall[/FONT] and [FONT=Courier New]apt-get purge[FONT=Verdana]  -and[/FONT]- [/FONT][FONT=Courier New]apt-get [/FONT][FONT=Courier New]install linux-sound-base alsa-base alsa-utils[/FONT]. But now, sound is broken, just a Dummy exists in the applet.

Is there a way to completely reinstall the kernel now, without doing it to the whole system? I'm posting here, because you may have a sketchy idea of what i've done!?

Thank you for any hint!

unndreay


Solved my sound issue by deleting all sound modules:

```
rm /lib/modules/`uname -r`/kernel/sound/*
```and reinstalling some packages:

```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` libasound2
```Found this at 
[http://help.ubuntu.com/community/SoundTroubleshooting#Manual%20Installation]("http://help.ubuntu.com/community/SoundTroubleshooting#Manual%20Installation")

> **Another way to restore ALSA to the Ubuntu default**

 I installed alsa from source, and wanted to revert so I wouldn't have to reinstall alsa everytime the kernel moved. The above did not work for me. Here's a safer way that did. 
That re-grabs all of the alsa binaries and modules. You may also need to 
```
ls -lt /lib/modules/`uname -r`/kernel/sound/
```And delete anything from the day you manually installed alsa.


Now, there is still no hardware list in sound settings, but sound works and i will leave it that way...

---

### Post by Fitch on 2010-02-02
Post 10 worked absolutely brilliant for me.

A few weeks later, I activated the computer janitor and didn't notice that hsfmodem was in the "unused" section until after I pressed OK.

Hey presto! no modem.

I re-installed (or tried to) and got a load of stuff basically saying "Go away. I'm not going to play"

Sudo hsfconfic came ip with:
insserv: warning: script 'S01linux-restricted-modules-common' missing LSB tags and overrides
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (2 3 4 5) of script `hsf' overwrites defaults (3 5).
insserv: warning: current stop runlevel(s) (0 1 6) of script `hsf' overwrites defaults (0 1 2 6).
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: warning: script 'rsyslog-kmsg' missing LSB tags and overrides
insserv: warning: script 'udev-finish' missing LSB tags and overrides
insserv: warning: current stop runlevel(s) (1) of script `policykit' overwrites defaults (empty).
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'ufw' missing LSB tags and overrides
insserv: warning: script 'usplash' missing LSB tags and overrides
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: script 'hal' missing LSB tags and overrides
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'linux-restricted-modules-common' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and hwclock if stopped
insserv:  loop involving service hwclock at depth 4
insserv:  loop involving service sysklogd at depth 3
insserv: There is a loop between service rsyslog and apache2 if stopped
insserv:  loop involving service apache2 at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service hwclock and sysklogd if started
insserv:  loop involving service sysklogd at depth 2
insserv:  loop involving service hwclock at depth 1
insserv: There is a loop between service hwclock and sysklogd if stopped
insserv:  loop involving service rsyslog at depth 1
insserv: There is a loop between service rsyslog and apache2 if stopped
insserv: exiting without changing boot order!
/sbin/insserv failed, exit code 1
brafferton@office:~/Desktop/hsfmodem-7.80.02.05-DiacoEdition$ 

Any ideas?

---

### Post by phoenix7 on 2010-02-06
I couldn't manage to get it to run. After compiling hsfmodem-7.80.02.05-DiacoEdition.zip, I ran hsfconfig and got this output.

```

Conexant HSF softmodem driver, version 7.68.00.09oem

If you need assistance or more information, please go to:
	http://www.linuxant.com/

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

Warning: existing driver modules found under:
	/lib/modules/2.6.31-19-generic/
Would you like to keep using them? [no] 

No pre-built modules for: Ubuntu-9.10 linux-2.6.31-19-generic i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.31-19-generic/build] 

Building modules for kernel 2.6.31-19-generic, using source directory
/lib/modules/2.6.31-19-generic/build. Please wait...
done.

Warning: no device detected by hsf driver - HDA modems may require reboot

Note: HDA support not compiled in the driver

Note: kernel module snd-via82xx-modem overridden by hsfmc97via
Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati

```

when I wanted to connect using gnome-ppp it gave me this message
```

Cannot open /dev/modem: Input/output error

```

Is it something related to my HDA modem? How can I fix it?

Note that I am using karmic on my Dell 640m.

---

### Post by habib_seif on 2010-02-23
> I couldn't manage to get it to run. After compiling hsfmodem-7.80.02.05-DiacoEdition.zip, I ran hsfconfig and got this output.

I recently have the same problem...
I think the latest kernel update of karmic (2.6.31-19) causes some problems.

Habib

---

### Post by Fitch on 2010-02-24
Definitely the kernel upgrade.  I now have a permanent directory of the install files for hsf modem. and was doing a make clean, makeinstall, hsfconfig, every two days at one point when the updates were comeing thick and fast,
but it always cured it... touch wood.

---

### Post by kwstas on 2010-02-24
sorry for my newbie question but i'm afraid to make any mistake here.
regarding the sound issues..  you meant that the fix is because efax has no sound(my issue) or the total system?

---

### Post by Fitch on 2010-02-24
The last few replies are to do with ttySHSF0 disappearing on a kernel upgrade.  This results in no fax or modem - the sound not being an issue as the modem is dead at this point.

If you re-install hsfmodem, then re-instal the alsa drivers, then you should get everything back.

---

### Post by kwstas on 2010-02-25
sorry i had to quote before!

my question is for this issue
>                                   **Re: Problem with Conexant Modem on Karmic**             
                                                                there is indeed a pulseaudio bug:

[https://bugs.launchpad.net/ubuntu/+s...io/+bug/394500]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500")

A temporary fix to our problem is to edit /etc/pulse/default.pa and change this:

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
.endif

to this:

### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
#.endif

than reboot.  One problem remains is that sound preferences still does not show card listing.

i have succesfuly installed the hsf drivers and efax-gtk is now working as it has detected the modem!
though i havent proceed in these fixes because i don't understand if they refer to general pc sound or modem sound.
my system has sound as normal.

"i never installed any sound drivers and i already had the last kernel installed"

---

### Post by kwstas on 2010-03-04
hey guys,

after the instructions of "diaco" i have my modem working now!
i'm a little worried though because it seems the speed is wrong...
here is what i get when i send a fax with efax-gtk:

> efax-0.9a: 16:32:43 opened /dev/ttySHSF0
efax-0.9a: 16:32:44 using hsfmodem-7.68.00.09oem in class 1
efax-0.9a: 16:32:44 dialing T23920xxxxxx
efax-0.9a: 16:33:04 connected
efax-0.9a: 16:33:05 Warning: bit-reversed HDLC frame, reversing bit order
efax-0.9a: 16:33:05 received UNKNOWN
efax-0.9a: 16:33:06 received CSI - answering ID
efax-0.9a: 16:33:06 The remote ID is      +30 2310 xxxxxx
efax-0.9a: 16:33:07 received DIS - answering capabilities
efax-0.9a: 16:33:07 remote has no documents to send and can receive
efax-0.9a: 16:33:07 local   196lpi 14.4kbps 8.5"/215mm  any   1D    -     -  0ms
efax-0.9a: 16:33:07 remote  196lpi 14.4kbps 8.5"/215mm  any   2D ECM-64   -  20ms
efax-0.9a: 16:33:07 session 196lpi 14.4kbps 8.5"/215mm  any   1D    -     -  20ms
efax-0.9a: 16:33:07 sent TSI - caller ID
efax-0.9a: 16:33:09 sent DCS - session format
efax-0.9a: 16:33:12 sent TCF - channel check of 2700 bytes
efax-0.9a: 16:33:14 received CFR - channel OK
efax-0.9a: 16:33:15 header:[2010-03-04 16:32    Joe Bloggs (0000 00000) --> 23920xxxxxx      1/1]
efax-0.9a: 16:34:03 sent 20+2292 lines and 10107+74611 bytes, in 48 secs at 14119 bps
efax-0.9a: 16:34:03 sent EOP - done
efax-0.9a: 16:34:05 received MCF - page OK
efax-0.9a: 16:34:05 sent page /home/kwstas/Desktop/AS.ps.001
efax-0.9a: 16:34:06 sent DCN - disconnect
efax-0.9a: 16:34:07 finished - success


sorry if i get a little off the topic...
i also noticed that when i send to some specific fax recipients, my call drops at the time that the recipient gives the signal. i'm not sure if these are related to modem or efax-gtk.

anyone can help pls?

---

### Post by frank cox on 2010-03-09
Just out of curiosity why is it important enough to have sound to go to these great lengths ? Are you all using the modem as an answering machine or you just want to hear it dial?

I went through the same nightmare until I found out network manager was not helping.
After buying a hardware modem I realized the Dell I had would connect on the internal windmodem {spelling intended}  with no modifications. I still think the external is faster so I use it and will buy an external USB hardware modem for my laptop.

Most of the time I use Puppy Linux on dialup. it is simple to get it to dial and much faster.

I like Ubuntu on broadband because it is more robust.

---

### Post by Shim on 2010-04-02
Hi all,
I am trying to install the modem drivers on Vostro 1500 + Karmic 64 bit.
I am following the instructions from this thread, but got stuck at the first bullet :(
I've downloaded the generic DEB package from the linuxant site, but the installation fails with the following error:
```

shim@ubuntu:~/Downloads/Modem$ sudo dpkg -i alsa-driver-linuxant_1.0.20.3_all.deb 
[sudo] password for shim: 
Selecting previously deselected package alsa-driver-linuxant.
(Reading database ... 178012 files and directories currently installed.)
Unpacking alsa-driver-linuxant (from alsa-driver-linuxant_1.0.20.3_all.deb) ...
Setting up alsa-driver-linuxant (1.0.20.3) ...
Building modules for the 2.6.31-20-generic kernel, please wait... done.
Conexant HSF softmodem driver, version 7.68.00.09oem

If you need assistance or more information, please go to:
    http://www.linuxant.com/

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

No pre-built modules for: Ubuntu-9.10 linux-2.6.31-20-generic x86_64-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Building modules for kernel 2.6.31-20-generic, using source directory
/lib/modules/2.6.31-20-generic/build. Please wait...

ERROR: Module build failed!
Please examine the log file "/etc/hsfmodem/log/buildlog-20100402204815.txt" to determine why.

Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot

```
Here is the text from the txt file it creates during the build process.
```

driver version 7.68.00.09oem
Makefile:25: *** WARNING: Trying to compile kernel modules on a x86_64 system while the installed hsf driver package is for i386, this is likely to fail... ***
(cd /lib/modules/2.6.31-20-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-20-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
/usr/lib/hsfmodem/modules/Makefile:25: *** WARNING: Trying to compile kernel modules on a x86_64 system while the installed hsf driver package is for i386, this is likely to fail... ***
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
(cd /lib/modules/2.6.31-20-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-20-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.31-20-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-20-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
/usr/lib/hsfmodem/modules/Makefile:25: *** WARNING: Trying to compile kernel modules on a x86_64 system while the installed hsf driver package is for i386, this is likely to fail... ***
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
/usr/lib/hsfmodem/modules/mod_engine.c:1: error: CPU you selected does not support x86-64 instruction set
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [all] Error 2

```

What should I do next?

---

### Post by fcorades on 2010-04-03
How install Conexant Modem driver FREE on Karmic 64 bit with kernel 2.6.31-20:

Download the following package:

([http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.05x86_64full/hsfmodem-7.80.02.05x86_64full.tar.gz](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.05x86_64full/hsfmodem-7.80.02.05x86_64full.tar.gz))
**Original source (path A): hsfmodem-7.80.02.05x86_64full**

([http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09x86_64oem.tar.gz](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09x86_64oem.tar.gz))
**Dell OEM source (path B): hsfmodem-7.68.00.09x86_64oem**

Extract the package on your home.

1) rename this folder : (path A)/modules/imported ---> (path A)/modules/imported.orig
2) copy this folder :   (path B)/modules/imported ---> (path A)/modules/
3) rename this folder : (path A)/modules/imported/include --> (path A)/modules/imported/include.orig
4) copy this folder :   (path A)/modules/imported.orig/include --> (path A)/modules/imported/include
5) cd hsfmodem-7.80.02.05x86_64full
6) sudo make uninstall
7) sudo make clean
8) sudo make install
9) sudo hsfconfig

---

### Post by Shim on 2010-04-05
I followed the instructions from the previous post, but still no luck... :(

here is the output from the console...


```

**shim@ubuntu:~/Downloads/Modem/hsfmodem-7.80.02.05x86_64full$ sudo make uninstall** 
[sudo] password for shim: 
if [ -x /usr/sbin/hsfconfig ]; then \
        /usr/sbin/hsfconfig -remove; \
    else \
        true; \
    fi
Warning: Module snd_hda_intel is in use
Warning: Module snd_hda_codec_idt is in use
Warning: Module snd_hda_codec is in use by snd_hda_codec_idt,snd_hda_intel
Sending TERM signal to processes still using the driver:
  PID USER     COMMAND
14849 shim     /usr/bin/pulseaudio --start --log-target=syslog
Warning: Module snd_hda_intel is in use
Warning: Module snd_hda_codec_idt is in use
Warning: Module snd_hda_codec is in use by snd_hda_codec_idt,snd_hda_intel
Warning: Module snd_hda_intel is in use
Warning: Module snd_hda_codec_idt is in use
Warning: Module snd_hda_codec is in use by snd_hda_codec_idt,snd_hda_intel
Warning: Module snd_hda_intel is in use
Warning: Module snd_hda_codec_idt is in use
Warning: Module snd_hda_codec is in use by snd_hda_codec_idt,snd_hda_intel
Sending KILL signal to processes still using the driver:
  PID USER     COMMAND
23714 shim     /usr/bin/pulseaudio --start --log-target=syslog
Warning: Module snd_hda_intel is in use
Warning: Module snd_hda_codec_idt is in use
Warning: Module snd_hda_codec is in use by snd_hda_codec_idt,snd_hda_intel
Warning: Module snd_hda_intel is in use
Warning: Module snd_hda_codec_idt is in use
Warning: Module snd_hda_codec is in use by snd_hda_codec_idt,snd_hda_intel
ERROR: Can't stop the Conexant HSF softmodem driver!
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/nvm'
rm -rf  "/etc/hsfmodem/nvm/hsfpcibasic2"  "/etc/hsfmodem/nvm/hsfpcibasic2smart"  "/etc/hsfmodem/nvm/hsfpcibasic2hsfi"  "/etc/hsfmodem/nvm/hsfpcibasic2bry"  "/etc/hsfmodem/nvm/hsfpcibasic3"  "/etc/hsfmodem/nvm/hsfmc97"  "/etc/hsfmodem/nvm/hsfmc97ali"  "/etc/hsfmodem/nvm/hsfmc97ati"  "/etc/hsfmodem/nvm/hsfmc97ich"  "/etc/hsfmodem/nvm/hsfmc97sis"  "/etc/hsfmodem/nvm/hsfmc97via"  "/etc/hsfmodem/nvm/hsfcadmus2"  "/etc/hsfmodem/nvm/hsfcadmus2smart"  "/etc/hsfmodem/nvm/hsfhda"
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/nvm'
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/scripts'
rm -f  "/usr/sbin/hsfconfig"  "/usr/sbin/hsfstop"  "/usr/sbin/hsfmodconflicts"  "/usr/sbin/hsfdcpd"
rm -f  "/usr/lib/hsfmodem/rchsf"
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/scripts'
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/modules'
rm -rf "/usr/lib/hsfmodem/config.mak" "/usr/lib/hsfmodem/modules/imported" "/usr/lib/hsfmodem/modules"
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/modules'
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/diag'
rm -f "/usr/sbin/hsfdiag" "/usr/sbin/hsfscr" "/usr/sbin/hsfdmp"
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/diag'
rm -f /usr/lib/hsfmodem/LICENSE
rm -f /etc/hsfmodem/package
**shim@ubuntu:~/Downloads/Modem/hsfmodem-7.80.02.05x86_64full$ sudo make clean**
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/nvm'
rm -rf cvt
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/nvm'
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/scripts'
rm -f  hsfconfig.in  hsfstop.in  hsfmodconflicts.in  hsfdcpd.in  rchsf.in
rm -f hsfconfig hsfstop hsfmodconflicts hsfdcpd rchsf patcher
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/scripts'
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/modules'
(cd /lib/modules/2.6.31-20-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-20-generic/build" "M=/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/modules" "CC=gcc" clean)
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
(cd /lib/modules/2.6.31-20-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-20-generic/build" "M=/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/modules'
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/diag'
rm -f *.o 
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/diag'
rm -f hsfmodem.spec packages/SPECS/hsfmodem.spec
rm -f ./cnxtmodem.spec ./scripts/cnxtstop ./scripts/cnxtmodconflicts ./scripts/cnxtdcpd ./scripts/rccnxt ./scripts/cnxtconfig ./scripts/patcher
**shim@ubuntu:~/Downloads/Modem/hsfmodem-7.80.02.05x86_64full$ sudo make install** 
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/nvm'
mkdir -m 755 -p cvt
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic2.inf | ./cvtinf.pl cvt/hsfpcibasic2; if [ -n "inf/hsf.cty" ]; then ./cvtinf.pl cvt/hsfpcibasic2 < "inf/hsf.cty"; else true; fi
(cd cvt/hsfpcibasic2/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic2/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic2smart.inf | ./cvtinf.pl cvt/hsfpcibasic2smart; if [ -n "" ]; then ./cvtinf.pl cvt/hsfpcibasic2smart < ""; else true; fi
if [ -d cvt/hsfpcibasic2/Profile ]; then ln -sf ../hsfpcibasic2/Profile cvt/hsfpcibasic2smart/.; else true; fi
ln -sf ../hsfpcibasic2/Region cvt/hsfpcibasic2smart/.
(cd cvt/hsfpcibasic2smart/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic2smart/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic2hsfi.inf | ./cvtinf.pl cvt/hsfpcibasic2hsfi; if [ -n "inf/hsf.cty" ]; then ./cvtinf.pl cvt/hsfpcibasic2hsfi < "inf/hsf.cty"; else true; fi
rm -rf cvt/hsfpcibasic2hsfi/Region
ln -sf ../hsfpcibasic2/Region cvt/hsfpcibasic2hsfi/.
(cd cvt/hsfpcibasic2hsfi/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic2hsfi/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic2bry.inf | ./cvtinf.pl cvt/hsfpcibasic2bry; if [ -n "inf/hsf.cty" ]; then ./cvtinf.pl cvt/hsfpcibasic2bry < "inf/hsf.cty"; else true; fi
rm -rf cvt/hsfpcibasic2bry/Region
ln -sf ../hsfpcibasic2/Region cvt/hsfpcibasic2bry/.
(cd cvt/hsfpcibasic2bry/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic2bry/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfpcibasic3.inf | ./cvtinf.pl cvt/hsfpcibasic3; if [ -n "inf/hsf.cty" ]; then ./cvtinf.pl cvt/hsfpcibasic3 < "inf/hsf.cty"; else true; fi
rm -rf cvt/hsfpcibasic3/Region
ln -sf ../hsfpcibasic2/Region cvt/hsfpcibasic3/.
(cd cvt/hsfpcibasic3/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfpcibasic3/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfmc97ich.inf | ./cvtinf.pl cvt/hsfmc97; if [ -n "" ]; then ./cvtinf.pl cvt/hsfmc97 < ""; else true; fi
rm -f mc97/HW_ADAPTER_TYPE
ln -sf ../hsfpcibasic2smart/Profile cvt/hsfmc97/.
ln -sf ../hsfpcibasic2smart/Region cvt/hsfmc97/.
(cd cvt/hsfmc97/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfmc97/COUNTRY_CODE_LIST
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97ali
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97ati
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97ich
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97sis
ln -sf `basename cvt/hsfmc97` cvt/hsfmc97via
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfcadmus2.inf | ./cvtinf.pl cvt/hsfcadmus2; if [ -n "" ]; then ./cvtinf.pl cvt/hsfcadmus2 < ""; else true; fi
rm -f cadmus2/HW_ADAPTER_TYPE
ln -sf ../hsfpcibasic2/Profile cvt/hsfcadmus2/.
ln -sf ../hsfpcibasic2/Region cvt/hsfcadmus2/.
(cd cvt/hsfcadmus2/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfcadmus2/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfcadmus2smart.inf | ./cvtinf.pl cvt/hsfcadmus2smart; if [ -n "" ]; then ./cvtinf.pl cvt/hsfcadmus2smart < ""; else true; fi
rm -f cadmus2smart/HW_ADAPTER_TYPE
ln -sf ../hsfpcibasic2smart/Profile cvt/hsfcadmus2smart/.
ln -sf ../hsfpcibasic2smart/Region cvt/hsfcadmus2smart/.
(cd cvt/hsfcadmus2smart/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfcadmus2smart/COUNTRY_CODE_LIST
sed -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' -e 's!@CNXTTARGET@!hsf!g' -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' < inf/hsfhda.inf | ./cvtinf.pl cvt/hsfhda; if [ -n "" ]; then ./cvtinf.pl cvt/hsfhda < ""; else true; fi
rm -f hda/HW_ADAPTER_TYPE
ln -sf ../hsfpcibasic2smart/Profile cvt/hsfhda/.
ln -sf ../hsfpcibasic2smart/Region cvt/hsfhda/.
(cd cvt/hsfhda/Region && grep -v -l '\*' *NAME | sed -e 's/^0//' -e 's/^0//' -e 's/_NAME$//' | tr '\012' ',' | sed -e 's/,$//' -e 's/^/"/' -e 's/$/"/' ; echo "") > cvt/hsfhda/COUNTRY_CODE_LIST
cd cvt && find . -type f ! -empty -exec md5sum {} ';' | sort | \
    while read sum file ; do \
        if [ "$sum" = "$prevsum" ] && cmp -s "$file" "$prevfile"; then \
            rm -f "$file"; \
            if ! ln "$prevfile" "$file"; then \
                echo 2>&1 "$0: ln FAILED - recreate $file based on $prevfile"; \
                exit 1; \
            fi; \
        else \
            prevsum="$sum"; \
            prevfile="$file"; \
        fi; \
    done
touch cvt/.linksame
cd cvt && (find  hsfpcibasic2  hsfpcibasic2smart  hsfpcibasic2hsfi  hsfpcibasic2bry  hsfpcibasic3  hsfmc97  hsfmc97ali  hsfmc97ati  hsfmc97ich  hsfmc97sis  hsfmc97via  hsfcadmus2  hsfcadmus2smart  hsfhda | cpio -pdmu /etc/hsfmodem/nvm)
127 blocks
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/nvm'
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/scripts'
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!x86_64!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < patcher.in > patcher
chmod --reference=patcher.in patcher
ln -s cnxtconfig.in hsfconfig.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!x86_64!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < hsfconfig.in > hsfconfig
chmod --reference=hsfconfig.in hsfconfig
ln -s cnxtstop.in hsfstop.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!x86_64!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < hsfstop.in > hsfstop
chmod --reference=hsfstop.in hsfstop
ln -s cnxtmodconflicts.in hsfmodconflicts.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!x86_64!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < hsfmodconflicts.in > hsfmodconflicts
chmod --reference=hsfmodconflicts.in hsfmodconflicts
ln -s cnxtdcpd.in hsfdcpd.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!x86_64!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < hsfdcpd.in > hsfdcpd
chmod --reference=hsfdcpd.in hsfdcpd
install -m 700 hsfconfig hsfstop hsfmodconflicts hsfdcpd /usr/sbin
ln -s rccnxt.in rchsf.in
sed \
        -e "s!@DATE@!`date \"+%a, %d %b %Y %T %z\"`!g" \
        -e 's!@CNXTDRIVER@!hsf!g' \
        -e 's!@CNXTDRVDSC@!Conexant HSF softmodem!g' \
        -e 's!@CNXTTARGET@!hsf!g' \
        -e 's!@CNXTARCH@!x86_64!g' \
        -e 's!@CNXTSERDEV@!HSF!g' \
        -e 's!@CNXTMAXMDM@!8!g' \
        -e 's!@CNXTETCDIR@!/etc/hsfmodem!g' \
        -e 's!@CNXTLIBDIR@!/usr/lib/hsfmodem!g' \
        -e 's!@CNXTSERIALMAJOR@!240!g' \
        -e 's!@CNXTCALOUTMAJOR@!241!g' \
        -e 's!@CNXTSERIALMINOR@!64!g' \
        -e 's!@CNXTDCPMAJOR@!242!g' \
        -e 's!@CNXTDIAGMAJOR@!243!g' \
        -e 's!@CNXTDIAGDMPMINOR@!255!g' \
        -e 's!@CNXTSCRMAJOR@!244!g' \
        -e 's!@CNXTSBINDIR@!/usr/sbin!g' \
        -e 's!@CNXTNVMDIR@!/etc/hsfmodem/nvm!g' \
        -e 's!@CNXTLINUXVERSION@!7.68.00.09x86_64oem!g' \
        -e 's!@CNXTLINUX_REL@!1!g' \
        -e 's!@CNXTLINUXRPM_REL@!1!g' \
        -e 's!@CNXTLINUXDEB_REL@!1!g' \
        -e 's!@CNXTMODS@!hsfpcibasic2 hsfpcibasic3 hsfmc97ich hsfmc97via hsfmc97ali hsfmc97ati hsfmc97sis hsfusbcd2 snd_hda_codec_hsfmodem hsfhda hsfsoar hsfserial hsfengine hsfosspec!g' \
        -e 's!@PATCHERURL@!http://www.linuxant.com/drivers/hsf/full/archive/patches!g' \
        -e 's!@PATCHERURLUSER@!http://www.linuxant.com/drivers/hsf/downloads-patches.php!g' \
        -e "s!@BLAM_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@SCR_SUPPORT@!`test ! \"\" = yes; echo $?`!g" \
        -e "s!@DMP_SUPPORT@!`test -z \"\"; echo $?`!g" \
        < rchsf.in > rchsf
chmod --reference=rchsf.in rchsf
install -m 700 rchsf /usr/lib/hsfmodem
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/scripts'
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/modules'
rm -rf "/usr/lib/hsfmodem/config.mak" "/usr/lib/hsfmodem/modules/imported" "/usr/lib/hsfmodem/modules"
mkdir -m 755 -p /usr/lib/hsfmodem/modules
(cd .. && find config.mak modules/imported -depth -print | cpio -pdmu /usr/lib/hsfmodem)
8944 blocks
find . \( -name COPYING -o -name '*.sh' -o -name '*.[ch]' -o -name '*.mak' -o -name '[Mm]akefile' \) -print | cpio -pdmu /usr/lib/hsfmodem/modules
5856 blocks
find binaries -depth -print | cpio -pdmu /usr/lib/hsfmodem/modules
0 blocks
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/modules'
make[1]: Entering directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/diag'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/shim/Downloads/Modem/hsfmodem-7.80.02.05x86_64full/diag'
install -m 444 LICENSE /usr/lib/hsfmodem

To complete the installation and configuration of your modem,
please run "hsfconfig" (or "/usr/sbin/hsfconfig")
**shim@ubuntu:~/Downloads/Modem/hsfmodem-7.80.02.05x86_64full$ sudo hsfconfig**
Conexant HSF softmodem driver, version 7.68.00.09x86_64oem

If you need assistance or more information, please go to:
    http://www.linuxant.com/

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

No pre-built modules for: Ubuntu-9.10 linux-2.6.31-20-generic x86_64-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.31-20-generic/build] 

Building modules for kernel 2.6.31-20-generic, using source directory
/lib/modules/2.6.31-20-generic/build. Please wait...

ERROR: Module build failed!
Please examine the log file "/etc/hsfmodem/log/buildlog-20100405143931.txt" to determine why.

```

and the txt file:

```

driver version 7.68.00.09x86_64oem
(cd /lib/modules/2.6.31-20-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-20-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
(cd /lib/modules/2.6.31-20-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-20-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.31-20-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.31-20-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-20-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from <command-line>:0:
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:244:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:265:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:286:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:304:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:322:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:343:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:366:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:388:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:406:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:425:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:447:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:469:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:490:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:508:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:526:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:548:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:570:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:593:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:614:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:645:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:667:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:688:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:712:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:736:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:757:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [all] Error 2

```

---

### Post by PRDR on 2010-04-17
Hi:

I followed fcorades  last post in my kubuntu karmic 64 bits, and everything went well :) until I did the "sudo hsfconfig". Then I got :(

```
Conexant HSF softmodem driver, version 7.68.00.09x86_64oem

If you need assistance or more information, please go to:
        http://www.linuxant.com/

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: warning: script 'hal' missing LSB tags and overrides
insserv: Script elektra-kdbd is broken: incomplete LSB comment.
insserv: missing `Required-Stop:'  entry: please add even if empty.
insserv: missing `Default-Start:'  entry: please add even if empty.
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `elektra-kdbd'
insserv: warning: script 'kdm' missing LSB tags and overrides
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
insserv: warning: script 'hwclock' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: script 'dbus' missing LSB tags and overrides
insserv: warning: script 'rsyslog-kmsg' missing LSB tags and overrides
insserv: warning: script 'rsyslog' missing LSB tags and overrides
insserv: warning: script 'network-manager' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'acpi-support' missing LSB tags and overrides
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
insserv: Script virtuoso-nepomuk is broken: missing end of LSB comment.
insserv: exiting now!
/sbin/insserv failed, exit code 1
```

I saw those same errors in some previous posts, but I am not sure I understood if there is some other fix for them. Any help will be greatly appreciated.

Thanks in advance.

---

### Post by fcorades on 2010-04-30
In your log there is :
ERROR: Can't stop the Conexant HSF softmodem driver!

You need to unload the module.

---

### Post by lfloyd on 2010-05-05
I'm having the same problem.  I tried all the drivers and when I run hsfconfig all I get is missing LSB tags and overriding errors.  I can't install my modem at all because of these errors.  This is unacceptable.  Businesses and schools cannot rely on products like Ubuntu with these kind of bugs.  With these kind of bugs Ubuntu will remain a household toy for those new to linux.  I can't afford these kind of errors.  I have servers that are providing services and all I want Ubuntu to do is fax. It is is the only linux server that I have that I can't use.  I'm not interesting in surfing and social dating on the internet.  I want to provide services. I simply cannot trust Ubuntu not to break itself.  It was the same three years ago.  I'm back and its still the same.  I'm sorry for venting, but I'm sick of these types of problems.  And yes you do need sound for your modem so that you can here if its working.  Modem function is of critical importance and I'm on broadband.  

Loretta

---

### Post by Shim on 2010-05-05
After upgrading to 10.04 managed to run hsfconfig without the previous errors, but now got stuck with no sound :(
here is the output from re-running hsfconfig
```

shim@ubuntu:~$ sudo hsfconfig
[sudo] password for shim: 
Conexant HSF softmodem driver, version 7.68.00.09x86_64oem

If you need assistance or more information, please go to:
    http://www.linuxant.com/

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

Warning: existing driver modules found under:
    /lib/modules/2.6.32-21-generic/
Would you like to keep using them? [no] 

No pre-built modules for: Ubuntu-10.04 linux-2.6.32-21-generic x86_64-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.32-21-generic/build] 

Building modules for kernel 2.6.32-21-generic, using source directory
/lib/modules/2.6.32-21-generic/build. Please wait...
WARNING: Module /lib/modules/2.6.32-21-generic/extra/hsfserial.ko ignored, due to loop
done.

Warning: hsf driver not active - HDA modems may require reboot

Note: HDA support not compiled in the driver
shim@ubuntu:~$ 

```
reboot does not solves the issue ](*,)
ideas?

---

### Post by blulite on 2010-05-08
> arning: hsf driver not active - HDA modems may require reboot

Note: HDA support not compiled in the driver
shim@ubuntu:~$

Me too.  Help?

---

### Post by blulite on 2010-05-15
bump.

---

### Post by HisBigness on 2010-05-24
I installed diaco's driver and was able to dial using pon/poff. However, I wasn't able to establish a connection. The modem would just hang up after making the usual sign in robot gibberish. Then I restarted my computer and pon would no longer attempt to dial. A process was running and I could shut it off with poff.  I did a sound-test and my speakers are functioning. But just to be sure i removed and reinstalled alsa and the other audio contoller and got the same result - sound test works, no dialing. 
 
Any ideas?

---

### Post by blulite on 2010-05-24
There's a new alsa driver on [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) that now works with Karmic.

---

### Post by bohemier on 2010-06-16
Shim, I was in the same situation, here's what I did to get back on my feet with sound:
Uninstall alsa-driver-linuxant: 
```
sudo dkpg -r alsa-driver-linuxant
```
Uninstall hsf driver: cd hsfmodem-7.80.02.05x86_64full (or whatever the directory name is for the source of this driver)
```
sudo make uninstall
```
Still no sound? Try reinstalling the kernel package
```
sudo apt-get --reinstall install linux-image-`uname -r`
```

That got my sound working again. Now, as for correctly installing that alsa-driver-linuxant: You need to install the generic alsa-driver-linuxant FIRST from [here]("http://www.linuxant.com/alsa-driver/downloads.php#generic"). For example: ```
wget http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip
``` (When the version changes, this link may no longer work). Then install it:```
unzip alsa-driver-linuxant_1.0.23.0_all.deb.zip
sudo dpkg -i alsa-driver-linuxant_1.0.23.0_all.deb
```

Then I installed the hsf driver as instructed by fcorades, but hsfconfig --info gives ```
Warning: hsf driver not active - HDA modems may require reboot
``` even after reboot... Anyone got that hsf modem driver working in Lucid 64?

---

### Post by amp3030 on 2010-07-25
> **lfloyd said:**
> I'm having the same problem.  I tried all the drivers and when I run hsfconfig all I get is missing LSB tags and overriding errors.  I can't install my modem at all because of these errors.  This is unacceptable.  Businesses and schools cannot rely on products like Ubuntu with these kind of bugs.  With these kind of bugs Ubuntu will remain a household toy for those new to linux.  I can't afford these kind of errors.  I have servers that are providing services and all I want Ubuntu to do is fax. It is is the only linux server that I have that I can't use.  I'm not interesting in surfing and social dating on the internet.  I want to provide services. I simply cannot trust Ubuntu not to break itself.  It was the same three years ago.  I'm back and its still the same.  I'm sorry for venting, but I'm sick of these types of problems.  And yes you do need sound for your modem so that you can here if its working.  Modem function is of critical importance and I'm on broadband.  

Loretta

I know how to solve this: open a terminal and type: sudo gnome-ppp
(first you should install GNOME-PPP if you haven't.)

enter your password and then gnome-ppp appears. Enter the phone number and user/pass and then Click connect. You can actually connect to the Internet. Once you do this, the problem is fixed; you can start gnome-ppp normally and it works :)

---

