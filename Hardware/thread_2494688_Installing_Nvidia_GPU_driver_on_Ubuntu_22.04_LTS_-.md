---
title: "Installing Nvidia GPU driver on Ubuntu 22.04 LTS - which source is better?"
date: 2024-01-23
forum: Hardware
---

### Post by johnmne on 2024-01-23
There are two sources for Nvidia's GPU drivers:

1. The GPU drivers download webpage in Nvidia's website, i.e.:
[https://www.nvidia.com/en-gb/geforce/drivers/](https://www.nvidia.com/en-gb/geforce/drivers/)

2. The Ubuntu's "Additional Drivers" tab in the "Software & Updates" window.


Which of them should I choose to install an Nvidia's GPU driver?

---

### Post by #&amp;thj^% on 2024-01-23
If you go with nVidia drivers from Nvidia.com when the kernel gets an updated upgrade it will break your driver, and possibly your system.

the ones from Ubuntu are meant to work with all kernel upgrades seamlessly. (In Theory)

That should help in making a wise choice.

---

### Post by johnmne on 2024-01-24
> **1fallen said:**
> If you go with nVidia drivers from Nvidia.com when the kernel gets an updated upgrade it will break your driver, and possibly your system.

the ones from Ubuntu are meant to work with all kernel upgrades seamlessly. (In Theory)

That should help in making a wise choice.

Then it's better to use drivers provided by Ubuntu.
Thank you.

---

### Post by Yellow Pasque on 2024-01-24
> **1fallen said:**
> If you go with nVidia drivers from Nvidia.com when the kernel gets an updated upgrade it will break your driver, and possibly your system.

This shouldn't happen if you have dkms installed when you launch the .run file. (But yes, most people should use the packaged Nvidia version since it takes care of this caveat and several others.)

---

### Post by #&amp;thj^% on 2024-01-24
> **Yellow Pasque said:**
> This shouldn't happen if you have dkms installed when you launch the .run file. (But yes, most people should use the packaged Nvidia version since it takes care of this caveat and several others.)

Your right of course, but you and i have a bit more Linux savvy.
I just can't in good faith recommend the binary from nVidia to a newer user is all.

The best is from Ubuntu's repos for newer users.
```
nvidia-smi
Wed Jan 24 10:12:09 2024       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 545.29.06              Driver Version: 545.29.06    CUDA Version: 12.3     |

```
```
$apt policy nvidia-driver
nvidia-driver:
  Installed: (none)
  Candidate: 525.147.05-4
  Version table:
     525.147.05-5 600
        600 http://http.us.debian.org/debian unstable/non-free amd64 Packages
     525.147.05-4 650
        650 http://http.us.debian.org/debian testing/non-free amd64 Packages
     525.147.05-4~deb12u1 600
        600 https://deb.parrot.sh/parrot lory/non-free amd64 Packages
        600 https://deb.parrot.sh/parrot lory-updates/non-free amd64 Pac
```
I do know how to fix mine if it ever breaks though, and I have the mindset for this kind of frustration, but would a normal user?

---

### Post by johnmne on 2024-02-17
> **Yellow Pasque said:**
> This shouldn't happen if you have dkms installed when you launch the .run file. (But yes, most people should use the packaged Nvidia version since it takes care of this caveat and several others.)

> **1fallen said:**
> Your right of course, but you and i have a bit more Linux savvy.
I just can't in good faith recommend the binary from nVidia to a newer user is all.

The best is from Ubuntu's repos for newer users.
```
nvidia-smi
Wed Jan 24 10:12:09 2024       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 545.29.06              Driver Version: 545.29.06    CUDA Version: 12.3     |

```
```
$apt policy nvidia-driver
nvidia-driver:
  Installed: (none)
  Candidate: 525.147.05-4
  Version table:
     525.147.05-5 600
        600 http://http.us.debian.org/debian unstable/non-free amd64 Packages
     525.147.05-4 650
        650 http://http.us.debian.org/debian testing/non-free amd64 Packages
     525.147.05-4~deb12u1 600
        600 https://deb.parrot.sh/parrot lory/non-free amd64 Packages
        600 https://deb.parrot.sh/parrot lory-updates/non-free amd64 Pac
```
I do know how to fix mine if it ever breaks though, and I have the mindset for this kind of frustration, but would a normal user?


Thank you all!

Ubuntu has a list of drivers to choose from via the GUI of "Software & Updates" under the "Additional Drivers" tab.
I'm looking for the most stable and safe driver to choose.
Is it the topmost option?
Topmost option in my case is:
> Using NVIDIA driver metapackage from nvidia-driver-535 (proprietary, tested)

---

### Post by MAFoElffen on 2024-02-17
I've been using high-end NVidia GPU's with Unix and Linux since 2005.

I used to use the binary driver straight from NVidia. Noticed "used to". They are a pain to stay stable.

I can tell you that using Ubuntu's packaged NVidia drivers are simpler, easier to install and usually more stable. You have the Ubuntu support system standing behind you to help support them, since they were packaged by them (to a point). They are still 3rd Party binaries, which Ubuntu is just repackaging. 

They are less trouble, but still sometimes blow out with a major kernel updates, especially if you have the HWE stack installed and it changes kernel series. As a Linux User who has NVidia, just accept that they are work to stay working, occasionally.

What I advise new users is to learn how to add "nomodeset" into the commandline by editing the Grub2 menu... in the line that starts with the word "linux", right after the words "quiet splash". Or just toggle over to a vtty4 console session using <Cntrl><F4>...

Then remember these commands:
```

DRIVER=$(apt list nvidia-driver-* --installed 2>/dev/null | awk -F "/" '/nvidia-driver/ {print $1}')
sudo apt remove --purge nvidia* lib-nvidia*
sudo apt install --yes $DRIVER nvidia-dkms

```
That will remove the old drivers (recommended) and reinstall what you had installed, with the updated kernels. That will work 95% of the time. Nothing is 100%. There are sometimes challenges that come up. 

I try to stay up on current Linux Graphics Layer issues.

Now you have heard from the 3 different Members who I've seen support the most NVidia Users with issues on this forum... I feel all are correct and have good things to add, from their own years of experience and support of.

---

### Post by johnmne on 2024-02-18
> **MAFoElffen said:**
> I've been using high-end NVidia GPU's with Unix and Linux since 2005.

I used to use the binary driver straight from NVidia. Noticed "used to". They are a pain to stay stable.

I can tell you that using Ubuntu's packaged NVidia drivers are simpler, easier to install and usually more stable. You have the Ubuntu support system standing behind you to help support them, since they were packaged by them (to a point). They are still 3rd Party binaries, which Ubuntu is just repackaging. 

They are less trouble, but still sometimes blow out with a major kernel updates, especially if you have the HWE stack installed and it changes kernel series. As a Linux User who has NVidia, just accept that they are work to stay working, occasionally.

What I advise new users is to learn how to add "nomodeset" into the commandline by editing the Grub2 menu... in the line that starts with the word "linux", right after the words "quiet splash". Or just toggle over to a vtty4 console session using <Cntrl><F4>...

Then remember these commands:
```

DRIVER=$(apt list nvidia-driver-* --installed 2>/dev/null | awk -F "/" '/nvidia-driver/ {print $1}')
sudo apt remove --purge nvidia* lib-nvidia*
sudo apt install --yes $DRIVER nvidia-dkms

```
That will remove the old drivers (recommended) and reinstall what you had installed, with the updated kernels. That will work 95% of the time. Nothing is 100%. There are sometimes challenges that come up. 

I try to stay up on current Linux Graphics Layer issues.

Now you have heard from the 3 different Members who I've seen support the most NVidia Users with issues on this forum... I feel all are correct and have good things to add, from their own years of experience and support of.

So I understand that the choice of "nvidia-driver-535 (proprietary, tested)" should be stable among the other driver choices?
I fear of driver issues and don't want to get locked out of my OS because of it.

Regarding:

> What I advise new users is to learn how to add "nomodeset" into the  commandline by editing the Grub2 menu... in the line that starts with  the word "linux", right after the words "quiet splash". Or just toggle  over to a vtty4 console session using <Cntrl><F4>...

Then remember these commands:
```

DRIVER=$(apt list nvidia-driver-* --installed 2>/dev/null | awk -F "/" '/nvidia-driver/ {print $1}')
sudo apt remove --purge nvidia* lib-nvidia*
sudo apt install --yes $DRIVER nvidia-dkms

```
That will remove the old drivers (recommended) and reinstall what you  had installed, with the updated kernels. That will work 95% of the time.  Nothing is 100%. There are sometimes challenges that come up. 

I should perform it only in case that an issue happens with the graphics driver, correct?

Honestly I don't think that I'll remember it.
I'll need to write it somewhere.

If I understand correctly, the "rescue" method in case of a driver issue is as follows:
1. Perform the "nomodeset" thing via the GRUB menu during boot - to be able to boot into OS.
2. Perform the re-installation of Nvidia drivers.

Should the same commands work properly when Secure Boot is enabled?

Thank you for all those details!

---

### Post by MAFoElffen on 2024-02-18
nvidia-driver-535 is currently the most stable driver for most recent model NVidia GPU's within the past few years. It is stable. That is what I use on my daily driver.

Yes. Just when something goes wrong. Print out those directions for an emergency... 

Another way to easily start a Desktop in safe mode is to, at the Grub2 Menu > Select "Advanced Options" > Select any kernel with Recovery Mode > select "continue"... That will automatically insert "nomodeset" into the kernel boot line, as a boot parameter.

A good read for graphics diagnostic and solving graphics issues is in the "Installations & Upgrades" Section > "Graphics Resolution" sticky (The first 3 posts). That would give you miles of information explaining how things work, how to diagnose problems, and many work-arounds. 

It is boots to a black screen or gets a blackscreen after the Graphical Login... First thing to do is to simultaneously press the keys <Cntrl><F4>. If that goes to a vtty4 console prompt, then the kernel booted and it's a graphics problem.

After starting in safe mode, you can always (alternatively) go to the GUI "Additional Drivers" tab of "Software & Updates" and select your driver from there. In Ubuntu, there is 4-5 different ways to install NVidia drivers from the 3rd party Repo's. That is just for the standard drivers for those.

---

### Post by johnmne on 2024-02-23
> **MAFoElffen said:**
> nvidia-driver-535 is currently the most stable driver for most recent model NVidia GPU's within the past few years. It is stable. That is what I use on my daily driver.

Yes. Just when something goes wrong. Print out those directions for an emergency... 

Another way to easily start a Desktop in safe mode is to, at the Grub2 Menu > Select "Advanced Options" > Select any kernel with Recovery Mode > select "continue"... That will automatically insert "nomodeset" into the kernel boot line, as a boot parameter.

A good read for graphics diagnostic and solving graphics issues is in the "Installations & Upgrades" Section > "Graphics Resolution" sticky (The first 3 posts). That would give you miles of information explaining how things work, how to diagnose problems, and many work-arounds. 

It is boots to a black screen or gets a blackscreen after the Graphical Login... First thing to do is to simultaneously press the keys <Cntrl><F4>. If that goes to a vtty4 console prompt, then the kernel booted and it's a graphics problem.

After starting in safe mode, you can always (alternatively) go to the GUI "Additional Drivers" tab of "Software & Updates" and select your driver from there. In Ubuntu, there is 4-5 different ways to install NVidia drivers from the 3rd party Repo's. That is just for the standard drivers for those.

I found the Recovery mode of the additional kernels in GRUB menu!
Now it feels safer to try the NVIDIA driver installation.

Regarding:
> 
First thing to do is to simultaneously press the keys <Cntrl><F4>. 

In my case, the keys for entering a text console ("vtty4") while I was in (standard) Desktop were:
<Cntrl>+<Alt>+<F4>

I was thinking about an additional approach in case of an emergency - if I would have an integrated graphics (in my CPU; "iGPU"): 
Would connecting the cable of the display to the iGPU (instead of to the GPU RTX 4060) help to overcome issues with the display driver in case that the boot to Desktop fails?


I appreciate your help!!

---

