---
title: "Manual removal of Adobe Reader 8.12"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by BhumibolTheGreat on 2009-04-20
Hi guys, 

I had Adobe Reader 8.12 installed on Ubuntu 8.04, after while I have upgraded to Ubuntu 9.04.
And now every time I'm trying to open PDF file from my browser I get an error saying Adobe Reader can not be found. 
I could see that there is existing Adobe folder under my /home/user 
What is the safest way of removing the /home/user/.adobe/Acrobat folder without causing things to brake (even though they are already broken ;))
Is there a way to check for dependencies?

Thanks,

---

### Post by ajgreeny on 2009-04-20
Can you look in synaptic and remove it there?  If so, do it, and then reinstall if you want it back, and all dependencies should be sorted for you.

---

### Post by BhumibolTheGreat on 2009-04-20
Oh yeah, and I forgot to mention that Adobe Acrobat doesn't show up in the add/remove list ;)
Obviously that if it was there, I wouldn't ask this question. 

Thanks for your reply though!

---

### Post by krgp on 2009-04-23
Same problem here. (Newb who doesn't know how to remove programs that don't appear in Add/Remove list.)

---

### Post by m_2009 on 2009-04-23
Try installing Adobe reader 9.1.0??

Its available on the adobe website as a deb package, so that should overwrite any previous versions i think?

---

### Post by krgp on 2009-04-24
Here's what I did.

Manually removed the 8.x version that was crapping up my update manager in terminal: sudo apt-get remove acroread.

Then, I re-added acrobat and it automatically went for version 9.x: sudo apt-get install acroread. 

So stupidly easy. Someday I'll get the hang of this biz.

---

