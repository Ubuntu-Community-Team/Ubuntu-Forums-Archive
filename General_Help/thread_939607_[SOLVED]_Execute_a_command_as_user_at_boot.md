---
title: "[SOLVED] Execute a command as user at boot"
date: 2008-10-06
forum: General Help
---

### Post by martin_legion on 2008-10-06
Hello, I need a command to be executed as a user, not root, at boot. I thought putting the command in .bashrc or something like that, but I guess that if the user doesn't open any terminal the command won't execute. Is there any other place where I can put that command so it executes no matter what the user does?
Thanks

M.

---

### Post by Elfy on 2008-10-06
Make a script and run it in sessions would be possible

---

### Post by martin_legion on 2008-10-06
> **forestpixie said:**
> Make a script and run it in sessions would be possible

What do you mean with "run it in sessions"?
Tks.

---

### Post by Elfy on 2008-10-06
Add it to System > Preferences > Sessions

It will, I think, be run each time user logs in

---

### Post by bogdan.veringioiu on 2008-10-06
Hi.

You could try something like this:

Edit /etc/rc.local 

add a line like this:

su myUser -c /home/myUser/scripts/myScript.sh

Regards.

Bogdan

---

### Post by martin_legion on 2008-10-06
> **bogdan.veringioiu said:**
> Hi.

You could try something like this:

Edit /etc/rc.local 

add a line like this:

su myUser -c /home/myUser/scripts/myScript.sh

Regards.

Bogdan



That's exactly what I was looking for.
Thanks a lot.

Martín.

---

### Post by Calmatory on 2008-10-06
Don't forget to add [SOLVED] to the title so others find the right thread faster and easier from e.g. Google. Thanking him(blue ribbon next to Multi-Quote button) wouldn't hurt either. :)

---

### Post by martin_legion on 2008-10-06
Done! ;)

---

