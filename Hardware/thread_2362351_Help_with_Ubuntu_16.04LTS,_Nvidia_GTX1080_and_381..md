---
title: "Help with Ubuntu 16.04LTS, Nvidia GTX1080 and 381.22 driver"
date: 2017-05-27
forum: Hardware
---

### Post by troopie on 2017-05-27
G'day folks.

I'm in need of help with nvidia drivers. I'm running a fresh install of Ubuntu 16.04LTS 64bit on a desktop and have had an Nvidia GTS450 fitted since before the install. All was good until I fitted a new GPU (GTX1080ti). With the old card I had choices under 'additional drivers', namely the Xorg open source driver or the Nvidia 375 driver; both worked.

Now that I've fitted the new card every thing fired up and works o.k. but:
-the GPU doesn't appear at all under 'additional drivers'.
-'Nvidia X Server Settings' lists the 375.39 driver as being used but refers to the card as 'GPU 0- (graphics device)'. As opposed to previously it would identify the old card by model.
-some programs will use the card, some will not. e.g. the desktop (unity) will use the card but Blender will not even acknowledge a GPU is available (main problem).

The 375 driver is the latest PPA but well predates my card so I'm guessing that's the issue? Not sure how it works but I'm guessing the driver doesn't know what the card is and Ubuntu et. al. are relying on the driver to find the card?

Anyway, after spending days trawling the web, forums and youtube I can't find any one else having this particular issue. Even if I could update through 'additional drivers' it would only find the same driver. All I can find is people having compatibility issues with on-board graphics on laptops or people fitting new cards/upgrading-o.s. and then having resolution/blackscreen errors etc or wanting to update drivers for their old cards on old ubuntu versions.

I have found a few confused and conflicting work arounds but they all seem inappropriate (not to mention dodgy) for the following reasons (some from this forum and 'askubuntu'):
-most use commands to get the driver as a PPA (no good to me; I have it).
-most do not say how to use the latest driver (.run file form Nvidia).
-some say completely remove old nvidia files, some say cuda files, some don't, some have different commands for doing this.
-some use a heap of commands that others don't and are mostly for old versions of ubuntu/different distros (how can I know which to include?).
--some use 'remove purge' (with and without extra elans - ?), some use 'purge remove', some use just 'remove', some use just 'purge'.
--some use blacklist first, some do not. some list specific files to blacklist some do not (would specific files from old tutorials be appropriate for me?).
--some use 'lightdm stop', some do not.
--some use 'chmod +x' some do not (if I enable 'allow executing....' via the gui desktop does this have the same effect?).
-some refer to 'several' files that need to be installed; e.g. 'cuda' (is that because they are deleting unnecessary files to start with? where would I get said files? would they just be part of the driver file?).

I have also tried this official ubuntu page: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?action=show&redirect=RestrictedDrivers%2FNVIDIAOfficial](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?action=show&redirect=RestrictedDrivers%2FNVIDIAOfficial)
 but it doesn't help, there is no mention of removing old stuff (is it necessary?) and the command 'sudo ubuntu-drivers devices' won't list my GPU.

Anyway, as a new user I am up against it and am asking only after much searching. Would anyone be kind enough to answer some questions and help out with a verbatim step by step solution?

I have the latest driver in my 'dowloads' file as a .run file (NVIDIA-Linux-x86_64-381.22.run).

Apologies if I'm just missing something really obvious. I know Nvidia drivers are a common problem but I really can't find an apt solution.

Desktop System;
Gigabyte G41M-D3
Intel Q9650
8gb DDR3
Ubuntu 16.04LTS 64bit

---

### Post by oldfred on 2017-05-27
Are you sure you have ppa?
This shows 381 as newest in ppa.
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

       #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab, if ppa should then show the 381.
ubuntu-drivers devices 

Remove normally deletes packages, but can save your settings or various hidden configurations.
purge deletes packages and related settings

You can only have one driver in kernel, see dkms above. So must purge older first.


 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by troopie on 2017-05-27
Thanks for replying but it still doesn't help or I am still missing something?

The link you provided includes 381 in the list but it is not 'clickable'?

