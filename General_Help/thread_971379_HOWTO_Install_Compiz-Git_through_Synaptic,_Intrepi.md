---
title: "HOWTO Install Compiz-Git through Synaptic, Intrepid"
date: 2008-11-04
forum: General Help
---

### Post by loomsen on 2008-11-04
I'm basically just reassembling 
[this thread before it will die, hence it's got some quite usefull information](http://ubuntuforums.org/showthread.php?t=966030)

If you don't know what git is, this probably isn't for you.
If you prefer your OS to be ultrastable and reliable, this probably isn't for you neither.
If you're a bug:
[img]http://www.thinkgeek.com/images/products/front/lg-go-away-tshirt.jpg[/img]

Everybody else, here we go.

We're going to add shames git-repository, probably one of the best maintained to our sources list. Then we're going to remove our compiz shipped with intrepid completely. Finally we're going to pull compiz from git easily through synaptic.

1. Drastically improving compiz through protobuf:
```

sudo apt-get install libprotobuf0 libprotobuf-dev libprotobuf-java protobuf-compiler python-protobuf
```

[Info about protobuf](http://dev.compiz-fusion.org/~cornelius/2008/10/19/startup-time-improvements-part-1/)

And hence protobuf is enabled by default, we've got nothing else to do in this section.

Note: the protobuf extension will probably cause heavy tearing and loads after initial setup, as it's building the cache then. Stay logged in for like 5-10 minutes, log out and back in, and feel the difference :)
But that l8r.

2. Now we've got to remove our old compiz installation completely, otherwise we'll get some broken dependency messages and our update notifier going nuts for this last update he isn't able to install.

In the thread above is shown what you can do if you're already facing that problem, here we're going to do it right.

So, for now, as we're going to purge everything right away, you should have thought about doing a backup yourself already. To export your profile, go to ccsm -> preferences and hit export profile :) name and place it foo.bar-whatever and place it to your prefered backup location.

Now you should change your window decorator if you've got emerald or compiz running.
```
metacity --replace
```

Now search synaptic for compiz, but don't take the quick search as it will maybe not show everything we want. Mark all installed packages now for complete removal. Sort them by status, and then mark every package you see, rightclick, mark for complete removal.
[[img]http://www.ubuntu-pics.de/thumb/5213/screenshot_63_2a7cHi.png[/img]](http://www.ubuntu-pics.de/bild/5213/screenshot_63_2a7cHi.png)

You may omit cairo-clock if you like :)screenlets, awn and sim-dock as well if you have any of them installed. Everything else should be removed.


3. Add shames repo to your list:
I assume you have intrepid, then do this for instance (after closing synaptic for one moment)
```

sudo -i
echo 'deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./' >> /etc/apt/sources.list.d/custom.list
apt-get update
wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
[color=red]exit[/color]

```

Alright, sources set up, now lets get this working, bring synaptic back up, and...

---

### Post by loomsen on 2008-11-04
4. Chose to install everything, hit cancel when you're prompted about broken dependencies, and keep going till it looks like this:

4 Packages left, which couldn't and can't be installed :confused:

Let's have a look at this:
[[img]http://img47.imageshack.us/img47/1798/screenshot10pg0.th.png[/img]](http://img47.imageshack.us/img47/1798/screenshot10pg0.png)[[img]http://img378.imageshack.us/img378/5927/screenshot11xu2.th.png[/img]](http://img378.imageshack.us/img378/5927/screenshot11xu2.png)
[[img]http://img137.imageshack.us/img137/2194/screenshot12xq0.th.png[/img]](http://img137.imageshack.us/img137/2194/screenshot12xq0.png)[[img]http://img99.imageshack.us/img99/8126/screenshot13hi6.th.png[/img]](http://img99.imageshack.us/img99/8126/screenshot13hi6.png)

And, as you see, 4 METAPACKAGES left. Descriptions can be pretty descriptive here n there ;)

So, basically, nothing left than 4 README&DEPENDONMEs 
And don't forget to add the packages from the universe repo:

[[img]http://img113.imageshack.us/img113/3207/screenshot14go1.th.png[/img]](http://img113.imageshack.us/img113/3207/screenshot14go1.png)[[img]http://img113.imageshack.us/img113/9234/screenshot15xb7.th.png[/img]](http://img113.imageshack.us/img113/9234/screenshot15xb7.png)

If you're now thinkin how in hell can I have compiz if synaptic keeps telling me compiz-gnome is not installable, 
[then you probably may want to read some info about metapackages](https://help.ubuntu.com/community/MetaPackages)


Mission: accomplished



-> Notes: 
- If you're having any kind of trouble doing this and keep being told you have broken dependencies, check the other thread again.
- Please no I can't get compiz to work tho I got a job, what do I do wrong questions here. There are more apropriate places for that.
- If none of the above applies to you, and you still have got a question, check  [ again if I really didn't provide a solution](http://ubuntuforums.org/showthread.php?t=966030), cause I most likely have.


Still?
- OK, ask.


Hint: You are now able to add different repositories for git-compiz to your list as well. They should live together in symbiosys, tho I recommend you know what you're doing... Else stick to these repos, they are usually the newest and most complete ones.

[SHAMES REPO](http://shame.tuxfamily.org/repo/?cat=11)


[color=green]REMINDER - You still know about that note on protobuf I made at the beginning?[/color]

---

### Post by ellalan on 2008-11-05
Thanx loomsen for this excellent post and IMHO it should be in the Tutorial section for the way you have presented.

---

### Post by loomsen on 2008-11-05
:)

---

### Post by kilou on 2008-11-17
Excellent tutorial and I got everything working...almost....just missing the window borders and I couldn't find anything related in the other thread. The window decoration plugin is marked in ccsm but it's looking for /usr/bin/compiz-decorator. If I run compiz-decorator in the terminal I get:

"The program 'compiz-decorator' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
bash: compiz-decorator: command not found"

However checking in synaptic compiz-core is really installed from git sources...

Does it mean git-compiz only work with emerald?

If I use /usr/bin/emerald as command in the window decoration plugin then it works with emerald.....but I'd rather use the gtk decorator coz I use a modified Dust theme. Any solution to that little problem?

Thanks

---

### Post by loomsen on 2008-11-17
Thanks.

Well, compiz default window decorator, or lets say the one adding some wobbling sugar to your windows is emerald.
You may as well use any other window decorator, metacity --replace for instance.

If you want to use metacity specify it in CCSM-->window decorator--> command 
metacity

Or you may as well chose metacity in your gconf:

```
gconf-editor
```

search for the key desktop-->gnome-->session-->required components
and adjust it to your preferences.

[[img]http://www.ubuntu-pics.de/thumb/5756/screenshot_94_D7odW3.png[/img]](http://www.ubuntu-pics.de/bild/5756/screenshot_94_D7odW3.png)

Oh wait, read your post again.

I think you're messing some things up here, emerald draws your Window BORDERS only.

So, emerald takes care of a frame around every window, of a titlebar and common window controls, like shade, minimizing and so on. Further it provides the possibility to resize your windows. 

> Dust theme
This, if I got you right, is actually the engine creating the look of your inner window, so if the background is black or brown or blue or so.

[[img]http://www.ubuntu-pics.de/thumb/5757/screenshot_96_pSsWB9.png[/img]](http://www.ubuntu-pics.de/bild/5757/screenshot_96_pSsWB9.png)[[img]http://www.ubuntu-pics.de/thumb/5758/screenshot_97_mkQNve.png[/img]](http://www.ubuntu-pics.de/bild/5758/screenshot_97_mkQNve.png)

See? same window frame, different engines.

[[img]http://www.ubuntu-pics.de/thumb/5759/screenshot_98_3sROoQ.png[/img]](http://www.ubuntu-pics.de/bild/5759/screenshot_98_3sROoQ.png)

Themes, which actually consist of a window decorator, a window manager, an icon set and a cursor theme, are basically just reassembled icon/engine/decorator/(cursor) themes melt together.

---

### Post by binbash on 2008-11-17
I tried this 3-4 times.

4-Chose to install everything, hit cancel when you're prompted about broken dependencies, and keep going till it looks like this:

If you choose this, synaptic tries to install compiz-kde, you can't select install compiz without this, also you cant select compiz-gnome as you mentioned.

Did you try this with gnome?

---

### Post by kilou on 2008-11-17
> **binbash said:**
> I tried this 3-4 times.

4-Chose to install everything, hit cancel when you're prompted about broken dependencies, and keep going till it looks like this:

If you choose this, synaptic tries to install compiz-kde, you can't select install compiz without this, also you cant select compiz-gnome as you mentioned.

Did you try this with gnome?

I have gnome and it works for me (Ubuntu 8.10). I didn't have any broken dependecies message either. Actually I selected exactly the packages on the screenshots without selecting those that couldn't be installed. Installation went smoothly with that.

---

### Post by loomsen on 2008-11-17
> **binbash said:**
> I tried this 3-4 times.

4-Chose to install everything, hit cancel when you're prompted about broken dependencies, and keep going till it looks like this:

If you choose this, synaptic tries to install compiz-kde, you can't select install compiz without this, also you cant select compiz-gnome as you mentioned.

Did you try this with gnome?

How about actually reading my howto? This is exactly why I wrote this, jeez.

---

### Post by binbash on 2008-11-17
> **kilou said:**
> I have gnome and it works for me (Ubuntu 8.10). I didn't have any broken dependecies message either. Actually I selected exactly the packages on the screenshots without selecting those that couldn't be installed. Installation went smoothly with that.

So you are also installing compiz-kde and other kde deps?

---

### Post by kilou on 2008-11-17
> **loomsen said:**
> 
Oh wait, read your post again.

I think you're messing some things up here, emerald draws your Window BORDERS only.

So, emerald takes care of a frame around every window, of a titlebar and common window controls, like shade, minimizing and so on. Further it provides the possibility to resize your windows. 


This, if I got you right, is actually the engine creating the look of your inner window, so if the background is black or brown or blue or so.

[[img]http://www.ubuntu-pics.de/thumb/5757/screenshot_96_pSsWB9.png[/img]](http://www.ubuntu-pics.de/bild/5757/screenshot_96_pSsWB9.png)[[img]http://www.ubuntu-pics.de/thumb/5758/screenshot_97_mkQNve.png[/img]](http://www.ubuntu-pics.de/bild/5758/screenshot_97_mkQNve.png)

See? same window frame, different engines.

[[img]http://www.ubuntu-pics.de/thumb/5759/screenshot_98_3sROoQ.png[/img]](http://www.ubuntu-pics.de/bild/5759/screenshot_98_3sROoQ.png)

Themes, which actually consist of a window decorator, a window manager, an icon set and a cursor theme, are basically just reassembled icon/engine/decorator/(cursor) themes melt together.

Actually the Dust theme also draw the windows borders but in GTK. When using compiz 0.7.8 that came with Intrepid, I was able to use a GTK theme (with the windows borders from the GTK theme) along with compiz effects and plugins. Now with GIT compiz 0.7.9, it seems this is no more possible. If I use metacity in the ccsm window decoration settings, it doesnt change. I have to run metacity --replace to get back to the Dust theme....but doing so obviously also disable totally compiz (no more effects/plugins etc). The same occurs if I mod the setting in gconf as you mentionned.

I can live with emerald but I just prefer the GTK version of Dust which seems much better that the emrald version. The difference between compiz stock and git compiz seems that the compiz-decorator command is no more available in the compiz-core package. That command was allowing to run a GTK theme (including window borders) along with compiz. Would be nice to have this feature back in GIT though.

Thanks for your replies!

---

### Post by kilou on 2008-11-17
> **binbash said:**
> So you are also installing compiz-kde and other kde deps?

Yes I have compiz-kde.....but not compiz-gnome (well interesting since I'm running gnome, I may be able to drop the kde part maybe). But if you have troubles, maybe just start over again and do not select the 4 packages that cannot be installed (the blank ones on the screenshots) but select the kde parts exactly as on the shots. You shouldn't get any dependency warnings (at least I didn't).

---

### Post by binbash on 2008-11-17
No i can install, i just dont want all kde libs and kde-compiz.Thanks

---

### Post by loomsen on 2008-11-17
?

Then don't install them. 1 more comment about broken packages or whatsoever without even reading one sentence, and I have to assume you're a bug, which as well could be ignored.


@ gtk-window-decorator

I didn't even take notice of this so far actually. But not 2 long, and emerald 2 might be released, maybe you'll get familiar with it then a little more :)

---

### Post by loomsen on 2008-11-17
Alright, this bothered me somehow, so a little bit of googlin, and:
> Decorators

Compiz uses small programs called decorators which draw the window borders with the usual minimize, maximize and close buttons. Compiz provides two window decorators.
gtk-window-decorator uses either a basic cairo based rendering engine or can use metacity themes.
kde-window-decorator uses native KDE themes

In addition, Emerald, Beryl's custom decorator with its own theme format, has been ported to Compiz as part of the Compiz Fusion project (see below) and is available in unofficial packages.


[From here.](http://en.wikipedia.org/wiki/Compiz)

Ok, thats a pretty weird story, seems like GTK- and gnome-window-decorator have been split years ago. Still I can't remember anything like a GTK --> window manager. GTK is usually intented to provide informations on how the windows will be drawn, but not actually draw them.

However, metacity was the only window decorator based on gtk I found, at least if we want to keep this somewhat up to date.

*edit*
chrooted into my build environment, and when trying to install compiz-gtk, this is what I got:
```

Package compiz-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-gnome compiz-plugins compiz-core

```

So looks like it has become obsolete itm.

---

### Post by kilou on 2008-11-17
Thanks for all these researches Loomsen! Actually it is pretty bad if compiz-gtk went obsolete....because I'm getting a high cpu load with emerald (laptop) and the dust theme was really looking much better with the gtk decorator. Maybe these issues will be fixed with emerald 2. It is strange however that this gtk thing went obsolete between compiz 0.7.8 and compiz 0.7.9..... It was working fine with the built-in compiz version in Intrepid. Is there any changelog file in the GIT version somewhere that would mention that the gtk decorator has been droped off in compiz-core between v0.7.8 and v0.7.9?

EDIT: or probably I just need that compiz-gnome package (which is not installable here). But why is it not installable? Should I use/add other sources to get it from?

---

### Post by loomsen on 2008-11-17
You may try if you like, I'll try l8r too.

You can do this from your homedir, assuming you do not have a dir called ~/tmp 
Open up a terminal, and copy and paste this to build a tmp dir and check out compiz source package from git:
```

 mkdir tmp && cd tmp && git clone git://anongit.compiz-fusion.org/compiz

```

Then, to build, you prlly have to run sth pretty common, like:
```

./configure && make && make install
```


But note, usually if your building and installing like this the pkg would go to /usr/local

The pkges installed through this tut are installed to /usr

So you prlly will have to append it to configure or autogen.sh.

So, maybe sth like this:
```

./autogen.sh --prefix=/usr && make && make install
```

But I don't know, I cannot guarantee this will work cause I didn't build it yet. Maybe I'll do l8r tho. Anyway, I'd suggest you chroot into some sane build environment, so you don't mess up your current filesystem if sth goes wrong.

---

### Post by el-mar01 on 2008-11-17
Can you just do step 1 by itself or do you need to do all the steps to get protobuf working ??

---

### Post by loomsen on 2008-11-17
You can install protobuf without any further steps. I don't know if it's implemented and enabled by default in other versions tho.

---

### Post by binbash on 2008-11-17
loomsen Thanks, this didnt do the trick with my ubuntu BUT i installed debian lenny on my main notebook and it is working perfect : )

---

### Post by kilou on 2008-11-17
@loomsen:

gtk windows decorator still appears to be part of compiz 0.7.9. I've been able to use it after having installed/compiled GIT with this script:

[http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=259077&p=1) (in french...)

The script automates the whole compiling and install of GIT (+awn if you want it) and gtk windows decorator works perfectly with it. It is a bit of a blackbox for me but it works nicely. Doesn't use the same sources as you provided though. So my Dust theme is back. The only drawback is that you have to compile GIT everytime you want to update it. Nothing managed throuhgh synaptics....but I can live with that :)

---

### Post by loomsen on 2008-11-17
> **kilou said:**
> @loomsen:

The only drawback is that you have to compile GIT everytime you want to update it. Nothing managed throuhgh synaptics....but I can live with that :)

Me too, I even prefer building my own pkges. But I'm building some custom installation CDs at the moment, so this way is much more stressless for me :) There are a couple of scripts out there, most of them will work. But avant? cmon :) Nah, don't like awn at all...
Compared to kiba / cairo it barely configurable, not to mention only one instance of it is possible.

But I'll give the script a try, thx buddy.

*edit*
[Here's the one I used (I like the build depencies with gnome option of the script, guess I'll use this one again)](http://georgia.ubuntuforums.org/showthread.php?p=5996157)
Plus, it will compile without gnome running, saves some time(at least it feels like ^^)

---

### Post by screaminj3sus on 2008-11-29
whats the command to completely remove compiz before installing the new version. In your guide you skip that step completely... you say now we have to completely uninstall compiz but you don't detail how to do it.

---

### Post by loomsen on 2008-11-30
Just READ my post:

[quote=me]Now search synaptic for compiz, but don't take the quick search as it will maybe not show everything we want. Mark all installed packages now for complete removal. Sort them by status, and then mark every package you see, rightclick, mark for complete removal.[/quote]

---

### Post by loomsen on 2008-12-01
Hi everyone.

Unfortunately shame's repo 
> **shame]is now on hold indefinitely[/quote]
due to
[quote=shame]issues in my personal life and poor health[/quote]

So I'd like to say thanks for all the work shame, if you read this by chance, and my wholehearted best wishes to you. Hopefully everything will take a turn for the better as soon as possible.

[quote=shame]That&#8217 said:**
>  in the near future....

[The whole story](http://shame.tuxfamily.org/repo/?p=266)

So, thx again shame, it's always been a pleasure using your repo.


Much obliged

loom.

---

### Post by Izek on 2008-12-02
Is there another repo for compiz somewhere other than shame's that sees a lot of update?

---

### Post by loomsen on 2008-12-02
Here are the repo's I still have in my custom sources.list, tho I usually just use omegas script and build the packages myself.

```

# 		shame compiz
# wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
# deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./
# 		compiz PPA
# deb http://ppa.launchpad.net/compiz/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/compiz/ubuntu intrepid main
# deb http://ppa.launchpad.net/mvo/ubuntu intrepid main

```

So I can't tell how up to date or not these are. But give em a try.

---

### Post by Izek on 2008-12-02
yeah, the compiz/ubuntu ppa has version 0.7.8 while mvo has version 0.7.7 it seems.

---

### Post by loomsen on 2008-12-02
Yeah, well, shame offered 0.7.9 for quite some time now.

However, if you want to give omegas script a try, create a dir in your prefered build location, like /usr/src or so, and get the script with
```

mkdir git-compiz && cd git-compiz
git clone git://anongit.compiz-fusion.org/users/omega/scripts
cd scripts

```

Now you might want to take a look at the git-compiz.conf file, I usually remove the headtracking plugin as it will fail to compile anyway if you don't resolve further dependencies (how to do should be written in the README)

When done I use to drop to a shell and stop gdm. 
Ctrl + Alt + F2
```

sudo /etc/init.d/gdm stop
[color=blue]## now change to the build-dir[/color]
cd /usr/src/git-compiz/scripts
[color=blue]## and remove the actual installed compiz (you should have considered to backup your profile by now)[/color]
./git-compiz --purge
[color=blue]## When done, check your dependencies[/color]
./git-compiz --check-dep --with-desktop=gnome
[color=blue]## And get your git-compiz[/color]
./git-compiz --with-desktop=gnome

```

Now depending on your habits consider to have a nice smoke or so, or just smoke a cigarette. When done bring gdm back up and enjoy
```

sudo /etc/init.d/gdm start
```


If you didn't install protobuf yet, open up synaptic, search for protobuf and grab the 5 or 6 packages NOW.
The next minutes may be somewhat slow/tearing, hence the protobuf cache is built.(the dir is located in your home dir: ~/.cache/ and the files should end with .pb)
Log out and back in, and enjoy the ride :)

---

### Post by Izek on 2008-12-12
By the way loomsen, you forgot to mention that libcompizconfig0 doesn't appear when searching for compiz in the quick search. You can however remove it from terminal, **sudo aptitude remove libcompizconfig0** and it WILL remove.

Seems my hanging issue/bug is still apparent even with protobuf. *sighs* Oh well, time to remove compiz altogether.

---

### Post by loomsen on 2008-12-12
Thanks for pointing at.

---

### Post by Izek on 2008-12-14
By the way: [http://ubuntuforums.org/showthread.php?t=1010651](http://ubuntuforums.org/showthread.php?t=1010651)

Though, I haven't tried using shame's repo with hardy.

---

### Post by hellsgator on 2009-02-24
Loomsen,

Great tut, even i managed to install git-compiz. Not bad for a no0b. 

Time for a stupid question, but those need to be asked as well sometimes.

I followed all of your instructions and yahoo, i got it working. Still at start up, it does not recognize git-compiz and it does not work as it should. If i use "compiz --replace" it stays the same and not all is working well. I have to use the fusion icon and reload the window manager to get it working okay. After the reload it works like a charm.

After i tried to install and configure AWN, it did not appear after i rebooted. Instead i gotten a error message telling me that the screen was not composited and that i need to select a window manager. It is there, it just not recognized at startup. The reload in Fusion Icon fixes the issue and AWN appears. 

I just have no idea on how to change this permanently. Where the peep! do i change this in order to make it recognize git-compiz at startup? I think both issues are connected and i am not sure what to do next. Will you give a little help here, so i can fix the issue? 

I am running on Jaunty. It might also be a temp issue.

---

### Post by loomsen on 2009-03-07
Sorry, haven't been online for a while cause I moved.

Might be jaunty related, but it sounds like it's just due to your startup.

Write a little bash script to start AWN after fusion-icon, and chose fusion-icon as your default window manager.(You could i.e. change gnome-wm to fusion-icon in System->Pref->Startup Applications. Look for window manager and change the command to /usr/bin/fusion-icon.

Should be fine at startup then I think. 
Did you notice the hint that this repo is no longer maintained by shame?

---

### Post by yuki86 on 2009-03-08
how can i revert my original compiz back. i don't see it in repo through synaptic anymore

thanx

---

### Post by hellsgator on 2009-03-10
Thanx again for pointing in the right direction. ;)

No GWM in there, i just added Fusion Icon with command fusion-icon.

All works fine now. :D

---

### Post by jordan420 on 2009-04-20
hello, does anybody have any information in getting this working with the release candidate? (jaunty) i've been trying but i can't seem to get it working.. at all.

---

### Post by loomsen on 2009-04-22
> **loomsen said:**
> Hi everyone.

Unfortunately shame's repo 

due to


So I'd like to say thanks for all the work shame, if you read this by chance, and my wholehearted best wishes to you. Hopefully everything will take a turn for the better as soon as possible.



[The whole story](http://shame.tuxfamily.org/repo/?p=266)

So, thx again shame, it's always been a pleasure using your repo.


Much obliged

loom.

Couple of posts above this one.

---

### Post by loomsen on 2009-04-22
[QUOTE=steigerjb]Ok, I got Git. I can't seem to be able to enable advance desktop effects.

See below of before/after when i try enabling desktop effects in appearance.

before:
[http://i43.tinypic.com/15yx7bt.png]("http://i43.tinypic.com/15yx7bt.png")

after:
[http://i39.tinypic.com/15cxzix.png]("http://i39.tinypic.com/15cxzix.png")[/QUOTE]


Please avoid private messages, and also read above... This is outdated. Just stay with the packages that are in the repos. Compiz is stable now, there won't be much of a difference till 0.9 will be released somewhen.

Unless you encounter a seriously annoying bug, want to change source code or happen to be a developer you probably won't need compiz git.

---

### Post by pete_m on 2010-04-28
many thanks loomsen for the information you provide in this thread.  . .

not being scared off by git and the prospect of ( eventually ) creating and modifying source i have read through . .

as my first ubuntu install is of ( an updated ) koala netbook remix 2 i suspect that i do not ( presently ) need the git repo stuff

my question here is should i install the protobuf stuff into my install ? will this offer better/ faster/ more reliable performance ?
i am new to ubuntu and relatively new to debian linux so some of the material is a little beyond me presently.  .

just beginning to learn about the internals of gnome/ windows managers and decorators. .

i guess fusion-icon will be very useful to me as i get to grips with compiz/ metacity/ gnome/ kde/ LXD/Xfce and such.

if anyone were to read this and be able to any pointers to good resources for learning about this more generally i would be most grateful, and such might also be useful to others .. 

i hope in the near future to move to Lucid and debian unstable( as per eb4 ) - any observations as to this plan would be appreciated . .

perhaps i should stick with my present install where i have a blender 2.5 and compiz working and continue my explorations here, but my inclination is to move to the newest versions. .

i hope finally to create ( in gtk and python ) a time-based program for manipulating blender in a compiz-enabled desktop environment.

thanks, and best wishes to all.

---

