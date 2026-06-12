---
title: "Wacom Bamboo Works in 7.04 - How To"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by cubeist on 2007-11-02
Hello All, I just got my new wacom bamboo this week (the regular model not the bamboo fun) and was able to successfully compile the drivers.  Everything works, all the buttons can be customized and pressure sensitivity works well in gimp 2.4.  Here's how I got it working in Feisty... basically I just followed the great tutorial from the linux wacom project, but many people find that a bit too comprehensive.  Therefore, I will outline the steps I used to get my bamboo working, so hopefully you can get yours working too! (Note: this should work for both bamboo and bamboo fun although I have not tested the fun model) (Note2: If you are even a remotely advanced linux user you should use the linux wacom project tutorial as it is much better than what I can provide!)



First, the drivers from synaptic (0.7.7) do not recognize the bamboo (or bamboo fun) so you can't just plug it in and have it start working.  In order to get your bamboo working you will need to custom compile the drivers from the linux wacom project ([http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)).  Even though the 0.7.7 drivers in synaptic don't recognize the bamboo you will need the xserver-xorg-input-wacom (0.7.7) and wacom-tools to compile the driver in the next step, so make sure they are installed.  Also, while in synaptic you can install tcl and tk 8.4 dev files if you want to compile wacomcpl, however, this is completely optional and if you don't know what wacomcpl is you probably don't need it.  Lets move on.

Download the latest stable version 0.7.8-3 from [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/) and extract the files.  Open up a terminal session, navigate to the folder you extracted your files in and type [COLOR="Red"]./configure --help[/COLOR]  This will give you all the options available for a custom compile.  The defaults were aok for me so I just entered [COLOR="Red"]./configure[/COLOR] and hit return.  Note: One area where some people have messed up on is adding --enable-wacom to the configure which builds a wacom.o driver... unless you are specifically running an old 2.4 kernel you do not need to add --enable-wacom

If your configure comes back with errors it is probably because you do not have the correct dependencies on you computer.  The easiest way to fix this is check to see where the config failed and add the appropriate library it needs from synaptic.  For example, to build wacomcpl you first need the tcl and tk -dev files... just search for them on synaptic and install them, then reconfigure.

If you didn't get any errors you can finish the install by typing [COLOR="Red"]make[/COLOR] and then [COLOR="Red"]sudo make install[/COLOR].  However this won't install the driver... just the associated wacom tools.  Note: Another area where some users may encounter difficulties is if they have tried installing wacom drivers previously, perhaps a prior beta driver... if this applies to you, type [COLOR="Red"]make clean[/COLOR], then [COLOR="Red"]make[/COLOR], then [COLOR="Red"]sudo make install[/COLOR], this will clean out the old files first.

For Bamboo Fun --- You need to patch the src files to get a working tablet.
You can get the patch here <http://sourceforge.net/tracker/index.php?func=detail&aid=1802837&group_id=69596&atid=525126>
I haven't tried this, but it looks fairly straight forward... it also looks like you could manually change the dev id... for those advanced users who know how...

To install the actual driver I will now refer you to part 3 of the linux wacom manual.  It explains things much better than I could, specifically, follow this page <http://linuxwacom.sourceforge.net/index.php/howto/testwacom>.  That page asks you to navigate to your [COLOR="RoyalBlue"]/src/2.4.22[/COLOR], but assuming everyone reading this is now using at least FF you should navigate to [COLOR="RoyalBlue"]/src/2.6.19[/COLOR] (for 7.04) or [COLOR="RoyalBlue"]/src/2.6.22[/COLOR] if you are using gutsy gibbon and the beta 7.9.1 files from linux wacom.  The rest of the commands on that page worked fine for me and my bamboo lit up like a blue Christmas tree.  In [COLOR="Red"]tail /var/log/messages[/COLOR] my bamboo was recognized using 1.4.6-pc, hopefully yours is too.

