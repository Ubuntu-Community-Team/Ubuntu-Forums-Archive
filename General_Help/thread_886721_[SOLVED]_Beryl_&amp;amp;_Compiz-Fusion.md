---
title: "[SOLVED] Beryl &amp;amp; Compiz-Fusion"
date: 2008-08-11
forum: General Help
---

### Post by TDragon on 2008-08-11
Hi, I have the latest release of Ubuntu and have painfully installed Beryl over the weekend (switched back from windows) w/o realizing the following:
  A) Beryl & Compiz have merged.
  B) Compiz-Fusion was already installed.

[LIST]
[*]How do I remove (uninstall) beryl from my installation w/o damaging compiz-fusion?

[*]Also, should I remove Emerald as well? If so, how?

[*]Finally, How do I add Compiz-Fusion to my sessions list so that it can be a default like Beryl (currently running Gnome w/ XGL while working on Beryl)?
[/LIST]

---

### Post by isaacj87 on 2008-08-11
The best thing to do at at this point is to start over. Remove all traces of Beryl, Emerald and Compiz Fusion. Then, reinstall Compiz Fusion and Emerald.

I have couple of questions for you. How did you install Beryl? Did you use an installation script or found instructions on how to do it via a repo?

Are Beryl and Compiz Fusion conflicting with one another?

---

### Post by TDragon on 2008-08-11
> **isaacj87 said:**
> The best thing to do at at this point is to start over. Remove all traces of Beryl, Emerald and Compiz Fusion. Then, reinstall Compiz Fusion and Emerald.

I have couple of questions for you. How did you install Beryl? Did you use an installation script or found instructions on how to do it via a repo?

Are Beryl and Compiz Fusion conflicting with one another?


As far as i know, they are not conflicting with each other. I installed Beryl by downloading the packages through apt-get. Any time I would get an install error for a missing file, I would go and download that as well.

When I run Beryl (over Gnome XGL), the only problem that I have is missing titlebars on windows, but that's a common problem from what I understand.


I'm still pretty rusty with my linux commands, etc. Can you walk me through removing them, because I don't want to have to go through the Ubuntu installation process again?

---

### Post by isaacj87 on 2008-08-11
> **TDragon said:**
> As far as i know, they are not conflicting with each other. I installed Beryl by downloading the packages through apt-get. Any time I would get an install error for a missing file, I would go and download that as well.

When I run Beryl (over Gnome XGL), the only problem that I have is missing titlebars on windows, but that's a common problem from what I understand.


I'm still pretty rusty with my linux commands, etc. Can you walk me through removing them, because I don't want to have to go through the Ubuntu installation process again?

Hmm...Well, I think you must of added a repo in order to install Beryl, if you do have the latest version of Ubuntu installed (8.04). Beryl (as far as I know) does not have Beryl in its repos. Don't worry, you won't have to reinstall Ubuntu! :)

In any case, this should remove everything Beryl related (run this command in terminal):

```
sudo apt-get remove beryl beryl-manager
```

Once we get rid of Beryl, we can get everything up an running (and deal with your missing titlebar problem ;)).

---

### Post by Crafty Kisses on 2008-08-11
I'd say start over, but I'm pretty sure you can remove Beryl by doing the following:
```
sudo apt-get remove beryl
```

---

### Post by tuxxy on 2008-08-11
Yes start over again and just reinstall emerald too, remove all traces of beryl

```
sudo apt-get remove --purge beryl*
```

---

### Post by Crafty Kisses on 2008-08-11
> **tuxxy said:**
> Yes start over again and just reinstall emerald too, remove all traces of beryl

```
sudo apt-get remove --purge beryl*
```

Yeah, that should about do it, remember any other issues post back.

---

### Post by TDragon on 2008-08-11
> **isaacj87 said:**
> Hmm...Well, I think you must of added a repo in order to install Beryl, if you do have the latest version of Ubuntu installed (8.04). Beryl (as far as I know) does not have Beryl in its repos. Don't worry, you won't have to reinstall Ubuntu! :)

In any case, this should remove everything Beryl related (run this command in terminal):

```
sudo apt-get remove beryl beryl-manager
```Once we get rid of Beryl, we can get everything up an running (and deal with your missing titlebar problem ;)).


ok.. so I ran that and **apt-get autoremove**, which took care of the child programs, as terminal suggests.

---

### Post by TDragon on 2008-08-11
> **Codename said:**
> Yeah, that should about do it, remember any other issues post back.


