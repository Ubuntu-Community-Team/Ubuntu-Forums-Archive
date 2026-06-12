---
title: "Controlling a Mac with Ubuntu"
date: 2008-11-11
forum: General Help
---

### Post by x C0MMAND0 x on 2008-11-11
I am running Ubuntu 8.1 and I love it.  My girlfriend has a new Mac, and would like for me to be able to give her remote support.

What programs would work connecting FROM an Ubuntu computer TO a Mac computer, where she would be able to see me control her computer (ie watch the mouse move etc...)

I'm wondering if some sort of VNC is the way to go, but I'm not sure.  I also have thought about using Hamachi, and I have it installed on both machines but have had no luck controlling them.

---

### Post by m_l17 on 2008-11-12
Yes you can, you need to install xtightvncviewer on Ubuntu:

```
$ sudo apt-get install xtightvncviewer
```

On the Mac side you need to enable remote connections from the sharing pane in system preferences. In order for it to work you need to set a password under her account. The passwrod can only be 8 characters long.

To connect from Ubuntu:

```
$ xtightvncviewer ip.add.re.ss 
```

Then it will ask you for the pasword.

If you want to set xtightvncviewer as your default vnc viewer:

```
$ update-alternatives --set vncviewer /usr/bin/xtightvncviewer
``` 

Now you only have to type vncviewer instead xtightvncviewer.

This works well within my lan. 

To control over the net read this:

[https://help.ubuntu.com/community/VNC?highlight=(only)|(cli)#Accessing%20your%20PC%20over%20the%20Internet]("https://help.ubuntu.com/community/VNC?highlight=(only)|(cli)#Accessing%20your%20PC%20over%20the%20Internet")

Hopes this helps.

---

### Post by calibre97 on 2009-01-25
Gotta love these forums. I've installed xtightvncviewer as you mention and I do indeed see my Mac screen (I've configured it with Screen Sharing and a password). So far so good. However, when I click either horizontally or vertically to see the whole Mac screen (Studio display) on my smaller Dell D630 laptop screen, I can't scroll the screen back to the top or the left. I click and click and click anywhere I can but the black bars don't budge from their now permanent homes at the bottom and right of the screen. Is there any way to control/configure xtightvncviewer? I'm using Linux Mint 6 which is Ubuntu 8.10 based but I don't have any kind of GUI component-that I can see anyway.

---

### Post by Ocxic on 2009-01-25
turn on remote login in the sharing preferences, and you can ssh into the mac.

---

### Post by mb_webguy on 2009-01-25
Just out of curiosity, but why the suggestion of xtightvncviewer, when Ubuntu comes with Vinagre?

---

### Post by calibre97 on 2009-01-25
> **Ocxic said:**
> turn on remote login in the sharing preferences, and you can ssh into the mac.

I don't mean to be dense or curt but...um, ok, and then what?
SSH into the Mac for what? I understand (barely) the concept of SSH but then what would you use or do? I use SSH at work to use CVS but how would that help in this case since the idea is to see the Mac desktop in Ubuntu?

Personally, I'm using Linux Mint so Vinagre isn't installed by default nor is it in the Mint Install program as easily chosen. It is available in the Package Manager, though, so I'll give it a try.

---

### Post by calibre97 on 2009-01-25
OK, I tried Vinagre and it was slower than molasses. Cool features, though...easy Full Screen, quick select of what to connect to unlike the command-line launching of tight..but sloooooooooow.

---

### Post by x C0MMAND0 x on 2009-01-26
What ports does vncviewer use by default?  I want to know so I can set up port forwarding to my girlfriends laptop so that way I can automatically just connect to her computer when I vnc to her external IP.

---

