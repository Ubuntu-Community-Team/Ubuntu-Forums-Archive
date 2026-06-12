---
title: "install apps to computer without internet"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by shane2peru on 2009-04-14
Ok, I have read several posts on how to do this, and they don't address what I need to do.  I have a laptop running Ubuntu intrepid 64bit with wireless.  I have just installed Ubuntu intrepid 64bit to my desktop which doesn't have internet.  Now, I need to install applications to the desktop.  I can access the internet with my laptop.  I have tried this on the laptop:
```

cat packagelist | xargs sudo apt-get -qq --print-uris --reinstall install | awk -F\' '{print $2}' > get.lst

```
and it produced a nice get.lst file of which I downloaded it with:
```

wget -c -i get.lst

```
which in turn gives me a nice file of debs.  However installing these debs on the desktop has proven to be very difficult, in fact I have had to re-install twice now on the desktop because I have royally botched my system.  Since I don't have any apps installed, re-installing is not a big deal.

here is how I botched the desktop the first time:

```

sudo dpkg -i *.deb

```
that was exciting and produced so many errors it wasn't funny.

Next I tried one by one installing by double clicking, gdebi would then tell me the dependency and I would install it, eventually botched the system because I managed to try and install gcc+4.3 which is a newer version.  I forgot to update before trying to install things.  
I also tried dumping all the debs into /var/cache/apt/archives  and it doesn't install them, because the sources says it doesn't exist!  I have tried to point the repo to a local file with:
```

deb file:/location/of/directory intrepid main restricted universe multiverse 
``` and it says the Packages.gz cannot be found, however I did make the file and it does exit I made it with:\
```

dpkg-scanpackages . /dev/null > Packages && gzip Packages

```
in the directory with the files.  Why does this have to be so difficult?  I don't want to download all the repos (over 20Gb) so that I can install a few hundred MB's of apps.  Any help would be greatly appreciated.  Ohh, and when I try to download the apps on my laptop, it doesn't get all the deps because I use --reinstall with apt-get, but it doesn't re-install all the dependencies.  Arggh. ](*,) This is getting on my nerves.  Any help would greatly be appreciated.

Shane

---

### Post by shane2peru on 2009-04-14
ok I got the desktop (no internet) to recognize and accept my local repository.  However, how do I get the laptop to download all the dependencies?

Shane

---

### Post by shane2peru on 2009-04-14
I must say that is is rather a frustrating thing for Linux in general.  There is not easy way to install applications on a computer that is not connected to the web, you end up in a dependency nightmare.  

Shane

---

### Post by shane2peru on 2009-04-15
Ok, after all the searching, reading, and googling a small tutorial is in order from what I have learned.  First, I had a malformed source.list line for a local repository.  However I did learn very effectively to track down dependencies and download them.  So I will jot my lessons down here for my own future use and for anyone that can use them.

NOTICE:  Only use the same version of Ubuntu as your are installing on, unless you really know what you are doing.  Hardy with Hardy, Intrepid with Intrepid, 32bit with 32bit, 64bit with 64bit, ok you get the idea.

For Online Ubuntu machine

1.  lets make a directory to put our deb files, I called mine, offline.  I made mine in my home directory.  Use ```
mkdir ~/offline
``` or open nautilus and create a direcotry that way.

2.  Copy all our current cache to this directory, this helps with dependencies in the future, but is not necessary.
```
sudo cp -v /var/cache/apt/archives/*.deb ~/offline/
```

3.  Now we need to get an app or two for the next few steps.
```
sudo apt-get install dpkg-dev apt-rdepends 
```
Ok now the tricky part, chasing down those dependencies that for whatever reason disappeared from your apt-cache or you want to install an application on offline machine.

