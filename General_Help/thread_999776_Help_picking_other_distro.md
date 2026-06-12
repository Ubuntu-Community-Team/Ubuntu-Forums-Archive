---
title: "Help picking other distro"
date: 2008-12-02
forum: General Help
---

### Post by [=Vion=] on 2008-12-02
Okay so I installed Ubuntu Intrepid Ibex about 2 weeks ago because my friend literally begged me to. Plus Im sort of sick and tired of M$. I wanted a new experience in my Pc besides Windows so I got an Ubuntu CD put another HDD on my PC and installed Ubuntu in it. It turns out that I cant download programs online and install them with a normal executable. I dont mind using the terminal but the PC where I have linux doesnt have Internet access so I get screwed when it comes to updates and programs.

Is there a Linux that´s right for me.

Ive done some researched but there are too many distros put there.

Thanx in advanced.

---

### Post by mxrten on 2008-12-02
That's a little tricky. There are a lot of distributions, yes, but most rely upon a package manager to install programs.

How do you intend to install the programs? It is possible to download packages on one computer, transfer it on a cd or usb-stick to another computer, and then install it. Problem is that a package may depend on other packages, that depend on even more packages. So you must first find out this dependency, and then transfer all packages in this inefficient way. A package manager connected to the internet does this automatically.

There are alternative install methods, but they are usually not very beginner friendly.

Ubuntu, Debian, Gentoo, SuSE, Red Hat and Fedora are some of the most common distributions. I'm no expert on their difference though, and have no idea which could suit your needs best.

Whichever you choose, I would still recommend, if possible, to hook up your pc to the internet temporarily, just to install everything you need.

---

### Post by [=Vion=] on 2008-12-02
Okay, can you link me to a guide on doing that.
If in the end I do have to hook my PC to the web than I might as well stick with Ubuntu right? Or is Mandriva any better?

---

### Post by binbash on 2008-12-02
I strongly suggest ubuntu of course but you can try fedora 10.Maybe latest suse also.

---

### Post by snowpine on 2008-12-02
Hi there, typically with Linux distros like Ubuntu, we do not "download programs online and install them with a normal executable." That is the Windows way of doing things. :) If you want to learn the Linux way of doing things, do some research about repositories, apt-get, and the synaptic package manager. Or, use the Add/Remove Programs application built into Ubuntu if you prefer a graphical interface.

If you don't have internet access, I suggest choosing a Linux distro that's as close as possible to meeting your needs "out of the box." For example if you are into making music, there is Ubuntu Studio. I can't really give you a recommendation unless you tell us more about your needs...

Good luck!

---

### Post by SeanHodges on 2008-12-02
Check out [Apt on CD]("http://aptoncd.sourceforge.net/").

---

### Post by mxrten on 2008-12-02
To download a single deb-package manually, go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), browse through the right ubuntu-flavor, category and find your package. Note all dependencies and download them as well. You will not get a direct link, but a list of mirrors and the path to the packages.

Then use dpkg ([http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)) to install the packages.

However: NOT recommended. I would never install packages in this way if there was an alternative...

I also recommend Ubuntu (most people here will =)).

---

### Post by bodhi.zazen on 2008-12-02
There is a nice listing and review of distros on Distrowatch :

[http://distrowatch.com](http://distrowatch.com)

As has been mentioned, to install / update software they all depend on internet connectivity.

AptOnCD may be your best option, or just connect the pc to the internet when needed.

---

### Post by mixmaster on 2008-12-02
Most applications etc are available via the synaptic package manager (accessible from the system/administration option if you are using gnome).  If you can't see something you want you may need to enable the community maintained and third party repositories (from the settings/repositories option in the package manager).

In my experience, the things not available via this method generally come with detailed installation instructions - often just to add additional repositories.  Software which is not in a proper repository and does not come with specific installation instructions should be treated with caution.

Using synaptic (or aptitude, the command line equivalent) has a lot of advantages.  These programs will sort out the dependency issues for you and install/upgrade/uninstall stuff as required.  They will also allow the update manager to automatically keep individual packages up to date for you - none of the windows registry chaos or mad tuesday update crap.

Don't get hung up because things don't work the way they did with M$.  Generally once you get used to the linux methodology you will find that there are good reasons for doing it this way.  As for program installation, all the major distros use debs or something similar and have similar management tools.  The ubuntu stuff is as good as any and better than most, and certainly better than the mess you can get into with Windoze when multiple apps decide they want to replace the same system dll.

---

### Post by [=Vion=] on 2008-12-02
This is the Ubuntu forums so it would make sense for them to prefer Ubuntu lol :)

