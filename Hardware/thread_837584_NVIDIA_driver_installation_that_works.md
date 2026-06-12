---
title: "NVIDIA driver installation that works"
date: 2008-06-22
forum: Hardware
---

### Post by eXsolacyst on 2008-06-22
I've been trying for a while to get my nvidia 9600gt to work in Ubuntu 8.04.  I've read so many forums and guides and README's even from really good sources and they didn't help out that much.  I'm not big into editing x config files so I actually found a way to install the drivers and software with out having to do anything except answer the questions in the setup. This procedure is based on my system which dual boots Ubuntu and Windows.

IN UBUNTU

1. - Download your devices appropriate drivers from the nvidia site [http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")(it's easiest if you download it to your desktop).

2. - Right-click the file and enable the execute permission of the file in the permissions tab.

3. - It also helps to rename the file to something like [COLOR="Blue"]nvidia.run[/COLOR] that way you don't have to remember so much for the next steps.

4. - Restart your system and in the OS selection menu (if you dual boot) select your version of Ubuntu with the (recovery mode) option next to it.

5. - It should bring you to a list of choices, choose [COLOR="Blue"]root[/COLOR] and it will bring up the command line.

6. - (Assuming your file is on your Desktop) Logged in as root, the only thing you need to type in after you submit your credentials (user name and password) is (this must type with the single quotes included) [COLOR="Blue"]'/home/yourusername/Desktop/nvidia.run'[/COLOR]. This should run the setup file without any errors.

7. - Read and follow the instructions provided by the software and it should install the driver as well as the X Server Settings which will appear in your Applications Menu. Make sure you read the first prompt closely because the choices of 'yes' and 'no' might no be what you think it is.

8. - You'll know it installed right after it finishes and you reboot.  When it's done just type [COLOR="Blue"]reboot[/COLOR] and your system will restart.  When your system starts back up you should get an NVIDIA splash screen before it goes to your desktop.

Executing this file does not work if you try to stop your GUI in the command line or by pressing Ctrl+Alt+F2 when starting your system regularly (X Server still runs in the background) this is why the procedure insists that your restart your system and start with the root CLI in order to prevent error.

NOTE: The setup will search and delete any preexisting files that will conflict with it so you don't really have to worry about uninstalling any drivers or configuration files you might have tried previously, but I do suggest doing so just in case.

Hopefully this helps anyone who has been having problems getting their drivers installed for currently unsupported high-end NVIDIA cards.

-eXsolacyst

---

### Post by steveneddy on 2008-06-22
What's wrong with the driver in the repos?

Why does every one seem to think that the driver that will work for them is one that they have to download from nVidia.

There are two great drivers in the repos.

Using these drivers will ensure that you don't have to reinstall video drivers if there is a kernel update.

New folks to Ubuntu and Linux in general should use the nVidia driver in synaptic.

If you aren't uninstalling the previous video driver, you won't get good results.

Go to Synaptic Package Manager and uninstall the current video driver, unless you are using VESA.

Open Synaptic

System --> Administration --> Synaptic Package Manager

search for nvidia

install

nvidia-glx-new

and

nvidia-kernel-common

***************************

Scratch that, why don't you just 

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

to configure your driver correctly?

This will set up the file for you.

[Look here]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_ATI_and_nVidia_Graphics_drivers") for additional info about video driver installation for Hardy.

---

### Post by eXsolacyst on 2008-06-22
Nothing is wrong with those drivers, it's just the fact that they are generic for the most part.  Downloading the file you need for your model video card will ensure that you can utilize the device most effectively.  Not to say the synaptic drivers and utilities don't work, they just don't work as well (they don't allow you to use all the visual effects for the OS, and gamers can't run games with optimal performance).

---

### Post by veedub on 2008-06-22
I am using the proposed 173.14.05 driver from the repositories with no problems.  Even multiple displays using twinview is flawless.  Been through 3 kernel updates with no need to reconfigure the display driver; something that was inevitable with nvidia bin...

---

### Post by steveneddy on 2008-06-22
> **eXsolacyst said:**
> it's just the fact that they are generic for the most part. 

What? The nvidia-glx-new is the nvidia driver from nvidia.

It comes with the kernel modules from Ubuntu so you don't have to reinstall the video drivers when there is a kernel update.

I have used these nvidia drivers from day one on all of my machines and I don't get poor performance.

I learned that I don't want to make time to recompile a video driver when the kernel updates. I have to work on this machine daily. The driver is only 1 step behind the cutting edge of the one on the nvidia site at any one time, so I opt for stability instead of cutting edge. 

Machines that you can tell the difference on are not machines that you game on. They are very high end cad/cam or medical research machines, even architectural design PC's that require large amounts of power to accurately represent technical depictions on screen.

Regardless of what the masses think, there is not a game in existence that needs the graphical dexterity as most of the medical and cad/cam software suites in use today. 

The driver out of the repos are fine, but there is a link in my first post to tell you how to get the latest/greatest driver for nvidia.

You **must** uninstall any other video driver except VESA if you want to be successful in installing the new nvidia driver.

If you goof up, you can use the VESA driver to get things straight.

If you don't have much experience in installing drivers from source and have a hard time following detailed instructions, then installing the driver from the repos will give you acceptable performance until you gain a little more knowledge.

Uninstall whatever nvidia driver you have now and do the dpkg-reconfigure command I told you about earlier.

I remember that you need to go to a tty terminal to do that and stop the gdm.

[COLOR="Red"]**Print this info before you start.**[/COLOR]

ctrl+alt+F1

login with screen name and password.

```
sudo /etc/init.d/gdm stop
```

then

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

follow the instructions, using the defaults when necessary.

Choose the nvidia driver.

```
sudo /etc/init.d/gdm start
```

That should get you most of the way there.

---

### Post by sdennie on 2008-06-23
A couple of things:

1) You don't have to manually recompile the drivers on kernel updates: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

