---
title: "custom live 9.04 &quot;thinclient&quot; cd/usb to boot/load into citrix desktop"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by ibbers on 2009-10-08
Hi folks,

I'm looking at several options to convert our old retired boxes into ubuntu-based thinclients (yes, i'm also looking at thinstation etc too, but am comparing possibilities), and have a few questions i thought someone here might have an idea or two about what i'd like to do.

I'd like to create a custom build of 9.04, running of a CD or USB stick, that:

1.  autologins into gnome/xfce etc (the faster the better),
2.  autoloads a preconfigured citrix client connection to our citrix server, with the only other applications in the build being those necessary to support the citrix client software

I already do this with my own Ubuntu  laptop when out at remote offices, and this is how i got the idea for a Live Ubuntu CD/USB that could avoid the necessity of maintaining a tftp server for thinclients, and slimmed down to the very barest necessities

The questions though that I have:

* what applications would i need in a slimmed down ubuntu to support the citrix client (anything else being unnecessary)

* could i configure it to log into the citrix server from the login (automatically or manually - actual logging into the citrix server with windows credentials would be left to the user when the blue windows screen appears)?

* or would I have to preconfigure ubuntu to autologin and then automatically load the citrix client at startup (and in doing so, automatically load the preconfigured connection to the citrix server)?

ultimately, the idea of just burning a custom ISO of ubuntu and throwing it in a box to boot up into citrix is the target - and would be very impressive to boot :D

cheers

jon

---

