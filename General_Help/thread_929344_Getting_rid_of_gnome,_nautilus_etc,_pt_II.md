---
title: "Getting rid of gnome, nautilus etc, pt II"
date: 2008-09-24
forum: General Help
---

### Post by loomsen on 2008-09-24
Hello.

As I got some private messages concerning my Desktop and how to achieve it, I decided to start this thread instead of offtopic'in the sticky to death.

OK, I'll try and keep this one as short as possible, I think most of the important steps I mentioned in my other post. Tho I switched to debian unstable I think I'll be able to remember some steps...

First of all, be sure that the gnome-panel as it is became obsolete for your purpose.

However, I'd suggest a launcher like gnome-do or similar, just in case you will find yourself watching a pointer on a desktop without any panel, right-klick options or any way to fix your situation except dropping to a terminal and trying and fixing it there (tho I love the terminal, sometimes it's just more comfortable hitting Super+Space and typing gnome-panel to have a menu, systray and so on)

Alright, 

sudo apt-get gnome-do gnome-do-plugins

should install this little lifeline. In earlier versions gnome-do used to have a little bug forcing you to log-out and back in before being able to configure it to start at login. So I recommend you do so.

Back in, and as my eyes surprisingly just get to see, I think there's a somewhat more elegant solution to nautilus/gnome-panel-concerns.

Open up your preferred terminal and type 
```

gconf-editor

```
I assume nautilus has already been disabled by now.

In the opening gconf-editor navigate to 
Desktop-->gnome-->backgrounds 
and uncheck draw background to prevent gnome from drawing a desktop too (compiz usually works even if gnome draws a background, but I just don't like it dirty :) )
Alright, now uncheck draw background.

Navigate to 
Desktop --> session --> required_components

As you see, gnome asks for a filemanager, a window manager as well as a panel to be able to run a session.

By default the values here should be nautilus(fm), metacity(wm) and gnome-panel as your panel.

You may edit this values to your preferences, I replaced all three of those Sumo-Wrestlers amongst the fly-weight apps, up to you.
Anyway, to get rid of your gnome-panel replace it with a dock of your choice.
My Key looks like this:
[[img]http://www.ubuntu-pics.de/thumb/3646/screenshot_01_m6ey67.png[/img]](http://www.ubuntu-pics.de/bild/3646/screenshot_01_m6ey67.png)

What I did too, which tho isn't really necessary, I backed up my gnome-panel binary in /usr/bin with (as root)
```
 
cp /usr/bin/gnome-panel /usr/bin/gnome-panel.bak && rm /usr/bin/gnome-panel && ln -s /usr/bin/kiba-dock /usr/bin/gnome-panel

```

This way you will have your kiba-dock run at startup, pretending it was actually the gnome-panel :)

--- If you prefer not to have X running while configuring, why so ever, you may also edit the files by hand:
```

Ctrl + Alt + F2 
```in running gnome to drop to a terminal
login, then do
```
/etc/init.d/gdm stop     ## to stop gnome display manager, when prompted OK do:
sudo nano ~/.gconf/desktop/gnome/session/required_components/%gconf.xml

```
respectively
```

sudo nano ~/.gconf/desktop/gnome/background/%gconf.xml
```

and replace the panel/file-manager/window-manager binaries with the ones of your choice, resptectively replace the option <true> in the second file, which should be the end of the 3rd line if you didnt edit it yet, with <false> to prevent gnome from drawing a background.
Save and close both files with Ctrl+X, then type 
```

startx

```


Actually I dont know what else I could have forgotten to mention, feel free to use this post tho for questions (rather than writing pms, please).

Just give it a try, ain't too hard actually.

Another program which I find very useful in times of extreme customizing ( :D ) is backstep, which will make icons of minimized windows on your desktop.
```

sudo apt-get install backstep

```
and simply typing 
backstep
into a terminal after finishing the installation should do the trick.
From now on minimized windows will be transformed to icons (not 2 shiny ones tho) on your desktop. As I said, I usually use it while customizing and editing files over and over again. Allright, feel free asking questions if you got some, fell free to give 
Cairo-Dock
a try too, it is actually worth it too, I just like Kiba more, even if Cairo is a little more configurable than kiba. But I hope the akamaru physics engine will be implemented back into kiba soon. You can run both if you like, my kiba is pretty lightweight, tho I got three separate docks.

I'll add my configuration files to this post (extract the archive to ~/.kiba-dock/ )

Alright, l8rs all

---

### Post by HippyRandall on 2008-09-25
as soon as I get some time I plan on trying this. I recall trying to insall kiba-dock before and running into problems for one reason or another so I may try out cairo instead. 

Thanks loomsen

Hippy

---

### Post by sloggerkhan on 2008-09-25
Can you link back to your 1st post that this makes reference to? It sounds like it might have a lot of useful info.
I have been trying to customize an acer aspire one with ubuntu to have a lighter interface with a few of the really needed conveniences like network manager applet and have been getting nowhere because of annoying dependancy problems and few other issues.

---

### Post by loomsen on 2008-09-25
Sure, I forgot, pardon.

[http://ubuntuforums.org/showpost.php?p=5691394&postcount=39](http://ubuntuforums.org/showpost.php?p=5691394&postcount=39)

Well then, lets get it goin hippy :)

---

### Post by HippyRandall on 2008-09-25
can't do it :mad::frown:](*,)

after hours of messing about with cairo dock and that blasted kiba-dock I managed to screw up my setup enough that I want to wipe the drive and start over. I managed to get rid of nautilus drawing the desktop which seemed to make everything a fair bit more responsive. stalonetray only wanted to give me more headaches on top of the one from cairo-dock and the migraine from kiba-dock so I gave up on that as well. Think I might move some files to my /files partition and just hose out the whole machine. oh well. still better than using the Vista bloatware that cam preinstalled on this puter :)

