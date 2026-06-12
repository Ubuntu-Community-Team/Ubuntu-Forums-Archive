---
title: "Sleep and hibernate on HP Pavilion dv9000"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by jogu on 2007-03-26
Is there anyone who's got a HP Pavilion dv9074 (or another laptop on the dv9000 series) where sleep/suspend to RAM and hibernate/suspend to disk works well?

Hibernates works OK for me -- almost, I've some minor problems with the wireless.
Sleep doesn't work at all -- the machine goes to sleep, but don't wake up well, the screen is just blank and the keyboard is not working (for example caps lock)
I'm running Feisty beta, and had the same problem in Edgy and when I've tested Dapper. 
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9074ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9074ea)

If it works for you, have you done anything special (as opposed to the automatic installation using a Live-CD)
For example in /ect/default/acpi-support. 
Boot options.

---

### Post by shute on 2007-03-28
I have exactly the same problem. Mine: HP nx8220

---

### Post by pjotre on 2007-03-30
surprisingly suspend2ram worked for me with Feisty... I have a nx6310. 

The problem is: it workED... Like eight times or something, I did a perfect recovery. After that, Gnome showed me a message, something like "problem with suspend", since that my keyboard won't work after resuming...

Any ideas?

It did work with s2ram -f using Opensuse10.2. I just don't like suse so I  switched back to Ubuntu, eventhough suse is supposed to have a better notebook-support.

---

### Post by huzzak on 2007-03-30
My laptop is a Pavilion dv5237cl.  I'm running Edgy Eft and when I come back from hibernate the wireless simply stops working.  The little light indicator doesn't even turn on to show that it recognizes it.

---

### Post by jogu on 2007-03-31
It seems like there's problems with the sleep and hibernate when one use the free nv-driver. If one installs the non-free nvidia-glx driver then it works better, at least sleep...

I got this info from a testing report of another laptop in the dv9000 series:
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9297ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9297ea)

---

### Post by Blue Label on 2007-04-16
> **jogu said:**
> Is there anyone who's got a HP Pavilion dv9074 (or another laptop on the dv9000 series) where sleep/suspend to RAM and hibernate/suspend to disk works well?

Hibernates works OK for me -- almost, I've some minor problems with the wireless.
Sleep doesn't work at all -- the machine goes to sleep, but don't wake up well, the screen is just blank and the keyboard is not working (for example caps lock)
I'm running Feisty beta, and had the same problem in Edgy and when I've tested Dapper. 
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9074ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9074ea)

If it works for you, have you done anything special (as opposed to the automatic installation using a Live-CD)
For example in /ect/default/acpi-support. 
Boot options.

Experiencing very same problem.  Mine: Pavilion dv9207us

---

### Post by FrancoNero on 2007-04-19
hp compaq nx7400
no keyboard and touchpad on return from suspend

---

### Post by jak140 on 2007-04-19
I have a dv9000t and have the opposite problem, suspend works, but hibernate locks the computer up

---

### Post by bhaverkamp on 2007-04-25
My dv9000t will not suspend anymore since upgrade to feisty. Worked great in Edgy.

I thought this was a generic feisty issue but my toshiba works just great. It's only issue is sound.

---

### Post by fxckkonka on 2007-04-25
Any idea to this??

My laptop is dell D410, and it has the same problem.

---

### Post by FrancoNero on 2007-04-25
yeah that hibernate/suspend problem on HPs is a major annoyance....

---

### Post by inchaos on 2007-04-25
Yeah, I have a similar problem on a dv5000, with sleep or hibernate, my computer just wakes up to a blank screen with no keyboard functionality.  
Lame!

---

### Post by strabes on 2007-04-25
If you have an ATI card look at the fix on this page: [http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)

---

### Post by jak140 on 2007-04-25
Could those of you with working hibernate post your grub boot options and ACPI-support files? Suspend works for me and these are my current settings (I have a dv9000t):

grub boot options:

# defoptions=pci=bios idle=halt acpi_sleep=s3_bios vga=normal quiet splash resume=UUID=1dcd542e-2ebe-4fca-886f-3599e0fa3ce9

ACPI_Support:

```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions? true is default
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most. 
# default is commented out
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true
```

---

### Post by FrancoNero on 2007-04-26
well i'd have to look for options that would explain why i dont have any input devices upon return from suspend, right? i don't see any. ideas?

---

### Post by 3rods on 2007-05-12
Anybody find anything on this or are we all hibernate-less still?

