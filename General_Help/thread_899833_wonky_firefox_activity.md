---
title: "wonky firefox activity"
date: 2008-08-24
forum: General Help
---

### Post by HarmonicaGoldfish on 2008-08-24
Lately firefox has been shutting down with no warning. It has been happening more often this past week or so.

So I opened it via terminal to see what was going on and this is what I get the next time it shut down:

(the first part, up until segmentation fault was repeated over and over again in the terminal.)
> (firefox:11071): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:11071): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
tracy@tracy-laptop:~$ 

Then when I went to re-open firefox I got this:

> Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIStringBundle.formatStringFromName]

and all of my customizations, including bookmarks are gone.
Though if I open it via the terminal it is ok.

Anyone know what is going on? It is very frustrating to be in the middle of doing something and bam - browser disapears! 

thanks...

oh, I checked if I had the latest version, apparently I do.
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1


I'm running 8.04 on a dell inspiron 1525 laptop

---

### Post by HarmonicaGoldfish on 2008-08-25
Even after a reboot, I can seem to only open firefox through the terminal (sudo firefox). If I use the icon in my panel, the one I always use, I get this message:

> Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIStringBundle.formatStringFromName] 

Does anyone know what that means and why this is happening?


As well, the other issue re: firefox shutting down suddenly. Still a mystery.

Thanks for any help!

---

