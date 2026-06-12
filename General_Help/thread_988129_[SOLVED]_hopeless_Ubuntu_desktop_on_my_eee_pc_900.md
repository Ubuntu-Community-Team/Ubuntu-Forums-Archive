---
title: "[SOLVED] hopeless Ubuntu desktop on my eee pc 900"
date: 2008-11-20
forum: General Help
---

### Post by nigj on 2008-11-20
Since I m a quite new linux user I would hope that som of are able to help solve my trouble some desk top:(. I have attached a screen shot to illustrate what I would like to deactivate:confused:.

Hope that some of you are abel tohelp me.
I am running Ubuntu 8.10
:popcorn:

---

### Post by dznn on 2008-11-20
Hi,

Don't panic, it's not that hard :) It's a while ago I did this but if I remember it right this is how it's done:

Go to preferences - sessions and there uncheck UME Desktop.
You also might wanne uncheck Maximus if you prefer, then the app's you start wont automaximize.

Ps. I'v bad experience with that version of ubuntu... I now just run the normal distrubition, desktop version with a custom kernel ( adam's... ) Gives me better battery live and stuff...
Just telling you :)

Good luck.

( My English isn't great indead :p )

---

### Post by nigj on 2008-11-20
> **DeathZan said:**
> Hi,

Don't panic, it's not that hard :) It's a while ago I did this but if I remember it right this is how it's done:

Go to preferences - sessions and there uncheck UME Desktop.
You also might wanne uncheck Maximus if you prefer, then the app's you start wont automaximize.

Ps. I'v bad experience with that version of ubuntu... I now just run the normal distrubition, desktop version with a custom kernel ( adam's... ) Gives me better battery live and stuff...
Just telling you :)

Good luck.

( My English isn't great indead :p )
Thanks it was not to hard after all. What normal distrubition do you mean? I've tried several vesjoner of ubuntu, KDE and the latest version of Linux Mint on my Asus EEE PC 900 (16G). None of these works particularly well. Mint worked well, but I had never WLAN to work.
My experience with Linux is very thin. I've only run Linux in 2 months now so it's probably still a lot to learn.
:-)

---

### Post by Peter09 on 2008-11-20
In fact the administration settings within the netbook remix have an applet to switch between the standard and remix mode.

---

### Post by nigj on 2008-11-20
Well what does that actually mean :confused:where can I finde theese settings?
 :(

---

### Post by AlanR8 on 2008-11-20
I have the EeePC 700 (?) series with the 7.5 inch screen and 4 gigs of hard disk.

I've installed KUBUNTU 8.1 and it works a treat. I did have to spend about 5 minutes getting the wireless running but it's not hard.

---

### Post by snowpine on 2008-11-20
DeathZan was referring to the custom kernel from this site:

[http://array.org/ubuntu/](http://array.org/ubuntu/)

You can install this kernel into any version of Ubuntu Hardy or Intrepid (including Xubuntu, Kubuntu, and non-official distros like Crunchbang). The instructions on the array.org site are very clear to follow. If you can connect to the internet using wired ethernet, it's a breeze.

If you are using Ubuntu eee, you already have the array.org kernel.

I am running Crunchbang 8.10 with the array.org eeepc-lean kernel on my eee 900ha.

Good luck, let me know if you have any questions for a fellow eee user!

---

### Post by nigj on 2008-11-20
How did you solved the problem of wireless network? I did not find this at all when I tried Kubuntu 8.10 :confused:

Nils Gunnar
Norway

---

### Post by nigj on 2008-11-20
> **snowpine said:**
> DeathZan was referring to the custom kernel from this site:

[http://array.org/ubuntu/](http://array.org/ubuntu/)

You can install this kernel into any version of Ubuntu Hardy or Intrepid (including Xubuntu, Kubuntu, and non-official distros like Crunchbang). The instructions on the array.org site are very clear to follow. If you can connect to the internet using wired ethernet, it's a breeze.

If you are using Ubuntu eee, you already have the array.org kernel.

I am running Crunchbang 8.10 with the array.org eeepc-lean kernel on my eee 900ha.

Good luck, let me know if you have any questions for a fellow eee user!
Thanks, I found the kernel. I started with ubuntu for eeepc and has now upgraded to ubuntu 8.10 do I stil haave the array.org kernel?
:-)

---

### Post by snowpine on 2008-11-20
> **nigj said:**
> Thanks, I found the kernel. I started with ubuntu for eeepc and has now upgraded to ubuntu 8.10 do I stil haave the array.org kernel?
:-)

I do not know what happens if one upgrades Ubuntu eee from 8.04 to 8.10, never tried it. Does your wireless internet still work? If not, you probably need a new kernel. :)