My 9000t won't even get bact to the grub menu if i try to standby/hibernate.  Is this normal? I dual boot vista64/ubuntu and I'm guessing I should see the grub menu even if I hibernate it.

---

### Post by jogu on 2007-05-12
No solution for me. 

Current status on my dv9074ea (running the ubuntu i386 version): 
[LIST]
[*]Hibernate: the kernel panics if I try to hibernate -- workaround: boot option 'nosmp' (no symmetric multiprocessing in the dual core processor :-/ )
[*]Sleep: with the additional boot option 'nosmp' the machine goes to sleep, the sleep light comes on, it wakes up on a key press, but the screen is just blank and the keyboard is not working (for example caps lock)
[/LIST]
I also boot with option 'noapic', otherwise the booting stalls. 

This post gave me hope: 
[http://ubuntuforums.org/showpost.php?p=2582225&postcount=19](http://ubuntuforums.org/showpost.php?p=2582225&postcount=19)
But I haven't got s2ram work either, even trying the workarounds described on
[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)

---

### Post by 3rods on 2007-05-12
I'm not using the noapic option; does it eventually boot or does it fail completely? Mine gets about 40% and halts for about a whole minute then it jumps to 100% and loads the login manager.

---

### Post by jogu on 2007-05-13
It fails 99% of the times. 
I've played around with with BIOS versions, 32 bits and 64 bits ubuntu, live CD and alternate CD etc ,and none of the installation has been stable out-of-the-box. 

I'm not suprized that our laptops don't behave the same. The siblings in dv9000 series aren't exactly the same under the hood.

---

### Post by Paulo79 on 2007-05-17
Has anyone of you tried a suspend2 patched kernel?

My dv9000t has two hard-drives set in a raid0 configuration. I wonder if that makes it harder to get suspend / hibernate to work...

---

### Post by FrancoNero on 2007-05-22
I really wish there would be an official ubuntu patch to address laptop issues like this. i can see past the fact that fonts and stuff look fugly in feisty, but i cant use ubuntu on my laptop unless sleep and hibernate work at least ast good as under  windumb

---

### Post by 3rods on 2007-05-22
I would be willing to pay $50 USD via paypal** to the first person** who can fix (or supply me with instructions on how to fix) the hibernate issue with my dv9000t. Suspend, I can live without, but I am totally serious about this. 

Fixed = can hibernate and revive at least 3 times in a row without messing up. After hibernation everything must work with little or no effort (i.e. if wlan does not work, but issuing command fixes, that's ok), but if the keyboard or mouse goes crazy after a revive, that doesn't mean "fixed".

My DV9000t is an intel C2D 2.0Ghz with 2GB RAM, the GO 7600 w/512RAM and two 7600rpm HD. I am dual booting with vista 64 and use grub as a boot loader. I am using the restricted nVidia driver and using beryl. I can live without beryl (and driver) if it means I can hibernate. 

Contact me at ubuntu at 3rods dot com if you are interested in the $50 USD and have a solution. Solution first, cash after - sorry. 

I will also donate the $50 to the (ubuntu) community if so desired. If anyone else is wiling to pile in on this; please post here. Maybe adding some $$$ to the pot could speed things along a little.

---

### Post by FrancoNero on 2007-05-23
is all that in launchpad yet? i mean are there bugreports filed already? maybe it'll help to vote those bug reports up

---

### Post by 3rods on 2007-05-23
Still willing to throw cash at it at this point, since I don't require the know how or time to learn how to fix it on my own. 

I'll check out the bug reports, but, from what I hear, HP's are famous, no, notorius for having these sorts of issues with *nix OSes and S1/S3 sorts of operations.

---

### Post by FrancoNero on 2007-05-23
well I don't see a reason why anyone would ship an OS that doesn't get the most basic things done.... I would throw cash at the problem if I had cash. right now, i just hope this problem gets recognized by the devs and a fix is out soon

---

### Post by 3rods on 2007-05-26
I guess because it's a "free" OS, of sorts. This is the main downfall of "free" software.

---

### Post by FrancoNero on 2007-05-26
I can't believe there aren't enough Ubuntu devs with HP laptops. guess i just bit the sour apple and bought the wrong hardware

---

### Post by 3rods on 2007-05-26
Are you using 6.10 on your dv9000? 7.04 works a lot better FYI.

---

### Post by FrancoNero on 2007-05-28
using the very latest ubuntu feisty. i am currently downloading kernel etc updates that just popped up in software updates. my hopes for improvement are rather low though

---

### Post by 3rods on 2007-05-28
I found this:

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/") 

And someone emailed me, but their suggestion doesn't seem to work for me. Probably because I have the dual hard drive setup. My boot is /dev/sdb for ubuntu not sda, so that might mess it up too. 

Kernel updates do nothing; I'm sure you know by now. :(

---

### Post by kingkookie on 2007-05-28
Same problem here too.  HP Pavilion ze4500.  The system suspends, but when powering back up, the screen stays blank.  Not even the backlight comes on.  Hibernate works sometimes, but more often that not, it fails.  I also tried the newest kernel download.  That apparently didn't address the suspend issues.

---

### Post by brk3 on 2007-05-28
got a hp dv8000 and neither hibernate or suspend works at all. so annoying :(

---

### Post by FrancoNero on 2007-05-28
when i go to hibernate, as i said before, i get a screen with loooots of text, which seems mostly USB related, though. i'll try to take a picture

---

### Post by 3rods on 2007-05-28
Can't you just get the same info from the log files? Be easier than trying to take a picture of a computer screen.

---

### Post by FrancoNero on 2007-05-28
hm... I'll look into that....

---

### Post by mikeytag on 2007-05-30
I found this thread through Google. I am the proud owner of a new dv9000 series laptop and am absolutely in love with it. I have great news for everybody reading this thread. I have gotten suspend and hibernate to work correctly. I am using Feisty btw.

All you need to do is:

```
sudo pico /etc/modprobe.d/options
```

and in that file add the following line:

```
options nvidia NVreg_SoftEDIDs=0
```

After you add that line, make sure your Feisty setup is exactly the way it comes installed by default. Meaning remove any other suspend related packages you may have installed to try to get it to work. In my case I removed the hibernate package.

Once you have removed the excess packages simply reboot and then you will have the ability to suspend and hibernate. Both work well for me and I haven't had a problem yet. I hope this helps someone out there.

---

### Post by FrancoNero on 2007-05-30
well i dont even have an nvidia adapter, and i have a nx7400.....
:-(

---

### Post by Paulo79 on 2007-05-30
Thanks for the hint, Mikeytag. I will try it here later today. 

Besides installing the hibernate, did you try installing any other package that might have changed other configuration files? I mean, were you able to reproduce your fix/suggestion by getting suspend/hibernate to work after a fresh install of Feisty?

EDIT: could you please post your hardware specifications? The HP Pavilion dv9000 is actually a family of laptop computers with different configurations. Mine, for instance, is a dv9000t CTO. I guess CTO means customized and the "t" means it has an Intel processor (as opposed to 9000z for the laptops with AMD processors). Please let us know what BIOS version you have (I recently updated mine to F.16). Finally, how much memory do you have and what is the size of your swap partition? 

Thanks again!

---

### Post by 3rods on 2007-05-30
Hmm... No love for me. I got the dual HD's though, so maybe that has something to do with it. I uninstalled beryl and removed the restricted driver, even tried the previous kernel. No dice. 

mine is the dv9000t C2D 2.0ghz dual sata HD's 2GB ram and nvidia go 512mb. 

Thanks for the help though, maybe it will work for someone else.

---

### Post by Paulo79 on 2007-05-31
Hey 3rods,

Notice that, in the hint made by mikeytag,  the line you add is "options nvidia NVreg_SoftEDIDs=0". That is an option to the **restricted** nvidia driver. I read somewhere that you **have** to use it in order to be able to suspend/hibernate. It seems that the open source "nv" driver won't do the job.

---

### Post by Paulo79 on 2007-05-31
Hey 3rods,

I just installed feisty for the first time. I'm not using the nvidia restricted driver, just the open source 'nv' (no 3D acceleration). I found out that hibernate works out-of-the-box for me, while suspend to ram actually suspends but doesn't resume.

Using the restricted driver, suspend works but it seems the network connection is down after resuming. Have to check that... Hibernate hangs and the computer doesn't turn off.

I tried the hibernate script and it complains that the nvidia module is failing to unload. I've also tried the latest nvidia BETA driver from nvidia.com and no difference (although the change log claims there are notebook capability improvements).

Well, let's keep trying. I feel it is a lot better than it was with Edgy and soon it will propably just work out-of-the-box. Patience is a virtue!

EDIT: I've also tried the suspend2-patched kernel and I didn't work. The problem is the same: the system hangs during hibernate and won't power off. Hope nvidia will release an update that works with the dv9000. Or HP could release a BIOS update to address this problem.

---

### Post by Paulo79 on 2007-06-06
Looks like people have quit trying. But here's some news about my latest achievement: hibernate works (but not always yet). To summarize:

I'm using nvidia's restricted driver (nvidia-glx-new). Suspend to ram works for me out-of-the-box with my HP dv9000t. Hibernate, however, would not poweroff my computer (it would hang with a dark screen, all LEDs on). My laptop has a PCI-Express video card. So I guessed I don't need AGP and added the following two lines to /etc/modprobe.d/blacklist:

blacklist intel_agp
blacklist agpgart

Also, in the device section of my xorg.conf, I added:

Option "NvAGP" "0"

Please, follow these steps, try hibernating, and let me know how it work for you guys.

If it still doesn't work, here is the WEIRD part: keep the settings above and run glxgears on a xterm for about 15 seconds, just after logging in and just before trying to hibernate. I guess this may initialize some junk in the nvidia module. After doing this, my system powers off after I click on hibernate. Sometimes it reboots instead of powering off. I'm going to try uswsusp now and see if there is any difference.

This thing with glxgears affecting hibernate makes me wonder if those people reporting working hibernate are also beryl/compiz users. Hum...

---

### Post by explemonk on 2007-06-14
> **Paulo79 said:**
> If it still doesn't work, here is the WEIRD part: keep the settings above and run glxgears on a xterm for about 15 seconds, just after logging in and just before trying to hibernate. I guess this may initialize some junk in the nvidia module. After doing this, my system powers off after I click on hibernate. Sometimes it reboots instead of powering off. I'm going to try uswsusp now and see if there is any difference.

This thing with glxgears affecting hibernate makes me wonder if those people reporting working hibernate are also beryl/compiz users. Hum...

I am using Beryl and with the solution mikeytag posted both suspend and hibernate work for me, but only if I disable Beryl first.  This is on a dv9207us (Intel processor).

Edit: forgot to mention that I am also using the nvidia-glx-new driver.

---

### Post by jogu on 2007-07-12
> **Paulo79 said:**
> 
Please, follow these steps, try hibernating, and let me know how it work for you guys.

If it still doesn't work, here is the WEIRD part: keep the settings above and run glxgears on a xterm for about 15 seconds, just after logging in and just before trying to hibernate. 


I can confirm this behaviour in Ubuntu 7.04 (i.e. Gnome) on my dv9074ea using nvidia-glx as installed by the restricted driver manager, but no 'desktop effects' or Beryl running. (I don't need boot with the 'noapic' option as I have to do if I use the free nv-driver)

Weird indeed...

More hardware info on [https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9074ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9074ea)

---

### Post by aldeby on 2007-09-11
I had this experiece with gutsy gibbon (tribe6) and HP laptop:

**Problem:** Black screen when resuming from suspends

However /etc/acpi/prepare.sh file has no issues

**Cause:** **compiz! **(to figure out do a simple test: disable compiz before entering standby and you should be perfectly able to resume)

**Solution:** install via apt-get [B]CompizConfig
[/B]then in **General Options** go to **Display Settings **and disable **Sync to VBlank**


If problem persists also try changing some values in /etc/default/acpi-support

most notable change should be changing POST_VIDEO=true to POST_VIDEO=false

hope it helps,
cheers :)

---

### Post by ATrentino on 2007-09-14
I have a dv9408nr, with AMD Turion 64x2 TL-56, nVidia GeForce 6150, 1GB of RAM and 2 GB of swap. When I return from suspend, everything seems fine but though I seem to be able to connect to my network with the ethernet plug, my computer doesn't receive anything. Does anyone know how to even start finding out why this is? Thanks.

---

### Post by stracso on 2008-06-13
Hi,

I have a dv9000 with the nvidia Go 700 videocard. After reading thru all the forum replies, I managed to get the sleep mode working:

The only thing that worked was changing the POST_VIDEO to false in my /etc/default/acpi-support  file, by default it was true. 

After that, sleep mode works by pressing the laptop's sleep key or by clicking on suspend from the GDM. 

Forgot to mention: I am using ubuntu 8.04 LTS with the restricted nvidia driver. I have kernel 2.6.24-18-generic

cheers.

---

