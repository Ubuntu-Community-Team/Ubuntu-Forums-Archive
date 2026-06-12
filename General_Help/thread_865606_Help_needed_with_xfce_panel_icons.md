---
title: "Help needed with xfce panel icons"
date: 2008-07-20
forum: General Help
---

### Post by Wim De Winter on 2008-07-20
Hi,
I customized my panel by following the tips on this blog : [http://jozmak.blogspot.com/2007/04/optimizing-xubuntus-user-interface.html]("http://jozmak.blogspot.com/2007/04/optimizing-xubuntus-user-interface.html") . All went well, but there are just some minor "finishing touch" issues.

1. As mentioned in that blog I added the .gtkrc-2.0 file in my home folder. This is it:
> style "panel"
{
bg[NORMAL] = "#909599"
xthickness = 0
ythickness = 0
}

widget_class "*Panel*" style "panel"
widget "*Panel*" style "panel"
class "*Panel*" style "panel"

style "xfdesktop-icon-view"
{
XfdesktopIconView::label-alpha = 0
#Text colors you can delete these if you want you use gtk theme colors
fg[NORMAL] = "#909599"
fg[SELECTED] = "#00ff00"
fg[ACTIVE] = "#0000ff"
}

widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

I like it, but the issue is that when the mouse pointer moves over the icons, the background of the icons (which are .png files with a transparent background) becomes white. Where/how can I change this to the panel background?

2. Some of the icons didn't change to the installed and selected nimbus theme. The icons include are the trash-can icon and the mail-icon from the. I can't seem to find  a good e-mail icon in the icon-repository in /usr/share/icons/nimbus , but that's just me. More worrying is that the trash-bin icon in xfce seems to bet set by default and can't be changed? Any one has any suggestions on how to work around this? When I emptied the bin just yet, the "correct" nimbus "empty bin" icon showed up. How is this possible?

---

### Post by Wim De Winter on 2008-07-29
no one? (one-week-bounce)

---

