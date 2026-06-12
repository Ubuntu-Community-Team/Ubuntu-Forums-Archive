---
title: "Uninstalled in order to reinstall and now i'm stuck"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by angelsaint02 on 2009-11-13
Okay I am new to linux and ubuntu, I set up my system a few weeks ago with 9.04 and loved all the functionality of this OS and the whole movement of linux and sharing and developing as a community. 

Here is where I messed up though and now need some help if anyone can crack this situation for me. 

I was upgrading to 9.10 and near the end of the upgrade process I had to close the laptop to head back home from work and when I opened the laptop up again the system was not loading ubuntu, but I could get into vista. So I decided to delete the partition before I read that you should not do that first to perform an uninstall. 

So now that the partition is deleted I get an error when booting my machine:GRUB error 22.
I have already read other forums on how to correct this error, however my machine is a HP and I do not have the installation disc or a recovery disc to repair the MBR.

What I do have is an external enclosure which I have used to slave the drive from my laptop to another machine. I can access all my files and I can see both the recovery partition and the main partition this way and want to know if there is a way to repair the MBR from the command line somehow using the device externally. 

any help would be very appreciated and if worse comes to worse I have backed up my stuff and will resort to formating the main partition and just doing a clean install.

---

### Post by ShadowMage on 2009-11-13
Hi,

I'm not exactly sure how (if possible) to repair it like that, but, if you do decide to do a clean install of Ubuntu it should also reinstall grub for you (unless you tell it not to).

EDIT: What do you mean by main partition, though? Since you deleted your Ubuntu partition, I'm assuming you would need to do a clean install (as opposed to upgrading from older version) anyway to have Ubuntu again. No need to touch your Vista, though. You can just install it where your old Ubuntu was.

---

### Post by PRC09 on 2009-11-13
Found this site with the Vista repair disk from Microsoft.Should get you back up in Vista.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by John Bean on 2009-11-13
Boot from the live CD and reinstall. It makes no difference that grub is broken since it isn't used unless you're booting from the hard disk.

---

### Post by angelsaint02 on 2009-11-14
Thanks for the help PRC09. I haven't really used torrents before now and this was a life saver!  And thanks to everybody else trying to help me out!

---

