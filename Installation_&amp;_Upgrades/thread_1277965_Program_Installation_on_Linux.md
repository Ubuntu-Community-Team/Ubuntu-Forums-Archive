---
title: "Program Installation on Linux"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by martin122089 on 2009-09-28
OK, so I have a very noobish problem. I recently purchased a HP Mini 1000 netbook with the Linux based operating system on it (called the Mii OS by HP). Being new to Linux, I have no idea what I am doing when it comes to anything besides surfing the internet. I want to download and install a program on this netbook, but I don't know where to start. I am able to download the file and have it in the download folder of the browser. Where do I go from here?

---

### Post by hub_cap on 2009-09-28
What version of Linux is installed? Click on System, About

You may want to check out this article.

[http://the-gadgeteer.com/2009/03/17/hp-mini-1000-netbook-running-linux/](http://the-gadgeteer.com/2009/03/17/hp-mini-1000-netbook-running-linux/)

---

### Post by brian mcgee on 2009-09-28
> **hub_cap said:**
> What version of Linux is installed? Click on System, About

Guessing it's this:
[http://en.wikipedia.org/wiki/Mobile_Internet_Experience](http://en.wikipedia.org/wiki/Mobile_Internet_Experience)

martin122089, what program are you trying to install?

---

### Post by martin122089 on 2009-09-29
I was trying to install an emulator for the Gameboy Advance. The emulator is called VisualBoyAdvance.

---

### Post by snowpine on 2009-09-29
Hi Martin, are you using Ubuntu? (If you aren't I can't really help you. :))

Generally, we install applications from the "repository" of tested and trusted software. You can do this using Add/Remove Applications, Synaptic Package Manager, or the command line (apt-get or aptitude).

Downloading random software from the internet is kind of a "Windows way" of doing things. Stick with the repositories as a beginner and you can't really go wrong. I am sure there are several emulators in there. Good luck!

---

### Post by brian mcgee on 2009-09-29
Actually, while I've never used it, VisualBoyAdvance appears to be in the repository. Martin, I'm not familiar with the interface on those HP Minis, but assuming it's Ubuntu, look for something called Terminal, and in it, type the following command and hit enter:

```
sudo apt-get install visualboyadvance
```It should prompt you for your password, and proceed to install the program.  Like snowpine suggested, you might look for "Add/Remove Programs" or "Synaptic Package Manager" for graphical ways to install software from the repositories. Once you get the hang of it, you'll love it. :)

If it's not working, but you find the Terminal, do this command and tell us what it says.

```
cat /etc/issue
```

---

### Post by martin122089 on 2009-09-30
Brian Mcgee, I tried the first command in Terminal (called Root Terminal on my system, I don't know if this is important or not) and it said 
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package visualboyadvance is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package visualboyadvance has no installation candidate"

Taking this to mean that it didn't work I did the second command you gave me and it said
"Ubuntu 8.04.2 \n \l".

---

### Post by martin122089 on 2009-09-30
Oh, and also hub_cap, my version of Linux is Kernel Linux 2.6.24-22-Ipia. Not sure why Ubuntu and Linux are mentioned on my system haha.

---

### Post by martin122089 on 2009-09-30
Never mind that last statement, I figured out that Ubuntu and Linux are related.

---

### Post by aysiu on 2009-09-30
Read this. It'll help:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

The menus aren't exactly the same, but I bought an HP Mini with Mi preinstalled on it (promptly replaced it with regular Ubuntu, which runs so much faster), and I'm pretty sure it comes with Synaptic Package Manager.

---

### Post by aysiu on 2009-09-30
Read this. It'll help:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

The menus aren't exactly the same, but I bought an HP Mini with Mi preinstalled on it (promptly replaced it with regular Ubuntu, which runs so much faster), and I'm pretty sure it comes with Synaptic Package Manager.

---

### Post by brian mcgee on 2009-10-01
martin, that's definitely the right terminal, but be careful, the root user can do anything on the system, so use the root terminal with caution! :)

I'll bet the right repo isn't enabled. In the same terminal, give us the results from the following command:

```
cat /etc/apt/sources.list
```

---

### Post by martin122089 on 2009-10-01
OK, so I was able to find the Synaptic Package Manager and Visual Boy Advance was in there but now a new problem has occurred. I marked the package for installation, downloaded the needed packages in order to install vbaexpress, and said apply and then apply again in the dialog box that popped up and then this error pops up:

"vbaexpress:
 Depends: visualboyadvance  but it is not installable".

Am I doing something wrong or is my fiddling with the MIE OS doomed?

---

### Post by martin122089 on 2009-10-01
brian mcgee, in response to your post I typed the command you gave me in terminal and this is what it gave me back:

"deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse restricted

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-updates main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-updates main universe multiverse restricted

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-security main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-security main universe multiverse restricted

deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-hpmini main universe multiverse restricted
deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-hpmini main universe multiverse restricted"

---

### Post by brian mcgee on 2009-10-02
That's exactly what I was looking for. :) So far we haven't made any changes to your system, so don't worry. However, it could be that the HP Mini repo has some trouble. Try doing this in the terminal:

```
sudo apt-get update && sudo apt-get check && sudo apt-get install vbaexpress
```Post the output too.

---

### Post by martin122089 on 2009-10-02
OK brian I did what you said and here is what the Terminal spit out. Its a bit wordy so I apologize ahead of time.

"Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy Release.gpg
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/main Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/main Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security Release.gpg
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/main Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/restricted Translation-en_US
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini Release.gpg
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/main Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/universe Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/multiverse Translation-en_US
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/restricted Translation-en_US
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini Release.gpg
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/public Translation-en_US
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy Release
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates Release
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security Release
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini Release
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini Release
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/main Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/universe Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/multiverse Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/restricted Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/main Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/universe Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/multiverse Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy/restricted Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/main Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/restricted Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/main Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/main Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/universe Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/restricted Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/main Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/universe Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/main Packages
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/universe Packages
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/multiverse Packages
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/restricted Packages
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/main Sources
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/universe Sources
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/multiverse Sources
Ign [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/restricted Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/public Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/public Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/main Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/universe Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/multiverse Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/restricted Packages
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/main Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/universe Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/multiverse Sources
Hit [http://hpmini.archive.canonical.com](http://hpmini.archive.canonical.com) hardy-hpmini/restricted Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vbaexpress: Depends: visualboyadvance but it is not installable
E: Broken packages"

---

### Post by brian mcgee on 2009-10-05
Hmm, no fun. If it were my machine, I'd install the latest Ubuntu on it, but for a less drastic approach, I'll bet you could just install the Hardy packages for vbaexpress and visualboyadvance. First though, could you post the output of the following command:

```
uname -a
```

---

### Post by mikewhatever on 2009-10-05
The package visualboyadvance is in the Ubuntu repositories for Hardy Heron, i368 and amd64 only, the problem is that you are using lpia architecture as well as non-standard repositories.

---

### Post by brian mcgee on 2009-10-06
> **mikewhatever said:**
> The package visualboyadvance is in the Ubuntu repositories for Hardy Heron, i368 and amd64 only, the problem is that you are using lpia architecture as well as non-standard repositories.

Which doesn't necessarily mean it's hopeless. Assuming he doesn't plan on removing the packages, couldn't he grab the i386 .deb files and install with:

```
dpkg -i --force-architecture whatever.deb
```More info: [http://ubuntuforums.org/showthread.php?t=982260](http://ubuntuforums.org/showthread.php?t=982260)

---

### Post by hantechbl on 2009-10-06
try 'sudo apt-get update' that should get the newest catalog of programs.

---

### Post by brian mcgee on 2009-10-07
> **hantechbl said:**
> try 'sudo apt-get update' that should get the newest catalog of programs.

Yep, he tried it. See post #15 :)

---

### Post by martin122089 on 2009-10-08
brian_mcgee, here is the output for the line you gave me:
"Linux martin122089-umpc 2.6.24-22-lpia #1 SMP Thu Apr 2 02:03:56 UTC 2009 i686 GNU/Linux"

---

### Post by brian mcgee on 2009-10-08
Martin, do you ever intend on uninstalling VisualBoyAdvance? There's a way we should be able to do this somewhat simply, but you won't be able to remove it with Synaptic Package Manager. (however, it should still be able to be removed from the command line)

Also, mikewhatever is right, the source of the trouble is that HP shipped that netbook with unusual repos and architecture, which might make it difficult to install other stuff down the road. Normal Ubuntu installs are rarely this painful.

---

### Post by martin122089 on 2009-10-08
Haha well, the biggest thing I would like to learn is how to install things in general. I've installed several other things from synaptic but after they're installed I can't seem to find them to use them. I can live without the emulator, but I would like to be able to install other things onto the computer.

---

### Post by Phil Newman on 2009-10-09
Thanks for that "aysiu" :) The first link was very informative and the second was good to know as well :) All Power To You My Friend :D

---

### Post by brian mcgee on 2009-10-10
> **martin122089 said:**
> Haha well, the biggest thing I would like to learn is how to install things in general. I've installed several other things from synaptic but after they're installed I can't seem to find them to use them. I can live without the emulator, but I would like to be able to install other things onto the computer.

Often, when something is installed in Ubuntu through Synaptic or APT, a menu item for the new software will be automatically created. For example, after installing FileZilla, I can go to Applications -> Internet and see FileZilla available. Given that you're using HP's version of Ubuntu, it's hard to say exactly what to expect since I don't have an HP netbook. :P

However, if you're comfortable installing it, I think things would be easier for you with the normal release of Ubuntu, or perhaps Ubuntu Netbook Remix. Though, I have no experience with the latter.

---

### Post by martin122089 on 2009-10-11
Yes I was thinking about doing that, but I'll fiddle around with it some more before I commit to anything. Thanks to all of you for the help, you have helped further my knowledge of Ubuntu greatly!

---

