---
title: "Firefox 3.5"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by psychok7 on 2009-06-20
hi there, i was just wondering since firefox 3.5 is almost coming out, if there will be an update on the ubuntu repositorys, or if i have to add another repository to actually get firefox 3.5 running? 

i know i can add :
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) intrepid main 

is there a better repository?

---

### Post by starcraft.man on 2009-06-20
No, there likely won't be an update to 3.5, at least from my experience. No need for a repo to get 3.5 right now.

They way I stay bleeding edge with firefox is simply to download the nightly snapshots. One great thing about linux is you can just extract the archive and run it in place on your desktop or a folder.

[Link]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/") Go to their site and download the tar.bz2 archive you need whether it's 686 or 64 (for 64 bit obviously). Once you download it to your desktop, just extract and you can run it from the command line quite easily. To simplify this I always make a launcher along side. To make a launcher, right click on the desktop and say create launcher. Type in a name (like firefox3.5) and then add the below path to the command box. You just need to direct the launcher towards the firefox command to launch that version. Assuming you download and run it from your desktop, you can use this path...

```
./Desktop/firefox/firefox
```

If you want to put it in the home directory you just direct it there.

Hope that helps, 3.5 is MUCH better than 3.

---

### Post by psychok7 on 2009-06-20
> **starcraft.man said:**
> No, there likely won't be an update to 3.5, at least from my experience. No need for a repo to get 3.5 right now.

They way I stay bleeding edge with firefox is simply to download the nightly snapshots. One great thing about linux is you can just extract the archive and run it in place on your desktop or a folder.

[Link]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-1.9.1/") Go to their site and download the tar.bz2 archive you need whether it's 686 or 64 (for 64 bit obviously). Once you download it to your desktop, just extract and you can run it from the command line quite easily. To simplify this I always make a launcher along side. To make a launcher, right click on the desktop and say create launcher. Type in a name (like firefox3.5) and then add the below path to the command box. You just need to direct the launcher towards the firefox command to launch that version. Assuming you download and run it from your desktop, you can use this path...

```
./Desktop/firefox/firefox
```

If you want to put it in the home directory you just direct it there.

Hope that helps, 3.5 is MUCH better than 3.


wont i have problemas with flash and other sort of things or the executable automatically knows the paths to get wht it needs?

---

### Post by starcraft.man on 2009-06-20
> **psychok7 said:**
> wont i have problemas with flash and other sort of things or the executable automatically knows the paths to get wht it needs?

Nope. Not to my knowledge. I got flash and my VLC plugin working in it. Those are only two I really need. I just had a look and didn't see java for some reason, might just be because it isn't compatible with 3.5 yet. I think the plugins are loaded from your profile in the home folder, and that means it's the same whether you use 3 or 3.5.

If your scared, don't be, you can always click the icon on the top panel and get 3.0 with all your compliant plugins. Running from the desktop means you aren't modifying anything on the computer (to my knowledge), just don't make it default since you might delete the desktop version one day.

---

### Post by psychok7 on 2009-06-20
i decide to go for the repositorys, dont feel like checking for an updated version all the time.. it seems to work fine and i can still use both. thanks anyways

---

### Post by khelben1979 on 2009-06-20
I guess it won't compile for the ppc linux platform. Am I right?

---

### Post by psychok7 on 2009-06-22
> **starcraft.man said:**
> Nope. Not to my knowledge. I got flash and my VLC plugin working in it. Those are only two I really need. I just had a look and didn't see java for some reason, might just be because it isn't compatible with 3.5 yet. I think the plugins are loaded from your profile in the home folder, and that means it's the same whether you use 3 or 3.5.

If your scared, don't be, you can always click the icon on the top panel and get 3.0 with all your compliant plugins. Running from the desktop means you aren't modifying anything on the computer (to my knowledge), just don't make it default since you might delete the desktop version one day.

i have one last question, how does it work with the updates if i use your method? they will be automatically available or i have to get another source folder?

---

### Post by trx64 on 2009-07-27
Firefox 3.5 is updated (3.5.1) in the repositoris, I'm using it roght now. Just install [firefox-3.5]("apt:firefox-3.5") package.

---

### Post by bakhy on 2009-07-27
I just tried out the "firefox-3.5" package. It installs something called Shiretoko, which seems to be a codename for the new version. The font used on the menu and toolbar looks really blurry (and crappy, too), and facebook is convinced I'm using an outdated browser, and won't activate chat :/

Why is all this so? When is the regular update mechanism going to upgrade it to 3.5, but some normal variant of it? Why isn't it done already? The Firefox I use at work, on a Windows machine, upgraded itself a week or two ago without any fuss...

I'm guessing (or hoping) you guys have to do some extra work before the new version can fit into Gnome seamlessly? Well, until that happens, can somebody help with these two issues I'm having?

---

### Post by trx64 on 2009-07-27
> **bakhy said:**
> I just tried out the "firefox-3.5" package. It installs something called Shiretoko, which seems to be a codename for the new version. The font used on the menu and toolbar looks really blurry (and crappy, too), and facebook is convinced I'm using an outdated browser, and won't activate chat :/

Why is all this so? When is the regular update mechanism going to upgrade it to 3.5, but some normal variant of it? Why isn't it done already? The Firefox I use at work, on a Windows machine, upgraded itself a week or two ago without any fuss...

I'm guessing (or hoping) you guys have to do some extra work before the new version can fit into Gnome seamlessly? Well, until that happens, can somebody help with these two issues I'm having?

The new Firefox will be included in Karmic. To use it now, you have two choices:

1 - Use Shiretoko, the Firefox 3.5 development version, constantly updated (just the name is different). The Facebook problem could be solved using the extension User Agent Switch, making Shiretoko identifies as Firefox.

2 - Download Firefox from Mozilla, unpack it in your home and run "firefox" in that directory. 

Font problems? Try this links:
[http://ubuntuforums.org/showthread.php?p=7094387#9](http://ubuntuforums.org/showthread.php?p=7094387#9) (better solution. If doesn't work for you, try the next one)
[http://webupd8.blogspot.com/2009/07/fix-fonts-in-firefox-35-and-ubuntu.html](http://webupd8.blogspot.com/2009/07/fix-fonts-in-firefox-35-and-ubuntu.html)

---

### Post by bakhy on 2009-07-27
Karmic gets out at October 29th. Am I wrong to think just waiting for it is not appealing?

Is this generally the case - when a new version is in the works, updates to the current one stop?

---

### Post by trx64 on 2009-07-27
> **bakhy said:**
> Karmic gets out at October 29th. Am I wrong to think just waiting for it is not appealing?

Is this generally the case - when a new version is in the works, updates to the current one stop?

Major version updates (like Firefox 3.0 --> 3.5 or KDE4.2 --> 4.3) are made only during version changes in Ubuntu (I understand it in KDE's case, it's a huge update, but in Firefox case that should be different).

The better solutions are that I've posted... Download from Mozilla, use Shiretoko or wait for Karmic.

---

