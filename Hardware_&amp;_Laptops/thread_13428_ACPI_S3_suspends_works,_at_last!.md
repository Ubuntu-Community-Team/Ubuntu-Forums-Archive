---
title: "ACPI S3 suspends works, at last!"
date: 2005-01-31
forum: Hardware &amp; Laptops
---

### Post by tv123 on 2005-01-31
Hi folks,

I have recently purchased a Dothan centrino tablet pc, and have
quickly discovered that the good ol' "apm -s" no longer works
on newer laptops.

After wasting a good bit of time fixing DSDT tables etc, I finally
found out a way get ACPI S3 suspend (supending to RAM) to work
on my pc, thanks to Ubuntu's outstanding linux distribution!!
(My favorite full linux distros of all time: RH 6.1/6.2, Knoppix 3.3/3.4,
recent Kanotix, recent Ubuntu).

Here is the recipe that works for me:

1) Install a daily Ubuntu snapshot (mine is from 1/22/05, kernel: 2.6.10-2-386).

2) Add these lines to /etc/apt/sources.list so that you can access the source
and binaries for the "video_post" utility, written by some Intel chap:

#ACPI
deb [http://www.srcf.ucam.org/~mjg59/laptops/](http://www.srcf.ucam.org/~mjg59/laptops/) ./
deb-src [http://www.srcf.ucam.org/~mjg59/laptops/](http://www.srcf.ucam.org/~mjg59/laptops/) ./

2) Download video_post source to some folder, build it, and install it:

apt-get source --build video-post
dpkg -i video-post_0.1-1_i386.deb

3) comment out the line "" /sbin/shutdown -h now "Power button pressed" ""
in /etc/acpi/powerbtn.sh, as this this gets triggered when trying to
resume using the power button, and it starts the shutdown sequence then.

4) add options "noapic" and "nolapic" to the kernel line in the grub stanza
that boots this ubuntu install (not sure if these are really needed, but I had
read somewhere that this helps). Here is the kernel command line (change it to
suit your setup)

root=/dev/hda* ro quiet splash resume=/dev/hda* noapic nolapic

5) Reboot to make sure these options take effect.

6) create the script /sbin/ZZ:
#!/bin/sh
echo "mem" > /sys/power/state
# restart your kernel graphics module, if necessary
# modprobe i915 # my video card is Intel Extreme Graphics chipset
/usr/sbin/video_post

7) Do "chmod 775 /sbin/ZZ", and "sudo /sbin/ZZ". This should put your pc
to sleep, hopefully temporarily :)

8) To resume, do what ever it is that you do to resume from hibernation under
windows, such as "jogging" the power button. You should get a blank BACKLIT
screen (presumably due to the use of "video_post", which is meant for console
use, but without it, the screen never wakes up after resume).

9) Do "Ctrl-Alt-F1", which should take you to the first console screen. Then do
"Ctrl-Alt-F7", and that should bring you back to Gnome. Directly switching to
graphics screen fails for me.

10) FInally, if you suspend and close the lid, then reopening the lid
trigger the resume sequence, and in this it seems to go straight to
the graphics screen.

Good luck with the recipe, and please post your success or failure with
details so we can try and help you out.

Thanks,
Tom

---

### Post by knappen on 2005-01-31
Did you have any other problems running Ubuntu on your tablet pc?

---

### Post by tv123 on 2005-01-31
[QUOTE=knappen]Did you have any other problems running Ubuntu on your tablet pc?[/QUOTE]

Ubuntu (well, the particular snapshot I used at least) installed like a gem!
Not a single hickup during the install. Post install, I managed to get things to
work nicely after about a week or so.

Configuring the digitizer, pen etc is a snap using help available on the web,
except for rotating the screen, which I have barely managed to get working today.
Will tweak somemore.

Oh, BTW, I have an Acer C303XMi with a 14.1" screen, 1.7GHz Dothan, 1GB RAM,
80GB HDD. The machine is quite competent as a laptop. As a tablet, it offers
a large screen, but not so wide viewing angles (at least the US models), and
is quite heavy (6.2lbs).

Kudos and thanks to the Ubuntu team for an amazing distribution. I'll put in the
good word whereever I can.

Looking forward to the final Hoary release.

-Tom

ps: Oh BTW, the liveCD versions (both Ubuntu/Gnoppix), including the
latest one, did have some problems, such as not recognizing the
Synaptics touchpad automatically etc. Also, in the final hoary live CD, make
sure that there is a good HD installer included with it.

pps: there was a hitch or two with some programs (lyx, I think)
complaing about incompatible python version.

---

### Post by knappen on 2005-02-01
Thanks!!

---

### Post by stcoulon on 2005-03-02
Hello,

I followed your simple recipe, and I'm now able to have my Acer Aspire 2003 WLMI to resume from S3 suspend, well, almost correctly.

Until now, the laptop would go to suspend, but never resume. I tried a few configurations based on the "standard" acpi scripts, but no way. In fact it appears to me now that when they do not work, these scripts are too complicated and you don't know what to tweak inside them.

Your recipe is quite simple, although it appears that it doesn't apply exactely to my laptop.

What's different:
- apparently I do not need noapi nolapic option to the boot (will have to check that)
- I don't run on frame buffer, and unload both vesafb and fbcon if loaded
- I unload both my intel 2200 wlan and USB modules (others may require to be unloaded too, UBUNTU does load a great number of modules which are not used here, and some of theme could be problematic ???)
- the display obviously is the point. This is a radeon 9200 video. I had to both post the bios, and restore a known state using vbetool vbestate restore

