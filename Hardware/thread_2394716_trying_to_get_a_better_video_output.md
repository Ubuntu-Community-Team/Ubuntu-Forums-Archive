---
title: "trying to get a better video output"
date: 2018-06-20
forum: Hardware
---

### Post by wfriedwaldgmail.c on 2018-06-20
hardware: HP Stream 11 (not sure if it's 2014 or 2015 machine)
OS: a brand new install of Ubuntu 18
program: either the builtin video player OR VLC - same issue on both

the video playback is just too jerky and stutter-y 

especially when I'm trying to do something else at the same time, even if that "something" is as a simple as doing a basic search for the next video I'm going to be playing.

is there anyway I can increase performance? either via software, the OS, or additional physical memory?

or, is there another low-price windows machine (maybe $300) that I should get?

thanks for any input!

W

PS: there's basically only TWO things I want to do with my laptop:
A. play videos for presentations
B. access google doc's & gMail.
everything else I will happily disable or delete, anything to increase video performance..

LAST THING: I actually think Ubuntu 17 was better than 18 as far as this particular issue goes, although 18 seems to be an improvement in every other way.  But this is crucial to me...

---

### Post by Yellow Pasque on 2018-06-20
Start by looking at vainfo:
```
sudo apt-get install vainfo 
vainfo
```


> additional physical memory?
No. It's soldered on to the mainboard.

---

### Post by wfriedwaldgmail.c on 2018-06-20
thanks - this is what I get:

```
password for will: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  vainfo
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 9,884 B of archives.
After this operation, 39.9 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 vainfo amd64 2.1.0+ds1-1 [9,884 B]
Fetched 9,884 B in 0s (119 kB/s)  
Selecting previously unselected package vainfo.
(Reading database ... 160596 files and directories currently installed.)
Preparing to unpack .../vainfo_2.1.0+ds1-1_amd64.deb ...
Unpacking vainfo (2.1.0+ds1-1) ...
Setting up vainfo (2.1.0+ds1-1) ...
Processing triggers for man-db (2.8.3-2) ...
```

---

### Post by Yellow Pasque on 2018-06-20
> **wfriedwaldgmail.c said:**
> thanks - this is what I get

LOL. I was asking for the output of the vainfo command:
```
vainfo
```

But hey, at least we know it successfully installed now.

---

### Post by wfriedwaldgmail.c on 2018-06-20
will@will-HP-Stream-Notebook-PC-11:~$ vainfo
```
libva info: VA-API version 1.1.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_1_1
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.1 (libva 2.1.0)
vainfo: Driver version: Intel i965 driver for Intel(R) Bay Trail - 2.1.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Simple            :    VAEntrypointEncSlice
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileH264StereoHigh         :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc
      VAProfileJPEGBaseline           :    VAEntrypointVLD
```

sorry - I do NOT claim to know what I am doing!

thanks!

w

---

### Post by wfriedwaldgmail.c on 2018-06-20
[ATTACH=CONFIG]280162[/ATTACH]

---

### Post by Yellow Pasque on 2018-06-21
Well, that looks okay. I will let someone else take this as I don't have a lot of experience with Intel GPU's and the best video player to use with them. If you can get a log from vlc, that may help.

---

### Post by kazakore on 2018-06-23
I'm fairly certain this will get you most of the way to what you want.

[https://askubuntu.com/questions/667466/screen-tearing-in-ubuntu-with-nvidia-intel-graphics](https://askubuntu.com/questions/667466/screen-tearing-in-ubuntu-with-nvidia-intel-graphics)

---

### Post by Yellow Pasque on 2018-06-23
^I don't think the OP is describing tearing, which is more of a synchronization issue.
It seems the system is underpowered or using the wrong video output. Ideally, intel GPU should use VA-API output. (If I had VLC installed on my curent system, I'd take a screenshot.) 
Note that the GPU doesn't support hardware accelerated decode of H.265/HEVC, so I would expect a lower end CPU to struggle with those.

---

### Post by kazakore on 2018-06-24
Well if the OP is using onboard Intel graphics, which he is with the i925 driver, then he is almost certainly going to want to set the video tearing option anyway and it will still vastly improve the video output, even if the machine isn't powerful enough to handle some files such as HEVC.

---

