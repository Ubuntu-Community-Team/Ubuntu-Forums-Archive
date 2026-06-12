---
title: "Touchpad not detected on Dell E5510"
date: 2010-08-17
forum: Hardware
---

### Post by Fiery Spirited on 2010-08-17
I am using Ubuntu 10.4 on a Dell Latitude E5510 computer. My first experience of using Ubuntu on a laptop. The installing experience was pretty smooth with almost everything working out of the box. The exception is the touchpad that is not recognized properly.

The touchpad is from my understanding using Macintosh Mouse emulation. This means it works in fashion, meaning you can point and click on things. Problem is that I don't get any configuration tab for the touchpad so I can't activate essential functionality like the touchpad being disabled when I type. This makes the cursor jump around randomly, very annoying.

I am not sure about what brand of touchpad I have, but I think that might be an Alps one since I have seen this brand mentioned together with Latitude computers.

How can i verify what brand of touchpad I have? What can I do to resolve the problem?

---

### Post by djwohls on 2010-09-03
Bump.  Same issue on Dell Latitude E6410.  It is an Alps touchpad (with multitouch) according to Windows.

---

### Post by aa-hcl on 2010-09-20
> **Fiery Spirited said:**
> I am using Ubuntu 10.4 on a Dell Latitude E5510 computer. My first experience of using Ubuntu on a laptop. The installing experience was pretty smooth with almost everything working out of the box. The exception is the touchpad that is not recognized properly.

The touchpad is from my understanding using Macintosh Mouse emulation. This means it works in fashion, meaning you can point and click on things. Problem is that I don't get any configuration tab for the touchpad so I can't activate essential functionality like the touchpad being disabled when I type. This makes the cursor jump around randomly, very annoying.

I am not sure about what brand of touchpad I have, but I think that might be an Alps one since I have seen this brand mentioned together with Latitude computers.

How can i verify what brand of touchpad I have? What can I do to resolve the problem?


I have the same problem with my Dell E5510. Can you please post the solution if you manage to it?  Many thanks!

---

### Post by aa-hcl on 2010-09-21
> **aa-hcl said:**
> I have the same problem with my Dell E5510. Can you please post the solution if you manage to it?  Many thanks!


just to say that I managed to get it working, but only under ubuntu live stick...  

see more detailed discussions in 

