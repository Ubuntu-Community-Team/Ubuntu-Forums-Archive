---
title: "Recover original MBR of harddrive/partition"
date: 2018-08-25
forum: Hardware
---

### Post by cogitans on 2018-08-25
Okay. I've got several years of experience in Linux so I'm not actually a newbie. I've used Linux Mint for several years and am now using Ubuntu (same HOME-partition).

My computer consists of 3 harddrives. I've got an ssd containing only the system, a 1.8 TB harddrive split up into several partitions containing HOME-partition, DATA-partition, "Windows 10"-partition and data-partition to Windows and the a 300 GB Maxtor harddrive for data.

To get some sort of privacy I'm using VeraCrypt on several partitions.

Now the initial symptoms:
my system has during a long period of time (months) taken more that 1 minute to load. To fix that I tried several options in the BIOS (motherboard H81M-D PLUS). But nothing helped.

A deeper explanation of the long boot-time is several second between power on and going into actual reading from the harddrives / boot-menu appearing. I couldn't figure out what caused this initial booting to take such a long time. So I though maybe it was some update from Ubuntu that made the system search a long time for information (a security-update maybe). So I figured maybe some security-update now was forcing me to update my configuration from a MBT to GPT. So I made the system convert all the MBRs on my harddrives.
All the conversions went great except my 300 GM harddrive. There was some sort of minor error during the conversion so I had to cancel the conversion (later on I managed to convert it through a GUI-utility, though).

Now the real heavy issue. This 300 GB harddrive consists of only 1 VeryCrypt-file. This file doens't exist on the partition anymore (all the space of the partition is free). As I haven't deleted anything I conclude that the index of the files on the partition is corrupt (MBR -> now GPT). That's why I've tryed several recovery-options:
* gfisk (recover mbr, convert mbr to gpt, search for lost information)
* testdisk (both recovery of files and the partition [I've got experience in using testdisk -> a year ago I managed to recover 1 TB from an external harddrive that a paid, recognized computer-forensic-shop wasn't able to recover]). But testdisk isn't able to find any partition or files.
* I ran Photorec which found some files of difference format. But as I knew that the partition was only 1 big VeraCrypt-file I canceled the search by PhotoRec as that utility apparently looked deeper down the filestructure of the partition (discovered files laying below the VeraCrypt-image).

What am I to do to save my data?

I've located another utility (extundelete-0.2.4) but haven't tested it yet.

By the way: my 1.8 TB harddrive is rather new and all the states of several programs tells me that it functional and isn't faulty in any way.
Never the less my partitions get some sort of filesystem-error now and then. When I have to make a hard reset of my system (sometimes Ubuntu 18.04 freezes) I have to fix it the hard way. And then my system won't boot after completing the BIOS. It states something about a usb-setting in one line in terminal. Then a couple of seconds later it prints another line of information about the same thing (USB). And then another line and continues like that.
To fix this issue I first reinstalled Ubuntu and everything was alright. But after a few bootups the situation was back.
To figure out a new fix I tried booting into recovery-mode and fix the file-system here. But somehow the computer freezed up in this process. And if I managed once in a while to get to the login-screen in normal bootup and tried to login the system logged me in alright but after 1 second I transferred be right back to the login-screen like I wasn't logged in. And now I could continue this process over and over again not getting out of the situation. When I tried this I noticed some sort of counter appearing on screen when logged in before I was transferred back to the login-screen (this happeded in recovery-mode, too). I figured out that this was some sort of check of the file-system that didn't complete. So my solution was to boot into the Ubuntu installations-USB and run a check on my harddrives here. Here I was able to discover errors in the filesystem (on both the system-partition (ext4) and the HOME-partition (ext4)) and to fix them. Afterwards I am able to boot normally.
Strange enough this problem occurs pretty often and the fix is always the same (taking a long bootime to boot into the Ubuntu-installation, too, from BIOS).

So somehow my ext4-partions often get some sort of file-structure-error although I shutting down the system as supposed to.
(I got both ufw and Sophos Antivirus with realtime-protection installed).

Now what am I to do?

My main concern at the moment is to get my VeraCrypt-file contain data from the 300GB partition back.

Any help will be greatly appreciated :-)

PS:
testdisk states among other things about the 300 GB partition:
Warning: number of heads/cylinder mismatches 2 (FAT) != 255 (HD)
Warning: number of sectors per track mismatches 18 (FAT) != 63 (HD)

PPS:
I've installed all updates to Ubuntu 18.04 including kernels.

---

### Post by oldfred on 2018-08-25
Do not know Veracrypt. 

But tools like photorec or even testdisk are looking at drive as if unencrypted. They will not work on encrypted data  as that is the entire purpose of encryption, preventing anyone from getting to it.

In past grub would have issues installing in MBR to some drives using Windows DRM. That would write data into the sectors after the MBR and grub's core.img with BIOS/MBR is also in that same area. And with gpt that area does not exist, so grub uses a bios_grub partition and Windows creates a system reserved partition for storing that type of info on gpt drive.

So if veracrypt used the sectors after the MBR, and you converted to gpt, I think you overwrote your data. If data was just in MBR, it would still be there as with gpt you can use the protective MBR for BIOS booting.

I might see what Veracrypt has in the way of recovery tools.
[https://www.veracrypt.fr/en/Home.html](https://www.veracrypt.fr/en/Home.html)

---

### Post by cogitans on 2018-08-25
> **oldfred said:**
> Do not know Veracrypt. 

But tools like photorec or even testdisk are looking at drive as if unencrypted. They will not work on encrypted data  as that is the entire purpose of encryption, preventing anyone from getting to it.

In past grub would have issues installing in MBR to some drives using Windows DRM. That would write data into the sectors after the MBR and grub's core.img with BIOS/MBR is also in that same area. And with gpt that area does not exist, so grub uses a bios_grub partition and Windows creates a system reserved partition for storing that type of info on gpt drive.

So if veracrypt used the sectors after the MBR, and you converted to gpt, I think you overwrote your data. If data was just in MBR, it would still be there as with gpt you can use the protective MBR for BIOS booting.

I might see what Veracrypt has in the way of recovery tools.
[https://www.veracrypt.fr/en/Home.html](https://www.veracrypt.fr/en/Home.html)

Sure, but the harddrive (=partition) had it's data after the canceled  conversion from MBR to GPT. It wasn't lost until I finally converted the  partition and before I did that I read that GPT uses up to 200MB before  the partition and 10MB after the partition to store data about the  partition. That's why I manually made the free space before the  conversion.

And the encryption isn't interesting in this case as it's the file containing the encrypted files that I want to recover.
That  being said I found some information online that veracrypt didn't use  any headers which would make it very difficult to recover.

---

