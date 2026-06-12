---
title: "IVTV firmware not found in modprobe, Hauppage PVR 150"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by Yorn on 2006-11-30
I have an ivtv firmware problem with my PVR 150.

I've followed the recent Edgy Eft guide, trying all three installation options and it does not install ivtv. I can see the device in device manager. The primary purpose of trying out Ubuntu, or even linux at all, for that matter, is to see how well it does MythTV. I tested KnoppMyth and it did not work at all, judging from the last ISO release date for that distribution, it doesn't look like it's supported anymore.

The following is a log of what I'm doing for each option and the errors I get when I follow the instructions:

**Debian Archive from ivtvdriver.org (Option 1)**
[INDENT]myth@mythtv:~$ sudo nano /etc/apt/sources.list
myth@mythtv:~$ wget [http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg](http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg) -O- | sudo apt-key add -
--20:47:42--  [http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg](http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg)
           => `-'
Resolving dl.ivtvdriver.org... 130.133.35.30
Connecting to dl.ivtvdriver.org|130.133.35.30|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,690 (1.7K) [text/plain]

100%[========================================>] 1,690         --.--K/s             

20:47:42 (36.63 MB/s) - `-' saved [1690/1690]

OK
myth@mythtv:~$ sudo apt-get install ivtv-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ivtv-firmware
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 120kB of archives.
After unpacking 164kB of additional disk space will be used.
Get:1 [http://dl.ivtvdriver.org](http://dl.ivtvdriver.org) edgy/firmware ivtv-firmware 20061007 [120kB]
Fetched 120kB in 6s (18.0kB/s)                                                     
Failed to fetch [http://dl.ivtvdriver.org/ubuntu/pool/edgy/firmware/ivtv-firmware_20061007_all.deb](http://dl.ivtvdriver.org/ubuntu/pool/edgy/firmware/ivtv-firmware_20061007_all.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
myth@mythtv:~$ 
[/INDENT]

**Build Debian Archive (Option 2)**
[INDENT]myth@mythtv:~$ wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip) 
--20:49:05--  [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
           => `pvr_1.18.21.22254_inf.zip.2'
Resolving ftp.shspvr.com... 216.234.188.64
Connecting to ftp.shspvr.com|216.234.188.64|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /download/wintv-pvr_250-350/inf ... done.
==> PASV ... done.    ==> RETR pvr_1.18.21.22254_inf.zip ... done.
Length: 593,441 (580K) (unauthoritative)

100%[========================================>] 593,441      191.92K/s    ETA 00:00

20:49:19 (191.45 KB/s) - `pvr_1.18.21.22254_inf.zip.2' saved [593441]

myth@mythtv:~$ export DEBFULLNAME="Mario Limonciello" 
myth@mythtv:~$ export DEBEMAIL="superm1@ubuntu.com"
myth@mythtv:~$ sudo ivtv-make-fwpkg pvr_1.18.21.22254_inf.zip 
ivtv-make-fwpkg: Extracting firmware from pvr_1.18.21.22254_inf.zip
ivtv-make-fwpkg: Firmware is .zip variety
ivtv-make-fwpkg: Firmware version is 1.18.21.22254
ivtv-make-fwpkg: Maintainer: Mario Limonciello <superm1@ubuntu.com>
ivtv-make-fwpkg: package directory "ivtv-firmware-1.18.21.22254" already exists.
ivtv-make-fwpkg: please remove it to continue.
myth@mythtv:~$ sudo dpkg -i ivtv*firmware*deb 
(Reading database ... 93734 files and directories currently installed.)
Preparing to replace ivtv-firmware 1.18.21.22254 (using ivtv-firmware_1.18.21.22254_all.deb) ...
Unpacking replacement ivtv-firmware ...
Preparing to replace ivtv-firmware 1.18.21.22254 (using ivtv-firmware_20061007_all.deb) ...
Unpacking replacement ivtv-firmware ...
dpkg: error processing ivtv-firmware_20061007_all.deb (--install):
 trying to overwrite `/lib/firmware/v4l-cx2341x-init.mpg', which is also in package ivtv-utils
Setting up ivtv-firmware (1.18.21.22254) ...
Errors were encountered while processing:
 ivtv-firmware_20061007_all.deb
myth@mythtv:~$ wget [http://home.eng.iastate.edu/~superm1/contrib/firmware/v4l-cx25840.fw](http://home.eng.iastate.edu/~superm1/contrib/firmware/v4l-cx25840.fw) 
--20:49:49--  [http://home.eng.iastate.edu/~superm1/contrib/firmware/v4l-cx25840.fw](http://home.eng.iastate.edu/~superm1/contrib/firmware/v4l-cx25840.fw)
           => `v4l-cx25840.fw'
Resolving home.eng.iastate.edu... 129.186.23.45
Connecting to home.eng.iastate.edu|129.186.23.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,264 (14K) [video/unknown]

100%[========================================>] 14,264        --.--K/s             

20:49:49 (259.07 KB/s) - `v4l-cx25840.fw' saved [14264/14264]

myth@mythtv:~$ sudo mv v4l-cx25840.fw /lib/firmware 
[/INDENT]

**TGZ Archive (Option 3)**
[INDENT]myth@mythtv:~$ cd /lib/firmware/
myth@mythtv:/lib/firmware$ sudo wget [http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)
--20:50:56--  [http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)
           => `firmware.tar.gz'
Resolving dl.ivtvdriver.org... 130.133.35.30
Connecting to dl.ivtvdriver.org|130.133.35.30|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 119,775 (117K) [application/x-gzip]

100%[========================================>] 119,775      158.30K/s             

20:50:58 (157.90 KB/s) - `firmware.tar.gz' saved [119775/119775]

myth@mythtv:/lib/firmware$ sudo tar zxvf firmware.tar.gz
v4l-cx2341x-dec.fw
v4l-cx2341x-enc.fw
v4l-cx2341x-init.mpg
v4l-cx25840.fw
v4l-pvrusb2-24xxx-01.fw
v4l-pvrusb2-29xxx-01.fw
myth@mythtv:/lib/firmware$ sudo rm firmware.tar.gz
[/INDENT]

Option 3 appears to work, then I do the next step:
[INDENT]myth@mythtv:/lib/firmware$ sudo m-a update,prepare

Updated infos about 83 packages
Getting source for kernel version: 2.6.17-10-generic
Kernel headers available in /lib/modules/2.6.17-10-generic/build
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Done!
myth@mythtv:/lib/firmware$ 
[/INDENT]

Then lastly:
[INDENT]myth@mythtv:/lib/firmware$ sudo modprobe ivtv
FATAL: Module ivtv not found.
[/INDENT]

So of all 3 options, none of them seem to be working. Any advice?

---

### Post by Titus A Duxass on 2006-11-30
Do a search, there is a really good how-to prepared by superm1 in the docs.

Found it - [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

---

### Post by Yorn on 2006-11-30
> **Titus A Duxass said:**
> Do a search, there is a really good how-to prepared by superm1 in the docs.

Found it - [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

Yes, I am following that guide. This is why my post contained:
"I've followed the recent Edgy Eft guide, trying all three installation options and it does not install ivtv."

In fact, the commands in my first post are for all three options listed on that exact page.

Anyone have any other advice?

---

### Post by Yorn on 2006-11-30
I've done numerous searches for ivtv and ubuntu and found nothing to help. Still stuck on this same problem.

---

### Post by superm1 on 2006-12-01
Yorn, there was a bug with the ivtvdriver.org repo the last day.  I've updated it and you should be able to install the firmware from there again.  Update your package lists and try to reinstall ivtv-firmware.

---

### Post by superm1 on 2006-12-01
Well that just resolves using option 1.  You are still not getting the modules built.  You skipped the step sudo m-a a-i ivtv.

---

### Post by Yorn on 2006-12-01
Ahh ok. Thanks. I will take a look at both your suggestions tonight. I thought it was really odd I was having problems with each step. I don't know what the "m-a a-i ivtv" command stands for. I think that's why I've had a hard time adjusting to a new OS, I don't know what the commands stand for, so my only real option is to ask for help on the forums.

---

### Post by superm1 on 2006-12-01
Well m-a is for module assistant.

**sudo** **m**odule**-a**ssistant **a**uto**-i**nstall [B]ivtv
[/B]
Is identical and also works.  Sudo will launch as super user.  Module assistant builds kernel modules for particular kernels.  Auto-install indicates that it will fetch sources, build, and then install all in one step.

For future reference, if you come across a command that you aren't too sure what its doing:

```
man m-a
```

---

### Post by Yorn on 2006-12-01
Ah yeah, I could have just RTFM. :)

On a second look, it would appear I did do that step, I just copied and pasted wrong when I first wrote this post.

Anyway, I like the "man" method better than the Windows options:
program.exe -?
program.exe /?
program.exe -h
program.exe -help
program.exe --help

Basically, trying each possible option till it spits something out.

---

### Post by Yorn on 2006-12-02
Well, I'm still not getting any of the three options to work

Still ends up with "FATAL: Module ivtv not found."

I'm trying to convince myself to keep using Ubuntu. I'll try reinstalling and following the guide again, then I'll just go back to Windows.

---

### Post by superm1 on 2006-12-02
Well its not those 3 options where the problem is occuring for you.  After the module-assistant auto-install step is where the ivtv module is generated.

---

### Post by Yorn on 2006-12-08
I ended up getting it to work. The problem was not separating the commands as I copied and pasted them, ironically. Once I did that, it worked. Now the problem I'm having is getting the card to produce quality output. Only some of the channels seem to come in decent. But I suspect that has more to do with something else that the guide can't help me with, so I'm going to do some more fiddling around. Thanks for being patient with me.

---

### Post by superm1 on 2006-12-08
If your using this with mythtv, there are post processing filters that you can run on the content.  I agree though, often the raw content received isn't very high quality.  Good Luck!

---

### Post by majoridiot on 2006-12-08
as simple as it sounds, you might try a signal booster to
improve your video quality.  i was having signal quality issues 
with my pvr-150 and installed a motorola 484095-001-00 booster
before the tv/modem splitter.  it noticably improved the video
and audio on all stations and i improved broadband recieve 
performance as well- boosting signal strength from 5db to 23db.

it was a fairly inexpensive improvement... $50 after rebate.

---

