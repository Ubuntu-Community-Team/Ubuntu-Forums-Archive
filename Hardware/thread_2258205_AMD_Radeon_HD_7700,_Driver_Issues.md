---
title: "AMD Radeon HD 7700, Driver Issues"
date: 2014-12-25
forum: Hardware
---

### Post by waterlubber on 2014-12-25
Hello, I'm trying to use the propietary drivers with my newly purchased AMD Radeon HD 7700. 
(The manufacturer was Sapphire). It is detected in the Additional Drivers section, so I selected it. I hit "Apply Changes" and rebooted.
However, when I went to check, the Catalyst Control center was not there. I would like to access this but I do not know what the issue could be...
my previous graphics card was a Nvidia GeForce 8400 GS card. 
Running Ubuntu 14.04 LTS.

edit: I downloaded the .deb file from the AMD website to see if that would work, and I got this error:
Dependency is not satisfiable: fglrx-core
I tried using sudo apt-get to install it, but that didn't work (Package not found).



Solution: Uninstalling the old fglrx-amdcccle when reinstalling the new one from AMD's webpage.

---

### Post by waterlubber on 2014-12-26
Alright, so I somehow managed to get it so when I type "amdcccle" into the terminal, this happens:
 [FONT=courier new]There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
[/FONT]
[FONT=courier new]  [/FONT][FONT=courier new]No AMD graphics driver is installed, or the AMD driver is not functioning properly.[/FONT]
[FONT=courier new] [/FONT][FONT=courier new]Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.[/FONT]
[FONT=courier new] [/FONT]
However, aticonfig still shows a "not found" error and it still says that "fglrx-core" is not satisfiable. Please help, I have no idea how to fix this and I am very sad.

---

### Post by Bashing-om on 2014-12-26
waterlubber; Hummmm .....


a conflict in drivers ?
> 
my previous graphics card was a Nvidia GeForce 8400 GS card. 

What do we have ? : Post back the outputs - Between Code Tags - of terminal commands:
```

sudo find / -name "NVIDIA-Linux-*"
dpkg -l  | grep nvidia
ls -al /usr/share/ati/
dpkg -l | grep fglrx

```
Bet the old Nvidia drivers were not removed.

[INDENT]We have an idea then of what it will take to clean things up, and then perhaps as a start on new beginnings, install the open source driver for the ATI card. Try it and see.[/INDENT]

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by waterlubber on 2014-12-26
Oh, facepalm. I *did* forget to remove the old drivers, but I'm not sure how...
Outputs:
find NVIDIA-Linux:
Returned nothing. Sudo asked for my password, I entered it, and nothing appeared. I'll check back on this one to see if it's still searching.

dpkg:
```

rc  nvidia-304                                                  304.117-0ubuntu1                                    amd64        NVIDIA legacy binary driver - version 304.117
rc  nvidia-304-updates                                          304.117-0ubuntu1                                    amd64        NVIDIA legacy binary driver - version 304.117
rc  nvidia-331                                                  331.113-0ubuntu0.0.4                                amd64        NVIDIA binary driver - version 331.113
rc  nvidia-331-updates                                          331.113-0ubuntu0.0.4                                amd64        NVIDIA binary driver - version 331.113
rc  nvidia-libopencl1-304                                       304.117-0ubuntu1                                    amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-304-updates                               304.117-0ubuntu1                                    amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-331                                       331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-331-updates                               331.38-0ubuntu7                                     amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-304                                       304.117-0ubuntu1                                    amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-304-updates                               304.117-0ubuntu1                                    amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331                                       331.38-0ubuntu7.1                                   amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331-updates                               331.38-0ubuntu7                                     amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver

```


ls:
```
drwxr-xr-x   4 root root  4096 Dec 26 13:51 .
drwxr-xr-x 412 root root 16384 Dec 26 13:51 ..
drwxr-xr-x   2 root root  4096 Dec 26 13:52 amdcccle
-rw-r--r--   1 root root  5184 Dec 25 11:12 fglrx-install.log
drwxr-xr-x   2 root root  4096 Dec 26 13:51 lib64
-rw-r--r--   1 root root 10732 Dec 25 11:12 LICENSE.TXT


```



dpkg fglrx:
```
ii  fglrx                                                       2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                              2:14.501-0ubuntu1                                   amd64        Catalyst Control Center for the AMD graphics accelerators
rc  fglrx-updates                                               2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators


```


Alright,that should be it.
The first one still hasn't found anything, I'll let it run for a few minutes. My hard drive indicator isn't blinking very much though.

---

### Post by darksidedude on 2014-12-26
this should remove all your nvidia packages in one swoop

```
Sudo apt-get purge nvidia*
```

what that does is purges any package with nvidia in its package name. the "*" is a wildcard so that it catches any package with nvidia in it ;)

---

### Post by waterlubber on 2014-12-26
> **darksidedude said:**
> this should remove all your nvidia packages in one swoop

```
Sudo apt-get purge nvidia*
```

