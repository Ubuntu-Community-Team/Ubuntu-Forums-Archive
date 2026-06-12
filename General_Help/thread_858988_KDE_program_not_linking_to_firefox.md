---
title: "KDE program not linking to firefox"
date: 2008-07-14
forum: General Help
---

### Post by Robbyx on 2008-07-14
I have installed basket note pads, a KDE program within Ubuntu. I can paste into it urls. When I click on a url within BN the following error message appears:

KDEInit could not launch 'firefox'.:
Could not find 'firefox' executable

That message arises even though I have chosen FF in the right click choice to open the link.

Is there a solution?

Robin

---

### Post by nikgare on 2008-07-14
what happens if you type **firefox** in a terminal, does firerox run?

---

### Post by Robbyx on 2008-07-23
Although I am using FF all the time by clicking on an icon this is the terminal error message:

> robin@robin:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
robin@robin:~$ 


---

### Post by SOULRiDER on 2008-07-23
Im not sure what the program binary is, it may be firefox-bin (im not using linux ATM). What you could do is use the menu editor to see what the firefox icon points to and then make a symlink in /usr/bin called firefox pointing to that binary. I think that could work.

---

### Post by Robbyx on 2008-07-23
Thank you for your help. Could you please advise me as to where I can find the menu editor?

Robin

---

