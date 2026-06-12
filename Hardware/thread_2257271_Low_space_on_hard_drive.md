---
title: "Low space on hard drive"
date: 2014-12-18
forum: Hardware
---

### Post by michigogo on 2014-12-18
Hello,
I have a big problem. I was going to play Dota 2 on steam, when something unexpected happened:
As i was going to launch the game, steam told me an update had to be downloaded. So I said "okay" because I'm use to it. But... I had no space left to finish downloading the update! That when it started getting weird. I decided to do a clean up of my computer, after having closed steam. After getting some space by emptying the trash, some unimportant files... I opened up steam once again... And... Dota 2 had disappeared! When i clicked on the icon, it said "Install the game"! but I never uninstalled it! And it stills takes space on my computer!
So i have decided to come here once again to ask for help. Is there a way to completely uninstall steam and all other games on it? I already tried to do this:
sudo apt-get purge steamBut when i enter the command in the terminal this is what i get:
*[sudo] password for myname: *
*Sorry, try again.*
*[sudo] password for myname: *

Please help me!
Thanks!

---

### Post by mörgæs on 2014-12-18
Running out of space can make a real mess in a system.

You could try rebooting the computer and run ```
sudo apt-get clean
``` and ```
sudo apt-get autoremove
``` After that please post the output of ```
df -m
```

---

### Post by michigogo on 2014-12-18
Thanks for your reply!
This is the output of df -m:


Filesystem     1M-blocks  Used Available Use% Mounted on
/dev/sda5          37173    34600       684       99%        /
udev             1986  1 1986        1%         /dev
tmpfs             3991398   1%        /run
none                   5050%        /run/lock
none             1993 2719672%        /run/shm
$and this is what happened when i did "sude apt-get autoremove":

```
myusername@E6520:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gir1.2-ubuntuoneui-3.0 libdmapsharing-3.0-2 libgdiplus libllvm3.0
  liblog4j1.2-java libmikmod2 libsdl-mixer1.2 libsdl-net1.2
  libubuntuoneui-3.0-1 libunity6 linux-headers-3.2.0-32
  linux-headers-3.2.0-32-generic linux-headers-3.2.0-32-generic-pae
  openjdk-7-jre-lib prboom rhythmbox-data timidity timidity-daemon
0 upgraded, 0 newly installed, 18 to remove and 136 not upgraded.
After this operation, 107 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 393010 files and directories currently installed.)
Removing gir1.2-ubuntuoneui-3.0 ...
Removing libdmapsharing-3.0-2 ...
Removing libgdiplus ...
Removing libllvm3.0 ...
Removing liblog4j1.2-java ...
Removing prboom ...
Removing libsdl-mixer1.2 ...
Removing libmikmod2 ...
Removing libsdl-net1.2 ...
Removing libubuntuoneui-3.0-1 ...
Removing libunity6 ...
Removing linux-headers-3.2.0-32-generic-pae ...
Removing linux-headers-3.2.0-32-generic ...
Removing linux-headers-3.2.0-32 ...
Removing openjdk-7-jre-lib ...
Removing rhythmbox-data ...
Removing timidity-daemon ...
Removing timidity ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libglib2.0-0 ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
```

---

### Post by ajgreeny on 2014-12-18
Crikey! That's an awful lot of space already used by your root partition; almost 40GB nearly all gone.  Do you run a lot of games, which I assume will be sitting mainly in /usr, though not being a gamer I am not sure about that.

You really need to find what is using it all so you can make a more managed attempt to release more space, or you are not going to be able to safely use the OS.

I'm sure there is a way to do this in terminal with the du command but at the moment I can't find out how to do it for the whole filesystem, only for /home which is not going to help.  Running baobab, the **disk-usage-analyser** may show you enough about which of the root main directories are using all your space and you can then set about removal of the things that are not needed.

---

### Post by mörgæs on 2014-12-18
In addition to what has been posted above another thing to watch is 

> **michigogo said:**
> 
0 upgraded, 0 newly installed, 18 to remove and** 136 not upgraded.**


You are not up to date with regards to security updates.

If you have a lot of user files I recommend that you move them to another drive and update all packages as soon as possible.

---

### Post by michigogo on 2014-12-19
> [COLOR=#000000]Crikey! That's an awful lot of space already used by your root partition; almost 40GB nearly all gone. Do you run a lot of games, which I assume will be sitting mainly in /usr, though not being a gamer I am not sure about that.[/COLOR]

Well, I don't have a lot of games on my computer, however, I have also Windows  installed on my computer, (I never took it off, in case I needed it for something...) and it's using quite a lot of space.

> [COLOR=#000000]You are not up to date with regards to security updates.[/COLOR]

Yes, I have been harassed by Ubuntu telling me that, lately. I never like to update things, everything can go wrong, I don't like updates!

---

### Post by michigogo on 2014-12-19
Guys!
I'm very happy, using the:
> [COLOR=#000000] Running baobab, the [/COLOR]**disk-usage-**[COLOR=#000000]**analyzer**[/COLOR]
I was able to find the biggest file that took all my space, and that i didn't even need!
And it was: Steam, with 44,545 items, totalling 20.6 GB on it! Thank you very much for all your answers, and for your little commands tip which were also very useful to free up some space!
Thanks, Thanks, Thanks, i'm going to be able to play much more games!

---

### Post by mörgæs on 2014-12-19
Updates (within release number) are generally safe. Upgrades (to the next release) sometimes break a system in part or completely.

It's a bigger risk not to apply security bugfixes.

---

