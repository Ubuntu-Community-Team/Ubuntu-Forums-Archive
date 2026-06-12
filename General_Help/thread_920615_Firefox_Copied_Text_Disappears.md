---
title: "Firefox Copied Text Disappears"
date: 2008-09-15
forum: General Help
---

### Post by Jerrac on 2008-09-15
Something odd I have run into a couple times.

I copy the streaming url for a radio station in firefox. Then I have to close firefox to free up the audio stuff. When I try to paste the url into Songbird, it's disappeared. Nothing to paste. Even tried it with gedit, no text. But if I paste the text while firefox is open, it works fine.

So, does Firefox wipe any copied text from the clipboard when closed? Is that a setting somewhere?

---

### Post by jerome1232 on 2008-09-15
This is the norm in Linux, when a program closes so does anything copied into the clipboard from that application.

---

### Post by bingoUV on 2008-09-15
> **Jerrac said:**
> 
So, does Firefox wipe any copied text from the clipboard when closed? Is that a setting somewhere?

Almost.

In fact what happens is this: when you copy text, nothing happens. The text does not get loaded into a special place. Only firefox is selected to be the application holding clipboard. Now when you paste, firefox is asked about the text that was copied. At this time, if firefox is not running at this moment, nothing can be pasted.

This way, if you copy but don't paste, not much effort is made by the system.

---

### Post by Jerrac on 2008-09-15
Huh, interesting. I wonder why I never noticed it before. Thanks for the answer! :D

---

### Post by jerome1232 on 2008-09-15
> **bingoUV said:**
> Almost.

In fact what happens is this: when you copy text, nothing happens. The text does not get loaded into a special place. Only firefox is selected to be the application holding clipboard. Now when you paste, firefox is asked about the text that was copied. At this time, if firefox is not running at this moment, nothing can be pasted.

This way, if you copy but don't paste, not much effort is made by the system.


huh thanks for the explanation, I never knew the why before.

edit: I forgot to put a whole word in there...

---

### Post by Vivaldi Gloria on 2008-09-15
The general view about this copy & paste issue in linux circles is

> cut buffers are evil; they only support ASCII, they don't work with many clients, and they require data to be copied to the X server. Therefore clients should avoid using cut buffers and use only selections.

from [[COLOR="Sienna"]freedesktop.org[/COLOR]]("http://standards.freedesktop.org/clipboards-spec/clipboards-latest.txt").

Here is an interesting [[COLOR="Sienna"]discussion[/COLOR]]("http://mail.gnome.org/archives/desktop-devel-list/2003-September/thread.html#00193") about a clipboard daemon for gnome. It starts as a technical thread but it quickly turns into a discussion of clipboard daemons.

---

### Post by vaerer on 2009-08-06
How can I change this so that if a program is closed while it still has content that is cut / copied ("on the clipboard") the content will stay available to cut and copy commands in other programs ?

---

### Post by alex bodi on 2009-08-07
I have same question as vaerer!
 
Only in my case I need it for symbol copying/pasting between NEdit and CScope. Everytime I select a symbol in NEdit window, I have to close it in order to get back to CScope. That's when I lose the clipboard data.

---

### Post by alex bodi on 2009-08-07
It's funny how in Unix Solaris, I would not lose that clipboard data.
 
I would simply press Shift+Insert to copy (while NEdit is opened) and then press Ctrl+Insert into CScope search area.
 
It doesn't work on Linux Ubuntu though.

---

### Post by vaerer on 2009-08-07
I finally worked it out :D

In Xubuntu (Xfce) you:

1) Install the xfce4-clipman-plugin if it's not there already
2) Right click top window bar and select "Add New Items..."
3) Add Clipman to the bar

I'm not sure about Ubuntu (GNOME) or Kubuntu (KDE) but they will probably have alternatives.

---

