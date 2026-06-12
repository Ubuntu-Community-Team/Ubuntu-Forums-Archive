---
title: "[SOLVED] Ubuntu works bad after overheating"
date: 2008-07-28
forum: General Help
---

### Post by Hyper Tails on 2008-07-28
I have a laptop with vista and hardy (i once used wubi but uninstalled it and partioned my hardrive to install it)
When i was doing things with it to get it up running the thing must of overheated because it shut off on it own (a hard shutdown)
and i rebooted it and there is that poo poo look of the human and other themes ](*,) , i can't open firefox anymore because i click it and it says starting firefox and the hardrive sits there like a potato and after 10-15 seconds it cancles the start of fire fox #-o , Also i the start up sound does not play when i log in my account :confused: and i can no longer update:-({|=
and the shut down screen looks alot different than it orignal look (how wierd)

any help will he thanked alot.
if you know something about it.PLEASE tell me

Laptop:acer aspire 5175-4740
system type:64-bit

---

### Post by nbayiha on 2008-07-28
What were you trying to do before the computer went down ?
Be more explicit when u open a thread . And what happen in the command line when you input firefox. Try to open firefox in the terminal and paste the output here.

---

### Post by gunksta on 2008-07-28
Do applications other than firefox work? Can you post a screenshot or two?

---

### Post by knightcoder on 2008-07-28
Are you able to see the system monitor ??
Check to see if any processes are running, RAM getting used, CPU struggling.

Yeah, as Gunksta said, post a couple of screenshots.

---

### Post by Hyper Tails on 2008-07-29
i'l post some screen shot sometime today to show what is going on and what i'm trying to do

---

### Post by Hyper Tails on 2008-07-29
well here they are

and this is what i was trying to do
[http://ubuntuforums.org/attachment.php?attachmentid=73323&d=1212891748](http://ubuntuforums.org/attachment.php?attachmentid=73323&d=1212891748)

---

### Post by philetus on 2008-07-29
It looks like you have some updates according to screenshot #3.Do the updates.
You also need to find out why it overheated.

---

### Post by todak on 2008-07-29
In a terminal enter this ```
sudo dpkg --configure -a
```. Enter your password at the prompt. Apparently your system shut down before something finished configuring. After that is finished, run the update manager to get any newer updates and then reboot and post what happens.

---

### Post by Hyper Tails on 2008-07-29
i got it now!!!111!!!1

Thanks soo soo much i really aprechiated it

---

