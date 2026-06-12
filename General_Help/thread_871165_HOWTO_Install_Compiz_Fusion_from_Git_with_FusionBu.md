---
title: "HOWTO: Install Compiz Fusion from Git with FusionBuild (GUI)"
date: 2008-07-26
forum: General Help
---

### Post by isaacj87 on 2008-07-26
[CENTER][SIZE="4"][COLOR="DarkOrange"]**FusionBuild**: A GUI that installs Compiz Fusion from Git[/COLOR][/SIZE][/CENTER]

[SIZE="2"][CENTER][COLOR="Red"]*****Warning*****[/COLOR][/CENTER][/SIZE]
First and foremost, I want to let you guys know that I am *not* a programmer. I'm just a noob who does this as a hobby and wants to learn how to program. I do this out of love for Ubuntu, Linux, Compiz Fusion and the community. :) FB is the first program I have ever created. I have tested FusionBuild on my own computer and have not experienced any problems. The code is pretty hackish (at best), but serviceable IMO. FB is currently *alpha* quality and should be treated as such. If problems should arise from using FB, I want you all to know that they didn't occur purposefully. Only use FB if you are **daring and adventurous**. ;) [B]PLEASE BACK UP ALL DATA!!! 
[/B]

**One more thing to consider, CF from Git is bleeding-edge software and could possibly be unstable!**

[SIZE="2"][CENTER][COLOR="Red"]*****End of Warning*****[/COLOR][/CENTER][/SIZE]

[COLOR="Blue"]...so with that, and if I haven't scared you off, let's begin![/COLOR]

[CENTER]**_[SIZE="2"]Introduction[/SIZE]_**[/CENTER]

**What is FusionBuild?**

FusionBuild aims to be an easy-to-use GUI (designed with Glade, Python, and built on top of this [script]("http://gitweb.compiz-fusion.org/?p=users/omega/scripts;a=summary")) that will build/install/update/uninstall Compiz Fusion from Git.

**Why would I want to install CF from Git?**

In my experience, CF seems to run a lot better when compiled. Plus, the user is able to get bug fixes quicker and try out the latest features that make it into CF.

**What makes FusionBuild any different than the script I currently use?**

Honestly? Probably nothing other than it has a GUI (which is pretty basic). Most CF scripts will essentially do the same thing. I created FB because there are certain things I wanted out of a CF script and certain people just like using a GUI. Also, there are some features that certain scripts don't have (see below). If you find your current script working fine, then I suggest staying with it.

**Features:**
[LIST]
[*]Simple interface that requires little user interactivity
[*]Installs, updates, and uninstalls
[*]Removes the default version (the one included in Hardy) of CF to avoid conflicts
[*]Handles the dependencies needed to build
[*]Creates an autostart entry if the user wants CF to start on boot (removes it as well)
[/LIST]

**Some things to consider before running FB:**
[LIST]
[*]**If you've already used another script to install CF from Git, use it to remove CF!!!** To reiterate, please remove all traces of CF before using FB. This program *should* remove the CF that comes with Hardy. I'm going to add an option to allow the user to purge everything CF related.
[*]**FusionBuild (the GUI) is very GNOME focused.** While it may look like FB only works with GNOME, the script I used actually will compile for KDE3/KDE4. I *do not* recommend it however because it requires the user to install the necessary GNOME libraries needed to run FB. If the user is adventurous enough, simply install the necessary GNOME libs, go into /fusionbuild/library/core.sh (and update.sh) and comment out the GNOME ARGS and replace it for KDE3 or KDE4. Like I said, I wouldn't do that because, at this point, FB is mainly for GNOME users currently.   
[*]I've only tested FB with Ubuntu Hardy. I cannot say if FB will work with previous versions of Ubuntu (Gutsy, Feisty, etc) or any other distros (OpenSUSE, Fedora, etc).
[/LIST]

[CENTER]**_[SIZE="2"]Using FusionBuild[/SIZE]_**[/CENTER]

**Current version:** [COLOR="Blue"]0.1a[/COLOR]

**Installation and running**

Well, this is an easy one. Simply download the tar (see attachments) and do this:

