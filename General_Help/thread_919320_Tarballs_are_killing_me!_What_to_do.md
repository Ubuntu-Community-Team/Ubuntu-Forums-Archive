---
title: "Tarballs are killing me! What to do??"
date: 2008-09-13
forum: General Help
---

### Post by Pharohs on 2008-09-13
[SIZE="3"]I am almost insane from files with the ".tar.gz" extension. These are NOT anything like .zip files.  These things download and hide in the file system and I can't find them.  The ones that do land on the desktop are unusable.  The instructions for dealing with these things claim to be simple, step-by-step instruction, but the authors are delusional. I am a beginner and you have to make it simple to understand.  I need someone to explain in English and not in computer code.[/SIZE]  :confused:

---

### Post by mb_webguy on 2008-09-13
If you're using Ubuntu, you should be able to open the files using Archive Manager.  Just double-click on the file in Nautilus (the file manager) and then click the Extract button.

---

### Post by tact on 2008-09-13
Ok you are a beginner...  here is the good oil in non code language.

You can get, install, and use software in a variety of ways:
-  the simplest and easiest click on Applications>Add/Remove... and search for what you want.
-  just as easy, click on System>Admin>Synaptic Package Manager ...  and again search the roughly 25,000 packages for what you want.

The above two methods will download and install perfectly whatever you want, provided what you want is in the repository.

If what you want is in the repository...  use it!  Forget about downloading source or tarballs.

If you cannot find what you want in an official repository you MAY still find better options than tarballs:
-  Sometimes kind individuals make the effort and package up software that is not in the repositories as "deb" packages.  Download, and double click, software installs and all dependencies are looked after and later you can remove using Synaptic if you like.  Nice.

-  Sometimes  kind individuals make the effort and package up software that is not in the repositories as "Personal Package Archives", or "PPA's".   Add the PPA address to your software sources list, refresh packages, then use synaptic to install (or the commandline equivalent "apt-get install").

So when you see a write-up about some software you must have and instructions to download some tarball, DEB, or source...  in order of preference and total ease:
- FIRST!   Check if its available via Synaptic (System>Admin>Synaptic)
- Second!  Google for DEBs or whether someone has built a PPA site
- then only think about trying tarballs or source compiles.

---

### Post by tact on 2008-09-13
...now as to where the tarballs you download disappear to?  Who knows!  hehehe.  Hey if you are using firefox it defaults to saving downloads to the desktop, but can be configured to save elsewhere.  Where is your's configured to save downloads?

When you initiate a download.... usually a dialog comes up asking whether to save the file or open it with the default application.  ALWAYS choose to save the file (to desktop presumably).   If you choose the archiver application then the file is kept in a temp folder to be deleted later, never makes it to the desktop, and you really don't want to open in the archiver application.  Its better to save the file to desktop, then right click on it and "Extract here".   No need to run the archiving application at all.

---

### Post by kostkon on 2008-09-13
> **Pharohs said:**
> [SIZE="3"]I am almost insane from files with the ".tar.gz" extension. These are NOT anything like .zip files.  These things download and hide in the file system and I can't find them.  The ones that do land on the desktop are unusable.  The instructions for dealing with these things claim to be simple, step-by-step instruction, but the authors are delusional. I am a beginner and you have to make it simple to understand.  I need someone to explain in English and not in computer code.[/SIZE]  :confused:
Why do you have to deal with tar.gz files?! What programs are you trying to install?

---

### Post by Pharohs on 2008-09-14
1) I found the tarballs in a temp folder and moved them to the desktop. 

2) I have found the applications in other formats and installled them.

3) I still would ike to know how to deal with tarballs directly, but that will come another day.

4) THANK YOU ALL! I am learning slowly, but surely.  One day it will all come together.  :)

---

### Post by Pharohs on 2008-09-14
Ok. Here is a perfect example.  I just downloaded Soundconverter to convert .mp3 to .ogg.  It only comes as ***soundconverter-1.3.2.tar.gz***.  So what , **specifically** must I do to make this useful?  I tried to extract it, but then what- I don't understand what's going on at all.

I was wrong. It just looked like it only came as a tarball on their download site.

---

### Post by mb_webguy on 2008-09-14
Ok...  Tarballs really *are* like zip archives.  I think you're just making things difficult for yourself.  

First download the tarball to somewhere convenient, like your home directory.  Then, in Nautilus, double-click on the archive to open it in Archive Manager (just as you would in Windows).  Click the Extract button, and give it the location where you want the files to be extracted.  Then click Extract.  This will extract the archive to the location you gave it.

Now you're done with the tarball.  Open the terminal and navigate to the location where you extracted the archive.  To install the software, you will sometimes have a binary installer, in which case you would type "./<nameoftheinstaller".  Most of the time however, you will have to type "./configure", and then "make", and then "sudo make install".

---

### Post by Pharohs on 2008-09-14
Now we're getting somewhere! :)  I've only been using Linux in earnest for 3 days.

So, what does the "./" mean?

And what about "make"?  I looked it up in the commands glossary and here's what it said:

[I][B]make

make [options] [targets] [macro definitions]

Update one or more targets according to dependency instructions in a description file in the current directory. By default, this file is called makefile or Makefile. Options, targets, and macro definitions can be in any order. Macro definitions are typed as:

name=string[/B] [/I]


