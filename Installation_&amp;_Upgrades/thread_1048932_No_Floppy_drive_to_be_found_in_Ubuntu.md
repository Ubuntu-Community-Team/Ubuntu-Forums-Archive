---
title: "No Floppy drive to be found in Ubuntu"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by Matt_Rapp on 2009-01-24
I just benchmarked my rig with a Inquisitor live CD and saved the results to a floppy, but I can't acess my floppy drive in Ubuntu. I do not think there is a problem with the drive because it was able to read and write the test results though the live CD and also booted up an old copy of a Windows 98 Rescue Diskette. I've tried running the following commands as root 

root@Matt-Ubuntu-Desktop:~# mount /dev/fd0 /mnt/floppy
mount: mount point /mnt/floppy does not exist
root@Matt-Ubuntu-Desktop:~# mount /dev/fd0
mount: can't find /dev/fd0 in /etc/fstab or /etc/mtab
root@Matt-Ubuntu-Desktop:~# /mnt/floppy
bash: /mnt/floppy: No such file or directory
root@Matt-Ubuntu-Desktop:~# 

Any sugestions to get this drive working?

I am runing Ubuntu 8.10 and the drive is a Nippon Labs ICR-EE All-in-one USB + FDD1.44" Card Reader w/ 3.5" FLOPPY DRIVE that I just ordered from newegg
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820816002]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820816002")

Thanks!

---

### Post by pytheas22 on 2009-01-24
Try this:

```
sudo mkdir /mnt/floppy
sudo mount /dev/fd /mnt/floppy
```

If that doesn't work, try:

```
sudo mount /dev/fd0 /mnt/floppy
```

If that still fails, please post the output of:
```

ls /dev
```

---

### Post by Matt_Rapp on 2009-01-24
No Dice, sorry the text got mushed together. I attached the .txt file but it doesn't seam to be working. 

