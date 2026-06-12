---
title: "[monitors setup] why there's no simple GUI for the xorg.conf? Microsoft does it well"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by adhg on 2007-08-22
Hi all,

So...I'm newbie to Linux and so far its going *really* good! I'm impressed. I wanted to install kubuntu on my office-computer but there's one major problem: I have 4 monitors connected to my computer. 

Now, Windows (the 'other' company) provides a very good mechanism to set-up the screens. They provide the user a GUI and all you need to do is couple of clicks...and it's working. So simple... even a caveman can do that ;-) 

I spent nearly 5 hours today, trying to figure it out 'how to' connect all 4 monitors to work with kubuntu. I learned that I need to change the /etc/X11/xorg.conf
well...this assumes that I need to know my video cards, monitors etc...

Question: isn't there any simple GUI that I can use to avoid editing the xorg.conf? 
I tried (in kubuntu) the System-Settings-->Hardware (administrator mode) but couldn't execute the TEST. so no monitors were selected (I'm using 2 monitors of 24" and 2 monitors of 15". both DELL)

Thanks to any pointer!!!

---

### Post by stinger30au on 2007-08-23
there is a GUI for this... its in beta stage at the moment

---

### Post by tseliot on 2007-08-23
Ubuntu's next release will have a nice GUI.

---

### Post by adhg on 2007-08-23
> **tseliot said:**
> Ubuntu's next release will have a nice GUI.

any suggestions what to do now? 
(is there a simple tutorial anyone knows that solves the problem?)

thanks for your replies

---

### Post by tseliot on 2007-08-23
What's your graphic card model?

---

### Post by adhg on 2007-08-23
As I'm using windows right now, it suggests:

RADEON x300 SE 128MB HyperMrmory
RADEON x300 SE 128MB HyperMrmory Secondary

---

### Post by tseliot on 2007-08-23
Did you install ATI's proprietary driver?

---

### Post by adhg on 2007-08-23
I'm not sure what you mean by: "ATI's proprietary driver?"
thanks

---

### Post by tseliot on 2007-08-23
the "fglrx" driver

---

### Post by adhg on 2007-08-23
;-)
I guess I have no idea. I'm a complete newbie (I'm 2 month Linux old) but I'm growing...
So...how do I install the ATI's driver? if I use the system it works fine but only with one screen (24")
want me to post the  xorg.conf?

thanks for your help.

---

