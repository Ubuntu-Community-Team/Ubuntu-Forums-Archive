---
title: "Installing Adobe CS4 in Wine"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by jk.cheng on 2009-09-09
[**Installing Adobe CS4 in Wine**](http://www.jinkang-cheng.co.cc/archives/2009/09/installing-adobe-cs4-in-wine/)

When it comes to using Wine in any flavor of Linux, it is definitely best described as a love/hate relationship.  Because you will find that Wine will sometimes work straight up, and other times you will have to sacrifice a virgin to make it work.  But in any case, it is hands down one of the coolest things available for the Linux environment.

Wine stands for “Wine Is Not an Emulator”, simply because it’s not an emulator.  It is in fact a compatibility layer.  What does all this mean?  Doesn’t really matter, but if you care to find out Google can help.  But what does matter is how to install Adobe CS4 in Wine.  And that’s what I’ll be showing you how to do today.  But before we get into it, you must know that Wine is a very precise machine, different versions and different software can give you different results!  But there is hope, that hope lies in the open hands of the WineHQ developers and community.  No where else where you find a more nerdy, hardcore and devoted community.  It is a beautiful thing to see this community in action, as it is filled with some very intelligent people.

In your ventures with Wine you are more than likely going to find yourself in the WineHQ reading and reading and more reading.  This is not necessarily a bad thing because you are bound to learn something new!

With the warning out of the way, we are safe to break some stuff!  I decided to write this guide because it will show some fundamentals of how to use wine and it will even give some examples of some of the more advanced and intimidating stuff.  Things like patching to be specifc.  As Wine grows and develops, it will fix some old problems and it will create some new one’s.  Patches are often released in raw code form and require you to recompile Wine to get things back under control.  So it is especially important to know how to patch and recompile the Wine software.

This guide will probably not be a cake walk, it might not even work for you.  But I will show you the steps I had to go through to get it to work for me.

What you will need
    * A legal version of Adobe Creative Suite 4
    * Wine  1.1.26 (not installed yet)
    * Ubuntu 9.04 Jaunty Jackalope (32bit or 64bit)
    * Patience

Lets begin

Install some basic compiling tools
```
$ sudo aptitude install build-essential checkinstall
```

Backup your current configuration folder if you already have one
```
$ mv ~/.wine ~/.wineBACKUP
```

Rid yourself of any current Wine install
```
$ sudo aptitude remove wine
```

Add the Wine Launchpad PPA
```
$ sudo sh -c "echo 'deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu jaunty main' >> /etc/apt/sources.list"
$ sudo sh -c "echo 'deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu jaunty main' >> /etc/apt/sources.list"
```

Add the appropriate keys
```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
```

Update your repositories
```
$ sudo apt-get update
```

Install any needed dependencies
```
$ sudo apt-get build-dep wine
```

Make a directory to hold our source files
```
$ mkdir ~/source/
```

Navigate into our newly created folder
```
$ cd ~/source/
```

Download the Wine source files
```
$ apt-get source wine
```

Navigate into the newly downloaded wine source folder
```
$ cd wine*
```

At this point we now have the basic source files, however to make Adobe CS4 install we need to patch the wine application to correctly install CS4. Thanks to a member of WineHQ named Hans Leidekker we have a patch for bug 18070.
```
$ wget http://bugs2.winehq.org/attachment.cgi?id=22139 -O pseudo_start_msi_MTA_thread.diff
```

Apply the patch to our source files to prepare them for compiling.
```
$ patch -p1 < pseudo_start_msi_MTA_thread.diff
```

Check for all dependencies
```
$ ./configure
```

Assuming everything checks out compile the source code (depending on your computer this will most likely take around 15-20 minutes, maybe more)
```
$ make -j3 depend && make -j3
```

Once the source code finishes compiling Install the wine package. (Accept all the defaults to any question prompts unless you wish to change any)
```
$ sudo checkinstall
```

That should finalize the install of Wine. But we’re not out of the woods just yet, We must now install the dependencies for CS4.
```
$ wget http://www.kegel.com/wine/winetricks
```

Change the permissions for winetricks to make it executable
```
$ chmod a+x winetricks
```

Move winetricks to /usr/local/bin so we can execute it where ever and whenever we like
```
$ sudo mv winetricks /usr/local/bin/
```

Use winetricks to download and install our dependencies ( FYI to save yourself lots of trouble, never run winetricks as root ) This will start several windows installers. Accept all defaults by hitting next all the way through until they are all installed.
```
$ winetricks msxml6 gdiplus gecko vcrun2005 ie6 corefonts fontsmooth-rgb
```

After all the installers finish you will need to download the atmlib.dll file. A simple Google search will give you several options of where to get this file. Once you have it, move it into Wine.
```
$ mv atmlib.dll ~/.wine/drive_c/windows/system32/
```

Enter the Wine Configuration utility and go to the “Drives” tab and remove the Z: drive, by default it is bound to /

After removing the Z: drive that is bound to / Add a new drive that points to your installation media (most likely your CD/DVD drive)

Click Apply and OK

Back in your terminal, navigate to your installation media “Adobe CS4&#8243; folder
```
$ cd /media/cdrom0/Adobe\ CS4/
```

Run the Setup.exe file with Wine
```
$ wine Setup.exe
```

The Adobe CS4 install utility should now come up and begin the install.  You’ll notice that you will be stuck installing with the default options (Full install) as a separate bug prevents you from selecting and unselecting different components of the install.

I also noticed that on some of the prompts I could not select the next button with the mouse, I had to use the TAB key to select the next button.  Then again, some of the other screen’s I was able to use the mouse.

While going through the install of CS4 it stated that it crashed while trying to install Illustrator and needed to close.  However when I clicked the close button that popped up with the error the install resumed like nothing crashed at all.  Not perfect of course, but not a show stopper for everyone.

Original Post: [http://www.jinkang-cheng.co.cc/archives/20...be-cs4-in-wine/](http://www.jinkang-cheng.co.cc/archives/2009/09/installing-adobe-cs4-in-wine/)

---

