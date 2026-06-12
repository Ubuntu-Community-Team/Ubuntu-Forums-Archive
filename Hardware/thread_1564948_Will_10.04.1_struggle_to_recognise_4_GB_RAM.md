---
title: "Will 10.04.1 struggle to recognise 4 GB RAM?"
date: 2010-08-31
forum: Hardware
---

### Post by Phosphoric on 2010-08-31
AS Windows does?

I'm building a new desktop as follows:

Gigabyte GA-MA770T-UD3P motherboard
Phenom II X2 550 CPU
OCZ StealthXStream 2 500W PSU
WD Caviar Green 500GB HD
Antec 300 Case

I'm finding it difficult to find compatible memory.  I was looking at 2x2 GB 1300 MHz DDR3 but I'm not sure that I need that much at this stage.

My computer use is pretty general, no gaming or overclocking.  The occasional DVD rendering...if I can find a decent Linux application.  (Currently dual booting in to Windows XP and using Ulead 12.

Thanks

---

### Post by ghostborg on 2010-08-31
No you will be using the AMD64 version.

Check out ManDVD and others.

Openshot Video editor

Handbrake encoder
I got mine from Stebbons ppa
[http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu]("http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu")

[https://launchpad.net/~stebbins/+archive/handbrake-snapshots]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots")

At the time there was not version of Handbrake for Lucid and I have not checked back.

---

### Post by Phosphoric on 2010-08-31
Thanks ghostborg.

Is it essential to use the 64 bit version?  I seem to recall various problems of the 64 bit over the 32.

Thanks

---

### Post by lykwydchykyn on 2010-08-31
If you need to use 32bit, use the -server or -pae kernel (they keep changing the name) and it will recognize all the RAM.

---

### Post by PRC09 on 2010-08-31
If you are using the 32bit and are connected to the internet during install it will automatically install the PAE kernel if there is more than 3gb of ram detected.....

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by oldfred on 2010-08-31
If you are working with DVD's and have 4GB of memory you will find the 64 bit version works better. 

I have run the 64 bit version since Karmic and cannot find any issues related. But I do not push system, primarily internet, email and occassionily other things.  If some web site does not work then I just do not want to go there, but in most cases I have found work arounds.

---

### Post by Cavsfan on 2010-08-31
I just did a fresh install with 10.04.1 2 days ago and I have a core 2 quad **64 bit** with **4GB RAM** and it runs flawlessly! :D
It shows I have 3.9GB in System Monitor. What is amazing is my monitor doesn't click anymore during bootup!
It used to click 2 or 3 times during a boot and I knew that wasn't good, but now it doesn't click even once.

---

### Post by cascade9 on 2010-09-02
> **oldfred said:**
> If you are working with DVD's and have 4GB of memory you will find the 64 bit version works better. 

Working with video, even with 2GB the 64bit version would be better. 

Go for at least DDR3 1333 (not 1300), and up to 1666 is useable in that system. If your having problems finding some RAM at decent prices, try staticice- 

[http://www.staticice.co.uk/](http://www.staticice.co.uk/)

BTW, unless you are really buuilding this down to a budget, try finding a GA-770T-USB3 (same motherboard as the GA-MA770T-UD3P but with USB3.0 suppport) orbetter yet a GA-870A-UD3 (updated version with the newer 870 northbridge and 850 southbridge, and SATAIII support).

---

### Post by Phosphoric on 2010-09-02
Thanks for all the advice folks.

I'll post back when I've built my new PC.

---

### Post by Phosphoric on 2010-09-18
OK, I've gone with the preceding advice and ordered a GA-870A-UD3, stretched my budget by £20!.

Back with a very basic question, slightly off topic.  The recommended motherboard has 2 x SATA 2 sockets and 6x SATA 3 sockets.  Can I plug a SATA 2 device in to a SATA 3 socket?  From my research so far it appears that the there is little or no difference between the SATA 1 2 & 3 cables.

Is there anything to be gained at this stage in only installing SATA 3 HDs and DVD writer?

Thanks.:)

Edit:  don't think you can get a SATA 3 optical drive!

---

### Post by Phosphoric on 2010-09-28
OK, new build all up and running with 10.4.1 amd64.  No problems at all after 3 days with any of my current applications.  4Gb RAM is recognised OK.  SATA3 HD and SATA1 Optical drive plugged in and recognised in to the SATA3 MB sockets.
More good news is that my old ATI X700 works quite well with Compiz fully utilsed straight out of the box.  I could never get it to run properly under 9.04.

Only problem is with the Gigabyte GA 870A-UD3 MB.  The Realtek chipset (ALC892) is not supported yet so very limited audio.  I've found some workarounds but they look very complicated and get broken with each Linux header update.  So I've gone for the simple but annoying remedy of fitting a separate sound card.

Also the BIOS for this MB does not appear to have the feature for unlocking my Phenom II X2 555 CPU.  I'm not in to heavy overclocking but unlocking  a couple of extra cores would have been very welcome.

---

### Post by mastablasta on 2010-09-28
> Realtek chipset (ALC892)
 
Have you tried to upgade Alsa? though you probably still won't get propper surround sound... :-/ so a separate card seems to be the solution (at least for now).

---

### Post by Phosphoric on 2010-09-28
Upgrading Alsa was the script that I was looking at.  However it's quite complicated (for me) and needs to be re-run at each upgrade of the Linux headers or whatever they are called.

I just need to wait until Ubuntu decide to do the upgrade through the official route.

Meantime, my add-on sound card works.

---

### Post by lykwydchykyn on 2010-09-28
> **Phosphoric said:**
> Upgrading Alsa was the script that I was looking at.  However it's quite complicated (for me) and needs to be re-run at each upgrade of the Linux headers or whatever they are called.

I just need to wait until Ubuntu decide to do the upgrade through the official route.

Meantime, my add-on sound card works.

I was able to get sound on my system working by just adding a repository and upgrading.  Repository is:
```


deb http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu lucid main

```

Then I installed linux-alsa-driver-modules.  I get regular alsa updates, it's painless.  Worth a try, maybe.

---

### Post by Cavsfan on 2010-09-28
**lykwydchykyn**'s solution should work great! And if it doesn't, here is a howto on making a script that runs when there is a 
kernel update or a new kernel is installed. The script is for installing nVidea video drivers, but the principle is the same for 
any script. Just sustitute your script for the one in the howto. I can verify that it works great. So, now you have 2 possibilities.

Edit: Forgot the thread [[COLOR=blue]_HOWTO run a script after kernel update._[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by Phosphoric on 2010-09-28
> **lykwydchykyn said:**
> I was able to get sound on my system working by just adding a repository and upgrading.  Repository is:
```


deb http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu lucid main

```

Then I installed linux-alsa-driver-modules.  I get regular alsa updates, it's painless.  Worth a try, maybe.

OK, I enable that rep and loads of linux-alsa-driver-modules are available.  Which one to choose?  I don't want to stuff up what I've got already.

Thanks

---

### Post by Cavsfan on 2010-09-28
> **Phosphoric said:**
> OK, I enable that rep and loads of linux-alsa-driver-modules are available.  Which one to choose?  I don't want to stuff up what I've got already.

Thanks

I don't think you can go wrong installing any or all of the updates.

In case you didn't get the key for the above repository, here's the command:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72B194E5
```

---

### Post by Phosphoric on 2010-09-28
> **Cavsfan said:**
> I don't think you can go wrong installing any or all of the updates.



I clicked on the latest Lucid generic module and got this message:

"This package contains modules supplied by Ubuntu for Linux 2.6.32-22-generic ALSA
snapshots from [http://kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.bz2](http://kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.bz2)

You likely do not want to install this package directly. Instead, install
the linux-alsa-driver-modules-lucid-generic meta-package, which will
ensure that upgrades work correctly and that supporting packages are
also installed."

I couldn't find this in the Synaptic Package Manager.

---

### Post by lykwydchykyn on 2010-09-28
> **Phosphoric said:**
> OK, I enable that rep and loads of linux-alsa-driver-modules are available.  Which one to choose?  I don't want to stuff up what I've got already.

Thanks

You need the one that matches your kernel version.  If you don't know that, you can just run this:
```

sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

Unfortunately it looks like there isn't a metapackage to just grab the latest one, so you may have to manually select the new package if your kernel gets upgraded.  I didn't notice that.

Kernel upgrades are relatively rare, though.

---

### Post by Cavsfan on 2010-09-28
> **Phosphoric said:**
> I clicked on the latest Lucid generic module and got this message:

"This package contains modules supplied by Ubuntu for Linux 2.6.32-22-generic ALSA
snapshots from [http://kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.bz2](http://kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.bz2)

You likely do not want to install this package directly. Instead, install
the linux-alsa-driver-modules-lucid-generic meta-package, which will
ensure that upgrades work correctly and that supporting packages are
also installed."

I couldn't find this in the Synaptic Package Manager.

I wouldn't touch that one as you probably have kernel 2.6.32-25-generic if you are up to date.
That PPA says this "This PPA will be used to provide [COLOR=Red]testing[/COLOR] versions of packages for supported Ubuntu releases."
[[COLOR=blue]_https://launchpad.net/~ubuntu-audio-dev/+archive/ppa_[/COLOR]]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa")

You might want to see if that script works and then incorporate it into the boot scripts.

---

### Post by Cavsfan on 2010-09-28
Or just open **System** > **Administration** > **System Monitor** and look on the System Tab.

---

### Post by Phosphoric on 2010-09-28
Thanks Cavsfan and lykwydchykyn.

Your very experienced advice is outside of my comfort zone, it effectively takes me back to the solution that I looked at before that involved running a script and re-running it if there was a kernel upgrade.

I'll bottle out of this as I have a working sound card any way.  I'll keep an eye out for when my Realtic chipset is supported conventionally.

Meantime, I'll mark this thread as solved as my original query was about 4 GB memory being recognised, which it is.

Thanks folks. :P

---

### Post by Cavsfan on 2010-09-28
I am using the Integrated sound same as you are.
Maybe you just need to install **pavucontrol** - PulseAudio Volume Control
It can be installed via **System** > **Administration** > **Synaptic Package Manager**.
Just enter **pavucontrol** in the quick search on the top.

---

### Post by Phosphoric on 2010-09-29
Installed Pulse volume control, but no different.  There are simply no more than the basic master volume control sliders for the on-board audio.

Then I noticed that I had lost sound in Realplayer. :(

Removed Pulse volume control and thank goodness I got sound back again.

I'll quit whilst I still have full audio control of my separate sound card.

I'll just wait until Ubuntu catches up with Realtek's latest chipsets. :)

Cheers Folks

---

