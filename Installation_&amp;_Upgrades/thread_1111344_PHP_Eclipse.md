---
title: "PHP Eclipse"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by OldManRiver on 2009-03-30
All,

Was using HOWTO from:

[INDENT][http://www.smokinglinux.com/opensource-software/how-to-install-eclipse-and-php-eclipse-plugin-in-ubuntu-gutsy-710](http://www.smokinglinux.com/opensource-software/how-to-install-eclipse-and-php-eclipse-plugin-in-ubuntu-gutsy-710)[/INDENT]

The Eclipse installed fine but the part on installing the PHP plugin is toast.

First off I found the URL for the PlugIN source has changed to:
[INDENT][http://phpeclipse.sourceforge.net/update/stable/1.2.x/plugins/](http://phpeclipse.sourceforge.net/update/stable/1.2.x/plugins/)[/INDENT]

and not sure which file to download.  I saved my source in:

> /home/files

A shared dir I created.

My problem is none of the other HOWTOs show a step-by-step on unpacking the tar, then importing into Eclipse.  I believe, if I use the:

> tar -zxf your.downloaded.eclipse.version.tar.gz -C /usr/local/opt

the unpacked files will now install under "Local" instead of "Remote"
as the original HOWTO says.

Can I get someone to either show me a good HOWTO URL for my problem or confirm/validate my steps before I do something to screw up my machine?

Thanks!

OMR

---

### Post by OldManRiver on 2009-03-31
All,

Can I get some help here?

OMR

---

### Post by OldManRiver on 2009-05-16
Help Please

---

### Post by OldManRiver on 2009-08-22
Dang,

Guess no one uses eclipse for PHP, at least not on Ubuntu?

OMR

---

### Post by AgentWD-40 on 2010-06-09
Sure they do! Why not just install Eclipse-PDT. It comes with the PHP plugin already installed. Download it from [http://eclipse.org/pdt/]("http://eclipse.org/pdt/") and just extract the archive to a folder in your home directory. Go in to the directory and run the "eclipse" executable.

---

### Post by OldManRiver on 2011-03-20
All,

The original install was on my laptop (Widow - UGH), thank goodness last MS machine, but now installing on Ubuntu boxes, so if all goes good will try the laptop again.

Thanks!

OMR

---

### Post by OldManRiver on 2011-03-20
Hey,

What happened to this PDT repository.  Can not find it anywhere.

OMR

---

### Post by AgentWD-40 on 2011-03-28
Hey OldManRiver,

I'm not aware of a PDT repository. Here's a step-by-step procedure of how to install the latest version of Eclipse with the PHP plug-in right into your home directory:

1. Open your web browser (more than likely Firefox) and go to [http://eclipse.org/pdt/downloads/]("http://eclipse.org/pdt/downloads/")

2. Download the latest version of PDT (currently 2.2.0) for your systems architecture. This will either be the "All-In-One Linux x86/GTK 2 32-bit" or the "All-In-One Linux x86/GTK 2 64-bit" link. After that, choose the mirror closest to your location and start downloading the file.

3. On your main menu in the upper left corner of your screen go to "Places" then "Home Folder". We'll need to create a directory here to store the application. For simplicity, let's create a new folder called "Apps" by going to "File" then "Create Folder". Next type "Apps" (without the quotes) and press enter.

4. Go into your Downloads folder (assuming you haven't changed the Firefox default settings for the download manager) and open the file named something like "eclipse-php-helios-linux-gtk.tar.gz". When the archive manager pops up, extract everything into the "Apps" folder we created earlier.

5. To start Eclipse, go back to your file manager (most likely Nautilus). Go up one directory, then into "Apps", then into "eclipse", and then double click on the file named "eclipse". The application should now start up.

6. Optional: Create a shortcut on your top panel by right clicking in some blank space. On the menu that pops up go to "Add to Panel...". Double click on "Custom Application Launcher". In the "Create Launcher" dialog, enter "Eclipse" in the "Name" field. Next click the "Browse..." button and locate the "eclipse" file under "Apps/eclipse/". Next, change the icon by clicking the little image on the left side (most likely a spring) and point it to "<your home folder>/Apps/eclipse/icon.xpm". Click OK on the "Create Launcher" dialog and then Close on the "Add to Panel" dialog. You should now have a working shortcut on your top panel.

Sorry for the depth of these instructions. I wrote them not only for you, but for anybody who happens to come across this thread. 8)

---

### Post by OldManRiver on 2011-03-29
AgentWD-40,

Had already done all that and it does not install worth a crap.

Thanks anyway!

OMR

---

### Post by AgentWD-40 on 2011-03-29
What happens when you attempt to run the "eclipse" executable file?

---

### Post by OldManRiver on 2011-05-02
> **AgentWD-40 said:**
> What happens when you attempt to run the "eclipse" executable file?
A,

Guess you did not understand my last entry.  There is no executable, the build crashes, so never get anything. No file, no icon, no nothing!

OMR

---

### Post by AgentWD-40 on 2011-05-03
Hey OldManRiver,

You shouldn't have to build anything. You should just have to simply extract the archive (.tar.gz) file to a location on your system. The files you extracted should contain the eclipse executable. Hopefully this helps.

---

### Post by OldManRiver on 2011-05-13
> **AgentWD-40 said:**
> Hey OldManRiver,

You shouldn't have to build anything. You should just have to simply extract the archive (.tar.gz) file to a location on your system. The files you extracted should contain the eclipse executable. Hopefully this helps.

AWD,

Not meaning to sound rude or weird, but seems you and I are in two seperate universes.  What I find, get, download and install does not even sound like what you describe.  This is what I got from all the EClispe users I know, "a failure to communicate" and it evolves, I don't think around the users as much as it does about which source code each is using.  When I search I do not find anything for PDT, I just get a "broken link (404) message" and there seems to be over 6 different other forks of PHP plug-ins and I have never gotten any of them to work.  Oh hey I stand corrected, just retried the PDT link and actually got something this time.  Man they must have a really flaky sever, as been 404 surfing on that URL for over a month.

Well let me see if this solves my problem and frustration.

Thanks!

OMR

---

### Post by OldManRiver on 2011-06-04
AWD,

Hey it install OK, but can not run it.  This is on my machine that has the Keyboard lockup issue, having to do with switching X11 resolutions, which Eclipse does, so everytime I start it the system freezes.  I kept the download, so will port to another machine and try again.

Thanks!

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #29 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

### Post by greenpeace on 2012-06-11
This thread is a year old.. 

are you genuinely still wanting to edit PHP files in Eclipse?

This article from January this year goes through the steps, but does concede that it's not a straightforward installation:

[http://www.i-programmer.info/programming/php/3662-developing-with-php-and-eclipse-indigo.html](http://www.i-programmer.info/programming/php/3662-developing-with-php-and-eclipse-indigo.html) 

It might be a good idea to check that eclipse is really what you need to use... there are a lot of text editors, with varying levels of functionality, which are much easier to set up!


For what it's worth, I've always preferred using general-purpose tool "[joe]("http://joe-editor.sourceforge.net/")" where the keyboard shortcuts are always the same...

...but that said, I have quite enjoyed working with the extra functionality of the "[sublime]("http://www.sublimetext.com/")" text editor.

---

### Post by AgentWD-40 on 2012-09-06
Setting up Eclipse for Ubuntu is really easy and straightforward. Since you're having trouble installing it by downloading from their site there is an alternative. Just install it from the software center and then add the PHP development tools like this:

1. Load up Eclipse

2. In the main title bar of the window go to Help -> Install New Software.

3. Under "Work with" select "Indigo Update Site..." and a tree of tools will show up under the "Name" section below.

4. In this tree expand "Programming Languages" and click the checkbox next to "PHP Development Tools (PDT) SDK Feature".

5. Hit the "Next >" button and follow the instructions from there.

That's it!

---

### Post by OldManRiver on 2012-11-25
> **AgentWD-40 said:**
> Setting up Eclipse for Ubuntu is really easy and straightforward. Since you're having trouble installing it by downloading from their site there is an alternative. Just install it from the software center and then add the PHP development tools like this:

1. Load up Eclipse

2. In the main title bar of the window go to Help -> Install New Software.

3. Under "Work with" select "Indigo Update Site..." and a tree of tools will show up under the "Name" section below.

4. In this tree expand "Programming Languages" and click the checkbox next to "PHP Development Tools (PDT) SDK Feature".

5. Hit the "Next >" button and follow the instructions from there.

That's it!

Sorry no "Work with" option available, but my tech and I got something working here, but still have no idea how to use it.  Been doing web dev since 1994 and PHP since 2000 and always have used GEDIT only, so have no idea how to use and IDE.

Sorry my Bad!

Cheers!

OMR

---

### Post by OldManRiver on 2013-07-02
> **AgentWD-40 said:**
> What happens when you attempt to run the "eclipse" executable file?

AgentWD-40,

You are not insulting me with a Windows answer are you?  

I don't do Windows and haven't for 8 years.

Eclipse and Eclipse PDT are PHP therefore developed for Linux.

Therefore there is no "Executable" file. Either it works from the command line or the launcher or it does not!

When run from the command line, after latest install, here are the results:
> eclipse
find: `/root/.eclipse': No such file or directory
find: `/root/.eclipse': No such file or directory
W: Cannot inject update-sites, cannot find the correct config.
No protocol specified
No protocol specified

(Eclipse:5628): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(Eclipse:5628): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(Eclipse:5628): Gtk-CRITICAL **: IA__gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(Eclipse:5628): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(Eclipse:5628): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_display_get_pointer: assertion `GDK_IS_DISPLAY (display)' failed

(Eclipse:5628): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_screen_get_n_monitors: assertion `GDK_IS_SCREEN (screen)' failed

(Eclipse:5628): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_screen_get_monitor_geometry: assertion `GDK_IS_SCREEN (screen)' failed

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed

(Eclipse:5628): Gdk-CRITICAL **: IA__gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f04d797b30e, pid=5628, tid=139659585943296
#
# JRE version: 6.0_27-b27
# Java VM: OpenJDK 64-Bit Server VM (20.0-b12 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.12.3
# Distribution: Ubuntu 12.04 LTS, package 6b27-1.12.3-0ubuntu1~12.04.1
# Problematic frame:
# C  [libgdk-x11-2.0.so.0+0x7230e]  gdk_window_enable_synchronized_configure+0xe
#
# An error report file with more information is saved as:
# /root/hs_err_pid5628.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   [https://bugs.launchpad.net/ubuntu/+source/openjdk-6/](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#


When run from the launcher it gives:
1.  Startup screen say "Indigo" not PDT,
2.  Edit screen shows and limited editing allowed, some locked not sure why,
3.  Run attempts fail,
4.  Debug attempts fail,
5.  Bookmarks of code (Run to scenarios) not working at all.

Since it partially works from the launcher, should work seamlessly from the command line, so still some install issues, mostly not registered correctly in the "init" file so available in all directories and for all users.

Install manuals do not address this and must!

Cheers!

OMR

---

