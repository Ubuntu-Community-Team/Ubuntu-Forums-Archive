---
title: "cairo-dock-plug-ins not in repository?"
date: 2008-11-15
forum: General Help
---

### Post by andrewabc on 2008-11-15
I installed cairo, and I see that I should install cairo plugins as well for full functionality. But when I search synaptic for cairo-dock-plug-ins there is none listed. Even when I search fro cairo not listed.

Was plugins removed from synaptic? Anywhere else I read it says it should be in repository.

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

EDIT:
So I have to add cairo repository in order to get plugins? So ubuntu only provides cairo app, and users have to add another repository for cairo plugins? I presume the cairo repository has the latest cairo app as well? Does this add stability issues?

EDIT:
I added cario repository and it shows an update for cairo-dock and is also installing cairo-dock-plug-ins
Is cairo plugins not used in official repository because it is 15mb?

When installing I got an error
> E: /var/cache/apt/archives/cairo-dock_1.6.3.1_all.deb: trying to overwrite `/usr/share/cairo-dock/icon-mouse.png', which is also in package cairo-dock-data

So new version of cairo-dock didn't install, and now cairo-dock wont start.

So the advice given on the ubuntu website link in this post is incorrect?

Looks like a different bug as shown [here](https://bugs.launchpad.net/ubuntu/+source/cairo-dock/+bug/289484). As it seems that they have cairo-dock-plug-ins in default repository?

EDIT:
According to [here](https://bugs.launchpad.net/ubuntu/+bug/248826) someone said they'd package plugins back in July. Looks like it never happened?

---

### Post by ziptnf on 2008-11-16
I am experiencing the exact same problem.  Cairo-dock will not install.

> E: /var/cache/apt/archives/cairo-dock_1.6.3.1_all.deb: trying to overwrite `/usr/share/cairo-dock/icon-mouse.png', which is also in package cairo-dock-data


Any solutions/ideas?

---

### Post by loomsen on 2008-11-16
No bug, just some usual mess-up.

Package plugins from the repos is called cairo-dock-data whereas the svn provides cairo-dock-plugins.

1.6.3.1 --> SVN, pkgnames: cairo-dock cairo-dock-plugins cairo-dock-themes
1.6.2.3 --> Synaptic, pkgnames: cairo-dock cairo-dock-data cairo-dock-dev

Chose one.

---

### Post by andrewabc on 2008-11-16
> **loomsen said:**
> No bug, just some usual mess-up.

Package plugins from the repos is called cairo-dock-data whereas the svn provides cairo-dock-plugins.

1.6.3.1 --> SVN, pkgnames: cairo-dock cairo-dock-plugins cairo-dock-themes
1.6.2.3 --> Synaptic, pkgnames: cairo-dock cairo-dock-data cairo-dock-dev

Chose one.

That post makes it even more confusing.

I have added cairo repository, and I do not see cairo-dock-themes in synaptic.

I attempt to remove cairo-dock-data and it gives an error. So cairo-dock is still using old version, and cairo-dock-data is still installed.

If I want to install cairo-dock-dev it wants to install about 30 more packages. But I am past that and have cairo repository installed, but it wont install update.

I have no idea what I am supposed to choose since nothing works.

From ubuntu repository, cairo-dock, cairo-data ->cairo works, but no plugins possible.
I try using cairo repository, and it wont upgrade cairo-dock, and wont uninstal cairo-data. Cairo-dock-plug-ins does install, but useless since cairo doesn't work.

!?

---

### Post by loomsen on 2008-11-16
Well, chosing one does actually implicit delete the other one.

Step by step, do this

1) Download the pkges from berlios cairo repo, these:

[Cairo-dock](http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.6.3.1_i686.deb)

[Plug-ins](http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.6.3.1_i686.deb)

