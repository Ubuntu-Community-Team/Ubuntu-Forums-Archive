---
title: "Microphone Does not Work"
date: 2010-09-06
forum: Hardware
---

### Post by Lyude on 2010-09-06
Hello, I use a acer 6530G on amd64 ubuntu 10.4, and I noticed that my microphone does not work. Speakers and headphones seem to work fine, but not my microphone (internal and external). I cannot seem to find a working solution on google, could someone help me out? I would give more information, but I'm not exactly sure what would be relevant to this.

---

### Post by MISIEKasd on 2010-09-06
Hi everyone ):P
I have the same problem, I'm still looking for working solution (on google), but all doesn't work.  I use HP dv5 
Do you know how to fix it ?

---

### Post by ajgreeny on 2010-09-06
Try running **alsamixer** in terminal and see if any of the levels are set too low or muted;  it seems to often be the case, for some weird reason.

---

### Post by Lyude on 2010-09-06
Nope, already tried that

---

### Post by Lyude on 2010-09-06
Bump

---

### Post by Lyude on 2010-09-06
OK, Pulse audio is the devil. I found out how you fix it:
Go into Synaptic, and mark pulse audio for removal. Now this will also mark the indicator applet for removal, so scroll down to that and unmark it (if you don't you'll lose the little sound icon on your Gnome panel). Then mark esound and gstreamer0.10-esd for installation. After that, you might have to mess with your audio settings to get it to work (I set my main audio card to analog stereo duplex, and turned up the mic a lot, and it worked after that), but it should work.
Ubuntu REALLY needs to stop relying on pulseaudio.
EDIT: I just read something that said that this fix can break updates. So be careful when using this fix. There's one that says it doesn't break updates, I have yet to try it though: [http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

---

### Post by AlexZaim on 2010-09-06
[try this]("http://ubuntuforums.org/showpost.php?p=9486962&postcount=62")

don't forget to check system>pref>sound

---

