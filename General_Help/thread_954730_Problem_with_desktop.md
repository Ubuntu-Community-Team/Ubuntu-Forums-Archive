---
title: "Problem with desktop"
date: 2008-10-21
forum: General Help
---

### Post by Solarplight on 2008-10-21
my desktop is displaying everything in my /home/*usr folder.  How do i change it back so it just displays the contents of my Desktop folder?

---

### Post by cmnorton on 2008-10-21
This is a long-shot answer, but what line is at the bottom of:

~/.kde/Autostart/.directory 

I have this:

X-Ubuntu-Gettext-Domain=desktop_kdebase

This is a good question. I cannot find what the default display directory is for the desktop, unless it's what I've listed.

---

### Post by Solarplight on 2008-10-26
I can't find that file

---

### Post by cmnorton on 2008-10-27
ls -la | grep .kde

---

### Post by Solarplight on 2008-10-28
Found it, thank you.

The bottom line on my .directory file is the exact same as yours.

---

### Post by jabeez on 2008-10-28
are you using KDE 4? if so it is the folder view widget, in which you can pick what folder to display (or none at all).

---

### Post by Solarplight on 2008-11-04
nope

---

### Post by editrix on 2008-11-06
This is more by way of diagnostics, but the info could help us figure out what's going on.

First, choose some file in your home directory that has a unique name, then in the terminal type:

```
locate nameofthatfile
```

and post the results.

Also, what does Konqueror have to say about your Desktop directory? What's in it?

And, do you have /home on a separate partition?

---

### Post by Solarplight on 2008-11-06
heres the output

  /home/cable/duckballs
  /home/cable/duckballs/analysis
  /home/cable/duckballs/dead_sounds
  /home/cable/duckballs/duckballs.ardour
  /home/cable/duckballs/duckballs.history
  /home/cable/duckballs/export
  /home/cable/duckballs/instant.xml
  /home/cable/duckballs/interchange
  /home/cable/duckballs/peaks
  /home/cable/duckballs/interchange/duckballs
  /home/cable/duckballs/interchange/duckballs/audiofiles

My Desktop folder is currently empty.  I have full permissions.  The properties look good to me.

And I have only one partition.

---

### Post by editrix on 2008-11-08
Ah well, I was hoping for something simple, like somehow you'd moved /home into the /Desktop folder.

> My Desktop folder is currently empty.

I don't think it should be. Been a while since I installed, but I think at least the floppy drive icon (if you have a floppy drive) shows up on the desktop. What happens if you use a USB stick? Does that icon show up on the desktop? Or a music CD or a DVD?

Hmm ... Did you ever install Ubuntu? i.e., with the Gnome desktop? I just did an Uboontu search (last link in my sig) for **home appears on desktop** and it seems to be a Gnome bug.

I guess you'd better check out the links on Uboontu, but since this is KDE, I'd also make sure you're using kdm and not gdm.

---

### Post by Solarplight on 2008-11-11
My Desktop folder is empty, when i put any type of disk(usb, cd) it displays in my desktop view witch is actually my #home/cable file.

---

### Post by editrix on 2008-11-11
First off, I'm hoping that #home/cable file is a typo for [COLOR="Red"]$[/COLOR]home/cable [COLOR="Red"]directory[/COLOR]

Because the # means you're logged in as root, and that could explain a lot.

Second, please answer the following questions from my previous post:

> Did you ever install Ubuntu? i.e., with the Gnome desktop? 
> make sure you're using kdm and not gdm
And then let us know if you researched the links on Uboontu.

---

### Post by Solarplight on 2008-11-22
Yes i originally istalled it that way. how would i check if i am using kdm?

---

### Post by swoody on 2008-11-22
> **Solarplight said:**
> how would i check if i am using kdm?

Log out, and when the login window is displayed, is it the fancy looking KDE login window, or the Ubuntu/Gnome login window?

But first unlock your widgets, and rollover the desktop box/window thingy. When the bar with the options on the side of it displays, click on the wrench for more options. Is the "Show Desktop" selected instead of "Show a custom folder"? And is your filter set to "*"(without quotes)?

---

