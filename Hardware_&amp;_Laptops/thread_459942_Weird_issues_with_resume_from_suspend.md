---
title: "Weird issues with resume from suspend"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by endlesssnowfall on 2007-05-31
I have a Thinkpad R50e that was resuming from suspend flawlessly in Edgy and Dapper, but now with Feisty, it only works well about 60% of the time, and the rest of the time it has some very weird issues.

1. Sometimes on resume, the screen will be blank except for the mouse cursor.  Sometimes the area around the cursor is a bunch of garbled colors that disappear when I move the mouse. The cursor also can change to the text input cursor, presumably when I am hovering over the password entry box.  If I try to restart X using Ctrl+Alt+Backspace, I can see everything starting up again, but then it returns me to a blank screen with only the cursor.

2. Sometimes, upon resume, no network interfaces are detected at all, except for the loopback adapter.  Restarting Network Manager does nothing, ifconfig shows nothing as well.

---

### Post by linux4me on 2007-07-01
I can't help with problem #1, but I had problem #2 after upgrading to Feisty and fixed it--so far--by editing /etc/default/acpi-support from this:

```

# Add services to this list to stop them before suspend and restart them in
# the resume process.
#STOP_SERVICES=”mysql “

```

to this:

```

# Add services to this list to stop them before suspend and restart them in
# the resume process.
#STOP_SERVICES=”mysql networking“

```

based on info in another post I found here. 

Now I get a little pop-up that tells me the network connection has been established every time I resume from standby and all is good. ;)

---

