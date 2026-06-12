---
title: "Forgot administative password, no GRUB screen"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by veryannoyed on 2009-05-18
I got the Dell Mini 9 and when I first turned it on, I had to decide on a password. Well, I forgot it and now I can't install any updates or change any settings. All the directions online tell me to hit esc during "GRUB" loading. Well, I don't have a "GRUB" screen and, when I hit esc, I go to the bios settings. I see nothing that looks remotely like this: [http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html) or this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I'm really getting angry about this. All the step by step directions I've looked at to set a new password do not work because they all assume a GRUB loading screen, which I do not have! Can someone please help me? Thank you!

---

### Post by coffeecat on 2009-05-18
You're probably hitting esc too early. It's unfortunate that Dell chose the esc key to get into the BIOS. It's easier when it's something like delete or F2 which is what other manufacturers use.

Anyway, there is a hidden grub menu, but you've only got about 2 seconds to get into it (if it's set up like other systems - Dell may have done something different). Try booting up and watch the screen carefully. Don't try to hit esc this time; just watch. After the BIOS screen and POST messages (if any), the screen should briefly go black just before the Ubuntu orangey-brown usplash starts up. You should see (again very briefly) top left of screen, something like "GRUB - booting in 2 seconds. Press ESC" Something like that - I'm going from memory. If you press escape just at that point then you should see the GRUB menu, from which I guess you need to choose rescue mode.

Beyond this point, do you have instructions on how to reset your password?

**Edit:** OK, you posted your edit just as I was posting. The first image in your psychocats link is what you should be seeing. **But it's only on screen for a second or two**. Blink and you miss it.

---

### Post by veryannoyed on 2009-05-18
Well, I don't see a GRUB screen anywhere. Even if it's only a second or two, I'd notice it. I get a screen of some info about my computer and when I press esc, I go into bios settings. Then it says MDR and when I press esc, nothing happens. I've tried hitting esc later too, it doesn't do anything. In my bios, there was an option for a quick boot that I thought might be skipping the GRUB screen, but even when I changed my boot settings, I still don't see a GRUB screen.

Here's a video of what happens when I power on my computer: [http://www.youtube.com/watch?v=TNSVf60JycE](http://www.youtube.com/watch?v=TNSVf60JycE)

---