Oh and I did 3 days worth of research on Ubuntu and have over 50MB
of tutorials and guides on Ubuntu. I know all about the commands and the Package Manager.

I did read about thhe above utility before but I didnt really understand it much. I thought I already needed an ubuntu to make a copy of and then put that copy into an existing ubuntu but oh well I guess I will have to carry my Desktop PC all the way to my brother´s house and hook it up.

Im still doing some research but now that I have Ubuntu it would be too much of a hastle to switch to Mandriva or Debian now, even though I have read that Ubuntu originated from Debian?

But alright thanx guys Im staying with Ubuntu then.

---

### Post by Catalyst2Death on 2008-12-02
This may help you decide:
[http://www.zegeniestudios.net/ldc/index.php](http://www.zegeniestudios.net/ldc/index.php)

My first encounter with linux was SimplyMepis, which was fairly good.  Windows didn't play well with it, and I wasn't ready for the plunge, so I ran away.  For the record, it wasn't Mepis' fault that Windows didn't like it, it was mine for messing with the master boot record.

My second, and more permanent experience with Linux was Ubuntu.  It is great to learn on, and is one of the few distributions that will grow with you.  Ubuntu is extraordinarily powerful, its just that it has a reputation of being for "n00bs" which really isn't the case.  I've hopped around the major distros (Fedora, OpenSuse, Mint(based on Ubuntu), Mandriva, and Arch).  But I've always come back to ubuntu.  Ultimately I come back because:

1) Fully implemented tab completion.  Other distributions have command tab completion implemented, but not as intelligently as ubuntu. Its hard to explain, but its not normal for other distributions, (in my experience) to intelligently select which file type goes with a given command.  For instance:
```
$latex bla[TAB] 
```
would fill in blah.tex rather than any of the other blah.* files in the directory. This is also true for cd which makes moving around in the terminal a lot easier.

2) Apt-get/Repositories.  While other distributions may have features of their package managers which are better than apt-get, apt-get wins for two reasons, firstly the diversity of the repositories (which isn't a good reason, but it factors in). And secondly, apt-get supports tab completion, which is useful if you know roughly the name of which package you want to install.

3) Hardware Support.  While this isn't such a huge issue anymore, everything works in Ubuntu.  It takes some tinkering but with a swift kick, everything will work *optimally* in ubuntu.  In other distributions it may take a swift kick to get something to work, and an out right fight to get it to run *optimally*.

Some of this might not be important to you, but these are what keep me stuck to ubuntu (it certainly isn't their default color scheme/theme).  When I get time I want to try something like slax, Gentoo, or Linux From Scratch, but I'm too busy with other things right now...

---

### Post by TeXtonyx on 2008-12-02
sudo apt-get install filename.deb

will download and install the file, which is easier than .exe.
If you download filename.deb one can double click on it to 
install it, there may be a little add-on for this. 

If your computer has a nic card you can unplug your dsl cable
and plug it in there temporarily. I have mine hooked up prior
to installing a Linux OS and the install programs always find
the internet connection so you could install a bunch of programs
initially so you wouldn't have to plug and unplug the cable often.

[http://tldp.org/guides.html](http://tldp.org/guides.html) This is a free resource.

Introduction to Linux - A Hands on Guide [this is quite current]

version: 	1.27
author: 	Machtelt Garrels, <tille>
last update: 	Jun 2008
ISBN: 	1596821124
available formats: 	

   1. HTML (read online)
   2. HTML (read online, single file, 800k)
   3. HTML (tarred and gzipped package, 1.1M)
   4. PDF (1.6M)

Also if your Linux computer has a dvd player, you can download
the Ubuntu dvd and it has lots of programs on it. You can add
your Ubuntu drive after your Windows drive and dual boot, so
that you could share the internet connection.

Now if you are a bit of geek, Advanced Bash Scripting is even
better than Windows Powershell if you are into writing scripts.

Advanced Bash-Scripting Guide available in .pdf and .html formats.

version: 	5.5
author: 	Mendel Cooper, <thegrendel(at)theriver.com>
last update: 	Nov 2008

---

