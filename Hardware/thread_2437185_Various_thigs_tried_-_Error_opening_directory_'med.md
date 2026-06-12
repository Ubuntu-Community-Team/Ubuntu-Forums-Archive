---
title: "Various thigs tried - Error opening directory '/media': Permission denied"
date: 2020-02-19
forum: Hardware
---

### Post by freedex on 2020-02-19
I want to open files from a separate partition, usually accessed through /media in programs like Chromium or Inkspace.[I] [edited out: I also want to be able to open my root folder.]
[/I]
I get this error: Error opening directory '/media': Permission denied

I have tried:

 
[LIST]
[*]gksudo nautilus (Terminal sat there and did not give me a command prompt or any other sign it still was alive) 
[*]sudo chown user:user /media (tried changing user:user to user:[my user name], [my user name]:user, and [my user name]:[my user name]:[my user name]. All things gave me various error messages) 
[*]Change permission in the file explorer (nothing happened) 
[/LIST]
 
I noticed that in the media folder there is a folder named [my user name]. It has a lock icon like on my root folder, which I also can't access. The permissions say the owner is root.


[LIST]
[*]The hard drive I am trying to acess is FAT32 and seen as detachable media 
[*]error: Error opening directory '/media': Permission denied 
[*]Macbook Pro Mid 2009 15 inch 
[*]2.53 GHz Intel Core 2 Duo 
[*]8GB 1067 MHz DDR3 
[*]El Capitan 10.11.6 partition 
[*]Ubuntu 16.04 partition 
[*]58 GB FAT32 partition 
[*]NOT USING BOOT CAMP 
[/LIST]

---

### Post by yancek on 2020-02-19
Ubuntu uses the /media/user directory as a mount point for external media such as flash drive or external drives.  Do you have a sub-directory or directories at that location?  I would not try to change ownership of /media, sub-directories under your user name would not be a problem.  What type files are you trying to access with Chromium and Inkscape.  You should be able to access /media/user as a normal user but not to write to in all likelihood.  Doubt that is the problem though.

Ubuntu like all Linux systems is designed as a multi-user system and the /root directory is not accessible to a normal user.

If you tried to change ownership and got errors, you need to post the actual command and the output, the errors you got.  I wouldn't think there would be any problem accessing a FAT32 filesystem but I don't know what you are trying to do in the software you mention.

---

### Post by TheFu on 2020-02-19
Non-native file systems don't support Unix permissions.  

The only way userid, groupid and permissions can be set is through mount options.  Once mounted, the only way to modify them is to umount the storage and remount with different options.  To see the mount options, run the **mount** command without any options and find the line for the portable media.
```
$ mount |grep **vfat**
/dev/sdb1 on /media/tf/32G-PATRIOT type **vfat** (rw,nosuid,nodev,relatime,**uid=1000,gid=1000**,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
```
that's for a FAT32 32G flash drive.  The uid/gid are critical and must match the output from the **id** command. This should be automatic. If not, something isn't working normally.

Recent Ubuntu releases have included a new package system called snaps.  Snaps add many more constraints, like where on the file system the package/program can access.  Chromium is one of these "snap" packages and by default it can only access the user's HOME directory.  If the snap package maintainer chooses, access to files under /media and /mnt can be requested.  This is for higher security for high risk programs like a web browser.
[https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022](https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022)
# Hook up snaps to access removable-media
    # snapd v2.36+.