### Post by coffeecat on 2009-05-18
Actually, it's not a 'grub screen' you're looking for, but that "Grub loading stage 1.5.." message, but you're right - I can't see it either. Just a blinking cursor at top left for a few seconds after the MDR (haven't a clue what that is) message. Sounds like a Dell 'special'. Goodness knows what they've done.

Is this a Dell pre-loaded with Ubuntu machine? Is there anything in the handbook that might help? I can't believe they've set it up so that you can't get into recovery mode. Very odd.

Anyway, my apologies for not thinking of this before, but there's a Dell subforum [here]("http://ubuntuforums.org/forumdisplay.php?f=342"). If you want this thread moved there, just click on the report button [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] and ask a moderator to move it for you.

Oh, and a belated welcome to Ubuntu forums.

---

### Post by unutbu on 2009-05-18
Since you can boot into Ubuntu, how about try this:

Open a terminal (Applications>Accessories>Terminal) and type
```

gksu gedit /boot/grub/menu.lst
```

Around line 19 change
```

timeout		5 (<-- or whatever. Change it if it is smaller than 10)
```

to
```

timeout		10

```

Around line 23 change
```

#hiddenmenu

```
to
```

hiddenmenu
```

Save and exit gedit. Then reboot. You should now see the GRUB menu by default without having to press any key and it will stay on the screen for 10 seconds.

---

### Post by coffeecat on 2009-05-18
> **unutbu said:**
> Since you can boot into Ubuntu, how about try this:

Open a terminal (Applications>Accessories>Terminal) and type
```

gksu gedit /boot/grub/menu.lst
```

The problem with that is that the OP will need their password.

**Edit:** actually, **unutbu**'s come up with a good idea, but it would require a live CD. **veryannoyed**, if you've got (or can get hold of) a USB CD drive, and if the Dell can be configured to boot from a USB device, it's possible to download the Ubuntu live CD and use that to edit menu.lst in the way **unutbu** describes. And you won't need a password either. It's slightly more complicated from a live CD, but if that interests you, post back and someone will take you through it. It's late here so it won't be me, at least not until tomorrow.

---

### Post by aysiu on 2009-05-18
Hm. There's a way around this, but it's rather complicated.

**Step 1**
Use UNetBootIn to "burn" a Linux CD .iso to USB

**Step 2**
Boot the USB

**Step 3**
Mount your Ubuntu drive

**Step 4**
[Edit the /etc/shadow file on the Ubuntu drive so that your username will have no password](http://ubuntuforums.org/showthread.php?t=513820). Make sure you edit the /etc/shadow file of the mounted drive and not the live CD one. It'll probably be something like /media/drive/etc/shadow. And you'll need to launch Nautilus as root (*gksu nautilus*) to get privileges to edit that file.

**Step 5**
Reboot into Ubuntu and then set a new password using System > Administration > Users and Groups

---

### Post by veryannoyed on 2009-07-21
Hello. It appeared there was no easy solution and my Windows XP desktop was giving me enough problems that I didn't want to potentially mess up my only other working computer. Anyway, going back to this discussion...

Would it simply be easier to reinstall Ubuntu? I don't have data (documents, music, etc.) saved on this because it only has an 8GB SSD. So I'm not concerned about losing my data if reinstalling Ubuntu would be easier than trying to change the password. 

However, this netbook doesn't have a CD drive and I would be using the Ubuntu disc that came with it to reinstall... but how do I do that? Whether I use the disc for a complete reinstall or to recover my password, I do not have an optical drive and don't want to buy one just for this. #-o

---

### Post by aysiu on 2009-07-21
> **veryannoyed said:**
> 
However, this netbook doesn't have a CD drive So follow the instructions I gave.

But instead of booting a live CD, you boot a live USB.

You can "burn" an .iso to USB using UNetBootIn. It's available for Windows and Linux:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by veryannoyed on 2009-07-21
Double post. D'oh. See the next one.

---

### Post by veryannoyed on 2009-07-21
Well, I tried your method but I don't know how to create a new user account and I don't see the full path of the drive location. I am very unfamiliar with how Ubuntu works. I need step by step directions because I'm not going to know what to do if something is glossed over. When I type in that code you have there, all I get is "[sudo] password for user:" I don't have a password, which is the problem. I don't know what nautilus is either.

Can't I just use this mounted version to run recovery mode? I tried to boot from my USB device, but it wouldn't, it always went into the OS, even when I set removable media before the hard drive for bootup.

---

### Post by aysiu on 2009-07-21
You can run the mounted version in recovery mode, but it's a little bit tricky and involves something called *chroot*, which I'm not even that familiar with.

So step by step.

1. It seems you've successfully booted your live USB, yes?

2. Once you get the live session up, there should be three text menus in the top-left corner. One says *Applications*, one says *Places*, and one says *System*. Select **Places**.

3. The menu will drop down vertically and you'll see a bunch of places (Home, Desktop, Networks). One of these places will not actually have a name. It'll look like a silver drive and in place of a name, it'll have a size (*16 GB*, for example). That is most likely your Dell Mini's drive. Select that drive and it should automatically mount.

4. Press Alt-F2. This will get up a Run dialogue, which is a little box where you can launch commands.

5. In that box, type or paste in ```
gksudo nautilus
``` Nautilus is the name of the file manager (the Ubuntu equivalent of Windows' Explorer or Mac OS X's Finder). With the *gksudo* prefix, you're telling Ubuntu to launch Nautilus with system-wide access, so you can make modifications to the mounted drive.

6. Once you're in Nautilus, navigate up to the top-most directory by pressing the Up arrow. Then click on *media*. Within *media*, you should see a few folders. A couple will be called *cdrom*-something. Ignore those. Select the other one. It'll probably be called *disk*, but it may be called something else.

7. Inside that folder, you should see a whole bunch of folders. To make sure this is your actual drive, click into *home* and then your username, which I'll assume for the sake of this example is *veryannoyed*.

8. If everything looks good, click the Up arrow two more times to get back to /media/disk/

9. Then click on *etc* so you're in the /media/disk/etc directory

10. Inside that directory, you should see a text file called *shadow*

11. Copy shadow and paste it in the same directory and name the new file *shadow.bak*. That's a backup of the encrypted password file.

12. Open the original *shadow* file by double-clicking it.

13. It should open in a text editor. If it doesn't, and you're prompted for what application to use to open it, select *Text Editor* or use the custom command ```
gedit
```

14. You'll see a bunch of lines with a bunch of gibberish. At the beginning of each line, though, will be a username. Look for *veryannoyed* (or whatever your actual username is).

15. The line will look something like ```
veryannoyed:$1$2TUdk8Z0$tb2Fn6Idgo8dq9EgYv4xZ0:13721:0:99999:7:::
```

16. Change the gibberish so looks like ```
veryannoyed:**U6aMy0wojraho**:13721:0:99999:7:::
``` That U6aMy... stuff has to be exactly as written.

17. Save and exit the file.

18. Reboot without the live USB.

19. When you get to the login screen, your username is still *veryannoyed* (or whatever it really is), but your password will be blank, so just hit Enter for the password.

20. You can then reset your password to be whatever you want it to be by going to System > Preferences > About Me

**If you find those instructions intimidating, this video may help you feel more comfortable**:
[http://www.youtube.com/watch?v=AkENYv7kEhg](http://www.youtube.com/watch?v=AkENYv7kEhg)

---

### Post by veryannoyed on 2009-07-22
:D I got it. Thank you all! It's so exciting to be able to install new programs! 

Now, one last little question as I am probably an idiot -- where might I find new programs I install via Synaptic Package Manager? I downloaded Loderunner through Add/Remove Programs and I see that in Applications > Games, but I downloaded XMMS2 via Synaptic Manager and I don't see it anywhere, not even in Applications > Sound & Video. What do I do?

Obviously still learning my way around, but knowing I can't get a virus is a freeing feeling. \\:D/

---

### Post by aysiu on 2009-07-22
I don't know much about XMMS2, but I think it may be a command-line program, and you may have to install a graphical frontend to access it graphically. ```
*apt-cache search xmms2*
**abraca - A simple and powerful graphical client for XMMS2**
**esperanza - XMMS2 client which aims to be as feature-full and easy-to-use as possible**
gkrellxmms2 - GKrellM plugin to control xmms2
**gxmms2 - xmms2 client for the GNOME desktop**
libaudio-xmmsclient-perl - XMMS2 - perl client library
libxmmsclient++-dev - XMMS2 - client library for c++ - development files
libxmmsclient++-glib-dev - XMMS2 - glib client library for c++ - development files
libxmmsclient++-glib1 - XMMS2 - glib client library for c++
libxmmsclient++3 - XMMS2 - client library for c++
libxmmsclient-dev - XMMS2 - client library devel files
libxmmsclient-glib-dev - XMMS2 - glib client library - development files
libxmmsclient-glib1 - XMMS2 - glib client library
libxmmsclient-ruby - XMMS2 - Ruby client library
libxmmsclient-ruby1.8 - XMMS2 - Ruby bindings
libxmmsclient4 - XMMS2 - client library
pidgin-musictracker - Plugin for Pidgin which displays the current music track in your status
python-xmmsclient - XMMS2 - Python bindings
wmxmms2 - remote-control dockapp for XMMS2
xmms2 - Client/server based media player system
xmms2-client-avahi - XMMS2 - avahi client
xmms2-client-cli - XMMS2 - cli client
xmms2-client-medialib-updater - XMMS2 - medialib-updater client
xmms2-core - XMMS2 - core package
xmms2-dev - XMMS2 - plugin development files
xmms2-et - XMMS2 - phone home package
xmms2-plugin-airplay - XMMS2 - airplay output plugin
xmms2-plugin-all - XMMS2 - all plugins
xmms2-plugin-alsa - XMMS2 - ALSA output
xmms2-plugin-ao - XMMS2 - libao output plugin
xmms2-plugin-asf - XMMS2 - ASF plugin
xmms2-plugin-asx - XMMS2 - ASX playlist plugin
xmms2-plugin-avcodec - XMMS2 - avcodec decoder
xmms2-plugin-cdda - XMMS2 - CDDA plugin
xmms2-plugin-cue - XMMS2 - CUE playlist plugin
xmms2-plugin-curl - XMMS2 - curl transport for HTTP
xmms2-plugin-daap - XMMS2 - daap plugin
xmms2-plugin-faad - XMMS2 - faad decoder
xmms2-plugin-flac - XMMS2 - flac decoder
xmms2-plugin-gme - XMMS2 - gme plugin
xmms2-plugin-gvfs - XMMS2 - gvfs plugin
xmms2-plugin-ices - XMMS2 - ogg streaming output
xmms2-plugin-icymetaint - XMMS2 - shoutcast metadata plugin
xmms2-plugin-id3v2 - XMMS2 - ID3v2 plugin
xmms2-plugin-jack - XMMS2 - JACK output
xmms2-plugin-karaoke - XMMS2 - karaoke plugin
xmms2-plugin-lastfm - XMMS2 - Last.FM plugin
xmms2-plugin-m3u - XMMS2 - M3U playlist plugin
xmms2-plugin-mad - XMMS2 - libmad based mp3 decoder
xmms2-plugin-mms - XMMS2 - MMS transport
xmms2-plugin-modplug - XMMS2 - modplug decoder
xmms2-plugin-mp4 - XMMS2 - MPEG-4 plugin
xmms2-plugin-musepack - XMMS2 - mpc decoder
xmms2-plugin-normalize - XMMS2 - Normalize plugin
xmms2-plugin-ofa - XMMS2 - OFA plugin
xmms2-plugin-oss - XMMS2 - OSS output
xmms2-plugin-pls - XMMS2 - PLS playlist plugin
xmms2-plugin-pulse - XMMS2 - pulseaudio output plugin
xmms2-plugin-rss - XMMS2 - RSS podcast plugin
xmms2-plugin-sid - XMMS2 - libsidplay2 based decoder
xmms2-plugin-smb - XMMS2 - Samba transport
xmms2-plugin-speex - XMMS2 - speex decoder
xmms2-plugin-vocoder - XMMS2 - vocoder plugin
xmms2-plugin-vorbis - XMMS2 - vorbis decoder
xmms2-plugin-wma - XMMS2 - wma decoder
xmms2-plugin-xml - XMMS2 - XML plugin
xmms2-plugin-xspf - XMMS2 - XSPF playist plugin
xmms2-scrobbler - Audioscrobbler/Last.FM client for xmms2
xmms2tray - systray integration for XMMS2
```

---

### Post by veryannoyed on 2009-07-22
Ah, I guess that would help. Thank you. I thought xmms2-core - XMMS2 - core package was all I needed. I don't like this esperanza... I'll try another. :wink:

---