what that does is purges any package with nvidia in its package name. the "*" is a wildcard so that it catches any package with nvidia in it ;)
I was about to run that, was going to post to see if it was safe. Ninja'd!
-----
Okay, so I uninstalled all the Nvidia packages and rebooted. Here are the new results:


dpkg: Nothing


ls:
```

total 48
drwxr-xr-x   4 root root  4096 Dec 26 14:56 .
drwxr-xr-x 411 root root 16384 Dec 26 14:56 ..
drwxr-xr-x   2 root root  4096 Dec 26 15:05 amdcccle
-rw-r--r--   1 root root  5184 Dec 25 11:12 fglrx-install.log
drwxr-xr-x   2 root root  4096 Dec 26 14:56 lib64
-rw-r--r--   1 root root 10732 Dec 25 11:12 LICENSE.TXT

```


dpkg (#2):
```

ii  fglrx                                                       2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                              2:14.501-0ubuntu1                                   amd64        Catalyst Control Center for the AMD graphics accelerators
rc  fglrx-updates                                               2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators

```

---

### Post by Bashing-om on 2014-12-26
waterlubber; Sure;

We can certainly do that "Sudo apt-get purge nvidia*" ; see if then you can come up on the ATI driver.

Then we need to remove all the packages marked as rc (package (R)emoved but (C)onfig files remain).
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

[INDENT][INDENT]Maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by waterlubber on 2014-12-26
Alright, I did that and rebooted. Then I ate lunch.
dpkg -l  | grep nvidia: Did nothing


ls -al /usr/share/ati/:
```

waterlubber@GamingPC:~$ ls -al /usr/share/ati/
total 48
drwxr-xr-x   4 root root  4096 Dec 26 14:56 .
drwxr-xr-x 411 root root 16384 Dec 26 14:56 ..
drwxr-xr-x   2 root root  4096 Dec 26 15:05 amdcccle
-rw-r--r--   1 root root  5184 Dec 25 11:12 fglrx-install.log
drwxr-xr-x   2 root root  4096 Dec 26 14:56 lib64
-rw-r--r--   1 root root 10732 Dec 25 11:12 LICENSE.TXT

```

dpkg -l | grep fglrx:
```

ii  fglrx                                                       2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                              2:14.501-0ubuntu1                                   amd64        Catalyst Control Center for the AMD graphics accelerators

```

---

### Post by waterlubber on 2014-12-26
I still don't have access to the catalyst control center. I tried switching the drivers around in the additional software section, but that didn't help.
:(

---

### Post by darksidedude on 2014-12-26
Looking at what I have installed on my system I can see your missing some of the FGLRX files. a simple apt-get or aptitude install will fix that and you should be good to go ;)

here is what *I think * you will need based on the card you have


```

fglrx-updates - Video driver for the AMD graphics accelerators
fglrx-updates-core - Minimal video driver for the AMD graphics accelerators
fglrx-updates-dev - Video driver for the AMD graphics accelerators (devel files)

```

since you already have fglrx-amdccle and fglrx that should be all you need

---

### Post by waterlubber on 2014-12-26
fglrx-core and fglrx-updates-core do not exist...
that's my real problem...however there is a similar item on the AMD site, I'll go try that.
Hmm, AMD had an flgrx-core on their site, apparently it's been removed from the repositories! :O



Okay, so I downloaded the fglrx-core package from the AMD site. However, ubuntu won't let me install it because it conflicts with "ocl-icd-libopencl1".
Any explanations? Is there a way to override these and just install it anyway?

---

### Post by darksidedude on 2014-12-26
do you have wine installed by chance?

---

### Post by waterlubber on 2014-12-26
Yes, I do. I really can't uninstall it because a lot of the games I run use wine. I did research this and apparently it has to do with wine, but there is no real issue and it's just a stupid programming quirk.
This really annoys me, because the OS driver sucks.

---

### Post by darksidedude on 2014-12-27
> well I was able to get wine installed and running. although not threw any package manager I had to compile from source. 

I followed the thread located [http://wiki.winehq.org/BuildingBiarchWineOnUbuntu](http://wiki.winehq.org/BuildingBiarchWineOnUbuntu) 

it works and wow D3 is functional. however when in my situation I had to build without OpenCL support. 

so when you run
Code:
sudo apt-get build-dep wine
make sure you don't install the OpenCL libs or it will remove AMDCCCLE and thus defeat the purpose of this.

I just quoted from a thread that I posted in the Ubuntu +1 thread as I run Kubuntu 15.04 alpha. the link to the wine wiki will show you how to compile wine from source. its really your only option at this point. due to the way wine is packaged. it depends on a version of libCL that conflicts with AmdCCCLE. you will have to :

1. Purge wine
2. install the AMD/ATI driver
3. follow the guide to install wine from source.

---

### Post by Yellow Pasque on 2014-12-27
You'd probably get better results from the open source driver if you used a recent version. [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by waterlubber on 2014-12-27
> **Temüjin said:**
> You'd probably get better results from the open source driver if you used a recent version. [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

No, I will not, I tried those already and I get worse performance then my previous GPU.

Now, after uninstalling wine (ARGH) I got another error:
```

Selecting previously unselected package fglrx-core. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 568542 files and directories currently installed.) 
Preparing to unpack .../fglrx-core_14.501-0ubuntu1_amd64_UB_14.01.deb ... 
Unpacking fglrx-core (2:14.501-0ubuntu1) ... 
dpkg: error processing archive /home/waterlubber/Downloads/fglrx-core_14.501-0ubuntu1_amd64_UB_14.01.deb (--install): 
 trying to overwrite '/etc/acpi/fglrx-powermode.sh', which is also in package fglrx 2:13.350.1-0ubuntu2 
dpkg-deb (subprocess): decompressing archive member: internal gzip write error: Broken pipe 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg-deb (subprocess): cannot copy archive member from '/home/waterlubber/Downloads/fglrx-core_14.501-0ubuntu1_amd64_UB_14.01.deb' to decompressor pipe: failed to write (Broken pipe) 
Errors were encountered while processing: 
 /home/waterlubber/Downloads/fglrx-core_14.501-0ubuntu1_amd64_UB_14.01.deb 

```

I have no idea what this means, I despise this thing already. :(

---

### Post by waterlubber on 2014-12-28
Quick update; the drivers appear to be working but the catalyst control center still does not appear. I noticed a significant performance improvement when switching to the proprietary drivers. All I really need now is the CCC, any ideas? It woul be appriciated.

---

### Post by darksidedude on 2014-12-28
hmm looks like you were tying to install a .deb you downloaded? 
The only driver I know of you download from ATI is the .run which at this time is 14.12 omega. 

you have 2 ways to proceed 
1. install the .run from ATI *but keep in mind every kernel update you will have to reinstall the driver manually* since apt isn't installing it for you
2. purge out all the fglrx packages you have right now and start from the beginning. 

what is the output of ```
dpkg --list | grep "fglrx"
```

---

### Post by waterlubber on 2014-12-28
1. Where do I get this "run" driver?
2. When I install it, do I need to switch to the opensouce drivers in software and updates?
3. I already purged the drivers a few times and tried installing via the repositories, deb and software and updates.
4. How do I use the Software and Updates?

Output of dpkg:
```

ii  fglrx                                                       2:13.350.1-0ubuntu2                                 amd64        Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                                              2:13.350.1-0ubuntu2                                 amd64        Catalyst Control Center for the AMD graphics accelerators

```

---

### Post by waterlubber on 2014-12-30
Is there any way simply to get the Catalyst Control Center running? I don't have any issues with the drivers themselves, just the control center.

When I start fresh, should I:
-Install _only_ from AMD's site,
-Install _only_ from software and updates,
-Install _only_ from the repositories, 
or a combination of both?
If I don't use Software and updates, what driver should I select?


Finally, what's the difference between fglrx-updates and fglrx?
Thanks in advance, I would love some help on this issue.

---

### Post by QIII on 2014-12-30
Hello!

For your first question, could you please run ```
 gksudo amdcccle 
``` and post ant messages returned?

(I think gksudo still works in 14.04)

---

### Post by waterlubber on 2014-12-30
Exact same error as before, no errors in the terminal.

---

### Post by waterlubber on 2015-01-04
Is there any way to completely reset all the drivers related to graphics? Things seem to be getting even worse. I really need help, because right now my card is just an expensive fruit juicer. AMD does not support linux and I'm about to give up...

---

### Post by Bashing-om on 2015-01-04
waterlubber; Yeah,

Let's do that, completely remove the graphics drivers, and install the open source driver.
Then we have a firm foundation from which to work from.
```

sudo sh /usr/share/ati/fglrx-uninstall.sh ##If you installed the driver from the ati site, you can remove it by
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##gets a no-longer needed file out of the way
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates ##removes all the proprietary driver files
sudo apt-get install dkms ##cheap insurance - for installing supplementary versions of kernel modules (the driver is a module)
sudo apt-get install xserver-xorg-video-radeon ##the Open Source module it's self
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core ##just to make sure the related libraries and the xserver layer is clean and uncorrupted - the current version
sudo dpkg-reconfigure xserver-xorg ## just that, make the operating system forget the purged 'FGLRX' module, and pick up and use the new module(s) installed (radeon)
sudo update-initramfs -u ##again, cheap insurance, make sure the linux-image is rebuilt with the new libs and modules.

```

Reboot and let's see what the result is .. hopefully up and running on the open source driver for the ATI card.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by waterlubber on 2015-01-04
Thanks for the response. It was greatly appreciated. However, as I was executing it, I realized I forgot to install the old amdcccle when I downloaded it from AMD's site. I also rebooted a lot. It was just in time, as my other graphics card started to go nuts. 

Not sure how to give rep, but you helped a ton. *throws invisible reputation*

---

### Post by Bashing-om on 2015-01-04
waterlubber; Great !

Pleased you are up and running.

all's well that ends well
[INDENT][INDENT][INDENT]many paths to an end
[/INDENT][/INDENT][/INDENT]

---

