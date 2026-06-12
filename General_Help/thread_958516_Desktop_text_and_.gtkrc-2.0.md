---
title: "Desktop text and .gtkrc-2.0"
date: 2008-10-25
forum: General Help
---

### Post by small_sammy on 2008-10-25
Hi there,

I am trying to remove the background color from the text of my desktop icons.
I am using xubuntu 8.04 and did my google research on how to do that...

All articles where refering to create a .gtkrc-2.0 file in my home directory and put some settings there...
Namely the setting I have are :

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 75

    base[NORMAL] = "#00ff00"
    base[SELECTED] = "#5050ff"
    base[ACTIVE] = "#0000ff"

    fg[NORMAL] = "#ff0000"
    fg[SELECTED] = "#ff0000"
    fg[ACTIVE] = "#ff0000"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

However logging out and back in, does not remove the background color...
I tried by giving the command 
source .gtkrc-2.0 
and what i got back is

style: Opening `xfdesktop-icon-view' failed (No such file or directory).
style: Opening `{' failed (No such file or directory).
No sentences found.
bash: XfdesktopIconView::label-alpha: command not found
bash: base[NORMAL]: command not found
bash: base[SELECTED]: command not found
bash: base[ACTIVE]: command not found
bash: fg[NORMAL]: command not found
bash: fg[SELECTED]: command not found
bash: fg[ACTIVE]: command not found
bash: .gtkrc-2.0: line 11: syntax error near unexpected token `}'
bash: .gtkrc-2.0: line 11: `}'

Any ideas on what i am doing wrong here?
Thanks for reading this.!

---

### Post by small_sammy on 2008-10-25
Well after doing a restart it was actually fixed...

I am feeling a bit stupid now, but what the heck... :)

---

