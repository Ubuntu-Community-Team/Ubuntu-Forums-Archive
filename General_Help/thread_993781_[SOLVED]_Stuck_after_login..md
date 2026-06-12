---
title: "[SOLVED] Stuck after login."
date: 2008-11-26
forum: General Help
---

### Post by diwas on 2008-11-26
Hello, 
First of all, the official live cd from canonical wont go after the log in screen. It stucks there.
Now, I have successfully installed the OS and when i boot it...again the same thing happens. I had selected automatic log in during the setup. Now after i select UBUNTU in GRUB, it loads everything and my system is stuck on brownish background (which usually comes after logging in) and a cursor. I cannot do anything except hard restart..

Is there any solution for this??

Thank you.

---

### Post by Peter09 on 2008-11-26
Well here is some information

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg235397.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg235397.html)

---

### Post by diwas on 2008-11-26
I got the reason...its GNOME2...also, if i remove compiz i have some chances to get into the desktop. How can i do that?? How do i get to the terminal prompt in my situation?? 

Thank you.

---

### Post by Peter09 on 2008-11-26
You could try Xbuntu, it uses does not use Gnome for a window manager.

---

### Post by diwas on 2008-11-26
Well, I have found a solution:
First boot into command line through recovery mode
Then remove compiz
[code]
sudo apt-get remove compiz
sudo apt-get remove compiz-core
[\code]

This problem is solved!

---

### Post by newagelink on 2009-02-11
> **diwas said:**
> Well, I have found a solution:
First boot into command line through recovery mode
Then remove compiz
[code]
sudo apt-get remove compiz
sudo apt-get remove compiz-core
[\code]

This problem is solved!I did that, and still I get only a cursor. I have been using Ubuntu 7.10 for what, two years now? And it suddenly decides to stop working last night.

---

### Post by diwas on 2009-02-11
The problem might be different. I suggest u start another thread.

---

### Post by newagelink on 2009-02-11
> **diwas said:**
> The problem might be different. I suggest u start another thread.Thank you for your reply. I think it may be different; I have started another thread entitled [After login only cursor loads]("http://ubuntuforums.org/showthread.php?t=1066817").

---

