---
title: "Problem updating to 8.04"
date: 2008-07-16
forum: General Help
---

### Post by RolandFlagg on 2008-07-16
OK, so I was updating to the 8.04 version of ubuntu, but every time the updater gets to the lines

Setting up locales (2.7.9-4) ...
Generating locales...
  en_AU.UTF-8... 

the whole thing becomes stuck. Wonder if anyone could give me some solutions to this.

Thanks!

OK, since it froze for a while, i decided to terminate the process and "reupdate" the whole thing. however, when i try that, it says "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.", which I do
and what do you know... same thing happens, gets stuck at 

Setting up locales (2.7.9-4) ...
Generating locales...
  en_AU.UTF-8... 

then I check the system info, apparently I'm already in 8.04, but I never restarted my computer, nor does it look any different

---

### Post by RolandFlagg on 2008-07-16
bump

---

### Post by Elfy on 2008-07-16
Don't bump so quickly.

Open aterminal and run

```
sudo dpkg --configure -a
```

---

### Post by RolandFlagg on 2008-07-16
> **forestpixie said:**
> 

Open aterminal and run

```
sudo dpkg --configure -a
```



I did do that, but it still gets stuck at the same place

---

### Post by RolandFlagg on 2008-07-16
I (foolishly) decided to see what would happen if i restarted the computer, well now there's nothing on the desktop, just a wallpaper. Now I'm posting this in windows... seems like i have bigger problems now, how do i get back into a workable ubuntu gui, or is it now hopeless and I'd have to reinstall ubuntu?

---

### Post by RolandFlagg on 2008-07-16
uh... help? someone? anyone?

---

### Post by wobbiebobbie on 2008-07-16
I just do a fresh install and start over when upgrading ( Backup everything and do a fresh install) I run into that kind of problem  when upgrading

---

### Post by ReelExterminator on 2008-07-16
I've got the same problem on one of my computers. If you press alt-f2, you can still get to a console even if the graphical desktop isn't working. So far, running 'sudo dpkg --configure -a' results in it getting stuck at the same place (de_AT.UTF-8 is the first one, and the one it gets stuck at, for me).

---

### Post by RolandFlagg on 2008-07-17
and im guessing that you dont know the solution either?
hm.. maybe i will just reinstall ubuntu but get the 8.04 live cd and install it directly
any other help is greatly appreciated

---

