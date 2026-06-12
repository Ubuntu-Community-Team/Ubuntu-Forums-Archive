---
title: "Internet Card"
date: 2010-06-28
forum: Hardware
---

### Post by Automag05 on 2010-06-28
Hi all, this is my first post on Ubuntu Forums so I apologize if I did not post this in the correct area.

I am new to Ubuntu and if anyone could give me some advice on how I may acquire wireless internet connection on my laptop it would be greatly appreciated.

I went to the terminal and typed in "lspci" and my network controller popped up as "Broadcom Corporation BCM4312 802.11b/g"

I noticed it was suggested in another thread to type "echo wl | sudo tee -a /etc/modules"
I am not sure what that does... it was just advised. 

When I do so, I get [sudo] password for mycomputer

I am not sure what to do with that information. 
If anyone could tell me what do do at this point, I would appreciate it

---

### Post by aphatak on 2010-06-28
The 'sudo' allows a command to run with special (root) privileges.  When you see the prompt, key in the password you normally log in with - I am assuming you installed Ububtu yourself.  If someone else did, and created your account for you, you will have to ask that someone to do it for you.  Let me know if this worked.

---

### Post by Automag05 on 2010-06-28
Thanks for the reply, 
I tried to type my password in directly across from "[sudo] password for my computer" but I was unable to type, so I hit enter first and typed beneath and "Sorry, try again" popped up.
Maybe I did something wrong?

---

### Post by aphatak on 2010-07-01
When you type in response to the '[sudo] password ...' prompt, your response does not show up, but the system is still reading it.  This is tricky - if you mis-type a character, you won't see it; you won't even know if a keystroke simply did not register.  So it is possible that your password was not keyed in correctly.  I should try it again.

---

