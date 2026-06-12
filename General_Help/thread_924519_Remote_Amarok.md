---
title: "Remote Amarok"
date: 2008-09-19
forum: General Help
---

### Post by MarshyTheKid on 2008-09-19
I'm planning on setting up my desktop this weekend as kind of a remote server.
I want to have all of my music on the desktop, which will be hooked up to my stereo system. Then I want to be able to control my Desktop amarok with my laptop. I know I can terminal into it, but I was wondering if there was a way have the amarok interface on my laptop, but control everything on the desktop. Meaning it reads the files from the desktop and it plays the music back to the desktop.
If that doesn't make sense let me know and I can try to explain it better.

---

### Post by MarshyTheKid on 2008-09-19
I'm not sure if I could just link to the db on the desktop, then have the sound play to a file and then have my desktop automatically play from that file. That seems like it would work at first until I took my laptop from the network.

---

### Post by Captain Giraffe on 2008-09-19
I have a similar setup and would really appreciate any suggestions.

---

### Post by AndyCooll on 2008-09-19
There are a few ways you can do this, though it's a while since I've done anything similar so you may need to check about where the sound outputs from.

Firstly you can set up VNC so that you remote into your remote "desktop pc"  (Applications > Internet > Terminal Server Client).

Secondly you can use XDMCP. This displays your remote machines desktop on your local machines virtual terminal, e.g.  ALT+F8 (your normal gui desktop is ALT+F7). So your "desktop pc's" desktop will display on your laptop but all the processes are actually running on the desktop pc. What I can't remember is where the sound comes out.

Finally you can setup ssh so that it will allow you to  display graphical applications on the local machine. So from your laptop you ssh into the remote pc using the -X switch. And then type "Amarok" without the parentheses. The Amarok interface will now open on your laptop but will actually be running on your remote pc. Again I can't remember where the sound comes out, though with this one I do think it is on the remote pc.

There are probably other options too, like setting up mpd in some way so that it runs on a remote pc but is controlled from a web-interface on your laptop.

:cool:

---

### Post by MarshyTheKid on 2008-09-19
I think I'll try doing the ssh route. If not I think I found an amarok script that will work. Really just a web interface would work.

Thanks!

---

### Post by HermanAB on 2008-09-19
One word: SSH
$ ssh user@server amarok

Or if you are click happy:
$ ssh user@server gnome-panel

---

