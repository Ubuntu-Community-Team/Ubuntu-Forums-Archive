---
title: "Gigsbyte 970A-D3 Mother board"
date: 2015-12-25
forum: Hardware
---

### Post by Mig23 on 2015-12-25
Hi,

I posting my hardware configuration because, i try to install ubuntu 15.04 in it and i was not able to do it.

So,

Hardware configuration is:
MB GIgabyte 970A-D3
AMD Phenon II (6cores)
MSI R6770 1Gb
256Gb SSD Samsung

I search here, and didn't found a solution 
I search the internet and I found that this board and processor are not supported by ubuntu.
Can some one with more experience then me in ubuntu, confirm this.
And if is possible to install, how can I do it? I out of options. 

Thanks in advanced

Mig24

---

### Post by Vladlenin5000 on 2015-12-25
Hi and welcome.

Basically you told us "I tried, didn't work". Not enough.
The MB + CPU are compatible. It may or may not have issues that require further tweaking but otherwise installation is as usual.

Now, please describe what you did and what failed. Thank you.

---

### Post by mörgæs on 2015-12-26
Agree with the post above. Just adding that 15.04 is soon running out of support so 15.10 is a better option.

---

### Post by Mig23 on 2015-12-26
Hi, vlad, Mörg

Thanks, 

Well, what i did was when 15.04 can out ,I burn it in a DVD, and try to install it...
doesn't even show the installation screen when it boots... weird ... So ...
I try several types of bios configuration, with and without UEFI, Legacy support, ... nothing ... it doesn't show the installation screen.

Then I search the net, I find some post around 2013 that said, the AMD Phenon was not support, and some other saying Some AMD Video card also was not support, ...
Search for the Here (ubuntu forums),  askubuntu, and didn't find anything saying that my config, is or is not support.

I will do what you said, DL 15.10 and try it again... I will post outcome, here, ... give a couple of hours.

---

### Post by Mig23 on 2015-12-26
Dl 15.10, burn it on DVD, and boot it ...
DVD speed up, ... ubuntu purple screen, without any letter on the screen, just the initial purple screen , after 2 seconds DVD speeds down, and monitor goes black, monitor power led blinks, ...
Stays for about 2/3 minutes, until I decided to power off the computer.

The teststhat I did with the 15.04 version, the purple screen didn't show up, the screen just goes black, and the monitor power led blinks.

 My monitor is a full HD, if doesn't recognize a full HD, it should recognize a normal monitor and assume it's one and use my monitor as a normal monitor, right?
I have the AMD-X(virtualization) actived, .. can it be possible this being the cause of this problem? I will test it... again with the 15.10 version.
I Deactivated the virtualization with version 15.04 and the result was the same.

---

### Post by tokyobadger on 2015-12-26
Reading around it seems you might need to set IOMMU to enabled in BIOS.

After installation you would then modify /etc/default/grub 
```
[COLOR=#000000]GRUB_CMDLINE_LINUX="iommu=soft"
```
[/COLOR][Read more on the issue and the fix in this thread](http://ubuntuforums.org/showthread.php?t=2111223&page=3)

---

### Post by Mig23 on 2016-01-02
Hi, Tokyo

Thanks...

But that's my actual config and it doesn't work, ... I have being tried many bios config, but the result is the same, just the first screen, and then when doesn't show the installation screen, for being possible to install the OS.

I follow your link, and it seems that there is still a problem with the 64bit kernel, or the bios in this MB have some type of bug that wasn't fixed yet.

I want to steup a full dual boot in my system so I have to wait for updates to the kernel or bios or keep trying to fix this, ... somehow.

Any help it's welcome... 

bottom line: it's boot, but after the first initial screen, doesn't show the installation screen of ubuntu... I will try 32 bit kernel ...

---

### Post by Mig23 on 2016-01-02
BTW, AMD sb970 North bridge and SB950 south brigde seems not to be supported in 64bit kernel... can someone confirm this?
Because those are the chipset that I have in my MB.

---

### Post by tokyobadger on 2016-01-03
[Another link](http://ubuntuforums.org/showthread.php?t=2114055&page=1) with Arch and Fedora users chiming in. Sorry to hear that the IOMMU fix didn't work for you but it does seem to work for others - see post #12 in the link above

As I don't have that motherboard I can't add much more - maybe join one of the threads and ask a user with the same board who succeeded if there is anything else you need to do

---

