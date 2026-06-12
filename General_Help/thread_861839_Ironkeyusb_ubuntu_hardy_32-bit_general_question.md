---
title: "Ironkey/usb ubuntu hardy 32-bit general question"
date: 2008-07-17
forum: General Help
---

### Post by studunn on 2008-07-17
i am trying to run a device called the ironkey - a secure password protected thumbdrive - on ubuntu 32 bit. the problem is that i can only access the drives unlocker as the root user. i need to access the drive as the main user... i think it is a simple permission problem but given the nature of the device i am having trouble establishing the proper permission for the regular user. when i try to run the usb drive i get the following error:

sh: cannot create /proc/scsi/device_info: Permission denied
unable to add IronKey entry to /proc/scsi/device_info
please try re-running as root
Hit return to exit

does anyone know how i can enable permission and get the device running?

---

### Post by Rocket2DMn on 2008-07-17
Are you mounting it manually with the "mount" command?  You can use options with it like uid=1000
```
sudo mount <device> <mount point> -t <filesystem> -o <options>
```
Where <options> can be something like
```
uid=1000,umask=007
```

---

### Post by studunn on 2008-07-17
it mounts automatically, i just can run it. i am trying to run it from a command icon. could you be a little more specific... also how would i find the name of the device? it isn't 'ironkey' when i tried to mount it manually it said the location '/media/IronKey/linux' did not exist...

to give you a little more info the device mounts as a cd. so ubuntu read it as a cd and shows the files that are available when the drive is locked. i can not get the unlocker to work, wich is located at the above directory.

---

### Post by bodhi.zazen on 2008-07-17
You will need to do this in several steps.

First plug in the device.

Open a terminal and enter "ironkey"

Enter your password.

The device, ie crypt, is now unlocked, but needs to be mounted.

First make a mount point :

```
sudo mkdir /media/ironkey
```

Then mount it. mounting depends on the file system though.

To identify the device enter :

```
sudo fdisk -l
```

Or by UUID

```
sudo blkid
```

then 

sudo mount <device> /media/ironkey

<device> will be something like /dev/sda1

Or you can mount by uuid.

To be able to mount the device as a non-root user you need an entry in fstab. Setting permissions depends on the file system.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by studunn on 2008-07-17
When I plug in the device it auto reads the cd and opens the displayable files.

When I type ironkey in the terminal it says command not found. I'm going to try fstab.

also bodhi.zazen you seem to be quite the expert. can I please refer you to another post of mine on an issue I need help.

[http://ubuntuforums.org/showthread.php?p=5404854#post5404854](http://ubuntuforums.org/showthread.php?p=5404854#post5404854)

---

### Post by joshtheitguy on 2008-11-12
I figured out what is going on with the Ironkey command. 

For whatever reason when trying to execute "ironkey" from /media/Ironkey/linux you cannot use sudo to issue the command, it will return a command not found.
If you use su then run the application from root it works perfectly and Kubuntu will automatically map the secure storage area.

---

### Post by dmflad on 2009-02-07
Been using my IronKey between Ubuntu, WinXP and occasionally Red Hat.

Recently did fresh install of Hardy and key was recognised by the system without problem, the IronKey circle logo just appears on screen when I plug it in. 

To be able to open/use it I made a launcher
  -right click on upper screen toolbar | Add to Panel | Custom Application Launcher
  - In the Create Launcher window I entered
    - Type : Application in Terminal
    - Name : IronKey
    - Command: sudo /media/IronKey/linux/ironkey
    - Comment: Start IronKey
    - and I picked an icon I liked

Now I have a "button" for my IronKey in my tool bar and all I do to use my IK is click on the "button"
  - a Terminal window pops up with this: 
  ... [sudo] password for dmflad:
    I enter my password for my laptop and press enter key
  - a second Terminal window labeled "IronKey Unlock" appears with this:
  ... Enter your IronKey password:
    I enter my IronKey password and press enter. Password is "shown" as asterics
  - A File Browser window opens. Its labeled "IronKey USB - File Browser". I can now see and get to all the stuff I keep in my IK.

Because I switch between PCs, LTs, and servers I do not use any of the Win-based tools that come with the IK but I really wanted password storage that moved with me. So...

- I store copies of the KeePass/KeePassX software on my IK in case I need it and am off the grid.  
- I copied my KeePass database (.kdb) from my WinXP PC to my IK and made sure I could open it and use it from the IK using the software on the PC. Once I was sure about that I removed the .kdb from my WinXP PC. 
- Then I installed KeePassX on my Ubuntu LT and made sure it would run and use the .kdb on my IK.
Now I have only one password collection on my IK, it rides along with me, and no worries about having out-of-sync copies on various machines.

Now if FireFox or some other standard compliant,cross-browser web browser could run directly (and only) from my IK I'd be a really happy SysAdmin!

---

### Post by champagj on 2009-04-14
dmflad,

I used an IronKey in a similar fashion.

I created a directory on the secured drive as :"firefoxProfile"

From any host machine via terminal (you have to do this once per machine)
- firefox --profilemanager

in the GUI you can now create a new profile (on the secured drive) which will contain all cookies, bookmarks cache  etc..

One word of caution: do not hot unplug the drive while the browser is open: not good..

---

