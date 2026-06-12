---
title: "[SOLVED] uShare &amp;amp; Xbox 360"
date: 2008-10-05
forum: General Help
---

### Post by timstone on 2008-10-05
I installed uShare and edited it's config file to be xbox 360 compatible.  I wanted to set it up to start when the computer ran, but didn't.  Instead I just used 

sudo /etc/init.d/ushare start


i started up the xbox and it wasnt seen the computer at all, my older windows share was on there but not the new stuff...

can anyone help me out?

---

### Post by kramulous on 2008-10-05
Hi, here's my /etc/ushare.conf
> 
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Bender

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/media/Media/Public

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
#USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
#ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
#ENABLE_DLNA=

Also, inside /etc/init.d/ushare, I needed to set 

> USHARE_OPTIONS="-x"

Which appears around line 25.  It should work now.

---

### Post by timstone on 2008-10-05
worked perfect! it might have made a difference if i would have done

sudo /etc/init.d/ushare -x start  but i dont know

i just set up the way you did and it works fine, so thank you!

---

### Post by timstone on 2008-10-05
how can i go about starting this up everytime the pc starts up?  can i run it as a session and do

/etc/init.d/ushare

or maybe something else?

---

### Post by rsambuca on 2008-10-05
> **timstone said:**
> how can i go about starting this up everytime the pc starts up?  can i run it as a session and do

/etc/init.d/ushare

or maybe something else?

Yup.  If you are running Gnome, you can add the ushare -x to your startup programs in the Sessions tab.

---

### Post by Moezzie on 2008-10-05
I've been using ushare with my xbox 360 for a good while now and in my experience your better of starting it manually with:
ushare -x -f /path/to/your/config
The daemon usually does not work as supposed, at least not for me. It stopps showing up on the xbox after a while.

---

### Post by timstone on 2008-10-05
well i ended up doing this after reading on another thread....would it work?

sudo ps -e | grep ushare

---

### Post by rsambuca on 2008-10-05
Work for what?  What are you trying to do?

That command will just tell you whether ushare is already running.  It won't start ushare.

---

### Post by timstone on 2008-10-05
that goes to show you how much i know about linux so far :)   the thread that was posted in said that command would add ushare to the startup group :) 

obviously it didnt work.....i think ill just stick with starting it manually

---

### Post by rsambuca on 2008-10-05
Just go to "System - Preferences - Sessions".  In the Window that opens, select "Startup Programs".  Click "Add".  Put the ```
/etc/init.d/ushare -x
``` in the "Command" box.  After that, it will start up whenever you login to your gnome desktop.

---