[http://ubuntuforums.org/attachment.php?attachmentid=100919&stc=1&d=1232819422]("http://ubuntuforums.org/attachment.php?attachmentid=100919&stc=1&d=1232819422")


matt@Matt-Ubuntu-Desktop:~$ sudo mkdir /mnt/floppy
[sudo] password for matt:                         
mkdir: cannot create directory `/mnt/floppy': File exists
matt@Matt-Ubuntu-Desktop:~$ sudo mount /dev/fd /mnt/floppy
mount: /proc/6705/fd is not a block device                
matt@Matt-Ubuntu-Desktop:~$ ls /dev                       
adsp                ptyd9  ptyu0  ram15       tty60  ttyq0  ttyw3
audio               ptyda  ptyu1  ram2        tty61  ttyq1  ttyw4
block               ptydb  ptyu2  ram3        tty62  ttyq2  ttyw5
bus                 ptydc  ptyu3  ram4        tty63  ttyq3  ttyw6
cdrom4              ptydd  ptyu4  ram5        tty7   ttyq4  ttyw7
cdrom5              ptyde  ptyu5  ram6        tty8   ttyq5  ttyw8
cdrw4               ptydf  ptyu6  ram7        tty9   ttyq6  ttyw9
cdrw5               ptye0  ptyu7  ram8        ttya0  ttyq7  ttywa
char                ptye1  ptyu8  ram9        ttya1  ttyq8  ttywb
console             ptye2  ptyu9  random      ttya2  ttyq9  ttywc
core                ptye3  ptyua  rtc         ttya3  ttyqa  ttywd
cpu_dma_latency     ptye4  ptyub  rtc0        ttya4  ttyqb  ttywe
disk                ptye5  ptyuc  scd0        ttya5  ttyqc  ttywf
dsp                 ptye6  ptyud  scd1        ttya6  ttyqd  ttyx0
dvd4                ptye7  ptyue  sda         ttya7  ttyqe  ttyx1
dvd5                ptye8  ptyuf  sdb         ttya8  ttyqf  ttyx2
dvdrw4              ptye9  ptyv0  sdb1        ttya9  ttyr0  ttyx3
fd                  ptyea  ptyv1  sdb2        ttyaa  ttyr1  ttyx4
full                ptyeb  ptyv2  sdb5        ttyab  ttyr2  ttyx5
fuse                ptyec  ptyv3  sdc         ttyac  ttyr3  ttyx6
hidraw0             ptyed  ptyv4  sdc1        ttyad  ttyr4  ttyx7
hpet                ptyee  ptyv5  sdd         ttyae  ttyr5  ttyx8
initctl             ptyef  ptyv6  sde         ttyaf  ttyr6  ttyx9
input               ptyp0  ptyv7  sdf         ttyb0  ttyr7  ttyxa
kmem                ptyp1  ptyv8  sdg         ttyb1  ttyr8  ttyxb
kmsg                ptyp2  ptyv9  sequencer   ttyb2  ttyr9  ttyxc
log                 ptyp3  ptyva  sequencer2  ttyb3  ttyra  ttyxd
loop0               ptyp4  ptyvb  sg0         ttyb4  ttyrb  ttyxe
lp0                 ptyp5  ptyvc  sg1         ttyb5  ttyrc  ttyxf
MAKEDEV             ptyp6  ptyvd  sg2         ttyb6  ttyrd  ttyy0
mem                 ptyp7  ptyve  sg3         ttyb7  ttyre  ttyy1
mixer               ptyp8  ptyvf  sg4         ttyb8  ttyrf  ttyy2
ndiswrapper         ptyp9  ptyw0  sg5         ttyb9  ttys0  ttyy3
net                 ptypa  ptyw1  sg6         ttyba  ttyS0  ttyy4
network_latency     ptypb  ptyw2  sg7         ttybb  ttys1  ttyy5
network_throughput  ptypc  ptyw3  sg8         ttybc  ttyS1  ttyy6
null                ptypd  ptyw4  shm         ttybd  ttys2  ttyy7
nvidia0             ptype  ptyw5  snapshot    ttybe  ttyS2  ttyy8
nvidiactl           ptypf  ptyw6  snd         ttybf  ttys3  ttyy9
oldmem              ptyq0  ptyw7  sndstat     ttyc0  ttyS3  ttyya
parport0            ptyq1  ptyw8  sr0         ttyc1  ttys4  ttyyb
port                ptyq2  ptyw9  sr1         ttyc2  ttys5  ttyyc
ppp                 ptyq3  ptywa  stderr      ttyc3  ttys6  ttyyd
psaux               ptyq4  ptywb  stdin       ttyc4  ttys7  ttyye
ptmx                ptyq5  ptywc  stdout      ttyc5  ttys8  ttyyf
pts                 ptyq6  ptywd  tty         ttyc6  ttys9  ttyz0
ptya0               ptyq7  ptywe  tty0        ttyc7  ttysa  ttyz1
ptya1               ptyq8  ptywf  tty1        ttyc8  ttysb  ttyz2
ptya2               ptyq9  ptyx0  tty10       ttyc9  ttysc  ttyz3
ptya3               ptyqa  ptyx1  tty11       ttyca  ttysd  ttyz4
ptya4               ptyqb  ptyx2  tty12       ttycb  ttyse  ttyz5
ptya5               ptyqc  ptyx3  tty13       ttycc  ttysf  ttyz6
ptya6               ptyqd  ptyx4  tty14       ttycd  ttyt0  ttyz7
ptya7               ptyqe  ptyx5  tty15       ttyce  ttyt1  ttyz8
ptya8               ptyqf  ptyx6  tty16       ttycf  ttyt2  ttyz9
ptya9               ptyr0  ptyx7  tty17       ttyd0  ttyt3  ttyza
ptyaa               ptyr1  ptyx8  tty18       ttyd1  ttyt4  ttyzb
ptyab               ptyr2  ptyx9  tty19       ttyd2  ttyt5  ttyzc
ptyac               ptyr3  ptyxa  tty2        ttyd3  ttyt6  ttyzd
ptyad               ptyr4  ptyxb  tty20       ttyd4  ttyt7  ttyze
ptyae               ptyr5  ptyxc  tty21       ttyd5  ttyt8  ttyzf
ptyaf               ptyr6  ptyxd  tty22       ttyd6  ttyt9  urandom
ptyb0               ptyr7  ptyxe  tty23       ttyd7  ttyta  usbdev1.1_ep00
ptyb1               ptyr8  ptyxf  tty24       ttyd8  ttytb  usbdev1.1_ep81
ptyb2               ptyr9  ptyy0  tty25       ttyd9  ttytc  usbdev1.2_ep00
ptyb3               ptyra  ptyy1  tty26       ttyda  ttytd  usbdev1.2_ep81
ptyb4               ptyrb  ptyy2  tty27       ttydb  ttyte  usbdev2.1_ep00
ptyb5               ptyrc  ptyy3  tty28       ttydc  ttytf  usbdev2.1_ep81
ptyb6               ptyrd  ptyy4  tty29       ttydd  ttyu0  usbdev2.3_ep00
ptyb7               ptyre  ptyy5  tty3        ttyde  ttyu1  usbdev2.3_ep01
ptyb8               ptyrf  ptyy6  tty30       ttydf  ttyu2  usbdev2.3_ep82
ptyb9               ptys0  ptyy7  tty31       ttye0  ttyu3  usbdev3.1_ep00
ptyba               ptys1  ptyy8  tty32       ttye1  ttyu4  usbdev3.1_ep81
ptybb               ptys2  ptyy9  tty33       ttye2  ttyu5  usbdev4.1_ep00
ptybc               ptys3  ptyya  tty34       ttye3  ttyu6  usbdev4.1_ep81
ptybd               ptys4  ptyyb  tty35       ttye4  ttyu7  usbdev5.1_ep00
ptybe               ptys5  ptyyc  tty36       ttye5  ttyu8  usbdev5.1_ep81
ptybf               ptys6  ptyyd  tty37       ttye6  ttyu9  vcs
ptyc0               ptys7  ptyye  tty38       ttye7  ttyua  vcs1
ptyc1               ptys8  ptyyf  tty39       ttye8  ttyub  vcs2
ptyc2               ptys9  ptyz0  tty4        ttye9  ttyuc  vcs3
ptyc3               ptysa  ptyz1  tty40       ttyea  ttyud  vcs4
ptyc4               ptysb  ptyz2  tty41       ttyeb  ttyue  vcs5
ptyc5               ptysc  ptyz3  tty42       ttyec  ttyuf  vcs6
ptyc6               ptysd  ptyz4  tty43       ttyed  ttyv0  vcs7
ptyc7               ptyse  ptyz5  tty44       ttyee  ttyv1  vcs8
ptyc8               ptysf  ptyz6  tty45       ttyef  ttyv2  vcsa
ptyc9               ptyt0  ptyz7  tty46       ttyp0  ttyv3  vcsa1
ptyca               ptyt1  ptyz8  tty47       ttyp1  ttyv4  vcsa2
ptycb               ptyt2  ptyz9  tty48       ttyp2  ttyv5  vcsa3
ptycc               ptyt3  ptyza  tty49       ttyp3  ttyv6  vcsa4
ptycd               ptyt4  ptyzb  tty5        ttyp4  ttyv7  vcsa5
ptyce               ptyt5  ptyzc  tty50       ttyp5  ttyv8  vcsa6
ptycf               ptyt6  ptyzd  tty51       ttyp6  ttyv9  vcsa7
ptyd0               ptyt7  ptyze  tty52       ttyp7  ttyva  vcsa8
ptyd1               ptyt8  ptyzf  tty53       ttyp8  ttyvb  xconsole
ptyd2               ptyt9  ram0   tty54       ttyp9  ttyvc  zero
ptyd3               ptyta  ram1   tty55       ttypa  ttyvd
ptyd4               ptytb  ram10  tty56       ttypb  ttyve
ptyd5               ptytc  ram11  tty57       ttypc  ttyvf
ptyd6               ptytd  ram12  tty58       ttypd  ttyw0
ptyd7               ptyte  ram13  tty59       ttype  ttyw1
ptyd8               ptytf  ram14  tty6        ttypf  ttyw2
matt@Matt-Ubuntu-Desktop:~$

---

### Post by pytheas22 on 2009-01-24
Alright, please give this a try:
```

sudo mkdir /media/floppy-disk
sudo mount /dev/fd /media/floppy-disk
```

This would mount it at /media/floppy-disk.  Any luck?  If not, please post the errors that you get.

---

### Post by Matt_Rapp on 2009-01-24
Okay this is what I got through the terminal

matt@Matt-Ubuntu-Desktop:~$ sudo mkdir /media/floppy-disk
mkdir: cannot create directory `/media/floppy-disk': File exists
matt@Matt-Ubuntu-Desktop:~$ sudo mount /dev/fd /media/floppy-disk
mount: /proc/6293/fd is not a block device
matt@Matt-Ubuntu-Desktop:~$

and when I go to /media/ there is a folder "floppy-disk" that I can open but has nothing on it, I also can not create new files in the folder so the disk itself is not being read as blank.

On a whim I tried to open floppy formatter and I got this error-

"Cannot initialize device

Unable to open any device, formatting cannot continue."

Now what?

---

### Post by pytheas22 on 2009-01-24
hmmm, could you please post the output of:
```

cat /etc/fstab
```

I'm thinking that the solution mentioned [here]("http://ubuntuforums.org/showthread.php?p=6415536") is the next thing to try.

Also, which version of Ubuntu are you using?

---

### Post by Matt_Rapp on 2009-01-24
Terminal

matt@Matt-Ubuntu-Desktop:~$ cat /etc/fstab
proc            /proc           proc    defaults        0       0
UUID=0d0df397-a2cf-4357-b50e-0d0dfcbbe030 /               ext3    relatime,errors=remount-ro 0       1
UUID=c27d2dcb-53be-4242-86ec-efd48cd36408 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
matt@Matt-Ubuntu-Desktop:~$

I'm running 8.10 with all updates installed.

---

### Post by Matt_Rapp on 2009-01-24
I don't know what to do to change fstab like the other user did. You'll have to walk me through the commands.

---

### Post by pytheas22 on 2009-01-24
First, back up your current fstab by typing:
```

cp /etc/fstab ~/Desktop/fstab
```

This will save a copy on your desktop.

Then, open up your fstab file by typing:
```

sudo gedit /etc/fstab
```

Finally, add this line to the bottom:
```

/dev/fd0 /media/floppy-disk rw,user 0 0
```

Save the file and reboot.  Can you mount the floppy now?  If not, try repeating the steps above, but replace the line you added with this line:
```

/dev/fd /media/floppy-disk rw,user 0 0
```

That line contains /dev/fd as opposed to /dev/fd0, which might make a difference.

---

### Post by Matt_Rapp on 2009-01-24
Nothing new happened, the FDD indicator light on the drive doesn't even flash. I rechecked the cable connection and now am going to 1) see if the drive works using that win 98 diskette again and 2) boot from my live 8.10 Ubuntu CD to see if the floppy drive is recognised.

On a some what related note I have a second hard drive called Data that never mounts on its own when I boot the system. If I click on its icon I get a message saying that the mount failed or something, but then the icon changes to a hard drive picture and the drive appears on my desktop. Is there away to make it mount automatically on boot, and could I also switch it out of the removable media area folder some how?

---

### Post by Matt_Rapp on 2009-01-24
Okay here's the scoop.

1) the win 98 diskette booted so the drive is good.