[http://ubuntuforums.org/showthread.php?p=9871231](http://ubuntuforums.org/showthread.php?p=9871231)

....

I am still trying to find out how to get the touchpad properly detected when I boot normally..

---

### Post by Fiery Spirited on 2010-10-31
In the following Kernel discussion they are working to understand the protocol of new multitouch Alps TouchPads
[https://bugzilla.kernel.org/show_bug.cgi?id=14660](https://bugzilla.kernel.org/show_bug.cgi?id=14660)

There seems to be a patch developed together with Dell to get scrolling  to work to some degree on at least some of the new Alps models, but it is still a emulation mode. I am bit  a hesitant to try that one since I am not very comfortable with patching  the kernel. The lack of scrolling is not a big deal for me. Multitouch  support would be a different thing...

The right launchpad issue for this problem is as far as I can tell btw [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/606238]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606238") One useful thing in that thread is the script toggleps2.sh that can be used to turn of the touchpad when you intend to type. I did bind it to key-shortcut and can thus turn of the twitchy touchpad when I intend to type longer passages.

---

### Post by ERIC H on 2010-10-31
Thanks for the update. Just got an E5510 from work and installing 10.10 is like night and day compared to Lucid with the exception of the touchpad issues.

---

### Post by aa-hcl on 2010-10-31
> **Fiery Spirited said:**
> In the following Kernel discussion they are working to understand the protocol of new multitouch Alps TouchPads
[https://bugzilla.kernel.org/show_bug.cgi?id=14660](https://bugzilla.kernel.org/show_bug.cgi?id=14660)
 
There seems to be a patch developed together with Dell to get scrolling to work to some degree on at least some of the new Alps models, but it is still a emulation mode. I am bit a hesitant to try that one since I am not very comfortable with patching the kernel. The lack of scrolling is not a big deal for me. Multitouch support would be a different thing...
 
The right launchpad issue for this problem is as far as I can tell btw [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/606238]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606238") One useful thing in that thread is the script toggleps2.sh that can be used to turn of the touchpad when you intend to type. I did bind it to key-shortcut and can thus turn of the twitchy touchpad when I intend to type longer passages.
 
Many thanks for the update and the info about the toggleps2.sh script! it is really useful!!!
 
Another questions about E5510 - did you you manage to get the SD card reader working? Many thanks!!!!

---

### Post by aa-hcl on 2010-10-31
> **ERIC H said:**
> Thanks for the update. Just got an E5510 from work and installing 10.10 is like night and day compared to Lucid with the exception of the touchpad issues.
 
Does it mean that touchpad does NOT work under 10.10?
 
Another question:  does the SD card reader work under 10.10?
 
Many thanks!

---

### Post by Fiery Spirited on 2010-11-03
> **aa-hcl said:**
> Does it mean that touchpad does NOT work under 10.10

If you check the release schedule of Ubuntu [https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule) you will see that they by 16 September did Final Freeze and Kernel Freeze. This mean that any development that happened after that will not be included in the release of 10.10. X.Org develors did on their mailing list discuss how to get multitouch working in middle of October. I have not patience to really sort out how far they have come, but they seems to be making great progress. 

It seems likely that when the X.Org guys have managed to make use of the improvements in the Kernels handling of MultiTouchPads the guys using Archlinux and similar will get it working first and eventually some Ubuntu-guru will post an explanation on the bug threads about how to perform the necessary upgrades to get the fix in both 10.04 and 10.10.

---

### Post by Fiery Spirited on 2010-11-03
> **aa-hcl said:**
> Another questions about E5510 - did you you manage to get the SD card reader working? Many thanks!!!!

I have no use of the SD card reader so I have really not tried.

---

### Post by nrune on 2010-11-30
Can someone please post the toggleps2.sh script. launch pad is giving errors and this touchpad is driving me nuts.

Thanks

Never mind got it from launchpad.  Thanks!

---

### Post by msifakis on 2010-12-13
> **aa-hcl said:**
> 
 
Another question:  does the SD card reader work under 10.10?
 
Many thanks!

Hi aa-hcl following the instructions:  [https://bugs.launchpad.net/debian/+source/linux-2.6/+bug/605043](https://bugs.launchpad.net/debian/+source/linux-2.6/+bug/605043)

I managed to have it work!
take a look at posts #7 and #24

cheers

---

### Post by theopulus on 2010-12-21
any progress regarding these 2 issues? Touchpad and SD are quite important for me in my day by day work...

---

### Post by aa-hcl on 2011-01-05
SD card:  NOW solved!!!

 to fix the SD card reader we need the following:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605043)

see #10  for the correct filename

Solution:  create the file "sdhci-pci.conf" that contains one single line "options sdhci debug_quirks=0x40" in a directory "/etc/modprobe.d" 

root@aa-i3:/etc/modprobe.d# cat ./sdhci-pci.conf 
options sdhci debug_quirks=0x40

and then reload the modules:

root@aa-i3:/etc/modprobe.d# rmmod sdhci-pci
root@aa-i3:/etc/modprobe.d# rmmod sdhci
root@aa-i3:/etc/modprobe.d# modprobe sdhci-pci

(or reboot)

and the SD card now works...

---

### Post by aa-hcl on 2011-01-05
Touchpad:  still NOT working.... I am at the moment waiting for the possible solution, see also 

[http://newyork.ubuntuforums.org/showthread.php?t=1655339&](http://newyork.ubuntuforums.org/showthread.php?t=1655339&)

hopefully it will be re-solved since it did work on earlier versions of ubuntu...

meanwhile I am using the script to disable the mouse

---

