---
title: "Two distros on two physical drives in 1 PC ... help?"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by absolve on 2009-08-11
I have a machine with 2 physical drives.  I had Fedora installed on one.  I wanted to try Ubuntu, so I installed that on the other.  I was just planning on using the BIOS's boot menu at startup to choose which drive I wanted to boot, but ... ugh ... it's not working out so well.  

After my first Ubuntu install, I couldn't get either installation to boot.  I reinstalled Ubuntu on the same drive, this time choosing the option to install the boot loader on the same disc as the installation.  

So now I can boot up Ubuntu w/no problem.  This would all be fine and dandy except that: 

1)  For some reason, I cannot find/browse the drive containing the Fedora installation in order to get at my files.  

2)  I also *still* cannot boot up the Fedora install.  I believe I get an "error 17."

Advice here?  There once was a time when I knew how to manually change boot files to do anything I wanted them to do, but over these past few years I've forgotten more about Linux than I probably ever knew.  And I can't see any reason why I can't see the drive and files from Ubuntu.  I have a third physical disc in this machine as well, and Ubuntu sees that one just fine.  

Thanks for any advice!  

=abs

---

### Post by host47 on 2009-08-11
In order to look for you Fedora partition, you could try a Live-cd distribution. Google for Knoppix, Slax or another good Live-cd.

For the boot problem, you would repair the original boot loader of the Fedora. Should be easy, but look in the fedora documentation for that.

---

### Post by louieb on 2009-08-11
Fedora 5 was the last one for me. at that time it defaulted to a seperate /boot partition and lvm. 
The instructions say to run this from a live CD but it can be run from you hard drive install.  [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")

If this does not help you get it figured out. please put the results.txt file in your next post.

---

### Post by absolve on 2009-08-11
Well I've figured out how to find and mount the volumes, but as you mentioned there are 2 partitions -- one with the system files and one for storage.  It's the storage drive I need access to, and it's LVM2.  I can't quite get the LVM2 mounted.  I have searched for and found the following instructions on this:  

[http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html)

I can apt-get the lvm2 without a problem, but following that, when I use the 

modprobe dm-mod

command, I get FATAL ERROR: dm_mod not found.  

Weird ... but I think I'm on the right track.  If I could just access my files, I wouldn't care too much about booting up Fedora again.

---

### Post by louieb on 2009-08-11
Haven't use LVM in years and then only a short while. So going to bow out now. but I did find this. 
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

it has one note about your error.
> Load the LVM module - modprobe dm-mod. You can skip this step in Jaunty (9.04) because the dm-mod module is *compiled into* the kernel. 

---

### Post by absolve on 2009-08-12
I wanted to mount the contents of this LVM drive "on the fly" (as opposed to altering fstab)  I found a solution that works here:

[http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html](http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html)

However, apparently permissions are in effect because, even though the filesystem is mounted, I cannot view the contents of certain folders -- for instance, my personal folder in the /home directory.  

Is there a way I can take ownership of that? 

-abs

---

### Post by louieb on 2009-08-12
Ubuntu does not enable root to log in. What you can do is open the file browser with root privileges.

Alt+F2 brings up the run dialog. 

```
gksudo nautilus
```Should be able to get the files this way. 

or get root privileges in a command prompt ```
sudo -i

```
[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by absolve on 2009-08-13
Thanks louieb!  The Nautilus method doesn't work (for some reason, Nautilus won't browse even as far as "Computer" when run that way), but I can find the files in terminal.  I should be able to copy the things I really need that way.  Thanks again!

---

