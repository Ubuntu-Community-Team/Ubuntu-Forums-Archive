---
title: "Urgent- Help needed asap, computer useless"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by wilsonisme on 2006-02-02
Hey guys I just ditched windows 2k pro on my only main computer. I am typing this on an old one.

I installed Kubuntu once. Install was problem free, or so it looked. However once the kubuntu start screen was done my screen was all screwed up. So I got some advice on installing nvidia drivers as I have a 6600 GT. I did this, and now I could see my kubuntu log in screen.

However, when I logged in, I got flooded with errors, then kicked back into the log in screen! I figured I would try installing once more before posting and I did, and it is still doing the same thing.

The errors are:

"Will not save configuration:
Configuration file "/home/grant/.kde/share/config/konsolerc not writeable.
Configuration file "/home/grant/.kde/share/config/kdeglobals not writeable."

"Unable to save bookmarks in:
/home/grant/.kde.share/apps/konqueror/bookmarks.xml Reported error was: Permission is denied."

Finally:

"There was an error setting up inter-process communications for KDE. The message returned by the system was:
Could not read network connection list
/home/grant/.DCOPserver_grantcomp_0
Please check that "dcopserver" is running."

Anyone? I need help bad :( Please keep the reponses kind I am pretty new to linux

---

### Post by wilsonisme on 2006-02-02
Guys? Anyone? Little extra background: The hard drive is a SATA. Windows has always worked fine with it, but one weird thing is it kinda showed up as a removeable device. I mean I could always boot off it, everything worked fine, but the little "safely remove device" thing was always on my taskbar in windows, with the hard drive on the list.

---

### Post by towsonu2003 on 2006-02-03
You got too many permission errors, so let's try adjusting the permissions of your home directory (*grant is your username*): ```
sudo chown -R grant:grant /home/grant
sudo chmod -R u+w /home/grant
```
The first one will change ownership of everything under /home/grant to be grant's stuff.
The second one will change the ownership of everything under /home/grant to be writable by you.
None of them will give any output. 
Do these in a terminal and log in after these. 

**very important note:** while using sudo, check that you wrote everything correctly at least 3 times.

Note: I am not sure how to get to a command line from the log in screen. Try the session option?? Someone could help me here... You could also use the LiveCD, mount your filesystem, and adjust the above to:
```
sudo chown -R grant:grant path/to/mounted/home/grant
sudo chmod -R u+w path/to/mounted/home/grant
```
:confused:

---

### Post by wilsonisme on 2006-02-03
Thanks, ill try that tomarrow and give an update on what happened :-k

Oh one other thing though, why would a fresh install of kubuntu not give it's own home user permission to write to his own directory by default? That is just whack, makes no sense, and when I tried ubuntu/kubuntu before that was never the case (installed it on a different computer)

btw, you press CTRL ALT F2 at login screen to get to the shell

---

### Post by wilsonisme on 2006-02-03
Anyone know why ubuntu would not give you write privlages from the get go?

---

### Post by towsonu2003 on 2006-02-03
I experienced this with a couple of distros. if you had an existing home partition (without format, was there, usually from another distro), this tends to happen. each have their own pattern of home ownership. suse gives ownership to username:users, ubuntu gives it to username:username so you adjust them to your needs. if that was a brand new home pertition, than no clue.

---

### Post by wilsonisme on 2006-02-03
It was brand new, im pretty sure. Anyway, I just spent ten hours writing zero's over the hard disk. I'm going to burn a new kubuntu disk this evening at like 4x. One thing i'm confused on though is it doesn't seem that kubuntu has a disk check utility. So how would I go about making absolute sure that the disk im about to install with did not get corrupted during the dowload or burning?

I know there is a kd5 or something check thing but I have never used it- so any tips on how to go about doing that would be greatly appreciated.

Thanks guys for all the help

Oh one other thing, because I am using a nvidia 6600 GT, kubuntu does not have a default video driver to use. I was told how to use ctrl alt f2 etc to install the video drivers. I used:

> sudo apt-get install nvidia-glx
> 
sudo nvidia-glx-config enable
As these were already in the default allowed repo's.
Then I restarted.

 Is this all I need to do to get basic video drivers until I can put on the new ones? It seemed to work, although I could not log in with KDE- atleast I could now see the KDE login screen. But as described above im thinking that problem is completly unrelated to this video driver situation.

This guide: [Installing nvidia drivers]("http://ubuntuguide.org/#installnvidiadriver") has me do some extra steps so im not sure. it also sounds like the guide wants me to add new repos before I run the commands, which I cant do from the shell because Kate gives me some video error, which is what im trying to fix! =\

---

### Post by towsonu2003 on 2006-02-03
[QUOTE=wilsonisme]One thing i'm confused on though is it doesn't seem that kubuntu has a disk check utility. So how would I go about making absolute sure that the disk im about to install with did not get corrupted during the dowload or burning?[/quote]
for example you are downloading it from here: [http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/)
Scroll down and you'll see a file called md5sums, open it and save it as a txt somewhere (in Windows this is). Google to download md5sum.exe. after downloading the iso at the same place you downloaded md5sum.exe, open up the windows command line utility and navigate to wherever the iso and md5sum is located. from there ```
md5sum.exe isofilenamehere
```you can write the few first characters of the file and complete it with tab. hit enter and compare the output to the corresponding line for your corresponding line for your file. the two number sequences should match. If downloading in linux, no downloading of the exe file is necessary: md5sum filename

> it also sounds like the guide wants me to add new repos before I run the commands, which I cant do from the shell because Kate gives me some video error, which is what im trying to fix! =\
in the command line, you can use ```
sudo nano /path/to/filename
```to edit the file after saving a backup of it (copy the file w/ cp with a different name). nano will show you important commands at the bottom. it's an editor for command line.

---

### Post by wilsonisme on 2006-02-04
Most weird thing! ALL problems fixed. I will say exactly what I did in case someone else is having a similar problem :)

-Wrote zeros over hard drive
-Continued downloading Kubuntu's and burning until they both FINALLY passed the kd5 check thinga majig
-Bought a really nice 19' inch LCD monitor to replace this crappy HP CRT I was using

The weird thing? I didn't even have to install nVidia drivers this time! It must be the ownage new monitor or something :)

Anyway, I sure am happy now! This experiance did make me think of one thing though. If it is this difficult to even get a clean download/burn of a single disk...
A) Fedora Core 4 must be HELL
B) There are a lot of users having otherwise avoidable problems if they had done the md5 checks.
C) A lot more people would be having a more enjoyable experiance with linux if there was some way to verifiy the download on the spot.
D) Buying a disk set of popular distros for like 15 bucks is more then worth it!

Anyway, thanks for the help guys, see ya around the boards 

\\:D/

---

