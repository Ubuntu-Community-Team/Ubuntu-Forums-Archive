---
title: "[SOLVED] Kernel Fix for Sound crackling on recent Nvidia HDA chipset"
date: 2008-09-29
forum: General Help
---

### Post by Zaff on 2008-09-29
Hi everyone, 
So according to this post my sound problem is a common issue amount owners of a motherboard equipped with a recent Nvidia HDA chipset.
The crackling is unbearable and I can't even listen to music anymore. It's not a Pulseaudio issue or an alsa issue and I even tried installing OSS4 and that turned out to be a complete failure.
So I know there is a solution :  [http://lkml.org/lkml/2008/8/4/110](http://lkml.org/lkml/2008/8/4/110)
It's a kernel fix but I don't know how to apply it. It would be sad to have to buy a sound card if I can fix this for free.
So can anyone help me with this ? I didn't find a tutorial on how to apply kernel patches and I'm kind of a n00b in that regard so I'd need some pretty precise information.
Thanks to anyone who'll help.

---

### Post by Zaff on 2008-09-30
I really need help on this please !

---

### Post by hoofdletterb on 2008-09-30
I can't help you out but the problem also occurs on the asus m3n78-emh hdmi mobo. I guess we should just wait for updates.

---

### Post by rudy.elgato on 2008-09-30
ughhhh...  I wasted over a week, going through the forums, googling, trying a couple dozen different fixes, trying to clear up the awful, hissing noises that were coming out of my nvidia hda chipset and nothing I tried worked.  I finally went out and bought an inexpensive sound card, plugged it in, and a minute later was enjoying some nice clear audio.

so... My recommendation would be to save yourself the frustration of trying to get that nvidia hda chipset to work, and buy a cheap sound card.

good luck...

---

### Post by Zaff on 2008-10-01
okay first of all, a fix is out in the next kernel (in Intrepid) which is next month. So I'm not buying a cheap sound card for a month of music.
Second of all there is a solution, I just need to find someone who'll explain how to patch the kernel. I know it's been done before, and it can't be that hard so why isn't there anyone around to explain how to do that ?

---

### Post by rudy.elgato on 2008-10-01
Right...  Be sure post an end note to this thread when you get the information you're looking for and your fix is in place. 

Lotsa luck...

---

### Post by Zaff on 2008-10-03
Edit : if you don't want to recommpile the kernel, try the linuxant drivers : [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

It works !
So for all of you here, who are having problems with that crackling sound and don't want to wait a month for intrepid to come out, here's our to do it.
It's fairly simple really and not as dangerous as it sounds. I used this [guide]("https://help.ubuntu.com/community/Kernel/Compile") to help me : 
First thing you wanna do is backup your grub menu:
```
sudo cp /boot/grub/menu.lst ~/menu.lst.bak
```
This to be able to get your old entries back if the procedure changes your menu.lst file.
Then you want to get the kernel source as written in the guide and the tools you'll need : 
```

sudo apt-get install linux-kernel-devel fakeroot build-essential
sudo apt-get build-dep linux-image-$(uname -r)
sudo apt-get source linux-image-$(uname -r)
mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-<version-number-here>.tar.bz2
cd linux-source-<version-number-here>

```
You are now inside the linux source directory.
And this is where it gets a bit tricky. The patche you need to apply is [here]("http://lkml.org/lkml/diff/2008/8/4/110/1"). However it wouldn't patch for me so I had to edit the code by hand. The file you want to edit is : sound/pci/hda/hda_intel.c. 
I created and attached a patch to allow you guys to do this automatically.
Extract it in the source directory.
It should patch cleanly using the following command :
```

nvidia_hda.patch | sudo patch -p0

```

Now what you want to do is copy your old kernel config to the directory and use it to get your new kernel to the configuration of the current one.
```
cp -vi /boot/config-`uname -r` .config
```

To configure the Kernel you are going to need the following packages : 
```
sudo apt-get install qt3-dev-tools libqt3-mt-dev
```
and then start the configuration dialog :
```
make xconfig
```
This will open a window filled with a bunch of stuff begging for you to tweak. **Don't do anything to any of that unless you're absolutely sure of what you're doing !**
Now the one thing you must do (I tried without it, it didn't solve the sound crackling thing) is go to* Device Drivers -> Sound -> Advanced Linux Sound Architecture -> PCI devices *and select *Intel HD Audio*. A bunch of stuff are going to be activated with that, leave them.
Save and Exit.
Now your kernel is ready to be built.
From here I'm just following the guide that I linked to at the beginning :
```

make-kpkg clean && fakeroot make-kpkg --initrd --append-to-version=custom-sound kernel-image kernel-header
cd ..
sudo dpkg -i linux-image-<version>.deb
sudo dpkg -i linux-headers-<version>.deb

```

When installing the linux-image, you may be asked if you want to replace your grub/menu.lst file by the new one. Replace it and then look inside both the one you backed up at the beginning and the new one to see if your old kernel entries are still in there. If they are not, paste them. That way if the new kernel doesn't start, you can always select the old one from Grub at startup.

Finally if you installed drivers without using the packaging system (apt-get or synaptics) you will have to reinstall them.

I have had no more crackling issues, my sound is clean and that makes me happy. I realize this is mostly a copy/paste from the kernel guide and anyone who took the time could probably have done it as well.
Enjoy !

---

### Post by Gizmonty on 2008-10-04
Thanks very much for your efforts. I am having the same issue with a gigabyte motherboard (GA-M78SM-S2H) and have been trying to apply your instructions with limited luck (I am no kernel guru either but am happy following instructions).

The first problem I have is that I think you need to add the line
```
sudo apt-get install linux-source
```
before mkdir ~/src

The next problem I have is that your patch file seems to be corrupted. I have extracted it with the command *tar -xf nvidia_hda_patch.tar* and get the file nvidia_hda.patch. This seems to contain garbage though and I am unable to apply it with the instruction you gave. If I instead try
```
patch -p0 sound/pci/hda/hda_intel.c nvidia_hda.patch
```
I get

[I]patch unexpectedly ends in middle of line
patch: **** Only garbage was found in the patch input[/I]

Have I just done something wrong or do you need to re-upload the patch (perhaps without compressing it - it's not that big is it?).

Alternatively, I might just try the beta of intrepid now that that's out.

---

### Post by Zaff on 2008-10-05
Okay well the patch should be this : 
```

*** /usr/src/linux-source-2.6.24/sound/pci/hda/hda_intel.c  2008-10-03 10:38:11.000000000 +0200
--- linux-source-2.6.24/sound/pci/hda/hda_intel.c   2008-10-01 20:23:46.000000000 +0200
***************
*** 268,273 ****
--- 268,278 ----
  /* Defines for Nvidia HDA support */
  #define NVIDIA_HDA_TRANSREG_ADDR      0x4e
  #define NVIDIA_HDA_ENABLE_COHBITS     0x0f
+ #define NVIDIA_HDA_ISTRM_COH          0x4d
+ #define NVIDIA_HDA_OSTRM_COH          0x4c
+ #define NVIDIA_HDA_ENABLE_COHBIT      0x01
+ 
+ 

  /*
   */
***************
*** 871,876 ****
--- 876,887 ----
        update_pci_byte(chip->pci,
                NVIDIA_HDA_TRANSREG_ADDR,
                0x0f, NVIDIA_HDA_ENABLE_COHBITS);
+         update_pci_byte(chip->pci,
+                 NVIDIA_HDA_ISTRM_COH,
+                 0x01, NVIDIA_HDA_ENABLE_COHBIT);
+         update_pci_byte(chip->pci,
+                 NVIDIA_HDA_OSTRM_COH,
+                 0x01, NVIDIA_HDA_ENABLE_COHBIT);  
        break;
          }
  }

```
So try pasting this inside a text file and use the patch command (mine and yours are supposed to have the same effect).
Let me know if this works, I'd like to know if I did something wrong myself :)

---

### Post by Gizmonty on 2008-10-09
Thanks for that. I have encountered a major hardware problem so it'll be a few days until I can let you know if it works, but I will as soon as I get it working (although 8.10 is getting closer and closer [the beta wouldn't run on my hardware - known bug with nvidia graphics]).

---

### Post by Zaff on 2008-10-09
> **Gizmonty said:**
> Thanks for that. I have encountered a major hardware problem so it'll be a few days until I can let you know if it works, but I will as soon as I get it working (although 8.10 is getting closer and closer [the beta wouldn't run on my hardware - known bug with nvidia graphics]).

