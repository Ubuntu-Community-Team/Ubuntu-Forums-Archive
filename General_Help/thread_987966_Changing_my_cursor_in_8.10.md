---
title: "Changing my cursor in 8.10"
date: 2008-11-20
forum: General Help
---

### Post by Oplix on 2008-11-20
I've followed several walk-throughs on how to do this but can't figure it out.

The simples drag+drop method to install the cursor theme didn't seem to work. Nothing happened when I dropped the tarball into the window. Also tried dropping the extracted folder.

I've also tried extracting the files into /use/share/icons. No luck on that.

I'm running 8.10, and despite how easy everyone says this should be to do, none of their methods have seemed to work for me.

---

### Post by trendyabinash on 2008-11-20
I think this will help you out

Changing Mouse Cursor Themes

    * Download the theme to an easily accessible location; ~/Desktop is good.
    *

      Install the gcursor package via Synaptic Package Manager or apt-get.
    *

      Start gcursor with System &#8594; Preferences &#8594; Cursor Selection.
    * Select a theme, or click 'Install theme' and select the compressed file to add it.
    * Once you're finished, select the theme you want to use and click "Close"

---

### Post by trendyabinash on 2008-11-20
Sorry that previous method is not working
try this it will do the trick

system-->preferences-->appearance-->customise-->pointers

---

### Post by trendyabinash on 2008-12-17
you can also change by typing the cursor name
in the CompizConfig manager under general tab

---

### Post by ScottyJavea on 2008-12-23
> **trendyabinash said:**
> Sorry that previous method is not working
try this it will do the trick

system-->preferences-->appearance-->customise-->pointers
Thanks,

That worked OK.
GCursor did not.

Regards,
ScottyJavea

---

