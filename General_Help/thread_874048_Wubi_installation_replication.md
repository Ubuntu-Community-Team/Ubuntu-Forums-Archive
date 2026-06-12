---
title: "Wubi installation replication"
date: 2008-07-29
forum: General Help
---

### Post by ricardo.mireles on 2008-07-29
Does anyone have experience with mass replication of a Wubi/Ubuntu installation? 

I have installed Wubi with Hardy Heron on 2 laptops. I need to install on 23 others. They are all the same: Sony Vaio VGN-BX760 with Windows Vista Business. This project is for a small school which received the laptops as a donation.

I would like to remove as much of the individual installation/configuration steps as possible. The idea is that all of the "post-installation" configuration/customization (e.g. additional software installation, plugins, preference, sysadmin account, etc.) could be easily duplicated.

One idea I am seeking others' experience for is the use a "ghost" image of a "template" laptop to apply to the others. Using Windows ghost tools, even the windows configuration/customization could be replicated.

Alternative, could just the Wubi/Ubuntu installation be copied?

---

### Post by jnw222 on 2008-07-29
the wubi install or the whole thing

if the whole thing (inclub=ding vista and all files and configurations)use partimage (on gparted livecd)

for wubi itself try coping the wubi folder and bootloader files (i have never tried it

---

### Post by ricardo.mireles on 2008-07-30
I will experiment with both:

A. Full hard disk image copies via partimage/gparted 
-- this will allow replication of the Windows software set-up as well, but not sure how the licensing issues will play out

B. Ubuntu only replication via Wubi folder copy + bootloader copy 
-- stills means I need to individually configure the Windows side, but its still a savings.

I was just hoping this post would provide some initial experience based tips/guidance.

For example, how would the copied bootloader know how to find the linux image?

---

### Post by minhmeoke on 2008-07-30
Wubi is really intended only to be a demo of ubuntu's capabilities, due to the limitations of the loopmounted filesystem; if you are doing a widescale deployment, you should consider installing to a dedicated partition. The easiest way to do this would building a customized iso, then netbooting off a tftp server, see [http://en.wikipedia.org/wiki/Network_booting](http://en.wikipedia.org/wiki/Network_booting) for details.


If you still want to use the wubi approach though, one way to do this would be to create a reference installation on one computer, and make a the list of the required/installed packages, for example with
```
dpkg --get-selections > /backup/installed-software.log
```

Then download the ubuntu 8.04 iso and all packages in the list (they can also be found at /var/cache/apt/archives on the reference installation) to a local server, distribute the iso to each computer via local network, and run wubi.exe to install the default ubuntu desktop to the loopmounted filesystem. Next restore the package list
```
dpkg --set-selections < /backup/installed-software.log
dselect
```
and you can now install all packages from the local server.

Edit: Copying the wubi folder itself and editing the vista boot menu with EasyBCD should also work if all the computers have exactly the same hardware, although I have never tried this. If you put the virtual disks to the same location on all the computers, ie c:\wubi, then the copied bootloader should be able to detect it.

---

### Post by ago on 2008-07-30
> **minhmeoke said:**
> Wubi is really intended only to be a demo of ubuntu's capabilities, due to the limitations of the loopmounted filesystem; if you are doing a widescale deployment, you should consider installing to a dedicated partition. The easiest way to do this would building a customized iso, then netbooting off a tftp server, see [http://en.wikipedia.org/wiki/Network_booting](http://en.wikipedia.org/wiki/Network_booting) for details.

I second that. Both statements. For long term deployment do an installation to a dedicated partition. Network booting is the way to go here. Once one machine is setup as an installation "server" all you have to do is connect the machines on the same LAN and boot them up selecting network booting in the BIOS. Then the installation server will instruct the machines on what to do and the installation will proceed automatically. Also note that for schools, the edubuntu project is more appropriate for several reasons, see 

[http://edubuntu.org/](http://edubuntu.org/)

If you want to install with Wubi anyway

1)  If the hardware is all the same, you can install on one golden machine, reboot and finish off the Linux side installer. Then configure at will and install any extra package (edubuntu!!!). 

2) You need to edit C:\ubuntu\disks\boot\menu.lst and change the "root=UUID..." -> "root=/dev/sda1" (sda1 means disk 1=a, partition 1, change as appropriate). Since the UUID notation is not portable, while the /dev/sda notation is (with some caveats, but assuming you install in the same partition on identical notebooks it will be ok)

3) Copy the c:\ubuntu folder on all the other machines

4) Copy  c:\ubuntu\winboot\wubildr* to c:\

5) You will have to modify manually the Windows bootloader. You can use EasyBCD for Vista, pointing to C:\wubildr.mbr (#4). Note that wubi contains a command line tool to edit the Vista bootloader which of course can be scripted (when you install wubi in windows the content gets unpacked in your user temp folder, there is a wubibcd.exe in the plugins folder).


If the machines are not identical and you want to use Wubi, the procedure is the same as above except that you need to copy the c:\ubuntu folder BEFORE doing the linux-side installation on the golden machine (#1 and possibly #2). It would be wise to generate the c:\ubuntu\disks\*.disk files in a script (they are just large empty files) as opposed to copying them over as in the non-identical-hardware case, they need to be vergin so that the linux-side installation can be performed on each machine, and moving large empty files is a waste of bandwidth.

Of course you might just as well copy the ISO and wubi.exe in the same folder on each machine and run wubi.exe manually. In the future I will make it take optional parameters so that it can be run in scripts.

---