### Post by chandra53 on 2008-07-17
Same problem here! <inserts disclaimer about lack of experience>
I was in the middle of upgrading from 6.10 -> 7.04 -> 7.10 -> 8.04 (following along this post: [_http://ubuntuforums.org/showthread.php?t=848852_]("http://ubuntuforums.org/showthread.php?t=848852")), but now I'm stuck.

I eventually rebooted the machine and tried to "sudo dpkg --configure -a" only to end up back where I started. While in that state I opened up another ssh connection to see what was going on. top reported that the 'localedef' process took over the CPU. huh...
[INDENT]  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5622 root      25   0 54972  52m  820 R 99.0 21.1   1:30.73 localedef[/INDENT]


Despite running top as root I couldn't kill the process (?!), so I did a reboot. After this second reboot I ran "sudo apt-get update" again, just to see if anything changed. apt-get replied with the following:
[INDENT]Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
[...]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Reading package lists... Done[/INDENT]


Noting the lack of complaints about dpkg being interrupted, I ran "sudo apt-get upgrade", and got back into the same loop again. :(
[INDENT]Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
197 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up libx11-data (2:1.1.3-1ubuntu2) ...
Setting up libx11-6 (2:1.1.3-1ubuntu2) ...

Setting up libxpm4 (1:3.5.7-1) ...

Setting up locales (2.7.9-4) ...
Generating locales...
  en_US.UTF-8...[/INDENT]


When I run "lsb_release -a" I get back:
[INDENT]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy[/INDENT]


I'd really prefer not to have to reinstall, but don't know how to fix things...

---

### Post by mostlydead on 2008-07-17
Sorry, I don't have a solution either. Just want to add that I've got the same issue, but...

Interestingly the upgrade worked on this machine once. I bought a Dell laptop (E1505) that came with feisty. I ran with that until upgrading to gutsy. And ran with that until upgrading to hardy a couple nights ago. All worked fine.

I decided that I wanted a fresh install (lost track of which packages I've installed ages ago etc. etc.) so I wiped it and reinstalled feisty again from dell's iso (the last install was actually from this same disk as well - I had reinstalled it once).

So, it seems just running through the upgrade path straight away is what's causing this? Maybe I had installed something else that prevented this? Or maybe this package (not sure which one it is) was updated recently and it broke?

I doubt this will get much attention, so I'll just run gutsy for awhile again I suppose.

-edit-

Just want to add that I tried to reinstall twice as well as running the recommended dpkg command several times. Nada.

---

### Post by n8gray on 2008-07-17
Just a "hardy" me too.  I am attempting to upgrade Feisty -> Gutsy -> Hardy but things are stuck at "Generating locales" in the Gutsy -> Hardy step.  :confused:

This sucks.

---

### Post by ishields on 2008-07-17
Same problem here. FWIW, I'm using the 64-bit version on an AMD-64 processor.

---

### Post by Elfy on 2008-07-17
There appaear to be a few of the same error at the moment - it's a bug I think, there are some methods of getting around the problem detailed in some of these

[http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=Setting+up+locales+%282.7.9-4%29&sa.x=51&sa.y=15](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=Setting+up+locales+%282.7.9-4%29&sa.x=51&sa.y=15)

But if you are at all unsure it'd be best not to do what has been done or you could perhaps end up with bigger problems.

---

### Post by RolandFlagg on 2008-07-17
well maybe there IS a bug, but there's something else, idk if it has anything to do with this. Since my computer already had 3 partitions, when i installed ubuntu i neglected (actually was unable) to make a swap partition... maybe that screwed the system up? Just wondering if everyone else with the same problem has a swap partition.
O yea, and chandra53, i think our problems are exactly the same, "localedef" was taking over my CPU as well.

---

### Post by Elfy on 2008-07-17
Not sure about the swap thing tbh - if you have enough ram it propbably wouldn't use it much nayway. I assume you could only make 1 partition and made a primary instead of extended and logicals.

did you try any of the fixes?

---

### Post by dorath on 2008-07-17
Same problem, stuck at```
Setting up locales (2.7.9-4)...
Generating locales...
  en_AU.UTF-8
```Upgrading from 7.10, 32-bit

---

### Post by RolandFlagg on 2008-07-17
yea i tried, but i dunno how to start the process again once i stop it, like i dunno what the id of the process is
remember how i hav to do it all in command cuz i cant even start up the gui properly, so i hav to do one thing at a time
to do the "sudo killall locale-gen", i have to stop the entire installation, but after i killed the locale, i have no way of starting the installation again
also, "sudo apt-get dist upgrade" doesnt seem to work for me, i dunno why, but it says "dist" is not an available command or something

---

### Post by JG6_oddball on 2008-07-18
> **RolandFlagg said:**
> yea i tried, but i dunno how to start the process again once i stop it, like i dunno what the id of the process is
remember how i hav to do it all in command cuz i cant even start up the gui properly, so i hav to do one thing at a time
to do the "sudo killall locale-gen", i have to stop the entire installation, but after i killed the locale, i have no way of starting the installation again
also, "sudo apt-get dist upgrade" doesnt seem to work for me, i dunno why, but it says "dist" is not an available command or something

its  "sudo apt-get upgrade" no "dist" is needed

I am having the same problem with the local hangin gthe whole install

S!

---

### Post by RolandFlagg on 2008-07-18
ok "sudo apt-get upgrade" doesn't work because as soon as i try to run that it asks me to run "sudo dpkg --configure -a", which again gets stuck at the same old place

---

### Post by avtolle on 2008-07-18
[http://ubuntuforums.org/showthread.php?t=861194](http://ubuntuforums.org/showthread.php?t=861194) is a very long thread concerning the same problem; there seems to be a workaround in the latter pages of the thread. Don't know if any of you has seen this, so am posting the link.

---

### Post by ishields on 2008-07-18
I was able to get around the problem by getting to a terminal window (ctrl-alt-fn) and then running
sudo dpkg -r -a
before rerunning
sudo dpkg --configure -a
The first command sompletes without output, then the second one picks up and continues the upgrade from the failing en_AU locale.

---

### Post by RolandFlagg on 2008-07-18
Ok guys! thanks to everyone, i actually got mine to work. To overcome the problem of not able to kill the process when dpkg is running, I logged into ubuntu using the "failsafe graphics" or something, it's in options. So then i have the access to the gui. From there i opened up a terminal and ran dpkg as before, but when it gets stuck, i was able to open up a separate terminal to kill the process, then the upgrade continued. However, the locale enAU came up a couple times again, but i just killed it each time it came up. At the end it says something about errors so things werent installed, but i just exited it and ran update again. This time it went to enAU and actually worked XD

---

### Post by alecz20 on 2008-07-18
I ran in the exact same hang situation when attempting to add another Language on Language Support on Ubuntu 7.10.

I can't kill the process except by restarting the system.

The problem is that I cannot install anything now because the dpkg was interrupted.

> **ishields said:**
> I was able to get around the problem by getting to a terminal window (ctrl-alt-fn) and then running
sudo dpkg -r -a
before rerunning
sudo dpkg --configure -a
The first command sompletes without output, then the second one picks up and continues the upgrade from the failing en_AU locale.

not only I couldn't find out what the first command does, this didn't help me at all.

As of right now I cannot install anything new on my system. 
All I did to break it was trying to add a new language!:cry:

---

### Post by n00bWillingToLearn on 2008-07-19
If you would like to help get this problem solved the Ubuntu devs are asking for information, specifically the log files from
 /var/log/dist-upgrade/

Here is a link to the bug report:

[https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340/](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340/)

And there are probably going to be other requests in the future as well so come back to it periodically if you can.

---

### Post by punkybouy on 2008-07-19
Not that it helps but I had the exact same problem this morning.  I like fresh installs as much as I hate them too.

---

### Post by hedonplay on 2008-07-19
I've got the same problem.
30 minutes has gone. Nothing changes.
Help!!!

---

### Post by JG6_oddball on 2008-07-19
well guys I was able to do a "work around" on mine which is as follows

#1 reboot system and chose "failsafe" as boot option
#2 open a konsole window via command line (right click on desk top) or in main menu under "system" "konsole"
#3 type "sudo dpkg --configure -a" and then in the upper left hand corner of "Konsole" choose "session" and click "new Shell" and type in "sudo killall locale-gen" and you will have to switch back and fourth between the windows and redo "killall locale-gen: a few times as the en_AU.UTF-8 comes up a few more times.

S!

---

### Post by chandra53 on 2008-07-19
After reading through various approaches, I finally tried [_this one_]("https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340/comments/9") posted by Rocco in one of [_the launchpad bug reports_]("https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340/"), since I was also running the -server kernel. It worked, and I'm now on the new 2.6.24-19-server kernel! I got past the dreaded step:[INDENT]Setting up locales (2.7.9-4) ...
Generating locales...
en_US.UTF-8...
[/INDENT]

Just in case, I ran "sudo apt-get update" and got a clean result:
[INDENT]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
[...]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [908B]
Fetched 424kB in 4s (85.4kB/s)
Reading package lists... Done[/INDENT]

"sudo apt-get upgrade" also came back clean:
[INDENT]Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/INDENT]

"sudo dpkg --configure -a" didn't have anything to complain about either.... so far so good.

Thanks Rocco!

---

### Post by alecz20 on 2008-07-19
can you please run:

/usr/bin/localdef

in terminal and tell me what is the output?
It should read the localdef file and tell you the system language

You might see the file is not found, so you do not have a language. If you go to Language support in Administration you will see there is no default default language.

This "workaround" helps with the up-gradation, but it cripples the system completely.

---

### Post by IwasAnex on 2008-07-19
Assuming some of us trusting if somewhat head strong newbs have gone and foolishly deleted the localedef, is there an easy way to get it reinstalled/setup again?

Just curious

---

### Post by alecz20 on 2008-07-19
I think the proper way to re-install localdef back would be via the Synaptic Package manager by reinstalling "locales" and "belocs-locales-bin"

However the system will hang again when generating the locales.
This leaves only one option -> complete system re-install until the bug is fixed.

---

### Post by IwasAnex on 2008-07-19
Ok just to add the things that have happened, here is how I got around the bug. After the second freeze I booted the Gutsy recovery kernel and dropped to a root prompt (third option down). Then I
```
rm /usr/bin/localedef
dpkg --configure -a
```

That went on fine for a bit but kicked out to the command prompt due to a bunch of errors mostly surrounding the lack of a localedef. So not knowing what else to do I rebooted. The hardy kernel came up with the login screen, but I logged into a blank orange screen. Hitting ctl-alt-f1 I loggged into the command prompt. Tried to run a 'sudo apt-get update' but was told by apt-get to run a 'dpkg --configure -a' instead. So I did. It installed a bunch of locales and the rest of the upgrade.

Rebooting yet again, the Hardy kernel booted without a hitch. Logging in however yielded Xubuntu and not Gnome. I logged out and accessed the options on the Login screen, there I selected the Gnome interface and my preferred language. 

Incidentally, the /usr/bin/localedef is gone but the /usr/bin/locale command is there. 
Running it yielded the languages that I have installed and my preferred language. Did someone change the name between Gutsy and Hardy? 

Anyway the box is up and running as smooth as a linux box should. Thanks everyone for the myriad of help even if I wasn't the first one to have this problem.
Cheers

---

### Post by alecz20 on 2008-07-20
My /usr/bin/locale yields:

```

LANG=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=

```

Which is not really what I expected. The /usr/bin/localdef used to give the language I chose on the install.
Going to the Language Support I still have no language.
I tried 'sudo apt-get update' but nothing really happened. I suppose this is one of the thing that will only be fixed for 8.04 and up. Maybe I should upgrade, but I don't want the system to freeze crash every 5-10 minutes (that's what i read on the forums anyway)

---

### Post by chandra53 on 2008-07-20
Things seem to be ok in my world - here are my results:

```
~$ /usr/bin/localdef
-bash: /usr/bin/localdef: No such file or directory

```

```
~$ /usr/bin/locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```

---

### Post by alecz20 on 2008-07-20
chandra53,

Did you have the problem with the hang as well?
If so, what were the steps you used to solve it?

Thanks.

---

### Post by chandra53 on 2008-07-20
Yeah, I was stuck in the same place:
```
Setting up locales (2.7.9-4) ...
Generating locales...
en_US.UTF-8...
```

I got past it like this, based on [_this post_]("https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340/comments/9") by Rocco [_this launchpad bug report_]("https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340"):

> Bug #249340:
Gutsy->Hardy upgrade hangs in localedef
 Rocco wrote on 2008-07-18: (permalink)

My findings so far when upgrading a couple of servers.

*When localedef takes 100% cpu it's not possible to kill it.
*killall locale-gen makes the upgrade continue for awhile but get stuck when one package tries to do a ps, which will also hang.
*Poweroff and then start with Gutsy kernel doesn't work since localedef takes 100% again when configuring locales.

The only solution I can find on -server kernel is to:
* mv /var/lib/locales/supported.d/local ~/
* do-release-upgrade
* start with new Hardy kernel
* mv ~/local /var/lib/locales/supported.d/
* dpkg-reconfigure locales
* reboot

Again, Thanks Rocco!

---

### Post by alecz20 on 2008-07-20
Well, thanks... I guess if I had encountered the problem while upgrading, those steps would work, but I haven't tried to upgrade yet.

Maybe I'll give it a try... but my system works fine right now, so why bother?

---

### Post by stebrepar on 2008-07-20
I ran into the same problem upgrading from Gutsy to Hardy tonight, and I seem to have gotten through it with the following variant of what others have described above:

1. Open a terminal window and do "sudo killall locale-gen". This lets the upgrade process continue. I had to repeat this about three times, whenever the locale generation got hung again at "en_AU.UTF-8".

Killing the process worked fine for me. In the System Monitor window, the "localedef" process was taking about 75% of the CPU, rather than the 99% reported by others, although the total CPU usage was indeed 100%.

There were configuration error pop-ups for several packages during the upgrade. For me these were: language_pack_en_base, language_pack_en, language_pack_gnome_en_base, language_pack_gnome_en, ubuntu_minimal, sun_java5_jre, sun_java5_bin, sun_java6_jre, sun_java6_bin, sun_java6_plugin, and I think locales, iirc.

2. After the upgrade process finishes, reboot.

3. When the login screen appears, switch to a terminal via ctrl-alt-F1. I don't know that this is strictly necessary here, but I wanted to do a couple things before logging into the GUI.

4. Run "sudo apt-get update" (and "sudo apt-get upgrade" for good measure), just to be sure everything was up to date before going further.

5. Run "sudo locale-gen --purge en_US.UTF8" (or whichever locale is appropriate for you). This was probably not actually necessary, as I found in the next step.

6. Run "sudo dpkg --configure -a". This configured all the locales (and indicated that en_US.UTF8 was already done in the list, from my probably unnecessary previous step), and it appeared to configure all the packages that had configuration problems in step 1; I didn't catch seeing the whole list, but what I did see looked like the right stuff.

7. Finally, exit the terminal, and switch back to the GUI login screen via ctrl-alt-F9. Log in, and all appears to be well (so far anyhow). Note that I did not need to delete anything, or move anything, or chmod anything.

As for the cause of the problem, my suspicion is on the kernel update I took within the past couple days on Gutsy. Others reported that this problem had appeared at about the same time, and that going back to the previous kernel avoided the problem, as well as going forward to the new Hardy kernel did (which I had in place after my reboot in step 2 above).

Sadly, Hardy is not working with my Nvidia FX 5200 card and somewhat old 19" IBM monitor any better than Gutsy did, so I'm still stuck with my built-in Intel graphics and no 3D. It used to work with one of the earlier releases though (maybe Edgy? I forget now), which is quite annoying. But that's a problem for another day...
-- 
Stephen in NC

---

### Post by m4st3r*nix on 2008-07-23
okay this fix seems to work for me if anyone is still having problems upgrading to ubuntu 8.04 Hardy... if your stuck or hanging at Gnerating Locales... en_AU.UTF-8... reboot your computer and hit escape as soon as the grub menu comes up and choose to reboot in recovery mode which is the second choice in the list that appears... you will be prompted with 4 choices 1. resume normal boot 2. fix broken packages 3. drop to root shell prompt or 4. try to fix X server... the second choice is what you want, this will repair any broken packages you have during the upgrade...

---

### Post by m4st3r*nix on 2008-07-23
with your nvidia fx card did you try going to [www.nvidia.com](www.nvidia.com) and looking for drivers there? there is an updated driver that you could possibly use with your system... however if you check synaptic you could also install the nvidia-glx packages corresponding to your card... i have an nvidia 8600 gt which i used the updated driver from nvidia for it works fine.

---

### Post by m4st3r*nix on 2008-07-23
stebrepar the post on page 5 is for you or right above this one.

---

### Post by nroussi on 2008-08-04
I did all that and up to step 3 everything was fixed. It recreated all locales. Thanks.

> **stebrepar said:**
> I ran into the same problem upgrading from Gutsy to Hardy tonight, and I seem to have gotten through it with the following variant of what others have described above:

1. Open a terminal window and do "sudo killall locale-gen". This lets the upgrade process continue. I had to repeat this about three times, whenever the locale generation got hung again at "en_AU.UTF-8".

Killing the process worked fine for me. In the System Monitor window, the "localedef" process was taking about 75% of the CPU, rather than the 99% reported by others, although the total CPU usage was indeed 100%.

There were configuration error pop-ups for several packages during the upgrade. For me these were: language_pack_en_base, language_pack_en, language_pack_gnome_en_base, language_pack_gnome_en, ubuntu_minimal, sun_java5_jre, sun_java5_bin, sun_java6_jre, sun_java6_bin, sun_java6_plugin, and I think locales, iirc.

2. After the upgrade process finishes, reboot.

3. When the login screen appears, switch to a terminal via ctrl-alt-F1. I don't know that this is strictly necessary here, but I wanted to do a couple things before logging into the GUI.

4. Run "sudo apt-get update" (and "sudo apt-get upgrade" for good measure), just to be sure everything was up to date before going further.

5. Run "sudo locale-gen --purge en_US.UTF8" (or whichever locale is appropriate for you). This was probably not actually necessary, as I found in the next step.

6. Run "sudo dpkg --configure -a". This configured all the locales (and indicated that en_US.UTF8 was already done in the list, from my probably unnecessary previous step), and it appeared to configure all the packages that had configuration problems in step 1; I didn't catch seeing the whole list, but what I did see looked like the right stuff.

7. Finally, exit the terminal, and switch back to the GUI login screen via ctrl-alt-F9. Log in, and all appears to be well (so far anyhow). Note that I did not need to delete anything, or move anything, or chmod anything.

As for the cause of the problem, my suspicion is on the kernel update I took within the past couple days on Gutsy. Others reported that this problem had appeared at about the same time, and that going back to the previous kernel avoided the problem, as well as going forward to the new Hardy kernel did (which I had in place after my reboot in step 2 above).

Sadly, Hardy is not working with my Nvidia FX 5200 card and somewhat old 19" IBM monitor any better than Gutsy did, so I'm still stuck with my built-in Intel graphics and no 3D. It used to work with one of the earlier releases though (maybe Edgy? I forget now), which is quite annoying. But that's a problem for another day...
-- 
Stephen in NC

---

### Post by alecz20 on 2008-08-04
> **alecz20 said:**
> My /usr/bin/locale yields:

```

LANG=C
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=

```

Which is not really what I expected. The /usr/bin/localdef used to give the language I chose on the install.
...


I really need to fix this problem because it messed up the entire system.
My sorting is all messed up, i.e. case-sensitive, so I have "alpha" folder after "Delta" folder.

**How do i get en_CA in locale?**

---

### Post by alecz20 on 2008-08-04
Ok, I solved this! Here's what I had to do:

reboot in 2.6.22-14 not 2.6.22-15

Go to synaptic and re-install belocs-locales-bin

This re-generated all the locales. Now I have the system language, and Sorting is case-insensitive!

---

