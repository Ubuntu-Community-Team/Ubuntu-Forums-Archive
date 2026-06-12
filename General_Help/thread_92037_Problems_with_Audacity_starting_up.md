---
title: "Problems with Audacity starting up"
date: 2005-11-18
forum: General Help
---

### Post by darknuala on 2005-11-18
Whenever I try to start Audacity, I get the following error message.

Error Initializing Audio
There was an error initializing the audio i/o layer.  You will not be able to play or record audio.
Error:  Host error

I don't have any problems with sound in Breezy, so what could be the problem?

*Update*
I can log into xfce and audacity works fine.  But there are 2 icons for audacity, one with an icon on the menu, and one with just text.  The one with just text works?  What could be going on in gnome to prevent it from working?

---

### Post by lreyes6 on 2005-11-21
i have the same problem? any ideas? will try with xfce but i don't want to switch from gnome to xfce just because of audacity...

thanks

---

### Post by 0okami on 2005-11-22
[QUOTE=darknuala]Whenever I try to start Audacity, I get the following error message.

Error Initializing Audio
There was an error initializing the audio i/o layer.  You will not be able to play or record audio.
Error:  Host error

I don't have any problems with sound in Breezy, so what could be the problem?
[/QUOTE]

Interesting... Same problem here.

---

### Post by Bachstelze on 2005-11-22
Same here...

---

### Post by joshpelkey on 2005-11-22
try "sudo killall esd" at the terminal and then start audacity.  audacity doesn't play nice with esd, unfortunately.  some people have created a small script for launching audacity; first killing esd; then launching.

---

### Post by darknuala on 2005-11-22
[http://www.linuxdevcenter.com/pub/a/linux/2005/11/17/ubuntu_laptop.html?page=4](http://www.linuxdevcenter.com/pub/a/linux/2005/11/17/ubuntu_laptop.html?page=4)

Killing ESD fixed it.
There'a a link above of a review of Ubuntu on a laptop, that mentioned the same thing today.  How odd!  

Thanks GUYs!

---

