---
title: "[SOLVED] Firefox tabs all white?"
date: 2008-07-18
forum: General Help
---

### Post by cdtech on 2008-07-18
I have no idea. Firefox is the only window this is happening to so I know its not the desktop settings.

Anyone else having this issue?

---

### Post by cdtech on 2008-07-26
This is in regards to the toolbar font being all white. I have no idea how it became that way, unless one of my themes changed it, anyway.

This is how I was able to change the toolbar colors:

You need to create a userChrome.css file (if it's not already created for you)

**Open** Places > Home Folder

**In the folder toolbar select show hidden files**

**open** .mozilla > firefox > *.default (the default folder)> chrome

**If you have the userChrome.css file then:**

**right-click** "userChrome.css" and select open with “text editor”

modify the code at the bottom of the page so it looks like this:

```
menubar, menubutton, menu, menuitem, menupopup, popup > * {
color: black !important;
}
```

**Save the file**

When you restart Firefox your font will be black

**If you don't see the "userChrome.css" but have a "userChrome-example.css":**

**right-click** "userChrome-example.css" and select open with “text editor”

Modify the code at the bottom of the page so it looks like this:

```
menubar, menubutton, menu, menuitem, menupopup, popup > * {
color: black !important;
}
```

**Save the file as "userChrome.css"**

**Restart firefox**

If you want the text to be white just add this code:

```
menubar, menubutton, menu, menuitem, menupopup, popup > * {
color: white !important;
}
```

---

