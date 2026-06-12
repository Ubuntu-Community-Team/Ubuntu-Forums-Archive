---
title: "sudo: /etc/init.d/cups: command not found :: Why ?"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by cascader on 2007-05-07
Can anyone here tell me why I would be getting this command line output ?

I am attempting to install a HP C3180 PhotoSmart.

[COLOR=Blue]cascade@~
:->[/COLOR] **sudo /etc/init.d/cups restart [COLOR=DarkGreen](input)[/COLOR]**
Password:
**sudo: /etc/init.d/cups: command not found [COLOR=DarkGreen](output)[/COLOR]**
[COLOR=Blue]cascade@~
:-> [/COLOR]

Thanks to anyone listening out there . . .

---

### Post by mbeierl on 2007-05-07
What's the output of ```
ls -al /etc/init.d/cups
```?

---

### Post by cascader on 2007-05-07
Thanks for the reply **[COLOR=Red][mbeierl]("http://ubuntuforums.org/member.php?u=93334")[/COLOR]** . . . unfortunately I am at work and only have access to **[COLOR=Blue]MSXP[/COLOR]** **:-(** 
Different time frame I'm afraid, I see your post is 1 hour ago, which would've been like 07:00 my time . . . my best work is done at **[COLOR=Blue]night[/COLOR]** in front of a **[COLOR=Blue]Linux[/COLOR]** box . . .

So, won't be trying your suggestion for another **[COLOR=Blue]nine[/COLOR]** hours.
Again, **:-(**

---

### Post by Erlander on 2007-05-07
Well, I've just looked in the /etc/init.d folders on both my Ubuntu pc's that are running Feisty.

There is no cups file in either hence the error message.  There is a cupsys file but it won't respond to a restart command either.

Rob

---

### Post by cascader on 2007-05-08
Alright, thanks **[COLOR=Red]Erlander[/COLOR]**. I am still running **[COLOR=Red]Edgy[/COLOR]** on my main puter. Went to the directory '**[COLOR=Blue]/etc/init.d[/COLOR]**' and right, no cups . . . guess that's why the '**[COLOR=Blue]sudo: /etc/init.d/cup[/COLOR]**' couldn't find it, hey. **BTW, what is this directory ?** My guess is initialisation scripts . . .

How I solved my installation of my **[COLOR=Red]HP C3180 PhotoSmart[/COLOR]** was great . . . went to the [HPLIP]("http://hplip.sourceforge.net/supported_devices/inkjet_aio.html") site, downloaded what I guess is the latest installer :: **[COLOR=Red]hplip-1.7.4a[/COLOR]**., ran the command '**[COLOR=Blue]./hplip-1.7.4a.run[/COLOR]**' and away we went. Took a few minutes and required a little interaction from me, but otherwise, too easy.
[CENTER]**[COLOR=SeaGreen]++++++++++++++++++++++++++++++++++[/COLOR]**
[/CENTER]
So, I guess another reason I reply is to raise the awareness of any other HP punters out there . . . there is a simple easy way. Trust HP. By far the best general purpose printers on the market. I don't work for them, BTW . . .
[CENTER][B][COLOR=SeaGreen]++++++++++++++++++++++++++++++++++
[/COLOR][/B][LEFT]**What is this ****directory**** ? ****[COLOR=Blue]/etc/init.d[/COLOR]**[/LEFT]
  [/CENTER]

---

### Post by Erlander on 2007-05-08
I believe the folder is of scripts for starting and stopping daemeons and like you had expected there to be one for starting and stopping cups.

I have used it for starting and stopping samba, mysql, mythtv-backend and probably a few others at times.

As a relative newbie to Linux I'm still learning about these things and am not even sure what a daemeon is.

Rob

---

### Post by cascader on 2007-05-09
Cheers **[COLOR=Red][Erlander]("http://ubuntuforums.org/member.php?u=209027")[/COLOR]** . . . my very basic understanding is that these '**[COLOR=Blue]daemons[/COLOR]**' represent processes that ( possibly create a thread ) run in the background - thus the nifty analogy of '**[COLOR=Blue]demons[/COLOR]**' working in the back of scared ppls lives . . . jump on me if I'm wrong . . . I am keen to know more . . .

---

### Post by 13u11fr09 on 2007-05-09
Here's a bit more information for the curious:

/etc/init.d holds the scripts that *could* be run at startup...

when your computer starts up, it enters a "run level" of anywhere from 1 to 5 (default, I believe,  is 2).  Assume your computer enters run level 2 at bootup.  Then your computer will look in the directory /etc/rc2.d and run certain scripts from this directory.  An example rc2.d from 7.04 might contain:

```

someone@somewhere:/etc/rc2.d> ls -a
./                            S19cupsys@         S25bluetooth@
../                           S19hplip@          S89anacron@
README                        S20apmd@           S89atd@
S05vbesave@                   S20apport@         S89cron@
S10acpid@                     S20hotkey-setup@   S90binfmt-support@
S10powernowd.early@           S20makedev@        S98usplash@
S10sysklogd@                  S20nvidia-kernel@  S99acpi-support@
S10xserver-xorg-input-wacom@  S20powernowd@      S99rc.local@
S11klogd@                     S20rsync@          S99rmnologin@
S12dbus@                      S20samba@          S99stop-readahead@
S13gdm@                       S20ssh@
someone@somewhere:/etc/rc2.d>

```

if you look at the README file by running
```

cat /etc/rc2.d/README

```
you get 
```

The scripts in this directory are executed each time the system enters
this runlevel.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

To disable a service in this runlevel, rename its script in this directory
so that the new name begins with a 'K' and a two-digit number, where the
number is the difference between the two-digit number following the 'S'
in its current name, and 100.  To re-enable the service, rename the script
back to its original name beginning with 'S'.

For a more information see /etc/init.d/README.

```
As the README says, look in /etc/init.d/README for more information

Note: there are two "special" run levels of 0 and 6:

0 shuts the computer down
6 restarts the computer

to enter a run level of 6 (to restart the computer) you can, as root, type
```

init 6

```
or, using sudo
```

sudo init 6

```

Have fun ;)

---

