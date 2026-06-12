---
title: "How to mount a network drive on ubuntu 9.10?"
date: 2009-11-07
forum: Hardware
---

### Post by Ryan8524 on 2009-11-07
Hey guys,

As you all know, 9.10 came out the other day.

So I was wanting to mount a network drive like windows.

I found that this guide is a help: 
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

But I heard that was only for 9.04.

So does anyone have an idea how to mount a network drive for me?

And even if that guide does work with the new ubuntu, can someone please simplify for me... Its somewhat hard to understand.

Thanks!

---

### Post by shocksafe on 2009-11-07
It's pretty easy.

Go to your windows machine and bring up a terminal (Windows key + r and type cmd, hit enter)
Type ipconfig at the prompt.  Note ipaddress. I'll use one of mine as an example which is 10.1.1.3
If it's going to be permenent you will want to set up a static ip for the windows machine (google it, plenty good guides on that)

Go to ubuntu machine.
open terminal and type 

# smbclient -L //10.1.1.3 (insert your windows machine ip instead)

This shows a list of shared directories on that machine.

Now make a dir for the mount where ever you like eg 

#sudo mkdir /media/my_windows_box

Now test to see if you have all the info right.

#sudo mount -t cifs -o username=windows_username, password=windows_password //10.1.1.3/windows_share_name /media/my_windows_box

#ls /media/mywindowsbox            

That should have the contents of the windows directory.

Then to mount at everyboot 

#sudo gedit /etc/fstab

add line at bottom like this -
//10.1.1.3/windows_share_name    /media/my_windows_box    cifs    username=windows user_name, password=windows_password    0    0

save and exit and done

---

### Post by Ryan8524 on 2009-11-09
On the first instruction, where do i add my windows ip adress?

---

### Post by shocksafe on 2009-11-09
Where ever I've put 10.1.1.3 you need to remove that and put in the ip for you windows machine.

So if your windows machine ip is 192.168.0.4 you would put

# smbclient -L //192.168.0.4

---

### Post by WallaceTech on 2010-01-30
Hi guys.

I am trying to get this up and running and running into a slight snag. I have created the directory ok, but when i run the command below i get the following message. I am not Linux guy by default and i am coming from the Windows world. 

Any ideas where i am going wrong?

I am running 64bit 9.10 Ubuntu

Thanks in advance

htc@HTC:~$ sudo mount -t cifs -o username=USERNAME HERE, password=PASSWORD HERE //LISA/Films /media/my_windows_box
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by WallaceTech on 2010-01-30
Oh and here is what i am trying to map to. There is nothing secret here so dont mind posting it.


htc@HTC:~$ smbclient -L //LISA
Enter htc's password: 
Domain=[WALLACETECH] OS=[Unix] Server=[Samba 3.0.10]

    Sharename       Type      Comment
    ---------       ----      -------
    config          Disk      config
    Public          Disk      Public
    Films           Disk      Films
    TV              Disk      TV
    Music           Disk      Music
    Photos          Disk      Photos
    pollyand scooby Disk      pollyand scooby
    Gary Scotton    Disk      Gary Scotton
    IPC$            IPC       IPC Service (Maxtor Shared Storage)
    ADMIN$          IPC       IPC Service (Maxtor Shared Storage)
Domain=[WALLACETECH] OS=[Unix] Server=[Samba 3.0.10]

    Server               Comment
    ---------            -------
    LISA                 Maxtor Shared Storage
    SKINNER              

    Workgroup            Master
    ---------            -------
    WALLACETECH          SKINNER

---

### Post by garvinrick4 on 2010-01-30
You can set up a Workgroup on windows machines and samba on lunix installs and will be
able to see all devices over network. Drives,printers,USB devices,router
and on each machine in Places you have all partitions on that computer. Make sure you
share everything you want access to. Will come up as icon in Linux as Icon Windows network
and when clicked it will go to Workgroup and in their resides all your devices across the network. Kind of does itself really I have
a dual boot Vista/Karmic on desktop with USB backup drive and USB printer and router and triple boot with 7/karmic/lucid on
laptop with wifi and it all see's each other. Nothing fancy just settings.

---

### Post by racerxd on 2010-03-11
I am trying to mount a drive on my router.  I have a linksys wifi router with a media port.  I have it set up on my drive but how do i mount it?

---

### Post by Dhrystone on 2010-03-30
I'm also trying to mount a Windows shared drive, and keep getting a message saying, "Please make sure the Samba service is marked as Trusted in your firewall settings."

I've checked System>Administration, but do not show a "Firewall" section.

I think this setting may be why I'm not showing my Windows network or any Windows network printers.

Anyone have an idea what I'm doing wrong? The shared folder seemed to almost attach itself before, but somehow mysteriously disappeared from my laptop, which is a Dell Inspiron 1525 with 4GB of RAM. I'm running Ubuntu 9.10 32-bit.

Thanks!

---

### Post by ac4rb on 2013-04-19
I can't understand why Ubuntu and other Linux distros make this so hard and command line specific. Have any of you ever tried the now unsupported Xandros 4.X?
None of this was used, all you had to do to use the complete drive was to right click on the drive and set it up for shareing. When you went to the other network computer (windows or Linux), you could access the entire drive. Setup was a snap including file and print shareing with no command line setup. I would still be using Xandros if they still supported it. I even purchased the professional version and it was worth every penny. I used it until the support and updates stoped. It is still on one of my old laptops and I loved it. All I have been able to share on Ubuntu is files. I did make a directory and placed most of a drive on it and got it to work, but never a complete drive.

---

### Post by QIII on 2013-04-19
Please do not respond to such old threads.  Thank you.

Thread closed.

---

