---
title: "How to map Super_L key to the Application Launcher"
date: 2009-11-02
forum: Hardware
---

### Post by Alan C on 2009-11-02
Hi,

Just installed NBR 9.10 on my Eee PC 901 (replacing the original Xandros) and am absolutely delighted with it.  One small annoyance, however, is that I haven't managed to map the home/Win key to take me straight to the Application Launcher.  This is what it did on Xandros and I also had this working when I previously tried NBR 9.04 from a USB stick.  I'm talking about the key that is between "Fn" and "Alt" and has a picture of a house on it;  on Windows versions of this machine it has the Windows logo.

When I try to assign this key in "Keyboard Shortcuts", it isn't recognised at all - nothing at all happens when I press it.  I can assign other keys just fine.

I've run xev and confirmed that this key is detected, with keycode 133 and is mapped to Super_L.  xmodmap -pk also shows keycode 133 mapped to Super_L.

Any ideas?

Even once I've solved this, I'm not sure what I should be mapping this key to in Keyboard Shortcuts.  

Any help with this would be most gratefully received.

Many thanks

Alan

---

### Post by Alan C on 2009-11-02
Ok - I've found the answer to my question...

I'd already found [this]("http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html") page, which showed how to map this key to bring up the Application menu but I still didn't know how to change the mapping to the Application Launcher.  Anyway, I found gconf-editor and after browsing in there, I found the answer. You can change it in there but the following command (adapted from the link above), has the desired effect:

gconftool-2 --set /apps/metacity/global_keybindings/show_desktop --type string "Super_L"

My "home" key now flips nicely to the application launcher and back, just as I wanted.

Hope that helps someone else.

Alan

---

### Post by andypiper on 2009-11-05
How does that work for you with Compiz? on an Acer Aspire One I find that the Win/Home/Super-L key+Alt does app switching. If I set this key using gconftool, I find that it gets a bit confused.

---

