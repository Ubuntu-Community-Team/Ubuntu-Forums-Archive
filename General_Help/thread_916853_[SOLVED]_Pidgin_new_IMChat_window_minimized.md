---
title: "[SOLVED] Pidgin new IM/Chat window minimized"
date: 2008-09-11
forum: General Help
---

### Post by gen.alcazar on 2008-09-11
I'm using Ubuntu Hardy 8.04, GNOME 2.22.3 and Pidgin 2.4.1.  I'm trying to figure out a way to ensure that new IM/Chat windows start minimized to the panel.  Just to clarify:

1. I am not looking for the new IM/Chat windows to start minimized to the tray, rather to the window list in the panel.  I have the window hint set to "urgent" to grab my attention.
2. I tried using devilspie to achieve this, but this causes inconsistencies in the "urgent" hint being set.  So I'm trying to figure out if there's another way to do this.
3. I was using KDE until not long ago, and it was easy to achieve this using the KDE window manager, but still trying to figure this out in GNOME.

Anyone know how I can achieve this?

Thanks!

---

### Post by Sycron on 2008-09-11
I don't understand. You want Pidgin to start minimized ?

---

### Post by gen.alcazar on 2008-09-11
> **Sycron said:**
> I don't understand. You want Pidgin to start minimized ?

No.  I'm looking for new IM/Chat-message windows to start minimized.  I end up using my laptop for a lot of presentations, and every now and then, I will forget to log off of IM.  Trying to make sure that the whole room doesn't end up seeing my IMs on the large screen when situations like that happen.  At the same time, I would like the "Urgent" hint on the window to work so that I don't miss new IMs.  Hope I'm clear.

I figured out a way to do this in a slightly inefficient manner, if someone has a better way to do this, please feel free to suggest.

1. In Pidgin, configure the "Message Notification" plugin to
[INDENT]Notify For -
[INDENT]- IM windows
- Chat windows[/INDENT][/INDENT]

[INDENT]Notification Methods -
[INDENT]- Set window manager "URGENT" hint[/INDENT][/INDENT]

[INDENT]Notification Removal -
[INDENT]- Select all *EXCEPT* for "Remove when conversation window gains focus".  This was causing the urgent hint to not be set at times when used in conjunction with devilspie.  My theory is, at times, devilspie minimizes the window after it gains focus, thereby causing the urgent hint to be removed.  Unchecking this options lets the urgent hint remain even after the window is minimized - consistently.[/INDENT][/INDENT]

2. Use devilspie to identify chat window and minimize.

```
(if 
        (and
                (is (application_name) "Pidgin")
                (not (is (window_name) "Buddy List"))
        )
        (begin
                (shade)
                (minimize)
                (pin "TRUE")
        )
)

```

Please note that the (shade) action was also necessary to achieve consistency in setting of the urgent hint.

---

### Post by morgue on 2010-04-12
Kind of works, but if you are the one opening the window, it also starts minimized, which is kind of annoying.

---

### Post by bonfire89 on 2010-07-02
this method opens the window then minimizes it. 

1. It's annoying because you see the window flash
2. I'm using cairo dock and because the window opens and then minimizes it loses it's "needing attention" state, which means there will be nothing to indicate that I have a new message since the message was already looked at for a split second when the window flashes open.

---

