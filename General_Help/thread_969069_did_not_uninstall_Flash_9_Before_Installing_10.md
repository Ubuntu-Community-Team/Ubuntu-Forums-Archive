---
title: "did not uninstall Flash 9 Before Installing 10"
date: 2008-11-03
forum: General Help
---

### Post by skitter.rusty on 2008-11-03
I heard flash 10 fixes some bugs and I just went straight to the Adobe site, downloaded and installed. Then I realized that no flash objects were appearing. I then found out That I had to uninstall flash 9. I have tried 

```
$ sudo apt-get remove flashplugin-nonfree
```

But it doesn't work and I just want to delete flash altogether and get flash 10. How can I do this? I use flash everyday for streaming but this has stuffed me up.

Running Ubuntu 8.04

---

### Post by NilsE on 2008-11-03
Go into Synaptic Package Manager and search for the work flash and remove anything that is installed.  Then you can install the deb from Adobe.

---

### Post by skitter.rusty on 2008-11-04
I now have uninstalled Flash 9 but I can not seem to get Flash 10 to work. I click install from the .deb and it tells me te current version has already been installed. Flash does not appear in the plugins section of Firefox either. libflash-mozplugin.so still appears in /usr/lib/mozilla.

---

### Post by NilsE on 2008-11-05
> **skitter.rusty said:**
> I now have uninstalled Flash 9 but I can not seem to get Flash 10 to work. I click install from the .deb and it tells me te current version has already been installed. Flash does not appear in the plugins section of Firefox either. libflash-mozplugin.so still appears in /usr/lib/mozilla.
Go back into Synaptic and make sure any package that has flash in the name is "completely removed" including the Mozilla plugin.  Then search the drive for anything with flash in it and ends with .so and delete it.  Check the FF plugins again to make sre nothing for flash shows then try to install 10 again.

---

### Post by skitter.rusty on 2008-11-08
> **NilsE said:**
> Go back into Synaptic and make sure any package that has flash in the name is "completely removed" including the Mozilla plugin.  Then search the drive for anything with flash in it and ends with .so and delete it.  Check the FF plugins again to make sre nothing for flash shows then try to install 10 again.
Removed all files with the word flash and ending with .so. Uninstalled everything completely with the Synaptic File Manager but it does STILL not work. Flash 10 is kind of important for me and is a hastle for me to boot into Windows everytime I need it.

---

### Post by kostkon on 2008-11-08
Go to *Synaptic* and install again the *flashplugin-nonfree* package. Hit *Apply*. After installing it, select it for *Complete Removal* and hit *Apply* again.

Then search for the *adobe-flashplugin* package. If it is installed, select it for *Complete Removal* too. Hit *Apply* (obviously).

After doing the above close *Synaptic*. Double click on the deb that you have downloaded from Adobe and install it.

You should then have a working *Flash*.

---

### Post by SPr on 2008-11-08
> **skitter.rusty said:**
> Removed all files with the word flash and ending with .so.

/usr/lib/openoffice/program/libflash680li.so I hope you didn't delete all of them. (That's in Debian and I assume it will be the same for Ubuntu).

Download the .tar.gz file from Adobe. Copy the libflashplayer.so from the archive and stick it in one or all of the directories mentioned above. This PC only has one user so I put it in ~/.mozilla/plugins. It doesn't need uninstalling or installing.

---

### Post by skitter.rusty on 2008-11-08
> **kostkon said:**
> Go to *Synaptic* and install again the *flashplugin-nonfree* package. Hit *Apply*. After installing it, select it for *Complete Removal* and hit *Apply* again.

Then search for the *adobe-flashplugin* package. If it is installed, select it for *Complete Removal* too. Hit *Apply* (obviously).

After doing the above close *Synaptic*. Double click on the deb that you have downloaded from Adobe and install it.

You should then have a working *Flash*.
Installed Flash Plugin-nonfree and it uninstalled adobe-flashplugin for me automatically. Did not work. Websites still tell me I need flash.

---

### Post by skitter.rusty on 2008-11-08
> **SPr said:**
> /usr/lib/openoffice/program/libflash680li.so I hope you didn't delete all of them. (That's in Debian and I assume it will be the same for Ubuntu).

Download the .tar.gz file from Adobe. Copy the libflashplayer.so from the archive and stick it in one or all of the directories mentioned above. This PC only has one user so I put it in ~/.mozilla/plugins. It doesn't need uninstalling or installing.
Ya. I kinda did delete /usr/lib/openoffice/program/libflash680li.so. I was reluctant because is was in openoffice but I did so anyway. What does it do?

---

