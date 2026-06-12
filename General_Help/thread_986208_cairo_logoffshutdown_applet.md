---
title: "cairo logoff/shutdown applet"
date: 2008-11-18
forum: General Help
---

### Post by lunar cranium on 2008-11-18
hey guys.  i'm trying to set up an applet/launcher in my dock, and i want it to display this menu:
[IMG]http://i37.tinypic.com/20pr98o.jpg[/IMG]

instead of this one:
[IMG]http://i36.tinypic.com/2lt2hbn.jpg[/IMG]

the last one is the default on the dock.  i'd like to be able to change it to the first pic.

does anyone know how to launch the first menu from terminal?  i'm in ubuntu 8.10 with the cairo dock and compiz.  

thanks for any help you can provide!

---

### Post by hansaplast on 2008-11-30
Any luck with this problem? After upgrading to 8.10 I'm facing the same issue.

---

### Post by kawaji on 2008-11-30
```
gnome-session-save --shutdown-dialog
```

---

### Post by whoeva on 2008-11-30
That's right, I had the same problem. Changing the executed code to the one posted above fixed it for me.

---

### Post by Tankerdog2002 on 2009-08-31
Hey KAWAJI! Thank you sir!

I've been trying to figure this out for weeks now.](*,)

Your code for cairo logoff/shutdown applet applet worked like a charm.

---

### Post by fabounet on 2009-09-01
hmm, the logout applet that is provided in the plug-in package has 2 actions :
right clic and middle clic
that's probably what you want.

---

### Post by edxabbey on 2009-10-26
> **kawaji said:**
> ```
gnome-session-save --shutdown-dialog
```
I can't wait to see if this fixes my issue.  I have tried the ~sudo shutdown -h now, no avail.  I'll try it on my desktop tonight.

---

### Post by edxabbey on 2009-10-27
> **edxabbey said:**
> I can't wait to see if this fixes my issue.  I have tried the ~sudo shutdown -h now, no avail.  I'll try it on my desktop tonight.

I couldn't see the screenshot of what it actually did when I posted at work.  This was better than I had hoped.  Thanks!

---

### Post by fabounet on 2009-10-27
again, the middle click will raise the first window, the left click will raise the other.
you can invert the buttons in the config.
hope this helps

---