ok, since the last step removed Beryl, I ran the following to attempt gutting out Emerald.
[INDENT]**sudo apt-get remove --purge emerald***[/INDENT]

---

### Post by TDragon on 2008-08-11
OK, I'm attempting to install fusion and have already installed all components found in add/remove. I also have attempted to install it based upon the instructions on its website including its tarballs. It looks partially installed and many of the effects still work minus the burning windows (draw flames), etc.

---

### Post by TDragon on 2008-08-12
Currently attempting to install via a git script that i got from the fusion forums. However, it fails at the compiz install (first part)....
[INDENT][SIZE=1]>> compiz <<

 * Updating compiz
Already up-to-date.
 * Cleaning old compile
make: *** No rule to make target `clean'.  Stop.
 * Configuring new version
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:39: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
configure.ac:197: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
gtk/gnome/Makefile.am:68: Libtool library used but `LIBTOOL' is undefined
gtk/gnome/Makefile.am:68:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
gtk/gnome/Makefile.am:68:   to `configure.ac' and run `aclocal' and `autoconf' again.
gtk/gnome/Makefile.am:68:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
gtk/gnome/Makefile.am:68:   its definition is in aclocal's search path.
kde/window-decorator-kde4/Makefile.am:38: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:32: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:35: `%'-style pattern rules are a GNU make extension
kde/window-decorator/Makefile.am:38: `%'-style pattern rules are a GNU make extension
libdecoration/Makefile.am:1: Libtool library used but `LIBTOOL' is undefined
libdecoration/Makefile.am:1:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
libdecoration/Makefile.am:1:   to `configure.ac' and run `aclocal' and `autoconf' again.
libdecoration/Makefile.am:1:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
libdecoration/Makefile.am:1:   its definition is in aclocal's search path.
metadata/Makefile.am:77: GCONF_SCHEMAS_INSTALL does not appear in AM_CONDITIONAL
metadata/Makefile.am:40: patsubst %.xml.in,compiz-%.schemas,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:40: (probably a GNU make extension)
metadata/Makefile.am:43: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:53: patsubst %.xml.in,compiz-%.kcfg,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:53: (probably a GNU make extension)
metadata/Makefile.am:57: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:58: subst compiz-,,$*: non-POSIX variable name
metadata/Makefile.am:58: (probably a GNU make extension)
plugins/Makefile.am:150: Libtool library used but `LIBTOOL' is undefined
plugins/Makefile.am:150:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
plugins/Makefile.am:150:   to `configure.ac' and run `aclocal' and `autoconf' again.
plugins/Makefile.am:150:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
plugins/Makefile.am:150:   its definition is in aclocal's search path.
autoreconf: automake failed with exit status: 1
 -> compiz's autogen.sh reports errors. Bailing.[/SIZE]
[/INDENT]
I've also downloaded libtool and attempted to compile it for install. However, that doesn't seem to work properly either.

---

### Post by isaacj87 on 2008-08-12
Okay, you have to be careful here, because if you start mixing and matching installations, you going to have problems. 

There's 3 ways to have Compiz Fusion. 

1) Just using the version installed by default on Hardy (8.04). It's not the latest version and does have numerous bugs in it that have already been fixed elsewhere.

2) Downloading the source tarballs and compiling. This requires the users to install all the necessary dependencies needed to build Compiz Fusion from Source. Then, the user must proceed in downloading each part of Compiz Fusion (the core, plugins, the manager, etc) and build each. If you decide to go this route, you have to remove the existing version (default version of CF) from Hardy.

