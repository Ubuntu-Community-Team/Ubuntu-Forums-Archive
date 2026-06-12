---
title: "nvidia 64bit driver, x-server, blanck screen"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by Ajn on 2007-09-21
Hello!

I have decided to, at least turn to semi-linux user (I´m not going to leave windows....yet)
and once I tested Kubuntu and it looked nice. So I searched information about it and then
downloaded it.

The version is Kubuntu 7.04 feisty fawn 64-bit

the hardware used is in the sig

the dvd-image was easy to burn, use and install and I had no problems using that (note: although
I´m a linux-noob, I know how to handle windows so the basics are in control).

But I run into problems right away; those gpu-drivers for nvidia are nasty.

what have I done so far:

Installed/checked
[I]the make and gcc are installed
the linux-headers package matching the installed Linux kernel is installedthe pkg-config and xserver-xorg-dev packages are installed
[/I]
removed/checked
[I]the nvidia-glx package has been uninstalled with the --purge option
the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist
the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled
the /lib/linux-restricted-modules/.nvidia_new_installed does not exist[/I]

then I tried to install the driver

*sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run*

And it said that I need to stop the x server, so I typed:

**ctrl alt F1**
*sudo /etc/init.d/kdm stop*

and I get blank screen, monitor goes to power-save state and there is nothing else I could do,
exept** ctrl alt del** and then it boots.

Another frustrating  thing is, that when I select my Kubuntu from the GRUB, the screen turns blanck and
monitore goes to power-save state and about 10s after the Kubuntu-login screen comes in.

And one more thing, I´m a gamer. If I dont get css, ut and so on running on Kubuntu (with/without wine/cedega)
then it´s almost useless to me.

I need help on this, please give me advice!
Thanks,
Ajn

---

### Post by DaftDahl on 2007-09-22
Hello Ajn,

   I'm afraid I won't be any help here being extremely new to the Linux scene myself. However, I am in the same boat as you. Accept my question is how does one turn off the x-server? I have the latest Nvidia drivers downloaded and I know the commands to use to run them, just unsure as to how I turn off the x-server. I thought the key press command was ctrl+alt+backspace, but that just takes me to the login screen. Any help would be greatly appreciated.

Good luck to you Ajn,

DaftDahl

Also I'm using Kubuntu Feisty 64-bit just like Ajn.

---

### Post by PmDematagoda on 2007-09-22
So why don't you guys do the easiest thing(In my opinion), install the N-vidia driver under Recovery Mode, but be sure that you got the driver directly from the nvidia website and not from any other, so as to reduce the chances of the file being a virus.

---

### Post by DaftDahl on 2007-09-22
That worked perfectly. It asked me to install libc.dev before it would continue, but after doing that it worked like a charm. Thank you very much!

---

### Post by Ajn on 2007-09-22
Ok, thanks for the posts and help.

You mean, I start Kubntu in recovery mode and the just type to konsole

*sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run*

or what?


And the commands to stop the x-server (which didnt work correctly in my case, ended up with that black screen) are:

*sudo /etc/init.d/kdm stop*

or

*sudo invoke-rc.d kdm stop*

but today I´ll try that recovery mode install. I just need help with that (what do I need to do then, when I am in recovery mode?)

and another thing, what I have been suggested to try in another Kubuntu forum, is to use ENVY
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
I may try that too.

So, please help with that recovery install thing, and I´ll try it and then envy-installer. I think this problem will be solved very soon :)

---

### Post by PmDematagoda on 2007-09-22
> **Ajn said:**
> Ok, thanks for the posts and help.

You mean, I start Kubntu in recovery mode and the just type to konsole

*sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run*

or what?


And the commands to stop the x-server (which didnt work correctly in my case, ended up with that black screen) are:

*sudo /etc/init.d/kdm stop*

or

*sudo invoke-rc.d kdm stop*

but today I´ll try that recovery mode install. I just need help with that (what do I need to do then, when I am in recovery mode?)

and another thing, what I have been suggested to try in another Kubuntu forum, is to use ENVY
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
I may try that too.

So, please help with that recovery install thing, and I´ll try it and then envy-installer. I think this problem will be solved very soon :)

The thing about recovery mode is it never starts X until you say so(From what I've seen) since Kubuntu has the same base as Ubuntu you shouldn't have any differences between recovery mode in Ubuntu and recovery mode in Kubuntu, so you can install the nvidia driver normally as given in the Nvidia website.:)

Just select recovery mode in Grub, after that Ubuntu will start loading, except in this case there is no progress bar but you can see all the processes going on.

After loading is done, you will be brought to the "terminal" with "root@user-desktop:-~$"

I trust you know what to do from there?

---

### Post by Max Luebbe on 2007-09-22
The run level recovery mode runs in could give the NVidia installer some hangups as well.
Instead, try booting the computer normally. When it gets to the part where it black screens, hit ctrl-alt-f3 to switch to a terminal

from there, log in, bring down X and install the driver.

---

### Post by Ajn on 2007-09-22
okey, the problem solved. I used envy (you can download it @ [Alberto Milone`s homapage]("http://albertomilone.com/nvidia_scripts1.html") ) and from it, I used the text-based install, which was VERY simple, all I had to do was: press 1, K+enter, K+enter and then it restarted and thats it.

highly recommended for those who dont know so much about linux OR for those who want to get it done easy.

_Thanks_ to all who helped (I`m sorry I did it via the "noobiest" way but, I`m sure some day I will need the advice you gave me)

ps. this is posted @ linux ^^

---

