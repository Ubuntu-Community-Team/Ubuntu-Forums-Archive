---
title: "wireless connection multiple users"
date: 2010-10-29
forum: Hardware
---

### Post by gtr@frii.com on 2010-10-29
Installation was single user on 10.10 unity (netbook).  I have a wpa-2 wireless connection with a long (50 character) random password.  I expected, when adding a second user that at login they would automatically hook up to the wireless (that is what happened on previous non-netbook ubuntu releases).  Did not happen, the wireless asked for the password.  I had stored the password in the original login ~/Private -- which, of course is not accessible to the new user login.  In a word frustrating, and to add to the frustration, switching to the original user did not connect wireless, nor did it give me access to ~/Private.  Ultimately, from a fresh login, I used sudo to write the wpa passwordinto the second users ~/Documents directory.

Why is this the behavior for network connections in Unity?  Alternatively, did I do something wrong in installation.  The initial installation was with the RC release, but I have been regularly updating.

---

