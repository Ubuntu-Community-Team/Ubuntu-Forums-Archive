---
title: "Using SCIM and ATOK at the same time?"
date: 2008-11-15
forum: General Help
---

### Post by violagirl23 on 2008-11-15
How would I do this? I hate scim-anthy with a passion (I think the conversion and learning ability is just GOD awful) so I finally broke down and bought ATOK. I got the download version and it took me forever to figure out how to install it, but once I finally got it working, I'm quite pleased with it. It's great and I love it. The only problem is that I occasionally need to type in Korean too, so I need Scim for that. ATOK starts up automatically no problem but SCIM does not. If I manually start Scim, of COURSE the only way I can use it is by right-clicking and changing the input method manually to Scim. I set up the key bindings to avoid conflict with ATOK, removing all scim keybindings except a custom alt-~ to toggle it on and off (this turns on and off Korean), but I still can't get it to start w/o ATOK not working. I tried making the file /etc/X11/Xsession.d/74custom-scim_startup and I put the following in it:
```
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"
```
and then scim starts automatically. However, then ATOK won't start. How can I get it so I can use BOTH of them, seeing as I need them for entirely different things?

---