---

### Post by dznn on 2008-11-20
I was indeed referring to the kernel mentioned here above... I messed around alot with my eeepc and ubuntu and found this to be the best solution for me:

1. Download the latest ubuntu release or the 8.04 ( but then you'll maybe need an extra step I don't remember *** )
2. Install it, change kernels an do all updates.
3. Instal the eee-control center ( again I havent got the link for it on this computer so sorry you'll have to google ), this makes all the hotkeys and cpuscaling stuff work.

And that's it, then all worked for me.

*** When you have hardy version of ubuntu you might wanne upgrade networkmanager to 0.7 instead of the 0.6.6 being used. It's a big difference here and maybe you wlan won't work with 0.6.6 but I doubt that since I think I read adam's kernel makes it work anyway.

( ps. You can use other program's to get your wlan to work, wicd or mad-wifi drivers and so on... I read about those but it just worked without them for me so why bother :) )

Good luck!

---

### Post by nigj on 2008-11-20
Hello again:) My wireless connection works fine. The only times it has failed was when I tried Kubuntu 8.10 and Linux Mint latest version. Why I dont know.
:popcorn:

---

### Post by AlanR8 on 2008-11-20
In KUBUNTU I do this to get the wireless to work:

> sudo kate /etc/modprobe.d/blacklist

and add to the bottom of the file:

blacklist ath_pci
blacklist ath_hal

Save the file.

in terminal:

sudo apt-get install linux-backports-modules-intrepid

reboot

gets everything up again


---

### Post by AlanRogers on 2008-11-20
There's two other ways of getting wireless working on the Eee 900:

[LIST=1]
[*]Go to [www.box.net/shared/zfvhhlao8w]("http://www.box.net/shared/zfvhhlao8w") and download the SuokoTweak.sh file. Set it to executable ```
sudo chmod a+x SuokoTweak.sh
```and set it running```

./SuokoTweak.sh
```It's an adaptation of the RiceeeyTweak.sh script that is designed for the 900 specifically and will make a number of necessary or useful changes, including configuring the wireless
[*]Install build-essential ```
sudo apt-get install build-essential
```Go to [http://downloads.sourceforge.net/madwifi](http://downloads.sourceforge.net/madwifi) and download the latest tarball - 0.9.4 at the time of writing - then extract, compile and install```
tar zxf madwifi*
cd madwifi*
make
sudo make install
sudo reboot now
```
[/LIST]I've just done this on my 900, having freshly install Hardy Heron. I had to do it all a second time though because the kernal updates from Ubuntu, undid that work. Still, it's all good practice!

---

### Post by nigj on 2008-11-21
This might be a hopless question but so what:) What exactly do I do to make the SuokoTweak.sh executable:confused: Do I have an application to do this or do I do this within the terminal:-?:-?

	
So far you have all contributed with the help of someone who is trying to learn to use Linux instead of Windows. Now I have a whole lot I have to try out for myself.
:guitar:

---

### Post by Peter09 on 2008-11-21
The command below (from Alan Rodgers previous post) should do it.

```
sudo chmod a+x SuokoTweak.sh
```

---

### Post by nigj on 2008-11-21
Thanks, I just tried sudo chmod a+x SuokoTweak.sh to get my downloaded file running (Iv saved it on my desktop) this is the result. chmod: cannot access `SuokoTweak.sh': No such file or directory
nils@nils-laptop:~$ 
what am I doing wrong:confused:

---

### Post by Peter09 on 2008-11-21
You are in the wrong directory.

Doing the command ```
ls
```will show you the files in the current  directory and any other directories in the directory you are in.

```
cd <directory name>
```will change to any directory in the current directory.

```
cd /home/<your user name>
```will start you at the top of your directory tree.

Do you know where the file is?

---

### Post by nigj on 2008-11-22
Iv finaly got my Ubuntu desktop the way I like it so thanks to all of you for helping me out:popcorn: 
But Im still not to happy with ubuntu. Have any of you seen or tried eeeMint:?: I tried Mint 6 but neither Ian or wlan would work.

---

### Post by AlanRogers on 2008-11-24
> **nigj said:**
> What exactly do I do to make the SuokoTweak.sh executable:confused: Do I have an application to do this or do I do this within the terminal:-?:-?I've just editted my original post to make it clearer. All of the necessary information was already there but obviously not quite clear enough. I too am a Linux newbie - you learn by asking.

---

### Post by nigj on 2008-11-25
I couldn't agree more.
To get the Ubuntu desktop on my eee pc 900  the way I really want it to be I had to install 8.10 and then fix the wifi problems. My wired connection worked right away.
:guitar:

---

