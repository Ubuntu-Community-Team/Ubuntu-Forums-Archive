---
title: "Having trouble installing media players VLC Mplayer"
date: 2006-01-03
forum: Installation &amp; Upgrades
---

### Post by dixonstalbert on 2006-01-03
hello

I have using synaptic  and automatix to download a variety of media players, but the only 2 that are stable on my system are Beep Media Player and Totem-xine.

Many on the forums prefer Mplayer and VLC but I cannot get them to run

I have been battling VLC the last few days, which does the following:

1. If I start it off the applications menu it it immediately minimizes and will not maximize if I right-click on it

2. If I start in terminal I get the message ""GLib-Warning **: g_main_iterate(): main loop already active in another thread""       continuously until I press Ctrl-C

3 If I start in terminal with 'sudo vlc '  I get error message Gtk-WARNING: ""Unable to locate loadable module in module_path: libredmond95.so"",  but the application will start. It will play mp3's but it will not play DVD video

I am running a Dell Inspiron with integrated Intel915 graphic and my gcc version is 4.0.2

I used gnome search tool to try to find an error log that gets written to when vlc crashes but I cannot find anything.

I have tried removing with synaptic manager and reinstalling with synaptic and with Automatix but get same errors.

I tried using debfoster to remove them and all their dependancies, plus everything else I thought was interfering. After I reinstalled with Automatix I could get it to run off the application menu without any error messages , but it still would not read DVD. When I rebooted I lost my gnome desktop gui (from deleting something critical with debfoster!) and had to reinstall it with sudo apt get gnome-desktop.
When I rebooted desktop gui was back, but so was error messages!  

Any ideas how I can start to track down problem or better yet fix?;)

---

### Post by dixonstalbert on 2006-01-05
figured this one out!


gnome search tool does not find hidden files unless you set it under 'select more options' >> available options.

After I set this, I found the the hidden directories .mplayer and .vlc 

I deleted old config files in .mplayer and .vlc in my home directory and re-installed with Automatix

everything working great now

hope this helps someone

---