[Themes](http://prdownload.berlios.de/cairo-dock/cairo-dock-themes-1.6.3.1.tar.bz2)

Copy/download them to ~/
Don't worry, you will remove them after installation, but first get rid of your old one.

Open up a terminal, and run
```

sudo apt-get remove cairo-dock cairo-dock-data
```

Now lets install the new ones, run:
```

sudo dpkg -i cairo-dock_v1.6.3.1_i686.deb cairo-dock-plug-ins_v1.6.3.1_i686.deb
```

When done, extract the theme package to a working directory, for ease of use, take the directory you downloaded them to, /home/<you>
```

tar -xf cairo-dock-themes-1.6.3.1 && cd cairo-dock-themes-1.6.3.1
```

Now, again for ease of use, you probably might want to run the provided install script - or configure it further.

But I think you should be fine just running it with default values, which is cairo themes being installed to /usr/share/cairo-dock/themes.
So, you'd do:
```

./install.sh -t /usr/share/cairo-dock/themes
```

Then start cairo with 
```
cairo-dock &
```

or Alt+F2 cairo-dock or sth, and enjoy the ride :)


*edit*

Cleaning up:
```

cd ~ && rm cairo-dock_v1.6.3.1_i686.deb cairo-dock-plug-ins_v1.6.3.1_i686.deb cairo-dock-themes-1.6.3.1.tar.bz2 && rm -rf cairo-dock-themes-1.6.3.1/
```

*done*

---

### Post by ellalan on 2008-11-17
> **andrewabc said:**
> That post makes it even more confusing.

I have added cairo repository, and I do not see cairo-dock-themes in synaptic.

I attempt to remove cairo-dock-data and it gives an error. So cairo-dock is still using old version, and cairo-dock-data is still installed.

If I want to install cairo-dock-dev it wants to install about 30 more packages. But I am past that and have cairo repository installed, but it wont install update.

I have no idea what I am supposed to choose since nothing works.

From ubuntu repository, cairo-dock, cairo-data ->cairo works, but no plugins possible.
I try using cairo repository, and it wont upgrade cairo-dock, and wont uninstal cairo-data. Cairo-dock-plug-ins does install, but useless since cairo doesn't work.

!?

