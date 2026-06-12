---
title: "No printing on Dapper Edgy"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by flemmingbjerke on 2007-01-12
When I upgraded to Dapper my Brother hl-720 stopped working with cups, etc..](*,) :evil:  Upgrading to Edgy did not solve the problem. For quite a period, I had no working printer (I don't print much at home). What solved the problem was:
[URL="http://www.freestandards.org/en/OpenPrinting/Database/BackendErrorHandler"]
http://www.freestandards.org/en/OpenPrinting/Database/BackendErrorHandler[/URL]

You need not install beh on Edgy. It is there allready. I just ran the lpadmin command. Notice, that the "name of print queue" is the name that you have given the printer in cups.

---