2) A 8.10 Ubuntu Live CD CD did not recognise my floppy drive

3) A Fedora 10 Live CD did find my floppy drive but was unable to mount it, using both the win 98 disk and the diskette with my .txt files from the benchmarking software

If we can not find a solution to this thing for ubuntu, how do I get rid of the /media/floppy-disk directory that does nothing?

---

### Post by pytheas22 on 2009-01-24
I'm still not sure why Ubuntu won't mount the drive.  The only thing I can think of at this point is that the 'floppy' module is not loaded.  Do you have any better luck if you load it by typing:
```

sudo modprobe floppy
```

then try to mount the device?
> 
If we can not find a solution to this thing for ubuntu, how do I get rid of the /media/floppy-disk directory that does nothing? 

Easy, just type:
```

sudo rm -r /media/floppy-disk
```
> 
On a some what related note I have a second hard drive called Data that never mounts on its own when I boot the system. If I click on its icon I get a message saying that the mount failed or something, but then the icon changes to a hard drive picture and the drive appears on my desktop. Is there away to make it mount automatically on boot, and could I also switch it out of the removable media area folder some how? 

You can edit /etc/fstab to auto-mount the drive.  I don't know enough about it personally to be able to tell you what to do, but there's a good guide [here]("http://ubuntuforums.org/showthread.php?t=283131").

