---
title: "NVIDIA Drivers"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by baucomboy on 2007-12-02
Ok guys, I know there's been a few other threads similar to this, but none seem to be quite the same or work for me. I've tried both the 32 and 64 bit versions of ubuntu. I have an asus g1s that i bought about a month ago which, in case you didn't know, uses a 8600m 256 video card. The 32 bit ubuntu works great using the vesa (?) drivers, but i want to use the nvidia drivers for 3d. I install them, ive tried using both the restricted files menu and envy, but when i restart, they seem to be only partially working because i get a menu about how it could net detect my screen and card, so i'll have to configure them manually - ive tried everything in this menu. Some will let me boot, but only at 800x600, or just give me the rainbow of collors screen, or some just hang. When i tried to install the 64 bit, i didn't have to use the safe graphics mode, but it still went to a huge resolution and gave me the same message about how i'll have to configure manually. Ive tried editing my xorg.conf file. It already says 24 depth, at least after using envy. 
I'm also open to suggestions as far as using the 32 or 64 bit...64 seems to take a bit longer to boot...I want to start from scratch, so in your response, please take it from the point of a fresh install (id love your opinion of which to install too)
Thank you SO much for your future responses, Im starting to like ubuntu more and more, but this really is a deal breaker for me.

---

### Post by baucomboy on 2007-12-03
Okay, so Ive invested like 10 hours into just getting the stupid video drivers working...still to no avail. I know there are people out there that have gotten the video working on this thing. One of the reasons I bought this particular model was because of it's great functionality with linux...at least that is what everyone said...and true, everything else seems to be great...except the graphics...but that is a BIG exception...I want to make ubuntu my primary OS, but if it can't run simple 3d or even a dvd at full screen without running jittery, then I will have to stick with vista...

---

### Post by Officer Dibble on 2007-12-03
This is coming from many years experience in computing... never, ever, solely rely on onboard  video. Always treat onboard video as something to get you going or to allow you to test your system as you are building it.... that's all onboard video is good for in desktop PC's. Laptops are a little trickier as you have little choice.

So, my suggestion would be to go out and buy a video card... an Nvidia video card. :)

---

### Post by lswest on 2007-12-03
i had a similar issue with my Nvidia MCP67M driver, but i got it working after installing the driver, and then installing the nvidia control panel.  Also, what you could do is (after backing up your xorg.conf) manually edit it so that only one display resolution is there (e.g. 1280 x 800) and then, effectively, it forces ubuntu to use that resolution (at least, it worked for me).  hope it helps.  best bet might be the control panel though...not exactly sure of the package name (in windows atm).

---

### Post by baucomboy on 2007-12-03
I have tried editing the xorg.conf file, resolution, changing the driver name, the depth, etc. to no avail. I have not, however, tried the control panel. I'll do a fresh install, check synaptic for the package, and give it a try on my lunch break and report back. Thanks for the idea!

---

### Post by baucomboy on 2007-12-03
Too bad. I had high hopes for that idea. It didn't work. Any other suggestion? I did a fresh install, updated all the files, then activated the restricted driver, restarted and everything was all big and a dialogue box said i had to configure my graphix card and monitor, but nomatter what i do it continues on at 800x600 using some generic drivers. I did however run gksudo nvidia-settings, but there were no useful setting there like i had hoped. I can try to use the screens and graphics menu, but all it does is say that i have to log out for setting to take affect, so i do, and all the colors are all screwy. so i restart, and im back to square one! I am really frustrated - I saw some videos on youtube about confiz fusion and it looks wicked! I really would like to get the dumb 3d working.

---

