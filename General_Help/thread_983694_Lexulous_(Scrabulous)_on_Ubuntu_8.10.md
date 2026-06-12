---
title: "Lexulous (Scrabulous) on Ubuntu 8.10"
date: 2008-11-15
forum: General Help
---

### Post by Spanglegluppet on 2008-11-15
I've recently installed Ubuntu 8.10 (via Wubi, if that matters at all), and it works great, except for the fact that I can't seem to get Lexulous (formerly Scrabulous) to work in Firefox 3.0.3. All that will open when I click on a room is a blank window.

I'm not sure about Java, or if that's installed or not, and I recently installed Moblock, if that makes any difference whatsoever.

---

### Post by Pro-reason on 2008-11-16
Are other Flash apps working OK?

---

### Post by Spanglegluppet on 2008-11-16
> **Pro-reason said:**
> Are other Flash apps working OK?

Yep, as far as I can tell.

---

### Post by Pro-reason on 2008-11-16
By what means did you install Flash?

Try starting Firefox with extensions disabled.

---

### Post by Zill on 2008-11-16
Spanglegluppet:  I believe Lexulous (Scrabulous) uses Java.  Use these links to verify if it is installed properly...

[http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp")
[URL="http://javatester.org/version.html"]
http://javatester.org/version.html[/URL]

[http://www.w3.org/People/mimasa/test/object/java/clock]("http://www.w3.org/People/mimasa/test/object/java/clock")

---

### Post by jre on 2008-11-17
I don't know Lexulous. But since you have MoBlock installed it might be that a server is blocked that Lexulous is trying to connect to.
Check "tail -f /var/log/moblock.log" while you start Lexulous, to see if an IP gets blocked.

---

### Post by Newbuntu2009 on 2009-01-20
Good question. Now how do you get Lexulous to play on Ubuntu 8.04?
It works on Mac OSX 10.3.9, but with a detailed java error display.
Figuring this out would make a lot of logophiles more than happy.

---

### Post by Zill on 2009-01-20
> **Newbuntu2009 said:**
> Good question. Now how do you get Lexulous to play on Ubuntu 8.04?...

Lexulous runs fine on Ubuntu 8.04 :-)

Just make sure java is correctly installed and configured.  You can test it using the links I posted above (#5).

---

