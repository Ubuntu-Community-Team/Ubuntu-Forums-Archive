---
title: "How do i Install beryl?"
date: 2008-07-24
forum: General Help
---

### Post by Alex K. on 2008-07-24
Im very confused, ive downloaded beryl from here: [http://linux.softpedia.com/get/Multimedia/Graphics/Beryl-19790.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/Beryl-19790.shtml)
and there are 4 seperate .tar files and im unsure as to how to install beryl.

(P.S. im new at this, is beryl the program used to mod skins or use different skins?)

---

### Post by armageddon08 on 2008-07-24
Hi there!
Which Ubuntu version are you using? If you are using Hardy or even Gutsy, then you don't need to install Beryl. They have Compiz-fusion(which is a merge of Beryl and Compiz) preinstalled within them.

Open up Synaptic and search for Compizconfig-Settings-Manager and fusion-icon and install them.
Open System-->Preferences-->Compizconfig-Settings-manager and select options you need.

Now if you want to run Compiz-fusion on startup:
Go to System-->Preferences-->Sessions. Click on the tab Startup programs-->
Click Add. In name type Fusion and in Command type _fusion-icon_.

Enjoy!!

---

### Post by Alex K. on 2008-07-24
Im not sure which I am using to be honest, I am using Ubuntu 8.04 that is all I know, and i cannot find Compiz-Fusion on my Operating system. Is there anyway to download it or something?
Thanks!

---

### Post by flamethrower on 2008-07-24
well, im not using ubuntu at all but a google search for "ubuntu 8.04" turns up several results associating it to the acronym "hardy heron", so i fail to see how you can have simply no clue as to what version you are using, esp. given the limited choices of "hardy" and "gutsy" in the previous post.

---

### Post by chalewa on 2008-07-24
> **flamethrower said:**
> well, im not using ubuntu at all but a google search for "ubuntu 8.04" turns up several results associating it to the acronym "hardy heron", so i fail to see how you can have simply no clue as to what version you are using, esp. given the limited choices of "hardy" and "gutsy" in the previous post.

he said he was using 8.04 who cares if he didn't know what the name of the release was

---

### Post by Alex K. on 2008-07-24
Sorry, im new to this Linux bizz and I ask alot of questions :P Im not sure which distro it is I just know it is the latest version of Ubuntu. The packet manager says i have all the emerald files installed but i cant seem to locate them anywhere on my computer!

---

### Post by flamethrower on 2008-07-24
> **Alex K. said:**
> Sorry, im new to this Linux bizz

"bizz" -.-

> and I ask alot of questions :P Im not sure which distro it is I just know it is the latest version of Ubuntu.

as i said, a simple google search would've turned it up

> The packet manager says i have all the emerald files installed but i cant seem to locate them anywhere on my computer!

so u wanna "locate the files on your computer", eh?
well, it's in /usr if ubuntu puts stuff where it belongs.
now that you'Ve located the stuff, what r u gonna do?

---

### Post by Alex K. on 2008-07-24
> **flamethrower said:**
> "bizz" -.-



as i said, a simple google search would've turned it up



so u wanna "locate the files on your computer", eh?
well, it's in /usr if ubuntu puts stuff where it belongs.
now that you'Ve located the stuff, what r u gonna do?

You're really not helping.

---

### Post by klange on 2008-07-24
> **Alex K. said:**
> You're really not helping.

First off, Beryl is dead, Compiz-Fusion is the replacement, and as you're new, you shouldn't have any problems with the things that remain unported.

On that subject, Compiz-Fusion comes pre-installed with Ubuntu, and assuming you have your hardware drivers set up properly, it'll even be running.

To get all the fancy effects you may have seen on YouTube or been told about by others, you need to install the package **compizconfig-settings-manager** (better known as *ccsm*), which can then be run from System > Settings > Advanced Desktop Effects Settings.

On the subject of Emerald, it's old and, to be honest, deprecated. We (the C-F devs) don't really support it much any more and it hasn't had a real code change in months. As a beginner, using Emerald themes should be the least of your worries, what with all the fine GTK themes available and the gtk-window-decorator (active by default with Compiz) which uses your regular window decorations (or "skins" as you've referred to them). Compiz will add some special effects to normal themes that should suffice.

---