Hippy

---

### Post by loomsen on 2008-09-26
> 
 stalonetray only wanted to give me more headaches on top of the one from cairo-dock and the migraine from kiba-dock so I gave up on that as well.


Indeed. stalone survived about 3-4hrs on my laptop.

But, what actually really surprises me, I'm reading over and over again from people having trouble with kiba.

So I made some debs, all plugins (gaim, plugins-main, dbus) except ephany or so, didnt need that. Tbh, I dont even know what it is ^^

Anyway, I compiled them with debian unstable, but I think it should work for all 64bit debian distros, I just installed them on Intrepid without any problems.

Grab em here:  [ kiba-dock-all_amd64 ](http://rapidshare.com/files/148521183/kiba-dock-all_amd64.tar.bz2.html)

Sry for rapidshare, but after I had this post nearly finished twice, just to get to know that 1.2Mb are to much to upload, I chose the easiest way ^^

Let me know if you encounter problems while installing, tho I cannot imagine y someone should.

enjoy

---

### Post by HippyRandall on 2008-09-26
well that was very courteous of you! unfortunately I am not running 64bit :( time for a new install of Ubuntu perhaps.

Hippy

---

### Post by HippyRandall on 2008-09-27
Well after a few MORE hours I have gotten rid of any trace of a 32bit OS and installed Ubu 64bit. Which, means that I now have kiba-dock running thanks your debs :) but the physics isn't working :( I think that after all the issues I had trying to get rid of nautilus I am just going to stick with it for now.

Hippy

---

### Post by loomsen on 2008-09-27
The physics is actually not implemented. The dev wants to recode it, so it will take some time till it gets back in.

Glad the debs worked for you :)

---

### Post by HippyRandall on 2008-09-27
> **loomsen said:**
> Hello.
I'll add my configuration files to this post (extract the archive to ~/.kiba-dock/ )

Alright, l8rs all
just when I thought I had this thing licked...only the left hand bar is working for me. some sort of bar *attempts* to load in the middle. gonna delete all the xml files in the config folder and just unzip only yours in it. I'll let you know...](*,)