Unfortunately I don't know how to take the drive out of the removable-media folder; the closest I can come is editing [Nautilus Bookmarks]("http://ubuntuforums.org/showpost.php?p=2016866&postcount=5").

---

### Post by Matt_Rapp on 2009-01-24
It works, thanks a lot!!!!

One more thing, 

The drive is listed as 1.5 MB Media with a floppy icon, but is actually mapped to /media/disk instead of /media/floppy-disk. Can I delete the /media/floppy-disk directory then without causing problems?

Do you think something was wrong with my live CD's build and that's why I didn't have the floppy module wasn't installed? 

The sudo modprobe floppy command will be permanent, it will not clear out on a reboot, right?

---

### Post by pytheas22 on 2009-01-24
Glad that finally did it...sorry for not thinking of it sooner.
> 
The drive is listed as 1.5 MB Media with a floppy icon, but is actually mapped to /media/disk instead of /media/floppy-disk. Can I delete the /media/floppy-disk directory then without causing problems?

Yes, you can rm /media/floppy-disk

> 
Do you think something was wrong with my live CD's build and that's why I didn't have the floppy module wasn't installed? 

I don't think there's anything wrong with your build.  The floppy module was 'installed' in that it was on your system, it just wasn't activated.  In most cases the system is smart enough to know which modules are needed for attached hardware and will auto-load them at boot time.  But sometimes for various reasons it fails to do that and you have to load the module manually; I guess that's what happened in your case.

