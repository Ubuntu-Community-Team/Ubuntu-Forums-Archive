---
title: "Serial Mouse in Breezy"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by Edward The Bonobo on 2006-01-20
When I installed Hoary, my serial mouse wouldn't work.  I followed the instructions in the wiki [https://wiki.ubuntu.com/SerialMouseHowto](https://wiki.ubuntu.com/SerialMouseHowto) to reconfigure xserver-xorg and select my mouse port.  It worked fine.

I've just upgraded to Breezy.  Same mouse problem...but the instructions don't work; it doesn't give you the option of selecting the mouse port.

Any ideas?

(step by step please - I'm a newbie with a headache)

---

### Post by Herbie on 2006-02-01
I've had more or less the same problem except I installed fresh.  The software won't detect a serial mouse and so far all of the help points back to the same directions for Hoary that don't work for breezy.  When you do a search on "serial mouse" you get a fair idea of how many users are using a serial mouse and this distribution does not appear to support it!  I don't mind working the command-line, reading man pages, reading forums and searching on the internet, but I haven't managed to find an answer.  

Any takers on this?  I really don't want to throw in the towel, but....

---

### Post by BlackZen on 2006-02-08
I hope this will help some of you with the serial mouse problem...

I have struggled for 2 days with this, before a (how daft am I?) brainwave...

I thoroughly searched the forum (search term "serial mouse" in titles only, in the 5.10 hardware forum, revealed the most relevant posts [http://ubuntuforums.org/search.php?searchid=3712539]("http://ubuntuforums.org/search.php?searchid=3712539")), and the net in general for a solution, and tried them all. Nothing worked.

**My brainwave:** I'm using my nice new PS/2 mouse in the serial port (via an adapter) of the **old** collection of spares I use for testing.

So I exchanged the PS/2 mouse for a (proper) serial mouse attached to another PC, plugged it in to the Ububntu box, and a few moments later it sprang into life (without even rebooting - **not recommended**, slap on wrist for me, bad boy!)

Well, that fixed it for me, don't know how many of you may be using a PS/2 plugged into the serial port, but I bet I'm not the only one :-)

---

