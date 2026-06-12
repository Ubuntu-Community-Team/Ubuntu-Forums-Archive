---
title: "Connection refused using Unbuntu not Windows"
date: 2005-11-16
forum: General Help
---

### Post by Ob1ofwis on 2005-11-16
Hi all, I've been using linux for a number of years all be it not exclusivly. I'v recently installed Unbuntu and really love it.

My problem is this though. When I try to get to my web site using Unbuntu (through Firefox or IE in Wine) I receive a message that says "The connection was refused when attempting to connect to www.###.com"
This is happening on both of my machines running Unbuntu. Both machines are dual boot with Windows XP. Windows XP can access the web site just fine.
I was able to access the site fine last week. Nothing has changed that I know of.

How can I get Unbuntu (what ever browser) to access the site?

---

### Post by oskude on 2005-11-16
can you access the site under windows with another browser than iexploder ?
can you access other websites with firefox under ubuntu ?
does your site use some activex or other things that only newest iexploder can use ?

cause you didnt post the url, its a little hard to help...

but the question to "The connection was refused when attempting to connect to www.###.com" is, who refused ? your pc, router/firewall, the website/server...

---

### Post by Ob1ofwis on 2005-11-16
Yes, I can access other web sites using firefox in unbuntu
Yes I can access the site using firefox in windows.
The site is using some java, but it was working fine with firefox in unbuntu last week.

Sorry, the site is [www.mtask-radomski.com](www.mtask-radomski.com)

I was just now able to get the main page to come up but after clicking on a link I got the connection refused again.

It seems to be intermintent. Could it be my server is having a problem?
I am hosting this myself as it is a family thing.

Thanks for your help.

---

### Post by oskude on 2005-11-16
[QUOTE=Ob1ofwis]I am hosting this myself as it is a family thing.[/QUOTE]
in that case you could check your server logs to track down why your connection was refused.

i dont have/use java, but i can open the site with firefox/ubuntu (see mtask image and 3 "news" texts with dates)

oh, second a go i didnt have a menu on the left :)

oh, i get "connection refused..." when clicking the menu buttons...

oh, now i dont get any "connection refused...", you must be working there atm :)

---

### Post by Ob1ofwis on 2005-11-17
Ok, There is no entry from any linux computer in the log files leading me to believe that the computers are not even connecting. Windows machines work fine.

I rebuilt the server last night thinking that that might fix it. Still unable to connect to the site using a linux computer. 
Suse 9.0 using konqueror does not connect either "Could not connect to host"

---

