---
title: "Ubuntu 8.04 hangs every second on laptop."
date: 2008-09-25
forum: General Help
---

### Post by davemar on 2008-09-25
I've got Ubuntu 8.04 installed on a Dell Latitude D600 laptop. It has got an annoying habit of freezing for a split second every second or so. If you wiggle the mouse around the pointer will just stick momentarily every second. 

The trouble with such a short and frequent event it is difficult to track what could be causing this. Using 'top' just can't spot such things.

Has anyone experienced such a thing before, or know of a solution?

Thanks, Dave.

---

### Post by snowpine on 2008-09-25
> **davemar said:**
> I've got Ubuntu 8.04 installed on a Dell Latitude D600 laptop. It has got an annoying habit of freezing for a split second every second or so. If you wiggle the mouse around the pointer will just stick momentarily every second. 

The trouble with such a short and frequent event it is difficult to track what could be causing this. Using 'top' just can't spot such things.

Has anyone experienced such a thing before, or know of a solution?

Thanks, Dave.

Hi Dave, I would make sure you have Desktop Effects disabled, does that help? How much ram do you have on that laptop? 

I have an older Dell laptop as well (Latitude Cpx) and I've been much happier with lighter-weight options such as Openbox and Fluxbox.

---

### Post by davemar on 2008-09-25
It's got 512MB, so not a completely rubbish amount. Desktop Effects is turned off too.

---

### Post by snowpine on 2008-09-25
Dave, it's been a while since I last used Gnome desktop, so I'm trying to remember. One thing that helped me was turning off the Tracker application. I think you do that by going into System->Sessions and unchecking it, then rebooting. Sorry but I am running out of suggestions; your computer is better than mine so I don't think it is a ram issue, and I have had pretty good luck with Ubuntu and Dell. :(

---

### Post by davemar on 2008-09-25
We've cracked the problem. There was a touchscreen USB driver hunting for action every second, which once removed everything started to run smoothly. A rather obscure cause to the problem, but at least it's fixed now!

---

