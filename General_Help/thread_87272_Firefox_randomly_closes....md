---
title: "Firefox randomly closes..."
date: 2005-11-07
forum: General Help
---

### Post by allroz on 2005-11-07
Ill be surfing the web when all of a sudden firefox just closes without reason. There will be no warnign at all. I've tried uninstalling and reinstalling using ```
 sudo apt-get remove mozilla-firefox 
``` and then reinstalling by ```
sudo apt-get install mozilla-firefox
``` . It doens't seem to work. Also, when i supposedly uninstall firefox, i am still able to click the icon and surf the web, but it closes out even more. Anyone have any ideas?

---

### Post by 23meg on 2005-11-07
Are you using the version that shipped with Breezy? Did you dist-upgrade to Breezy? Try launching Firefox from terminal and see if any error messages are reported there during crashes.

Btw, mozilla-firefox is a dummy package. If you want to reinstall Firefox, the package name is "firefox".

---

### Post by daigorobr on 2005-11-07
I had frequent random closes with Firefox, be it 1.5 or 1.0.7.
Then the light came to me and told me to remove Totem from the plugins list.
It worked as a charm and now I know the taste of stability.

```
cd $HOME/.mozilla/plugins/
rm -rf *totem*
```

Ah!
And it helps to install mplayer firefox plugins too!
```
sudo apt-get install mplayer-nogui mozilla-mplayer
```

---

### Post by eyebrowman92 on 2005-11-07
i was having the same problem but the mplayer replacment helped! thanks.

---

### Post by dtfinch on 2005-11-07
On mine I also use the flashblock extension, allowing me to selectively view the flash movies I want. Flash is sometimes buggy, and occasionally crashy. I've also had crashes caused by Sun's Java plugin.

If the problem is easily reproduceable, you can try running firefox from the command line in order to see the error message it gives when it quits.

---

### Post by majed on 2005-11-08
Check this out: [http://ubuntuforums.org/showthread.php?t=84669]("http://ubuntuforums.org/showthread.php?t=84669")

---

### Post by eyebrowman92 on 2005-11-08
out of curiosity, why does totem force firefox to quit?

---

### Post by daigorobr on 2005-11-08
Nice question... :-)

---

### Post by Ubuntu Maniac on 2005-11-08
thats been happening to me also and i also made the switch to mplayer from totem and firefox has been fine.

---

### Post by allroz on 2005-11-08
This is the error that i keep getting:

```
WriteReady
Write
DestroyStream
Destroy
NP_Shutdown
NP_Initialize
New
SetWindow
SetWindow
Destroy
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 156 error_code 165 request_code 143 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by allroz on 2005-11-09
Anyone?

---

### Post by allroz on 2005-11-14
Still having problems.

---

### Post by dtfinch on 2005-11-14
Go to the command line and type "locate mozilla/plugins".
On mine, I get the following:
/usr/lib/mozilla/plugins
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libnpsoplugin.so
/usr/lib/mozilla/plugins/flashplayer.xpt
/usr/lib/mozilla/plugins/libjavaplugin_oji.so
/usr/lib/mozilla/plugins/libnullplugin.so
/home/david/.mozilla/plugins
/home/david/.mozilla/plugins/flashplayer.xpt
/home/david/.mozilla/plugins/libflashplayer.so

You can get a similar list by entering the url "about:plugins"

Also, if maybe it's an issue with your preferences, you can try "mv ~/.mozilla ~/.oldmozilla" to start with a fresh profile.

---

### Post by aysiu on 2005-11-14
If it's Flash-related, Arnieboy has a fix for it [in this thread](http://ubuntuforums.org/showthread.php?t=89827&highlight=arnieboy).

If not, you may want to try simply renaming /home/allroz/.mozilla to /home/allroz/.mozilla_backup and then relaunching Firefox. **Note**: I said *rename*, not copy.

---

### Post by Drifter on 2005-11-15
Firefox closes with no warning and I am back at the desktop and nothing else.  Have to get back online again.  This does not happen often and it is when I am in the forum and it seems to happen when I am using the slidebar to the right to make page go up or down.  I used annieboy's fix for flash and tried some others.  This is what my mozilla plugins look like:

david@ubuntu5:~$ locate mozilla/plugins
/usr/lib/mozilla/plugins
/usr/lib/mozilla/plugins/mplayerplug-in.so
/usr/lib/mozilla/plugins/nppdf.so
/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
/usr/lib/mozilla/plugins/mplayerplug-in.xpt
/usr/lib/mozilla/plugins/mplayerplug-in-wmp.xpt
/usr/lib/mozilla/plugins/mplayerplug-in-qt.so
/usr/lib/mozilla/plugins/mplayerplug-in-qt.xpt
/usr/lib/mozilla/plugins/mplayerplug-in-rm.so
/usr/lib/mozilla/plugins/mplayerplug-in-rm.xpt
/usr/lib/mozilla/plugins/mplayerplug-in-gmp.so
/usr/lib/mozilla/plugins/mplayerplug-in-gmp.xpt
/home/david/.mozilla/plugins
/home/david/.mozilla/plugins/flashplayer.xpt
/home/david/.mozilla/plugins/libflashplayer.so

What do u think is causing this, for now that is my only problem Breezy seems to be outstanding for me.
I also uninstalled totem and installed mplayer

---

### Post by allroz on 2005-11-20
Anything??

---

### Post by bluemax on 2006-05-03
I've been having this same problem with the latest Dapper build. At first I thought it was Flash so I uninstalled Flash. Then someone said it might be a corrupt profile so I started a new Firefox profile. Still the problem persists. This is a MAJOR bug. Does anyone know what's going on?

---

### Post by bluenova on 2006-05-03
Same problem on my girlfriends laptop. It used to happen with Fedora Core 4, reinstalled with Ubuntu 5.10 same problems. Terminal shows no errors. My computer has pretty much the same setup but it's never happened to me. strange :-?

---

### Post by Kobalt on 2006-05-03
Same problem after installing a dapper beta 2 amd64 version. FF crashes randomly. It was worse with the flahsplugin installed from synaptic, since there's no flashplugin-nonfree for 64 bits architectures, and after I removed it, it crashed less often but still crashed from time to time. 
One thing I also have is FF stucked : I can't type anything in the address bar or the google bar, even though browsing the current web page works... Only thing I can do is restart FF and then it works. 

Really anoying bug, yeah :( I hope it will be fixed in the dapper final version.

---

### Post by Biffy on 2006-05-03
From a newsforge review:

> I kept running up against this first release nature of Ubuntu. For instance, sometimes Firefox would randomly just disappear. I do not know whether this is a Firefox problem or a Ubuntu problem, but since it never happened to me in SUSE or Mandrake or even (gasp!) Windows, I suspect it's Ubuntu.

This is happening for me too. Not often tough, and i've switched to Epiphany and it has not "blinked out" for me yet.

I am just curious if the devs of Ubuntu are informed of this bug, so that it might be fixed.

---

### Post by bluenova on 2006-05-04
I don't think it's an ubuntu thing, the exact same thing was happening with Fedora Core 4 with my girlfriends laptop. It's more likely a certain plug-in that's causing it, like totam. Since running automatix on the laptop the problem has not happened again.

---

### Post by Biffy on 2006-05-04
[QUOTE=bluenova]I don't think it's an ubuntu thing, the exact same thing was happening with Fedora Core 4 with my girlfriends laptop. It's more likely a certain plug-in that's causing it, like totam. Since running automatix on the laptop the problem has not happened again.[/QUOTE]

It's not Totem. I have never used the totem-plugin.

---

### Post by Kobalt on 2006-05-04
[QUOTE=Biffy]
This is happening for me too. Not often tough, and i've switched to Epiphany and it has not "blinked out" for me yet.
[/QUOTE]

On my dapper beta 2 for amd64 Epiphany has the same problem of random closing...
And neither did I use the totem-plugin, I removed it to install the mplayer one. No effects...

---