2) People manually install the nvidia drivers to either get support for the most recent hardware or simply to have more control over their system.  Considering the state of the nvidia driver for last year or so, it's not completely unreasonable for people to want to stay up to date and pray for updates that actually make driver performance acceptable.

3) "sudo dpkg-reconfigure -phigh xserver-xorg" doesn't do anything to the video driver on Hardy.  You will need to boot into recovery mode and choose "xfix".

4) I agree that if installing nvidia-glx-new causes you no problems at all, then yes, stick with that.  Unfortunately, this is often not the case as the nvidia drivers are closed source and not tightly coupled with xorg or kernel development.

---

### Post by cooltd825 on 2008-06-23
> **veedub said:**
> I am using the proposed 173.14.05 driver from the repositories with no problems.  Even multiple displays using twinview is flawless.  Been through 3 kernel updates with no need to reconfigure the display driver; something that was inevitable with nvidia bin...

this is nice and dandy until someone decides to buy a new GTX 200 series card.  then the standard repo driver just screws you over.  as far as i know (and i just checked the website :P)  the GTX 200 series cards use the 177.13 driver.

---

### Post by steveneddy on 2008-06-23
> **vor said:**
> A couple of things:

1) You don't have to manually recompile the drivers on kernel updates: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

2) People manually install the nvidia drivers to either get support for the most recent hardware or simply to have more control over their system.  Considering the state of the nvidia driver for last year or so, it's not completely unreasonable for people to want to stay up to date and pray for updates that actually make driver performance acceptable.

3) "sudo dpkg-reconfigure -phigh xserver-xorg" doesn't do anything to the video driver on Hardy.  You will need to boot into recovery mode and choose "xfix".

4) I agree that if installing nvidia-glx-new causes you no problems at all, then yes, stick with that.  Unfortunately, this is often not the case as the nvidia drivers are closed source and not tightly coupled with xorg or kernel development.

You know - you may be right there.

BTW - great job on the laptop nvidia power settings script.

Just did it and the results are great.

thanks.

---

### Post by xp_newbie on 2008-06-23
> **steveneddy said:**
> What's wrong with the driver in the repos?
The nVidia drivers in the repos are suspected to cause the horrible freezes/lockups in Ubuntu 8.04 in systems that are not 5 years old...

Read here:

[http://techxplorer.com/2008/04/23/fixing-random-freezes-in-ubuntu-804/](http://techxplorer.com/2008/04/23/fixing-random-freezes-in-ubuntu-804/)

The latest driver from nVidia is dated June 11, 2008. Is this the same version as in the repos?

---

### Post by sdennie on 2008-06-23
> **steveneddy said:**
> 
BTW - great job on the laptop nvidia power settings script.

Just did it and the results are great.

thanks.

Glad it worked.  The nvidia hardware is great but the drivers haven't been very good lately.  It's unfortunate that linux users are reduced to using what essentially amounts to hacks to get good performance but, at the very least, it's possible to get good performance without having to wait for nvidia to provide a solution.  :)

---

### Post by Sef on 2008-06-23
> The nVidia drivers in the repos are suspected to cause the horrible freezes/lockups in Ubuntu 8.04 in systems that are not 5 years old...

Not necessarily true.  I just built my computer a few months ago, and have an 8600 video card.  All works well.

---

### Post by nl2br on 2008-06-23
Hello Guys, I don't know if this is the correct place to do this but the fact is that I have an 8500GT and the "restricted" drivers doesn't work as well as my old 6200, I mean delays switching apps and that stuff.

Do I have glx running? Yes, I do.

I am running the drivers that comes with ubuntu 8.04, that "restricted drivers" by default.

Thank you.

P.D.: Here is my post in which I explain my situation. [http://ubuntuforums.org/showthread.php?t=837659](http://ubuntuforums.org/showthread.php?t=837659)

---

### Post by xp_newbie on 2008-06-23
> **Sef said:**
> Not necessarily true.  I just built my computer a few months ago, and have an 8600 video card.  All works well.
That's good to know because right now I am pulling my hair, trying to troubleshoot freezes on my newly build system, running Ubuntu 8.04. This lockups do not occur on Vista (same exact hardware, dual boot configuration), so I assume it is the software, not the hardware.

If you have any ideas how to troubleshoot this problem I would be grateful. The full details of my system's configuration and what I went through so far can be found here:

[http://tinyurl.com/458she](http://tinyurl.com/458she)

Thanks,
Alex

---

