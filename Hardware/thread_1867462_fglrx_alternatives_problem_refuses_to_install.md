---
title: "fglrx alternatives problem refuses to install"
date: 2011-10-23
forum: Hardware
---

### Post by GinoMan2440 on 2011-10-23
```
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: error: unable to install /usr/lib32/libaticalcl.so.dpkg-tmp as /usr/lib32/libaticalcl.so: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up fglrx (2:8.881-0ubuntu4) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: error: unable to install /usr/lib32/libaticalcl.so.dpkg-tmp as /usr/lib32/libaticalcl.so: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
                                         

```

For some reason, I can't install fglrx and it's associated packages and the output I get when I try to install it is the above. I'm on an HP with an AMD processor and ATI graphics it's less than a year old and the ati stuff worked in 11.04, but no longer install properly in 11.10. Please help me?

---

### Post by horusofoz on 2011-10-23
Hardware:

Model: HP Pavilion DV5-1108AX
Graphics: ATI Raedon HD 3450 (stock)
Only modification to hardware is installing additional 2GB RAM to 4GB.

Summary: After installing Ubuntu 11.10 I cannot to install the FGLRX post update driver offered through Additional Drivers.

Situation: I first did a fresh Ubuntu 11.10 install and made my usual post install steps (Updates, VLC, Chrome, background, games, etc) then tried to install the post release FGLRX driver offered through Additional Drivers. This failed. I then attempted to install the stock FGLRX driver (the one not labelled post release) and it failed. Both with an error to saying to check jockey.log.

I then did a new install of Ubuntu 11.10 and without updating or installing anything else was able to install the stock FGLRX driver. I then rebooted and attempted the post release updated driver install offered through Additional Drivers and again got the error asking to check jockey.log.

My display is working but naturally would really like to be able to get the latest version of the driver working to get the best out of my hardware. To help devs and gurus resolve this issue I have attached a screenshot of the error, my jockey.log file (extension changed to zip so can be uploaded) in addition to providing hardware specs above.
Any help would be greatly appreciated to keeping Ubuntu Rockin' :guitar:

---

### Post by GinoMan2440 on 2011-10-23
ok, so I started looking around the postinst script for the package and found a curious pattern.... consider the following:
```

gino@hostname:pwd# update-alternatives --install /usr/lib/lib.conf ginos-testing-alternatives /usr/lib/gat/lib.conf 2000 \
> --slave /usr/lib/gat.txt gat.text-lib /usr/lib/gat/gat.txt \
> --slave /usr/lib32/gat.txt gat-text-lib32 /usr/lib32/gat/gat.txt
update-alternatives: using /usr/lib/gat/lib.conf to provide /usr/lib/lib.conf (ginos-testing-alternatives) in auto mode.
update-alternatives: error: unable to install /usr/lib32/gat.txt.dpkg-tmp as /usr/lib32/gat.txt: No such file or directory

```

This is a contrived example I ran on my computer which led to the error messages you see above. On my system, and I assume all ubuntu installs on a 32 bit arch, /usr/lib32/ is a symlink to /usr/lib/. for some reason update-alternatives does not recognize symlinks and does not ignore when a duplicate symlink is being created in the target directory with a different alternatives name (in /etc/alternatives/) but the same original file with a different path to the same location. Now the question is, is this a bug in update-alternatives or is this an error in how the postinst script for the package has been constructed?

---

### Post by GinoMan2440 on 2011-10-23
YAAAAAAY!!! I finally fixed the bug myself, I'll be emailing my work along with a readme to the ubuntu package maintainers, this bug is officially fixed as far as I'm concerned!
Gino

---

### Post by RoelitoRodas on 2011-10-23
hey man do you think you could send me the instructions about how to fix that bug?. i'm having the same issues! and i'm mad already! i would really apreciate it. Thank you!

---

### Post by GinoMan2440 on 2011-10-23
[SIZE="4"]THE FIXES ARE FINALLY READY FOR RELEASE!!![/SIZE]

Go ahead and download this file into your home directory, and issue the following commands:

```

sudo aptitude install qbittorrent-nox build-essential;
gunzip ubuntu-oneiric-ocelot-11-10-fglrx-installer-packages-with-bug-fix.torrent.gz;
qbittorrent-nox ubuntu-oneiric-ocelot-11-10-fglrx-installer-packages-with-bug-fix.torrent;
cd /Downloads/fglrx-packages-fixed/;
sudo aptitude purge fglrx fglrx-amdcccle fglrx-dev;
sudo dpkg -i fglrx*-bf-rc*.deb;
sudo amdcccle

```

If you are the package maintainer, the tar.gz included includes all three *.debs, as well as the deconstructed packages, in "fglrx-installer-8.881/debian/" are the files as they stand, I changed "fglrx.postinst.in" to check if /usr/lib/ is the same as /usr/lib32/ and if they are to only worry about alternatives in /usr/lib/. I also changed the changelog to reflect that fglrx has a bugfix and is a slightly later version, you will probably modify my work further before uploading it to the repository. I also changed "AUTHORS" to include my name for directly fixing the bug. Thanks guys!
Gino Vincenzini <OpenMySourceCode@gmail.com>

---

### Post by RoelitoRodas on 2011-10-23
Thank U man. I'm downloading it right now, but the download is going to slow... i have only downloaded 10mb, there are only a few seeds and peers =0(. Once again thank u for your hard work fixing the bug.

---

### Post by Bucic on 2011-10-24
> **RoelitoRodas said:**
> Thank U man. I'm downloading it right now, but the download is going to slow... i have only downloaded 10mb, there are only a few seeds and peers =0(. Once again thank u for your hard work fixing the bug.
I'm seeding now. BTW, I'm grateful for the fix and all but why upload to only one source?

---

### Post by Bucic on 2011-10-24
No seeders - can't complete and re-seed it further.

---

### Post by horusofoz on 2011-10-24
Kicked of download this morning before work (2 hours ago) and was jumping a long adequately. 1XXkb/s.

---

### Post by Bucic on 2011-10-25
I already downloaded the pack. Should I use just the
```
sudo aptitude purge fglrx fglrx-amdcccle fglrx-dev;
sudo dpkg -i fglrx*-bf-rc*.deb;
sudo amdcccle
```
to proceed with the installation? After I navigate to the directory with the pack that is.

---

### Post by Bucic on 2011-10-25
After
```
sudo amdcccle
```
I get 'Command not found' error.

---

### Post by Bucic on 2011-10-26
bump :oops:

---

### Post by GinoMan2440 on 2011-10-26
Did the installation succeed?, if you had errors during installation, then it amdcccle won't work

---

### Post by Bucic on 2011-10-26
> **GinoMan2440 said:**
> Did the installation succeed?, if you had errors during installation, then it amdcccle won't work
Exaclty as I said in the post #12 (error).

What do you mean it won't work? If I get that error (see above), it's a game over for me? I get **** poor performance both on open source and on AMD proprietary driver. I wanted to test if the latest one (post-release) could be the solution...

---

### Post by GinoMan2440 on 2011-10-27
No, it's not game over... I was asking if you got an error for the previous command "dpkg -i fglrx*-bf-rc*.deb"
if you did, then it's likely that fglrx did not install correctly, also if you use the command "echo $PATH" it should show you what folders are searched for amdcccle, if you don't see "/usr/bin/" then it's not finding the alternatives and you need to add that to your path, but we'll get there after we find out what the problem is. Did you get errors while running dpkg -i?

---

### Post by Bucic on 2011-10-27
> **GinoMan2440 said:**
> No, it's not game over... I was asking if you got an error for the previous command "dpkg -i fglrx*-bf-rc*.deb"
if you did, then it's likely that fglrx did not install correctly, also if you use the command "echo $PATH" it should show you what folders are searched for amdcccle, if you don't see "/usr/bin/" then it's not finding the alternatives and you need to add that to your path, but we'll get there after we find out what the problem is. Did you get errors while running dpkg -i?
Understood. IIRC there were no errors after dpkg -i. Only after the amdcccle.

---

### Post by GinoMan2440 on 2011-10-27
What's the result of the command:

echo $PATH?

---

### Post by Bucic on 2011-10-27
> **GinoMan2440 said:**
> What's the result of the command:

echo $PATH?
Thank you for staying with me. I'll reply as fast as possible. Here's the result
```
~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
Command issued in normal desktop - not in command line only mode. Just saying.

---

### Post by GinoMan2440 on 2011-10-27
That's weird that lightdm is at the front of the list but it's not hurting anything.....Otherwise your path matches mine; what about alternatives? run these and send me the output....

ls -l /etc/alternatives/ | grep amdcccle;
ls -l /usr/bin | grep amdcccle;

---

### Post by Bucic on 2011-10-28
> **GinoMan2440 said:**
> That's weird that lightdm is at the front of the list but it's not hurting anything.....Otherwise your path matches mine; what about alternatives? run these and send me the output....

ls -l /etc/alternatives/ | grep amdcccle;
ls -l /usr/bin | grep amdcccle;
Both commands gave no output nor errors.

---

### Post by GinoMan2440 on 2011-10-29
.... those packages couldn't have installed correctly then.... try these commands as su:

apt-get install aptitude;
aptitude purge fglrx fglrx-dev fglrx-amdcccle;
dpkg -i /Path/To/Packages/ # I used the wildcards fglrx*-bf-rc*.deb but that only works if they're in the current directory

(if you're not sure if they're there, run "ls | grep fglrx*-bf-rc*.deb" they should list themselves.)

also for good measure, run as either root or you:
file /usr/lib32
it should say that it's a symbolic link to /usr/lib/

Let me know what you find
Gino

---

### Post by Bucic on 2011-10-29
I've lost the copy of the packages and no one is seeding right now. Does anyone have another source or can re-upload the packages?

---

### Post by GinoMan2440 on 2011-10-30
I'm seeding right now, go ahead and connect. I wish the maintainer from fglrx would get back to me on whether he got my message about what the fix was exactly....

---

### Post by kchilaka on 2011-10-30
> **GinoMan2440 said:**
> I'm seeding right now, go ahead and connect. I wish the maintainer from fglrx would get back to me on whether he got my message about what the fix was exactly....

I am downloading the package as well.. Will seed when I am done downloading.. I have the same issue. Additional drivers failed to install.

---

### Post by Bucic on 2011-10-30
> **GinoMan2440 said:**
> I'm seeding right now, go ahead and connect. I wish the maintainer from fglrx would get back to me on whether he got my message about what the fix was exactly....
I kept it on but it has downloaded only about 50% and is idling for many hours now. Is this really impossible to upload it to whatever hosting service like rapidshare, mediafire or whatever?

---

### Post by Bucic on 2011-10-31
The torrent is still dead.

---

### Post by GinoMan2440 on 2011-11-01
Let's try it over rapidshare

The development files:
[fglrx-dev 8.881](https://rapidshare.com/files/861239590/fglrx-dev_8.881-0ubuntu4-bf-rc_i386.deb)
[fglrx 8.881](https://rapidshare.com/files/921338057/fglrx_8.881-0ubuntu4-bf-rc_i386.deb)
[fglrx-amdcccle 8.881](https://rapidshare.com/files/1335918004/fglrx-amdcccle_8.881-0ubuntu4-bf-rc_i386.deb)

For the package maintainer, I have tar.gz'ed all of the work I did to make these three packages work when they don't:

[fglrx installer bugfix.tar.gz](https://rapidshare.com/files/1308048817/fglrx-installer-bugfix.tar.gz)

just a caution, the tar package is very big, 200+MB, if you're just trying to install the packages, download the first three packages and dpkg -i them. if you don't know how but can install them one by one, install fglrx first, then fglrx-amdcccle, then fglrx-dev. you shouldn't have any problems and attempting to run amdcccle from the terminal or alt+f2 should work.

Good luck,
Gino V

---

### Post by Bucic on 2011-11-01
Softpedia says a new driver has been released [http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml](http://linux.softpedia.com/get/System/Hardware/ATI-Radeon-Linux-Display-Drivers-6719.shtml) In that case is there a point to try this one fixed by you?

I installed the one from softpedia without any problems and it seems to work best but still poorly (see my sig).

---

### Post by GinoMan2440 on 2011-11-01
the ones provided by me are in keeping with the version provided by the package manager. if/when ubuntu provides an update in the repo, even a minor one, my packages will be replaced with the updated ones without a hitch, and hopefully the bug will be addressed in said update. assuming this to be the case with any future updates to these three packages, then those will be used instead. if you acquire a later version package, great, but for the bulk of us, it's satisfying enough just to get the repository version to work. either way the bug needed to be addressed and for some users (me at least) fglrx would not install properly any other way than to use these fixed packages. in the meantime, anyone who needs the packages, has them here with the provided links or through bittorrent.

---

### Post by Cypour on 2011-11-07
those single files are x86

what about amd64???

---

### Post by monteceneri on 2011-11-15
Hello,

I have recently installed on my NOTEBOOK ACER TIMELINE X 5820 TG Ubuntu 11.10 Oneiric 32 bit. 
I am not able to activate ATI propietary driver neither from control panel (Jockey FAILDE) or by downloading the installer fro ATI website, 11.10**.run generating deb package and dpkg them. Firs I have errors on that step with update-alternatives on lib32aticalc....etc
the after type aticonfig --initial anf reboot, the system start only in console mode and I mast delete xorg.conf to reboot X normally.
So after a lot of forum...I try to follow Your suggestion to fic the Installer.run by I am not able to download the torrent file becouse the client remains in stalled state.
Please help me, becouse my laptop fan is always at maximum speed and the laptop is very hot.

---

### Post by monteceneri on 2011-11-15
Another information and precisation about my problems:
1) the error messages are:
    ....update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: error: unable to install /usr/lib32/libaticalcl.so.dpkg-tmp as /usr/lib32/libaticalcl.so: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2........

2) I try another approach, I have edited rc.local in order to disable the discrete graphics and use only the Intel integrated graphics following:([http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/](http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/)).
The result was good because the OVEREATHING DESAPPEAR but a new problem arises:
I have keyboard problem, It causes me that some word appear with missing character. So, after re-activate discrete graphics the keyboard returns OK.

Please help me. To me It will be good both the possibilities 1) with ATI works or 2) with keyboard ok.:(

---

### Post by monteceneri on 2011-12-05
Hello,

I have resolved my problem. :DThe solution was that I have download the last version of ATI driver installer.run: 11.11 and now It works! First of all the xorg.conf is rich of data and system reboot normally and also, I am now able to use ATI Catalyst control center. For example now I am able to use two monitors, that's incredible.!! 
Thanks to ATI developers for this new release that has fixed my problem.:P

---

### Post by jarek_s on 2011-12-10
I would like to suggest an alternative solution to problem. This way you will not need to download any non standard files.

If you get following error when installing fglrx, fglrx-updates, or via fglrx installer from amd:

update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf 
because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: error: unable to install /usr/lib32/libaticalcl.so.dpkg-tmp as /usr/lib32/libaticalcl.so: No such file or directory

We can force to skip update-alternatives with following command:
```
sudo update-alternatives --set i386-linux-gnu_gl_conf /usr/lib/i386-linux-gnu/mesa/ld.so.conf

