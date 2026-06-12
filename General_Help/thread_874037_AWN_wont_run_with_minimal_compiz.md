---
title: "AWN wont run with minimal compiz"
date: 2008-07-29
forum: General Help
---

### Post by markp1989 on 2008-07-29
on my dekstop, im running compiz-fusion as a stand alone WM (no gnome or kde)

trying to run AWN but it doesn't work

I tried running it from the terminal 

and i get this out put 

```
mark@markspc:~$ avant-window-navigator

** (avant-window-navigator:8111): WARNING **: Failed to make connection to session bus: Failed to execute dbus-launch to autolaunch D-Bus session

** (avant-window-navigator:8111): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:8111): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:8111): WARNING **: There was an error requesting the name: (null)

** (avant-window-navigator:8111): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed
Screen is composited.

** (avant-window-navigator:8111): WARNING **: Failed to make connection to session bus: Failed to execute dbus-launch to autolaunch D-Bus session
Segmentation fault
mark@markspc:~$ 

```

any one know why this is? and how to fix it?

Thanks Markp1989

---

### Post by moonbeam on 2008-07-29
> **markp1989 said:**
> on my dekstop, im running compiz-fusion as a stand alone WM (no gnome or kde)

trying to run AWN but it doesn't work

I tried running it from the terminal 

and i get this out put 

```
mark@markspc:~$ avant-window-navigator

** (avant-window-navigator:8111): WARNING **: Failed to make connection to session bus: Failed to execute dbus-launch to autolaunch D-Bus session

** (avant-window-navigator:8111): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (avant-window-navigator:8111): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:8111): WARNING **: There was an error requesting the name: (null)

** (avant-window-navigator:8111): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed
Screen is composited.

** (avant-window-navigator:8111): WARNING **: Failed to make connection to session bus: Failed to execute dbus-launch to autolaunch D-Bus session
Segmentation fault
mark@markspc:~$ 

```

any one know why this is? and how to fix it?

Thanks Markp1989

dbus needs to be installed and a session running before starting awn.

---

### Post by markp1989 on 2008-07-29
> **moonbeam said:**
> dbus needs to be installed and a session running before starting awn.

I installed dbus-x11 and ran " /usr/bin/dbus-launch"

then tried to run it and i get this 

```

mark@markspc:~$ avant-window-navigator

** (avant-window-navigator:9649): WARNING **: Failed to make connection to session bus: Failed to connect to socket /tmp/dbus-XTxtMZSauT: Connection refused

** (avant-window-navigator:9649): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed


** (avant-window-navigator:9649): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (avant-window-navigator:9649): WARNING **: There was an error requesting the name: (null)

** (avant-window-navigator:9649): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed
Screen is composited.

** (avant-window-navigator:9649): WARNING **: Failed to make connection to session bus: Failed to connect to socket /tmp/dbus-HzM202D3pE: Connection refused
Segmentation fault
mark@markspc:~$ 
```

sorted it out, i didnt have write permision to the .dbus folder in my home dir

---

