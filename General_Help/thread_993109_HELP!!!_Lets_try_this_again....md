---
title: "HELP!!! Lets try this again..."
date: 2008-11-25
forum: General Help
---

### Post by rktompsett on 2008-11-25
A few months back after several failed attempts at downloading and burning my own, I received from UBUNTU the verson 8.04 LTS Desktop Edition install disk.

I'm set up to dual boot with this install on the 2nd hard drive (HD1). 

During the attempted install all I get is a long alfa/numeric list of "stuff" scrolling up the screen with errors noted on several lines of text, then after 8 hours of waiting, yes 8 hours! It locks up. So what am I doing wrong or is it my system? System Data is below...

OS Name	Microsoft Windows XP Home Edition
Version	5.1.2600 Service Pack 3 Build 2600
OS Manufacturer	Microsoft Corporation
System Name	CANTANKE-SQPO8G
System Manufacturer	ASUSTeK Computer INC.
System Model	A7N8X2.0
System Type	X86-based PC
Processor	x86 Family 6 Model 4 Stepping 4 AuthenticAMD ~1336 Mhz
BIOS Version/Date	Phoenix Technologies, LTD ASUS A7N8X2.0 Deluxe ACPI BIOS Rev 1005, 5/14/2003
SMBIOS Version	2.2
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.5512 (xpsp.080413-2111)"
User Name	CANTANKE-SQPO8G\Robert K. Tompsett
Time Zone	Eastern Standard Time
Total Physical Memory	1,024.00 MB
Available Physical Memory	258.06 MB
Total Virtual Memory	2.00 GB
Available Virtual Memory	1.96 GB
Page File Space	2.40 GB
Page File	C:\pagefile.sys

---

### Post by tseligkas on 2008-11-25
Hello Robert,

Let me first state my admiration for your patience & persistence to try and install Ubuntu (your avatar spiced my curiosity so I visited your profile ;)). I'm saying that because other people (in here too), much younger than you, abort any effort from the first little bump they come across.

So, let us come to your issue. Could you tell us what is the procedure you follow to perform your installation? Like, are you booting with the Ubuntu CD? Are you selecting the installation option from the first menu that appears when the CD boots, or do you proceed into a Live Desktop environment and install Ubuntu from there?

The 8 hour wait is _definitely_ not normal. Ubuntu Linux installation should range from 15 minutes to 1 hour top.

Bonus option: What I am about to tell you was first incorporated into the Ubuntu 8.04 that you have (right now 8.10 is out). So, although I know that you'd like to avoid ties with your Windows OS, there is an option that you may like. If you boot to Windows, insert the Ubuntu CD and let it autorun you are given the option to install Linux from there. What will happen is that you will download wubi (**w**indows-**ub**untu-**i**nstaller - for more information look **[here]("http://wubi-installer.org/")**). That means that eventually you can have Ubuntu Linux installed in a windows filesystem folder/partition/disk, being perfectly bootable and possible to uninstall from the Add/Remove Programs icon of your Windows Cotrol Panel. If you decide to use wubi, just don't forget to (re-)format your second hard drive to ntfs (or maybe fat32 - I'm not sure), since you can use that to install Ubuntu.

---

### Post by kanikilu on 2008-11-25
You also mention that there are several errors on the screen. Can you elaborate? Were you able to write any down?

Also, I had trouble installing Ubuntu on a couple computers, and both times my installation problem was solved by choosing the safe graphics mode option. You could also maybe try the text based alternate installer:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Not saying this will fix your installation problems, but as we don't really know what your problem is exactly, this is my best guess right now...

---

### Post by rktompsett on 2008-11-25
First off I probably look older then I really am. I'm 59.5 and my hair was white from the traumas of Jr. High School some 40 years ago. That is me in the Avatar sitting in a surplus B-52 ejection seat that I converted to a desk chair.:popcorn: No it will NOT blast me through the ceiling.:lolflag:

Ok, I have a second drive HD1, that I wish to use as the Linux drive. Because I'm just testing the waters with Linux, I still wish to maintain the MS Windows XP. 
I have my DVD/CD-Rom set to the first boot and my C drive set as the 2nd boot.
I placed the Ubuntu disk into the CD-Rom and it boots fine, creating a dual boot with the GRUB Boot loader. I then ask the program to give me a full install to my 2nd HD. Then as I sit back I wait and I get the crashes. This seems to be the case wither I install (or at least try to) Ubuntu, SuSE, or Sun Microsystem's Solaris. I have had SuSE v.10 on, and then attemped to reinstall a Suse v.11 from a UK publication but it totally crashed. I have to keep it on because the GRUB loader is on C drive and defaulted to boot Windows.

---

### Post by rktompsett on 2008-11-26
> **kanikilu said:**
> You also mention that there are several errors on the screen. Can you elaborate? Were you able to write any down?

Also, I had trouble installing Ubuntu on a couple computers, and both times my installation problem was solved by choosing the safe graphics mode option. You could also maybe try the text based alternate installer:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Not saying this will fix your installation problems, but as we don't really know what your problem is exactly, this is my best guess right now...

There were numerous Errors through out the listing. I'll have to try installing again to see which ones they are.

---

### Post by uzi09 on 2008-12-18
First off: Welcome to the Ubuntu community!

Secondly: Perhaps you may want to just download and re-burn a new copy. It may have been that the disc was damaged some how.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
This should be a good resource. I'm not sure if this is the procedure you followed last time you tried burning your own. I, personally, tend to use Nero on a windows machine, but it normally costs $$$.
In Linux, I normally use k3b which works really well. I'm not sure if it'll run in Windows though.

Just in case all else fails: since you were interested in "just testing the waters with Linux", there is always the option of running it in a virtual machine like [VMware]("http://www.vmware.com/") or [Virtualbox]("http://www.virtualbox.org/"). Heck, you can try a lot more than Linux if you want. Here's a decent site with a variety of OSs as well as distributions for them: 
[http://www.oszoo.org/wiki/index.php/Main_Page](http://www.oszoo.org/wiki/index.php/Main_Page)

(I'll try to see if I can find you a good tutorial for setting up your own vmware setup, however I personally found Virtualbox a lot more user friendly and easier to setup. It was quite idiot proof, so it worked out for me :lolflag:)

---

