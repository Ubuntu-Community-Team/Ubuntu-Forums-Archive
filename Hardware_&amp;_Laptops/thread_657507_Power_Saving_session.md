---
title: "Power Saving session"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by X-dark on 2008-01-03
Hello,

I would like to be able to start a session without wireless, bluetooth, compiz and other energy consuming things.
The idea is when I take train I run on battery power and I'm a little short to watch a whole movie. So what I would like to do is having the possibility of choosing a minimalistic session with just the necessary stuff to play media.

How can I do that ?

Thanks

---

### Post by Paul Moir on 2008-01-03
There may be a better way but if I were to do it, I would do it like this:

Create a new user for the low power setting.  Set him so he is a member of your main user's group.  Set your main user so he's a member of the low power user group.  

(say my login is 'paul', and .  I create an account "paul_lowpower".  I make paul_lowpower a member of paul, and paul a member of paul_lowpower in addition to paul).

We do this so we can access each other's files.  Unfortunately the default creation mask in ubuntu doesn't allow members of groups to read or write each others files, so this must be fixed for both users.  Edit each's ~/.profile file to change umask from 022 to 002.  Alternatively, think about making this system wide by changing /etc/profile

Next, existing files would need to be chmoded to the new, group-accessable settings.  By way of example, from a shell :

sudo find /home/paul -exec chmod g+rw {} \;
sudo find /home/paul_lowpower -exec chmod g+rw {} \;

Then probably link the two together with some symbolic links on the desktop

This is just one idea.  I'm sure there's others!

---