[LIST=1]
[*]Place the archive in a folder
[*]Right-click the archive and choose "Extract here"
[*]Enter the uncompressed folder
[*]Double-click "fusionbuild" and choose "Run"
[/LIST]

**...or alternatively, using Terminal:**

[LIST=1]
[*]Uncompress the archive
```
tar -xzf fusionbuild-0.1a.tar.gz
```
[*]Change to the uncompressed directory
```
cd fusionbuild-0.1a
```
[*]And finally, running FB
```
python fusionbuild
```
[/LIST]

**FYI!** I've noticed that the virtual terminal window within FB doesn't have focus (something that puzzles me). When the program asks for your password, just click on the window within FB and then enter it in. :)

[CENTER]**_[SIZE="2"]Conclusion[/SIZE]_**[/CENTER]

Well, there you have it! Pretty easy stuff, huh? If you would like to watch my progress with FB, just head on over to the "blog" I've set up for it. Here's the link: [http://fusionbuild.wordpress.com]("http://fusionbuild.wordpress.com") (it's also in my signature)

If you have any trouble whatsoever, just post here on the thread and I'll do my best to get it all straightened out. If you have any errors during the compilation process, I'll try to help you. You'll probably get a better answer if you post your question [here]("http://forum.compiz-fusion.org/").

Please tell me of all bugs! and if you want to see any features. Don't hesitate to drop me a PM! The "Configuration" option of FB is currently broken, but I hope to have that working soon. I apologize for having such an unelegant way of configuring FB (see the README). I wouldn't mind some help from some programming pros as well. ;) I've also included some screenshots of the program. Have fun guys!

Last, but not least, I want to give a shout out to Master Kernel, omega, Martje_001, KristianL, and some-guy for all their hard work. Much appreciated guys!

P.S. I need to add omega to the credits! I'll make sure to include that in the next version. My apologies!

---

### Post by spirog on 2008-08-01
This is Awesome..... Installing as I type...  Great job and well Done!!!

Thanks for your time. I think others will love this as soon as they discover this

Spiro G

---

### Post by 0g_Trans_Fat on 2008-08-01
Great program, easy to use and makes installing a breeze.

Keep up the good work!

---

### Post by isaacj87 on 2008-08-02
Thanks guys! I'm glad you guys have found use for my program :)

This weekend I'm going to try and knock out a couple of bugs I've found in my personal use. 

A good tip to know, if you have any problems, just run "uninstall" and then re-run FB to install everything again. 

Let me know of any bugs you guys find! :D

---

### Post by painterh on 2008-08-12
Isaacj87;
     I have to give you kudos \\:D/. That is a very polished program for installing compiz-fusion.  I had been having quite a few issues previously (before using your script program), however after removing "ALL" traces of previously installed compiz-fusion files (both from git and synaptic), everything works nicely.  I was wondering about installing additional unsupported plugins from git.  If I use the script, found on this page:

 http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=820802&page=4[/URL]

will the new plugins install where they will be used properly, or is this a bad idea?  I really miss the screensaver and other plugins that are installed with the script posted on that page.  Again I have to say,"Nice Job!".
\\:D/

---

### Post by armageddon08 on 2008-08-12
Hey......nice work man! It's gonna be really useful to Linux n00bs and seasoned ppl alike. BTW, I think you should update your script to include more plugins like Stack Switcher, Animation Extras and more. And you should include an option which allows first time users to open Simple CCSM from the GUI itself....like after asking whether include CF in startup, it should ask the user whether he wants to configure it then and there and then give the option between Simple and Advanced.

Keep up the good work man! We are with you!

---

### Post by armageddon08 on 2008-08-12
Hey......nice work man! It's gonna be really useful to Linux n00bs and seasoned ppl alike. BTW, I think you should update your script to include more plugins like Stack Switcher, Animation Extras and more. And you should include an option which allows first time users to open Simple CCSM from the GUI itself....like after asking whether include CF in startup, it should ask the user whether he wants to configure it then and there and then give the option between Simple and Advanced.

Keep up the good work man! We are with you!