> 
The sudo modprobe floppy command will be permanent, it will not clear out on a reboot, right?

No, if you want the floppy module to be loaded permanently, run this command once to add it to your /etc/modules file:
```

echo floppy | sudo tee -a /etc/modules
```

After that, it should be there throughout reboots, because when Ubuntu boots, it looks at the /etc/modules file and loads whichever modules are listed there.

---

### Post by Matt_Rapp on 2009-01-24
Okay I rebooted and it all works great, except floppy formating tools can't find the drive, Floppy Formatter says

"Cannot initialize device

You do not have the proper permissions to write to /dev/floppy/0 or /dev/fd0, formatting will not be possible.
Contact your system administrator about getting write permissions."

---

### Post by pytheas22 on 2009-01-24
> Okay I rebooted and it all works great, except floppy formating tools can't find the drive, Floppy Formatter says

"Cannot initialize device

You do not have the proper permissions to write to /dev/floppy/0 or /dev/fd0, formatting will not be possible.
Contact your system administrator about getting write permissions." 

Probably because only root has permission to write to the device.  Try starting Floppy Formatter as root.  You can do that by opening a terminal and typing:
```

sudo [floppy formatter]
```

where [floppy formatter] represents the name of the executable for the program (I don't know what it is; hopefully you can figure it out; if not, go to System>Preferences>Main Menu and you should be able to figure out which command is actually being run when you launch Floppy Formatter from the Applications menu).

---

### Post by Matt_Rapp on 2009-01-24
Okay, That works. You think that the program, gfloppy, would just ask you for your password.

Thanks for all of your great help today!!!

---

### Post by 1Hobbs1 on 2009-01-25
Ok this is my first post so bear with me.

Great Info on the Ubuntu Forums!

I have a problem with permissions for the folder that was created in the media folder.

The folder/drive is named disk and root/other do not have access to the folder/floppy drive.

I can access the floppy drive just fine.

What I am trying to do is use Virtual Box and I need root/other to access the floppy drive.

MY question is how do I set the permissions for the folder/floppy drive? 

I have tried to right click then permissions and change it, but alas it will not change.

What would be the terminal commands to set the drive permissions so that root/other could have access to the drive.

Any help would be greatly appreciated.

Thank You in advance!:)

---

### Post by pytheas22 on 2009-01-25
1Hobbs1: what is the output of:
```

ls -l /media
```

Also, have you mounted your floppy drive in VirtualBox (see attached screenshot)?

(Ignore the error message in my screenshot; I think it's only there because I don't actually have any floppy disks to mount.)

---

### Post by 1Hobbs1 on 2009-01-25
Hey there  pytheas22

Thanks for the reply!!

here is the output
total 8
lrwxrwxrwx 1 root root    6 2008-11-28 19:57 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-11-28 19:57 cdrom0
drwxr-xr-x 2 root root 4096 2008-11-28 19:57 cdrom1

doesn't look like the /dev/fd0 is in the list. (Not sure how to fix this)

Quote
"Also, have you mounted your floppy drive in VirtualBox (see attached screenshot)?"

Yep made sure that was selected.

It shows PC Floppy Drive (/dev/fd0) in selection box

Thanks again

---

### Post by pytheas22 on 2009-01-25
It doesn't look like the floppy drive is mounted at all.  Please run this command:
```

sudo modprobe floppy
```

Then go to Places>Home Folder.  In the left-side pane you should an entry for the floppy drive.  Left-click on it once to mount it.

After it's mounted, start your virtual machine.  Can Windows access the floppy?

FYI: if you reboot Ubuntu, you will need to type 'sudo modprobe floppy' again in order to mount the disk.  Or run this command once:
```

echo floppy | sudo tee -a /etc/modules
```

and the disk should always be available thereafter in the side-pane of Nautilus.

---

### Post by 1Hobbs1 on 2009-01-25
Sorry I should have stated that I had followed your instructions and had used **sudo modprobe floppy** and echo **floppy | sudo tee -a /etc/modules** then rebooted and tried virtual box selected the floppy and got this error message.

see attached (new to this)

---

