---
title: "Setting up Lubuntu on laptop with seperate passwords"
date: 2012-05-04
forum: Hardware
---

### Post by Dlambert on 2012-05-04
Well I bought an old HP Ze2000 laptop for my sister (1GB ram) and I'm going to install Lubuntu on it. Basically I wanted to know if there was anyway I could make the root password different than the user password, to prevent her (she's 13) from messing anything up. Also, what can I do to lubuntu to make it look for like windows but keep the same speed. She has never used linux and I want to make it as easy as posible for her.

---

### Post by km3952 on 2012-05-04
Perhaps something like giving root a password that you keep private, & remove the normal login from the sudoers list.

---

### Post by dandnsmith on 2012-05-04
> **Dlambert said:**
> Well I bought an old HP Ze2000 laptop for my sister (1GB ram) and I'm going to install Lubuntu on it. Basically I wanted to know if there was anyway I could make the root password different than the user password, to prevent her (she's 13) from messing anything up.

The root password isn't the same as the user password - what happens is that the user you create when installing has privileges to allow use of administrator stuff, and the special privileges are safeguarded by requiring your password (not roots) when you attempt these functions.

Just create your sister a separate user with it's own username and password (which will, by default, have no special privileges) and only let her use that. Also ensure that any user has to log in to use the machine.

HTH

---

### Post by MG&amp;TL on 2012-05-04
13 year olds are designed to mess stuff up. :P

Go to the System submenu, then the users dialogue (sorry, I forget what it's called), make a new user, then switch the "administrator" bit off on that user.

Well, you could try a different icon theme and/or a transparent taskbar, btu other than that, not really. "Looking like windows" isn't really going to help, I suggest  telling her "it's different" and sticking around for the first day explaining how to do things. Oh, and "No, you can't have windows".

Also get flash working, that seems to irk teenagers if youtube doesn't work.

---

### Post by Dlambert on 2012-05-06
I Guess I just didn't realize it was that simple. Thank you all.

---

