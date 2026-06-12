---
title: "Logitech Special Function Key"
date: 2008-08-28
forum: Hardware
---

### Post by fauzie on 2008-08-28
Hi, I have a Logitech Internet Keyboard, Y-ST39. Everything works, including the special function keys. It has "Search", "Files", "E-Mail", "WWW", "Mute", and Volume control. I can launch firefox, change volume, etc. 

The only key that is not working is the one labeled "Files". Using System -> Keyboard Shortcuts, pressing on this one particular key doesn't generate any response. I wonder if there is a way to check whether the key itself is broken (other than plugging it into another, windows computer). Maybe cat something at /dev ?

I can live well without it, but it would be nice to get it to work.

Thanks in advance.

---

### Post by fauzie on 2008-08-31
I found a solution for this problem.

1. Check the messages
from a terminal
tail -f /var/log/messages

2. Press the Files button and read the instruction

3. Put the command given to the 2nd line of /etc/init.d/hotkey-setup
setkeycodes e005 144

where e005 is given when pressing the malfunctioned button during tail.
144 is given in /usr/share/hotkey-setup/key-constants

4. Restart the script as root
sudo /etc/init.d/hotkey-setup restart

5. Check with the tail button. There should not be any error message (unknown key).

6. Use System -> Preferences -> Keyboard Shortcuts
The Files key should be available now.

---

