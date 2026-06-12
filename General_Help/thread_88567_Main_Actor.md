---
title: "Main Actor"
date: 2005-11-10
forum: General Help
---

### Post by ColinG on 2005-11-10
Has anybody managed to get Main Actor running on Ubuntu. I tried the deb from the Main Concept site but had no joy::( 

Many thanks

---

### Post by daller on 2005-11-15
[QUOTE=ColinG]Has anybody managed to get Main Actor running on Ubuntu. I tried the deb from the Main Concept site but had no joy::( 

Many thanks[/QUOTE]

Don't know what main actor is, but drop me a link, and I will try it out :D

---

### Post by ColinG on 2005-11-15
[QUOTE=daller]Don't know what main actor is, but drop me a link, and I will try it out :D[/QUOTE]

[http://www.mainconcept.com/products.shtml](http://www.mainconcept.com/products.shtml)

Link is above and thanks for this. You need the mainActor for Linux product.
:D

---

### Post by daller on 2005-11-15
My inet connection is damn slow at the moment...

It's going to take an hour :(

...did you convert the rpm into deb? (install alien)

alien --to-deb ~/downloads/mainactor-5.5.19-suse_9.3.i686.rpm

and then "sudo dpkg -i mainactor*.deb"

---

### Post by ColinG on 2005-11-15
[QUOTE=daller]My inet connection is damn slow at the moment...

It's going to take an hour :(

...did you convert the rpm into deb? (install alien)

alien --to-deb ~/downloads/mainactor-5.5.19-suse_9.3.i686.rpm

and then "sudo dpkg -i mainactor*.deb"[/QUOTE]

No - what I did was use the deb package, which installed but then did absolutely nothing.:(

I'll try Alien.

Many thanks :smile:

---

### Post by daller on 2005-11-15
Trying to figure it out, it found that libpng was missing...

...so we install it!

sudo apt-get install libpng3 libpng3-dev (I don't know if both is needed, but it's only 60Kb :))

...now run "sudo mactor" (will start MainActor)

I assume the installation went right for you, so just use the .deb!

---

### Post by daller on 2005-11-15
I don't know why it has to be executed with superuser priv's, but I think you'll just have to live with it...

---

### Post by VosaxAlo on 2005-11-16
1) download the last beta mainactor_5.5.21-5_i386.rpm package
2) convert the RPM package in DEB with alien
3) install with dpkg -i mainactor_5.5.21-5_i386.deb
4) after a reboot I found the MainActor Icon under Applications/Audio & Video
5) run MainActor with this icon and it function well

---

### Post by ColinG on 2005-11-16
Thanks ever so much for all this. I've not had a chance to try it all yet but will do over next couple of days. I'll report back.

I've just migrated to Kubuntu from Mandriva and I have no regrets so far. Nice, very nice distro with some great help from the forums.

Great stuff:p

---

### Post by gotchawhatcha on 2005-12-04
[QUOTE=VosaxAlo]1) download the last beta mainactor_5.5.21-5_i386.rpm package
2) convert the RPM package in DEB with alien
3) install with dpkg -i mainactor_5.5.21-5_i386.deb
4) after a reboot I found the MainActor Icon under Applications/Audio & Video
5) run MainActor with this icon and it function well[/QUOTE]


Hi there,

can u tell me where yoy have found mainactor_5.5.21-5_i386.rpm?

From Mainactor web site I can download only 5.5.19 version. With this version I can't run the program. Libpng 2.0 is missing and I can't find it.

Can u help me?

ciao
Andrea

---

### Post by ColinG on 2005-12-04
Its on the website. Do a Google search foe mainactor and you'll find it:-)

---

### Post by VosaxAlo on 2005-12-04
[QUOTE=gotchawhatcha]Hi there,

can u tell me where yoy have found mainactor_5.5.21-5_i386.rpm?

From Mainactor web site I can download only 5.5.19 version. With this version I can't run the program. Libpng 2.0 is missing and I can't find it.

Can u help me?

ciao
Andrea[/QUOTE]


Hi Andrea,

the new version of MainActor is still in beta version, and for this reason is not yet downloadable from the official site.
But you can reach the link for download the last beta (now 5.5.22) in the MainActor's forum. Here I send you the link of the Linux section of the forum.

[http://forum.mainconcept.com/viewtopic.php?t=3193]("http://forum.mainconcept.com/viewtopic.php?t=3193")

best regards

---

### Post by andmer on 2005-12-06
[QUOTE=VosaxAlo]Hi Andrea,

the new version of MainActor is still in beta version, and for this reason is not yet downloadable from the official site.
But you can reach the link for download the last beta (now 5.5.22) in the MainActor's forum. Here I send you the link of the Linux section of the forum.

[http://forum.mainconcept.com/viewtopic.php?t=3193]("http://forum.mainconcept.com/viewtopic.php?t=3193")

best regards[/QUOTE]


Hi, thank you for your answer.
Sorry if I bother u but I have installed Mainactor using version 5.5.22 but whan I try to run the program with the command mactor I got the followiong message:
"mactor: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory"

Do u think I can fix it?

hope to hear from u soon

ciao
Andrea

---

### Post by binks on 2005-12-06
ok i think the package u need to install is libpng3 its in the repository

2. my problem is i have it installed and running but cant
a. import an xvid as it says unkown media type ( the clip plays in xine/mplayer)
b  the tool button has no options and this is where i import from my dv camera

cheers binks

---

### Post by VosaxAlo on 2005-12-06
[QUOTE=andmer]Hi, thank you for your answer.
Sorry if I bother u but I have installed Mainactor using version 5.5.22 but whan I try to run the program with the command mactor I got the followiong message:
"mactor: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory"

Do u think I can fix it?

hope to hear from u soon

ciao
Andrea[/QUOTE]


Ok Dear Andrea, I will explain you what you must do.

1) keep in mind that mainactor 5.5.22 beta is an RPM package 
    dedicated to SuSe. The DEB package will released from MainConcept only
    later with the official release.

2) we convert the RPM package to DEB with alien, but we not have the
    guaranty that all will perfectly function.

