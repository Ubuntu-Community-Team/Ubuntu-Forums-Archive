---
title: "Ubuntu and Nvidia Optimus for Laptops"
date: 2010-10-01
forum: Hardware
---

### Post by curryking1 on 2010-10-01
Hi,

I have a MSI laptop. The model number is FX600-002US.

This laptop uses the Nvidia-Intel Optimus technology which means the laptop has two graphics cards: one Nvidia chip and one Intel chip. The technology is supposed to allow dynamic switching between the two chips to save or exert more power depending on the task.

My laptop has a Nvidia 325M. I'm not sure which model is the Intel chip, though the CPU is an Intel i5 450M, so whichever model comes with this CPU.

Anyway, to the point... the problem is a few days after installing Ubuntu 10.04, I started getting black screens whenever I launched into the OS. The black screen would come after the Ubuntu splash page with the five dots running below it. I cannot get to the login screen anymore.

Also, there is discolouration of this Ubuntu splash page, which was not there when I was sometimes able to get into Ubuntu on the laptop.

The interesting thing is that I could get Ubuntu to install without a problem (I couldn't see anything wrong during install), so I assumed it was going to work after that. For a few days, I was able to use Ubuntu 10.04 without any issues.

Also, Ubuntu does not detect a Nvidia driver should be installed with my laptop.

At one point I did try to install the Nvidia drivers, but I failed, because I am not very computer literate. I don't know how to install Nvidia drivers without it being automatically detected by the Registered Drivers thing in Ubuntu. I may have done something here to cause issues, but I can't really remember what I did. I don't think I did anything to fabulous anyway.

I would just like to know if there is a way to get Ubuntu 10.04 working on a laptop with Optimus.

Any assistance with or information about this issue would be really helpful.

I was also wondering if Ubuntu 10.10 or any Ubuntu version in the future will be able to support Nvidia Optimus.

Cheers.

---

### Post by M2-player on 2010-10-10
Hi,

I have CPU Intel 450M, GPU nVidia GeForce GT 335M and Intel HD Graphics. In Win7 I use Optimus technology.

Today I installed Ubuntu 10.10, everything goes fine while I installed driver for nVidia. Now I do not have GUI. I just see terminal, like when you press Ctrl+Alt+F1 (F1-F6, F7 is Desktop I think).

Is there any solution for it? Something like Optimus for Linux? In the end I can remove that driver for nVidia and run on Intel graphic (rather I would remove driver for Intel graphic).
But I need help, I am newbie :P

---

### Post by Arcitens on 2010-10-15
Have a friend who is also having this problem. Anyone have a fix?

---

### Post by ekarasik on 2010-10-15
Unfortunately, there is no support for nvidia/intel hybrid graphics in linux yet. Do not install the nvidia driver.
The most you can do is to disable the nvidia card, to save battery. (the nvidia card actually still runs, even when you work with intel card)
look here - [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

---

### Post by CMOS4081 on 2010-10-15
Please excuse my ignorance in this issue but:
1)Is their any option in BIOS to specify which GPU you wish to use as the primary adaptor?
2)Would it be possible to disable/un comment/ un check the Intel in the Xorg.conf file?
3)Is there any advise on Nvidia's forums?

Edit: I remembered that they have a similar feature on a few motherboards for desktops called hybrid power. 
It might give a clue.
(But this was I believe limited to using onboard nvidia graphics with an higher end add on nvidia graphics card.)

EDIT2: It seems only the Intel IGP has a physical connection to the display and the Nvidia GPU output is handled thru a multiplexer that sends it's output into the memory of the Intel IGP, which in turns displays. (Reminds me of using a regular 2D VGA card plus a Voodoo graphics card from 3DFx for OpenGL/Glide from back in the day)

In other words, this is software related, and tied to Windows Vista and Windows 7. 
I don't know if there would be a work around in Linux, but again I'm no programmer/hardware guru...

---

### Post by curryking1 on 2010-10-20
If the Nvidia driver is incompatible, I will just try a fresh install of Ubuntu and try to disable the Nvidia GPU.

I don't think there is an option in BIOS for my laptop to choose which graphics card is running.

I haven't posted on Nvidia's forum about this issue yet. I think I will try that soon.

