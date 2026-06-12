---
title: "Noob Installed libdvdcss2 but movie players won't work"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by unckybob on 2009-07-08
Installed libdvdcss2, it made k9copy work. Then installed Kaffeine, Movie Player, MPlayer, and VLC and none of them will work. I installed them just as it says in

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Please help a noob. 

Bob

---

### Post by presence1960 on 2009-07-08
Medibutu stands for Multimedia, Entertainment & Distractions In Ubuntu and is a repository of packages that cannot be included in Ubuntu due to legal reasons. We need to add this repository to enable MP3, DVD playback, install certain codecs etc.

Take a terminal and enter:

> sudo wget [http://www.medibuntu.org/sources.list.d/](http://www.medibuntu.org/sources.list.d/)[COLOR="Red"]intrepid[/COLOR].list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Now we&#8217;ll enable all repositories (including Universe and Multiverse repositories) that Ubuntu provides. Take a terminal and enter:

    > sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list && sudo apt-get update

[U][B]Change the red word to the release you are using, i.e. hardy, intrepid or jaunty.
[/B][/U]
Playing MP3, WMA, Real and Apple QuickTime Files in Ubuntu.
Once the Medibuntu repository has been added as said above, take a terminal and enter:

For a 32 bit machine:

    sudo apt-get install w32codecs

For a 64 bit machine:

    sudo apt-get install w64codecs

For a PPC machine:

    sudo apt-get install ppc-codecs

---

### Post by unckybob on 2009-07-08
Wow, thanks for a really concise response. Unfortunately I didn't type in everything correctly. The first line I typed in: 

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt_get update 

Note the underscore instead of the - in the very last command. After realizing that I typed in: 

sudo apt-get update 

And then I typed the second command you recommended. Then I opened up Movie Player and it said: 

"Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc."

---

### Post by presence1960 on 2009-07-08
I am not familiar with totem, but it should ask you to download the plugins. if it doesn't look in the menu bar of totem for a plugin menu. Sorry I can't be of further help.

P.S. Go to System > it is either Preferences or Administration > Software Sources. Go to the Third party tab and make sure both medibuntu sources are checked. I am not in Ubuntu right now as I am logged into my Sabayon linux currently, so I can't look to be exactly sure.

Also you can copy & paste commands from the forum into the terminal so you don't mess up.

---

### Post by unckybob on 2009-07-08
Thanks again for getting back to me so quickly. 

There is a plugins option in the menus. I activated all of them: 

BBC content viewer
infrared Remote Control
Jamendo
Local Search
Python Console
Subtitles Downloader
Thumnail
Video Disc Recorder 
YouTube Browser 

Also, I have 

Kaffeine, 
Mplayer, and
VLC

installed. I don't know if it's relevant, but when I startup Kaffeine and VLC the disk drive starts humming and won't stop unless I manually open it and then close it again.

---

### Post by unckybob on 2009-07-08
Thanks again for getting back to me so quickly. 

There is a plugins option in the menus. I activated all of them: 

BBC content viewer
infrared Remote Control
Jamendo
Local Search
Python Console
Subtitles Downloader
Thumnail
Video Disc Recorder 
YouTube Browser 

I did as you said. One of the Medibuntu options wasn't checked. I checked it, then it downloaded and installed them. Same thing with Totem. Said I needed plugins. Also, I have 

Kaffeine, 
Mplayer, and
VLC

installed. I don't know if it's relevant, but when I startup Kaffeine and VLC the disk drive starts humming and won't stop unless I manually open it and then close it again.

---

### Post by unckybob on 2009-07-08
Hey, I was looking in 

[http://www.google.com/search?hl=en&lr=&q=site%3Ahelp.ubuntu.com+Totem+plugins+-Firefox&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&lr=&q=site%3Ahelp.ubuntu.com+Totem+plugins+-Firefox&aq=f&oq=&aqi=)

and what seemed to get him working was to uninstall everything having to do with libdvdss and then reinstall it. I installed libdvdcss2. How do I uninstall, I've never done that before.

---

### Post by unckybob on 2009-07-08
Did a reboot. Mplayer searched for a plugin, didn't find it. Still says it doesn't have the necessary plugin.

---

### Post by presence1960 on 2009-07-08
> **unckybob said:**
> Did a reboot. Mplayer searched for a plugin, didn't find it. Still says it doesn't have the necessary plugin.

did you go to Software sources as I mention above and make sure both medibuntu ( free & non-free) are checked? The plugins you need are non-free I believe. They are not enabled by default. I am still in Sabayon Linux but I know you can find Software Sources either in System > preferences or System > Administration.

---

### Post by unckybob on 2009-07-08
All these are checked: 

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[http://archive.canonical.com/ubuutu](http://archive.canonical.com/ubuutu) jaunty partner (Source Code)
Medibuntu - Ubuntu 9.04 "jaunty jackalope" free non-free
Medibuntu (source) - Ubuntu 9.04 "jaunty jackalobe" free non-free (Source Code)

---

### Post by unckybob on 2009-07-09
Yes, I went to "Software Sources" under "Administration" and both "free" and "non-free" Medibuntu sources are checked.

---

