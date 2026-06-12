---
title: "Mac like desktop customization"
date: 2008-08-13
forum: General Help
---

### Post by vidgms on 2008-08-13
Hello all,

I am looking for something that will completely or for the most part, make my desktop look like a Mac.  I have found bits and peaces around the net but nothing that truly works, except for this one.

I found Mac4lin.  I downloaded it and couldn't even get past step one because the most updated documentation was for GNOME 2.20 which now everyone has 2.22. It truly does look the most like a Mac desktop that I have seen yet and would gladly use it but I have problems. 

Can anyone help me with putting Mac4lin onto GNOME 2.22 or have any other full programs such as Mac4lin?

THanks,
vidgms

Edit:  I also am using Ubuntu 8.04.

---

### Post by ad_267 on 2008-08-13
What exactly are you having problems with? The themes from Mac4Lin should still work with the current GNOME. 

I suggest reading through these first to get an idea of how to apply different themes:
[http://justanothertechblog.blogspot.com/2007/03/quick-guide-on-customizing-ubuntu.html](http://justanothertechblog.blogspot.com/2007/03/quick-guide-on-customizing-ubuntu.html)
[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

Desktop effects sticky:
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

This explains how to install AWN:
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by conundrumx on 2008-08-13
The Mac4Lin iconset is for GNOME 2.20, and some icons will not display correctly unless you update them.  The GTK theme in general leaves something to be desired.

However, if you get a newer icon theme compatible with GNOME 2.22 you can accomplish decent results with other parts of Mac4Lin.

---

### Post by vidgms on 2008-08-13
I just started exploring and I found some things that really changed everything for me.  The documentation provided for the Mac4lin really sucks and is not very descriptive on what to do, but since I am curious I have fixed some things but will look over that pages that you provided to get all the kinks worked out. 

Thanks.

---

### Post by SpikeyMike on 2008-08-13
Hi, I just followed this howto and it worked very well, didn't encounter any problems:

[http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/](http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/)

The only thing I would like is to make the dock more mac-like, it works ok but it can be a bit buggy and it doesn't have the magnifying glass effect that the mac dock has

hope this works for you

Spikey

---

### Post by billgoldberg on 2008-08-13
> **SpikeyMike said:**
> Hi, I just followed this howto and it worked very well, didn't encounter any problems:

[http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/](http://rockmanx.wordpress.com/2008/06/02/make-your-linux-ubuntu-look-like-a-mac-hardy-heron/)

The only thing I would like is to make the dock more mac-like, it works ok but it can be a bit buggy and it doesn't have the magnifying glass effect that the mac dock has

hope this works for you

Spikey

Use the cairo dock instead (and the plugin package)

One of the standard skins is the max osx one.

Google for install instructions.

---

### Post by vidgms on 2008-08-13
Cool.  Ok, I have everything I need just about.

Is there a way to change the yellow/green/red buttons to the other side of the window, on top?

And

Does anyone know how to change the top panel so it says, Finder or whatever the apple bar says?  I can't find anywhere to change it or what to do to change it.

Thanks

---

### Post by conundrumx on 2008-08-13
I don't know that Metacity (Gnome's WM) can do buttons on the opposite side.  I do know Emerald (Compiz's window decorator) can.  As far as your other question, could you be looking for Global menu?  (Search for it on the wiki).

---

### Post by vidgms on 2008-08-13
I do have Emerald and followed the instructions that I find everywhere and nothing happened.

---

### Post by SpikeyMike on 2008-08-13
> **billgoldberg said:**
> Use the cairo dock instead (and the plugin package)

One of the standard skins is the max osx one.

Google for install instructions.


hi, where can I find the cairo dock? couldn't find it

Spikey

---

### Post by hotrod6657 on 2008-08-13
> **vidgms said:**
> I do have Emerald and followed the instructions that I find everywhere and nothing happened.

Do you mean that Emerald runs and everything but you can't get any of the themes to take effect?  If that's it then you can just do Alt + F2 and type emerald --replace.  That should make the theme you selected in emerald take effect.

---

### Post by SpikeyMike on 2008-08-13
its ok I found it, thanks for your advice, it seems much better than the avant window manager :o)

Spikey

---

### Post by SpikeyMike on 2008-08-13
> **vidgms said:**
> I do have Emerald and followed the instructions that I find everywhere and nothing happened.

also not sure exactly what the problem is your encountering, did you import the mac4lin theme into emerald and then select it and click refresh?

Spikey

---

### Post by vidgms on 2008-08-13
Ok, so that emarald --replace thing worked. THanks for that.

Now the only thing that needs changing is the panel/toolbar/menubar to have the apple logo and wording or whatever it has.

Thanks

---

### Post by ad_267 on 2008-08-14
> **vidgms said:**
> Ok, so that emarald --replace thing worked. THanks for that.

Now the only thing that needs changing is the panel/toolbar/menubar to have the apple logo and wording or whatever it has.

Thanks

Someone's already said that it's called global menu. Just do a google search for Ubuntu global menu. I found this: [http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu](http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu)

---

### Post by vidgms on 2008-08-14
From everything I have found, on the actual website that made it, it said that it was out of date with a warning and everything.  And the comments say it doesn't work so I would rather not use something that multiple people says doesn't work.

Is there any way to change it without this method?

Thanks

---

### Post by ad_267 on 2008-08-14
That's the only way I know of and I'm pretty sure it works fine. The part about it being obsolete is for Global menu for GNOME 1.x. The google code page is for the GNOME 2 version. It has a warning about the software being alpha and not fully tested.

This site here also shows how to do it in Hardy:
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/)

---

### Post by vidgms on 2008-08-14
I'm sure all this works.  I am just computer/ mostly ubuntu illiterate.  I actually know what to do but when I try I usually get errors saying that it didn't work or no location or something along those lines.

Any help for me on this?  Anyone?

---

### Post by ad_267 on 2008-08-14
Well you can just try it and post the errors here. All of those steps could easily be done graphically but it's just easier to give instructions with commands. 

If you'd prefer to do it the graphical way just download this:
[http://gnome2-globalmenu.googlecode.com/files/gnome-globalmenu-0.4-svn964.tar.gz](http://gnome2-globalmenu.googlecode.com/files/gnome-globalmenu-0.4-svn964.tar.gz)

Extract it to somewhere then double click on all of the .deb files in the globalmenu directory to install them.

If you do want to learn about using the command line there are a lot of tutorials out there and it can be very powerful.

---

### Post by vidgms on 2008-08-14
That last one was actually a little useful but on the libgtk2.0 bin I got an error that said that one of the dependencies was not satisfiable.  Is there something I am missing.

Oh, I guess I have amd64 and not i386 because the other .deb files didn't intall.

---

### Post by ad_267 on 2008-08-14
Did it say what dependency? You should be able to install the package it needs using Synaptic.

---

### Post by billgoldberg on 2008-08-14
> **SpikeyMike said:**
> hi, where can I find the cairo dock? couldn't find it

Spikey

From my customizing blog post:
> 
**12. Installing a dock**

There are loads of dock, and  I compared them in [this]("http://linuxowns.wordpress.com/2008/05/08/the-best-and-worst-docks-for-ubuntu/") post.

I believe the best dock is “cairo-dock”.

To download this dock, visit [this]("http://developer.berlios.de/project/showfiles.php?group_id=8724") site and download “cairo-dock_v1.5.6_i686.deb” and “cairo-dock-plug-ins_v1.5.6_i686.deb“.

First install the dock, then the plugin package.

Install them by double-clicking the file.

You’ll need to enter your password. Then press the big button on the top right.

After you installed both packages, go to “applications -> system tools -> cairo-dock”.

You’ll be greeted by a little wizard that will help you select the theme, …

You can easily change it’s option by right-click the dock, go to “cairo-dock” and press “configure’ or “manage themes”.

To start the dock when you boot up your pc, go to “system -> preferences -> sessions”, press “add” and in the middle field enter “cairo-dock” (without the ” “). You can make up what you put in the other fields.

---

### Post by vidgms on 2008-08-17
Is there a way that I could change the menu icon to the apple through gconf-editor?  It seems like that would be the easiest way to change it.

Thanks,
Vidgms

---

### Post by FerN(SA) on 2008-08-17
You can just replace the icon

It could be found here:
/usr/share/icons/gnome/32x32/places

the 32x32 is the size of your panel, if your panel is 24 pixels you have to replace the icon in the 24x24 folder

---

### Post by vidgms on 2008-08-17
See thats it.  I read all this stuff about the /usr folder or place and don't know where to find it, so I don't reall know how to change it by saying telling me to change it through /usr.

Thanks for the help though, I'm sure it works and if you could help me to find it I would surely give it a try.

Vidgms

---

### Post by hotrod6657 on 2008-08-18
If your file structure is normal then you should be able to get to it by doing the following:

click places at the top of the screen.

double click on "Filesystem"
double click on the "urs" folder
then "share"
then "GNOME"
then "32x32"
then "places"

Unless you have a unique file structure it should work like that.

Alternatly you can just copy:
```
/usr/share/icons/gnome/32x32/places
```

In to the location bar at the top of a window.

Open up places and then hit computer.  Paste that location in to the location area.  If you don't see location click the icon below the back button.

Did that help or is that a complete over simplification of the problem you're having?

hotrod

---

### Post by vidgms on 2008-08-18
So that worked and I understand what the USR folder is now.

But,
Dont you just hate it when there's a but,

But, how do I change the picture/emblem/icon?  I assume that it's one of the icons with menu in it, probably the start-here.png emblem.


I think I just found something.  I think the reason it isn't coming up is because I DO NOT get the .tar.gz mac icons from the Mac4Lin file. I GET the icons in a file but I do not get the .tar.gz folder that is need to be installed.  Does anyone have this or am I just thinking this is what I need when I don't really need it and no one has it?

---

### Post by EnGorDiaz on 2008-08-18
i was just like you until i made my desktop look like this

---

### Post by hotrod6657 on 2008-08-18
I don't know if this would help but i did find this site:
[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/]("http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/")

If you don't have all the items that it says to download then I'm sure that would be a bit of a problem.  I would try following a tutorial once you have all the files downloaded.  I'm sure their way is going to be way easier than manually changing the files.

hotrod

(i've not used this tutorial so i can't say that it works but it's worth a shot, at least to get the downloads you need.)

**EDIT**I see that it's just the icon set file you seem to need.  this: [http://maketecheasier.com/a/Mac4Lin_Icons_modified/](http://maketecheasier.com/a/Mac4Lin_Icons_modified/) seems to download correctly for me.  If that's all you're missing then maybe you'll be good to go with it.  The site i linked to seems to be using the same project (mac4lin).

---

### Post by vidgms on 2008-08-19
That is what I downloaded.

Did you only get the icons in pictures or did you get a file to install?

---

### Post by hotrod6657 on 2008-08-19
I downloaded the .tar.gz file to my desktop.  Then go to system, preferences, appearance.  There, on the window you see, drag the tar acrhive you just downloaded into the place where all the themes are.  It might ask about using the theme now or whatever.  If you say yes it should apply the icon theme.  If not click customize at the bottom of the screen and go to the icons tab.  select the mac4lin option and it should all change.

Let me know if that works for you, it worked for mine, changed the ubuntu icon and everything.

Hope that helped.

hotrod

---

### Post by vidgms on 2008-08-19
OMG, thank you so much, that was so easy, why couldn't the previous people help me the way that you have helped me!

Thanks, 
Vidgms

---

### Post by hotrod6657 on 2008-08-19
haha, no problem, glad that cleared it up for you!  That's one of those things that I had a heck of a time with until I figured it out.  Pretty much anything that you control through that menu can be added by dragging the file like that.  

Much less messy than messing with a bunch of extracting.  

Also, now that it's installed, you don't need to keep the folder around.  You might want it for future projects, but moving or deleting it shouldn't cause you any problems.

Glad you're back on track, good luck!

hotrod

---

### Post by Mgiacchetti on 2008-08-20
[This]("http://ubuntuforums.org/showpost.php?p=5578231&postcount=31") should help you with the cairo-dock, plus that post has some eye candy in it for you.

---

