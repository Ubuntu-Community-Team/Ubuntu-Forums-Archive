---
title: "Please help! Can't install files I downloaded."
date: 2008-07-17
forum: General Help
---

### Post by rmjohnson144 on 2008-07-17
Sorry for the newbish question, but search was no help.  I have a little experience with Linux a few years ago when I bought Red Hat.  It has a RPM files for more automated installs and ubuntu doesn't seem to support it.  so now I am having difficulties installing files I've downloaded.  

First I tried installing flashplayer and it took me to the Adobe site and offered me an x86 Linux version and it just vanished when I tried installing it without any error messages.  Couldn't find a x64 version for linux.

second.  I tried to install uTorrent and it seems to think it's an archive as it says wrong file type or some such.  I checked its properties and it is set to be executable.  Does it need special setup?  Does it need to be in a certain folder(/bin)?

Any help would be greatly appreciated.
-=Mark=-

---

### Post by Viper666 on 2008-07-17
> I tried to install uTorrent and it seems to think it's an archive as it says wrong file type or some such. I checked its properties and it is set to be executable. Does it need special setup?
Ubuntu can't read/use any Windows executable files without [Wine]("http://www.winehq.org/")
About the flashplayer i'm not sure what happened but u have a good flash plugin in the repository's "flash-nonfree" which also works with Firefox

Sidenote: uTorrent works great in Wine but why not use the default Transmission client or Azureus?

---

### Post by Ataris on 2008-07-17
Is it a .bin file? This instruction set is from a self-extracting (executable?) Java .bin file. Just modify it to suit your situation.

At the terminal: Type:
su 
Enter the root password. 
Change to the directory in which you want to install. Type:
cd <directory path name>
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java/

Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions. 
Change the permission of the file you downloaded to be executable. Type:
chmod a+x jre-6u<version>-linux-i586.bin 
Verify that you have permission to execute the file. Type:
ls -l 

Start the installation process.Type:
./jre-6u<version>-linux-i586.bin

For any future readers, there is a much easier way:
```
cd *the directory you placed the .bin file*
chmod +x *file*.bin
./*file*.bin
```
And that's it.

---

### Post by dracayr on 2008-07-17
First. [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) should give you the option to download as .tar.gz (in the dropdown menu). .tar.gz is an archive. extract and then double-click flashplayer-installer

Second. your uTorrent file is probably an archive containing the source code. actually, you don't need a Torrent client, as ubuntu has deluge...

dracayr

---

### Post by Yannick Le Saint kyncani on 2008-07-17
Flash is available either as flashplugin-nonfree (which is proprietary) or mozilla-plugin-gnash (which is free but won't work so well).

As for torrents, i believe transmission is the latest popular application.

When you want to install programs in ubuntu, just fire synaptic package manager. It will install programs that already packaged for ubuntu. It has a search tool builtin also.

---

### Post by rmjohnson144 on 2008-07-17
wow, thanks for such quick responses.  I went and installed Vista Ultimate x64 on my RAID 5 partition while waiting for responses.  I guess I didn't need to wait.

ok, first I downloaded the Linux version of uTorrent.  It came as an exe file.  Maybe I misclicked and got the wrong version.  Maybe I'll try to find the torrent program in ubuntu.  I didn't see one at first so I'll try again.  I'll see if I can track down the Synaptic Package Manager.  That sounds exactly what I've been looking for.


Thanks for the reminders Ataris.  I completely forgot about su and manually installing things.  I'm sure that little tidbit will get me through a lot in the near future.

Thanks everyone for the great help.
-=Mark=-

---

### Post by jonian_g on 2008-07-17
Try Deluge, it's in the repositories (Synaptic, Add/Remove). It will remind you uTorrent, but in my opinion is a lot better.

---

### Post by Vivaldi Gloria on 2008-07-17
Welcome to ubuntu. The linux way of installing things is very different. You use synaptic to install programs. It's in the top panel, system menu > admin.

Start synaptic, enable restricted and multiverse repositories from the repository settings. Then click refresh. Then search & install whatever you want in synaptic.

If synaptic doesn't have what you want only then consider downloading from the net.

The corresponding format of an rpm file is deb in ubuntu btw. You can download a deb file and double click on it to install it.

---

### Post by Sef on 2008-07-17
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by rmjohnson144 on 2008-07-23
Thanks agaian for all your help.  so far I've been able to install everything I need through synaptic.

-=Mark=-

---