From start to bottom of page the links do thus;
legacy drivers.
Volunteers for dev.
testing
testing
contribution
how to install a ppa
index of /graphics drivers/ppa/ubuntu which gives [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/) which gives [TABLE]
[TR]
[TD][/TD]
[TD][Parent Directory]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/")[/TD]
[TD][/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][artful/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/artful/")[/TD]
[TD="align: right"]10-May-2017 11:09[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][devel/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/devel/")[/TD]
[TD="align: right"]10-May-2017 11:09[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][precise/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/precise/")[/TD]
[TD="align: right"]19-Mar-2017 11:15[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][trusty/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/trusty/")[/TD]
[TD="align: right"]10-May-2017 11:35[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][vivid/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/vivid/")[/TD]
[TD="align: right"]15-Oct-2015 16:22[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][wily/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/wily/")[/TD]
[TD="align: right"]16-Aug-2016 13:33[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][xenial/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/xenial/")[/TD]
[TD="align: right"]10-May-2017 11:30[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][yakkety/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/yakkety/")[/TD]
[TD="align: right"]10-May-2017 11:09[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][zesty/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/dists/zesty/")[/TD]
[TD="align: right"]10-May-2017 11:09[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TH="colspan: 5"][HR][/HR][/TH]
[/TR]
[/TABLE]
 and [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/) which gives [TABLE]
[TR]
[TD][/TD]
[TD][Parent Directory]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/")[/TD]
[TD][/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][main/]("http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/main/")[/TD]
[TD="align: right"]25-Dec-2016 09:21[/TD]
[TD="align: right"]  -[/TD]
[TD][/TD]
[/TR]
[TR]
[TH="colspan: 5"][HR][/HR][/TH]
[/TR]
[/TABLE]

??  every link below that just goes to a user page?

I've no idea what all that is meant to mean but all the listings for 381 are not clickable.?

I don't know how to type the vertical slash you used here:
#What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab, if ppa should then show the 381.
ubuntu-drivers devices

I know what is currently installed: 375

System settings does not work; no GPU listed.

I have not installed anything manually; my current driver (375) was enabled through 'system settings (GUI)' with old card. do I still need to purge?

From my (limited research) bumblebee primus seems to relate only to laptops?

So I type this: sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

'sudo ubuntu-drivers devices' returns nothing but the cpu driver.


Then:
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX

So I just type this: sudo ubuntu-drivers autoinstall
And we're all good? we still haven't got the new driver have we?

The driver I need is in my downloads folder: computer/home/"me"/downloads

Sorry mate I really appreciate your time but I'm a bit slow, I must be missing something.

---

### Post by troopie on 2017-05-27
n.b. I have the 375.* driver installed (automatically through 'additional drivers' (so a ppa then? I dont know)) and 381.22 sitting as a *.run file in my 'downloads' folder.

---

### Post by Bucky Ball on 2017-05-27
Maybe you can start using [code] tags for code? I'm having trouble working out what's code and what's not as they're mashed together. One thing's for certain that I did notice from your first post, though; Blender should be seeing and using that card WITH full CUDA support. :)

See the link in my signature for how to insert code tags.

---

### Post by oldfred on 2017-05-27
The link is just to show that ppa has newer drivers.
You never click on a file in a ppa, but follow the directions to install the ppa which you say  you have done.

> [h=2][SIZE=2]Adding this PPA to your system[/SIZE][/h]                  You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:graphics-drivers/ppa**           to your system's Software Sources.           ([Read about installing]("https://launchpad.net/+help-soyuz/ppa-sources-list.html"))         
          sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update


Then you install using update commands as posted.
But best to see what you have installed already.

On my keyboard | is shift \ above the enter key.
But that can vary by keyboard. More info.
[https://ubuntuforums.org/showthread.php?t=1368997](https://ubuntuforums.org/showthread.php?t=1368997)

---

### Post by efflandt on 2017-05-28
It is better to use Ubuntu packages for graphics drivers, NOT .run files, so they are compatible with X and other programs. Once you add the ppa and *sudo apt-get update* (or Ubuntu 16.04 or newer can use **apt** or **apt-get**), the newer drivers should show up in Additional Drivers and you should be able to switch from there (then reboot). You should not even need xorg.conf unless you need to add something special and know what you are doing.

I am currently running nvidia-378 for my GTX 1060 and have not tried nvidia-381 yet.

---

### Post by troopie on 2017-05-28
Thanks very much for your patience and info oldfred I've got the 381 driver installed.

The decal on my keyboard for | is faulty and looks like an elonongated colon!  :) thanks!

A few hiccups though and for the benefit of any other beginners like me experiencing the same troubles I've listed the steps a little clearer:

So I got the ppa first from here: [https://launchpad.net/~graphics-driv...ive/ubuntu/ppa]("https://launchpad.net/%7Egraphics-drivers/+archive/ubuntu/ppa")

by typing this in terminal:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

and then this: (as per instructions on web site):
```
sudo apt-get update
```

Interestingly at this stage Ubuntu now began detecting my GPU and gave me driver options in the desktop and listed them in the terminal with:
```
sudo ubuntu-drivers devices
```

Next I switched to the Xorg driver through the desktop as it didn't feel right to be using the old proprietary driver whilst I was deleting it. (did I need to worry about this?)

I then ran:
```
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
```

Then next:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
But got a message that the path could not be found? looking at it now I may have missed the space after xorg.conf; The font in your original post makes it hard to see  :oops: Do I need to do something to fix this?

Then:
```
sudo apt-get install nvidia-381
```
and got the messages '*failed to fetch bbswitch...*' and '*failed to fetch prime...*'

I then selected the new driver from the desktop and restarted and all good.

I ran this again for good measure:
```
sudo apt-get update
```
And it turned up an extra Nvidia file. I didn't note the name of it but it was not one of ones that were listed as not fetched earlier.


My only problem now is that Blender still does not detect my GPU.

What does:
```
sudo apt-get update
```
actually do? Does it install what it finds, stick 'em in the corner 'till I tell the machine to use them or just list them for my general information?

@efflandt Thanks for clarifying the situation, I naively thought the .run file would be a better way to go.

---

### Post by troopie on 2017-05-28
@oldfred 
> -most use commands to get the driver as a PPA (no good to me; I have it).
I meant I had the driver (as .run file) not the ppa. untill today I hadn't installed any ppa's

---

### Post by oldfred on 2017-05-28
I regularly run the updates from command line. That is the same as when system says it wants to update software from gui.

This refreshes list from repository, I always change to a local repository for speed:
sudo apt update
This updates the software you have already installed to newest in repository, but not necessarily newest available version:
sudo apt upgrade


For more info see:
man apt
or 
man apt-get #older systems used this

As I posted above, old systems had this and they are trying to eliminate it. But occasionally still used to configure some device.
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by Yellow Pasque on 2017-05-28
Look at output of glxinfo to make sure driver is working (update-pciids just updates the strings for lspci):
```
sudo update-pciids
glxinfo | grep string
```

For GTX 1080, you supposedly need Blender 2.78 because it has CUDA 8 support:
[https://developer.blender.org/rB6353ecb996898b4ce2fe8065130ed1f5ea3b6989](https://developer.blender.org/rB6353ecb996898b4ce2fe8065130ed1f5ea3b6989)

---

### Post by troopie on 2017-06-01
All sorted and working thanks all and Temüjin for the blender tip. :p:p:p

I have one last naive question for future reference:

The links to ppa's I found on my own for the 'latest drivers' all turned up the 375 driver. How do I know where to look without bothering you all on the forum. As a paranoid ex-windows user I'm not inclined to just do a google search and click away. Especially with lines like this on the site I ended up using:

'You can update your system with unsupported packages from           this untrusted PPA by adding....'

---

### Post by oldfred on 2017-06-01
It is not an offical Ubuntu repository, so it is an untrusted ppa.
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 

Ppa shows newer drivers.
But sometimes the long lived branch is preferred as newest may not be tested even if released by nVidia.
You can probably purge and install by specifying version.
      
 Or you manually choose any in list.
sudo apt-get install nvidia-XXX  
    
From ppa:
> Current official release: `nvidia-381` (381.22)
Current long-lived branch release: `nvidia-375` (375.66)

---

