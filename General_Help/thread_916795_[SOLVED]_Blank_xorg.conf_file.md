---
title: "[SOLVED] Blank xorg.conf file"
date: 2008-09-11
forum: General Help
---

### Post by zdunham on 2008-09-11
Hi,

Well this all started because I wanted to change the screen resolution on the computer I was using and I couldn't. I tried to do it manually in the xorg.conf file and to my surprise it was blank. Then I did:

```

sudo dpkg-reconfigure xserver-xorg

```

I went through the configuration and saved it and then it was still blank when I opened it in gedit. Any ideas?

---

### Post by triphazard on 2008-09-11
When you opened it in gedit, did you do so from a terminal window?  I'm just wondering as the x in \X11\ is uppercase (if i recall correctly) and as everything Linux is case-sensitive if you typed it with as lowercase x then gedit would simply open a blank file for you.

---

### Post by zdunham on 2008-09-11
> **triphazard said:**
> When you opened it in gedit, did you do so from a terminal window?  I'm just wondering as the x in \X11\ is uppercase (if i recall correctly) and as everything Linux is case-sensitive if you typed it with as lowercase x then gedit would simply open a blank file for you.

Alright that did open the file, I feel dumb for that. Which line would I use to edit the screen resolution in there if possible? It doesn't want to go higher than 640x480 for some reason using the interface.

---

### Post by pastalavista on 2008-09-11
Try..
```
sudo gedit /etc/usplash.conf
```

---

### Post by zdunham on 2008-09-11
> **pastalavista said:**
> Try..
```
sudo gedit /etc/usplash.conf
```

The file didn't exist a blank one came up.

---

### Post by phidia on 2008-09-11
You may want to use the Ubuntu wiki [here]("https://help.ubuntu.com/community/Video") also there is a sample xorg.conf [here]("http://en.wikipedia.org/wiki/Xorg.conf") Scroll down and you should see the Section "Screen", subsection "display" the Modes are what you want to edit with the actual values you want.

---

### Post by zdunham on 2008-09-11
> **phidia said:**
> You may want to use the Ubuntu wiki [here]("https://help.ubuntu.com/community/Video") also there is a sample xorg.conf [here]("http://en.wikipedia.org/wiki/Xorg.conf") Scroll down and you should see the Section "Screen", subsection "display" the Modes are what you want to edit with the actual values you want.

I used the example file but still cannot change the resolution. Its an NEC AccuSync 70 I know it goes higher than 640x480 this is weird. I probably sound like a noob.

---

### Post by triphazard on 2008-09-11
Going on the potential noob vibe  ;) (just kidding) have you restarted X since making these changes?  Giving it a ctrl-alt-backspace should make the changes kick in.

---

### Post by zdunham on 2008-09-11
> **triphazard said:**
> Going on the potential noob vibe  ;) (just kidding) have you restarted X since making these changes?  Giving it a ctrl-alt-backspace should make the changes kick in.

Nope lol. There we go, what's the command to restart X haha?

---

### Post by triphazard on 2008-09-11
Hitting ctrl-alt-backspace together should restart X.  You'll be brought back to the login screen but hopefully you'll see the new resolution(s) available to you once you're back in.

---

### Post by zdunham on 2008-09-11
> **triphazard said:**
> Hitting ctrl-alt-backspace together should restart X.  You'll be brought back to the login screen but hopefully you'll see the new resolution(s) available to you once you're back in.

Alright I did that and for some reason the whole machine rebooted and I keep getting this message when it boots, it gives a warning saying its running in low graphics mode and does not say why, one of my co-workers said it might be missing a driver. Any ideas on that problem?

---

### Post by zdunham on 2008-09-11
Thanks for all your help I fixed it.

I chose configure when that warning came up and I selected the monitor and resolution and it changed the res but was all messed up looking. I restarted in recovery mode and told it to fix X and it was all fine. Thanks for help.

---

