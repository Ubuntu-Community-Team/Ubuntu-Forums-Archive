---
title: "Laptop with hybrid SSD/HDD disk?"
date: 2012-08-06
forum: Hardware
---

### Post by mrjohs on 2012-08-06
Hi! I am considering a Lenovo Thinkpad E530. I have some second thoughts about the disk, though, which appears to be a "hybrid ssd/hdd". After some googling it seems there are different implementations of that, some are software/hardware implementations which requires specific drivers for Windows, others are hardware only and transparent to the OS. In the latter scenario there should be no problems with Ubuntu, but with the former there could be trouble.

Does anyone have experiences with this particular machine, or "hybrid ssd/hdd" disks in general? Would be pleased to know!

The specs of the machine can be found here:
              [http://www.komplett.no/k/ki.aspx?sku=750195#extra](http://www.komplett.no/k/ki.aspx?sku=750195#extra)

Also, there is a brochure/datasheet which mentions Linux compatibility. Should I trust that?
[http://www.partnerinfo.lenovo.com/partners/us/products/downloads/thinkpad-edge/ThinkPad-Edge-E430-E530-Datasheet-US.pdf](http://www.partnerinfo.lenovo.com/partners/us/products/downloads/thinkpad-edge/ThinkPad-Edge-E430-E530-Datasheet-US.pdf)

---

### Post by 4walters on 2012-08-06
I am using an Acer S3 with a 320GB hybrid drive made by Hitachi. The drive shows up as two physical drives. I have my HDD mounted as /home while the SSD is mounted as /. The laptop is just less than a year old and I've had no issues with it. Hibernation and sleep work perfectly and am running 12.04 LTS with no issues.

---

### Post by oldfred on 2012-08-06
That they mention Linux is a plus, but you may also have some issues with Optimus graphics.

nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

This was Dell, but similar hybrid SSD/HDD??
 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

### Post by mrjohs on 2012-08-25
For the record, and/or for anyone stumbling upon this thread, I will give a little report on how it went with regards to the hybrid disk and other things:

After burning out the Windows recovery disks, which took a considerable amount of time, I booted Ubuntu from an USB-stick, told it to resize the Windows partition and installed. After that everything seems normal, apart from GRUB showing two options to boot Windows from, sda1 and sda2. However, it seems like none of these are the SSD-part of the disk, as GParted shows sdb as a 14.91 GB disk which it cannot work out the label or format of. In Windows there seems to be some crapware which handles the SSD-caching, which indicates that it is not a 100% hardware solution. I cannot see the SSD-disk in "My Computer" in Windows either. As long as everything works in Ubuntu I'm happy, so I will not make efforts to investigate this further. 

In case someone's interested I am attaching screenshots of GParted showing both the sda and sdb disks:

[IMG]http://apploudable.com/tmp/screenshotsdisk/screenshot01.png[/IMG]

[IMG]http://apploudable.com/tmp/screenshotsdisk/screenshot02.png[/IMG]

So it seems like the SSD-disk is just sitting there on sdb and not interfering with Ubuntu. I am a bit confused, though, about what the sda1 and sda2 partitions are for, as none of them seems to be the SSD-disk/cache.

With regards to the hybrid graphics solution: Actually, Bumblebee works quite well for this purpose. In addition, the 4000HD is quite a hefty little graphics processor, so there are no problems running Compiz, Sauerbraten or even Doom III without the NVIDIA GPU. The solution of calling it up explicitly with "optirun [application]" is not really that bad. It would be nice though, if Ubuntu had support for Bumblebee out of the box, and more GUI options, like a "Run with Bumblebee" rightclick-option in Launcher. I don't know, though, how much work Ubuntu are willing to put in to support that dreaded proprietary software. 

Other than that all of the stuff works in Ubuntu on the Thinkpad E530: Suspend/resume is fine, battery life is fine, fan control seems to behave nice, etc. I have not tested the fingerprintreader and HDMI-port, though. Apart from that, I can recommend this machine for anyone intending to run Ubuntu.

---

### Post by oldfred on 2012-08-25
Grub2's os-prober looks for Windows boot files & then adds menu entries if boot files are found.

Normally Windows 7 installs 2 boot files into a 100MB boot/repair partition and then has the main install. But you can repair or move boot files to main c: "drive" and boot directly from it. If bootmgr & BCD are in both places you can boot from both.

Boot files:
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=DarkRed]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

Gparted has two partitions with ! in red circles. If you click on symbol and right click what does it say?

---

### Post by mrjohs on 2012-08-25
> **oldfred said:**
> Gparted has two partitions with ! in red circles. If you click on symbol and right click what does it say?

If I rightclick on it and select "Information", I get this:

On sda2: 

[IMG]http://apploudable.com/tmp/screenshotsdisk/screenshot03.png[/IMG]

On sdb:

[IMG]http://apploudable.com/tmp/screenshotsdisk/screenshot04.png[/IMG]

I observe that if I click on any of the drives Windows7_OS, SYSTEM_DRV or Lenovo_Recovery in Nautilus nothing happens.

Should I be worried? Is it just that I'm missing ntfsprogs? I am pretty sure that last I installed Ubuntu it could read the NTFS partitions straight from the box.

---

### Post by oldfred on 2012-08-25
Do not try to install ntfsprogs. It merged with ntfs-3g and if you install the old ntfsprogs it uninstalls ntfs-3g. The ntfs-3g is included, but it will not read NTFS partitions that need chkdsk.

Run chkdsk from Windows on your NTFS partition.

Not sure what disk label issue is. Do you have a label with invalid characters? In gparted you can add/change labels with right click, I think. I usually add labels when creating partitions with gparted and when I forget or want to change I usually use Disk Utility.

---

### Post by mrjohs on 2012-08-25
Yeah... I did chkdsk on Windows in the meantime, after googling the issue. Now there is no exclamation mark on the partition in Gparted, and I can mount the disk! Thanks for making me aware of the issue, so it could be fixed.

Probably, as I understood during googling, it was caused by ntfresize which I guess occurs during installation if one selects "resize windows partition" upon install.

As for sdb, it still has an exclamation mark and comes up as unpartitioned, but as long as everything works I couldn't care less ;)

Thanks for the insights!

---

### Post by oldfred on 2012-08-25
I split my 60GB SSD into two 30GB / (root) partitions and have current & future versions of Ubuntu both installed. 

I am up to 11GB in Precise (I need to check why so large now) and 7 GB in Quantal. So you could reformat sdb as a 16GB root and install Ubuntu to that. With an SSD it boots very quickly.

---

### Post by mrjohs on 2012-08-25
> **oldfred said:**
> So you could reformat sdb as a 16GB root and install Ubuntu to that. With an SSD it boots very quickly.

Hmmm... But Windows currently uses it as a cache. How, I do not know. I might, at some point, install a "vanilla" Windows without the massive amounts of crapware which came with the machine. If I do so, I might attempt to use the SSD as a boot partition for Ubuntu. But right now I am happy as long as it does not get in the way.

---

### Post by Dr. McKay on 2013-02-27
It's an older thread I'm bringing back to life, but I'm also considering an E530 with hybrid drive (I liked this model, only discovered recently it had a hybrid drive).
I would however not be running Win8, which comes preinstalled, but use the laptop exclusively for different flavours of linux. 

How would this kind of drive behave with a dual boot setup, say with Xubuntu and Linux Mint ?  Would both distros be able to benefit from the SSD caching ? Or would this only work with Windows ?

---