```This sets manually mesa as alternative for gl_conf.

After that, you should be able to install your fglrx, for example following way:
```
 sudo apt-get install fglrx-updates 
```Now, just revert your setting for gl_conf:
```
sudo update-alternatives --auto i386-linux-gnu_gl_conf 
```It will still print the error message, however package should be already installed and it should not really matter (as /usr/lib32 should be link to /usr/lib on 32 bit systems) .

EDIT: this gets a little more complicated, cause we have to manually fix a few things that installer don't do.
Make sure that X11 can find libfglrxdrm.so 
```
sudo ln -s /etc/alternatives/i386-linux-gnu_xorg_extra_modules /usr/lib/i386-linux-gnu/xorg/extra-modules
```Ensure that kernel sees fglrx module while booting:
```
sudo update-initramfs -u
```One last thing, which you shouldn't have to do - looks like blacklisting "radeon" module in /etc/modprobe.d/fglrx.conf can be not enough to prevent this module from loading. Even with rdblacklist=radeon kernel option this module can get loaded. To avoid that module interacting with fglrx you can use "nomodeset" kernel option.



Hope it helps,
Jarek

---

### Post by eltomito on 2012-05-19
I have a Lenovo G570 notebook and the fglrx drivers are broken, too.
I somehow got it to install even the "updates" driver but it makes desktop
really lazy to respond.
Could anybody, please, seed the fglrx-packages-fixed  file mentioned here
so that I can download the torrent and try it out?
And does anybody know anything about how much fixed it really is?

Thank you!

---

