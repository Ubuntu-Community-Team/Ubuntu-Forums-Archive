---
title: "recommended programs for ubuntu?"
date: 2008-08-01
forum: General Help
---

### Post by jooking on 2008-08-01
can anyone help me with a list of programs that i should have to use ubuntu normally? not the programs that are needed for ubuntu, but other kinds of programs. for ex. i dled an .exe to run something and i cant even run it b/c i dont have a program to open it. anyone can help? thanks

---

### Post by niyonk on 2008-08-01
.exe are programs for WINDOWS  :)
Try a Linux program called WINE it will run the .exe file for you but is not compatible with all programs.

Most programs in Linux are listed in a package manager then retrieved from the internet.

And it also depends on what kind of stuff you want to do on Ubuntu
I have:
Kopete- yahoo messenger alternative
aMSN
Cheese- for my webcam
Amarok- for my music
K3B for CD burning
Mplayer or VLC for Video, DVD and Music playback 
You also need Gstreamer extra plugins and Gstreamer ffmpeg video plugin from Applications->Add or remove.. to play mp3s and some videos

---

### Post by UbuntuNerd on 2008-08-01
exe is an executable windows file Ubuntu can't open it, you need to install wine if you want to run windows apps but not all of them work well check this link for more info hope this helps 

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by jualin on 2008-08-01
Dedpending on your needs you can download extra packages (programs) using Synaptic Package Manager or "Add and Remove". Ubuntu comes with pretty much everything the common user might need. You have an Office Suite, CD/DVD Burner, Browser and Music Player. The only programs I might suggest are DVD Ripping programs (if you are into that), you can download DVD95 for that. I didnt like the default music player (Rythmbox) so I installed Audacious and Amarok. Hope this helps!

---

### Post by Vivaldi Gloria on 2008-08-01
For installing programs use

system menu > admin > synaptic

Also enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies.

---

### Post by jualin on 2008-08-01
[URL="http://linuxappfinder.com/"]This website/URL] has a good list of linux applications as well as alternatives for Windows applications. And to run some .exe files in Ubuntu download Wine using Synaptic Package Manager or by writing this in the terminal > sudo apt-get install wine Good luck!

---

### Post by jualin on 2008-08-01
> **Vivaldi Gloria said:**
> For installing programs use

system menu > admin > synaptic

Also enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies.

Those are always pretty good to have in a machine. Also you will need to install Adobe Flash Player. It's called flashplugin-nonfree. And you can install it by > sudo apt-get install flashplugin-nonfree or by Synaptic as suggested above

---

### Post by jooking on 2008-08-01
thanks for the help. can anyone help me in getting and installing awn or cairo? i already tried for cairo and couldnt, so i would prefer awn. thanks

---

### Post by rossjman1 on 2008-08-01
I will list some apps I have on my computer that arn't installed by default:
**Accessories**
* Mousepad - a simple notepad clone (smaller and faster than GNOME's gedit)
* Thunar - a simple file browser
**Games**
* Enemy Territory - An awesome free FPS (also avail for Windows and Mac)
* FreeCiv - Sid Meier Civilization clone
* Icy Tower (through Wine) - Simple game for Windows that works perfict in Wine
* LinCityNG - a SimCity clone
* WideLands - a Settlers 2 clone
**Graphics**
* GNUpaint - a MS Paint clone that is perfict for simple image editing/resizing.
**Internet**
* Gmail Notify - resides in the system tray and alerts you if you have new email in your Gmail account
**Office**
* NoteCase Notes Manager - If you take your laptop to lectures, this is a handy tool to have
**Programming**
* Eclipse
* NetBeans IDE
**Sound and Video**
* Amarok - the best media player for Linux
* DeVeDe - allows you to convert avi files into iso images to burn on DVDs aswell as other things
* Hydrogen - make some beats (somewhat like garage band)
* VLC Media Player - the best video player for Linux
**System Tools**
* VirtualBox - allows you to run other OS inside Linux

> **jooking said:**
> thanks for the help. can anyone help me in getting and installing awn or cairo? i already tried for cairo and couldnt, so i would prefer awn. thanks
[http://ubuntuforums.org/showthread.php?t=762363&page=26](http://ubuntuforums.org/showthread.php?t=762363&page=26)

---

### Post by jualin on 2008-08-01
For Cairo you can [take a look here]("https://help.ubuntu.com/community/CairoDock"). And for AWN you can install it using Synaptic, the package is called avant-window-navigator. You can also use the terminal > sudo apt-get install avant-window-navigator. I prefer Cairo better because it runs faster but is your choice. After you install either one you have to tell your computer to run it everytime it turns on. You can do this by going to System, Preferences, Sessions and adding one with the command **avant-window-navigator** (for AWN) or **cairo-dock** (for Cairo). Hope this helps.

---

### Post by rossjman1 on 2008-08-01
> **jualin said:**
> For Cairo you can [take a look here]("https://help.ubuntu.com/community/CairoDock"). And for AWN you can install it using Synaptic, the package is called avant-window-navigator. You can also use the terminal . I prefer Cairo better because it runs faster but is your choice. After you install either one you have to tell your computer to run it everytime it turns on. You can do this by going to System, Preferences, Sessions and adding one with the command **avant-window-navigator** (for AWN) or **cairo-dock** (for Cairo). Hope this helps.
Do not install AWN through the default repositories, use the link i posted. The one in the official repositories don't have applets, which means that AWN can ONLY act as a taskbar.

---

### Post by jualin on 2008-08-01
> **rossjman1 said:**
> Do not install AWN through the default repositories, use the link i posted. The one in the official repositories don't have applets, which means that AWN can ONLY act as a taskbar.

True, I forgot about that, Thank you!

---

