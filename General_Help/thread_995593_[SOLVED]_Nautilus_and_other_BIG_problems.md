---
title: "[SOLVED] Nautilus and other BIG problems"
date: 2008-11-28
forum: General Help
---

### Post by CommieTechie on 2008-11-28
Ok, forgive me if I'm doing this all wrong, but I really need some big time help. I've been using ubuntu for about 6 months now, and I normally can fix most things myself, or if I can't, I check on here and someone else has already had the same problem and fixed it. However, I can't find anything that seems to match what I have.

Sorry for what will be a long rambling paragraph, but I did a lot before this happened and I'm not sure which might have caused it.

Tonight I went to set up my internal microphone to use with skype. I have attempted it before but only halfheartedly, never really looking too deeply into the problem. I have a Toshiba Satellite A215-S4747. I eventually found what seemed like a fix. it involved installing several new items though synaptic. Unfortunatly, due to my AMAZING memory, I forget which exactly.

I believe it is either  linux-ubuntu-modules-2.6.24-16-generic   or   linux-headers-2.6.24-16-generic

I also played with several ALSA settings, and installed esound. I then installed skype, and my microphone did indeed work now. (hooray)

I then went to access my external HD. a western digital 750gb. formerly fat32 until I reformatted it to ext3. I used an "open as root" script through nautilus' right click > scripts menu, only the unlock dialogue never presented itself. I didn't think much of it and went to restart the computer.

when it booted up, several things I noticed were wrong. First, my conky script showing statistics about my external HD was displaying, although the external was not shown as mounted. (in retrospect I assume this was because the external was mounted, but nautilus was not displaying the icon)

second, conky had superimposed itself over open windows, another thing that rarely if ever happened (I had a script run at startup that had conky wait 60 seconds before running, to prevent exactly that from happening)

I attempted to open nautilus, to see if my external was mounted. it did not open.

I attempted to open a terminal. It froze instantly upon opening.

fortunatly, I have AWN with terminal apps which seem to function fine, and the system monitor hotkeyed to alt+F9. so far I have been able to determine:

[LIST]
[*]Upon starting up, nautilus does run, but will not display the desktop, any icons, or folder views.
[*]gnome-mount is a zombie process if my external is plugged in at boot
[*]compiz fusion does not display advanced features or addons
[/LIST]

using the terminal apps in AWN, I have the following.

```

jmack@commiecomp:~$ nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:6957): WARNING **: Unable to add monitor: Not supported

```


```

jmack@commiecomp:~$ gksudo nautilus
Initializing nautilus-share extension

** (nautilus:7003): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSS

```

after running this Nautilus opened, as root.


```

jmack@commiecomp:~$ gksudo nautilus --debug
No ask_pass set, using default!
xauth: /tmp/libgksu-xxlCri/.Xauthority
STARTUP_ID: gksudo/nautilus/7143-0-commiecomp_TIME927097
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
butter: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
SSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
xauth: /tmp/libgksu-xxlCri/.Xauthority
xauth_env: /tmp/.gdm6HA7KU
dir: /tmp//libgksu-xxlCri

```

I tried to enable compiz as it seemed to be lacking several features

```

jmack@commiecomp:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:05.0 0300: 1002:791f (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resulution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

at time of writing, I have all processes listed as Sleeping, except for one sh listed as Zombie, located at /bin/sh -c nautilus /home/jmack


please... I have no idea where to even start with this one. I've always found answers on this forum, I hope you can help me with my own >.<

if anyone spots problems with the terminal output, its because I had to type it by hand. I was using the terminal applet for AWN because my normal terminal sessions freeze when opening



EDIT - I have found which packages I installed. They were 

linux-headers-lbm-2.6.24-22-386
linux-headers-lbm-2.6.24-22-generic

and any other dependancy packages that came with. I am going to try removing those and restarting

---

### Post by CommieTechie on 2008-11-28
bump for help ):

I uninstalled the packages however all problems still remain

---

### Post by CommieTechie on 2008-11-28
anybody? at this point I'm seriously considering just wiping everything and upgrading to 8.10 ><

---

### Post by soro2005 on 2008-11-28
In the past, I had nautilus and some other stuff freezing on a hanging sound server. You could try
```
sudo killall -9 esd
```
and
```
sudo killall -9 pulseaudio
```
depending on which one's the one that's now running. If you can't do it from the AWN terminal, perhaps you can log in at tty1 (alt+ctr+f1, alt+ctr+f7 to get back to gnome).

If that works, you know that you have to look deeper into your sound setup. There might be some conflicts now after you've done your skype setup.

Also: The headers packages are very unlikely to be the cause of your woes.

---

### Post by CommieTechie on 2008-11-28
thank you so much! the killing esd fixed it! nautilus stopped hanging, the taskbar returned, and all was well with the world! thank you!

At the very least I now know how to fix it. Do you have any thoughts as to what could have caused it?

my major changes were just I used the alsa mixer. I previously had the input sources set to Front Mic, I changed them to Mic, and Toggled audio recording from capture 1 to off. Could that really have been the cause of all that?

---

### Post by soro2005 on 2008-11-28
I don't know. You may have to make sure that you uninstall pulse if you want to use esound. There might be a conflict between the two. I'm not sure whether I recommend that, though. In any case, esound did that to me from time to time until it was replaced with pulse in Hardy. I never found out why.

I also didn't get my internal mic to work in Skype, but I didn't try hard. I use an iMic, better sound quality. However, should I ever try to figure it out, I would probably look [here](http://ubuntuforums.org/showthread.php?t=789578) for inspiration on how to get it to work with pulse.

---

### Post by CommieTechie on 2008-11-28
ok well for now I have esound uninstalled and the problem is gone. Now that I know what causes it and how to stop it, I can play around and see what works and what doesnt. Thank you so much!

---

