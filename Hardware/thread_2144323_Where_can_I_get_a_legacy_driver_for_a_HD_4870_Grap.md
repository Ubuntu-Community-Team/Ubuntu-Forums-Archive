---
title: "Where can I get a legacy driver for a HD 4870 Graphics card for Ubuntu 12.04 64 bit?"
date: 2013-05-11
forum: Hardware
---

### Post by sir_robert007 on 2013-05-11
So after trying to install the proprietary drivers for my HD 4870 cards and twice breaking my system I learned the hard way that AMD no longer supports the HD 4870 in Linux. Does anyone know where I can get a legacy driver that will work the the 4870? I tried using the Additional Drivers app but that ended up breaking my system. Reverted back to open source drivers. If I cant find a legacy driver will Team Fortress 2 still work with the open source drivers?

Comp Specs:

OS: Ubuntu 12.04 64 bit
Graphics: HD 4870 1GB (Crossfire)
RAM: 4GB
Processor: AMD Phenom X4 2.6 GHZ

---

### Post by Mark Phelps on 2013-05-12
The link below should work (but ONLY if you are using 12.04.1):  

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx")

If you are using 12.04.2, you're out of luck  because that uses a new X-server version that is incompatible with the drivers from this link.

---

### Post by Yellow Pasque on 2013-05-12
> **Mark Phelps said:**
> If you are using 12.04.2, you're out of luck  because that uses a new X-server version that is incompatible with the drivers from this link.

False, 12.04.2 users can easily revert back to the 3.2.x kernel and Xserver 1.11.x
```
sudo apt-get install xserver-xorg-lts-precise
sudo apt-get purge xserver-xorg-lts-quantal xserver-xorg-lts-raring linux-generic-lts-quantal linux-generic-lts-raring
```
Reboot and install driver.

---

### Post by Mark Phelps on 2013-05-12
> **Temüjin said:**
> False, 12.04.2 users can easily revert back to the 3.2.x kernel and Xserver 1.11.x
```
sudo apt-get install xserver-xorg-lts-precise
sudo apt-get purge xserver-xorg-lts-quantal xserver-xorg-lts-raring linux-generic-lts-quantal linux-generic-lts-raring
```
Reboot and install driver.

Right ... and what do they do when they get kernel upgrades after that?

---

### Post by Yellow Pasque on 2013-05-12
They don't if they remove the packages listed... (they'll only get 3.2.x updates).

---

### Post by Mark Phelps on 2013-05-13
> **Temüjin said:**
> They don't if they remove the packages listed... (they'll only get 3.2.x updates).

