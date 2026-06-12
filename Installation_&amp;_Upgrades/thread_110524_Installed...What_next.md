---
title: "Installed...What next?"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by BlackShadow on 2005-12-31
Okay. I downloaded the Breezy Badger or whatever it is called.  Put the ISO on a cd, and put it in a seperate computer that I wanted to install Ubuntu on.  The installer came on and the first screen came up. It said something about typing server for one type of install or just hit enter for a different type of install. So I hit enter.  It went through, I did everything like it said, and it didn't work. It froze up after the install.  So my friend said re-install and type server at that one screen. So I typed server, and did the install for that one. Everything was partitioned, everything was configured, and it showed me a login page. So I logged in and I am now sitting with a command prompt in front of me.  I know NOTHING about command prompts, I am new and someone said this was the best starter, and everywhere I go it uses what is called GNOME (isn't that a lawn decoration?).  It says run terminal in GNOME.  What the hell is GNOME, and how do I find it? I am so lost. I just see this command prompt. HELP PLEASE!

---

### Post by Jeff12088 on 2005-12-31
Well, tell you what? You installed the wrong one, the server install only installs the "base system" without additional packages which is not suitable for new users.
The easiest way to do it is to reinstall again only hitting enter and post what problems you come up.

---

### Post by BlackShadow on 2005-12-31
Went through the entire re-install process, using the default install setup.  Well everything installed and everything loads fine.  The only Fail on the OK/Fail is when it tries to sync the clock to the website, because I don't have internet hooked up to that tower.

So it loads on and then I get a solid black screen. At the top left cornor is an unblicking, tiny white line.  That is all. I have let it set for an hour in hopes that it would load. So what do I do? I don't wanna install again, and you said not to do the server install since I was a beginner.

---

### Post by Herman on 2005-12-31
[http://ubuntuforums.org/showthread.php?t=108999&highlight=Herman]("http://ubuntuforums.org/showthread.php?t=108999&highlight=Herman")

Well, I would first try re-starting the computer just to see if that helps. I'm not sure if this is right or not, but I use the left alt key and the print screen key, (hold those two down), and press your 'r' followed by you 's' , then 'e', and 'i' 'u' and finally 'b' keys to make the computer re-boot.
I would just try re-booting it first and see if that fixes it. I have an old computer and sometimes it doesn't start up reliably every time and I just have to try again and then it starts up okay. (It's one of those infamous PcChips 'Book PCs')! (LOL).
Okay then, if that doesn't work, see how this problem (it sounds like the same problem anyway), was solved here a few days ago, by clicking on the link given above. I think that should help you fix it, hopefully. :D (Herman).

---

### Post by Jeff12088 on 2005-12-31
[QUOTE=BlackShadow]Went through the entire re-install process, using the default install setup.  Well everything installed and everything loads fine.  The only Fail on the OK/Fail is when it tries to sync the clock to the website, because I don't have internet hooked up to that tower.

So it loads on and then I get a solid black screen. At the top left cornor is an unblicking, tiny white line.  That is all. I have let it set for an hour in hopes that it would load. So what do I do? I don't wanna install again, and you said not to do the server install since I was a beginner.[/QUOTE]
I think that is because of problems with your video card and X server.

When you see the black screen, press Crtl+Atl+F1 and login.
Then type
```
sudo dpkg-reconfigure xserver-xorg
```
Basically follow the directions and finish reconfiguring.
Posting what kind of video card you have will help.
You might have to go to your xorg.conf and change some settings.
When your done, type
```
sudo init 2
```
to see if it works.
This thread should help a little [http://ubuntuforums.org/showthread.php?t=106986&highlight=dpkg-reconfigure](http://ubuntuforums.org/showthread.php?t=106986&highlight=dpkg-reconfigure)

---

### Post by BlackShadow on 2005-12-31
nothing happens when I press ctrl-alt-f1

---

### Post by Jeff12088 on 2005-12-31
Hmm Crtl Atl F1 or Crtl Atl F2 should bring you to text mode...
Don't know why it doesn't, perhaps keyboard problem?

---

### Post by BlackShadow on 2005-12-31
Well my keyboard works. I mean I did have to type in my username, computer name, and password.  So it can't be keyboard problems.  I don't know what it is. I have hit ctrl-alt- and all the f keys.

---

### Post by BlackShadow on 2006-01-01
anyone? I had FreeBSD installed and it worked fine. Why wouldn't this one?

---

### Post by ninotob on 2006-01-01
I would try the suggestion linked above first because I'll bet it's a problem with X (the windowing system).  I wonder if the default installer is failing in some way, like setting up X w/ wrong resolutions.  Not that I really know ...

However, I've had some problems with the Breezy installer.  The easiest solution is to install in two steps -- install as server, then install the desktop.  If you are a up to it, I would say .... sigh .... install one more time.  Except install "server".

Now, "server" installs the most basic system so when it reboots, you will be at a text based login propmpt.  Type in your username, press enter, type in your password, press enter.

You will then be at a "$" prompt. type:

sudo apt-get install ubuntu-desktop

and then enter your password again.  At some point during the install, you will be presented with a blue background page which asks for your monitor's resolutions.  Make sure the resolutions you want to use are starred, **but don't excede your monitor's resolution capabilities** -- that'll cause problems.  You can navigate the list with the arrow keys, tab key, the space-bar selects/deslects resolutions.  Press enter when "continue" or "ok" (or whatever similar concept is used) after checking the resolution table, and the rest should finish up without your interaction.

From then on, you'll have a graphical login.

---

### Post by Jeff12088 on 2006-01-01
[QUOTE=ninotob]I would try the suggestion linked above first because I'll bet it's a problem with X (the windowing system).  I wonder if the default installer is failing in some way, like setting up X w/ wrong resolutions.  Not that I really know ...

However, I've had some problems with the Breezy installer.  The easiest solution is to install in two steps -- install as server, then install the desktop.  If you are a up to it, I would say .... sigh .... install one more time.  Except install "server".

Now, "server" installs the most basic system so when it reboots, you will be at a text based login propmpt.  Type in your username, press enter, type in your password, press enter.

You will then be at a "$" prompt. type:

sudo apt-get install ubuntu-desktop

and then enter your password again.  At some point during the install, you will be presented with a blue background page which asks for your monitor's resolutions.  Make sure the resolutions you want to use are starred, **but don't excede your monitor's resolution capabilities** -- that'll cause problems.  You can navigate the list with the arrow keys, tab key, the space-bar selects/deslects resolutions.  Press enter when "continue" or "ok" (or whatever similar concept is used) after checking the resolution table, and the rest should finish up without your interaction.

From then on, you'll have a graphical login.[/QUOTE]

That is worth a good try. But to do sudo apt get install ubuntu-desktop
You need some kind of internet access ;)

---

### Post by Omnios on 2006-01-01
Some information might help people solve your problem. I had a similar problem with Nividia and a KTX monitor (monitor problem is common).
X just had a cursor line got around that by using recovery mode.

 It may be a problem with Xserver and your monitor.

 What is your graphics cand and monitor type.

---

### Post by BlackShadow on 2006-01-01
I have a dell flat panel screen and a EVGA video card installed.

---

### Post by BlackShadow on 2006-01-04
I think I am just going to try Debian or something else. :( This dosn't seem to work for me.

---

