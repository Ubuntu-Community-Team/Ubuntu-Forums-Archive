---
title: "Possibly to theme root windows differently?"
date: 2008-11-26
forum: General Help
---

### Post by secondstage on 2008-11-26
Somehow, in 8.04, the root windows were themed differently, but now that I've installed 8.10, I miss it. Is there a way to make the root windows have a completely different theme?

---

### Post by eternalnewbee on 2008-11-26
> the root windows 
What are the root windows?

---

### Post by hambone79 on 2008-11-26
By root windows I assume you mean GUI programs launched as root. If so, you should be able to run the following command and get access to change the theme used by root:

```

gksudo gnome-appearance-properties

```

---

### Post by secondstage on 2008-11-26
By root windows, I do mean GUI programs launched as root. The command from hambone79 doesn't work. I open the window properties, and select a different theme, but it isn't applied to 'sudo gedit'.

---

### Post by lswest on 2008-11-26
you can copy the themes to /root/.themes/ and /root/.icons/ and then set the proper themes you want using the gksudo gnome-appearance-properties command to choose which to use.

---

### Post by DJ_Peng on 2008-11-26
Thanks! I was about to look for info on how to do this myself.

---

### Post by fballem on 2008-11-26
As far as I can tell, you don't need to copy anything before using the gksudo gnome-appearance-properties command. Once you execute it, you can select from the existing themes, backgrounds, and icons.

---

### Post by lswest on 2008-11-26
> **fballem said:**
> As far as I can tell, you don't need to copy anything before using the gksudo gnome-appearance-properties command. Once you execute it, you can select from the existing themes, backgrounds, and icons.

My experience is that you'll have to re-install themes you want, so I just copy the .themes and .icons folders from my home folder to the /root/ folder.  However, I usually do this to get RID of the different themes.  Might be unnecessary, but it works.

And thanks for the thanks.

Oh, also, you can set the theme that's being used with terminal commands: ```
sudo gconftool-2 -s *theme_name* /desktop/gnome/interface/gtk_theme
sudo gconftool-2 -s *theme_name* /apps/metacity/general/theme
sudo gconftool-2 -s *theme_name* /desktop/peripherals/mouse/cursor_theme
sudo gconftool-2 -s *theme_name* /desktop/gnome/interface/icon_theme
```
I'm not sure exactly which theme the top 2 commands will change, and the theme names will be those described in the index.theme file.  I use this in a theme script to pull the values and show them, don't know if it will apply changes if you change the values, though I would assume so.  Please let me know if it does indeed work.

---