Just install in few steps by following the method in this page:
[http://www.cairo-dock.org/ww_page.php?p=Par%20d%C3%A9p%C3%B4t&lang=fr#0-Ubuntu](http://www.cairo-dock.org/ww_page.php?p=Par%20d%C3%A9p%C3%B4t&lang=fr#0-Ubuntu).

---

### Post by JuL.LeVi on 2008-11-17
yeah, just follow the method in the homepage of CAiro-dock, Everything went smoothly

I'm enjoying cairo dock with news features :guitar:

---

### Post by andrewabc on 2008-11-17
Thank you for the help!
Going to [cairo dock website ubuntu install](http://www.cairo-dock.org/ww_page.php?p=Par%20d%C3%A9p%C3%B4t&lang=fr#0-Ubuntu)
worked.

What I had to do was
sudo apt-get remove cairo-dock* --purge
sudo apt-get install cairo-dock

and now everything works. I already had the cairo repository enabled.

---

### Post by andrewabc on 2008-11-17
A question I have now is that there is no way for me to change the "view"
I go to configure cairo dock (advanced mode), go to views tab.
It now has main dock and sub dock. The only option I can select is blank and default. I can go to preferences and it lists 7 views (inclinated plane, caroussel, parabolic, rianbow, slide, simpleslide, curve) and options for each.

But there is no way to select any of these views. I click ok and it stays as blank or default (they are the only two available in drop down box). How do I change my views?

EDIT:
Even following [this](http://taufanlubis.wordpress.com/2008/06/22/cairo-dock-configuration/) it shows it in easy mode, and the person is able to select different views from dropdown list. But for me only a blank and default are available to choose.

Here's a screenshot of mine:
[[IMG]http://img511.imageshack.us/img511/5601/screenshotconfigurationor2.th.png[/IMG]](http://img511.imageshack.us/my.php?image=screenshotconfigurationor2.png)[[IMG]http://img511.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by ellalan on 2008-11-19
> **andrewabc said:**
> A question I have now is that there is no way for me to change the "view"
I go to configure cairo dock (advanced mode), go to views tab.
It now has main dock and sub dock. The only option I can select is blank and default. I can go to preferences and it lists 7 views (inclinated plane, caroussel, parabolic, rianbow, slide, simpleslide, curve) and options for each.

But there is no way to select any of these views. I click ok and it stays as blank or default (they are the only two available in drop down box). How do I change my views?

EDIT:
Even following [this](http://taufanlubis.wordpress.com/2008/06/22/cairo-dock-configuration/) it shows it in easy mode, and the person is able to select different views from dropdown list. But for me only a blank and default are available to choose.




Here's a screenshot of mine:
[[IMG]http://img511.imageshack.us/img511/5601/screenshotconfigurationor2.th.png[/IMG]](http://img511.imageshack.us/my.php?image=screenshotconfigurationor2.png)[[IMG]http://img511.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

I do have the same problem and I hope developers will rectify it in the near future.

---

### Post by JuL.LeVi on 2008-11-19
[B]HI Ellalan and Andrewabc,

Your cairo-dock's version now is 1.6.2.3 ( I guess that you guys installed it with synaptic manager , right? ) . Because this version ( or maybe older version also ) doesn't work smoothly with Ubuntu 8.10 anymore ).

There is a new version 1.6.3.1 in the homepage of cairo-dock . just follow the method there step by step and you'll get a smooth-working cairo dock

```
http://www.cairo-dock.org/
```

[COLOR="Red"]JuL[/COLOR][/B]

---

### Post by andrewabc on 2008-11-19
Nope. I am using
version 1.6.3.1
I have cairo dock repository enabled (which is listed on website).
So this is a problem with latest version as well.

I tried ubuntus version, but that doesn't work with plugins, so I had to switch to cairo dock repository to enable plugins.

---

### Post by ellalan on 2008-11-19
> **andrewabc said:**
> Nope. I am using
version 1.6.3.1
I have cairo dock repository enabled (which is listed on website).
So this is a problem with latest version as well.

I tried ubuntus version, but that doesn't work with plugins, so I had to switch to cairo dock repository to enable plugins.
I think I have found a solution,this is what I did:
First I had to select a Theme--- Right click the dock ->cairo-dock->Manage themes.
Then selected a Theme from the dropdown menu. 
Then I was able to change the view of Main dock.
HTH.

---

### Post by andrewabc on 2008-11-19
> **ellalan said:**
> I think I have found a solution,this is what I did:
First I had to select a Theme--- Right click the dock ->cairo-dock->Manage themes.
Then selected a Theme from the dropdown menu. 
Then I was able to change the view of Main dock.
HTH.

Thanks. I would be nice to know that it has to download the themes. I thought it had froze when I told it to use a theme.

I tried several themes, but still no way to change views. Different themes seem to use different views, as one theme will have the blank view selected, and another will have default selected, or a combo.

---

### Post by ellalan on 2008-11-19
Hi Andrew,
You don't need to download any themes, you can select from the dropdown menu, after slecting a theme(Aero in my case) you can go to Cairo-dock to configure and select View and choose whatever you want from the dropdown menu again(3D plane and Rainbow).

---

### Post by andrewabc on 2008-11-19
> **ellalan said:**
> Hi Andrew,
You don't need to download any themes, you can select from the dropdown menu, after slecting a theme(Aero in my case) you can go to Cairo-dock to configure and select View and choose whatever you want from the dropdown menu again(3D plane and Rainbow).

Yes, that is exactly what I do.
When I select a theme, it has to download the theme. I see my internet connection downloading around 200kb-1mb of data to show the theme (once done it then applies the theme). It even has to download data to simply show a preview of the theme.

Maybe this is a problem?

---

### Post by ellalan on 2008-11-19
> **andrewabc said:**
> Yes, that is exactly what I do.
When I select a theme, it has to download the theme. I see my internet connection downloading around 200kb-1mb of data to show the theme (once done it then applies the theme). It even has to download data to simply show a preview of the theme.

Maybe this is a problem?
I am bit lost here, I hope someone will come up with a better solution. Sorry mate.

---

### Post by andrewabc on 2008-11-20
I just noticed in Cario options
applets->add functionalities (spelt wrong) to your dock
There is one called "rendering" which says it allows for different views.

Does this need to be enabled to get different views? I enabled it but still no new views.

EDIT:
Yes enable this plugin. Then restart computer and the "views" will become available

---

