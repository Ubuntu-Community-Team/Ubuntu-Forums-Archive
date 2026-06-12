---
title: "HOWTO: Acer Aspire 7520"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by oli888 on 2008-02-19
***_[COLOR=Red]Installing Ubuntu Gutsy or Hardy on an Acer Aspire 7520[/COLOR]_***

***_[COLOR=Navy]On Hardy (8.04 LTS)[/COLOR]_***

**LiveCD** - The LiveCD will boot in a low resolution. This can be fixed after installation.

**Sound** - Works automatically.

**Wireless**

After installation, reboot and load your desktop. Then insert your LiveCD, as it has some extra packages. Open a terminal and run:

```
sudo mkdir /media/cdrom
sudo mount /dev/cdrom /media/cdrom
```

Now go to System > Administration > Software Sources, and unselect everything other than the CD - this includes all the ones under other tabs. Then go back to the terminal and run:

```
sudo apt-get update
sudo apt-get install g++
```

Then, download the following file - you will need to do this with another connection, or you could do it on another computer and copy it onto a USB stick.

[http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

Save/copy the file into your home folder (/home/yourusername), then go to System > Administration > Hardware Drivers, and deselect each of the drivers. It will ask to restart, but do this later. Then go to a terminal and run:

```
tar -xzf mad*.tar.gz
cd madwifi*
cd scripts
sudo ./madwifi-unload
```When asked, enter "r" and press enter, so that other modules are removed. Then do:

```
sudo ./find-madwifi-modules.sh $(uname -r)
cd ..
sudo make
sudo make install
sudo modprobe ath_pci
gksudo gedit /etc/modules
```Add a new line saying:

```
ath_pci
```Save, exit and reboot. Your wireless connection will be started automatically.

***_Graphics card_***

To install the Graphics card, open a terminal and run:

```
sudo apt-get update
sudo apt-get install envyng-gtk
```Then go to Applications > System tools > EnvyNG. It will pick the right driver, so just click "Forward" and "Ok" when needed, and then reboot once it's done. You should then get the maximum resolution of 1440x900.

**[COLOR=navy]*_Gutsy (7.10)_*[/COLOR]**
***LiveCD***

Select "Safe Graphics Mode" when booting.

**After Installation**

To stop it freezing on boot, wait until the Grub menu comes up, then press [e] on your keyboard. Press [Down] until you get to the line starting with "kernel". Then press [e]. Then, at the end of the line, enter:

```
 all_generic_ide
```Then press [Enter], then [b], and Ubuntu will boot correctly. Once you've reached the desktop, open a terminal and run:

```
gksudo gedit /boot/grub/menu.lst
```

On the Ubuntu entry, find the kernel line, and add the "all_generic_ide" just as you did before. Save the file and exit. Now, when you reboot, the entry will have changed automatically.

**Wireless**

Follow the instructions for the wireless on Hardy - they apply to Gutsy too. The only difference is that I don't think G++ is on the installation CD, so you'll have to download that too from [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=g%2B%2B"). Save it in your home folder, then open a terminal, and run:

```
sudo dpkg -i g++*.deb
```

**Sound**

Go to System > Administration > Software sources. Click on the "Updates" tab, and activate the top three options.

Then go to System > Administration > Synaptic Package Manager. Click "Reload", then find the linux-backports-modules-generic package. Right-click it, select "Mark for installation". Then click "Apply" and after a reboot you will have sound.

**Graphics card**

Follow the instructions for Hardy, but instead of installing Envyng-gtk, install envy-gtk.

To get rid of the Nvidia logo from the startup, you can run:

```
sudo nvidia-xconfig --no-logo
```

Good luck, and please post any problems that you have,

Oliver

---

### Post by Sigudian on 2008-03-10
Is it possible to modify the Ubuntu ISO to automatically support this GPU, wirless and soundcard?
would be easier, and then you could have a live cd that would work on 7520

---

### Post by gmclachl on 2008-03-10
Hardy Heron supports the soundcard out of the box, and the nvidia driver is a few clicks away, wireless still doesn't seem to work but that's pretty straight forward to sort (thanks to the madwifi guys)

George

---

### Post by Ebuntor on 2008-04-05
**Oli888 **thank you for the excellent howto, I would never been able to get everything working on my own. :)

---

### Post by oli888 on 2008-04-11
> Is it possible to modify the Ubuntu ISO to automatically support this GPU, wirless and soundcard?
would be easier, and then you could have a live cd that would work on 7520 

I imagine that it's possible, but not easy. Remastering Ubuntu is a bit of a grey area. If you get it working, it would be fantastic!

> Hardy Heron supports the soundcard out of the box, and the nvidia driver is a few clicks away, wireless still doesn't seem to work but that's pretty straight forward to sort (thanks to the madwifi guys)

Thanks for the post - the sound worked for me too, but I had upgraded and assumed that the driver had carried over. I've added your info to the post.

The wireless doesn't seem to activate on boot for me like it did on Gutsy. I guess you could try making your own startup script, so I might give it a try. But this could be because I upgraded, rather than doing a fresh install.

> Oli888 thank you for the excellent howto, I would never been able to get everything working on my own.

It's really just a compilation of all the info from [this thread](http://ubuntuforums.org/showthread.php?t=545401) and a couple of things I found on the web. I figured that it would be better to have one post, than 12 pages of posts. :) Thanks for the positive feedback.

**EDIT:** I've done a fresh install of the Beta, and the hardware detection was slightly different. I've added everything to the original post.

---

### Post by legionzars on 2008-05-01
what happens with the webcam? is it working? thanks for the info I managed to get Gutsy working on my Aspire 7520 and I got the webcam working and I just wanted to know it if works on Hardy too.

---

### Post by oli888 on 2008-05-10
> **legionzars said:**
> what happens with the webcam? is it working? thanks for the info I managed to get Gutsy working on my Aspire 7520 and I got the webcam working and I just wanted to know it if works on Hardy too.

I'm not sure - my one didn't come with a webcam. :) If you successfully get the webcam working on Hardy, please post here, and I'll add it to the post.

