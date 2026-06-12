---
title: "custom ubuntu 8.04 install via netboot"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by skullomaniac on 2009-04-23
hey ppl
I found nothing that completely walks me through this process this is why i decided to make this post  

I want to make a clean install of ubuntu without the gnome de but only with lxde and openbox 

so I am thinking of doing as follows:

install ubuntu via netboot 
then do i select command-line install or advanced options > command-line expert install? my only concern is that i do NOT want to install any de so i can add it later 

but if i install ubuntu with expert install, do i have to "manually" add important packages like networking and graphics card (nvidia) etc. or are the same packages installed as they would be with a live cd install apart from the de?

if i have to manually add packages, which ones should i add that match my goals? 

i read on an official ubuntu guide that to install lxde i have to type

```
sudo apt-get install lxde xinit gdm xorg
```

but do i have to include gdm?? i know that xorg is essential for a de but i really have my doubts for including gdm... 

i also made this post because i don't want to install ubuntu server and then add a GUI because i don't want packages i don't need


help is appreciated! thanks!

---

### Post by DavidTangye on 2009-04-23
At the time that I wrote [installing-from-a-lan-server]("http://sites.google.com/site/golinuxnow/installing-from-a-lan-server") & section 1 of [ Installation LocalNet]("https://help.ubuntu.com/community/Installation/LocalNet") I had been installing using netboot from the [Minimal CD Image]("https://help.ubuntu.com/community/Installation/MinimalCD") edition as well as from the Desktop edition. The reason for using the Minimal CD edition was partly to get a minimal set of packages installed via netboot. I then rebooted into the character interface, as no GUI packages were installed, and installed the icewm and related packages for a gui. As I recall it worked for netbooting Edgy but I had trouble with Gutsy, so netbooted the Desktop installer as per  [installing-from-a-lan-server]("http://sites.google.com/site/golinuxnow/installing-from-a-lan-server") & section 1 of [ Installation LocalNet]("https://help.ubuntu.com/community/Installation/LocalNet") from then on. Notwithstanding that, if the expert mode install allows you to not install any gui stuff these days, then the advice in [Installation LocalNet]("https://help.ubuntu.com/community/Installation/LocalNet") should be good for you, as it gets you to an installer via netboot, and from that point on it does not matter that the installer is running from a CD or via netboot. So when you install no gui ...

[LIST=1]
[*]networking drivers etc are still installed
[*]X is not installed, and a driver for your display is installed so you still can see stuff when you boot into a character-based system.
[/LIST]
When you then apt-get a package for your window manager of choice, all dependent packages are added in automatically. This is the power of debian-based package management. So X and whatever else needed is all added in.

So in summary, netboot a minimal system, then apt-get your window manager.

If you do not install gdm, what will handle gui logins? Try leaving it out. IF you need it, boot 'Recovery mode' ie character mode as root, and apt-get install it later. The  'de' is a meta-package 'ubuntu-desktop'. Look at it in Synaptic and see what real pacakges it represents (its 'depends' packages). If you do not install the ubuntu-desktop package, ask yourself which of the packages it includes/'depends' on would still be useful to you, and apt-get install them. You cant do damage. Just install minimal and slowly build up til you have what you are happy with.

---

### Post by slakkie on 2009-04-23
You can use netboot to create a cli system (which has less packages installed compared to the server install) or you can create a server install.

Afterwards you can install any DE/WM you want. You could use xdm in stead of kdm or gdm. 

It is really simple, you could try it out on a virtual machine first if you want :)

---

### Post by skullomaniac on 2009-04-24
hey dudes! 
this is how i did it
i downloaded the alternate cd and installed only the command line system
then from there i put lxde and openbox and as login manager i put slim

unfortunately for some dependencies i'm guessing somehow gdm also got installed but its not the default login manager

do you think there is something wrong or any possible mistake with what i did or does it seem clean enough?

---

### Post by Rotaj on 2009-04-25
A quick and dirty way to do this is install [Linux4One Lite.]("http://www.linux4one.it/forum/index.php?topic=962.0")

It is optimized specifically for the Acer Aspire One.

---

### Post by DavidTangye on 2009-04-26
> **skullomaniac said:**
> hey dudes! 
this is how i did it
...
do you think there is something wrong or any possible mistake with what i did or does it seem clean enough?That sounds fine to me. I checked and found that I also had to use the "Alternative CD's" iso, and also used netboot to install the command line interface (cli) only, then used apt-get to install the gui stuff. I stayed with gdm, and find icewm works nicely for me on an old slow laptop, (as does Puppy linux). Howevber I am sure there are other WMs such as what you have chosen that will work well too. Its all good. :)

---