If your still with me, go to the next page in the tutorial on linux wacom<http://linuxwacom.sourceforge.net/index.php/howto/installwacom> and follow the instructions.  Basically you are copying the file from your [COLOR="RoyalBlue"]/src[/COLOR] folder to the system.  For me this was: [COLOR="Red"]sudo cp wacom.ko /lib/modules/2.6.20-15-generic/kernel/drivers/usb/input/[/COLOR] yours may be different... just use the locate wacom.ko to find the correct path.

Next page, <http://linuxwacom.sourceforge.net/index.php/howto/loadwacom> your almost there.  Basically the only commands you want to follow on this page are [COLOR="Red"]sudo rmmod wacom[/COLOR] first which will unload the module and the lights on tablet will go out, then [COLOR="Red"]sudo modprobe wacom[/COLOR] and the lights should come back on... the reason to do this is to verify if you get errors when loading the module.  Hopefully you don't.  Use [COLOR="Red"]tail /var/log/messages[/COLOR] again to ensure there are no error messages.

Congrats, you have done the hard part, the rest is really easy.  You can now skip ahead to section five of the tutorial to get your xorg.conf file working but you will want to go back and read the pages you skipped when you are finished, learning how to use wacdump is important.  Note, everybody using a 2.6 + kernel should ignore the pages about building evdev and hid.ko as these are not required to get the bamboo working... they may be needed for a bamboo fun mouse, but I am not sure about this.  Also, they are interesting reading for later.


Go to section five <http://linuxwacom.sourceforge.net/index.php/howto/inputdev> and follow that page to a tee (NOTE! I had to use the standard [COLOR="RoyalBlue"]/dev/input/wacom[/COLOR] for my tablet to work because each time I plug it in the computer automatically assigns a different event number (usually event9 or event10 for me) which [COLOR="RoyalBlue"]/dev/input/wacom[/COLOR] is auto linked to the correct event).  If you have never edited your xorg.conf file before you should know the first step is to always create a backup.  Navigate to your [COLOR="RoyalBlue"]/etc/X11/[/COLOR] folder and type [COLOR="Red"]sudo cp xorg.conf xorg.conf.nobamboo[/COLOR] (you can call the nobamboo part whatever you wish).  Don't worry about the options available on this page... you can play with those later...just add the basics to your xorg.conf to get the tablet working.

Note: I skipped section 5.2 because the bamboo doesn't come with a mouse.

Next, ensure you add the server layout info from section 5.3 <http://linuxwacom.sourceforge.net/index.php/howto/srvlayout>.

Your done!  For some people you can just restart X (ctrl alt backspace) to have a working tablet.  For me I had to reboot, then use wacdump to get the tablet to initialize.  See this page <http://linuxwacom.sourceforge.net/index.php/howto/wacdump>.  Also if I unplug it or go to suspend I have to reboot to reinitialize... apparently there is a daemon file somewhere that fixes this, but I have not investigated this yet.

Good Luck ... post your results and problems!

---

### Post by xingmu on 2007-11-07
Thanks for the post.  I just bought a Bamboo, so it's good to see a guide up.  But I'm still lost.  

I have the 2.6.20 kernel.  To make the driver, I HAD to configure with --enable-wacom.  Once I got the driver (wacom.ko), I tried insmod with it and nothing scary happened.  So I copied it to kernel driver directory.  I tried modprobe wacom on it and nothing interesting happened.  I rebooted and the tablet has no response.  I ran more /proc/bus/input/devices and under the WACOM device, there is "driver=(none)".  So what's going on?

---

### Post by cubeist on 2007-11-07
I am positive you don't need the enable-wacom option to build the .ko driver, nevertheless, it probably does no harm if you aren't using the wacom.o driver.

Anyway, just to make sure, it sounds like the compile and make went successfully, did you use the linux-wacom 0.7.8.3 package? and did you navigate to the correct directory of src/2.6.19?

If so, after you have inserted the module, if you type sudo xxd /dev/input/wacom do you get feedback from the tablet or is it completely dead?  If you get feedback from running xxd or wacdump, then the problem probably lies with your xorg.conf file...

