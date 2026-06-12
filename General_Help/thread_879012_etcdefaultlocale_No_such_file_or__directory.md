---
title: "/etc/default/locale: No such file or  directory"
date: 2008-08-03
forum: General Help
---

### Post by gardara on 2008-08-03
I changed to slim login manager while ago, but it wasn't as great as I thought so I changed back to gdm, but now every time I try to log in I get a error message about my session only lasting less than 10 minutes and then this error from .xsession-errors

```
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/20slim_locale: line 1: /etc/default/locale: No such file or 
directory
```

Anyone that knows what's wrong?

---

### Post by hal8000 on 2008-08-03
> **gardara said:**
> I changed to slim login manager while ago, but it wasn't as great as I thought so I changed back to gdm, but now every time I try to log in I get a error message about my session only lasting less than 10 minutes and then this error from .xsession-errors

```
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/20slim_locale: line 1: /etc/default/locale: No such file or 
directory
```

Anyone that knows what's wrong?


From the error message it looks as though 20slim_locale is still being executed. Try removing slim with apt-get or alternatively recreate the locale file with:
sudo touch /etc/default/locale

---

### Post by Elfy on 2008-08-03
If it was me I would move the file out and see if the error went - but then I can be a bit "bull in a china shop"

I don't think I've changed anything in that folder or whether it would be changed without installing something else, but this is the contents of my /etc/X11/Xsession.d

> 20x11-common_process-args       55gnome-session_gnomerc  80ubuntu-xmodmap
30x11-common_xresources         60seahorse               90-console-kit
40x11-common_xsessionrc         60xdg-user-dirs-update   90x11-common_ssh-agent
50x11-common_determine-startup  80im-switch              99x11-common_start

It would certainly appear to me that if you've got rid of the slim manager - it's likely that the 20slim_locale wouldn't be needed.

But that is all supposition...


Edit - I wrote that before the above answer - I would go with that first :)

---

### Post by drs305 on 2008-08-03
All that is in my locale file is this:
```

LANG="en_US.UTF-8"
LANGUAGE="en_US:en"

```

If you want to make the file (if you use US english):
```

sudo touch /etc/default/locale
sudo echo LANG="en_US.UTF-8" > /etc/default/locale
sudo echo LANGUAGE="en_US:en" >> /etc/default/locale

```

That will create the file. Whether or not it will satisfy other dependencies I can't tell you.

---

### Post by gardara on 2008-08-07
Simply removing slim fixed the problem... Thanks for the other tips tho guys... Hope it will help someone else :)

---

