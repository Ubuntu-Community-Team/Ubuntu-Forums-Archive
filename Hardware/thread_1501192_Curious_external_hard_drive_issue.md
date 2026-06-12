---
title: "Curious external hard drive issue"
date: 2010-06-04
forum: Hardware
---

### Post by The Clown on 2010-06-04
Hi all,

I recently purchased a Western Digital Scorpio Blue 500GB, 5400 RPM SATA hard drive and put it in a Link Depot portable enclosure. I used to drive to back up my home folder, did a fresh install of the newest version of Ubuntu and plugged the drive in.

It automounted, I migrated my home folder to the fresh install, and then as soon as that was done...the icon disappeared from my desktop. I decided to let it go for the moment, ran the shell script I run whenever I do a clean install (shell script included later, just in case it's relevant, even though the issue arose before I ran it.), ran the update manager and updated everything.

I got back to the issue of the hard drive not being detected, restarted the computer, and plugged it back in...still nothing. Weird. Tried booting Ubuntu from a live CD and plugging it in to see if an out-of-the box version would still detect it, but that was a no go.

I opened the case to check for a loose connection, but the connection was fine. I even tried to tighten it a little just to make sure.

I would chalk it up to the hard drive not getting enough power, but then why would it run for the hour plus it took to copy my home folder to it, then again to copy it back to Ubuntu, then stop immediately after home was done copying? Also if I press my ear against the enclosure I can faintly hear the drive spinning. Doesn't make sense. I admittedly know nothing about hard drive power, so maybe that's it and I'm wrong? Is that possible?

EDIT: Also, my wife's 320 GB portable automounts, throwing another wrench in the "not enough power" theory.

It's not my USB drive, as a flash drive can be read from it.

I doubt it's a hard drive failure, as I just got the drive yesterday. I don't hear the click of death coming from it, and I haven't exposed it to magnets or anything crazy like that.

It's not a formatting issue, as the drive is formatted to ext4 specifically because I knew I'd be using it with Ubuntu.

I've never used the drive on a Windows or Mac machine, so it's not an issue of forgetting to safely remove the drive from those.

For those curious about my shell script, here it is, but I don't think I did anything that messes with media:

> sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
sudo apt-get update
sudo apt-get install msttcorefonts gparted ubuntu-restricted-extras  wine simple-ccsm powertop sun-java6-jre sun-java6-jdk sun-java6-plugin skype audacity gnome-do asunder mnemosyne f-spot gimp deluge easytag banshee
sudo apt-get update
sudo update-java-alternatives -s java-6-sun
cd /media/disk/"Ubuntu config" mv %gconf.xml ~/.gconf/apps/metacity
cd
sudo wget [http://wallpapoz.akbarhome.com/files/wallpapoz-0.4.1.tar.bz2](http://wallpapoz.akbarhome.com/files/wallpapoz-0.4.1.tar.bz2)
tar -jxvf wallpapoz-0.4.1.tar.bz2
cd wallpapoz-0.4.1
sudo python setup.py install
sudo apt-get remove tomboy ekiga tsclient ttf-thai-tlwg vino rdesktop vinagre xsane evolution rhythmbox gwibber pitivi simple-scan

And finally, here's my output from fdisk -l. The drive doesn't even appear to show up in the output.

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001dfe1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

So, any ideas? Is there something I'm missing here? Is it possible that it would be a lack of adequate power despite the fact that it read for quite a while? I'm completely stumped here. :confused:

---

### Post by The Clown on 2010-06-04
Ugh, I think I found the problem. I took a look at the specifications for the enclosure, and it only supports up to 250 GB. I've ordered one that will support 500 GB ones and will be returning this enclosure tomorrow. Boy, do I feel sheepish. :oops:

---

