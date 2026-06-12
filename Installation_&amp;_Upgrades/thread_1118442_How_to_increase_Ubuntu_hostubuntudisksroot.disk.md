---
title: "How to increase Ubuntu /host/ubuntu/disks/root.disk"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by wlbragg on 2009-04-07
I am NEW to Linux and have ran out of space on the /host/ubuntu/disks/root.disk. Is there a way to increase this space available for Ubuntu files.
I have duel boot xp/ubuntu. Ubuntu is running along side or ontop of Windows if I understand correctly how I installed it. Both OS's are on the same D: physical drive which is one partition of 76 gigs of which there is 33 gigs free. 

df -h reports

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   13G  131M  99% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  200K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  3.0M  502M   1% /dev
tmpfs                 505M  296K  505M   1% /dev/shm
/dev/sda1              77G   34G   43G  45% /host
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile

gparted shows
/dev/sda1 
ntfs 
/boot,/host D Drive 
Size 76.32 GiB 
Used 33.59 GiB
Free 42.73 GiB 
Flags - boot

How can I change the size of /host/ubuntu/disks/root.disk?

---

### Post by Partyboi2 on 2009-04-07
You can use LVPM to increase the size of the virtual drive. See [[COLOR=Blue]here[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?").

---

### Post by wlbragg on 2009-04-07
You are a lifesaver, thank you very much. I wasn't sure exactly how Ubuntu was installed. This explains the whole thing in my instance. Thanks again!

---

### Post by wlbragg on 2009-04-07
Any idea why LVPM hangs when resizing the above virtual root.disk?

It appears to just sit there at the beginning (10%) or so of the progress meter. I let it go for a couple hours with no change in progress. 

I was resizing the 13GiB root.disk to approx. 25GiB (25600 MB in LVPM) which would leave approx 18-19GiB free space on the hard drive. After closing it and booting back into Windows I see that it made a 23GiB new.disk but after moving original and renaming new.disk to root.disk Ubuntu failed to boot. Looks like it made the virtual disk but didn't transfer any files to it?

I ran LVPM from Ubuntu/Applications menu. I thought maybe Apache/Tomcat/MySQL servers running were possibly causing problems so I tried again with them off. No other applications running other than default Ubuntu startup.

Am I doing something wrong or does it take several "HOURS" to create the new virtual disk on a 3200+ processor with 1 GiB ram and I should let it sit there with no progress longer? It looked like the HD light was polling at a consistent loop, if that helps any?

Forget about the above I got it to work by reinstalling LVPM! It did take a little bit over an hour to resize the root.disk from 13GiB to 25GiB!

---

