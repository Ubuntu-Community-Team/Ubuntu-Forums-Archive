---
title: "Gnome hangs after login"
date: 2005-11-27
forum: General Help
---

### Post by sonium on 2005-11-27
After loggin in to gnome i just get an empty brown screen, and nothing happens. If I try to change the session type it also hangs, means I can't click on OK.

I tried to reinstall ubuntu5.10 but same problem.

The only thing i can do is starting ubuntu in secure mode.

here are some logs that might be helpful:

[http://www.abi-mmv.de/stuff/kern.log](http://www.abi-mmv.de/stuff/kern.log)
[http://www.abi-mmv.de/stuff/kern0.log](http://www.abi-mmv.de/stuff/kern0.log)
[http://www.abi-mmv.de/stuff/sys.log](http://www.abi-mmv.de/stuff/sys.log)
[http://www.abi-mmv.de/stuff/sys0.log](http://www.abi-mmv.de/stuff/sys0.log)

---

### Post by Hoop on 2005-12-15
Sorry if I got your hopes up by replying but I have exactly the same problem. Here is what I've found.

If I install base system, then xorg and then gnome, System works fine but I'm missing lib files and some software packages. These can be added by synaptic but I'm not sure which ones I need.

If I install standard packages and lib files, even after I have had it running normally via previous method,  I get a kerenl panic at the login screen.

You have the same CRON message I have at the end of system log. So I removed CRON and now ANACRON exits normally but the system still hangs at login window.

It has to be a package on the standard distro thats loaded on gnome initialisation but I don't know which one. If I ever work it out then I'll post it here.

---

### Post by Lifesteeler on 2005-12-15
Ok, I have the exact same problem, except my computer works fine if i reboot...but then it hangs, i can't even move the mouse...and i get that brown screen...

Need help... I can use other wm's but not gnome:( ...

---

### Post by sonium on 2005-12-16
I got around the problem by first installing Ubuntu-Server and update then to Ubuntu-Desktop via Apt-get.

---

### Post by kuraca on 2005-12-16
I hat the same problem, in my case was a problem with my nVidia video card. Here is how I fixed

Reboot the computer and load linux in safe mode

did:
apt-get upgrade
apt-get dist-upgrade

to have all up to date

Finally load "aptitude", select "not instaled packages"->"X11"->"restricted"

There is an option for an nVidia video card, selected and installed.

Finally, I run the command the installer said, something like: "sudo nvidia-glx-config enable".

That's it

I hope it helps others, and sorry for my bad english

---

### Post by markajharrison on 2005-12-17
Hi kuraca,

I have the same problem and display card (nvida) I followed all your steps and completed the nvidia-glx-config enable successfully. gnome desktop still hangs at unpredictable times, usually about 10 min into session.

Is there anything else that I should check? 

This is killing me, I just installed my 1st version yesterday and feel like a kid in a lolly shop, with no money!!!

Cheers,

---

### Post by obriente on 2005-12-17
sooooo... the solution to this is......?????

I'm haveing the same trouble, on an old IBM think pad.
log in and i get an empty brown screen.
can move the mouse, but nothing seems to load.
I can't even try to search and download for new drivers cause Unbuntu wont recognize my linksys wireless card...
some one ???
anyone???
help????
I guess this is a good way for me to learn and be introduced to linux... by imediately being forced to wander through the terminal...

---

### Post by obriente on 2005-12-19
Well I found that the audio drivers were my problem, removed the audio group and boots fine.
Any one have any advice on getting my linksys card to work???
its a wpc55ag card.
It powers up, ubuntu seems to recognize it, has an entry to configure it under networking.
But can't get signal or connect.
I know there is a signal cause I'm connected on an XP machine sitting right next to my new llinux box.

and downloading drivers isn't an option because there is no builtin ethernet in my aging Thinkpad 600x

any one have any ideas?
This weekend when I installed linux is my 1st prolonged exposure to it (a friend uses it, but he also has an wierd ass keyboard that I can't type on so I avoid his PC like the plague), so any help would be nice.

---

### Post by markajharrison on 2005-12-19
Hey obriente, how did you find out it was your audio driver? :confused:

---

### Post by abstauber on 2005-12-20
Hi,
I also have the same problem. I've found out (it's also described [here]("http://ubuntuforums.org/showthread.php?t=102359&highlight=esd+gnome")), that killing esd in the console, gets gnome running. Removing my user from the audio group also works.

It's just gnome for me, xfce4 works fine. Does anyone have a clue why gnome is hanging?

---

### Post by obriente on 2005-12-21
[QUOTE=markajharrison]Hey obriente, how did you find out it was your audio driver? :confused:[/QUOTE]


lots of googling and forum crawling I found lots of reports about issues with the audio on the 600/600x on ubuntu.
removed from the group and it loads fine.

so I'm assuming that unless I'm missing something that was the problem.

the laptop makes a strange noise when the logon screen first apears, which is what prompted me to look into it.

---

### Post by jthirt on 2005-12-23
Excellent post mate! And very good english too ...

[QUOTE=kuraca]

Reboot the computer and load linux in safe mode

did:
apt-get upgrade
apt-get dist-upgrade

to have all up to date

Finally load "aptitude", select "not instaled packages"->"X11"->"restricted"

There is an option for an nVidia video card, selected and installed.

Finally, I run the command the installer said, something like: "sudo nvidia-glx-config enable".
[/QUOTE]

It did the job for me and I was quite frustrated with this. I tried both ubuntu and kubuntu live cds first with no sucess while I had used them on many othe Pcs and installed ubuntu on a couple without a glitch.

So I'm posting for the first time running ubuntu on our home PC :smile: 

Cheers, I need to check if my cassoulet is burning now :???: 

'till later ...

---

### Post by obriente on 2006-01-03
[http://ubuntuforums.org/showthread.php?t=104723&highlight=thinkpad+600x]("http://ubuntuforums.org/showthread.php?t=104723&highlight=thinkpad+600x")
need to add these when loading the kernel
acpi=force pci=noacpi

found the solution.
now my sound card and my pcmcia wifi cards work flawlessly
been playing around for a bit now to make sure there were no problems, everything seems fine.

---

### Post by abstauber on 2006-01-05
I also got my problem solved by not using the Gnome Sound Server and switching to Alsa. :smile:

---

