---
title: "How To: Getting a Dell Inspiron 1521 to Suspend/Hibernate Properly"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by heypete on 2008-03-04
Evidently I'm [not the only person]("http://ubuntuforums.org/showthread.php?t=624400") who's had trouble with getting their Dell Inspiron 1521 laptop to suspend/wake and hibernate/restore.

My laptop is entirely stock, and came with the ATI Radeon XPress 1250 graphics card. Ubuntu would detect this card, and offer to use the restricted driver from the repository. I assumed this was a good choice, and opted to use it. 2D and 3D acceleration worked fine.

Interestingly enough, it turns out that the reason why the computer was having issues with suspending/waking and hibernating/restoring is the use of this repository-supplied graphics driver. Installing the closed-source binary driver from ATI's website resolved the issue.

While I nearly always prefer open-source software and have written to ATI to request open-source drivers, I'm not one to let dogma get in the way of practicality. Thus, I opted to use the close-source binary driver.

You can too. The directions are [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a")  (I didn't write them), and I'll reproduce them below in case the page changes.

.....
**IMPORTANT**: I installed these drivers on a brand new Gutsy 7.10 system. All that I did was install the system from the Live CD, restart, decline to use the restricted driver, update all packages to the latest repository versions, and that's it. I have not done this on a already-established installation, and have no idea what Bad Things might occur. Back up your data first. Also, I tried doing this installation without updating the newly-installed system to the latest packages, which resulted in core dumps and an unusable system.

[LIST=1]
[*] Installing the drivers requires the installation of some additional packages. You can do this thusly:
```
sudo apt-get install dpkg-dev debhelper libstdc++5 dkms
```
[*] Next, you'll need to get the binary driver from ATI's website. At the time of this posting, the driver is available [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html").
[*] Once the driver is downloaded to a suitable place (say, your Desktop), you need to change it to be executable. Right-click on the file, select "Properties", click the "Permissions" tab, and tick the "Allow executing file as program" button.
[*] Next, we need to build the installation files. Do this as follows:
```
./ati-driver-installer-[version].run --buildpkg Ubuntu/gutsy
```
[*] Stuff happens. On my system, certain other packages needed to be downloaded and installed. The installer properly invoked apt and fetched them for me.
[*] When done, it'll produce a few packages in the same folder. You should install the following files thusly:
```
sudo dpkg -i fglrx-kernel-source_<version>.deb
sudo dpkg -i xorg-driver-fglrx_<version>.deb
```
[*] Next, run aticonfig to build your xorg.conf file appropriately:
```
sudo aticonfig --initial
```
(Note: When I attempted to do this step on system straight off the installation CD, aticonfig broke in a horrible way and dumped core. When I rebooted, the system never came back up. Be sure to update your system ("sudo apt-get update && sudo apt-get upgrade") prior to doing any of this. Really.)

Assuming it works, it should display a few lines of text. I don't recall exactly what they were, but it wasn't anything scary like "core dumped" and ten pages of errors.
[*] Restart Ubuntu. When it restarts, you should notice that the screen isn't all stretched out like before -- it should have detected your monitor's resolution properly. To ensure that everything is working, open a terminal and run:
```
fglrxinfo
```

On my computer, it returns the following:
```
pete@inara:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7281 Release

```
[*] Celebrate! (However, if you see any mention of the "MESA" in the output, the drivers have not installed correctly.)
[/LIST]

When I did this on a properly-updated system, everything worked very smoothly indeed. Including the download of the driver, it took about 5-6 minutes. Now the computer suspends and wakes properly, and hibernation works. I think I've saved 5-7 minutes just in the last few days not having to have the system go through the whole booting-up process all the time.

If you have any questions or issues, read [this page]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") first. If you have any issues not resolved by reading that page, feel free to ask and I (and presumably others) will do my best to answer them. It should be pretty straightforward on a new system. Remember, I haven't done this on an already-established system, nor on one where I had to uninstall the driver from the repository. I would assume that one should uninstall the driver from the repository, restart, and then attempt the installation of the closed-source driver. Either way, back up your data...there's always that possibility of things going horribly wrong.

Also, I don't use Compiz. I found that Compiz wouldn't work with the driver from the repository, or with the above instructions. The page I got these instructions from, however, has some directions for getting it to work with Compiz. Since I don't use Compiz, I didn't bother following them and have no idea if they work or not. Any input would be appreciated.

---

### Post by fetisha on 2008-04-04
In step 4 I saved the file on the desktop and make  did ./ati-driver-installer-[version].run --build\pkg Ubuntu/gutsy and it told me this:
bash: ./ati-driver-installer-8-3-x86.x86_64.run: No such file or directory

---

### Post by heypete on 2008-04-04
> **fetisha said:**
> In step 4 I saved the file on the desktop and make  did ./ati-driver-installer-[version].run --build\pkg Ubuntu/gutsy and it told me this:
bash: ./ati-driver-installer-8-3-x86.x86_64.run: No such file or directory

Hmm. That's odd.

I think it's because it's supposed to be "--buildpkg" instead of "--build\pkg". If you do that instead, does it work?

My apologies, that was a typo on my part. I've corrected it in the original post.

---

### Post by fetisha on 2008-04-04
> **heypete said:**
> Hmm. That's odd.

I think it's because it's supposed to be "--buildpkg" instead of "--build\pkg". If you do that instead, does it work?

My apologies, that was a typo on my part. I've corrected it in the original post.

No, I'm afraid that still doesn't work. I typed in 
```
./ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

 and it still gave me 
```
./ati-driver-installer-8-3-x86.x86_64.run: No such file or directory
```

I have the file saved on my desktop and the file name is ati-driver-installer-8-3-x86.x86_64.run

---

### Post by heypete on 2008-04-04
> **fetisha said:**
> I have the file saved on my desktop and the file name is ati-driver-installer-8-3-x86.x86_64.run

Hmm. Two things occur to me (forgive me if they seem stupid):
1. Are you in the right directory in the terminal? Remember to type "cd Desktop", and then the ./ati... stuff. If you're not in the right directory, then of course it won't find the right file. :)
2. Did you mark the file as executable?

---

### Post by fetisha on 2008-04-04
> **heypete said:**
> Hmm. Two things occur to me (forgive me if they seem stupid):
1. Are you in the right directory in the terminal? Remember to type "cd Desktop", and then the ./ati... stuff. If you're not in the right directory, then of course it won't find the right file. :)
2. Did you mark the file as executable?
Oh, yeah. That was it. Ok, now it says
```
Generating package: Ubuntu/gutsy
Package /home/justin/Desktop/xorg-driver-fglrx_8.471-0ubuntu1_i386.deb has been successfully generated
Package /home/justin/Desktop/xorg-driver-fglrx-dev_8.471-0ubuntu1_i386.deb has been successfully generated
Package /home/justin/Desktop/fglrx-kernel-source_8.471-0ubuntu1_i386.deb has been successfully generated
Package /home/justin/Desktop/fglrx-amdcccle_8.471-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.KB9051

```

---

### Post by fetisha on 2008-04-04
Ok, in step 6 when i went to do this:
```
sudo dpkg -i xorg-driver-fglrx_<version>.deb
```

I put in this:
```
sudo dpkg -i xorg-driver-fglrx_8.471-0ubuntu1_i386.deb
```

and I got this:
```
(Reading database ... 100376 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 7.1.0-8.37.6+2.6.22.4-14.10 (using xorg-driver-fglrx_8.471-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
Setting up xorg-driver-fglrx (8.471-0ubuntu1) ...

Configuration file `/etc/xdg/compiz/compiz-manager'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/xdg/compiz/compiz-manager ...
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]

```

So I tried it again because maybe it is because I said yes to what it asked me and it gave me:
```
(Reading database ... 100442 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.471-0ubuntu1 (using xorg-driver-fglrx_8.471-0ubuntu1_i386.deb) ...
 * Stopping atieventsd                                                   [ OK ] 
Unpacking replacement xorg-driver-fglrx ...
Setting up xorg-driver-fglrx (8.471-0ubuntu1) ...
 * Starting atieventsd                                                          /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
                                                                         [fail]
```

---

### Post by heypete on 2008-04-04
I hate to say this, but I think you've got me stumped. It looks like there's some problem with libGL, but I'm not sure how to resolve it.

Perhaps [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") might be of some assistance?

Maybe [http://ubuntuforums.org/showthread.php?t=716543]("http://ubuntuforums.org/showthread.php?t=716543") could help as well.

I installed this driver without any issues on a brand-new Gutsy installation (all I did after installing the system was do all the updates/upgrades from the repository) and it worked without any issues.

Does anyone else out there have any ideas?

---

### Post by heypete on 2008-04-04
Hmm, supposedly this series of commands:

```
su
cd /lib/modules/fglrx/build_mod
sh make.sh
cd ..
sh make_install.sh
```

might help out with the libGL issues. I found this information [here]("http://ubuntuforums.org/showthread.php?t=68497").

**Update**: That information was posted in 2005. I can't find the directory here on my system, so I'm not sure if it exists in Gutsy.

---

### Post by fetisha on 2008-04-04
Ok, well, I just did a fresh install of Ubuntu gutsy amd 64 version. Downloading the updated as i type. Going to try it this way.

---

### Post by heypete on 2008-04-04
> **fetisha said:**
> Ok, well, I just did a fresh install of Ubuntu gutsy amd 64 version. Downloading the updated as i type. Going to try it this way.

Hmm. I didn't bother with the AMD-64 version; I just stuck with the i386 version for greater compatibility and whatnot.

If you do manage to get it working, do post here so other AMD-64 users will be able to replicate your steps.

---

### Post by fetisha on 2008-04-04
ok, now with the fresh install i get a little further, but i get this message:
```
~/Desktop$ sudo dpkg -i xorg-driver-fglrx_8.471-0ubuntu1_amd64.deb
(Reading database ... 93226 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.471-0ubuntu1_amd64.deb) ...
dpkg: error processing xorg-driver-fglrx_8.471-0ubuntu1_amd64.deb (--install):
 trying to overwrite `/usr/lib32/libGL.so.1', which is also in package ia32-libs
Errors were encountered while processing:
 xorg-driver-fglrx_8.471-0ubuntu1_amd64.deb

```

---

### Post by fetisha on 2008-04-04
Gosh, this is really starting to get annoying. I successfully got this to work, and now the normal visual effects don't work. I tried this:[http://ubuntuforums.org/showthread.php?t=738243](http://ubuntuforums.org/showthread.php?t=738243) and it still doesn't work (which is what I did to make them work before i did this). Very. Frustrating.

---

