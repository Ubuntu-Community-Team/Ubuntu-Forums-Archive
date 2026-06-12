---
title: "LCD Frequency Range"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by domstyledesign on 2005-07-24
obviously there are plenty of posts about setting the frequency range for an LCD monitor... but my problem is a little different.  my monitor also says "frequency out of range," however, if i switch to a virtual terminal (ctrl+alt+f1) and then back (ctrl+alt+f7), everything is fine.  i also tried to cycle the monitor's power, but that doesn't work at all.

why does it get the wrong frequency before, but correct frequency after switching in and out of a virt. term.?  and how can i fix it?

(although, it's almost an added security feature, but more of an inconvience)

---

### Post by domstyledesign on 2005-07-26
(i really hate doing this)

*bump*

---

### Post by tristan on 2005-07-26
Your problem is because X is trying to set a different frequency than your terminals. When I 1st hooked up an LCD monitor I had exactly the same problem. 

You need to edit the Xorg config file

sudo gedit /etc/X11/xorg.conf   

I can't remember the exact line (I'm at work, on lunch break of course!!) but there should be line with the monitor frequency. For LCD monitors 60-75Hz should be OK.

Once you've edited and saved, hit ctrl-alt-backspace to restart the X server.

Sorry I can't be more specific, but I hope this helps.

---

### Post by domstyledesign on 2005-07-26
yeah, i put in the HorizSync & VertRefresh attributes in there, using the specs from my monitor's manual.

what's really weird is this:  when my monitor displays the "out of range" message, it shows the current frequencies.  One of them (i think the horiz) is out of the range specified in the conf file! ...crazy.

---

### Post by domstyledesign on 2005-07-27
*bump* *again*

anybody?

---

