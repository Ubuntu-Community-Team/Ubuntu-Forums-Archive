---
title: "Theme Install Problem (Ubuntu 8.04)"
date: 2008-10-10
forum: General Help
---

### Post by RandomIP on 2008-10-10
Having a problem installing a theme with Ubuntu, was wondering if I could get a little help, google couldnt seem to provide me with a good soloution.

Installing a tar.gz Theme package from [http://ubuntu-snippets.blogspot.com/2008/05/die-hard-40-comes-to-ubuntu.html](http://ubuntu-snippets.blogspot.com/2008/05/die-hard-40-comes-to-ubuntu.html)

tried to install emerald using sudo apt-install emerald and got the error 
Couldn't find package emerald. Any idea what i'm doing wrong?

or is it a ID 10 T error?

Thanks to any help provided


(PROBLEM RESOLVED)

---

### Post by loomsen on 2008-10-10
OK, I don't know if I got you right, but the first thing to be mentioned:
> sudo apt-install emerald

should read:
[code]sudo apt-get install emerald[/quote]

If you have emerald, the window decorator itself installed, and just want to add a theme for it (which should be called foo-bar.emerald), just doubleklick on the package you downloaded. 
You don't need sudo for installing emerald themes. "Installing" a theme basically means you extract a couple of pictures, containing the button images, and a text file containing a configuration for every available option into a folder located in your home directory.

~/.emerald

So, if you sudo install it, then root owns files in your home directory what you should avoid. Don't let things get messed up by appending too many sudo.
Bear in mind what sudo means:
Superuser do

So, what you do as superuser affects every &HOME directory user, which is has to be for applications, but should strictly be avoided when installing themes or icons.
There is not only one place where you may install themes and icons.
I'd recommend installing them into your &HOME dir. Nearly every configurable installed application creates a hidden folder in your home dir, which contains configurations. So if you want to install a pkg of icons you might instead of installing them with sudo simply extract the tarball to ~/.icons/icon-pkg-name

Then you should as well be able to instantly acces them with your application choser.

You need the sudo cmd very rarely actually, using it for the wrong actions has consequences to file access permissions. So, for example, if you delete a file as root from your home directory, it is gone anyway. But if you edit a configuration file for example as root and save it, it is not longer yours, and you might end with a: Permission denied!

---

### Post by RandomIP on 2008-10-10
Thanks loomsen,yeah i was doing sudo apt-get install emerald, i just didn't switch back before I made the post. My problem at the moment isn't so much installing the theme, it's that it will not install emerald, using that command. Not being able to install the theme is a annoying byproduct of not being able to install emerald.

---

### Post by loomsen on 2008-10-10
Funny, just downloaded an icon theme from that site yesterday.

Anyway, obviously we should start some serioz version posting :)

Where have you installed Compiz from? Did you add repos manually or did you just take the ones shipped with your distro?

Compiz, however, is a plugin-based-application. This basically means it is written and provided by a whole lot of people.
For such programs, as well as dock-bars for example, I always try to make sure I have an appropriate repository in my list, which ships the latest possible versions, tho I'm not interested in developing.
I expect them to simply do the work, I can live with some glitches here n there -- like the free transformable windows plugin... this plugin is so incredibly awesome, that I'm pleased with waiting for bugfixes for the moment. 

Anyway, as there is no constant developement, and some plugins are under heavy developement while other just get forgotten, I'd recommend adding a solid repo to your sources.list and then updating the whole stuff, which often solves a lot of problems.

But for the moment, please just take a look which compiz version you actually have installed, and if there is an emerald package provided through synaptic at all.

If you prefer the comand line:
```

me@my-laptop:~$ apt-cache pkgnames emerald
emerald-themes
emerald
me@my-laptop:~$ 

```

If you don't get any output, it's time for some bleeding repository edge :P :)

---

### Post by RandomIP on 2008-10-10
Problem Resolved, Thanks Loomsen

---