---

### Post by armageddon08 on 2008-08-12
OOps .........I think my post got posted twice by mistake. How do I delete it?

---

### Post by isaacj87 on 2008-08-12
Hey guys!

Thanks for the feedback. I was wondering when someone was going to ask me to add the unofficial plugins ;).

I've been really busy with work and whatnot, so when I get some time, I'll make sure to put all the available plugins in there, such as stack-switcher and screensaver. I'll try to make it an option as well. 

**@painterh:**

I haven't had a look at the script yet, but I'd probably hold off. I'll try and take a look at that script today to see if it'll cause any problems. If you really want those plugins, you can git-clone the individual ones you want and just build them yourself. That *should* be fairly painless ;). If you need any help with that, I'd be glad to assist you. And, I'd like to thank you for reminding me (I'll stick this in the first post as well), that before using my program or any other script/way of installing CF, one must remove *all* traces of CF from any other installs. I've had situations where people couldn't get CF to work only to find out they had 2 versions installed (which causes conflicts)! I'll probably add an option to allow the user to purge a previous CF install if the user used another script before.

**@armaggedon08:**

That sounds like a good idea! I'll try and see if I can have Simple-CCSM and/or CCSM pop up so user can set everything. Shouldn't be too hard ;). Oh, and don't worry about the double post, but if you want, you can alert a mod and they can remove it for you.

I'm going to force myself (;)) to sit down and iron out some issues/bugs that are currently in FusionBuild and try to add some more features/options to make things easier. But, I'll make sure to add those unofficial plugins soon! 

Take care guys :)

---

### Post by painterh on 2008-08-12
[B]Isaacj87;
[/B]
Thanks for the reply.  I will wait for the updated version, I do not know enough about compiling to try it safely.  I have had enough problems doing things I "thought" I knew how to do. This works very smoothly, and I am enjoying not having to fix something.  As for removing all traces of previous installs of compiz, I found when I started rooting around in the filesystem, there were all kinds of leftovers here and there just waiting to cause conflicts.](*,) Hence the need to remove them.
Cheers

---

### Post by isaacj87 on 2008-08-13
> **painterh said:**
> [B]Isaacj87;
[/B]
Thanks for the reply.  I will wait for the updated version, I do not know enough about compiling to try it safely.  I have had enough problems doing things I "thought" I knew how to do. This works very smoothly, and I am enjoying not having to fix something.  As for removing all traces of previous installs of compiz, I found when I started rooting around in the filesystem, there were all kinds of leftovers here and there just waiting to cause conflicts.](*,) Hence the need to remove them.
Cheers

Hey painterh,

I just looked at the script you wanted to use to install the unofficial plugins and it looks okay to me. There's only 2 things I don't like about it:

- The "chmod" command in the script...not sure what's the point.
- There's no way to update or uninstall the plugins after they've been installed. At least not through that script. 

Other than that, it *should* be fine! :)

---

### Post by painterh on 2008-08-13
Isaacj87;
Hey, that sounds good, but I think I would like to be able to uninstall fairly easily if necessary, such having trouble with a particular plug in.  How hard is it to uninstall plug ins that were added via the script I linked to?  I am still learning my way around Linux, and don't know much other than the most basic commands. (*Old guys don't retain as much info*).   Any idea when you might get an update put together which would include those plug ins and the other changes you mentioned?  I trying to learn more Linux commands and file system structure. 
Cheers

---

### Post by isaacj87 on 2008-08-14
> **painterh said:**
> Isaacj87;
Hey, that sounds good, but I think I would like to be able to uninstall fairly easily if necessary, such having trouble with a particular plug in.  How hard is it to uninstall plug ins that were added via the script I linked to?  I am still learning my way around Linux, and don't know much other than the most basic commands. (*Old guys don't retain as much info*).   Any idea when you might get an update put together which would include those plug ins and the other changes you mentioned?  I trying to learn more Linux commands and file system structure. 
Cheers

It should be too hard to uninstall the plugins with the script. In fact, a simple deleting of a folder would do it. I'm currently working on FB 0.1b, which will include the third-party/unofficial plugins and a few other options. I'm almost done, but I've got school, work, USMC impeding my progress! It's unfortunate when real life gets in the way ;).

