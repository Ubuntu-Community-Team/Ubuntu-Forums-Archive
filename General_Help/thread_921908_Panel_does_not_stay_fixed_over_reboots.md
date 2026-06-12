---
title: "Panel does not stay fixed over reboots"
date: 2008-09-16
forum: General Help
---

### Post by bl4k3r on 2008-09-16
I customized my desktop according to a tutorial [via [How-To Geek]("http://blogs.howtogeek.com/tuxgeek/2008/09/08/pimp-your-gnome-in-7-steps/")] lately [[result screen shot]("http://flickr.com/photos/z0ck83r7/2860206461/")] and am baffled with an annoying issue now:

Every time I reboot, the main gnome panel is located on the bottom of my screen, underneath AWN dock. Of course I can change the location via the dock's settings menu, but on the next reboot, it appears on the bottom again.

Does anyone know a solution to this? Many thanks in advance!

---

### Post by daitau on 2008-09-17
Instead of rebooting immediately, try to logout first. This worked for me when I wanted to save the panel layout in the past.

---

### Post by bl4k3r on 2008-09-18
Thanks for the suggestion! Unfortunately it did not work for me. :-/

---

### Post by anotherdisciple on 2008-09-19
I'm not at a linux computer, but I have a solution

Okay...  hit Alt+F2 and type:

```
gconf-editor
```

then navigate to apps/panel/toplevels

find your panel and find the option to make it at the top or bottom.... change it to top.

If this won't stay after reboot. Go to (System > Preferences > Sessions) and type a command that sets that key every time you log in. You would do that with a gconftool command.

Here is a tutorial on how to do a gconftool command...

[http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/]("http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/")

---

### Post by bl4k3r on 2008-09-21
First, thank you very much for your detailed post!

I followed your instructions just to find out that gconf-editor *does not want me to change the value*. When I enter "top", it just goes back to "bottom" after about a second. I even looked up the appropriate XML-File (located at ~/.gconf/apps/panels/toplevels/top_panel_screen0/%gconf.xml) and edited it manually. After logging out and back in again, the value was back to "bottom". :-/

Might this be a general Gnome / Gconf bug?

---

### Post by anotherdisciple on 2008-09-21
That stinks! Sorry about that... Have you filed a bug report? I'm sure lots of people would appreciate it if you did. I'm sure other people have ran into this issue.

---

### Post by bl4k3r on 2008-09-22
I filed a bug via launchpad to gconf-editor, hope they can reprocuce it.

---

### Post by anotherdisciple on 2008-09-22
Cool... thanks!

PS- I tried it out... got the same result as you did.

---

### Post by malspa on 2008-09-22
I've run into a similar problem with my unexpanded panels, not only in Ubuntu but also in Mint.

In my case, in Hardy, using a top panel and a bottom panel, with each in unexpanded mode. With each new session, the panels would switch places unless I expanded them both before logging out.

Here's what worked for me. My screen resolution is 1024x768.

In gconf-editor:

In apps > panel > toplevels > bottom_panel_screen0, I changed the y key to 760.

In apps > panel > toplevels > top_panel_screen0, I changed the y_bottom key to 760.

Now when I start a new session, the panels are still in place, even if I have left them unexpanded.

A similar fix worked for my panel in Mint, which is a bottom panel (unexpanded) that kept relocating to the top when I started a new session.

I should also note that, as I recall, the first time I tried this in Hardy it didn't work when I started a new session, but after that the panels stayed in place with each new session.

---

