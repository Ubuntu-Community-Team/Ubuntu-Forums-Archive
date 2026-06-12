---
title: "Cairo Dock problem. Cant remove applet."
date: 2008-08-13
forum: General Help
---

### Post by HittingSmoke on 2008-08-13
I decided to give the whole dock thing a try today and settled on Cairo after some research. First I installed the repo version then found info on compiling a version that would run from the grafix card to save ram and CPU so I ran a script I found here to compile and install that version.

I started playing around with it and enabled the Compiz Icon applet. I realized I didnt really need it so I tried to remove it. When i click remove applet the dock disappears for a second then reappears with applet still on the dock. Ive tried going into Cairo config and disabling it but as soon as I clear the check box the config window crashes and the same thing happens to the bar as when I try the regular remove button.

I tried to go through the Cairo forums with this but I dont speak French and their English IRC channel is a wasteland, So I hope someone here can help

---

### Post by Mgiacchetti on 2008-08-14
you can speak english in their forums, someone will answer(provided it may not be in a 'timely' manner).

this may be the issue, you installed from the repos, then compiled your own (using a script i might add)

you *should* have 'sudo apt-get remove cairo-dock --purge'  before compiling and installing another version.

You should have also opted to learn about the compile process, instead of reverting to a script.

I am sorry I do not know how to correct your problem, because you have compiled and installed a non deb package, and I would suggest that you try to figure out how to remove this version from your setup first.

---

### Post by fabounet on 2008-08-14
this bug was fixed yesterady ;-)
the SVN is quite unstable right now cause of the last changes.
People who don't want to be up-to-date day after day should stick to a stable version, which can be found on our repository (and it will take 30s to install !)

---

### Post by HittingSmoke on 2008-08-14
Well here's the deal. I want a Glitz enabled version to take off CPU load as I have a decent video card. It payed off because the Glitz version is a lot more responsive than the first one I installed. The version in the repos doesnt have this option so I looked for a .deb that had Glitz already compiled in for Kubuntu but all I found was a script which compiled the whole thing for me. Everything went fine and works well except this one problem.

I'm a complete noob when it comes to Linux and havent been able to find a dumbed down guide for compiling anything other than the usual ones that just say to untar, do ./configure and then make commands.

> this bug was fixed yesterady
the SVN is quite unstable right now cause of the last changes.
People who don't want to be up-to-date day after day should stick to a stable version, which can be found on our repository (and it will take 30s to install !)

I'm not necacarily worried about staying up to date day to day, I just want a stable version that will run with the Glitz command. I'f someone could point me to a tutorial on compiling that someone with no programming experience could pick up on I would be extremely grateful. Or at least walk me through compiling a stable version for Kubuntu that will run with the Glitz command.

Excuse my noobiness, I just made the permanant switch from Windows last week.

---

