---
title: "Setting up a Bluetooth printer"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by mjrwingnut on 2007-04-25
Has anyone setup a printer with bluetooth?

---

### Post by djeley on 2007-04-28
Try this...

Step 1: Install Gnome bluetooth tools (using Add/Remove...).

Step 2: Using the command line, check you can see your printer and get its address:

```
hcitool scan
```

You should see the address string of your printer (amongst other info), similar to:

```
00:0C:55:19:89:81
```

Step 3: To configure your printer with CUPS don't use the Gnome Cups Manager. This has a bug so you can't set it up with the bluetooth protocol. See: [https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/9373](https://bugs.launchpad.net/ubuntu/+source/gnome-cups-manager/+bug/9373) for more info.

Instead, go to [http://localhost:631](http://localhost:631) in your browser to use the CUPS web based admin console to add your printer. When you're required to select a device, make sure you select "Bluetooth printer". When asked to enter the device URI (if your printer's bluetooth address was the same as above) type: 

```
bluetooth://000C55198981
```

Hope that helps!

Duncan

---

### Post by azalamo99 on 2007-04-28
Your link to:
[http://localhost:631](http://localhost:631)

returned a msg stating

SERVER NOT FOUND
Firefox can't find the server at localhost.

What am I doing wrong?

---

### Post by djeley on 2007-04-28
Not too sure why that's not working for you. Check CUPS is running:

```
ps aux | grep cupsd
```

If it is, try [http://127.0.0.1:631](http://127.0.0.1:631) instead. If that doesn't work take a peek at /etc/cups/cupsd.conf. Mine says this:

```
# Only listen for connections from the local machine.
Listen localhost:631

```

You could try changing it to:

```
# Only listen for connections from the local machine.
Listen *:631

```

I'm no expert on CUPS - sorry I can't be of more help!

---

### Post by mjrwingnut on 2007-04-28
Thanks!! I finally got it working.

:)

---