Thanks for all the new input.

---

### Post by thehero on 2010-11-03
If you have Nvidia Optimus and have installed the nvidia driver you don't need to reinstall to fix X. Boot into recovery mode from grub and start failsafe-X. Once X is started go to additional drivers under system > administration and uninstall the nvidia binary driver. You may have to remove the xorg.conf file as well. Move the file by typing "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old". This will not delete the file but instead move it in case you want it later.

Now reboot and the Intel driver should be working again.

---

### Post by thehero on 2010-11-03
Also take a look at your bios settings. I know on my Lenovo T410s that has Nvidia/Intel Optimus technology that I have the option to choose Optimus/Integrated/Discrete graphics. 

When in your bios make sure you have supervisor or administrator level access if your bios has this option. Some machines have the user level access and supervisor level access.

---

### Post by curryking1 on 2010-12-10
Hi again,

I haven't made that thread on Nvidia's forum yet unfortunately, though I will try to as soon as possible.

Also unfortunately, my laptop does not have the option to disable the Intel graphics or Nvidia graphics and use only one display adapter in the BIOS settings as much as I can tell so far. I've tried a few times. I do not know if a MSI BIOS update can open this feature for me though, because I have not yet tried this.

---

### Post by curryking1 on 2011-01-02
I found a thread complaining about this issue on the official Nvidia forums. Here is the link: [http://forums.nvidia.com/index.php?showtopic=188184&pid=1170075](http://forums.nvidia.com/index.php?showtopic=188184&pid=1170075)

If you also have concerns about this issue, please contribute to this thread on Nvidia's forums.

I will also look for another way to contact Nvidia through customer support. I will update this thread if I get any worthwhile response from Nvidia. Hopefully we will get something.

Cheers. Happy New Year everyone :)

---

### Post by 3602 on 2011-01-02
Made a [thread]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus") attempting to explain these issues.

---

### Post by gfreeau on 2011-02-05
Is it possible to setup two grub entries, one that is setup for discrete/nvidia and intergrated so depending on the situation we could make the switch in the bios and boot into linux?

I'm running on the discrete setting at the moment, it would handy to use an integrated version sometimes to save power.

---

