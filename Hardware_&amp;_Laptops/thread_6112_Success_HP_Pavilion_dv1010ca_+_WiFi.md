---
title: "Success: HP Pavilion dv1010ca + WiFi"
date: 2004-11-24
forum: Hardware &amp; Laptops
---

### Post by magicfab on 2004-11-24
Hi,

Just a quick report about installing Ubuntu Linux on a HP Pavilion dv1010ca laptop. I also managed to install Debian (using a network install ISO) previously. Anyways, here's the results:

[list]
[*] Resizing the existing NTFS partition:
At first I tried booting from Mandrake 10.0 community edition, using its partition manager but I got errors when trying the resizing. I had to go back to Windows XP and schedule a chkdsk (in a command-line, enter chkdsk). Once the chkdsk completed, rebooted back in Mdk 10.0 and then I was able to resize the NTFS partition. Once that was completed, booted with Ubuntu (Warty) installer disk and was able to complete network installation.

QuickPlay DVD and music playback were not affected and worked fine afterwards. I haven't checked the recovery partition ;)

[*] Network:
eth0 detected and working out of the box

[*] Display:
Haven't had success setting up 1280x768 WXGA, however 1024x768 works fine, stretching the display.

[*] Wireless:
Of course wireless-tools package has to be installed.

This model has the Broadcom-based Wifi mini-PCI card. It works fine with NDISwrapper, see the entry I created at:
[http://ndiswrapper.sourceforge.net/wiki/index.php/List](http://ndiswrapper.sourceforge.net/wiki/index.php/List)
Also see the step-by-step instructions at:
[http://www.linuxquestions.org/questions/showthread.php?postid=809664](http://www.linuxquestions.org/questions/showthread.php?postid=809664)

Remember to use make and then make install!
Also important, you may have to restart the interface (ifdown wlan0 / ifup wlan0)

The special key to diable wifi works to turn it off, but to  turn it back on you hav

[*] Internal mem card reader:
No luck so far, however I have a Lexar Jumprive Trio that worked without addtnl. config in any of the USB ports

[*] VGA-out: 
Works out of the box.

[*] Battery / power management
Battery meter works out of the box, when closing lid it seems only the screen is shutdown and when opening back, the screen saver password (?) is asked (same as main user's).

[*] Modem:
not tested

[*] DVD:
No luck so far playing DVDs, tried VLC and ogle

[/list]

---

### Post by magicfab on 2004-11-25
This report is listed at [TuxMobil - Linux on laptops, notebooks, PDAs and mobile phones](http://www.tuxmobil.org)  :smile:

---

### Post by ohrock on 2005-02-17
Thanks for your post.

  I'm just trying UBUNTU on a dv1130 (almost the same as the 1010) and your idea of using MDK for re-sizing the partion is great.  I tried Partition Magic, but the version I have - too old probably, - just doesn't like XP.  MDK 10 did the job perfectly.

Thanks!

By the way, I had to pass the parameter 'nolapic' to the kernel at boot from GRUB, otherwise the system would hang halfway through booting.  

I'm in the installation second stage now, so I haven't tried the wireless network, or anything else for that matter,  but I found this modline for the XF86Config-4 monitor section:

Modeline        "1280x768" 80.14 1280 1344 1480 1680 768 769 772 795

I found it here:  [http://antares.escomposlinux.org/index.php?p=67#Video](http://antares.escomposlinux.org/index.php?p=67#Video)

That howto is for this machine's Compaq twin brother - the dv2000-, so it should work fine and solve the widescreen problem.  

I have that modeline working perfectly and I have to say that the screen looks fantastic.

Thanks!

---

### Post by meeas on 2006-04-06
Hey guys, did you know that both Debian and Ubuntu BOTH support NTFS resizing?  While you are partitioning, simply select the NFTS partition, then select the size line, and enter a new size.  Its been there since the first sarge beta installer, about a year before Ubuntu officially launched.  Enjoy.

Also, do your laptops have the new Core Duo processor in them?

---

### Post by lliseil on 2006-06-29
Thank you guys for reporting your hardware experience.
I tried to get Dapper booting a HP Pavilion 1010dv last week but couldn't go further than launching the kernel :(
Of course if I had know the "nolapic" boot option, that may have been different...

meeas > Thank you for the old news about resizing NTFS partition with Debian Sarge & Ubuntu  :)
But for those laptops having the new Core Duo processor in them... well just have a look at the time they posted as it should answer your question straight forward lol

---

### Post by mgaskell on 2007-04-05
Regarding your card reader, look at the following url. It fixed the problem on my TI card reader in my HP Pavilion dv 1000:

[http://ubuntuforums.org/showthread.php?t=315497](http://ubuntuforums.org/showthread.php?t=315497)

---