Hippy

PS the gmenu does not work. crashes the dock if I click on it. man this thing needs ALOT of work

---

### Post by HippyRandall on 2008-09-27
I really can't figure out why your "tray" in the middle looks like the other docks and mine looks like...well...crap!

---

### Post by kaivalagi on 2008-09-27
Loomsen

What music player are you using, what's the GUI in your screenshot? mpd with a client or something?

---

### Post by loomsen on 2008-09-27
Hey Guys.

The systemtray is actually pretty hard to handle. Took quite some time to figure out how I shall do it. The background color of your system tray is is set by your system theme. I use xfce-dusk, you can get it with 

apt-get install gtk2-xfce-engines

Or you may reconfigure your dock to make it look better with your current theme. But the background is set by your system theme, change the borders color to black and the gradients color to white will make it look quite nice as well... Thats what I used to do before when I had a bright theme. 

@kaivalagi

I'm using gmusicbrowser. I like it, it's very high configurable and under quite promising developement.

Greets

---

### Post by HippyRandall on 2008-10-01
Ok I got it working...mostly.
> **loomsen said:**
> 
Navigate to 
Desktop --> session --> required_components

As you see, gnome asks for a filemanager, a window manager as well as a panel to be able to run a session.

By default the values here should be nautilus(fm), metacity(wm) and gnome-panel as your panel.

You may edit this values to your preferences, I replaced all three of those Sumo-Wrestlers amongst the fly-weight apps, up to you.
Anyway, to get rid of your gnome-panel replace it with a dock of your choice.


__Odd that I didn't have these options for file manager and window manager. I even tried using 'sudo gconf-editor' in case some options were only available to root user.

> **loomsen said:**
> 
What I did too, which tho isn't really necessary, I backed up my gnome-panel binary in /usr/bin with (as root)
```
 
cp /usr/bin/gnome-panel /usr/bin/gnome-panel.bak && rm /usr/bin/gnome-panel && ln -s /usr/bin/kiba-dock /usr/bin/gnome-panel

```This way you will have your kiba-dock run at startup, pretending it was actually the gnome-panel :) 
Kiba has been starting up for me just fine whenever I log in; it's compiz that is giving me the troubles. I have compiz set to start up on log in but I always have to right click on the icon in the tray and restart the window manager. Kind of annoying.
Oh, I made a slight change to my conky. I have it set as:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_colour black
own_window_hints undecorated  #,sticky,below,skip_taskbar,skip_pager
own_window_type normal
```
It looks great on the first desktop but holds the wallpaper from that desktop in it's cache or whatever when I switch to another desktop. I tried out the opacity settings you talked about in CCSM but found that I liked it better transparent even if it has that wallpaper bug.

At any rate, thanks for the tut. 
Hippy

---

### Post by HippyRandall on 2008-10-02
forgot to include a screenshot so here it is now

---

### Post by loomsen on 2008-10-05
Looks very nice after all :)

Glad it was helpful.

---

### Post by HippyRandall on 2008-10-06
well....
it used to look nice. Then I went and followed a tutorial that claimed to speed up your system and in the end all it did was hose my system and I ended up with no option but to reinstall. I still have the debs from your post but have not decided if I am going to go back into all the "tweaking" again. Seems every time I muck about too much I end up with a broken system. :(

---

### Post by loomsen on 2008-10-10
Alright, here we go Carney :)

Emerald theme and icons included.

My GtK theme is called: xfce-dusk
and should be included in the xfce-gtk-engines package provided by Synaptic.

Feel free to ask if I forgot anything left unsaid :)

enjoy

*edit*

I had to source the upload out due to filesize restrictions on this board.

You can grab it here: [DOWNLOAD](http://uploaded.to/?id=suosye)

---

### Post by HippyRandall on 2008-10-12
Completed my setup with compiz rendering the desktop instead of nautilus. I also reinstalled kiba dock and have that "mostly" to my liking other than I want to switch all the icons on the left bar over to the right bar.
As you can see from the SS I have the sphere deformation in compiz set up with 4 desktops and the a different shot of the earth on each. The cube caps are then shots of the poles.
The skydome is a shot of the Milky Way.

I will update this posting with the links to things i have used in my setup as soon as I get a chance.

Hope you like,
Hippy

---

### Post by HippyRandall on 2008-10-13
need some help.
I somehow managed to screw up my session management or something. When I log in using the default login session I get compiz and all it's effects but I do not get kiba and therefor cannot do anything. Alt+f2 do not work, Super+space do not bring up Gnome-Do. I am running under the failsafe session right now.
Any ideas on what I need to delete or reset in my home folder?

---

### Post by loomsen on 2008-10-13
Nice setup! I like it.

For the autostart... You could edit a textfile with something like this in it:
```


