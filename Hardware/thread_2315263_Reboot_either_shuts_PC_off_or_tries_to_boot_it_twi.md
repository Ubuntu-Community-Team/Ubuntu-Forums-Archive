---
title: "Reboot either shuts PC off or tries to boot it twice"
date: 2016-02-27
forum: Hardware
---

### Post by alex511 on 2016-02-27
Hello, everyone! It's my first time on ubuntu forum (google was entirely helpful so far), so correct me please if I do something wrong.
**Problem**: when I select the 'restart' option from xubuntu log-out menu, my system does rebooting quite well until it reaches the black screen stage. Then it should boot up the PC again, show some logos, show some BIOS info, load grub etc. But instead my PC just shuts down and either keeps on being in off-state or tries to load again. In that last case it always fails to do so at first attempt, I mean, I can hear fans starting, HDD weeping and stuff like that, but after a couple of seconds everything just goes silent again. And only then PC tries to start itself the second time and it's always a success. So far it resulted in nothing more than a slight annoyance, but I'm afraid that this kind of "double startup" feature is not healthy for my computer.
**Observations**: I have a dual-boot installation of Xubuntu with Windows 7 on that machine. When I reboot from Win7 it works perfectly fine, there's not even that weird blackout stage when I can't hear a thing from my PC. Also I can never tell if it will stay shut down or make a double-run, the behavior seems random to me, though it usually a 50%/50% chance of getting either result. The most interesting part is that it wasn't always that way. The problems began when I installed nVidia drivers and removed noveau. An obvious solution would be deleting that nVidia driver but it didn't work! And I'd like to keep nVidia stuff since I program glsl shaders from time to time and default IntelVGA has no support for it.
**System specs**: dual-boot installation of Xubuntu (/etc/issue shows ver 14.04.4) with Windows 7, PC is.. actually it's a laptop ASUS x55vd with nVidia 610M as a graphic adapter.
**Actions taken: **googled it, only found the opposite problem when people can't make PC shut down completely which is not my case. Also tried reverting to default video drivers with no luck fixing problem so far (did so through Additional drivers in Software Updater).

Any help or information would be much appreciated. And... ahem, I still consider myself a novice in linux, just so you know what to expect from me :). Thank you in advance.

---

### Post by weatherman2 on 2016-02-27
Have you seen this thread?

[http://askubuntu.com/questions/523638/why-does-ubuntu-freeze-during-reboot-14-04-lts](http://askubuntu.com/questions/523638/why-does-ubuntu-freeze-during-reboot-14-04-lts)

I would try the suggestions there.  The basic idea is that you are changing a file that sets Grub's default options to pass along to the kernel when booting (those options are retained and used during shutdown/restart as well).  You're trying to tell the kernel to restart with various different options that might work better with your hardware.  There are a few options to try, so it might be a bit of trial and error.

The suggestion in that link is to use something called "Grub customizer"

[http://ubuntuhandbook.org/index.php/2014/04/install-grub-customizer-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2014/04/install-grub-customizer-ubuntu-1404/)

but you are really just using that as a safe and convenient way to edit this file on your Ubuntu system:

```
/etc/default/grub
```

and probably changing just a single line.  I do it with a text editor, but the "customizer" might be easier for a new user.

No matter how you change the file, you still need to run this afterward in a terminal after each change to the Grub options:

```
sudo update-grub
```

and then reboot.  You may in fact need to reboot twice to see if the change worked (because the change you just made may not take effect until you have restarted once).

---

### Post by alex511 on 2016-02-27
> **weatherman2 said:**
>  You may in fact need to reboot twice to see if the change worked (because the change you just made may not take effect until you have restarted once).
That was a vital information for me :). I suspected right that it may be an nVidia driver problem, and (shame on me) when I tried to change it back to Nouveau display driver before, I only did reboot once... Then I probably just switched it back to nVidia and powered PC down and never found out the truth.
I tried all options from ask-ubuntu topic you provided, unfortunately, none seem to be working (this time I double-checked that I did update-grub and restarted PC twice to see changes take effect).
The good news is that I managed to narrow it down to nVidia driver problem, since switching back to Nouveau solves it for me (also purged nvidia-* just to be sure). Second reboot worked like a charm.
The bad news is that I may actually require nVidia functionality at some point in future and the problem will arise again.
So, let's consider this half-solved for now, tomorrow I'll try to find some nVidia-specific topics, maybe I'm not alone in my misery. Thanks for the help, weatherman2! 
*(and please excuse my 'french', I'm not a native english speaker so I can only hope that my two first posts here do not appear as an example of linguistic nightmare).*

---

