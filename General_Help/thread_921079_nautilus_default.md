---
title: "nautilus default"
date: 2008-09-15
forum: General Help
---

### Post by goodrench on 2008-09-15
I had recently installed the xubuntu-desktop package and with it came Thunar. When I uninstalled xubuntu-desktop I can no longer open nautilus from the 'Places' menu.I know this question comes up a lot but I have been trying all of the suggestions and nothing seems to be working.
I cured the problem quite some  time ago with a script from this site
> [http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)
but this time it is not working.
I have tried the gconf tool from the command line and get an error about the key not being writable. 
When I try to change the value in gconf-editor

> /apps/nautilus/preferences/always_use_browser

It gives me an error

> Cannot overwrite existing read-only value: Cannot overwrite existing read-only value: Value for `/apps/nautilus/preferences/always_use_browser' set in a read-only source at the front of your configuration path


From what I have been able to find online about this problem, this is where to fix the problem, but it doesn't seem to work.
I have attached a picture of gconf-editor.

---

### Post by Pro-reason on 2008-09-15
Try this:

```

sudo chown -Rv `whoami`:`whoami` ~/.gconf ~/.gnome*
sudo chmod -Rv u+rw ~/.gconf ~/.gnome*

```

---

### Post by goodrench on 2008-09-16
> **Pro-reason said:**
> Try this:

```

sudo chown -Rv `whoami`:`whoami` ~/.gconf ~/.gnome*
sudo chmod -Rv u+rw ~/.gconf ~/.gnome*

```


That seemed to do it.
Changes did not take effect until after a reboot.
But gconf-editor still says key is not writable.
Very strange.

---

### Post by Pro-reason on 2008-09-16
> **goodrench said:**
> That seemed to do it.
Changes did not take effect until after a reboot.
But gconf-editor still says key is not writable.
Very strange.

I don't understand.  You say it apparently did the trick... but also that the key is still not writable.  :confused:  Did it work or not?

---

### Post by goodrench on 2008-09-16
> **Pro-reason said:**
> I don't understand.  You say it apparently did the trick... but also that the key is still not writable.  :confused:  Did it work or not?

Sorry. It was early this morning when I wrote that.
Nautilus now opens when I open a folder from the 'Places' menu.
The key in gconf-editor still says 'not writable'.

this is the error message
> Cannot overwrite existing read-only value: Cannot overwrite existing read-only value: Value for `/apps/nautilus/preferences/always_use_browser' set in a read-only source at the front of your configuration path


I found this page

[http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/)

It talks about path settings in the file /etc/gconf/<version>/path

Is this what the error message is related to?

---

### Post by Pro-reason on 2008-09-16
Well, if you do &#8220;less /etc/gconf/2/path&#8221; you'll see that file.  It's a system-wide configuration file.  You shouldn't be able to edit it without root access anyway.  

I'm more of a KDE man than a GNOME user, so I don't know about all this.

If you run the editor as root, I imagine it will be writable to you.  I don't know if that's what you ought to do though.

P.S. Here's another idea.  Do this:

```

sudo chmod -Rv u**g**+rw ~/.gconf ~/.gnome*

```

That gives access to users in your &#8220;group&#8221; too.  You could even try shutting down GNOME and running the command from TTY1.

---

### Post by goodrench on 2008-09-16
I tried as you said and the key is still not writable.

---

### Post by Pro-reason on 2008-09-16
Well, I just don't know why it's doing that.

If you create a new user and use it to log on, does it have the same problem?

You could try taking ownership of /etc/gconf, but it's a bit risky.

---

### Post by goodrench on 2008-09-16
I will try new user tonight and post my results.

---

### Post by ryanhaigh on 2008-09-16
If you have previously run gconf as root/using sudo and made this setting mandatory then you won't be able to change it until you revert that modification. I can't give detailed instructions as I am not on my ubuntu machine but basically press alt-f2 and run gksudo gconf-editor and change the setting in there also making sure it is not manditory.

---

### Post by goodrench on 2008-09-17
I can use gconf-editor as root or with sudo and I can change the setting.
When I go back and use it as a normal user (not with sudo/gksudo) it still says not writable.

---

### Post by ryanhaigh on 2008-09-17
Ok did you figure out how to make sure the setting isn't mandatory?

Open gconf-edior using sudo and go to file>New Mandatory Window and make sure that the setting isn't in there, if it is right click and unset key.

You should also try doing this as your normal user.

---

### Post by goodrench on 2008-09-17
as super user the entry is not in there.
I can go through the side panel tree to get to apps/nautilus/prefs/ but there is not an entry to unset the key.
When I do this as normal user I don't  have the option of selecting New Mandatory Window.

---

