---
title: "Problem with burning cd/dvd"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by ubDed on 2007-08-23
First: I'm amateur in ubuntu stuff, second: my english is kinda poor.

So, I can't erase any cd-rw or dvd+rw dvd-rw and also I can't burn any disc because always error pop-ups at 40-50%.
Now I'm using gnomebaker on my Phillips DVD+-RW SDVD8441 recorder (recorder is for laptops, I've tested it on Windows XP and it works perfectly).
Here's some stuff from console, when i've tried to erase data on DVD-RW

ded@ded-laptop:~$ sudo gnomebaker

(process:22863): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

*



 * (gnomebaker:22863): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:22863): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnomebaker:22863): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed




Help??

---

### Post by CheeseEatingBulldog on 2007-08-25
I have this exact same problem, and have had for the past 2 weeks. 

```
bulldog@ifrit:~$ gnomebaker

(process:11195): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.
*** stack smashing detected ***: gnomebaker terminated
Aborted (core dumped)
bulldog@ifrit:~$ 

```

I have tried reinstalling, completely removing, different versions...but all have no effect.

---

### Post by CheeseEatingBulldog on 2007-09-07
BUMP

Is there nobody else who has this problem? Is there any way to fix it? I have tried completely removing and reinstalling, but it just won't launch.

---

### Post by chrome307 on 2007-09-07
The only suggestion I can give you is to try using K3b instead - I use it with NEC DVDRW drive and it works straight out the box.

```


http://k3b.plainblack.com/

Screenshots:

http://k3b.plainblack.com/screenshots


```

I'm using Feisty Fawn - Gnome desktop

---