Good thing I didn't try to install the beta then, I have Nvidia graphics too...
Hope it works for you.

---

### Post by Gizmonty on 2008-10-11
OK, 2 gig of shiny new RAM and I'm back in action.

Thanks for the patch. It wouldn't apply automatically, gave an error on the second hunk. I didn't invest too much effort to find the problem - however, I was able to edit the file manually and put the changes in (I'm assuming I understand patch files well enough to do this).

You were also 1 letter out on the line

```
make-kpkg clean && fakeroot make-kpkg --initrd --append-to-version=custom-sound kernel-image kernel-header

```

It needs to end with kernel-headers instead (but easy enough to find the error from your link - thanks).

Kernel is compiling now - I'll let you know the outcome.

---

### Post by Gizmonty on 2008-10-12
OK. The short answer is that it works. I am able to play sound without any crackling. Thanks very much!

Unfortunately when I boot up with this new bios I am unable to get my video drivers working properly and am stuck with 640x480 resolution. I have gone through the same process to install them as I did originally (nVidia's drivers from their website) but they just won't take! I'm sure it will work with a bit more coaxing though although I'm wondering if there's anything obvious I haven't done.

Anyway, thanks again. You've solved a very annoying issue for me (at least until 8.10 is out in 3 weeks :).

---

### Post by Zaff on 2008-10-12
> **Gizmonty said:**
> OK. The short answer is that it works. I am able to play sound without any crackling. Thanks very much!

Unfortunately when I boot up with this new bios I am unable to get my video drivers working properly and am stuck with 640x480 resolution. I have gone through the same process to install them as I did originally (nVidia's drivers from their website) but they just won't take! I'm sure it will work with a bit more coaxing though although I'm wondering if there's anything obvious I haven't done.

Anyway, thanks again. You've solved a very annoying issue for me (at least until 8.10 is out in 3 weeks :).

try removing the nvidia drivers completely by doing this first : 
```
sudo apt-get remove linux-restricted* nvidia*
nvidia-installer --uninstall

```
And then reinstall the driver. 
You need to reinstall the driver everytime you update the kernel if you are using the driver from nvidia's website

---

### Post by Gizmonty on 2008-10-14
Thanks yet again.

It took a little tinkering after reinstalling (with xorg.conf as it no longer detected my monitor correctly), but I am now back to a fully functional system with perfect sound.


I hope I can return your help in some way some day.

---

### Post by gulhaj on 2008-10-15
Hi, I had exactly the same problem  with the sound on my Compaq CQ50 laptop and this thread helped me get it fixed. Thanks a lot!! 

I've noticed that, running my patched kernel with perfect sound, the internal speakers continue to play when I connect external speakers. When I run my old kernel build, the internal speakers mute as soon as I connect the external ones. Does anyone know if there's a way to change this settings?

---

### Post by Zaff on 2008-10-15
> **gulhaj said:**
> Hi, I had exactly the same problem  with the sound on my Compaq CQ50 laptop and this thread helped me get it fixed. Thanks a lot!! 

I've noticed that, running my patched kernel with perfect sound, the internal speakers continue to play when I connect external speakers. When I run my old kernel build, the internal speakers mute as soon as I connect the external ones. Does anyone know if there's a way to change this settings?
I don't have any internal speak to test this but, maybe it's got something to do with your kernel config (and I'm just guessing here). I've found that a few settings were changed (for instance I didn't compile the midi sequencer module so I'm gonna have to rebuild the kernel yet again to use tuxguitar).
Check in the make xconfig dialog to see if there's anything in the sound sub menu that might help on this.

---

### Post by RobsterNZ on 2008-10-18
Another happy customer, thanks very much!

Zaff/Gizmonty, are you aware of the envyng package? It automates installing/removing the nvidia and ati drivers, and it's all class.

When I change a kernel version (usually due to a Kubuntu update, this was the first time I'd actually compiled my own), I boot into the "Recovery mode" option, and select Root prompt, then run envyng -t to remove and reinstall the nvidia driver. Only a couple of minutes, and everything Just Works.

---

### Post by gulhaj on 2008-10-21
I installed the Linuxant ALSA driver (improved support for Conexant chipsets which I have...) and it solved my problem with the internal speakers not muting when I plug in my headphones. It seems to fix the sound crackling problem without rebuilding the kernel!

[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by junfeng wu on 2008-10-23
> **gulhaj said:**
> I installed the Linuxant ALSA driver (improved support for Conexant chipsets which I have...) and it solved my problem with the internal speakers not muting when I plug in my headphones. It seems to fix the sound crackling problem without rebuilding the kernel!

[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

You are more than right. My CQ50z now has everything working! Thank you so much! :)

---

### Post by Zaff on 2008-10-24
Alright I'll put the link to the linuxant drivers on the main post now so people don't have to go to this page.
I should try that but I'm lazy :P
And intrepid is coming out in a few days anyway so ....

And here endeth my first real contribution to troubleshooting an issue in Ubuntu :)

---

### Post by juanfe on 2009-02-21
Zaff,

You found the answer that eluded me for months to fix the crackling sound on an ALC883 audio chipset. Using the Linuxant drivers saved me from having to compile my own kernel.

For the sake of someone googling this in the future looking for a similar fix:

I'm running XBMC (Live) on a Shuttle Barebones XPC SN78SH7. I suffered from static/crackling/popping sounds when playing audio files (MP3) over the SPDIF output. No such sounds when playing DVDs.

This box has an on-motherboard sound card.aplay -l lists it as follows

```
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

All my audio options on XBMC are as default in the XBMC Live install DVD (which is running Ubuntu -- kernel 2.6.24-19-generic, if it helps anybody).

To resolve the problem, i did the following:

1) Go to the root directory (xbmc user) and create a temporary holding place for linuxant drivers
```

cd ~    
mkdir tmp
cd tmp
wget http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.19.2_all.deb

```

2) Get the linux headers for the version of the kernel you're running -- you'll need these to install the drivers, even though you're not recompiling the kernel
```

sudo apt-get install linux-headers-$(uname -r)

```

3) Install the new drivers
```

sudo dpkg --install alsa-driver-linuxant_1.0.19.2_all.deb

```

4) Reboot and enjoy.

Hope this helps

---

### Post by djamu on 2009-05-14
Proper fix for jaunty ( possibly intrepid ) without compiling here.

> [http://ubuntuforums.org/showthread.php?p=7279149#post7279149]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149")

[COLOR="Red"]ignore this, I posted in wrong thread, sorry[/COLOR]

---

### Post by dcstar on 2009-05-15
> **djamu said:**
> Proper fix for jaunty ( possibly intrepid ) without compiling here.

> [http://ubuntuforums.org/showthread.php?p=7279149#post7279149]("http://ubuntuforums.org/showthread.php?p=7279149#post7279149")

And how does a post referring to Intel hardware relate to this thread's NVidia hardware?

---

### Post by djamu on 2009-05-18
> **dcstar said:**
> And how does a post referring to Intel hardware relate to this thread's NVidia hardware?

mm sorry my bad, thought it was about the same chipset ( branded differently )

---