4.  Here is a tricky line, I'm using k3b as an example, and perhaps this is overkill, but it works.
```

cd ~/offline
 apt-rdepends -f depends k3b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
k3b
  Depends: cdparanoia (>= 3a9.8)
  Depends: cdrdao (>= 1.1.7-5)
  Depends: cdrskin
  Depends: genisoimage
  Depends: k3b-data (= 1.0.5-1ubuntu6)
  Depends: kdelibs-data (>= 4:3.1.4-2)
  Depends: kdelibs4c2a (>= 4:3.5.9)
  Depends: libacl1 (>= 2.2.11-1)
  Depends: libart-2.0-2 (>= 2.3.18)
  Depends: libattr1 (>= 2.4.41-1)
  Depends: libaudio2
  Depends: libc6 (>= 2.4)
  Depends: libdbus-1-3 (>= 1.0.2)
  Depends: libdbus-qt-1-1c2 (>= 0.62.git.20060814)
  Depends: libexpat1 (>= 1.95.8)
  Depends: libfontconfig1 (>= 2.4.0)
  Depends: libfreetype6 (>= 2.3.5)
  Depends: libgcc1 (>= 1:4.1.1)
  Depends: libhal1 (>= 0.5.8.1)
  Depends: libice6 (>= 1:1.0.0)
  Depends: libidn11 (>= 0.5.18)
  Depends: libjpeg62
  Depends: libk3b3
  Depends: libmusicbrainz4c2a (>= 2.1.5)
  Depends: libpng12-0 (>= 1.2.13-4)
  Depends: libqt3-mt (>= 3:3.3.8-b)
  Depends: libsm6
  Depends: libstdc++6 (>= 4.1.1)
  Depends: libx11-6
  Depends: libxcursor1 (>> 1.1.2)
  Depends: libxext6
  Depends: libxft2 (>> 2.1.1)
  Depends: libxi6 (>= 2:1.1.3-1ubuntu1)
  Depends: libxinerama1
  Depends: libxrandr2
  Depends: libxrender1
  Depends: libxt6
  Depends: wodim
  Depends: zlib1g (>= 1:1.1.4)

```
That is the output of the command.  I take that whole thing and past it into a text editor and save it as my k3bgetlist or whatever you want to name it.  Afterwards do a search with ctrl-h for   Depends:  and replace it with nothing that will delete that.  Now sorry for this, I'm not that good with regexs so I just manually deleted the stuff in (parenthesis).  Save this file (k3bgetlist) in the offline folder for later use and close

5.  Now we can download:
```

cd ~/offline
cat k3bgetlist | xargs aptitude download
```
This will download all those packages.

6.  Build your package list:
```

cd ~/offline
dpkg-scanpackages . /dev/null > Packages && gzip Packages

```

Now copy this folder to your favorite USB stick or CD or some form of moving it to the OFFLINE machine.

Steps for Offline Machine:

1.  Edit sources.list
```

sudo cp /etc/apt/sources.lst /etc/apt/sources.lst.bak
sudo gedit /etc/apt/sources.lst

```
Now you can comment out all the lines that access the internet if you would like, or leave them if you intend to connect in the future.  Comment out a line by placing a # symbol in front of the line.  Now add our local repo in this file at the end 

```

deb file:/home/[COLOR="Red"]username[/COLOR]/offline ./ 
```
replace username with a valid username of the offline machine.
Save and close that document.

2.  Now copy your offline folder to the home directory of the username used above.

```

mkdir ~/offline
cp -v /path/to/offlinefolder/* ~/offline/

```

3.  Now we can update and install, or upgrade (if there are updates that are not updated, it is because you are missing dependencies, that need to be tracked down with the above method.)
```
sudo apt-get update
``` you may see errors if you didn't comment out the other ones in the sources.lst this is not a problem.
```
sudo apt-get install k3b
```
It will ask you to proceed without verifications provided, you got all these from the legit repos, you should be fine.

This is what I did, and it seemed to work for me.  If you have questions feel free to post and I will try to help as I can.  

Shane

---

### Post by Partyboi2 on 2009-04-15
Congrats on finding a solution :) 
A few other useful methods to install packages on machines without internet are the '[[COLOR=Blue]Generate Package  Download Script[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")' in Synaptic and the other one is [[COLOR=Blue]Keyrx[/COLOR]]("http://keryx.betaserver.org/").