3) Installing from git. This is the bleeding edge version that contains all the latest features, bug fixes, and bugs (I don't have any problems however). This also requires the user to install all the necessary deps needed to build from source and to remove the default installation of CF. You can achieve this by git-cloning CF (each part once again) yourself or using a script that will handle it for you (such as Git-Compiz or my program FusionBuild).

At this point, I don't think you've actually managed to install CF (from either Source or Git) on top of the default install, because from the looks of it, you don't have all the dependencies installed, which is a good thing. If you did, you're going to have problems and we're going to have to remove everything CF-related and start over!

Which way would you want to install Compiz Fusion? In all honestly, I wouldn't bother trying to go the Source or Git route because the version that comes by default should be all you need. Let me know!

---

### Post by TDragon on 2008-08-12
I think I'll stick with the git-script that I was using above, its interactive, takes care of all packages involved (emerald, plugins, etc), and allows me a certain level of control for the install.
 
Should I use a similar command to remove compiz? i.e.:
[INDENT]**sudo apt-get remove --purge compiz***
[/INDENT]

---

### Post by gjoellee on 2008-08-12
I don't think uninstalling emerald is necessary, uninstall compiz:
```
sudo apt-get remove compiz*
```and install compiz by clicking on the link below
[apt://compizconfig-settings-manager](apt://compizconfig-settings-manager) /you might have to wait up to 15sec, but it is a one click install and worth it)!

---

### Post by TDragon on 2008-08-12
> **gjoellee said:**
> I don't think uninstalling emerald is necessary
 
Emerald was removed along with Beryl in previous steps.

---

### Post by TDragon on 2008-08-12
***bump***

---

### Post by TDragon on 2008-08-12
***bump***

---

### Post by TDragon on 2008-08-12
> **gjoellee said:**
> I don't think uninstalling emerald is necessary, uninstall compiz:
```
sudo apt-get remove compiz*
```and install compiz by clicking on the link below
[apt://compizconfig-settings-manager](apt://compizconfig-settings-manager) /you might have to wait up to 15sec, but it is a one click install and worth it)!


Should I reinstall compiz first, even though the git-script will take care of that when installing fusion?

---

### Post by isaacj87 on 2008-08-12
No, you must have *everything* Compiz Fusion related (from the default install) **removed** before using the git-script (even Emerald). Otherwise, you could have a conflict because 2 versions of the same thing will be installed.

Make sure everything is removed. Don't reinstall anything and then run the git-script. Most scripts will install Compiz Fusion (in its entirety) and Emerald. If you're going to use that script, don't use the link gjoellee provided.

This should remove the CF that comes with Hardy (run this command in terminal):

```
sudo apt-get remove compiz compiz-bcop compizconfig-backend-gconf compizconfig-settings-manager compiz-core compiz-dev compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins emerald libemeraldengine0 libcompizconfig0 libdecoration0 python-compizconfig simple-ccsm fusion-icon
```

Once you've removed everything, go ahead and use the script to install CF. Then you're done!

---

### Post by TDragon on 2008-08-12
Ok, so I ran that line of code you gave me, but one thing that I noticed is that Beryl is still listed under the session options on the login screen. The perhaps could be a matter of editing a file, but is there a chance that I missed something?

---

### Post by isaacj87 on 2008-08-12
Hmm...I think you're okay. Probably just a fluke.

---

### Post by TDragon on 2008-08-12
ok, here is my second attempt...

[INDENT][SIZE=1]>> compiz <<[/SIZE]

[SIZE=1] * Updating compiz[/SIZE]
[SIZE=1]Already up-to-date.[/SIZE]
[SIZE=1] * Cleaning old compile[/SIZE]
[SIZE=1]make: *** No rule to make target `clean'.  Stop.[/SIZE]
[SIZE=1] * Configuring new version[/SIZE]
[SIZE=1]autoreconf: Entering directory `.'[/SIZE]
[SIZE=1]autoreconf: configure.ac: not using Gettext[/SIZE]
[SIZE=1]autoreconf: running: aclocal [/SIZE]
[SIZE=1]configure.ac:39: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library[/SIZE]
[SIZE=1]configure.ac:197: warning: macro `AM_GCONF_SOURCE_2' not found in library[/SIZE]
[SIZE=1]autoreconf: configure.ac: tracing[/SIZE]
[SIZE=1]autoreconf: configure.ac: not using Libtool[/SIZE]
[SIZE=1]autoreconf: running: /usr/bin/autoconf[/SIZE]
[SIZE=1]autoreconf: running: /usr/bin/autoheader[/SIZE]
[SIZE=1]autoreconf: running: automake --add-missing --copy --no-force[/SIZE]
[SIZE=1]gtk/gnome/Makefile.am:68: Libtool library used but `LIBTOOL' is undefined[/SIZE]
[SIZE=1]gtk/gnome/Makefile.am:68:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'[/SIZE]
[SIZE=1]gtk/gnome/Makefile.am:68:   to `configure.ac' and run `aclocal' and `autoconf' again.[/SIZE]
[SIZE=1]gtk/gnome/Makefile.am:68:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure[/SIZE]
[SIZE=1]gtk/gnome/Makefile.am:68:   its definition is in aclocal's search path.[/SIZE]
[SIZE=1]kde/window-decorator-kde4/Makefile.am:38: `%'-style pattern rules are a GNU make extension[/SIZE]
[SIZE=1]kde/window-decorator/Makefile.am:32: `%'-style pattern rules are a GNU make extension[/SIZE]
[SIZE=1]kde/window-decorator/Makefile.am:35: `%'-style pattern rules are a GNU make extension[/SIZE]
[SIZE=1]kde/window-decorator/Makefile.am:38: `%'-style pattern rules are a GNU make extension[/SIZE]
[SIZE=1]libdecoration/Makefile.am:1: Libtool library used but `LIBTOOL' is undefined[/SIZE]
[SIZE=1]libdecoration/Makefile.am:1:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'[/SIZE]
[SIZE=1]libdecoration/Makefile.am:1:   to `configure.ac' and run `aclocal' and `autoconf' again.[/SIZE]
[SIZE=1]libdecoration/Makefile.am:1:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure[/SIZE]
[SIZE=1]libdecoration/Makefile.am:1:   its definition is in aclocal's search path.[/SIZE]
[SIZE=1]metadata/Makefile.am:77: GCONF_SCHEMAS_INSTALL does not appear in AM_CONDITIONAL[/SIZE]
[SIZE=1]metadata/Makefile.am:40: patsubst %.xml.in,compiz-%.schemas,$(xml_in_files: non-POSIX variable name[/SIZE]
[SIZE=1]metadata/Makefile.am:40: (probably a GNU make extension)[/SIZE]
[SIZE=1]metadata/Makefile.am:43: `%'-style pattern rules are a GNU make extension[/SIZE]
[SIZE=1]metadata/Makefile.am:53: patsubst %.xml.in,compiz-%.kcfg,$(xml_in_files: non-POSIX variable name[/SIZE]
[SIZE=1]metadata/Makefile.am:53: (probably a GNU make extension)[/SIZE]
[SIZE=1]metadata/Makefile.am:57: `%'-style pattern rules are a GNU make extension[/SIZE]
[SIZE=1]metadata/Makefile.am:58: subst compiz-,,$*: non-POSIX variable name[/SIZE]
[SIZE=1]metadata/Makefile.am:58: (probably a GNU make extension)[/SIZE]
[SIZE=1]plugins/Makefile.am:150: Libtool library used but `LIBTOOL' is undefined[/SIZE]
[SIZE=1]plugins/Makefile.am:150:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'[/SIZE]
[SIZE=1]plugins/Makefile.am:150:   to `configure.ac' and run `aclocal' and `autoconf' again.[/SIZE]
[SIZE=1]plugins/Makefile.am:150:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure[/SIZE]
[SIZE=1]plugins/Makefile.am:150:   its definition is in aclocal's search path.[/SIZE]
[SIZE=1]autoreconf: automake failed with exit status: 1[/SIZE]
[SIZE=1] -> compiz's autogen.sh reports errors. Bailing.[/SIZE]
[SIZE=1]______________________________________________[/SIZE]

[SIZE=1]Failed to build compiz. No reason to continue.[/SIZE]
[/INDENT]

---

### Post by TDragon on 2008-08-12
Here is the GIT script for Fusion that I'm using. Perhaps the file needs to be tweaked.

---

### Post by isaacj87 on 2008-08-12
Ahhh...I see...

That script appears to be somewhat old. You can try this version, as it is pretty close to KristianL's script.

---

### Post by TDragon on 2008-08-12
> **isaacj87 said:**
> Ahhh...I see...

That script appears to be somewhat old. You can try this version, as it is pretty close to KristianL's script.

OK. reattempting using your folder and not the original (using these switches).[INDENT][I]./git-compiz --verbose --rebuild=true --with-desktop=gnome --root=su

[/I][/INDENT][COLOR=Red]**FAILED**[/COLOR] @ same part.

[INDENT][SIZE=1]>> compiz <<

 * Cloning compiz
Initialized empty Git repository in /home/mrmonaco/Desktop/scripts/compiz/.git/
remote: Counting objects: 19839, done.
remote: Compressing objects: 100% (6866/6866), done.
remote: Total 19839 (delta 15775), reused 16306 (delta 12959)
Receiving objects: 100% (19839/19839), 6.58 MiB | 1371 KiB/s, done.
Resolving deltas: 100% (15775/15775), done.
 * Cleaning old compile
make: *** No rule to make target `clean'.  Stop.
 * Configuring new version
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:39: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
configure.ac:197: warning: macro `AM_GCONF_SOURCE_2' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.ac:33: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:39: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
configure.ac:197: error: possibly undefined macro: AM_GCONF_SOURCE_2
autoreconf: /usr/bin/autoconf failed with exit status: 1
 -> compiz's autogen.sh reports errors. Bailing.
[/SIZE][/INDENT]

---

### Post by isaacj87 on 2008-08-12
Do you have all the deps installed?

Run this command in terminal:

```
sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex libx11-xcb-dev
```

Then, try the script again.

**Off-topic**

BTW, I noticed in your signature that you have kernel 2.6.24-20 installed, did you receive an update for that or did you manually install it? Thanks :)

---

### Post by TDragon on 2008-08-12
[SIZE=1]sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex libx11-xcb-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
autoconf is already the newest version.
autoconf set to manually installed.
automake is already the newest version.
intltool is already the newest version.
intltool set to manually installed.
xsltproc is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 7.0.3~rc2-1ubuntu3) but it is not going to be installed
  libgnome-desktop-dev: Depends: libgnomeui-dev (>= 2.14.1-1) but it is not going to be installed
  libmetacity-dev: Depends: libgtk2.0-dev (>= 2.10.0-1) but it is not going to be installed
  librsvg2-dev: Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
                Depends: libgtk2.0-dev (>= 2.10.1-1) but it is not going to be installed
  libstartup-notification0-dev: Depends: libx11-dev but it is not going to be installed
  libwnck-dev: Depends: libgtk2.0-dev (>= 2.8.17-1) but it is not going to be installed
               Depends: libxres-dev but it is not going to be installed
  libx11-xcb-dev: Depends: libx11-dev but it is not going to be installed
  libxcomposite-dev: Depends: libx11-dev but it is not going to be installed
                     Depends: libxfixes-dev but it is not going to be installed
  libxdamage-dev: Depends: libx11-dev but it is not going to be installed
                  Depends: libxfixes-dev but it is not going to be installed
  libxinerama-dev: Depends: libx11-dev but it is not going to be installed
                   Depends: libxext-dev but it is not going to be installed
  libxrandr-dev: Depends: libxrandr2 (= 2:1.2.2-1) but 2:1.2.3-1 is to be installed
                 Depends: libx11-dev but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed
                 Depends: libxrender-dev but it is not going to be installed
E: Broken packages[/SIZE]

---

### Post by isaacj87 on 2008-08-12
> **TDragon said:**
> [SIZE=1]sudo apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex libx11-xcb-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
autoconf is already the newest version.
autoconf set to manually installed.
automake is already the newest version.
intltool is already the newest version.
intltool set to manually installed.
xsltproc is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 7.0.3~rc2-1ubuntu3) but it is not going to be installed
  libgnome-desktop-dev: Depends: libgnomeui-dev (>= 2.14.1-1) but it is not going to be installed
  libmetacity-dev: Depends: libgtk2.0-dev (>= 2.10.0-1) but it is not going to be installed
  librsvg2-dev: Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
                Depends: libgtk2.0-dev (>= 2.10.1-1) but it is not going to be installed
  libstartup-notification0-dev: Depends: libx11-dev but it is not going to be installed
  libwnck-dev: Depends: libgtk2.0-dev (>= 2.8.17-1) but it is not going to be installed
               Depends: libxres-dev but it is not going to be installed
  libx11-xcb-dev: Depends: libx11-dev but it is not going to be installed
  libxcomposite-dev: Depends: libx11-dev but it is not going to be installed
                     Depends: libxfixes-dev but it is not going to be installed
  libxdamage-dev: Depends: libx11-dev but it is not going to be installed
                  Depends: libxfixes-dev but it is not going to be installed
  libxinerama-dev: Depends: libx11-dev but it is not going to be installed
                   Depends: libxext-dev but it is not going to be installed
  libxrandr-dev: Depends: libxrandr2 (= 2:1.2.2-1) but 2:1.2.3-1 is to be installed
                 Depends: libx11-dev but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed
                 Depends: libxrender-dev but it is not going to be installed
E: Broken packages[/SIZE]

Well, crap...Did you upgrade directly from Gutsy? or do a fresh install...

The only thing I can suggest is this:

```
sudo aptitude install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex libx11-xcb-dev
```

I'm hoping that will take care of it, but that's wishful thinking...:(

---

### Post by TDragon on 2008-08-12
> **isaacj87 said:**
> Well, crap...Did you upgrade directly from Gutsy? or do a fresh install...

The only thing I can suggest is this:

```
sudo aptitude install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex libx11-xcb-dev
```I'm hoping that will take care of it, but that's wishful thinking...:(

Fresh install.

OK, that worked, but i had to downgrade some pkgs. I just ran the script w/ standard options and it failed. I attached the output because its getting longer and longer.

---

### Post by TDragon on 2008-08-12
This seemed to help. I got this list from the directory you sent me, but I used aptitude instead (it was listed as Hardy dependencies). Still failing at *build plugins-extra* though.

[INDENT]sudo aptitude install intltool libtool libfuse-dev python-pyrex libxslt1-dev build-essential comerr-dev debhelper diffstat dpkg-dev enscript g++ g++-4.2 gawk hspell html2text intltool-debian libacl1-dev libart-2.0-dev libasound2-dev libaspell-dev libatk1.0-dev libattr1-dev libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-compat-libdnssd1 libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libbz2-dev libcairo2-dev libcroco3-dev libcupsys2-dev libdbus-1-dev libdbus-glib-1-dev libesd0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-dev libgcrypt11-dev libgl1-mesa-dev libglade2-dev libglib2.0-dev libglu1-mesa-dev libgnome-desktop-dev libgnome-keyring-dev libgnome-window-settings-dev libgnome2-dev libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgpg-error-dev libgsf-1-dev libgtk2.0-dev libice-dev libidl-dev libidn11-dev libjasper-dev libjpeg62-dev liblcms1-dev liblua50 liblua50-dev liblualib50 liblualib50-dev liblzo-dev libmetacity-dev libmng-dev libogg-dev libopencdk10-dev libopenexr-dev liborbit2-dev libpango1.0-dev libpcre3 libpcre3-dev libpcrecpp0 libpng12-dev libpopt-dev librsvg2-dev libsasl2-dev libselinux1-dev libsepol1-dev libsm-dev libssl-dev libstartup-notification0-dev libstdc++6-4.2-dev libtasn1-3-dev libtiff4-dev libtiffxx0c2 libvorbis-dev libwnck-dev libx11-dev libxau-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxres-dev libxt-dev lua50 mesa-common-dev po-debconf poster psutils quilt x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-resource-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev python-all-dev xsltproc libxss1 libxss-dev x11proto-scrnsaver-dev coreutils librsvg2-common libnotify1 libnotify-dev libx11-xcb1 libx11-xcb-dev mesa-utils
[/INDENT]

---

### Post by isaacj87 on 2008-08-12
> **TDragon said:**
> Fresh install.

OK, that worked, but i had to downgrade some pkgs. I just ran the script w/ standard options and it failed. I attached the output because its getting longer and longer.

Okay, I understand the problem. More likely than not, you have a compiz and bcop folder(s) near the script. Delete them (and any other folders that got created) then run the script again (I know it's frustrating). What's happening is the script thinks that Compiz (and bcop) is updated, compiled, *and* installed... when in actuality it isn't. The plugins can't compile without Compiz installed so that's why it's failing. That's what I'm understanding from the error ouput.

Long story short, delete all the folders (everything the script created) then run the script again. (When all else fails, delete everything and start over again ;)). That should do the trick!

If you're tired of doing this through the forums, I'd be happy to work over MSN, AIM, or Yahoo. Let me know how it goes!

---

### Post by TDragon on 2008-08-12
getting even closer. failed @ compizconfig-python. 


Let's do this over IM. I have Google Talk, MSN, and Yahoo!. I just have to install a client on this machine :P

---

### Post by TDragon on 2008-08-12
> **TDragon said:**
> Fresh install.

OK, that worked, but i had to downgrade some pkgs. I just ran the script w/ standard options and it failed. I attached the output because its getting longer and longer.

> **TDragon said:**
> getting even closer. failed @ compizconfig-python. 


Let's do this over IM. I have Google Talk, MSN, and Yahoo!. I just have to install a client on this machine :P

Getting even closer again! Failed @ fakeargb

---

### Post by TDragon on 2008-08-13
SOLVED - Worked w/Isaac last night over IM and wound up ditching the git scripts and just installed the packages one by one with apt-get.

---