Well, I said that the laptop is almost working correctly, because in fact, the post of the bios always gives me a floating point error (arghh). The display after restoring the vbestate looks a bit strange, there's some snow on it (similar to the current weather here in paris  :lol: ). The virtual terminal 12 I use to execute the suspend displays beautifull blinking semi graphic chars. But when I go back to gnome, graphic is ok. Going back to the first virtual console is also ok after that.

I tried vbetool post, video_post, boot-radeon I found on the web, same result: floating point error.

But that's already a great progress to have a working S3 suspend on this laptop !!!

---

### Post by jerome bettis on 2005-03-03
wow that actually worked ... well almost.  thanks for posting that.

the display finally came back which is **big**.  i had to recomplie the kernel with the i830 driver as a module (and i set the acpi video thing to built in .. maybe something else too i forget) and the display came right back after ctrl + alt + F7 .  

but then it just hung due to unhandled usb interupts, so had to unload / reload my usb modules and now everything works pretty good.

except :p

the touchpad updates the cursor about once per second, and the laptop keyboard gets stuck and lagged intermittently.  worse, the system just seems pretty unresponsive and slow at times.  any ideas?  i'm going to try unloading / reloading a few modules and such and see if that helps.

but this is great progress, thanks again!

oh yeah, the noapci nolapic kernel parameters were not necessary.  for my case at least.

---

### Post by jerome bettis on 2005-03-06
it works perfectly now .. i added some things to the script. 

```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# suspend to ram and come back

#save the console
CONSOLE=`fgconsole`
chvt 12
VBESTATE=`tempfile`
/usr/sbin/vbestate save >$VBESTATE;

# lock the powerbutton, so pressing it once starts the suspend,
# and pressing it again to come back doesn't start this script all
# over again.
LOCK_FILE=/var/lock/powerbtn.lock

get_lock () {
        dotlockfile -p -l -r 0 $LOCK_FILE
        [ $? -ne 0 ] && return 1
        return 0
}

release_lock () {
        [ $$ -eq `cat $LOCK_FILE` ] || exit 1
        dotlockfile -u $LOCK_FILE
}

trap "" 2 3 15
get_lock || exit 1

#stop the acpi daemon ... gross, but it's the easiest way
/etc/init.d/acpid stop >/dev/null 2>&1

# shut the backlight off
dpms off

#take down the network and unload the usb moduels
ifdown eth0
modprobe -r ehci_hcd
modprobe -r usbhid
modprobe -r uhci_hcd
modprobe -r ohci1394

# suspend to ram
echo "mem" > /sys/power/state

#reload the display module, mine is the intel i830
modprobe i830

# use that video post program and restore the state of the adapter
/usr/sbin/vm86_video_post
/usr/sbin/vbestate restore <$VBESTATE
rm $VBESTATE

# reload the usb modules, network, set the time
# and turn the backlight back on
modprobe ehci_hcd
modprobe usbhid
modprobe uhci_hcd
modprobe ohci1394
ifup eth0
hwclock --hctosys
/usr/sbin/dpms on

# go back to the console
chvt $CONSOLE;
#chvt 12;
#chvt $CONSOLE;

# Other half of the hideous hack
/etc/init.d/acpid start >/dev/null 2>&1

# done
release_lock
```

---

### Post by stcoulon on 2005-03-08
Hum, I didn't progress on this topic, cause in fact I discovered that my laptop appeared a bit unstable under hoary. I don't know the reason why.

I wanted to test an 'acpi=s3_late_bios" boot option in the kernel (found while googling), to see if I could get rid of the small display issues I had with suspend to ram. So I went to generate a custom kernel, including the required patch, and I entered into the problems.

From times to times, gcc (both 3.3 and 3.4 I tried) will simply core dump with segmentation fault on some modules. Re-starting the compile process will see the faulty module to compile, until some other fails later. Compiling a whole kernel was a pain, I had to restart the compilation a great number of time.

I tried a few tricks, throttling down the CPU, this appeared to be successful sometimes, and sometimes didn't change anything.

Also I realized that other programs while this situation had been reached, will pay the bill: example, while surfing with firefox while compiling the kernel, firefox will simply disappear.

I have recently installed a 512Mb So-DIMM pc3200 memory and I suspect that it has something to do with my problem. memtest86 didn't found anything.

Until I'm sure that there is no problem with the PC itself, including memory, I left Ubuntu (I continue to use it on my office laptop, inside vmware) and will stick to win xp (where I have some important apps, like tracktion for recording music using my firewire m-audio sound card). I got once a bsod , which unfortunately immediately rebooted the PC, but since a few days, nothing.

Wait and see.

---

### Post by rasnui on 2005-03-09
<I wanted to test an 'acpi=s3_late_bios" boot option in the kernel (found while googling)>

I guess you mean acpi_sleep=s3_bios. I have to use this option with my ibm thinkpad.

---

### Post by stcoulon on 2005-03-10
This one (s3_bios), as well as s3_mode, I tried with no success (system hangs, as far as I remember). I found some patch, specific for radeon systems (but may have been used with some success on other systems ???), see [s3_late_bios]("http://lambda.uta.edu/d600/")  which is a variant of s3_bios as far as I understood.

---

### Post by ming0 on 2005-03-12
I must say, I'm jealous and outraged (that S3 works for you and not for me) :) I tried the above ideas, and still didn't get much more progress than the stock howto  :| 

Maybe my panasonic R1 will never sleep...

Thanks for the ideas tho! Glad to hear that some people are having some luck w/ this, as it REALLY makes it worth having a laptop.

Once Linux gets S3 and S4 working well along with wireless network scanning and roaming, it will be ready for prime time as a mobile OS!

---