---

### Post by painterh on 2008-08-14
Isaacj87
Well I took that script for a spin, and it added the plugins alright,but some of them don't stay enabled for more than a second or two.  Is that because they may not be compatible with compiz-fusion 7.4?  I did see some mention of 7.6 launchpad ppa repos being added during installation.  I think I'll uninstall them and wait for FB 1.b.  You mentioned that a simple deleting of a folder would remove the plugins installed with that script.  Where should I look for that folder? :oops:

---

### Post by isaacj87 on 2008-08-14
> **painterh said:**
> Isaacj87
Well I took that script for a spin, and it added the plugins alright,but some of them don't stay enabled for more than a second or two.  Is that because they may not be compatible with compiz-fusion 7.4?  I did see some mention of 7.6 launchpad ppa repos being added during installation.  I think I'll uninstall them and wait for FB 1.b.  You mentioned that a simple deleting of a folder would remove the plugins installed with that script.  Where should I look for that folder? :oops:

Oh no!

Well, I had another look at that script and apparently it installs unnecessary dependencies that could potentially cause conflicts (compiz-bcop and compiz-dev). The short version is that you have 2 versions of the same thing installed (possibly) because FusionBuild should of installed the same thing. No matter though, all you would need to do is remove the packages (compiz-bcop and compiz-dev):

```
sudo apt-get remove compiz-bcop compiz-dev
```

Run FB and uninstall everything (sorry). Then, re-run FB and reinstall. (It would probably be helpful to click "Yes" to the remove everything CF related question ;)). 

Now, to answer your questions...

Some of the 3rd-party plugins don't work (you said they unchecked themselves) because they are in fact too old to work Git version of Compiz Fusion that FB installs. The author(s) of the plugins need to track the core changes and update the plugins so that they work with the bleeding-edge version.

It's very simple to remove these plugins! Simple open up your Home folder and press "Ctrl+H." This will allow you to see the hidden folders/files in your Home folder. Now, look for a folder called ".compiz" (take notice to the dot before compiz). Simply remove that folder and you're good to go. :)

I'm currently testing FB 0.1b to make sure everything is fine and dandy. I hope to have it up later tonight! Once again, I apologize for not having a closer look at the script, but thankfully, it isn't a serious problem. :)

Take care!

---

### Post by tyler24_11 on 2008-08-14
Fast and easy thank you very much.

---

### Post by amadeus266 on 2008-08-17
Im trying this out as I type this. It looks great so far. I hope this makes into an upcoming release (or even into the Hardy repos).

edit: I thought I was going to have problems when I tried to rotate the cube and X locked up. But after a reboot, everything works fine.

---

### Post by 16777216 on 2008-08-27
Any progress?

---

### Post by armageddon08 on 2008-08-27
Hey isaacj87 how are things going on? Any updates on the progress? Did you add the unofficial plugins to your script?

---

### Post by painterh on 2008-08-27
> **armageddon08 said:**
> Hey isaacj87 how are things going on? Any updates on the progress? Did you add the unofficial plugins to your script?
Hey there armageddon08;  I pm'd  isaac87  yesterday, and found out that he's had some issues with the some of the unofficial plugins.  Seems that the developers of some of the plugins don't keep their plugins up to date, and FB can fail to install the plugins if something isn't up to date.  In other words, it is a work in progress.  I do know that isaac87 is extremely busy with work and school.  Hopefully he might find time to fix issues with FB 0.1b, but I wouldn't hold your breath.  I hope I haven't spoke out of turn in passing this info along. Cheers

---

### Post by armageddon08 on 2008-08-27
> **painterh said:**
> Hey there armageddon08;  I pm'd  isaac87  yesterday, and found out that he's had some issues with the some of the unofficial plugins.  Seems that the developers of some of the plugins don't keep their plugins up to date, and FB can fail to install the plugins if something isn't up to date.  In other words, it is a work in progress.  I do know that isaac87 is extremely busy with work and school.  Hopefully he might find time to fix issues with FB 0.1b, but I wouldn't hold your breath.  I hope I haven't spoke out of turn in passing this info along. Cheers

