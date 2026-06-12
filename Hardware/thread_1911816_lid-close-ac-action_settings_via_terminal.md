---
title: "lid-close-ac-action settings via terminal"
date: 2012-01-19
forum: Hardware
---

### Post by zeezam on 2012-01-19
Trying to set this via ssh on my laptop:

```

sudo gsettings set org.gnome.settings-daemon.plugins.power lid-close-ac-action blanc

```

Got this response

```

** (process:9082): WARNING **: Command line `dbus-launch --autolaunch=7a82398b48ae7ae563de66580000000a --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n

** (process:9082): WARNING **: Command line `dbus-launch --autolaunch=7a82398b48ae7ae563de66580000000a --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n

```

Isn't possible to set close-ac-action via terminal?

---

### Post by jonguitud on 2012-04-13
Try it without "sudo", and obviously without logging in as root. That did the trick for me ;)

Cheers !

---

