---
title: "Firefox can't see Flash 10 plugin"
date: 2008-09-19
forum: General Help
---

### Post by stek79 on 2008-09-19
Hello guys,
   I'm trying to install the new Flash 10 RC 2 plugin.

I've downloaded it from Adobe site and then installed using the provided script.

The problem is that, despite several tries, once I open Firefox and type about:plugins, I cannot see it. And obviously no flash site works.

I've tried to put the libflash shared object close to everywhere with no luck!

- .mozilla/plugins
- /usr/lib/mozilla/plugins
- /usr/lib/firefox/plugins
- etc

I'm using Hardy, up-to-date. I've previously removed any flash package. If I install swfdec, then I correctly get swfdec flash plugin in Firefox.

Anyone had this problem? Any hints?

Thanks in advance

---

### Post by Nepherte on 2008-09-19
/usr/lib/mozilla/plugins should be the correct place to put it. Do you run a 64 version of Ubuntu?

---

### Post by stek79 on 2008-09-19
Hi,
 I have the 32 bit one.

---

### Post by ddarsow on 2008-09-19
I have several machines running Firefox on Ubuntu. On one of my kids' desktops I had the same trouble and ended up having to to install to:

- [B]/usr/lib/mozilla-firefox/plugins
[/B]
Hope that works for you too. I am not sure why, as all my other machines I installed to - [COLOR="Black"]**/usr/lib/mozilla/plugins**[/COLOR] with no trouble?

---

### Post by stek79 on 2008-09-20
Hi,
 thanks for the suggestion, but it didn't work.

---

### Post by mb_webguy on 2008-09-20
Uninstall it -- if you still have the makefile from where you installed it, you should be able to uninstall it with "sudo make uninstall" -- and install the version in the backports repository (check my signature).

---

### Post by stek79 on 2008-09-20
> **mb_webguy said:**
> Uninstall it -- if you still have the makefile from where you installed it, you should be able to uninstall it with "sudo make uninstall" -- and install the version in the backports repository (check my signature).

Thanks,
     are these packages the new Flash 10 Rc2 player?

---

### Post by mb_webguy on 2008-09-20
> **stek79 said:**
> Thanks,
     are these packages the new Flash 10 Rc2 player?

It's Flash 10.0.0 d569.  I don't know which release candidate it is, but I use it and it's very stable.

---

### Post by stek79 on 2008-09-20
> **mb_webguy said:**
> It's Flash 10.0.0 d569.  I don't know which release candidate it is, but I use it and it's very stable.

Thanks.

I did what you said, but the flash installed is version 9:

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

This is the installed package:

Get:1 [http://sm.archive.ubuntu.com](http://sm.archive.ubuntu.com) hardy-backports/multiverse flashplugin-nonfree 10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2 [18.8kB]

Why is that?

---

### Post by mb_webguy on 2008-09-20
Mine's listed as     ```
File name: /usr/lib/flashplugin-nonfree/libflashplayer.so
    Shockwave Flash 10.0.0 d569
```
And that's how I installed it.  Did you completely uninstall all previous versions of Flash before you installed it?  Sometimes not all files are deleted, and you have to manually delete them.  Use the command "sudo / -name flashplaye*" to locate all files and folders related to Flash.  Delete anything that looks like it probably doesn't belong to something else, especially if it's in a mozilla directory.

---

### Post by stek79 on 2008-09-20
Hi,
 as you can see from the package name, it refers to flash 9: "really9.0.124"

Also I've seen in the terminal that the package downloaded from Adobe site is flash 9, not 10.

So it's the package that actually install flash 9!

What do you get by running dpkg like that?

ste@ste-ubuntu:~$ COLUMNS=200 dpkg -l *flash*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                         Version                                      Description
+++-============================================-============================================-========================================================================================================
un  flashplayer-mozilla                          <none>                                       (no description available)
un  flashplugin                                  <none>                                       (no description available)
ii  flashplugin-nonfree                          10.0.1.218+10.0.0.525ubuntu1~hardy1+really9. Adobe Flash Player plugin installer
pn  flashplugin-nonfreebeta                      <none>                                       (no description available)
un  libflash-mozplugin                           <none>                                       (no description available)
pn  libflashsupport                              <none>                                       (no description available)

Thanks

---

### Post by steveneddy on 2008-09-20
You must uninstall the old version first.

Once uninstalled, just follow the directions again.

---

### Post by loafing on 2008-09-20
> **mb_webguy said:**
> Mine's listed as     ```
File name: /usr/lib/flashplugin-nonfree/libflashplayer.so
    Shockwave Flash 10.0.0 d569
```
And that's how I installed it.  Did you completely uninstall all previous versions of Flash before you installed it?  Sometimes not all files are deleted, and you have to manually delete them.  Use the command "sudo / -name flashplaye*" to locate all files and folders related to Flash.  Delete anything that looks like it probably doesn't belong to something else, especially if it's in a mozilla directory.
I had try all the methods above, but it didn't take effect.It seems that Firefox can't recognize the Flash 10 plugin.
Any advice would be greatly appreciated!!!

---

### Post by daniel83mk on 2008-09-20
Same here!
It recognizes libflashplayer.so from install_flash_player_9_linux.tar.gz, but can not recognize it from flashplayer10_install_linux_091508.tar.gz!

---

### Post by chapterthree on 2008-09-20
I managed to get Flash 10.0 r12 (which should be 10 RC2) working, but unfortunately I ended up bruteforcing my way through, so I don't have exact steps to follow.  I am using nspluginwrapper 0.9.91.5-2ubuntu2 from the Ubuntu repos.

Basically I ended up putting a symlink to libflashplayer.so in every mozilla/firefox related directory I could find in /usr/lib/.

For what it's worth, here's a picture of the mess I have (but a working mess :))```
chapterthree@home:~$ sudo locate libflashplayer
/home/chapterthree/.mozilla/plugins/libflashplayer.so
/home/chapterthree/downloads/install_flash_player_10_linux/libflashplayer.so
/home/chapterthree/src/install_flash_player_10_linux/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
/usr/lib/xulrunner-addons/plugins/libflashplayer.so
```

```
chapterthree@home:~$ sudo nspluginwrapper -v -l
List plugins in /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
List plugins in /usr/lib64/mozilla/plugins
Looking for plugins in /usr/lib64/mozilla/plugins
List plugins in /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins
List plugins in /usr/lib64/firefox/plugins
Looking for plugins in /usr/lib64/firefox/plugins
List plugins in /root/.mozilla/plugins
Looking for plugins in /root/.mozilla/plugins
```

Sorry I can't be of more definitive help, this Flash crap has been driving me nuts for so long that I've stopped trying to do things methodically and just started brute forcing things. :)

I can say that so far, Flash 10 RC2 is a dream.  No more Firefox crashes, and the plugin reliably loads.

---

### Post by mb_webguy on 2008-09-20
> **chapterthree said:**
> I can say that so far, Flash 10 RC2 is a dream.  No more Firefox crashes, and the plugin reliably loads.

Sorry it took you so much time and effort to get here, but I figured you'd think it worth it in the end.  The Flash 10-ok-so-it's-a-release-candidate-and-not-really-10 plugin has been great for me.  Since I've installed it, I've experienced none of the problems with Flash I see reported on this board every day, and I can even watch Flash videos in full-screen, which I was never able to do with the Flash 9 plugin!

---

### Post by daniel83mk on 2008-09-20
OK, this worked for me
Copy libflashplayer.so to /usr/lib/firefox-addons/plugins and then:
sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so

---

### Post by chapterthree on 2008-09-20
> **mb_webguy said:**
> and I can even watch Flash videos in full-screen, which I was never able to do with the Flash 9 plugin!

Good one, forgot to mention that, which was a big one for me.  I've always had choppy fullscreen playback with 9 and all of the 10 betas/rcs up until 10 RC2.  I now have smooth fullscreen playback on 10 RC2 (resolution is 1680x1050).  10 RC2 finally seems like it's heading in the right direction.

---

### Post by loafing on 2008-09-22
> **daniel83mk said:**
> OK, this worked for me
Copy libflashplayer.so to /usr/lib/firefox-addons/plugins and then:
sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so

Thanks daniel83mk it has exactly solved my proplem.

---

### Post by fragos on 2008-09-22
I installed 10 using the backports and Synaptic. about:plugins still reports 9 and Synaptic says 10 is installed. I tried uninstalling before installing but get the same results. Is about:plugins reporting the correct version? My N810 has a bug where flash 9 r48 reports as 9 r31. A patch came out to fix the reporting in about:plugins on the N810.

---

### Post by chapterthree on 2008-09-22
Here is what my about:plugins show.

---

### Post by stek79 on 2008-09-24
> **fragos said:**
> I installed 10 using the backports and Synaptic. about:plugins still reports 9 and Synaptic says 10 is installed. I tried uninstalling before installing but get the same results. 

Same for me. For some reason this Flash 10 plugin does not work. Flash 9 works, swfdec works too, but 10 not :(

---

### Post by jg1395 on 2008-09-25
mine was working, then i rebooted and it reverted back to flash 9.  :(

probably just need to search and delete all instances of it... grrrr, oh well.

it was working sweet for a while, i'm not messing with it tonight.

---

### Post by stek79 on 2008-10-17
Hello guys,
  last night I tried the new flash 10 final, installing the deb directly from Adobe site.

Conclusion: the same, Firefox can't see it!

Any other with this problem?

---

### Post by nekroskoma on 2008-10-17
EDIT: im just going to make a new thread for my problem

---

### Post by jspiers on 2008-10-17
Hi guys.  I had the same problem, lots of FF crashes with Flash version 9, needed to upgrade to version 10 but it hasn't shown up as an automatic upgrade.  I'm not a hardcore hacker or anything and I like to let the synaptic package manager do my upgrades, but the problem is that flashplugin-nonfree version 10 is not in the regular repository. Luckily I found another thread on ubuntuforums where someone said to use the "backports" repository.  Once you tell synaptic to use the backports repository, you can install version 10 automatically (no hacking necessary):

Open "System > Administration > Synaptic Package Manager"
Go to "Settings > Repositories"
Click on "Updates" tab
Check the "Unsupported updates (hardy-backports)" box
Now "Reload" the package information from the repositories
"flashplugin-nonfree" version 10 should now appear.

I hope this helps someone.  Long live ubuntuforums!

---

### Post by AzureCerulean on 2008-12-10
I tried ALL of these methods to no avail.  I did however find another article and tried the methods there:

[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html")

ultimately the Script they provided did the trick for me.

--- start script here ---

#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
tar zxvf install_flash_player_10_linux.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"


--- end script here  ---

you may save this to a text file then execute it you may need to change permissions or use sh to run it.

it may be run as a non root user.

Best of luck.

---

### Post by irolav on 2009-02-25
> **daniel83mk said:**
> OK, this worked for me
Copy libflashplayer.so to /usr/lib/firefox-addons/plugins and then:
sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so

Thank you very much, this worked for me.
Actually the links were correct but I had to copy the file.

Marco

---

### Post by Daverobb on 2009-03-01
you could try this - i had a similar problem and this got it going for me (altho now I'm into a choppy playback problem on some sites) but ...

1. ```
sudo apt-get remove --purge flashplugin-nonfree
```

2. open synaptic and search for the following entry -- ubuntu-restricted-extras -- uncheck if it is selected it contains a conflict for the flash player

3. reinstall the flash player from adobe using the .deb file

4. restart firefox and check

---