Nope......In fact...Thanks for passing the info. I am just seriously excited with FusionBuild and hope it becomes perfect. Its gonna be a great development for Compiz-Fusion for years to come.

@ isaac87: All the best to you...man!

---

### Post by isaacj87 on 2008-08-30
Hey everyone!

I just wanted to drop by and tell you all that I appreciate all the feedback/support and that FB is not dead. Quite the opposite really! Unfortunately, real-life is getting in the way. :(

As you know, my purpose for FB is to create a hassle free and easy GUI that will build CF. Unfortunately, there's one major flaw, as painterh mentioned, that will cause FB to stop the installation if one part fails. This could prove problematic for users who are new to Ubuntu/Linux. If I can find a free moment, I'll definitely take a look into the flaw. Take care everyone. :)

---

### Post by detroit/zero on 2008-10-11
Hi,

Can anyone tell me how to get the screensaver and freely-transform-windows plugins that don't seem to be included in the standard FB compile?

---

### Post by isaacj87 on 2008-10-12
> **detroit/zero said:**
> Hi,

Can anyone tell me how to get the screensaver and freely-transform-windows plugins that don't seem to be included in the standard FB compile?

Hey,

You can achieve this by doing the following...

1) Make sure you have all the necessary deps needed to build the plugins. Simply run this command in Terminal (in case you didn't know :) ):

```
sudo apt-get install git-core automake intltool libtool libfuse-dev python-pyrex libxslt1-dev build-essential comerr-dev debhelper diffstat dpkg-dev enscript g++ g++-4.2 gawk hspell html2text intltool-debian libacl1-dev libart-2.0-dev libasound2-dev libaspell-dev libatk1.0-dev libattr1-dev libaudio-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavahi-compat-libdnssd1 libavahi-glib-dev libbonobo2-dev libbonoboui2-dev libbz2-dev libcairo2-dev libcroco3-dev libcupsys2-dev libdbus-1-dev libdbus-glib-1-dev libesd0-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-dev libgcrypt11-dev libgl1-mesa-dev libglade2-dev libglib2.0-dev libglu1-mesa-dev libgnome-desktop-dev libgnome-keyring-dev libgnome-window-settings-dev libgnome2-dev libgnomecanvas2-dev libgnomeui-dev libgnomevfs2-dev libgnutls-dev libgpg-error-dev libgsf-1-dev libgtk2.0-dev libice-dev libidl-dev libidn11-dev libjasper-dev libjpeg62-dev liblcms1-dev liblua50 liblua50-dev liblualib50 liblualib50-dev liblzo-dev libmetacity-dev libmng-dev libogg-dev libopencdk10-dev libopenexr-dev liborbit2-dev libpango1.0-dev libpcre3 libpcre3-dev libpcrecpp0 libpng12-dev libpopt-dev librsvg2-dev libsasl2-dev libselinux1-dev libsepol1-dev libsm-dev libssl-dev libstartup-notification0-dev libstdc++6-4.2-dev libtasn1-3-dev libtiff4-dev libtiffxx0c2 libvorbis-dev libwnck-dev libx11-dev libxau-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev libxres-dev libxt-dev lua50 mesa-common-dev po-debconf poster psutils quilt x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-resource-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev python-all-dev xsltproc libxss1 libxss-dev x11proto-scrnsaver-dev coreutils librsvg2-common libnotify1 libnotify-dev libx11-xcb1 libx11-xcb-dev mesa-utils
```

That *should* take care of all the deps. Obviously, you'll probably already have most of them installed.

2) You have to pull freewins and screensaver from their respective branches. Again, run in terminal:

Freewins:
```
git-clone git://anongit.compiz-fusion.org/users/warlock/freewins
``` 

Screensaver:
```
git-clone git://anongit.compiz-fusion.org/users/pafy/screensaver
```

3) Now that we have the files, we can build and install them. Simply move into each directory, build it, and install it.

a)
```
cd freewins
```