### Post by 1Hobbs1 on 2009-01-25
I have mounted the floppy a number of times.

Ok it will be a while before I get back to any reply ie 2-3 hours

Thanks for helping me out here.

what im having to do is install win 95 then upgrade to 98 SE.... hehe

Its what i have so ill try and use it

I am gurbing XP PRO and mainly use Ubuntu Studio 8.10 AMD64

---

### Post by pytheas22 on 2009-01-25
> Sorry I should have stated that I had followed your instructions and had used sudo modprobe floppy and echo floppy | sudo tee -a /etc/modules then rebooted and tried virtual box selected the floppy and got this error message.

Did you mount the floppy in the terminal, or did you do it through the graphical file browser?  If you did it in the terminal, then probably only root has access to it, which explains the problem.  If you mounted it graphically, (I *think*), you should have read/write permissions to the floppy under your normal account.

Otherwise, there's probably some group that you would need to add yourself to in order to have permissions in VirtualBox for the device.  But I'm not sure how to do that.

What you could do is start VirtualBox as root by typing:
```

sudo VirtualBox
```

You will need to set up a new virtual machine (because the other one was made using your normal account, not under root) there and boot to it.  Since you would be running VB as root, you should not have permissions issues with your floppy drive, and should be able to install Windows.

After you finish setting up your VM while running as root, however, you will need to move the virtual disk-image and change the permissions on it in order to open it as a normal user.  But this shouldn't be too hard to do; just pay attention to the location where your virtual disk-image is saved (by default, VB will probably suggest /root/.VirtualBox, I think) when running VB as root so that you can find it again later.  I can help you deal with this once you get this far.

---

### Post by 1Hobbs1 on 2009-01-25
Im back, I took the time to try some permissions tests and non of them worked.

> **pytheas22 said:**
> Did you mount the floppy in the terminal, or did you do it through the graphical file browser?  If you did it in the terminal, then probably only root has access to it, which explains the problem.  If you mounted it graphically, (I *think*), you should have read/write permissions to the floppy under your normal account.

I have been mounting the floppy graphically. Still have not tried it through terminal.

> Otherwise, there's probably some group that you would need to add yourself to in order to have permissions in VirtualBox for the device.  But I'm not sure how to do that.

Yeah I'm not sure how to do that either. :) I did try and play around with the group for VirtualBox and root and my own user to no avail.

> What you could do is start VirtualBox as root by typing:
```

sudo VirtualBox
```

You will need to set up a new virtual machine (because the other one was made using your normal account, not under root) there and boot to it.  Since you would be running VB as root, you should not have permissions issues with your floppy drive, and should be able to install Windows.

After you finish setting up your VM while running as root, however, you will need to move the virtual disk-image and change the permissions on it in order to open it as a normal user.  But this shouldn't be too hard to do; just pay attention to the location where your virtual disk-image is saved (by default, VB will probably suggest /root/.VirtualBox, I think) when running VB as root so that you can find it again later.  I can help you deal with this once you get this far.

I have started VB in root as you suggested and the boot disk started right up!!!!  Thanks a bunch!!

I'll hit you up later for the permission changes... as I believe that running things as root can be a NO NO :D

Thanks for the Help pytheas22 U R AWESOME

---

### Post by Mark Phelps on 2009-01-26
pytheas22: I'm having much the same problems and have already tried everything I read in this thread.

Didn't want to hijack this thread, so I started another one here:

