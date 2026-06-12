---
title: "Silicon Image RAID - Hardware Detected but no drive"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by Ted_Smith on 2006-04-21
Hi

Having installed Ubuntu (again - I just keep retrying it but then keep getting problems which move me back to Windows) I need some help with my RAID. 

I have a Silicon Image RAID card with 4 HDDs connected as a partitioned RAID. Ubuntu only see's the HDD's themselves as seperate drives - not as a single RAIDed drive. I've looked in the 'Device Manager' and it is recognising the card as "Silicon Image Inc (formerly CMD) PCI0680 Ultra ATA-133 Host Controller" and it see's each of the drives below it. So I guess it's seeing the card and the drives, but why is it not seeing the RAIDed configuration? It is OK during the boot process and is seen before the OS loads. 

I've read a few threads like [this one]("http://www.ubuntuforums.org/showthread.php?t=160537"), and  [this one]("http://www.ubuntuforums.org/showthread.php?t=107183") but neither relate to my issue and the HOW TO that is referred to in one I could not find. 

Any ideas or a HOW TO that can help me out? Some people keep mentioning the beta of Dappa Drake - when is that officially released?

BTW, I using Kernal 2.6.12-10, Breezy Badger 5.10

Thanks in advance

Ted

---

### Post by Ted_Smith on 2006-04-23
Anyone? This is kind of a 'Farwell and goodnight' issue for me because my RAID is my main storage area and if Ubuntu can't access it then there's no point in me using Ubuntu, or Linux full stop. Which is a shame because every time I come back to Linux I do so with great enthusiasm but then seem to get ground down by endless problems that I can't fix (because I aint too bright :0) )

---

### Post by Ted_Smith on 2006-04-25
OK, I've made some progress....

If I go to 'System --> Administration --> Disks' it shows all the physical disks on the left hand side. 

The first disk of my RAID (dev/hde1) says 'Size : 447.14Gb (Free space not available)'. So, I've clicked on the 'Change' button where it says 'Access Path (as this is currently emplty). I've navigated to 'File System' --> 'mnt' and created a new mount point folder called '/mnt/RAID450Gb'. But when I click on 'Enable' the status just stays reading 'Inaccessible'. The other two disks that make up the RAID are both seen as unpartitioned. 

Does this help anyone help me? Feeling rather alone and useless....

Ted

---

### Post by Ted_Smith on 2006-04-25
OK, since my last post, I stumbled across [this post]("http://www.ubuntuforums.org/showthread.php?t=126647&highlight=Mounting+raid+ntfs+ubuntu"). In brief, I have now :

1) Ammended Synaptic Package Manager to look in the universe and multivers repositories and then managed to download and install 'dmraid'. I've rebooted. Since installing that I now have 'sil_agaedcdcaiae' and 'sil_agaedcdcaiae1' names in /dev/mapper. Still no access to the RAID though. 

So what I then tried to do was enter the following line in etc/fstab so that it would mount the RAID at boot up.

/dev/mapper/sil_agaedcdcaiae1 /mnt/RAID450Gb ntfs rw,user,auto

However, it says that only root has access to fstab and whenever I go into the terminal and typ 'su' or 'su root' and enter the password is says Authenitcation Failed, Sorry.  So I can't edit the file even though I know the password is the correct root password. Great! So I've not even got to see if it would work or whether my mount line was even correct because I can't even edit the text file!

This is driving me mad already. I know Linux is way better than Windows but bloody hell, everything is so difficult! 

Can anyone help\correct\guide me through the rest of this process? I really want to stick with Ubuntu this time, but things like this just kill me off every time! 

Cheers

Ted

---

### Post by Ted_Smith on 2006-04-26
I think I've worked out why it's not working. 

My RAID 'controller' is not a real hardware RAID controller I think. It was a fairly inexpensive affair advertised as a RAID controller, but I think in reality it's really just a mimic - controlled by it's BIOS as opposed to by the hardware. 

I've come to that conclusion because I've used a bootable Linux CD (that's used for imagine hard drives) on my machine and a machine at work that has a genuine (and expensive) hardware SCSI RAID. The boot-up on my machine saw 4 seperate disks (just like Ubuntu does) but on the work PC, it see's a 410Gb RAID. 

So, seeing as I don't actually need half a terabyte RAID (I just wanted one) I think I'll go back into the RAID configuration, remove the RAID, then just configure each of them as seperate 160Gb disks.

A shame, but I don't want to spend any more time on it I think. That said, if anyone can either support\refute the above and shed any more lioght on it before I do that I'd love to hear from you.

Cheers

Ted

---

### Post by ScarletEmerald on 2006-05-05
First, if you want to do something as root in Ubuntu, you should use the sudo command, as in:
sudo vim fstab

Now, for your fake RAID controller, you might want to look into dmraid- see [here]("https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/22107") for a bug report about getting this added to the installer.  There may be some advice on the forums here about getting it set up in the current version (I'm trying to do this myself).

---

### Post by Ted_Smith on 2006-05-06
Thanks for your response.

Re dmRAID - already installed that (see post above last) but it didn't seem to help (maybe it did but I am too dumb to understand - it wasn't obvious that it helped!).

Re sudo : admittedly I wasn't running vim to edit fstab. That might have been my problem. I was under the impression that all I had to do was sudo X Y Z, enter password, and that would allow me to do whatever I wanted to do as root providing I entered the password correctly. 

I uninstalled Ubuntu the other day and am at the moment torn between re-installing it again (D'oH!) or installing Arc Lnux. I prefer the KDE layout of Arc Linux and the way that it automatically detects and mounts (by a simple left click) the hard drives. Whereas Ubuntu doesn't. But the support for Ubuntu is better and I think overall it's a better OS with better features. 

Ted

---

