---
title: "SongBird player doesn't load"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by sh4dyPT on 2009-02-16
Hello, I have installed Ubuntu 8.10 32 bits OS and I want to install SongBird music player, bud after installing .deb file I can't open the player. By clicking once on SongBird icon, on System Monitor I have two instance of songbird and tow of songbird-bin.
I don't know what to do, I have already reinstalled application twice and it's always the same :S.
I really love this player.

Any help will be appreciated.

---

### Post by redroad55 on 2009-02-16
I had to download from here :[http://www.getdeb.net/app/Songbird]("http://www.getdeb.net/app/Songbird")
and chose to let it run rather than save..

---

### Post by sh4dyPT on 2009-02-16
> **redroad55 said:**
> I had to download from here :[http://www.getdeb.net/app/Songbird]("http://www.getdeb.net/app/Songbird")
and chose to let it run rather than save..

Nope, still not working :s


When I try to run songbird in terminal, the first line is 
"*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0xb2e9e640 ***"
I don't understand what this mean, but could this be an error or something?

---

### Post by redroad55 on 2009-02-16
This is what songbird's site says for Pkg. Requirments:

#  glibc 2.3.2 or later

# XFree86-3.3.6 or later

# gtk+2.0 or later

# fontconfig (also known as xft)

# libstdc++6

check synaptic to see if they are installed..

---

### Post by kk0sse54 on 2009-02-16
You can also just download the package from the songbird site and extract it into your home directory. Within it it already has a ready to go executable that you just have to double click on for it to run without having to install anything.

---

### Post by sh4dyPT on 2009-02-17
> **redroad55 said:**
> This is what songbird's site says for Pkg. Requirments:

#  glibc 2.3.2 or later

# XFree86-3.3.6 or later

# gtk+2.0 or later

# fontconfig (also known as xft)

# libstdc++6

check synaptic to see if they are installed..
I have those all packages installed on my system.

> **C!oud said:**
> You can also just download the package from the songbird site and extract it into your home directory. Within it it already has a ready to go executable that you just have to double click on for it to run without having to install anything.

I have already tried this way, and still not working.

And after executing songbird twice, I receive this message "Songbird is already running, but is not responding. To open a new window, you must first close the existing Songbird process, or restart your system."

---

### Post by redroad55 on 2009-02-17
Try removing songbird and reinstalling .. Remove by :
> sudo apt-get remove songbird

then install from link I provided from previous post ..

---

### Post by sh4dyPT on 2009-02-17
> **redroad55 said:**
> Try removing songbird and reinstalling .. Remove by :


then install from link I provided from previous post ..

Still not working. :s.
I have tried to install songbird 0.7.0 and it works, but 1.0.0 doesn't. If there is any way to get 1.0.0 working I prefer 1.0.0, otherwise I will use 0.7.0.

Thank you all for your help, I appreciate it ;)

---

### Post by redroad55 on 2009-02-17
I'm running 1.0  with the 8.04 kernel .. The 1.0 version uses gstreamer where 0.7 used vlc so I would say your problem lies there .. In repositories do you have Medibuntu , If not than go here :
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

---

### Post by sh4dyPT on 2009-02-17
> **redroad55 said:**
> I'm running 1.0  with the 8.04 kernel .. The 1.0 version uses gstreamer where 0.7 used vlc so I would say your problem lies there .. In repositories do you have Medibuntu , If not than go here :
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

What am I suppose to do? follow that tutorial? Songbird doesn't appear on "Add/remove...". I have vlc installed.

---

### Post by redroad55 on 2009-02-17
This adds the repository to your software sources allowing in this case any gstreamer pkgs. that may be needed for songbird 1.0 to become available ..be sure and choose the kernel that you have installed on your system..

---

### Post by sh4dyPT on 2009-02-18
> **redroad55 said:**
> This adds the repository to your software sources allowing in this case any gstreamer pkgs. that may be needed for songbird 1.0 to become available ..be sure and choose the kernel that you have installed on your system..

I have added Medibuntu repository and still have my problem not fixed. What am I suppose to do next?

---

### Post by sh4dyPT on 2009-02-20
> **redroad55 said:**
> This adds the repository to your software sources allowing in this case any gstreamer pkgs. that may be needed for songbird 1.0 to become available ..be sure and choose the kernel that you have installed on your system..

I have downloaded all available gstreamer packages, but Songbird 1.0.0 doesn't load!

---

### Post by redroad55 on 2009-02-20
I think since you have attempted to install both versions you have a conflict in profiles .. I believe you are going to have to do more than uninstall but also the profile .. Then reinstall .. It is important to log out and log back in after making changes to profile .. Here is a link that should help to purge :[http://wiki.songbirdnest.com/Developer/Articles/Uninstall_Songbird]("http://wiki.songbirdnest.com/Developer/Articles/Uninstall_Songbird")..Post back with any results and or questions

A simple test to see if your profile is the suspect is to log out and log back in as a different user..

---

### Post by sh4dyPT on 2009-02-20
> **redroad55 said:**
> I think since you have attempted to install both versions you have a conflict in profiles .. I believe you are going to have to do more than uninstall but also the profile .. Then reinstall .. It is important to log out and log back in after making changes to profile .. Here is a link that should help to purge :[http://wiki.songbirdnest.com/Developer/Articles/Uninstall_Songbird]("http://wiki.songbirdnest.com/Developer/Articles/Uninstall_Songbird")..Post back with any results and or questions

A simple test to see if your profile is the suspect is to log out and log back in as a different user..

I have tried few times to reinstall application and remove profiles, but after removing **libvisual-0.4-plugins** package and **profiles folder** Songbird 1.0.0 has finally load.
> sudo apt-get remove libvisual-0.4-plugins
Thank you very much, I really appreciate your help.

---

