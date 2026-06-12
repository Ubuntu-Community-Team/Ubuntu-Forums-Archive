---
title: "Trying to make a home server"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by ki3b on 2009-08-29
Howdy,

I"m trying to make a cheap home server. I have an old PC with two 40 g hard drives (not planning to do a lot on this thing right now, just experimenting) and 512 MB of RAM. Tried to install Ubuntu 8.04 server but evidently I do not have a fast enough processor for it since it had a fatal failure when I tried to load the OS on it.

What I'm looking for.....

A headless stand alone file server. Can be any form of Ubuntu (Xubuntu, etc) One I can turn on and forget. I'd like this to run with nothing attached, no keyboard/mouse or monitor. 

If possible, preferably raid 5 array with both drives, but if I can't do that, I can settle for using just one drive and may end up putting a lot larger drive in there in the near future. 

I'm going to be the only user and it's going to be on a home network, I'm not planning to do any file sharing over the internet, etc with it, just store the files I create or download somewhere else besides on my two machines running Ubuntu. No media sharing with the TV, etc. Mostly open office files and pictures / music from the internet. 


Any suggestions or help? Thanks.....

Joe

---

### Post by .nedberg on 2009-08-29
Not sure what kind of processor you have, but I used an old Pentium machine with 192MB RAM and a 350MHz processor as a file server until last week. I also used 8.04 server edition on it and I had no problems with it at all.

My server was used for NFS file serving to other Ubuntu machines locally, FTP (vsftp) for sharing files over the Internet and ssh (openssh-server) to administrate it. I also had fail2ban on it and Samba, but did not use it.

I didn't care to set up RAID, just used a 10GB disk for system and bigger disks to store all my data (MP3s, Videos, Pictures...).

Have you checked your CD for errors? What kind of processor is in the machine? You might also want to check the RAM. Don't install a GUI, as you will not need it and it will only give you problems when you want to run it headless (remember to set the BIOS to boot without keyboard).

---

### Post by ki3b on 2009-08-29
Hello again,

Thanks for the tips. No I didn't check out my CD. I'll have to try that first. At this moment, I don't have the computer available to check out the processor, will have to do that tomorrow.

I'll check things out and get back with you.

Thanks,

Joe

---