```
snap connect chromium:removable-media
```
[https://snapcraft.io/docs/removable-media-interface](https://snapcraft.io/docs/removable-media-interface)
That's an example only for the chromium snap package. Other snaps may or may not allow the "snap connect" to removable-media. The team who creates the snap package decides which connect options are supported.

Moving on ... 
Running any file manager, like nautilus, caja, thunar and others, with elevated permissions can cause all sorts of issues.
Similarly, changing permissions for directories outside of the user's HOME is a common way to break any Unix system. There isn't any script that will fix the permissions on the system files. A reinstall is almost always required, if excellent backups aren't made in advance. For any Unix-like system, backups must include user, group, permissions and ACLs.  Just copying files off is **not a sufficient backup**.

I don't know if nautilus is a snap package or not.  Check using **snap list**

What is **my root folder**? This is ambiguous.  /root?  /?  or $HOME?

---

### Post by freedex on 2020-02-21
> **TheFu said:**
> that's for a FAT32 32G flash drive.  The uid/gid are critical and must match the output from the **id** command. This should be automatic.


My output from the **id** command is uid=1000(compy) gid=1000(compy)

Does this change the command I should use from your first code box?

> **TheFu said:**
>  I don't know if nautilus is a snap package or not.  Check using **snap list**

From what you said, nautilus isn't a command and I thought it was. I am guessing I would have needed to type inkspace, chromium, or whichever program where it said nautilus.

**snap list** shows me that chromium, inkspace, libre office, skype, and vlc are in the list. I know chromium, inkspace, and libre office are programs that will not let me save files. Because of that, I am assuming snaps are the problem.

Can I use just the commands below and be able to open and save files from my removeable hard drive? 

Or do I need to do the **$ mount ...** command you have at the top of your reply first?
If not, is there a use to doing that I don't realize because I know little about these things? I mostly don't want to brick my computer.

**Chromium**
```


snap connect chromium:removable-media


```

**Other programs**
```


sudo apt update
sudo apt install [program]
sudo snap remove [program]


```


From what I have read from you two, I do not need to get into my /root folder, so I am not going to touch that. No way. I am just good enough with Linux to break stuff.

---

### Post by TheFu on 2020-02-21
> **freedex said:**
> From what I have read from you two, I do not need to get into my /root folder, so I am not going to touch that. No way. I am just good enough with Linux to break stuff.

/root/ isn't important. It is just the HOME directory for the "root" account.  It is only important if you put stuff into it.  I put some configuration information there to be included in backups, but pretty much nothing else.

/  <---- the file system root **is** important.  Don't screw with it. That goes for any child directories under it too. 

nautilus is a GUI program. That is a command too.  In most of the world "command" == "program"

You shouldn't copy/paste any commands provided by me or anyone else until you understand the command, all the options and what will happen when the command + options are run.  As Ricky would say to Lucy - "you got some learnin' to do, Lucy!"
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has a free, no hassle, PDF book that should explain the commands well enough. If not, there are always manpages on your system for the specific version of the command on-your-system.  Google results are for some variant of the command, which could be close enough or not to the actual version on your box.  If you want to learn about the mount command
```
$ man mount
```

---

### Post by TheFu on 2020-02-21
> **freedex said:**
>  
**snap list** shows me that chromium, inkspace, libre office, skype, and vlc are in the list. I know chromium, inkspace, and libre office are programs that will not let me save files. Because of that, I am assuming snaps are the problem.

Can I use just the commands below and be able to open and save files from my removeable hard drive? 


snaps are packages outside the normal APT package management system.  The names of programs and packages for those programs often match, but not always.  For some APT packages, Canonical has decided to have the APT package setup and load the snap package instead.  If you are happy with snaps, the security constraints, and auto-update (while retaining 3 package versions, that snaps do, great.  OTOH, if you have a system with 16G of storage, 2G of RAM, and snaps are 500MB-1GB in size, then loading just a few programs will prevent any room for data on the storage.

Snaps that can save data and open data should always be able to read and write to the HOME directory of the userid running the snap program.  It is only when trying to read/write data mounted elsewhere that the removable-media snap connection could be useful.  Sadly, not all snap packagers enable removable-media to be used and today, we can forget about accessing storage mounted outside the two (/mnt/ and /media/) directories by any snap, period.  To me, that is a 32TB design flaw which impacts about 15 systems.  Their choice of /mnt/ and /media/ as the only places shows extreme short-sightedness as well.  The design for snaps originally was for an Ubuntu phone/tablet, so the constraints there made more sense.

Also, you might find that the only packages provided for some of your favorite programs are snaps.  Since 19.04, the chromium browser is not available as a normal APT package anymore.  I still use 16.04 on my desktops, so chromium as a snap is an option, not the only option.

So on a limited system, all data has to go onto USB devices because the snaps took all the main storage, but the project team for the snap package may not have allowed the removable-media option to be used.  Wonder if they'd considered that?  I have a few chromebooks, currently running ubuntu.  I'm worried that 20.04 won't be viable due to required use of snap packages.

There are some great things about snaps too. Everything isn't all bad, but we notice the bad things first.

---

### Post by freedex on 2020-02-24
I think I may have misunderstood how my system is set up.

I input **snap connect chromium:removable-media** to test what that would do as I use Chromium very little (because of this problem).

Nothing changed.

Perhaps my system sees this drive as a second internal hard drive for this?

It  is a partition on my hard drive so Ubuntu and IOS can both see and edit  files. I have had to treat it like a removable hard drive before so I  might have got it wrong again this time.

---

### Post by him610 on 2020-02-24
> What is my root folder? This is ambiguous. /root? /? or $HOME?
Yeah, I always wondered about that phrase, as well as, *root partition* and *root drive*

---

### Post by TheFu on 2020-02-24
To see what, where and how storage is mounted,  
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
any lines with "fuse" will be slower.

To see how connected disks, not necessarily mounted, are laid out, 
```
lsblk -o name,size,type,fstype,mountpoint
```

chromium is a browser. It can't open local files without specific options. They made this the default about 5 yrs ago.  The command line I have to use to allow opening local files is:
```
chromium-browser --allow-file-access-from-files
```
Google, the primary developers of chromium, really doesn't like for their sheeple to access local files, local media. They consider it a security risk.  They are not wrong.

Include that chromium-browser is being packaged as a snap, with more constraints, and those added constraints can get in the way.

---

### Post by freedex on 2020-03-12
Somehow I missed this reply.

Thanks for the help. It seems to have worked.

Do  you know of a good resource to learn more about how Linux works?  Preferably something a little kid would like, because I get bored and go  stare into space

---