### Post by mikedemario17 on 2008-07-24
> **Alex K. said:**
> Im very confused, ive downloaded beryl from here: [http://linux.softpedia.com/get/Multimedia/Graphics/Beryl-19790.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/Beryl-19790.shtml)
and there are 4 seperate .tar files and im unsure as to how to install beryl.

(P.S. im new at this, is beryl the program used to mod skins or use different skins?)
1st-----> Compiz-fusion....its a merge of beryl and compiz...compiz bought out beryl....and yea it does all the fancy stuff..

-great video of it in action-->[http://www.youtube.com/watch?v=ZxfSwzhSn1c]("http://www.youtube.com/watch?v=ZxfSwzhSn1c")

-great link to help you along---> 7.10--->[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200")
8.04--->[http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200]("http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200")

---

### Post by flamethrower on 2008-07-24
> **Alex K. said:**
> You're really not helping.

i wasnt really trying .. and it really wasnt neccessary.

everything to be said has basically been said:
beryl/emerald are old, get compiz-fusion.

you seem capable of operating the package manager, so install it and you're set.
if you wanted something else, you didnt ask for it.

---

### Post by klange on 2008-07-24
> **mikedemario17 said:**
> 1st-----> Compiz-fusion....its a merge of beryl and compiz...compiz bought out beryl....and yea it does all the fancy stuff..
First off, those arrows are really annoying.
Second, no one bought out anyone. Beryl was a fork of Compiz that added some kludges to the core as well as tons of new plugins. It was forked because the Compiz developers didn't agree with some of the changes made by the Beryl developers. Eventually, their differences were resolved and the Beryl plugins were ported to Compiz, as well as various Beryl tools, some core changes were made, and out came Compiz-Fusion. Some of the core developers will still argue that Compiz and Compiz-Fusion are technically separate projects, but as we all intermingle (even I have explored changes to the core, though only to a personal extent), and as it's all hosted in the same place, it's all just one big project (and since Compiz-Fusion has Compiz in it, we tend to just using it as the name).

Phew. Well, there you have it.

@flamethrower: Install what? The only thing you'll ever have to install in Ubuntu as of Gutsy is ccsm <[b]compizconfig-settings-maanager[b]>, but Compiz (as well as c-f-plugins-main and c-f-plugins-extra) are included by default.

---

### Post by overdrank on 2008-07-24
Hi and if the op would look at the FAQ's at the top of the forum, then if still having issues make a thread.
As for the other comments if you would like to help do so in a polite manner. Thanks :)

---

### Post by Joeb454 on 2008-07-24
+1 overdrank

Also @ flamethrower, emerald isn't dead, it's still around. I believe a lot of themes still use it actually.

---

### Post by armageddon08 on 2008-07-25
> **armageddon08 said:**
> Hi there!
Which Ubuntu version are you using? If you are using Hardy or even Gutsy, then you don't need to install Beryl. They have Compiz-fusion(which is a merge of Beryl and Compiz) preinstalled within them.

Open up Synaptic and search for Compizconfig-Settings-Manager and fusion-icon and install them.
Open System-->Preferences-->Compizconfig-Settings-manager and select options you need.

Now if you want to run Compiz-fusion on startup:
Go to System-->Preferences-->Sessions. Click on the tab Startup programs-->
Click Add. In name type Fusion and in Command type _fusion-icon_.

Enjoy!!

C'mon I told you in the above post what you need to be doing. just follow the steps.

Before doing anything goto System-->Preferences-->Appearance. Click the tab 'Visual Effects' and then enable 'Extras' and then follow the steps said above.

---

### Post by russo.mic on 2008-07-25
> **flamethrower said:**
> i wasnt really trying .. and it really wasnt neccessary.

everything to be said has basically been said:
beryl/emerald are old, get compiz-fusion.

you seem capable of operating the package manager, so install it and you're set.
if you wanted something else, you didnt ask for it.

Let me refer you to this webpage:

[http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29](http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29)

Don't be an *******.

Russo

---

### Post by Alex K. on 2008-07-25
> **WindowsSucks said:**
>  which can then be run from System > Settings > Advanced Desktop Effects Settings.



I dont have Advanced Desktop Effects in that Directory.
Or in any directory I cant locate it.

---

### Post by steveneddy on 2008-07-25
> **Alex K. said:**
> I dont have Advanced Desktop Effects in that Directory.
Or in any directory I cant locate it.

In terminal

```

sudo apt-get install compizconfig-settings-manager

```

Then look in

System --> Preferences --> Advanced Desktop Effects Settings

---

### Post by Alex K. on 2008-07-25
> **steveneddy said:**
> In terminal

```

sudo apt-get install compizconfig-settings-manager

```

Then look in

System --> Preferences --> Advanced Desktop Effects Settings

ak@ak-laptop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for ak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

Thats what i got.

---

### Post by steveneddy on 2008-07-26
> **Alex K. said:**
> ak@ak-laptop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for ak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

Thats what i got.

You may need to enable extra repositories, maybe even all of them.

Open System --> Administration --> Software Sources

Check all of the boxes if you like, but especially the Universe repo, where

compizconfig-settings-manager

resides.

In terminal

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

then when that is done do

```

sudo apt-get install compizconfig-settings-manager

```

then go look for it here:

System > Settings > Advanced Desktop Effects Settings

---