### Post by ac90b671 on 2011-03-01
This is not possible. The way the technology works, the Intel unit has access to the monitor. When performance is needed, the nvidia gpu turns on and does the rendering and sends the data to the intel gpu but the intel gpu still acts as a relay to the monitor. Thus there is no way to have only the nvidia gpu on because it cannot access the monitor without some serious drivers. The only way I see linux support is for nvidia to release driver support (I imagine they will eventually) or serious reverse engineering (I imagine would be extremely difficult). You can read the white papers on optimus here if you like: [http://www.nvidia.com/object/LO_optimus_whitepapers.html](http://www.nvidia.com/object/LO_optimus_whitepapers.html)

---

### Post by asuslap on 2011-03-06
Greetings and Salutations,

So I read some info on this forum to get my Ubuntu 10.10 installation to actually run the nvidia driver. With an Asus UL80JT, I went into BIOS (press f2 at ASUS logo), advanced, select "boot VGA Controller Selection" and changed it from "Windows 7" to "others". Then I booted into Ubuntu and accepted to enable by NVIDA driver (it asked). It then installed the driver for me and once I rebooted again the 3d acceleration was working. I see I have an xorg.conf stating the driver is nvidia so I assume I am using the actual driver. I recognize not having this hybrid feature deal but at least I have 3d stuff running. Thank you!

---

### Post by martin-juhl on 2011-05-04
[http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/](http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/)

or

[https://github.com/MrMEEE/prime-ng](https://github.com/MrMEEE/prime-ng)

---

### Post by unrater on 2011-06-18
> **martin-juhl said:**
> [http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/](http://www.martin-juhl.dk/2011/05/optimus-on-linux-problem-solved/)

or

[https://github.com/MrMEEE/prime-ng](https://github.com/MrMEEE/prime-ng)

Hi Martin, this is so so cool!

Well, I would like to propagate your work (in [ubuntued]("http://ubuntued.info/")) because I saw that it really works, but I would like to propagate it only when we have a repository with a simple installation process. So when can we have that?

---

### Post by curryking1 on 2011-06-18
Thanks for the work, Martin!

I've tried it myself. I am currently running Ubuntu 11.04 on my MSI FX600-002US laptop. It has a 325M Nvidia card.

I've been able to install the files you offered with the Bumblebee package.


The only problem is I am not sure if I have got it to work or not yet. 

I haven't tried any 3D applications or anything, and I'm not sure if I need to do any special commands. Ubuntu is at least working away on my laptop.

What should I be doing to test whether or not I can use my Nvidia card with Optimus in Ubuntu now? What are some good diagnostic tests or applications I should run?

And just to be sure, I don't have to install any other files than Bumblebee for Optimus to work do I (such as the Restricted Nvidia Driver)?

Cheers, and thanks a lot for your work.

---

### Post by martin-juhl on 2011-06-19
@unrater

The installer script from:

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

Should be easy to install... I have a ppa coming up with bumblebee, hopefully within the next few weeks...

@curryking1

You can test bumblebee by running:

optirun glxgears

there should be a performance boost compared to just running:

glxgears


Please report any bugs at:

[https://github.com/MrMEEE/bumblebee/issues](https://github.com/MrMEEE/bumblebee/issues)

---

### Post by kaloy on 2011-07-10
hi everyone, just to clarify, if I dont install the nvidia driver, is it only using the intel graphics chip. I really wouldnt mind if this was the case. Thanks!

---

### Post by foutes on 2011-07-10
> **kaloy said:**
> hi everyone, just to clarify, if I dont install the nvidia driver, is it only using the intel graphics chip. I really wouldnt mind if this was the case. Thanks!

Both will be running and if you are on a laptop/netbook this means about half the battery life.

If you install the bumblebee script it will install the nvidia driver and scripts to turn off and on the nvidia card so that only the intel card is running which means you get 50% extra battery life.

You have to use the optirun command to turn on the nvidia chip as default is off.

---

### Post by formylove on 2011-07-10
I have a the same problem.hope I can get a good answer.

---

### Post by kaloy on 2011-07-10
> **foutes said:**
> Both will be running and if you are on a laptop/netbook this means about half the battery life.

If you install the bumblebee script it will install the nvidia driver and scripts to turn off and on the nvidia card so that only the intel card is running which means you get 50% extra battery life.

You have to use the optirun command to turn on the nvidia chip as default is off.

Oh now I understand, thats why my laptop is so how even if I was just running a browser and a text editor, thanks thanks for the info and will definitely give Bumblebee a try. Cheers!

---

### Post by obscurant1st on 2011-09-27
so far the only option is trying the bumblebee. If you want to recover from the black getting batteryu status screen, just press ctrl+alt+f1.
there delete the /etc/X11/xorg.conf file, reboot!
Thats it, Now the system will work!

---

### Post by gewone on 2012-01-11
Would have been nice if 'Buntu 12.04 had introduced Optimus support.

---

### Post by gewone on 2012-01-15
[http://www.phoronix.com/scan.php?page=news_item&px=OTQxNg]("http://www.phoronix.com/scan.php?page=news_item&px=OTQxNg")

A reason to jump for joy?
Probably not, at least not until it's stable.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-15
> **gewone said:**
> A reason to jump for joy?
Probably not, at least not until it's stable.

And at least until it's able to power down the nVidia when not in use.

---

### Post by mcspanol on 2013-01-20
I found this on search and just wanted to post that Nvidia is planning support in Linux for the Optimus tech and I read somewhere that Ubuntu 12.10 was going to have some level of support for it but I have yet to see any drivers come across my software updater.  Anybody else?

---

### Post by Vargson on 2013-01-21
> **mcspanol said:**
> I found this on search and just wanted to post that Nvidia is planning support in Linux for the Optimus tech and I read somewhere that Ubuntu 12.10 was going to have some level of support for it but I have yet to see any drivers come across my software updater.  Anybody else?

Nvidia is planning optimus support? Where did you read that? Could you provide a link or something?
That would finally make me able to use ubuntu on my notebook. I really want to get rid of Windows, but I did buy  a notebook with strong graphics card for a reason and don't want to loose the power.

---