b)
```
make
```

c)```
make install
```

(don't do a "sudo" make install because it's just easier to install it locally)

Simply do the same for the screensaver plugin. 

That's it! Hope that is helpful. Just drop me a post on the thread if you have any trouble. I'm hoping with the holiday season coming up, I'll have some free time to work on FB again. Take care. :)

---

### Post by Sponzenbroekske on 2008-10-24
> **isaacj87 said:**
> 
Freewins:
```
git-clone git://anongit.compiz-fusion.org/users/warlock/freewins
``` 

Screensaver:
```
git-clone git://anongit.compiz-fusion.org/users/pafy/screensaver
```


If you use git-clone then you got more chance that it will download :)

---

### Post by detroit/zero on 2008-10-24
I couldn't ever manage to grab the screensaver pack, so that git-clone thing was a big help. Never knew about it..

Now that I have the screensaver plugin, I have a problem, though: What is 'xscrnsaver' and where do I find it?
```
zero@zero-laptop:~$ git-clone git://anongit.compiz-fusion.org/users/pafy/screensaver
Initialized empty Git repository in /home/zero/screensaver/.git/
remote: Counting objects: 176, done.
remote: Compressing objects: 100% (172/172), done.
remote: Total 176 (delta 102), reused 0 (delta 0)
Receiving objects: 100% (176/176), 44.75 KiB | 48 KiB/s, done.
Resolving deltas: 100% (102/102), done.
zero@zero-laptop:~$ cd screensaver
zero@zero-laptop:~/screensaver$ make
Makefile:58: *** [ERROR] No package 'xscrnsaver' found.  Stop.
```

---

### Post by isaacj87 on 2008-10-25
> **Sponzenbroekske said:**
> If you use git-clone then you got more chance that it will download :)

My apologies! That was a careless mistake on my part. Thank you for alerting me to that. Yes, the "git-clone" part would be useful :)

I'm not sure why you're getting the dep error. Did you make sure to install all the deps that listed in step 1? I'm pretty sure that I included what was necessary to install in step 1 to avoid any dependency errors.

---

### Post by detroit/zero on 2008-10-25
> **isaacj87 said:**
> I'm not sure why you're getting the dep error. Did you make sure to install all the deps that listed in step 1? I'm pretty sure that I included what was necessary to install in step 1 to avoid any dependency errors.
Well, isn't my face red?

Guess I got all excited and "looked past" that one.

Thanks!

---

### Post by 3232 on 2008-10-26
Dude ... 5 Stars.. realy good...


thanks...
;)

---

### Post by PreviousN on 2008-11-05
This script used to work for me, but now I get make errors when the script tries to make plugins.  
>> plugins-main <<

 * Updating plugins-main
 * Cleaning old compile
 * Configuring new version
 * Compiling new version
 --> plugins-main's make returned errors. Bailing.

echo
 -> Abort? [Y/n]

It used to work fine. Any ideas?

---

### Post by detroit/zero on 2008-11-05
> **PreviousN said:**
> This script used to work for me, but now I get make errors when the script tries to make plugins.  
>> plugins-main <<

 * Updating plugins-main
 * Cleaning old compile
 * Configuring new version
 * Compiling new version
 --> plugins-main's make returned errors. Bailing.

echo
 -> Abort? [Y/n]

It used to work fine. Any ideas?I've been getting the same errors for about the last week or so when I try to run update.

---

### Post by isaacj87 on 2008-11-06
Hey guys,

I've had issues like this before. It's my understanding that all CF-Git scripts will have trouble updating if some radical change has been made to a particular branch. For example, something got deleted or moved around in plugins-main. This would totally screw the update process.

Run an "uninstall" and make sure all the downloaded files are deleted. Then, run the "install" process again. That *should* take care of it.

---

### Post by PreviousN on 2008-11-06
So I tried completly removing CF using the uninstall function. Then I restarted and ubuntu wouldn't boot. I had to run through recover mode, then continue the normal boot. It seems ubuntu didn't like not having compiz. 

Anyways, I then reinstalled (using fusionbuild). I received the same error. Here's the output of my terminal...

