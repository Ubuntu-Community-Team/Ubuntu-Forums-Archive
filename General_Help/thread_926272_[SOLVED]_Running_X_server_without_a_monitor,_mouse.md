---
title: "[SOLVED] Running X server without a monitor, mouse, and keyboard. I have to use VNC t"
date: 2008-09-21
forum: General Help
---

### Post by Predator106 on 2008-09-21
Hello, I have been having a headache of problems, I have Hardy installed on a server downstairs, there is no monitor, keyboard, or mouse attached to this, just power and Ethernet.

I have had a ton of ATI problems, but that's not what this is about.

You see, to set up my Hardy workstation, I hooked it up to my input/outputs on my workstation upstairs(VGA, PS/2, USB). It all worked fine, I could access it through VNC PERFECTLY.

Upon moving it downstairs and removing the VGA, Keyboard, and Mouse, and VNC'ing it, my VNC screen was about 2 x 2 INCHES! Whilst it was quite funny to begin with, I quickly got annoyed with it. I cannot do a whole lot, including run nautilus, or nano, the most I can do is run gedit I guess, and the terminal.

It appears that X is autodetecting my screen, and discovering that there is in fact, no screen. It then sets it to the smallest X value-I guess, that it can do.

Does anybody know how to force my X server to FORCE it to be at any resolution I want, I want to be able to change it when I want, not to have to haul it back upstairs, which is an incredible pain.

I am really anxious to get this server up and running, and have a TON of work to do on it, so ASAP would be wonderful, naturally :)

---

### Post by geeth on 2008-09-21
[http://wiki.archlinux.org/index.php/Xorg](http://wiki.archlinux.org/index.php/Xorg)

That may help you.

Has info on setting display settings manually.

---

### Post by cariboo on 2008-09-21
Stop the gui from starting and use X forwarding with ssh. Install openssh-server on your server and access it using ssh. To use a graphical program on the server in a terminal type:

```
ssh -X user@server
```

Then in the same terminal type for example:

```
sudo synaptic
```

This will start synaptic on the server and run it on the desktop of the computer you are using.

For file management as well as transfering files use nautilus with sftp. to use sftp open nautilus and in the location bar type:

```
sftp://user@server
```

This will open the file system of your server in nautilus on the desktop of the computer you are using.

**Note**: You will have to change user to your user name and server to your server's name or ip address.

If you are accessing your server from a windows computer you can accomplish the same thing with putty and winscp which are both free downloads.

Jim

---

### Post by Predator106 on 2008-09-21
No, I don't want to go through all of this work just to do this (replying to above post only, haven't tried the 1st reply yet). I don't want the window's themselves to reside on my computer, as two separate people, using two different computers control this server, I want to have a normal X session.

Otherwise it's a pain in the ***, not worth it, and actually makes it harder for me to do any work. When I turn off my computer, I want the windows that were on the server to stay the same, I don't want to have to reopen it every time or something stupid.

It's counter-intuitive, I should've mentioned I didn't want to use that, as through hours of googling I have only managed to find that, basically.

---

### Post by Predator106 on 2008-09-22
I don't know, I suppose I don't not need a monitor for my server. I just figured it'd be easier, but then again every time something goes wrong with VNC, etc. I have to haul it upstairs.

---