Huh???  Can someone tell me that again in simple English?  If I ever learn how to do this, I promise to write a very simple explanation for the next noob, so they can understand it.

---

### Post by mb_webguy on 2008-09-14
You're trying to install a program from source code (which isn't the best way to go about it if there's any other option).  That means that you have to compile the code and configure it for your particular system.

That's what the commands "./configure", "make", and "make install" do, in a nutshell.  

The "./" in front of "configure" just means "this directory".  A single dot (".") is a reference to the current directory, and a double-dot ("..") is a reference to the parent of the current directory.  For example, if you are in /home/yourname/Desktop, and you wanted to view the contents of /home/yourname/Downloads, you could type "ls /home/yourname/Downloads", or use the double-dot reference with "ls ../Downloads", since you know that Downloads is in the same parent directory as the one you're currently in.  So "./configure" means run the configure script located in this directory, as opposed to some other configure script that may be located somewhere else on your system.  The configure script configures the source code to be compatible with your system, and creates a makefile, which provides instructions on how to compile the source code.

The make command compiles the source code according to the makefile generated by the configure script.

Finally, the "sudo make install" again uses the makefile to move the compiled code to the proper location(s) on your system, thus installing the code.  Unlike the previous commands, this command requires root permissions (and therefore "sudo") because it is moving the compiled software into directories for which a normal user wouldn't have write permissions.

As I and others have said, this is the most onerous and potentially hazardous way to install software.  The first place you should always look is the repositories.  These applications have been reviewed by the community to assure that they are safe and compatible with Ubuntu.  If the software isn't in the official repositories, it may be found in a third-party repository or PPA (personal package archive).  Once these repositories are added to your sources, you can install the software just as you would from the regular repositories.  If you can't find the software in a third-party repository or PPA, then you should look for a deb file.  This is a version of the software pre-packaged for Debian-based Linux systems (which includes Ubuntu).  To install software from a deb, you basically just double-click the file and click the Install button.  

All of these methods are preferred to installing from source not only because they are easier (which they are), but because software from repositories and popular PPAs have been checked on some level for malicious code.  When compiling source code, you really have no guarantee that the code actually does what you think it does.  While Linux doesn't get viruses, it will run malicious code just fine if you actually tell it to do so.

---

### Post by spec-chum on 2008-09-14
soundconverter is in the universe repository, so all you should need to do is ensure that's enabled in Software Sources and search for it in synaptic or Add/Remove.  Tick a box and it'll install.  No need for tarballs.

---

### Post by aysiu on 2008-09-14
> **spec-chum said:**
> soundconverter is in the universe repository, so all you should need to do is ensure that's enabled in Software Sources and search for it in synaptic or Add/Remove.  Tick a box and it'll install.  No need for tarballs.
If you need instructions with screenshots, go here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Raffles10 on 2008-09-14
Most of the time you won't need tarballs anyway.

```
sudo apt-get install soundconverter
```

Will do everything for you automagically. To search for a particular application:

```
apt-cache search soundconverter
```

Other useful apt commands:

sudo apt-get remove (uninstall a package)
sudo apt-get remove --purge (uninstall & remove configuration files)
sudo apt-get clean (this will clear the downloaded archive files)
sudo apt-get autoclean (this will clear old archive files)
sudo apt-get autoremove (this will clear all auto installed programs no longer needed, & remove unneeded dependencies).
sudo apt-get check (just to make sure your ok)
sudo apt-get upgrade (upgrade packages)
sudo apt-get update (updates package repository information)

Or just use Add/Remove Programs.

---

### Post by Pharohs on 2008-09-14
Ok. Great!  I think I've got it now.  Thank you all for your patience.  :)

---

### Post by baruch60610 on 2008-09-15
I would avoid using tarballs, at least for now.  You can get your software much more easily.

I recommend using synaptic for installing programs.  Synaptic doesn't come installed by default, so you'll have to get it.  Go to the "Add/Remove Programs" option in your menu.  Use the search bar to find "synaptic".  Click the checkbox to install it.  Once it has installed, exit the Add/Remove Programs application.

Why not just use the Add/Remove Programs application?  I don't like it, because after you make each selection, it checks to see if there are conflicts.  This can take a long time if you're trying to install several programs.  It should wait until you're all finished choosing, and *then* check.

Anyway, exit this application, then start synaptic (it should be under your "System" submenu.

Here again, you can search for your desired program.  In your case, you'd click on the Search button in the toolbar, enter "soundkonverter" in the search bar, and let it go find the program.  If it finds it (and it should), you check the box to install it.  You can pick whatever programs you want, using search or browsing through the various sections it will display.  When you're all done, click on "Apply" and let it go.

Note that if this program seems to hang, it may be waiting for input from you.  Sometimes it will check for bug reports on the programs you're installing.  If it finds one, it will pause and ask you if you're sure you want to install.  This question won't show, unless you click the "show details" option as synaptic is working.  If you see there is a question, you can type 'y' or 'n'.

I recommend using one of the package managers, instead of using tarballs, whenever possible.  These managers keep track of dependencies and conflicts, preventing you from accidentally installing or removing things that could cause problems.

Tarballs may be necessary in cases where a program isn't available through an Ubuntu repository.  You may want to use a tarball when you want to compile a program with special options such as optimization for your particular machine or needs.  But in general, it's safer and easier to use a package manager.

HTH

---