[http://ubuntuforums.org/showthread.php?t=1050192]("http://ubuntuforums.org/showthread.php?t=1050192")

Can you help me there?  thanks.

---

### Post by 1Hobbs1 on 2009-01-26
I should apologize a for taking this topic down a bunny trail and off topic a ways.

Should have started a new thread.

Well I'm all installed and updated to Win 98SE.

Ready to try Moving VB and changing permissions.

If you want we can move this to a new thread pertaining more to VB issues.

Thanks agian!!

---

### Post by pytheas22 on 2009-01-26
1Hobbs1: we might as well continue in this thread; the original poster's problem has already been solved.

Now that you've got your virtual disk image all set, you need first to move it to your regular user's home directory.  To do that, back up your existing .VirtualBox folder first by typing:
```

mv ~/.VirtualBox ~/.VirtualBox-old
```

Then, copy root's .VirtualBox directory into the /home folder of your normal user:
```

sudo cp -R /root/.VirtualBox ~/
```

Next, you should change the ownership of the files by typing:
```

sudo chown -R *your-user-name*\: ~/.VirtualBox
```

(Make sure to replace *your-user-name* with your real user name.)

Now open VirtualBox as your normal user.  If everything worked correctly, you should see the virtual machine that you created as root and be able to start it with no problems.

Please post any error messages as exactly as possible.  If you have problems, please also post the output of:

```
ls -lR ~/.VirtualBox
```

Mark Phelps: I'll reply in your thread.

---

### Post by 1Hobbs1 on 2009-01-27
Ok I've finished the move and permission change.

Virtual Box came up (graphically).

Started my VM and ....

got the same error as before

see attached

[ATTACH]101186[/ATTACH]

So I went into Virtual Box settings and disabled the floppy drive and Viola!

Its Alive!!

Thanks for all of your help pytheas22.

one last little question.

can you chown a drive??

Thanks Again!! WooHoo Learning is FUN! 
-1Hobbs1

---

### Post by pytheas22 on 2009-01-27
I'm glad that worked :)

In the interest of saving disk space, you now might want to delete your .VirtualBox-old and /root/.VirtualBox directories, which you could do by typing:
```

rm -r ~/.VirtualBox-old
sudo rm -r /root/.VirtualBox
```

Or you could just leave them--I don't imagine Windows 98 takes up that much space anyway.
> 
can you chown a drive??

I've never tried, but in principle, since Unix is supposed to treat everything as a file, it would work.  You could try (note that this involves a small amount of risk because I'm not positive what will happen; if you're paranoid, you might want to try it under the live CD first so that it can't permanently damage anything):
```

sudo chown -R username:\ /dev/fd*
```

and see what happens.  My guess is that your floppy drive would default back to root's ownership if you reboot your computer, but I'm not positive.

---

### Post by jimmy_j on 2009-02-08
Hi, I have been using Ubuntu for about a year now and still learning. Whenever I try to mount my floppy drive I get this message:

/proc/16335/fd is not a block device


I am running ubuntu 8.10 and for whatever reason I couldn't even see the drive when I first installed ubuntu. I had to run this command; "sudo modprobe floppy" This created a floppy drive icon but I am not able to mount it. I have created a directory in /media/floppy. Every time I try to mount the drive I get the error message above. Any ideas???

---

### Post by pytheas22 on 2009-02-08
jimmy_j: what is the exact command that you're trying to use to mount the device, and what is the output of:
```

ls /dev | grep fd
ls /media
```

---

### Post by jimmy_j on 2009-02-09
> **pytheas22 said:**
> jimmy_j: what is the exact command that you're trying to use to mount the device, and what is the output of:
```

ls /dev | grep fd
ls /media
```

thanks for replying... i switch to the "su" account and this is what i type.... 

mount /dev/fd /media/floppy  

below is what appears... 

mount: /proc/7131/fd is not a block device
root@linux-desktop://# 


in my dev directory i see "fd" and not "fd0" like others do... any ideas???

---

### Post by jimmy_j on 2009-02-09
the output of these commands

ls /dev | grep fd
ls /media

is: 


root@linux-desktop://# ls /dev | grep fd
fd
fd0
fd0u1040
fd0u1120
fd0u1440
fd0u1600
fd0u1680
fd0u1722
fd0u1743
fd0u1760
fd0u1840
fd0u1920
fd0u360
fd0u720
fd0u800
fd0u820
fd0u830
root@linux-desktop://# ls media
cdrom  cdrom0  disk  disk-1  floppy  Virtual-Drive
root@linux-desktop://#

---

### Post by pytheas22 on 2009-02-09
What happens if you type:
```

sudo mount /dev/fd0 /media/floppy
```

I think it needs to be 'fd0', not just 'fd'.

---

### Post by jimmy_j on 2009-02-09
this is what i get... 

root@linux-desktop://# mount /dev/fd0 /media/floppy
mount: /dev/fd0 is not a valid block device
root@linux-desktop://#

---

### Post by pytheas22 on 2009-02-09
That's strange.  Are you positive that this floppy disk isn't corrupted?  Do you have any other disks you could try?

---

### Post by jimmy_j on 2009-02-09
ya i've tried... anyway thanks for you help...

---

### Post by pytheas22 on 2009-02-09
I'm really out of other ideas.  Everything I found through Google suggests that this message occurs when your floppy disk is bad (or possibly when there's an issue with the drive itself).  I would try accessing the disk in a different operating system, and check the cables connecting it to your motherboard.  I wish I had better advice...

---

### Post by jimmy_j on 2009-02-09
i'll go into my system and check to make sure all is well... maybe i jarred the floppy cable... i'll let you know...