```

Done!

>> bcop <<

* Cloning bcop
Initialized empty Git repository in /home/previousn/.fusion_build/bcop/.git/
remote: Counting objects: 416, done.
remote: Compressing objects: 100% (378/378), done.
remote: Total 416 (delta 239), reused 0 (delta 0)
Receiving objects: 100% (416/416), 86.20 KiB | 58 KiB/s, done.
Resolving deltas: 100% (239/239), done.

Done!

 * Cleaning old compile
 * Configuring new version
 * Compiling new version
 * Installing new version

Done!

>> libcompizconfig <<

* Cloning libcompizconfig
Initialized empty Git repository in /home/previousn/.fusion_build/libcompizconfig/.git/
remote: Counting objects: 2146, done.
remote: Compressing objects: 100% (1106/1106), done.
remote: Total 2146 (delta 1386), reused 1594 (delta 1023)
Receiving objects: 100% (2146/2146), 453.30 KiB | 190 KiB/s, done.
Resolving deltas: 100% (1386/1386), done.

Done!

 * Cleaning old compile
 * Configuring new version
 * Compiling new version
 * Installing new version

Done!

>> compizconfig-python <<

* Cloning compizconfig-python
Initialized empty Git repository in /home/previousn/.fusion_build/compizconfig-python/.git/
remote: Counting objects: 517, done.
remote: Compressing objects: 100% (497/497), done.
remote: Total 517 (delta 251), reused 0 (delta 0)
Receiving objects: 100% (517/517), 105.87 KiB | 56 KiB/s, done.
Resolving deltas: 100% (251/251), done.

Done!

 * Cleaning old compile
 * Configuring new version
 * Compiling new version
 * Installing new version

Done!

>> ccsm <<

* Cloning ccsm
Initialized empty Git repository in /home/previousn/.fusion_build/ccsm/.git/
remote: Counting objects: 4803, done.
remote: Compressing objects: 100% (4472/4472), done.
remote: Total 4803 (delta 3492), reused 450 (delta 290)
Receiving objects: 100% (4803/4803), 2.21 MiB | 435 KiB/s, done.
Resolving deltas: 100% (3492/3492), done.

Done!

 * Cleaning old compile
 * Compiling new version
 * Installing new version

Done!

>> plugins-main <<

* Cloning plugins-main
Initialized empty Git repository in /home/previousn/.fusion_build/plugins-main/.git/
remote: Counting objects: 8151, done.
remote: Compressing objects: 100% (4754/4754), done.
remote: Total 8151 (delta 5612), reused 5008 (delta 3327)
Receiving objects: 100% (8151/8151), 2.94 MiB | 712 KiB/s, done.
Resolving deltas: 100% (5612/5612), done.

Done!

 * Cleaning old compile
 * Configuring new version
 * Compiling new version
 --> plugins-main's make returned errors. Bailing.

echo


```

So it seems to be a problem with plugins-main. Its not due to there being a left-over install. As I mentioned before, everything was completely removed. 

I'm now using Ibex, but I received the same error on Hardy. I'm using the amd64 build. 
My uname -a
Linux flipper 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

---

### Post by isaacj87 on 2008-11-06
> **PreviousN said:**
> So I tried completly removing CF using the uninstall function. Then I restarted and ubuntu wouldn't boot. I had to run through recover mode, then continue the normal boot. It seems ubuntu didn't like not having compiz. 

Anyways, I then reinstalled (using fusionbuild). I received the same error. Here's the output of my terminal...

I'm now using Ibex, but I received the same error on Hardy. I'm using the amd64 build. 
My uname -a
Linux flipper 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

Hey,

I'm pretty sure FB won't build CF on Ibex correctly until I update the script. I just checked the git repo and there seems to be some activity in plugins-main. It could be that it's currently broken as they're trying to work on something. I'll ask around on the IRC channel and see if it's broken. More likely than not, the script for FB might be outdated and will require work, which I unfortunately don't have a lot of time for. :(

I have some free time tonight, so I'll have a look at it. For the mean time, your best bet is to use another script that's more up to date, or the CF included in the Ibex/Hardy's repos. Sorry for the trouble guys!