---

### Post by shane2peru on 2009-04-16
> **Partyboi2 said:**
> Congrats on finding a solution :) 
A few other useful methods to install packages on machines without internet are the '[[COLOR=Blue]Generate Package  Download Script[/COLOR]]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")' in Synaptic and the other one is [[COLOR=Blue]Keyrx[/COLOR]]("http://keryx.betaserver.org/").

Well for the Generate Package Download it didn't pull in all the dependencies when I used it, because they were already installed on the machine that generated the script they were not included.  Perhaps there may be a setting somewhere that I overlooked, but that was my experience with it.  

As for Keryx, looks very interesting, and certainly covers the update part, but I'm not sure that it covers installing an application with all dependencies.  Plus it isn't in the repos, which just adds additional steps to setup.  I will check it out though.  Thanks for the link.

Shane

PS
Ok, after downloading Keryx and reading the tutorial, the show stopper for me is```
sudo dpkg -i *.deb
```  This is exactly what botched my system twice.  There absolutely needs to be a dependency checker, and dpkg doesn't do that.  That is the reason I stick with the apt-get stuff, apt,aptitude both handle dependencies, and (under normal circumstances) don't break your system.  sudo dpkg -i *.deb in a folder full of debs is not smart in my opinion.  

PSS
Keryx doesn't find the dependencies for the applications, no go.

---

### Post by EXCiD3 on 2009-04-17
Keryx DOES find the dependencies, but a few of them have odd dependency naming which has not been finished yet. It's not in the repositories because it's a brand new project and works in a manner that providing a package for it is not really logical until it is more complete. Keryx is still very much a work in progress and will take care of package installation with a method exactly like post #4 whenever I get some free time to work on it. Thanks for at least checking it out. :)

---

### Post by shane2peru on 2009-04-17
> **EXCiD3 said:**
> Keryx DOES find the dependencies, but a few of them have odd dependency naming which has not been finished yet. It's not in the repositories because it's a brand new project and works in a manner that providing a package for it is not really logical until it is more complete. Keryx is still very much a work in progress and will take care of package installation with a method exactly like post #4 whenever I get some free time to work on it. Thanks for at least checking it out. :)

It is a very sharp looking application.  It ran very well.  I didn't realize it did find dependencies, I looked up k3b and started to download it, but it didn't seem as though it was going to download any dependencies.  If it can work like post four that would be great, because honestly there should be a nice gui app for this kind of thing.  I have always had internet, but lately I had been waiting for over a month to get it hooked up, and was growing impatient so I found a way, but it was through a lot of searching and digging.  Go for it on the GUI level!!!

Shane

---

### Post by EXCiD3 on 2009-04-18
> **shane2peru said:**
> It is a very sharp looking application.  It ran very well.  I didn't realize it did find dependencies, I looked up k3b and started to download it, but it didn't seem as though it was going to download any dependencies.  If it can work like post four that would be great, because honestly there should be a nice gui app for this kind of thing.  I have always had internet, but lately I had been waiting for over a month to get it hooked up, and was growing impatient so I found a way, but it was through a lot of searching and digging.  Go for it on the GUI level!!!

Shane

Thanks! You probably already have all of the dependencies for k3b installed already so it would not need to download them since it checks your dpkg status file. I felt the same way that there is no way to do this graphically especially when you have no way to update your package lists on your offline computer. Having dialup at home I quickly realized the complications for not having internet. Just trying to help out, I'll let you know when we get version 1.0 released over the summer. :D

---

### Post by shane2peru on 2009-04-18
> **EXCiD3 said:**
> Thanks! You probably already have all of the dependencies for k3b installed already so it would not need to download them since it checks your dpkg status file. I felt the same way that there is no way to do this graphically especially when you have no way to update your package lists on your offline computer. Having dialup at home I quickly realized the complications for not having internet. Just trying to help out, I'll let you know when we get version 1.0 released over the summer. :D