[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=No Name
Name[en_US]=kiba-dock
Exec=kiba-dock
X-GNOME-Autostart-enabled=true
Comment[en_US]=

```

Name it 
kiba-dock.desktop
and place it in ~/.config/autostart

I'm running Intrepid, so I don't know if this folder exists in hardy. But as far as I remember for hardy there's a file called 
~/.gnome2/session
where all startup applications are written to. Either, if kiba is still in it, you could move it to the bottom of it, so that kiba will startup last.
Or, just add kiba to the end of the file. For example:
```

[Default]
0,Program=gnome-power-manager
1,Priority=40
1,RestartCommand=emerald --replace 
2,RestartCommand=pactl load-module module-x11-xsmp
num_clients=3

```

you would change to:
```

0,Program=gnome-power-manager
1,Priority=40
1,RestartCommand=emerald --replace 
2,RestartCommand=pactl load-module module-x11-xsmp
**3.RestartCommand=kiba-dock**
num_clients=**4**

```

That should work I think... For instance, add another entry for gnome-do if it doesn't look up. Did you set the key-binding for it to super+space and enable the autostart in the preferences?

---

### Post by HippyRandall on 2008-10-16
Kind of got things sorted out now. The entries for kiba, gnome-do, and compiz were already in the sessions file so I am not sure why it wasn't working. I did a dist upgrade to Ibex and have been having all kinds of other issues. Once it is out of beta I am going to have do a clean install, too many things are not working properly for me, ie evolution is gone, firefox toolbars are messed up, update manager doesn't work properly,........etc etc etc. Not a complaint though, I know it's a beta and the way that I upgraded is not recommended.

Hip

---

### Post by loomsen on 2008-10-16
Yeah, upgrading shouldn't be done with betas. So you'd prlly better have chosen to clean install to another partition to give it a try, and upgrading in two weeks when its released. 

I switched my repository server earlier, and instantly got surprised by broken dependencies - figuring out showed that one repo provided the two packages: linux-2.6.27-9 and linux-headers-2.6.27-9
and the new repo I added provided basically the same, but anyhow they were called: linux-generic-2.6.27-9 and linux-headers-generic-2.6.27-9

Beta styles, same pkgs, different appendix, broken dependencies. I added my old repo again and everything worked fine.

---

### Post by loomsen on 2008-10-19
[QUOTE=naknak987]In the gconf-editor I don't have any session or required components. I was trying to fallow your tut [here]("http://ubuntuforums.org/showthread.php?t=929344") Didn't have any trouble till that part. Will you help?[/QUOTE]

I wrote it when I just had a fresh install of Intrepid alpha, so this is new in Intrepid... When I wrote it I thought it was just a key I must have missed.

Anyway, it's optional in the end. So you don't need to set it. Just continue, oh, well, if you already came so far, you should be pretty much done ^^

As I said, it's just an option which is nice to use cause you won't have to mess around to much this way. But it's not mandatory.


I think I'll post into the thread tho... Don't wanna close the source I profit so much from :)

---