---

### Post by xingmu on 2007-11-07
I got it figured out now!

I have a Bamboo One with device id 0069.  It's not actually supported by the latest driver (and it's not actually a Bamboo).  You need to add two lines of code in the wacom_wac.c file:

In the table of features, add:
{ "Wacom Bamboo One", 8, 5104, 3712, 511, 63, GRAPHIRE },

In the table of devices, add:
{ USB_DEVICE(USB_VENDOR_ID_WACOM, 0x69) }

Then recompile, install, and it works.

This information came from the discussion on the mailing lists:
[http://sourceforge.net/mailarchive/forum.php?thread_name=200710091817.33581.freqmod%40gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=200710091817.33581.freqmod%40gmail.com&forum_name=linuxwacom-discuss)

---

### Post by cubeist on 2007-11-07
The bamboo one? I have never heard of it which is strange because my dev id is the same 0069 and was recognized right away.  It's not even on the wacom site here in Canada... Glad you got it working!

---

### Post by xingmu on 2007-11-07
I think it might only be available in from Wacom (Europe) and Wacom (China).  But it seems strange to me that your device id is the same...

---

### Post by quinnten83 on 2007-11-18
Hi all, 
I'm somewhat of a noob when it comes to Ubuntu and linux in general.
I have wacom bamboo one which I can't get to work under GG.
The light on the tablet lits up, but and when I hover with the pen over it, it changes color, but nothing happens on screen.
I tried compiling the newest drivers to see of it would work.
But since I don't want to break anything I tried it running ubuntu from the live CD.
I installed the linux wacom tools and the Xorg.conf linux wacom tools thing...
and ran /.configure after extracting the files to the desktop. I get this error:

```
ubuntu@ubuntu:~/Desktop/linuxwacom-0.7.9-2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
ubuntu@ubuntu:~/Desktop/linuxwacom-0.7.9-2$ 

```

I tried checking the log, but as I imagined, I can' t make much sense of that.
do you guys and girls know if the error I am getting is because I am running from the live CD or am I doing something else wrong?

Edit: I just tried this on my laptop where Ubuntu is installed and i get the same error. Could anybody tell me what it is I am doing wrong?

---

### Post by xingmu on 2007-11-18
To be honest, I don't know exactly why you have that error.  I'm guessing it's a problem with either using the live CD (maybe there is a write problem).  So I would suggest not using the live CD.

Also, it looks like you're trying to use the development drivers.  You *can* do that, but you don't need to.  And it might be possible they still have bugs to be ironed out.  So I would advise using the latest release:

[http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.7.8-3.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.7.8-3.tar.bz2)

Next, you might need to install more packages for compiling the drivers.  I can't remember everything I had to install, but it seems you could try:

sudo aptitude install build-essentials xorg-dev tk-dev tcl-dev

Lastly, if you have "Bamboo One" you need to add two lines of code in the source files.  See my message above.  (Of course, it would be best to try and compile first WITHOUT the changes.  When that works, then make the changes and recompile.)

Good luck!

---

### Post by quinnten83 on 2007-11-25
I also get the error on my laptop, which is not running from the live CD.
Perhaps I do need a few mor dev kits, I will try to see if adding those dev kits will work.

---

### Post by narehart on 2007-11-28
can you please specify which patches to download, which files to patch and how to patch them?

also, some of your links go nowhere.

---

### Post by narehart on 2007-11-29
bump

---

### Post by alzeih on 2007-11-29
I believe the patch you want for the Bamboo Fun is [here]("http://sourceforge.net/tracker/index.php?func=detail&aid=1802837&group_id=69596&atid=525126")

---

### Post by narehart on 2007-11-29
i appreciate you finding that for me but i still don't know how to apply the patch and what to apply it to

---

### Post by quinnten83 on 2007-11-30
I've been looking around a lot and appearantly this is still not resolved for the new fun and 1.
many users don't get the same output as what is described on the instructions on the linux wacom project. if you are newb, like me, this completely confuses you.

I hope somebody comes up with an instruction for idiots.

---

### Post by narehart on 2007-11-30
Yeah, i really hope someone will post a easy to understand guide or else we'll have to wait until Ubuntu updates their linuxwacom drivers and who knows when that will be.

---

### Post by jazzcat on 2007-11-30
Ok, when I try to compile the driver after having installed all the dependencies, I get this:

```
Making all in 2.6.19
make[3]: Entering directory `/home/sam/bamboo/linuxwacom-0.7.9-3/src/2.6.19'
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.20-16-generic/build M=/home/sam/bamboo/linuxwacom-0.7.9-3/src/2.6.19
make[4]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 0 modules

```

Errrr how do I "enable as a module in my kernel config"?  In the 12 years I've been using Linux I've never heard of that, in the context of compiling a kernel module.  Why should this driver care whether or not it's enabled in the kernel config?

---

### Post by jazzcat on 2007-12-01
Ok, so when I gave the configure command the --enable-wacom parameter, I got the kernel modules.

Using a plain vanilla Bamboo (USB Product ID 0065) under Feisty Fawn on a Dell 1505N laptop; driver version is 0.7.9-3....

I got through the module compilation and installation, and that seemed to work just fine.  The lights light up.

However, I get no response whatsoever from the tablet.  Even with no X running, if I run wacdump and give it /dev/input/event7 (or whatever the event is that the tablet is currently attached to), I get no output whatsoever from the tablet.  Dmesg shows that it is recognized.

The tablet works fine under windows xp.

Ideas?  How do I debug this?  This isn't like the old days where you could run minicom on the affected serial port and see if stuff is coming back...

Thanks,
-J

---

### Post by narehart on 2007-12-03
> **jazzcat said:**
> Ok, when I try to compile the driver after having installed all the dependencies, I get this:

```
Making all in 2.6.19
make[3]: Entering directory `/home/sam/bamboo/linuxwacom-0.7.9-3/src/2.6.19'
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.20-16-generic/build M=/home/sam/bamboo/linuxwacom-0.7.9-3/src/2.6.19
make[4]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 0 modules

```

Errrr how do I "enable as a module in my kernel config"?  In the 12 years I've been using Linux I've never heard of that, in the context of compiling a kernel module.  Why should this driver care whether or not it's enabled in the kernel config?

how did you get past the "Drivers not enabled as modules in your kernel config but requested through configure are NOT built". Even with --enable-wacom i still get that message.

---

### Post by narehart on 2007-12-03
okay i think we have to rebuild the kernel with the new wacom drivers in place. take a look at this.

> This part is for those who want to manually build the wacom kernel driver in source tree. If you already followed the steps above, you can move on to next page.

Please backup wacom.c in your kernel tree first. Then copy wacom.c (or wacom_wac.c, wacom_wac.h, wacom_sys.c, and wacom.h if defined) from the related linuxwacom directory to the source tree (if 4 files were copies, you need to add wacom-objs := wacom_sys.o wacom_wac.o to the Makefile under your kernel source input directory) and rebuild the kernel. An example for kernel 2.6.9 is as following:

     	 
    	 [jej@ayukawa linuxwacom]$ cp /usr/src/linux/drivers/usb/input/wacom.c /usr/src/linux/drivers/usb/input/wacom.c.2.6.9 	 
    	 [jej@ayukawa linuxwacom]$ cp src/2.6.9/wacom.c /usr/src/linux/drivers/usb/input/ 	 
    	 [jej@ayukawa linuxwacom]$ cd /usr/src/linux 	 
    	 [jej@ayukawa linux]$ make 	 
    	 [jej@ayukawa linux]$ su 	 
    	 [jej@ayukawa linux]#make install 	 
    	 [jej@ayukawa linux]#make modules_install 	 
    	 [jej@ayukawa linux]#reboot

The problem is i am unsure what to do at this step as there is no INPUT directory under /usr/src/linux/drivers/usb in Gutsy.  Any ideas?

---