Yes, that was the biggest problem.  I have a laptop with Ubuntu intrepid installed for quite a while and all the apps I needed.  I then installed it on my desktop without internet, and had no way of getting the apps installed that I needed because the dependencies debs were missing in my laptop cache and finding the automagically and downloading them into a new directory was the mission.  And I thought what if someone had dialup and didn't want to download all of those apps on their computer how could another Ubuntu friend help them out?  So let me know when you get version 1.0 released and I will test it out too.  It will be nice to have a user friendly method of doing this.

Shane

---

### Post by EXCiD3 on 2009-04-18
If you sign up to my mailing list for Keryx I can send out an email easiest to everyone. Also its a great place to send some ideas that you might have for features and other things too! :)

Keryx Mailing List: [http://groups.google.com/group/keryx-dev?pli=1](http://groups.google.com/group/keryx-dev?pli=1)

---

### Post by simon.hanna on 2009-04-30
This could be kind of messy, since it is the first one i wrote...

There is an easier way to do all this...
"Machine 1" is the Computer with access to the internet
"Machine 2" is the Computer without Internet access

The First steps are all done on machine 1
First make sure that you empty the cached package files in Synaptic preferences, so that you don't have to search through all your downloaded packages for the one you want to install on machine 2..

Search for the package you want to install...

If you have the package already installed on machine1, you can make sure you get all the packages with the dependencies by marking the package for removal and then selecting all the packages Synaptic would remove and choose to re-install them.

If you don't have the package installed on the machine1, you can just mark it for installation.

After that press Apply and choose "download Package files only" so it wont install or re-install all the packages on machine 1..
Open Nautilus and move to /var/cache/apt/archives and copy all the deb files to a pen-drive....

Then you go to machine 2
There are two ways to continue
1.
Just double-click each .deb and install them 
or
2.
Open Nautilus with administrative rights by typing: "gksudo nautilus" without quotes in the Terminal
Again move to /var/cache/apt/archives
and paste all the deb files in there

Then you just have to open Synaptic and choose the packages you wanted to install

And you're done with installing the packages...

Simon

---

### Post by EXCiD3 on 2009-04-30
Simon, yes that would work, but what if Machine 1 had a different architecture and other software was installed already? You would be downloading packages that wouldn't run on Machine 2 and would most likely be missing dependencies.

Keryx 1.0 is going to ship with some default projects with the list of packages installed by default on several versions of Ubuntu so you don't have to go home to create the project unless you have installed something on it already. That should help relieve a little bit of the trouble but you are still going to need to gather some information on that offline computer so you dont waste your time and end up getting the wrong packages or forgetting some dependencies.

---

### Post by shane2peru on 2009-04-30
> **EXCiD3 said:**
> Simon, yes that would work, but what if Machine 1 had a different architecture and other software was installed already? You would be downloading packages that wouldn't run on Machine 2 and would most likely be missing dependencies.

Keryx 1.0 is going to ship with some default projects with the list of packages installed by default on several versions of Ubuntu so you don't have to go home to create the project unless you have installed something on it already. That should help relieve a little bit of the trouble but you are still going to need to gather some information on that offline computer so you dont waste your time and end up getting the wrong packages or forgetting some dependencies.

Agreed, it is somewhat of an over-simplified approach.  In theory it looks good, but when you start messing with dependencies it is going to come up lacking here and there, speaking from experience here.  Throwing yet another architecture into the mix greatly complicates matters.  It is a thought and for some things I have no doubt it may work, for others, the dependencies are going to come up short.

Shane

---

### Post by wildman4god on 2009-05-01
I found away to install the downloaded apps with out the cli or screwing up your system:

Start [Synaptic]("https://help.ubuntu.com/community/Synaptic") Package Manager again and select the same package(s) name(s) that you initially selected. Go to “Add downloaded packages” from the File menu, notice that the window that pops up is titled "Select directory" not "Select file(s)", you do not select individual package files but the directory which contains them. Therefore you should browse to the directory which contains 'Downloads', click once on 'Downloads' to select it, then click Open. Synaptic will then scan the selected directory for packages and offer to install them.

found this on the ubuntu wiki:

[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

about half way down.

---