---

### Post by jimmy_j on 2009-02-09
i reseated the floppy cable and it worked.. the drive sounds a little rough though... it may need to be cleaned as it was grinding away... it may be on the brink of failing.... thanks for your help...

---

### Post by Mark Phelps on 2009-02-09
Hey guys, sorry to jump in here, but I had similar problems with my floppy drive, got help here and notice that when I issue the mount command, it always complains -- unless there's a diskette in the drive!

I checked my output of ls /dev | grep fd -- and it exactly matches what is posted here.  My output of ls /media differs in that mine says "floppy0" instead of "floppy".  

My /etc/fstab entry is the following:

/dev/fd0 /media/floppy0  vfat	user,utf8,umask=000 0 0

What I notice, though, is that under Places --> Removable Media, there's an icon for Floppy Drive, and if I insert a diskette and click that icon, the drive lights, the diskette is read, and Nautilus opens with the file list.

So, are you sure it's actually NOT working -- and not just the Mount command complaining?

When I stick a diskette in the drive and do a "sudo mount -a", it does NOT complain; only complains when the drive is empty.

---

### Post by northrup on 2009-12-31
I just went through all the procedures listed here for my floppy drive.  I'm using a TEAC USB floppy drive on Ubuntu 9.10 (via Wubi).

After following the last procedure (creating a directory in /media and adding the line in fstab), the directory I created is non-existent and there is still no floppy recognition.  Also, instead of just an ordinary device file, fd is now a directory.  The contents are mostly socket files, but there are two text files, named 1 and 2 respectively, that contain what seem to be background text output from during startup.

I also noticed this (I sudo'd to make sure it wasn't just a privilege issue):

```
root@ubuntu:~# modprobe floppy
FATAL: Error inserting floppy (/lib/modules/2.6.31-16-generic/kernel/drivers/block/floppy.ko): No such device

```

Could this be a kernel issue?  Maybe floppy support was dropped from the kernel due to a dwindling use?  Or maybe since it's USB, I need to look somewhere else?  My Linux experience is sparse, so maybe I'm missing something...

EDIT: I didn't see that there were more pages... My bad.

---

### Post by pytheas22 on 2010-01-01
northup: so did you sort out your problem after seeing the additional pages of the thread or do you still need help?  If you still need help, please post the output of:
```

ls /dev
sudo modprobe floppy
dmesg | grep floppy
modinfo floppy
```

---

### Post by alexberi on 2011-01-12
Commands output:

aberindei@abeubu64:~$ sudo modprobe floppy
FATAL: Error inserting floppy (/lib/modules/2.6.32-27-generic/kernel/drivers/block/floppy.ko): No such device

aberindei@abeubu64:~$ dmesg | grep floppy
[   22.532522] floppy0: no floppy controllers found
[  131.351034] floppy0: no floppy controllers found

aberindei@abeubu64:~$ modinfo floppy
filename:       /lib/modules/2.6.32-27-generic/kernel/drivers/block/floppy.ko
alias:          block-major-2-*
license:        GPL
author:         Alain L. Knaff
srcversion:     F09EF487AF6BE7153764D10
alias:          acpi*:PNP0700:*
alias:          pnp:dPNP0700*
depends:        
vermagic:       2.6.32-27-generic SMP mod_unload modversions 
parm:           floppy:charp
parm:           FLOPPY_IRQ:int
parm:           FLOPPY_DMA:int
aberindei@abeubu64:~$ sudo modprobe floppy
FATAL: Error inserting floppy (/lib/modules/2.6.32-27-generic/kernel/drivers/block/floppy.ko): No such device

aberindei@abeubu64:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aberindei/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aberindei)

aberindei@abeubu64:~$ ls -l /dev/fd*
lrwxrwxrwx 1 root root 13 2011-01-12 20:28 /dev/fd -> /proc/self/fd

---

### Post by pytheas22 on 2011-01-12
**alexberi**: I'm not sure what's wrong, but the error message you get from the first command about there being "No such device" is interesting.  I googled and the best I could find was this [old thread]("http://forums.gentoo.org/viewtopic.php?t=219849") from the Gentoo forums where someone has the same error message.

The solution there (or at least part of it) was apparently to disable floppy ACPI support.  You can do that on Ubuntu by editing the file /boot/grub/grub.conf and appending the line *floppy=no_acpi* to your kernel entries.  If you don't know what that means and need more specific instructions, let me know.

After making the change, you'll need to reboot for it to take effect.

---

