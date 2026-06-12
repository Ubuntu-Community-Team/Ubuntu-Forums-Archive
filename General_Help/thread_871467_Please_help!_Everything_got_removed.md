---
title: "Please help! Everything got removed"
date: 2008-07-26
forum: General Help
---

### Post by justinclark on 2008-07-26
I was following this guide [http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/?rcommentid=1494&rerror=incorrect-captcha-sol&rchash=fa1cd59fb05bf69dd21f079934ebf74d#commentform](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/?rcommentid=1494&rerror=incorrect-captcha-sol&rchash=fa1cd59fb05bf69dd21f079934ebf74d#commentform)
to help install the global menu. it says if I have trouble installing it then try sudo apt-get install -f so I did.  It then proceeded to remove everything and shut down my lap top!  What have I done? Can I get it back?  Any help please, thank you.

---

### Post by aysiu on 2008-07-26
Well, it depends what you consider "everything."

Are you able to boot to a command prompt at all?

If so, log in, and type ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by justinclark on 2008-07-27
Yeah Im actually typing this on it now.  It wasnt quite everything but it seems compiz is gone, along with a bunch of apps and im not sure what else yet.  What sort of command is that and how was it supposed to help with the global menu?  Is there some sort of system restore that I dont know about?

---

### Post by justinclark on 2008-07-27
I opened the update manager and it says that my software index is broken

---

### Post by aysiu on 2008-07-27
I'm confused. So the commands I gave you worked? You're in a graphical environment? Or have you been in one this whole time?

---

### Post by justinclark on 2008-07-27
sorry I have been in one the whole time.  It seems to have removed many settings and apps.  I also cant load the update manager or add/remove programs.  And my window frame is gone.

---

### Post by aysiu on 2008-07-27
If you can open a terminal, try ```
metacity --replace &
``` and see if that helps.

---

### Post by justinclark on 2008-07-27
sudo apt-get update gives me "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

---

### Post by justinclark on 2008-07-27
ok you got the window frames back with the metacity command.

---

### Post by jimv on 2008-07-27
> **justinclark said:**
> sudo apt-get update gives me "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

Open a terminal and type:

sudo dpkg --configure -a

When it's done, reboot.

---

### Post by justinclark on 2008-07-27
> **jimv said:**
> Open a terminal and type:

sudo dpkg --configure -a

When it's done, reboot.
This command isnt doing anything.  Last night I tried sudo apt-get install -f and it would eventually just give me a command screen and I would have to reboot.

---

