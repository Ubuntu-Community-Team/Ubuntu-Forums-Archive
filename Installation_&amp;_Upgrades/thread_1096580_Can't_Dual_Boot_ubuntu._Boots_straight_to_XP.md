---
title: "Can't Dual Boot ubuntu. Boots straight to XP"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Liveone on 2009-03-15
Whats up all? Glad to be apart of these forums, hope to be on the other end of these problems some day.

Well I have a little problem. I have no idea what I'm doing.

Firstly, I was able to make sense of how to partition ubuntu correctly, or so I though. I unpartitioned my HD completely, freeing up the entire thing(160GB). Then I installed ubuntu and and partitioned my drive just like this:

|| -- XP -- || ---- /home ---- || - / - || swap ||

   20 GB      120GB  ext3       10GB ext3      4GB       

Except, I left the XP, 20GB portion unpartitioned, unformatted and unmounted. I just set it as Primary as I planned to format it as NFTS with XP. Everything else was carried out as logical, partitioned and formated. Then, I went to install XP, but when I tried to install XP on the 20GB partition which I thought was unpartitioned...it apparently was not (I'm 100% sure I told ubuntu to leave it alone...no mount...nothing. Just a primary empty partition). So, the install told me deleting the 20GB partition, leaving it unpartitioned, and then partitioning over that was the only way to partition the drive...so thats what I did.

Windows Installed and formatted fine, but upon restart I did not get a dual boot menu, goes straight to windows every time. So, I then installed "FS-Drive". During the install process I saw :


         || -- XP -- || ---- /home ---- || - / - || swap ||

   20 GB **NFTS**     120GB  ext3       10GB ext3      4GB  

got to pick a letter for my partitioned drives and everything. So, everything is partitioned, but where is ubuntu at? The drives show up on windows, but when I click on any of them, other than the NTFS, I get a pop up saying " the disk in drive x is not formatted would you like to format it now?" I click no.

THEN, I restart my PC with the ubuntu install CD in there, and it boots up ubuntu, but as if I'm about to instll the OS for the first time. So, I clicked Install ubuntu. It started the install process all over. When I got to the partition portion, I chose manual, and there was nothing to partition. That /dev/sda5(whatever it is by default) was there, but no partitions showed up. So, I could've unpartition everything, but I just left it alone and hit quit. Then....ubuntu LOADED. I could use firefox and everything. 

I then went to click on the NFTS partition/volume/drive/whatever to open it (apparently mount it?), but I got some unclean shutdown message:

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdf1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sdf1 /mnt/external/ -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sdf1 /mnt/external/ ntfs-3g defaults,force 0 0


Got the same message even with ext3 volumes.

Thats when it hit me..."I'm in over my head". I didn't dare try any of that recommended stuff. Partly...because I have no clue where to under it or what it means. I'll figure that out in a tutorial though as I'm sure any help will require me using some commands....

So, I'm obviously completely oblivious to this crap. I'll be looking at tuts as I wait for a response, but I highly doubt I'll come up with anything. Thanks for looking! Any replys appreciated.

---

### Post by theozzlives on 2009-03-15
you're supposed to install XP first  see this to fix your GRUB: [http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restorehttp://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restorehttp://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore")

---

### Post by Liveone on 2009-03-15
Thanks for the quick reply. I tried to follow the instructions, but I couldnt "load" /swap /boot or / without formating as the directions clearly stated not to. Interestingly though...I was able to mount all drives this time around. I feel so leet. 

Buuuuuut i canceled, popped in the xp CD, deleted the ubuntu partitions. Ill be defragging windows, and partitioning the right way this time around. hopefully that solves it.

Edit: for anyone who is interested, this worked like a charm.

---

