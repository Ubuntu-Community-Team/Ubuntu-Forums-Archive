---
title: "Murrine SVN trouble"
date: 2008-10-12
forum: General Help
---

### Post by dbbolton on 2008-10-12
Here are the exact steps I followed to install the SVN version of Murrine: 
 
1. Uninstalled old version of murrine engine 
2. svn checkout [http://svn.gnome.org/svn/murrine/trunk/](http://svn.gnome.org/svn/murrine/trunk/) murrine 
3. cd murrine 
4. ./autogen.sh --enable-animation 
5. make 
6. make install 
 
None of these steps returned any errors. However, the engine is not working. When I try to use a theme designed for this version of the engine (like MurrineGlow), I end up with Redmond-like widgets. 
 
Does anyone know what's going on?

---

### Post by dbbolton on 2008-10-14
bump

---

### Post by Ub1476 on 2008-10-14
Make sure you use the latest Murrine Glow (0.2), because the first version doesn't support the latest svn version of murrine. 

Personally I just use the deb from [Shiki-Colors]("http://www.gnome-look.org/content/show.php/Shiki-Colors?content=86717").

---

### Post by perfectska04@hotmail.com on 2008-10-14
You can either try my .debs like Ub1476 mentioned, since I always upload the latest revision soon after it's out. You can also do this (it's what I use to build them):

1. Remove any previous version you installed with make install
2. Install Checkinstall (sudo apt-get install checkinstall)
3. svn checkout [http://svn.gnome.org/svn/murrine/trunk/](http://svn.gnome.org/svn/murrine/trunk/) murrine 
4. cd murrine 
5. ./autogen.sh --prefix=/usr --enable-animation
6. make
7. sudo checkinstall
8. It's important that you edit the checkinstall info. Make the name of the package gtk2-engines-murrine and use a numerical value for version and release number. Someting like version 0.60 and release 1 should work, just make sure to choose higher version/release number than the one you already have installed.

Edit: Also make sure any murrine theme you're using doesn't have the "style" option anywhere. This option was deprecated and is now replaced by "profile". Any murrine theme with "style" on it will not work in newer versions of Murrine SVN.

---

### Post by dbbolton on 2008-10-14
> **perfectska04@hotmail.com said:**
> You can either try my .debs like Ub1476 mentioned, since I always upload the latest revision soon after it's out. You can also do this (it's what I use to build them):

1. Remove any previous version you installed with make install
2. Install Checkinstall (sudo apt-get install checkinstall)
3. svn checkout [http://svn.gnome.org/svn/murrine/trunk/](http://svn.gnome.org/svn/murrine/trunk/) murrine 
4. cd murrine 
5. ./autogen.sh --prefix=/usr --enable-animation
6. make
7. sudo checkinstall
8. It's important that you edit the checkinstall info. Make the name of the package gtk2-engines-murrine and use a numerical value for version and release number. Someting like version 0.60 and release 1 should work, just make sure to choose higher version/release number than the one you already have installed.

Edit: Also make sure any murrine theme you're using doesn't have the "style" option anywhere. This option was deprecated and is now replaced by "profile". Any murrine theme with "style" on it will not work in newer versions of Murrine SVN.
Would these debs work with Debian sid? I'm not sure of the various dependencies and which versions are required.

Edit: I tried the deb and it does work for Debian sid. Thank you very much.

---

### Post by perfectska04@hotmail.com on 2008-10-14
> **dbbolton said:**
> Would these debs work with Debian sid? I'm not sure of the various dependencies and which versions are required.

Eh, I'm not sure since I've only tested them in Hardy and built them for it. You can however try following my instructions, they would result in the same .debs but you'd be certain that they will work with your system and can be easily removed/upgraded.

---

### Post by dbbolton on 2008-10-14
Also, do you know where "colorize_scrollbar" gets the color from?

---

### Post by BOBSONATOR on 2008-10-14
./autogen.sh --prefix=/usr 

Is what you were missing, same thing happened to me :)

---

### Post by perfectska04@hotmail.com on 2008-10-14
> **dbbolton said:**
> Also, do you know where "colorize_scrollbar" gets the color from?

It should get it from @selected_bg_color

---

### Post by dbbolton on 2008-10-15
> **BOBSONATOR said:**
> ./autogen.sh --prefix=/usr 

Is what you were missing, same thing happened to me :)
Hmm, that could have been it. I've never had to add that flag when compiling in the past, though.

---

### Post by j_baer on 2008-11-15
> **perfectska04@hotmail.com said:**
> You can either try my .debs like Ub1476 mentioned, since I always upload the latest revision soon after it's out. You can also do this (it's what I use to build them):

1. Remove any previous version you installed with make install
2. Install Checkinstall (sudo apt-get install checkinstall)
3. svn checkout [http://svn.gnome.org/svn/murrine/trunk/](http://svn.gnome.org/svn/murrine/trunk/) murrine 
4. cd murrine 
5. ./autogen.sh --prefix=/usr --enable-animation
6. make
7. sudo checkinstall
8. It's important that you edit the checkinstall info. Make the name of the package gtk2-engines-murrine and use a numerical value for version and release number. Someting like version 0.60 and release 1 should work, just make sure to choose higher version/release number than the one you already have installed.

Edit: Also make sure any murrine theme you're using doesn't have the "style" option anywhere. This option was deprecated and is now replaced by "profile". Any murrine theme with "style" on it will not work in newer versions of Murrine SVN.

I'm confused by the "profile" option. Are you referring to the style arguments found in the gtk.rc or something else?

:)

---

### Post by indecisive on 2008-11-22
How do I install in Intrepid, where older? packages are installed, and are needed for human-artwork and ubuntu-desktop?

---

### Post by dbbolton on 2008-11-22
> **indecisive said:**
> How do I install in Intrepid, where older? packages are installed, and are needed for human-artwork and ubuntu-desktop?
Those are meta-packages. You can safely remove them.

---

