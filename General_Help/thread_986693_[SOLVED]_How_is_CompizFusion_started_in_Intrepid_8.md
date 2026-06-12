---
title: "[SOLVED] How is CompizFusion started in Intrepid 8.10"
date: 2008-11-18
forum: General Help
---

### Post by ciscophoneguy on 2008-11-18
I want to make a change in the way Compiz is started, but I am unable to find a way to do it. The following is what I want to change:

> LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --indirect-rendering --sm-disable ccp &

However, there is no startup program for Compiz under sessions. Is there a conf file I have to make a change to? If so, does anyone know what it's called and were it's located? Thanks! ):P

---

### Post by omgorange on 2008-11-19
I download the Compiz Fusion Icon, via Add/Remove, which shows up under Applications >> System Tools after install. This icon launches Compiz Config to your system tray.

---

### Post by eternalnewbee on 2008-11-19
> However, there is no startup program for Compiz under sessions. Is there a conf file I have to make a change to? If so, does anyone know what it's called and were it's located? Thanks!
I'm not sure if I understood you correctly, but if you want to add compiz to your start up applications in sessions, go to: **Main Menu > System > Preferences > Sessions**, and click **Add**.
**Name**: Compiz Fusion
**Command**: compiz --replace
**Comment**: Desktop Effects.
Hope this helps.

---

### Post by glennric on 2008-11-19
Compiz is run from the script /usr/bin/compiz-manager.  If you want to change the options that compiz is run with you could edit that file.

---

### Post by ciscophoneguy on 2008-11-19
Thanks for the replies; I'll try to be more specific. I've been having some issues with compiz while using some applications (Firefox, Elisa, & GoogleEarth). I've been looking for a way to alleviate some of these problems and found the following:

> Intel GMA Cards

If you are using an Intel GMA card with AIGLX, you will need to start Compiz with LIBGL_ALWAYS_INDIRECT=1 prepended to the command line and run compiz with the --indirect-rendering option, as with the following example:

LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --indirect-rendering --sm-disable ccp &

From the CompizFusion website under Troubleshooting. I wanted to check and see if compiz is starting that way or if indirect rendering is turned on.

Currently compiz just starts when I login. I don't know how that's done, or what conf file I could make a change to that would start compiz in this way.

Also glennric, I did check /usr/bin/compiz-manager. However it did not look like a conf file to me. I cannot show you since I'm at work and don't have my Ubuntu Laptop with me.

Maybe a better question would be, how do I modify (what's the correct syntax) /usr/bin/compiz-manager so that compiz starts "LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --indirect-rendering --sm-disable ccp &" like so? 

Thanks allot for the replies, much appreciated! ):P

---

### Post by eternalnewbee on 2008-11-19
**Firefox**: No problem.
**GoogleEarth**: I don't think so.
**Elisa**: That's a problem.
(for compiz, that is).

---

### Post by CaminoSS on 2008-12-15
> **eternalnewbee said:**
> I'm not sure if I understood you correctly, but if you want to add compiz to your start up applications in sessions, go to: **Main Menu > System > Preferences > Sessions**, and click **Add**.
**Name**: Compiz Fusion
**Command**: compiz --replace
**Comment**: Desktop Effects.
Hope this helps.

I'm running Hardy. Compiz was working and then it wasn't. Your solution fixed my problem of starting compiz at boot time.

Thx

---

