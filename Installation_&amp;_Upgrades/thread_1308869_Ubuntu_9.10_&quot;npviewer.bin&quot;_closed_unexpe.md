---
title: "Ubuntu 9.10 &quot;npviewer.bin&quot; closed unexpectedly"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2009-11-01
After upgrading from Ubuntu 9.04 to 9.10 today, my system always jump out
a warning "Application problem" dialog and saying:

```

Sorry, the program "npviewer.bin" closed unexpectedly


if you were not doing anything confidential (entering passwords or other private information), you can help to improve the application by reporting the problem.

Ignore future crashes of this program version
```

So, can anybody help to explain why it is so, and how to avoid this 
"Application problem"?

Cheers
JIA

---

### Post by Youresorock on 2009-11-02
This happens to me literally twice an hour on 9.10.  I've resorted to using Google Chrome instead of Firefox.  It doesn't crash, but also doesn't have all the great plugins I'm used to.

How am I supposed to live without Rikaichan?

So npviwer.bin is some kind of plugin wrapper for Adobe Flash.  Also hard to live without Flash.

I've tried reinstalling Flash, but it doesn't help.

I've read this only affects 64bit.  Are you running 64bit?

---

### Post by black32 on 2009-11-04
> **Youresorock said:**
> This happens to me literally twice an hour on 9.10.  I've resorted to using Google Chrome instead of Firefox.  It doesn't crash, but also doesn't have all the great plugins I'm used to.

How am I supposed to live without Rikaichan?

So npviwer.bin is some kind of plugin wrapper for Adobe Flash.  Also hard to live without Flash.

I've tried reinstalling Flash, but it doesn't help.

I've read this only affects 64bit.  Are you running 64bit?

Well I tried downloading the 64 bit of adobe flash plugin and installed it as provided [here]("http://nixify.blogspot.com/2009/11/install-latest-flash-player-on-64-bit.html") . After installing this I don't see any npviewer.bin in the process tree. And it isn't eating the resources as before.

Cheers!

---

### Post by Youresorock on 2009-11-04
I tried removing flash and then installing as described above.  The result is firefox crashes within 5-10seconds on hulu.com.

---

### Post by black32 on 2009-11-04
> **Youresorock said:**
> I tried removing flash and then installing as described above.  The result is firefox crashes within 5-10seconds on hulu.com.

^ Firefox version ? mine is 3.5.4
  Checked with hulu.com its going fine. 

Plus, I have the flashblock plugin installed that will stop from loading unnecessary flash movies.

You don't even need to remove the flash plugin you have installed. Just replace libfflashplayer.so with the ones downloaded. You running 64 bit? I suppose yes.

---

### Post by paxmark1 on 2009-11-05
Upgrade from 9.04 to 9.10  4 GB ram Asys PK5VLM mobo.  

Upgrader for me went fairly smooth, however I kept getting notes that npvierwer.bin had crashed.  Opera upgraded just minutes before upgrading computer.  Opera come on when gnome comes up for me.  

I set the crash handler to stop reporting to me when npviewer.bin crashes.      Things well enough, but what is this npviewer. bin and why is it crashing.  I sent the bug off to launch pad.

---

### Post by jocko on 2009-11-05
> **paxmark1 said:**
> ... but what is this npviewer. bin and why is it crashing.
npviewer.bin is a wrapper that runs the 32 bit adobe flash plugin in 64 bit firefox. It's crashing because... it doesn't work properly. It's been like that for a long time (I've had it at least the last 3 ubuntu releases). To fix it, uninstall the packages flashplugin-installer and nspluginwrapper, then install the 64 bit flash plugin ([see this thread]("http://ubuntuforums.org/showthread.php?t=1259102")).

---

