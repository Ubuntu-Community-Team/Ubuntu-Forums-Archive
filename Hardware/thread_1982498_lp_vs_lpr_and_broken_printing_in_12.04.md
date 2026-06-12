---
title: "lp vs lpr and broken printing in 12.04"
date: 2012-05-18
forum: Hardware
---

### Post by rmcd on 2012-05-18
I am puzzled by the behavior of printing in 12.04 (I'm using xubuntu but I don't think that matters.)

First, printer discovery is *fantastic* in 12.04. Hats off to the developers for this.

I am using a Lexmark x364dn. Sometimes printing works. Other times, I will try to print a pdf from evince (for example), or from the command line using lp, and the print job simply fails. The printer light flashes a few times and then the printer quiets down. Nothing comes out. I can't find anything in the error log.

*However*: If I print from Acroread, it almost always works (I can't recall a failure.) Acroread is apparently using lpr (it shows you the command it is sending). 

Why would lpr work and lp not work? Is that really the difference between evince and acroread? I would love to debug this.

---

