---
title: "Java webstart - a few issues"
date: 2008-11-10
forum: General Help
---

### Post by whitehexagon on 2008-11-10
I'm a complete newbie to Ubuntu, but I have a player on my game I'm working on that's had some issues using Java.  So I'm busy setting up a box to try and recreate said issues.

Firstly I tried installing the Java 6 update 10 direct from the Sun site.  I put it into /usr/local/java.  Next I couldn't find the plugins directory for firefox, so I tried creating the directory and the symbolic link for the plugin.  That didn't work, so I had a hunt around for other plugins and tried the directory /usr/lib/xulrunner-addons/plugins.  That seemed to work better, at least in about:plugins in firefox it was displaying some java plugin stuff.  However it only seems to work for Java Applets, my Webstart jnlp still wasn't finding the plugin.

So I went back to searching the net and tried some apt-get install commands that I found for installing Java 6.  This went through ok, but from the command line java -version is reporting 1.6.0_07 when what I really want is update 10.  The sun Applet test still says I'm using update 10, but at least the webstart seems to work, although using update 7.

Besides all the above I was at least finally able to get into my game and give it a quick test drive.  However I noticed straightway that the Dialog popups are failing to display correctly.  The game is fullscreen, maybe that has something to do with it?  Anyway, the dialog appears briefly and then seems to fade & shrink before anything has been clicked or selected.  Anyone seen this behaviour?  The font's also look very strange, but that's a minor issue in comparison.

I'd like to get Java 6 update 10 working and see if that fixes the problem, I could also upgrade from Hardy Heron, but I'd prefer to find the cause of this problem rather than force players to upgrade their OS version.

Cheers
Peter

PS If anyone would like to help test the game (under development) you can visit whitehexagon.com    username: demo   password:   playme
PPS If you also get stuck with the dialog issue, you can hit ESC then Enter to quit the game.

---