### Post by skitter.rusty on 2008-11-08
> **SPr said:**
> /usr/lib/openoffice/program/libflash680li.so I hope you didn't delete all of them. (That's in Debian and I assume it will be the same for Ubuntu).

Download the .tar.gz file from Adobe. Copy the libflashplayer.so from the archive and stick it in one or all of the directories mentioned above. This PC only has one user so I put it in ~/.mozilla/plugins. It doesn't need uninstalling or installing.
Also tried what you suggested but did not work either

---

### Post by kansasnoob on 2008-11-08
At terminal:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

Then go here and reinstall the flash 10 .deb:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Then restart Firefox by going to File > Quit, and then restart Firefox!

---

### Post by skitter.rusty on 2008-11-08
> ```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

Do I **really** have to download a package **That Large** just to get **Flash Working?**. I have a slow 512kbps connection here in Australia.

> ```
sudo apt-get remove --purge flashplugin-nonfree
```

Already Removed

> ```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

:~/.mozilla$ rm flashplayer.xpt libflashplayer.so
rm: cannot remove `flashplayer.xpt': No such file or directory
rm: cannot remove `libflashplayer.so': No such file or directory

> Then go here and reinstall the flash 10 .deb:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Then restart Firefox by going to File > Quit, and then restart Firefox!

Still Doesn't work :confused:

---

### Post by skitter.rusty on 2008-11-08
> **SPr said:**
> /usr/lib/openoffice/program/libflash680li.so I hope you didn't delete all of them. (That's in Debian and I assume it will be the same for Ubuntu).

Download the .tar.gz file from Adobe. Copy the libflashplayer.so from the archive and stick it in one or all of the directories mentioned above. This PC only has one user so I put it in ~/.mozilla/plugins. It doesn't need uninstalling or installing.
Just realized that what you said gave me this:

[IMG]http://farm4.static.flickr.com/3231/3014532824_3f389a6225_b.jpg[/IMG]

Default Plugin??

---

### Post by SPr on 2008-11-09
Never seen that before... This is what I have in about: plugins on IceWeasel (FireFox):
```

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

```
(I restored a back up yesterday after hitting "enter" too soon in a terminal :D which is why flash is out of date.)
I wonder if Firefox is looking in the wrong places for it. Have you tried uninstalling and reinstalling FireFox? Or renaming ~/.mozilla to ~/.mozilla_old so Firefox has to rebuild the directory? (Renaming it backs up the directory so it's still there if needed.)

If that fails what does
```

sudo updatedb
locate libflashplayer.so

```
give? Apart from that I'm out of ideas, sorry.

---

### Post by skitter.rusty on 2008-11-10
I was kind of wondering why whenever I see someone talking about the mozilla folder, they put *.mozilla*. Is that what it is meant to be named or is that just some odd thing. I do seem to remember seeing a folder called .mozilla somewhere? My folder is just called mozilla.

---

### Post by skitter.rusty on 2008-11-10
Double Post, Soory

---

### Post by SPr on 2008-11-11
~/.mozilla is a hidden folder. All files and directories with a dot prefix are hidden. ~/.mozilla contains the Firefox settings for your account. In Nautilus hit ctrl+h to view hidden dirs.

---

### Post by skitter.rusty on 2008-11-13
I think I know what's wrong! I have no **Flashplayer.xpt** file. Would it be possible for someone to upload theirs for me to use? Or would that not work?

---

### Post by SPr on 2008-11-13
> **skitter.rusty said:**
> I have no **Flashplayer.xpt** file.

Neither do I and flash works for me.

[http://my.opera.com/lounge/forums/findpost.pl?id=2496471](http://my.opera.com/lounge/forums/findpost.pl?id=2496471) according to this the latest versions of Flash for Linux don't use an .xpt file.

---

### Post by skitter.rusty on 2008-11-21
I have had to go back to Flash 9 for now until I really need 10.

---

### Post by SPr on 2008-11-23
Well, I honestly can not think what has happened with your system. When I upgraded to flash 10 I simply extracted the libflashplayer.so from the archive and replaced the version 9 libflashplayer.so with it.

It would be nice to know if it is just your PC or if others are having the same problem.

---

### Post by dlawb on 2008-11-26
I had a very similar problem and had to switch to Opera from Firefox.

Opera worked a lot better, but still not perfect.

---

### Post by skitter.rusty on 2008-11-26
> **dlawb said:**
> I had a very similar problem and had to switch to Opera from Firefox.

Opera worked a lot better, but still not perfect.
Flash 10 wouldn't work in Opera either. Flash 9 will have to do, but if anyone finds the solution, happy to try it.

---

