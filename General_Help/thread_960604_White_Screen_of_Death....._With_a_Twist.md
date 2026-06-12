---
title: "White Screen of Death..... With a Twist"
date: 2008-10-27
forum: General Help
---

### Post by Buzzbait on 2008-10-27
I installed a new ATI video driver last night, which required that desktop effects be turned off. I turned it off, when logged in as myself, and all was well. There was no big problem until I tried to log in as root. The root "profile" seems to have visual effects still turned on, and now I only get the **White Screen of Death** when logging in as root. ](*,) I have no idea how to turn off visual effects for only a certain "profile". Any ideas?

Forgive my lack of proper terminology.  I'm a Linux noob crossing over from the Land of Gates.

---

### Post by dracayr on 2008-10-27
You shouldn't log in as root anyway. If you want to have root permissions, theres sudo to do that.

dracayr

---

### Post by Buzzbait on 2008-10-27
Great idea, but until I learn all of the terminal commands, I still to log in as root occasionally.

---

### Post by koenn on 2008-10-27
> **Buzzbait said:**
> Great idea, but until I learn all of the terminal commands, I still to log in as root occasionally.

No, you use sudo for running terminal commands as root, or gksu for GUI apps as root. you never need to log in as root - ubuntu is designed that way.

---

### Post by Buzzbait on 2008-10-27
The problem is that I do not yet know the terminal commands, which makes sudo somewhat useless. I sometimes need to do things visually until I learn how to do them from the terminal.

---

### Post by koenn on 2008-10-27
> **Buzzbait said:**
> The problem is that I do not yet know the terminal commands, which makes sudo somewhat useless. I sometimes need to do things visually until I learn how to do them from the terminal.

try to read beyound the first 10 words in my post.
you can use gksu to run gui applications with root privileges - in those rare cases the-at you actually need root privileges

---

### Post by Buzzbait on 2008-10-27
Bumping this back to the top, in hope of an answer to my question.

---

