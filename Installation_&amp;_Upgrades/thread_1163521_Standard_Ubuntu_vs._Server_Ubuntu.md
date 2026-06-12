---
title: "Standard Ubuntu vs. Server Ubuntu"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by compnut41 on 2009-05-18
I am curious as to what differences there is between the server addition to Ubuntu and the standard version, and possibly what advantage one has over the other if any. Especially if it makes my computer any stronger, I enjoy power.

---

### Post by spcwingo on 2009-05-18
The server edition puts more resources towards services and it doesn't come with a gui by default.  Of course you can:

```
sudo apt-get install ubuntu-desktop
```

to get a gui.  The desktop puts more resources towards apps.

---

### Post by cariboo on 2009-05-19
I'm not sure what you mean by stronger, but if you mean more secure, both version are very secure until you start up any services. I found that my server 1Ghz AMD X86_64 sure boots a lot faster than my desktop AMD X2 3200 X86_64, but the server doesn't have a gui so it doesn't spend time loading any graphics. :)

---

### Post by Das Goat on 2009-06-11
The thing that I don't understand is this:

Granted: You don't want your server to start with a GUI because of resources, security, etc.

Given: It is not as easy for the in-experianced user to configure a server without the GUI

Why: Why isn't there a configuration that allows the server to boot up and be a server, but allows an administrator to go to it and do something as simple as startx to configure the server via the GUI, then exit the GUI to let the server run as it should?

You would think that this would be simple thing to do. Do the powers that be really think that configuring via command line is how linux will be adopted?

And while I am on a rant, why can't there be a remote application, similar to ssh, but more robust like VNC, that lets you log in to the server and do what needs to be done? And don't tell me WEDMIN does it. It may sort of work if you spend hours configuring it, but basic setup doesn't even work with SAMBA correctly.

Sorry to rant. I love Liunx, but there are some basic short comings that make it hard for the tech in the field to support.

---

### Post by cariboo on 2009-06-11
Ubuntu has very few server specific gui tools, all configurations are done to plain text files. That being said, I use mc quite a bit on my server, it is an ncurses based file manager, that does a lot more.

If you really need gui tools, CentOs and Suse are two server distributions that come to mind.

---

### Post by Das Goat on 2009-06-12
I wouldn't say I need GUI tools, as much as a simplified way to look at the whole configuration. A text based menu system would be just fine, something like (from way back in the day) sidekick, or even like the installation menus. I'm just looking for a quick launcher for casual changes and to make sure all the configuration options have been set.

What is this MC you spoke of?

Das Goat

---

