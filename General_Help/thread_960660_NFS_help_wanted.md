---
title: "NFS help wanted"
date: 2008-10-27
forum: General Help
---

### Post by xeddog on 2008-10-27
Hi all,

I have two machines with Ubuntu installed on them.  All I want to do is share the disk drives between the two machines, and preferably not with SAMBA.  I have a couple of applications that don't seem to be able to access SAMBA shares, and I am hoping that NFS may help.  

I have looked for a solution in these forums and on the internet, but all I have found is either too complicated, or too old (2 to 3 years).  Maybe I am not using the correct search arguments, but I just have not found a solution.  Machine 1 also has a "problem" with a local disk drive.

So here goes.  Machine 1 has two internal disk drives installed in it.  sda has Ubuntu Hardy installed, and sdb has Ubuntu Intrepid RC-1 installed (both are desktop).  The "problem" I mentioned is when I boot the machine into the Intrepid install on sdb, the first disk (sda) shows up in "Removable Media" instead of being a "Place".  That does not seem to be a major issue but may have a bearing.  Also, it does not automount.  This machine also has an external USB disk drive that remains attached, as well as another USB disk drive that I am frequently adding and unmounting.  These two USB disk drives DO automount.

Machine 2 has only a single internal disk drive installed and has Ubuntu Intrepid RC-1 desktop installed on it too.  

What I would like to do is have all four of the disk drives on machine 1 available to machine 2 at boot, and the single disk on machine 2 available to machine 1.  It seems to me that this should be more or less automatic with linux, or at least easy peasy.  Isn't this one of the things that Linux was born for?  

Here are my basic questions:

1.  Is there a fix to the problem on machine 1 of having an internal disk shown as removable and have it automount?
2.  Is there an easy way to have all disks shared automatically when they become available?
3.  This may be answered with #2, but is there a way to have the USB disk drive automatically mount on both systems when it is connected to machine 1 after both machines are already up and running?
4.  Am I wasting my time trying to get nfs working?  If my applications still won't access anything other than the local disk, then all this may be moot anyway.

TIA,

xeddog




Anyway, is there an easy way to have all of the disk drives automounted on both systems when the machines boot?

---

### Post by xeddog on 2008-10-30
I have been making some great progress with nfs.  I have it working between my two Ubuntu machine, but still have one problem on XP.

I got it working on Ubuntu by following this thread:  [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

This made it easy to implement nfs between Ubuntu machines and it DID fix the issue I had with applications not being able to access SAMBA shares.  Two of the applications that come to mind are Pitivi and Rhythmbox.  They were not able to access the SAMBA shares but have no problem at all with NFS shares.  Sweet.  Do a search of the forums and you can also find a script that will keep checking machines and mount the nfs shares when they become available.  As it is now, If machine 1 has a nfs share on machine 2 mounted, and machine 2 is rebooted or ???, then the share is not remounted on machine 1 when machine 2 comes back up.

As for XP, I went to the Microsoft website and downloaded Windows Services for Unix Version 3.5.  After installing it, I am able to map a "drive" to a Linux nfs share, but I have not been able to resolve a problem with permissions yet.  I am sure it is because the windows userid and the linux userid are not the same and of course will have different uids.  Also not sure if I am going to pursue this problem for a while since I don't do a lot of transfer between XP and Linux any more.  SAMBA may just be ok for that.

xeddog

---

### Post by fragos on 2008-10-31
I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. On the server there must be an /etc/exports with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree. This scheme works with any mix of 8.04 and 8.10. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

This allows the Desktop to access the home folder of the laptop. Prior to Ubuntu 8.04 you need to run "sudo exportfs -rv" for the system to read /etc/exports. New versions do this for you at boot.

On the Desktop create a folder to mount to. In my case I placed that folder in my home folder.

On the Desktop side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

---