### Post by lswest on 2007-12-04
hmm, i'm fresh out of ideas...i'm switching OSes atm though, so if i think of something ill edit this post.  last idea from me for the moment would be try the nvidia-driver-new package (i think that's what its called) or, worst comes to worst, manually install the package that you need.

---

### Post by scizmeli on 2007-12-04
Pls see my recent post at [http://ubuntuforums.org/showthread.php?p=3892793#post3892793](http://ubuntuforums.org/showthread.php?p=3892793#post3892793)

---

### Post by baucomboy on 2007-12-05
Well, i tried the command...still no go. Plus I donwloaded openSUSE just to give a try, but still nothing, literally, just a black screen when I try to boot after the install. I might give knoppix a try to, but I do really like ubuntu - I just wish it would work! Every site that i read says they got ubuntu working no problem on this Lappy......am I missing something?!?!?!?

---

### Post by MadMalcolm on 2007-12-05
I think I have the same problem. Tried with Ubuntu x86 and x86_64. Graphics were running fine as long as I had 2GB or memory in my G1S but after upgrading to 4GB neither the nv or the nvidia driver is working. I can run the gdm using the vesa driver though.

To get this running I had to blacklist the nv driver:

```

sudo nano /etc/default/linux-restricted-modules-common

```

and make sure you have this line in there:

```

DISABLED_MODULES="nv nvidia_new"

```

And then use the vesa driver for your card. You can try the attached xorg.conf ... but you should now be able to set things up as low-resolution mode.

Somebody seems to have solved this issue over at the [nvidia forums]("http://www.nvnews.net/vbulletin/showthread.php?t=93293") by changing the PREFETCH window for his PCIe bus ... I am trying to figure out what I have to do to get this to work. I'll try to update later.

---

### Post by MadMalcolm on 2007-12-05
So it turns out that the /etc/modprobe.d/lrm-video forced modprobe to use /sbin/lrm-video  to insert the nvidia module into the kernel. If you (like me) compiled your own version of the nvidia driver inserting the nvidia driver will fail like this:

```

modprobe nvidia
sh: /sbin/lrm-video: not found
FATAL: Error running install command for nvidia

```

You can fix that by commenting out the relevant sections of your /etc/modprobe.d/lrm-video:

```

# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
#install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
#install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS

```

I'm told that it's an ugly workaround, but hey, At least that gets the driver in there. Hold on to your knickers though, The driver itself still writes to the wrong memory buffer, so this does si give you a really funky looking login screen when you run

```

sudo nvidia-xconfig

```

and then restart X. If you go ahead an reverse the changes, ie. head to a console (press ctrl-alt-f1) and do

```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart

```

Your login manager will crash because the nvidia driver wrote data into an illegal memory range, cuaseing part of your former (nvidia enabled) X-session to still be displayed. Reboot and all will be forgotten ...

I attached my Xorg log and the nvidia bug report i generated (and submitted to nvidia). Any help? Does anyone know if setting the PREFETCH window sounds like a solution and optimally direct me toward some resources that would tell me how to go about it?

---

### Post by baucomboy on 2007-12-09
i stumbled across this thread...maybe this will help us...personally, i'm a linux noob...so maybe you can dumb down the steps for me?

[http://ubuntuforums.org/showthread.php?p=3904760](http://ubuntuforums.org/showthread.php?p=3904760)

---

### Post by MadMalcolm on 2007-12-10
Right on. I think I will go though this tonight. [Here]("http://ubuntuforums.org/showthread.php?t=311158") are some really good instructions on how to build your kernel. Just use the kernel patch from the link you posted and we should be good.

---

### Post by MadMalcolm on 2007-12-11
Graphics are running like a charm now. I did run into a problem with wireless and sound though, but it seems that seems to be a common problem with compiling the kernel (if you're a newb anyway). I will post the steps I went though to get it all running :)

---

### Post by baucomboy on 2007-12-11
You, sir, are a god among men ;) Steps would be awesome...i've only been working successfully on ubuntu for about a week now, so newb is an understatement, lol. Glad to hear your up and running. Makes you wonder why this hasn't already been incorporated into the kernel...I yoinked a 2g stick out of my lappy just to play with compiz...it's working...beautifully - i love linux! lol I'll be glad to put that stick back in tho.

---

### Post by MadMalcolm on 2007-12-17
Finally got everything working. It's really not so bad, I've just been busy ... currently sitting in a conference in Montreal :D

Since wireless did not work for me in the new kernel i suggest you get the necessary files for this before you get going. They are available from [intel]("http://www.intellinuxwireless.org/?p=iwlwifi"):

```

wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.17.tgz
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.2.22.tgz

```

Once you have those let's get going on the kernel. Follow the instructions in the [master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158") to obtain and patch the 2.6.23 kernel. For step 6 I used the 2.6.23.9 patch, but I don't see why the most recent patch should not work.

```

wget http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.23.9.bz2

```

After patching the kernel also do this:

```

sudo gedit /usr/src/linux-2.6.23/arch/i386/pci/i386.c

```

Find the pcibios_allocate_bus_resources function. You will need to add these lines:
```

				if ((r->start == 0xbdf00000) && (r->end == 0xddefffff)) {
					r->start = 0xc0000000;
					r->end = 0xd0000000;
				}

```

Right after the section that looks like a so:

```

	/* Depth-First Search on bus tree */
	list_for_each_entry(bus, bus_list, node) {
		if ((dev = bus->self)) {
			for (idx = PCI_BRIDGE_RESOURCES;
			    idx < PCI_NUM_RESOURCES; idx++) {
				r = &dev->resource[idx];
				if (!r->flags)
					continue;

```

And before this:

```

				pr = pci_find_parent_resource(dev, r);
				if (!r->start || !pr ||
				    request_resource(pr, r) < 0) {
					printk(KERN_ERR "PCI: Cannot allocate "
						"resource region %d "
						"of bridge %s\n",
						idx, pci_name(dev));
					/*
					 * Something is wrong with the region.
					 * Invalidate the resource to prevent
					 * child resource allocations in this
					 * range.
					 */
					r->flags = 0;
				}
			}
		}
		pcibios_allocate_bus_resources(&bus->children);
	}

```

Now you need to configure for building the kernel. Again follow along with the master kernel thread. When you are looking at your make xconfig you may want to check the "Intel HD Audio" option under Device Drivers->Sound->Advanced Linux Sound Architecture->PCI Devices (that way your sound should just work ... I forgot the option and had to recompile ALSA afterwards).

Also under "Processor type and features" You may want to use the "Intel Core2 / newer Xeon" option.

All right follow the rest of the instructions of the master kernel thread to build your new kernel. Boot into int, and hope your wireless works. If ti does not you will need the drivers I had you download above. First get the firmware going (assuming you are in the directory to which you downloaded your drivers):

```

tar xvf iwlwifi-4965-ucode-4.44.17.tgz
sudo cp iwlwifi-4965-ucode-4.44.17/iwlwifi-4965.ucode /lib/firmware/iwlwifi-4965-1.ucode

```

And then build the driver:

```

tar xvf iwlwifi-1.2.22.tgz
cd iwlwifi-1.2.22 
make
sudo make install
sudo modprobe iwl4965

```

Reboot and your wireless should be working.

Well now try building the nvidia drivers. Have a look at the instructions [here]("http://www.nvnews.net/vbulletin/showthread.php?t=72490"). You have the linux headers (hell you just built your kernel :) ) Do make sure that nvidia-glx has been removed and that /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel and /lib/linux-restricted-modules/.nvidia_new_installed do not exist. Edit your /etc/default/linux-restricted-modules-common

```

sudo gedit /etc/default/linux-restricted-modules-common

```

And make sure you have the line:

```

DISABLED_MODULES="nv nvidia_new"

```

Get the NVIDIA driver packadge:

```

wget ftp://download.nvidia.com/XFree86/Linux-x86_64/100.14.19/NVIDIA-Linux-x86_64-100.14.19-pkg1.run

```

Go into a console (ctrl-alt-f1will do) and kill your X session:

```

sudo /etc/init.d/gdm stop

```

And build the nvidia drivers:

```

sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg1.run

```

Just floow though the prompts and let it configure your xorg at the end. Make sure you can modprobe the nvidia kernel object my editing your /etc/modprobe.d/lrm-video as I mentioned before:

```

# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
#install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
#install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS

```

OK, restart X:

```

sudo /etc/init.d/gdm start

```

And you should be running with nvidia graphics! Now you can get compiz and it's spiffyness going, mind you the regular ubuntu tools will not work, since they want to unstlal the generic nvida kernel modules. su just open a terminal and do:

```

nohup compiz --replace

```

If it all works you will probably wna tot add that to your System->Sessions Statup Programs.

In case your sound does not work, I got the it working my getting the realteck ALSA drivers:

```

wget ftp://202.65.194.211/pc/audio/realtek-linux-audiopack-4.07a.tar.bz2
tar jxvf realtek-linux-audiopack-4.07a.tar.bz2
cd realtek-linux-audiopack-4.07a
sudo ./install

```

*Note*: A more solid [kernel patch]("https://bugzilla.redhat.com/show_bug.cgi?id=425794") for this issue is in the works. I will try this one out over a nice spiked mug of nog when I get home for Christmas :guitar:

---