---

### Post by oli888 on 2008-05-24
After a discussion with ePax on the #ubuntu channel, I managed to get wireless working on startup. Open a terminal and run:

```
gksudo gedit /etc/modules
```

Then add the following on a new line:

```
ath_pci
```

Reboot and your wireless will work. I'm going to remove the guide for Gutsy, as I assume that anyone who is installing Ubuntu will be using Hardy, not Gutsy.

---

### Post by Ebuntor on 2008-05-29
> **oli888 said:**
> After a discussion with ePax on the #ubuntu channel, I managed to get wireless working on startup. Open a terminal and run:

```
gksudo gedit /etc/modules
```Then add the following on a new line:

```
ath_pci
```Reboot and your wireless will work. I'm going to remove the guide for Gutsy, as I assume that anyone who is installing Ubuntu will be using Hardy, not Gutsy.

I had to do a fresh install of Hardy again so I tried this but no luck. Do I have to disable the Atheros driver or something like that?

---

### Post by hp59dk on 2008-06-03
Thank You for this valuable guide.
Can i make the wireless work without the installation CD but with a cable connection instead?

---

### Post by liquerLOVER on 2008-06-03
Thanks a lot... Your tutorial on madwifi really help me. But I just make it shorter. Anyway....thanks Bro...

---

### Post by oli888 on 2008-06-07
> **liquerLOVER said:**
> Thanks a lot... Your tutorial on madwifi really help me. But I just make it shorter. Anyway....thanks Bro...

No problem - credit goes to the Madwifi developers and the people in the other Aspire 7520 thread. I simply collected all the information from it and put it in one place. :)

---

### Post by oli888 on 2008-06-07
> **Ebuntor said:**
> I had to do a fresh install of Hardy again so I tried this but no luck. Do I have to disable the Atheros driver or something like that?

I've replied via PM.

To everyone else:

That addition simply was to activate the wireless on startup. You still need to do the full instructions - it's just you longer need to create a script that activates the wireless every time you login.

---

### Post by oli888 on 2008-06-07
> **hp59dk said:**
> Thank You for this valuable guide.
Can i make the wireless work without the installation CD but with a cable connection instead?

Yes you can. :) Instead of deselecting all the boxes in the "Software Sources" tool, just open Synaptic, click "Reload", then find the g++ package, then right-click it, select "Mark for installation", then click "Apply".

---

