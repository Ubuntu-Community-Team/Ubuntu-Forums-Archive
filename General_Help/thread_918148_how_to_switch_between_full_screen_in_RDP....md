---
title: "how to switch between full screen in RDP..."
date: 2008-09-12
forum: General Help
---

### Post by Mia_tech on 2008-09-12
I'm using RDP in ubuntu to connect to my windows server, but I like to view the RDP console in full screen mode, but when I'm in full screen I can't switch back to ubuntu without first logoff... is there any key that let me toggle between rdp in full screen and ubuntu desktop?


thanks

---

### Post by Mister.Vash on 2008-09-13
I believe for that program, you do the following:

To zoom the Display Area to full screen mode, choose View -> Full Screen (F11). 
To exit full screen mode, press F11 or Ctrl+Alt.

---

### Post by Mia_tech on 2008-09-13
that's a no go.... there's no view option in RDP for ubuntu

---

### Post by sabby on 2008-09-13
Try Ctrl-Alt-Enter.

---

### Post by Mia_tech on 2008-09-13
the answer is to install krdp which is rdp for kde... has a lot more options, and let you switch back and forth with the desktop

---

### Post by cszikszoy on 2008-09-13
> **Mia_tech said:**
> the answer is to install krdp which is rdp for kde... has a lot more options, and let you switch back and forth with the desktop

I think you mean krdc.

Also, as someone else said, pressing ctrl+alt+enter for me will "break out" of full screen.  Actually, it doesn't really break out of fullscreen.  It allows linux to capture the keys.  So if you press ctrl+alt+enter and alt tab, it will use the host's alt-tab, not the alt-tab action on the guest.

Does that make sense?

---

### Post by Mia_tech on 2008-09-14
that's a lot of fingers for a lot of keys...I'm better off clicking the mouse... lol

---

### Post by chender on 2009-09-22
suggest you google rdesktop or rdesktop --h

rdesktop -A

for seamlesss mode.  I find it best to keep rdesktop in a different workspace and with the -A switch you can simply move in and out that way.

---

