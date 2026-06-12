---
title: "Touchpad doesnt work without command."
date: 2012-07-23
forum: Hardware
---

### Post by Neckrow on 2012-07-23
Hello everyone,  I am on a Dell XPS | 15Z. No matter what flavor of linux I install the touchpad doesn't automagically work. I have to open terminal and type

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

I have been told there is a RC2.D I can insert a script into to startup and run this command. If this is true I was wondering if I could get some hand holding or a link. I have no idea other than I was told the names are important, names starting with 99 are run last in the list. So I will want to name the script 99something. However I know nothing about scripts. Can anyone help please!??

Thanks in advance.
                                                    - Neckrow :guitar:

---

### Post by efflandt on 2012-07-24
Another option is to put it in /etc/rc.local which runs after everything else during boot.  That runs as root, so no need for sudo within rc.local, but use full path to modprobe.

To edit rc.local from a terminal: **sudo nano /etc/rc.local**

---

