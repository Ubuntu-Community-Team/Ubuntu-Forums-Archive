---
title: "Removing Konqueror's Internet Browser Comonent"
date: 2005-11-19
forum: General Help
---

### Post by cypher35 on 2005-11-19
D'oh, that should be spelled "component" not "comonent", darn edit thing won't let me change it.


Since i use Firefox and not Konqueror to browse the net, i would like to learn how to reset some of Konqueror's functions.

For instance, images and html files should be opened in Gwenview and Kate respectively instead of in the same window.  Also, i don't need it recording history, and i don't need the bookmarks menu.

I would also like to find a way to set my default browser to Firefox so that whenever i click a link in a program like GAIM, it will open in Firefox instead of defaulting to Konqueror.


Also, this is somewhat unrelated to my topic, but still concernes Konqueror.  When open a folder or mounted drive on the desktop, is there any way to get that to open into a new window instead of a new tab?

If any of this possible, even partly, someone please enlighten me.

---

### Post by kaltsi on 2005-11-19
Try the system settings/User account/Default aplications/web browser

---

### Post by lerrup on 2005-11-20
...and the Settings/ configure Konqueror control in Konqueror itself

---

### Post by cypher35 on 2005-11-20
that's odd, the default browser was already set to firefox...  it must be an issue with gaim.

---

### Post by asimon on 2005-11-20
[QUOTE=cypher35]For instance, images and html files should be opened in Gwenview and Kate respectively instead of in the same window. [/quote]
I think you can manage this in the following way:
ALT-F2 and start "kcontrol", choose KDE Components, then File Associations. There go for example to "image" and choose "Show file in seperate viewer" on Left Click Action. You can set this setting also for each single image type. There you can also specify what seperate viewer should be used, gwenview is probably already the default.

[QUOTE=cypher35]
Also, i don't need it recording history, and i don't need the bookmarks menu.[/quote]
In Konqueror choose "Settings", "Configure Konqueror", "History". Setting the history size to zero should probably disable it.

Konqueror does support different profiles. The file management profile already has the bookmarks menu disabled. The browser profile has it enabled. I think Kubuntu is missing a entry in Kmenu to start konqueror directly in filebrowser profile, they only have an entry to start it in the browser profile.

If you want to add/sub some toolbar for the current profile, rightclick on the toolbar, choose "Toolbars" and there activate/deactivate the toolbars you want or not. Then in the settings menu choose "Save View Profile xxxxxxxxxxxx" to save the changes to the profile.

[QUOTE=cypher35]
I would also like to find a way to set my default browser to Firefox so that whenever i click a link in a program like GAIM, it will open in Firefox instead of defaulting to Konqueror.[/quote]
GAIM has it's own setting which browser to use and doesn't follow KDE's settings. In Gaim choose in the menu "Tools", then "Browser" in the tree and set your browser there.

---

### Post by cypher35 on 2005-11-20
Thank you very much!

I don't believe i missed that browser setting in gaim, i feel stupid now...

Cheers

---

