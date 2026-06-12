---
title: "Ubuntu 8.04 Dual-Boot Issues (Windows XP Professional 32-bit)"
date: 2008-11-10
forum: General Help
---

### Post by jdschultz on 2008-11-10
Hello everybody, I'm not going to lie and say that I'm not new to all of this so I figure I'll just admit it.

Over the past couple of days I had some hard drive issues and thought this would be as good of time as any to try this whole Linux thing again... (had some issues with a Vista dual boot at one point in time absolutely hosing the drive, though that was Vista I'm fairly certain)

So I installed XP back on the new drive that I found but only partitioned 150 GB for XP. The remainder of it I left for a Linux Distro in this case Ubuntu 8.04. I used the rest of it during the Ubuntu install process. I then rebooted the computer and everything went downhill from there. I can get into Windows XP just fine, however whenever I try and boot into Ubuntu it gets to 

running boot scripts local /etc/rc.local [OK]

but after that the screen will just turn black and sit there and do nothing else. The version that I select in Grub is 

**Ubuntu 8.04.1 kernel 2.6.24-21-generic **

However the other options that are available are Ubuntu 8.04.1 kernel 2.6.24-21-generic (recovery mode), Ubuntu 8.04.1 kernel 2.6.24-19-generic and Ubuntu 8.04.1 kernel 2.6.24-19-generic (recovery mode) there is also a selection for Ubuntu 8.04.1, memtest86+

I'm assuming the last one is just to check the drive integrity. Any assistance would be great as I'd love to be able to actually use Ubuntu, but obviously cannot if I cannot get into the system itself.

Thanks
Jonathan.

---

### Post by uidb4056 on 2008-11-10
Have you tried to edit the first option for boot pressing 'e' key and 'e' again in kernel line to remove 'quiet' and 'splash' options (you can also test to add 'noacpi') then press enter and 'b' to boot with these options. May be it then boots or at least you can have more info about what happens.

---

### Post by jdschultz on 2008-11-11
Hey there uidb4056,

Thanks for the reply.  I removed the quiet (splash wasn't on there) and booted and still had the same issue.  I added the noacpi and the computer just restarted and went back to grub after it posted.  I added noacpi and removed quiet and had the same issue as well.

I hope this helps.  I'm at a loss, but whenever I have to restart the computer because it isn't booting correctly it reverts back to having quiet and not having noacpi.  I'm assuming this is because it wasn't able to boot correctly, but I could be wrong.

Thanks in advance!
Jonathan.

---

### Post by jdschultz on 2008-11-15
I'm still having issues with this and was curious if there were any other ideas out there.

Thanks for any help in advance!

---

### Post by uidb4056 on 2008-11-25
> **jdschultz said:**
> Hey there uidb4056,

Thanks for the reply.  I removed the quiet (splash wasn't on there) and booted and still had the same issue.  I added the noacpi and the computer just restarted and went back to grub after it posted.  I added noacpi and removed quiet and had the same issue as well.

I hope this helps.  I'm at a loss, but whenever I have to restart the computer because it isn't booting correctly it reverts back to having quiet and not having noacpi.  I'm assuming this is because it wasn't able to boot correctly, but I could be wrong.

Thanks in advance!
Jonathan.

The reason that every time you have to modify this options is because the method I suggest you is only temporary, you can fix this if you are able to boot editing the menu.lst file and modifying the correspondent kernel line that you see in the boot menu when press 'e', if you cannot boot with graphical environment, you can do that from Live CD.

Anyway is not clear from your message if you has been able to boot with no quiet and noacpi. If not have you tried to boot with the recovery option?

---

