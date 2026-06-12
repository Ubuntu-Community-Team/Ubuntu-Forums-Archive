---
title: "shutdown already running, change shutdown script"
date: 2008-11-27
forum: General Help
---

### Post by blingo on 2008-11-27
(Use 8.04)
Where can I find the Shutdown (button) script?

I use Shutdown from start, set with time.
If I press the shutdown button I get back to menu and can't login because "the computer will shutdown in one minute", which it doesn't.
seems buggy to me...

If I don't use the button I write:
sudo shutdown -c; 
sudo shutdown -P now;

Want to change the shutdown script to that.

I think shutdown -c should be in the script for everyone -
if there's no shutdown it just prints an error,
but if there is shutdown and no shutdown -c, get ready for trouble -
to see the problem (this may cause damage)
one can use 
'shutdown time' (replace time with, amm, time) 
then try to use the shutdown button.
I sometimes need to login a non-graphic mode to kill the running shutdown process.
(that is to use shutdown -c)

Thanks in advance.

---

### Post by cmnorton on 2008-11-29
You'll need to get the properties of the appropriate buttons and see their mapping. You can mouse-click on a button -- I believe right-mouse-click -- and see what is executed when the button is pressed.

---

