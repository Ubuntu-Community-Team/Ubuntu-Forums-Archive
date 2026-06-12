---
title: "FIX: Laptop eraser/nub"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by compaqdrew on 2006-06-02
Hey guys, I am totally new to Linux and for the past month or so have been having a really annoying problem.  On my laptop (Dell Latitude C600), there are two pointing devices--a touchpad, and a little eraser / 'nub' pointer.  The latter is broken and behaves erratically, causing my mouse pointer to 'jump' left a few hundred pixels every few seconds.  As you can imagine, this is highly annoying.  In Windows, there's a wonderful little checkbox I can tick that disables the eraser, in Linux I have been (until recently) unable to figure out how to disable it while preserving my touchpad.  I'm including my (admittedly simple) fix as well as the process I went through in the hopes it might be useful to someone else solving a similar problem or learning how to troubleshoot hardware problems in Linux.

First, I paraded through both GNOME and KDE's control panel(s).  I'm a Windows guy, and control panels are where things to do with mice and touchpads are kept in Windows.  No luck.

Then, I did some googling, and came accross a nifty tool called synclient.  In order to use it, I edited my xorg.conf file to include Option "SHMConfig" "On". Whenever you edit xorg.conf, you have to restart X, which you do by pressing ctrl+alt+backspace.   I played with synclient's settings and found a lot of cool features, ones similar to the Windows control panels I was used to.  There was even a way to disable the touchpad--and it worked--but I still couldn't disable that eraser.

At this point, I was feeling frustrated, so I went back to xorg.conf and started massively-editing and commenting things out to see if I could disable that eraser.  (You can always get your xorg.conf file back by typing 'sudo dpkg-reconfigure xserver-xorg).  What I discovered is this: for whatever reason, the "Synaptics Touchpad" entry in xorg.conf has absolutely nothing to do with things like pointing and clicking, which is a bit of a revelation to a Windows guy.  I'm still not really sure what it does, I believe it handles more-advanced features such as tap-to-click and scroll zones.

But what does handle the clicking and pointing--that's the "Configured Mouse"  entry.  And on my machine, the input was set to "/dev/input/mice"

Now aparrently, on Linux, everything is a file.  So I opened up a terminal and did 'ls /dev/input/' and sure enough, there was a file called 'mice'.  In fact, there were two other files of interest: 'mouse0' and 'mouse1'.  Since they were files, I figured maybe I could use the 'cat' tool on them, which outputs the contents of files.  So I ran 'cat mouse0', and was met with a blank line.  If I moved my hand on the touchpad, the terminal filled up with text.  I waited expectantly for some text to represent the 'drift' that I get every five seconds, but nothing happened.

Then I tried 'cat mouse1'.  Nothing happened when my hand was on the touchpad, but every few seconds the number '8' would appear.  That was where the drift was coming from.

A quick 'cat mice' revealed that somehow the messages from both files end up there.  

At first, I thought that by removing the mouse1 file (rm mouse1) I could stop the messages of 8s.  However, this turned out not to be--the 'mice' file still showed 8 messages.  

But what did work was changing the "/dev/input/mice" in my xorg.conf to "/dev/input/mouse0".  No more drift, and I figured it all out on my own.  Woot!

---