---

### Post by PreviousN on 2008-11-10
That's sad. Your script/program felt really pollished. Oh well. For those looking for the other script (I don't know if it works yet) here's a link to the other thread:

[http://ubuntuforums.org/showthread.php?t=781218&highlight=script+fusion](http://ubuntuforums.org/showthread.php?t=781218&highlight=script+fusion)

EDIT: The script installed CF fine (just with not as much zest as your script). Just choose the hardy option in the script. I think the author of that script will also update it soon for Ibex.

---

### Post by detroit/zero on 2008-11-17
I just ran update for the first time in a couple weeks and everything seemed to go OK; I didn't get the abort/bailing error this time.

It said almost everything was up-to-date, though, and that made me worry a little.. But it did update emerald, the fusion icon, ccsm, and a couple other things so I guess all is well in FusionBuild land?

(P.S. I never un-/reinstalled or anything. I've just been sitting on it waiting to try it again.)

---

### Post by ellalan on 2008-12-17
Hi
I have installed the FB without any hitches and working perfectly so far, but I have question regarding any icons for FB, I couldn't see one apart from that everything is fine. Thanks for this easy to use utility.
Ubuntu 8.04
Graphics: NVIDIA 6150SE nForce430-Integrated card
Memory:2GB

---

### Post by Izek on 2008-12-17
Thanks for this OP, even though I can't thank you using the forum feature of thanks since it's more than 30 days old -_-

---

### Post by trikster_x on 2009-01-26
Let me start by saying thanks for the easy to use script.  It is a great tool for upgrading compiz in hardy.  Unfortunately I have a problem.

I downloaded and installed FusionBuild a couple days ago.  Everything went fine up to the point where I tried to move one of my windows.  As soon as I tried to grab the window, the border completely disappeared.  I figured maybe I had forgotten to set emerald as the default window decorator.  But when I went to the window decoration tab I found emerald --replace.  Next I checked Sessions, everything was fine there as well.  I removed and reinstalled through FusionBuild, thinking maybe it was a botched install.  No luck.  Next I tried removing and reinstalling emerald, still nothing.  Because I want emerald as my window decorator, I tried removing the compiz that FusionBuild installed and installing the Hardy default version.  Emerald worked again but now I was missing some key plugins for compiz:  all of the window switchers.  Unfortunately those are a necessity for my desktop setup.  So, back to the FusionBuild version.  Upon another reinstall, I discovered that I could not set the visual effects above none.  When I try to select normal or extra, I get the message "Desktop Effects could not be enabled.  With the reinstall of the default version I could select normal or extra with no problems.

I am on an Acer Aspire One  1GB RAM, 120GB HDD, 1.6GHz Atom processor,  intel 945GME Express Integrated Graphics Controller 

Hopefully this is not a dead topic and I can resolve this situation.  Thanks for any help that can be provided.

*** Okay, I got the window switchers back with the default version along with many of the newer plugins. What I really want is the cube deformation plugin. I understand that I have to have the newer version of compiz to get it so it would be awesome if I could resolve the window border problem.

---

### Post by trikster_x on 2009-01-26
sorry, I double posted somehow.

---

### Post by trikster_x on 2009-01-28
I take it this is a dead thread, then?

---

### Post by detroit/zero on 2009-07-01
So it would seem.

Does anybody know if there's a project like this completed or in the works for Jaunty?

---

### Post by isaacj87 on 2009-07-06
Hello all,

I finally break my silence after 6 months! As of January 12th, I enlisted into the Marine Corps. Because of my new job, I cannot find time to work on this. I oversimplified the situation and I thought I could put aside some time to work on this. Unfortunately, the Marines is a 24/7 job. 

I got injured during training and the Navy is determining whether or not I am fit to continue military service. If I am medically discharged, I will return to working on this project. Thank you for all the support and feedback. 

Take care,

Isaac

---

### Post by timmy334 on 2009-08-07
Isaac,
I hope you can make a full recovery eventually. I like this program. I hope you can work on it at some point without being injured ;-)

---