3) in Ubuntu Breezy the default png library is **libpng12,** but mainactor search
    for the **libpng3** older version. You can install libpng3 with synaptic.

4) during the start mainactor search for TrueType Fonts. You must create
    this folder: **/usr/X11R6/lib/X11/fonts** and copy in some original Microsoft
    TTF like Arial, Verdana, etc. You can install with synaptic the package
    **msttcorefonts** that install some Microsoft TTF.

5) mainactor has a tool for importing original video from your camera through
    the i-link-1394 interface. The library that manage this tool is
    **libmvl.DVCapture.so** and during the start of mainactor is not loaded because
    a dependend library is not found. To find what library is not found you can
    use the command **ldd libmvl.DVCapture.so** in the mainactor folder
    **/opt/MainActor_V5/libraries**. This command show you that the library
    **libraw1394.so.8** is not found. In Ubuntu we have the library
    **/usr/lib/libraw1394.so.5.2.0** installed, and we can create a link to this library
    with the name **libraw1394.so.8**.

Now you can run MainActor and you will see that all libraries are correctly loaded, and that mainactor function very well.

I hope to have help you
best regards.

---

### Post by andmer on 2005-12-14
[QUOTE=VosaxAlo]Ok Dear Andrea, I will explain you what you must do.

1) keep in mind that mainactor 5.5.22 beta is an RPM package 
    dedicated to SuSe. The DEB package will released from MainConcept only
    later with the official release.

2) we convert the RPM package to DEB with alien, but we not have the
    guaranty that all will perfectly function.

3) in Ubuntu Breezy the default png library is **libpng12,** but mainactor search
    for the **libpng3** older version. You can install libpng3 with synaptic.

4) during the start mainactor search for TrueType Fonts. You must create
    this folder: **/usr/X11R6/lib/X11/fonts** and copy in some original Microsoft
    TTF like Arial, Verdana, etc. You can install with synaptic the package
    **msttcorefonts** that install some Microsoft TTF.

5) mainactor has a tool for importing original video from your camera through
    the i-link-1394 interface. The library that manage this tool is
    **libmvl.DVCapture.so** and during the start of mainactor is not loaded because
    a dependend library is not found. To find what library is not found you can
    use the command **ldd libmvl.DVCapture.so** in the mainactor folder
    **/opt/MainActor_V5/libraries**. This command show you that the library
    **libraw1394.so.8** is not found. In Ubuntu we have the library
    **/usr/lib/libraw1394.so.5.2.0** installed, and we can create a link to this library
    with the name **libraw1394.so.8**.

Now you can run MainActor and you will see that all libraries are correctly loaded, and that mainactor function very well.

I hope to have help you
best regards.[/QUOTE]


hi, thank u very much for your instruction.
There is only one thing I'd like to ask u. Can you tell me the comman to create the link to the library?
Thank u in advance

ciao
Andrea

---

### Post by VosaxAlo on 2005-12-17
[QUOTE=andmer]hi, thank u very much for your instruction.
There is only one thing I'd like to ask u. Can you tell me the comman to create the link to the library?
Thank u in advance

ciao
Andrea[/QUOTE]


Hi andrea,

create a link to an object in Linux is a very simple thing. The GUI way is this one:
1) open nautilus as **[COLOR="DarkRed"]root[/COLOR]** user: open a terminal and input the command **sudo nautilus**.
2) go to the folder **/usr/lib/** and select the library **libraw1394.so.5.2.0**
3) with the right mouse button select **create link** option.
4) rename the new link to **libraw1394.so.8**

Best Regards

---

### Post by mediaservant on 2006-02-17
[QUOTE=ColinG]Has anybody managed to get Main Actor running on Ubuntu. I tried the deb from the Main Concept site but had no joy::( 

Many thanks[/QUOTE]

Just wanted to update the thread.  All the info is good, it got me up and running with the Mactor demo.

I'm building up a robust media/art/video linux box and I really need a good video editor on par with Sony/Vegas - which I'm used to.  I've done a project with Cinelerra so far but even with familiarity it's painful and lacks text manipulation (except for titling -) as far as I can tell!

Main Actor seems to be well beyond cinelerra in usability, and has lots of features, and easily does a lot of what vegas can do for all my intents and purposes.  Unfortunately main actor is not free....

They seem to have a new release out with a deb, but it seg faults when you go to edit text.   The new RPM doesn't do that, but the tools menu is broken on ubuntu/deb when you alien it in.  The tool menu works using the .deb, but the only thing in the menu is DV import, and kino has that covered!

Unless someone has a free/open video editor on par with MA, or some way to make cinelerra nicer than it is - I'll probably shell out for MA!

---

