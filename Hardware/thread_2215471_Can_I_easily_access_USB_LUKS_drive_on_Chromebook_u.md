---
title: "Can I easily access USB LUKS drive on Chromebook using crouton / KDE"
date: 2014-04-06
forum: Hardware
---

### Post by psyguy92 on 2014-04-06
I couldn't figure out if this post should go in Hardware, Security, KDE/Kubuntu, or other, so here it goes. 

I have a chromebook (toshiba, intel based processor) and used crouton to install
the modified kde version of ubuntu trusty release.

I needed to access a USB external LUKS ext4 drive. I couldn't figure out how to do this
under chromeOS, so I tried under the KDE chroot that I installed alongside the ChromeOS 
on the Chromebook. KDE recognized the USB LUKS drive, prompted for the passphrase 
(after KDE wallet was triggered and closed), and failed to decrypt. I went to the command 
line to try. 

sudo parted -l
revealed location of LUKS device to be /dev/sdb , so:
sudo cryptsetup open /dev/sdb1 mine
caused drive to be mapped to /dev/mapper/mine , so:
sudo mount /dev/mapper/mine /mnt/ , 
caused decrypted mapped drive to be mounted and it is now accessible from /mnt/mine

:)

Now, how the heck to do I do that more easily? ? 

I would like to 
1.) Do this within ChromeOS and 
2.) Do this within the KDE chroot installation using the GUI

It's taken me hours to get this far. Any help would be appreciated! pleasepleaseplease

Additional info: my goal is to use the chromebook laptop and store data on an encrypted external drive using primarially linux. I'd like to possibly keep the ChromeOS installation and maintain the crouton / Ubuntu OS for using native linux applications. I know that the crouton is not a clean install of Kubuntu / KDE, and I'm willing to nuke the entire device's OS and do a straight Ubuntu install if necessary. I'm not particularly attached to KDE, though I dislike Unity.

---