OK, so if this is so simple and they are not faced with problems related from un-asked-for kernel upgrades, why do others so strongly recommend against doing this kind of driver installation?  Any ideas? (Asking because I'm in a similar situation and would like do this -- but have held off).

---

### Post by Yellow Pasque on 2013-05-13
> **Mark Phelps said:**
> OK, so if this is so simple and they are not faced with problems related from un-asked-for kernel upgrades, why do others so strongly recommend against doing this kind of driver installation?  Any ideas? (Asking because I'm in a similar situation and would like do this -- but have held off).
Probably because it's a lot easier just to tell people that they can't use 12.04.2 with the legacy driver. Quite frankly, I'm not sure the commands I've offered will completely preclude future kernel/X upgrades (from Ubuntu 13.10/saucy for example). There may be some metapackage that I'm not aware of that pulls these things in (I only run precise in a VM) or Ubuntu 12.04.2 may not come with the 3.2 kernel at all. However, I like to think that most of the users I'm giving this advice to can figure these things out for themselves ("Hmm, maybe I shouldn't install that xserver-xorg-lts-saucy package...")

---

### Post by snafu006 on 2013-05-13
go to here and download driver: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

after download unzip driver and place on desktop
open terminal ctrl-alt-t

sudo amdconfig --uninstall
(just so there is nothing to mess this up)

just drag and drop unzip ati driver into terminal will look like this

example:'/home/_**[COLOR=#ff0000]YOUR-USER-NAME[/COLOR]**_/Desktop/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run'

BUT change to this:

sudo sh '/home/_**[COLOR=#ff0000]YOUR-USER-NAME[/COLOR]**_/Desktop/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run' --force
hit enter
enter password

And ever tho the two guys above me are fight over what kernel you are on.  They are right you should be on kernal 3.2.0.41 anything like 3.5.0.? the driver will not work 

command for terminal: uname -a

OOOOOO AND P.S this computer i am on can run steam and will play all steam linux game ATI 4250 HD Good luck

---

### Post by QIII on 2013-05-13
I have the two following reasons I do not recommend the scripts that downgrade X Server, patch the kernel and install the legacy driver:

1.  None of us knows *for certain *what will happen in future upgrades or updates that will conflict with or cause dependency problems with the changes.

2.  12.04 and 12.04.1 are supported for another 4 years.  In that time, a user can enjoy Ubuntu without risking a fatal crash due to the changes.  

Just my two cents.

---

### Post by QIII on 2013-05-13
> **snafu006 said:**
> go to here and download driver: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

after download unzip driver and place on desktop
open terminal ctrl-alt-t

sudo amdconfig --uninstall
(just so there is nothing to mess this up)

just drag and drop unzip ati driver into terminal will lokk like this

example:'/home/_**[COLOR=#ff0000]YOUR-USER-NAME[/COLOR]**_/Desktop/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run'

BUT change to this:

sudo sh '/home/_**[COLOR=#ff0000]YOUR-USER-NAME[/COLOR]**_/Desktop/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.run' --force
hit enter
enter password

And ever tho the two guys above me are fight over what kernel you are on.  They are right you should be on kernal 3.2.0.41 anything like 3.5.0.? the driver will not work 

command for terminal: uname -a

Unfortunately, this will *not work *for 12.04.2 and beyond without downgrading X Server and replacing the kernel.

---

### Post by snafu006 on 2013-05-13
what did i just put in there look at the post

---

### Post by QIII on 2013-05-13
While your answer made perfect sense to Temujin, Mark Phelps, you and me, my concern is that a newer user will likely be less familiar with kernel versions than even their version of Ubuntu.  But he might understand the difference between 12.04, 12.04.1 and 12.04.2.

Your answer was correct, of course.  But it might not be clear to a newer user.  My response was a clarification.

---

### Post by snafu006 on 2013-05-13
```
I have the two following reasons I do not recommend the scripts that  downgrade X Server, patch the kernel and install the legacy driver:

1.  None of us knows *for certain *what will happen in future upgrades or updates that will conflict with or cause dependency problems with the changes.

2.  12.04 and 12.04.1 are supported for another 4 years.  In that time, a  user can enjoy Ubuntu without risking a fatal crash due to the changes.   

Just my two cents. 				
```

i get what you are saying but you know that only draw back linux/ubuntu has is they mess with that dam X.org file. If amd ati is saying here the driver for your card you should be able to install it with out doing all this crap FIX it!!!!

---

### Post by QIII on 2013-05-13
As frustrating as it may be, Canonical cannot fix a closed source driver.

The Radeon driver developers are making a Herculean effort.  That is what the open source community can do.

I am disappointed with AMD/ATI, but they have made a business decision they believe to be in the best commercial interest of their company.

The Linux community, for its part, cannot be held hostage by AMD's actions and simply decide not to move forward.

Further, Ubuntu didn't mess with X.  That is the business of the X.Org Foundation.

---

### Post by sir_robert007 on 2013-05-14
> **QIII said:**
> I have the two following reasons I do not recommend the scripts that downgrade X Server, patch the kernel and install the legacy driver:

1.  None of us knows *for certain *what will happen in future upgrades or updates that will conflict with or cause dependency problems with the changes.

2.  12.04 and 12.04.1 are supported for another 4 years.  In that time, a user can enjoy Ubuntu without risking a fatal crash due to the changes.  

Just my two cents.


So do u know where i can get Ubuntu 12.04.1? The only version that I see as being available to download is 12.04.2 unless there is a link to 12.04.1 that im not aware of.

---

### Post by sir_robert007 on 2013-05-14
Ok i just found a link to 12.04.1. For anyone else having this problem here is the link [http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/). I will try this out and report back.

---

### Post by Yellow Pasque on 2013-05-14
> **QIII said:**
> The Linux community, for its part, cannot be held hostage by AMD's actions and simply decide not to move forward.

Nonsense! I'm still running Ubuntu 8.04 because I need Catalyst 9-3 to play gamez on my Radeon X600. Everyone else should be held back too!

---

### Post by QIII on 2013-05-14
I haven't upgraded from Warty.

---

### Post by Mark Phelps on 2013-05-14
> **QIII said:**
> I have the two following reasons I do not recommend the scripts that downgrade X Server, patch the kernel and install the legacy driver: ... Just my two cents.

Thank you for your response.

---

### Post by sir_robert007 on 2013-05-14
Ok so I am now on Ubuntu 12.04.1. Just finished installing drivers however I dont know if 3D acceleration is enabled. I ran /usr/lib/nux/unity_support_test -p to see if 3D is enabled and this was my output.


```

robert@hawaii50:~/.local/share/Steam$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series        
OpenGL version string:  3.3.11672 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


```

So it seemas as if it works but when I installed and ran Steam I ran into this error message:

```

OpenGL GLX context is not using direct rendering, which may cause performance problems.

For more information visit https://support.steampowered.com/kb_article.php?ref=9938-EYZB-7457.

```


Is there any additional configuration steps I have to perform? Gonna install Team Fortress 2 and see if it works.

---

### Post by Mark Phelps on 2013-05-15
Been a long time since I used the fglrx driver, but you used to be able to enter the command "fglrxinfo" and it would tell you whether or not it was doing direct rendering.  You could try that.

---

### Post by sir_robert007 on 2013-05-15
> **Mark Phelps said:**
> Been a long time since I used the fglrx driver, but you used to be able to enter the command "fglrxinfo" and it would tell you whether or not it was doing direct rendering.  You could try that.


Ok I tried that. Here is my output:

```

robert@hawaii50:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series        
OpenGL version string: 3.3.11672 Compatibility Profile Context

```

---

### Post by sir_robert007 on 2013-05-21
Yay! So I finally got it working!! Realized that I had forgotten to install the [FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]ia32-libs-multiarch i386 lib32gcc1 libc6-i386 packages as well as the other dependencies as explained in this guide: [/FONT][http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx) Purged fglrx drivers, installed the dependencies and now Team Fortress 2 works!!

Thanks for the help everyone!! Its help like this that keeps me coming back to the Ubuntu Forums.

---

### Post by Madvil on 2013-05-26
Hello,

I did the exact same things that sir_robert007 did and worked fine (install 12.04.1 LTS, ATI Catalyst etc.) but I'm not sure about the things that are ok to update. Is it safe to run the update manager or is there a possibility that an update that breaks the driver installation will be applied, rendering the whole thing useless?

---

### Post by Yellow Pasque on 2013-05-26
@Madvil: Run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Post the output of the dist-upgrade command (do not confirm yes to the upgrade just yet).

---

### Post by snafu006 on 2013-05-26
DO NO UPDATE ANYTHING thats for Kernel or X.org Xserver if you do you break the Video driver. To workaround that uninstall ATI driver First then reboot, update, upgrade then reboot reinstall driver.


just sucks because this video card i have run's better on here then on windows (diablo 3 windows avg fps 20 on linux running diablo 3 in wine fps 32 ) but the driver support from F-UP AMD SUCKS

---

### Post by Yellow Pasque on 2013-05-26
> **snafu006 said:**
> DO NO UPDATE ANYTHING thats for Kernel or X.org Xserver
That's oversimplified. Users will want the security/bug updates. They just need to stay on 3.2.x kernel and Xserver 1.11.x

---

