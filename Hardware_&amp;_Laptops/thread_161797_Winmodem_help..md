---
title: "Winmodem help."
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by Xcelerate on 2006-04-17
I have a BCM4212 Dell 56K V.92 winmodem and I am trying to figure out how to get it to work on Ubuntu.  I found this page: [http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/15264](http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/15264), but I'm not sure how to compile it for this system.

Thanks for your assistance.

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=Xcelerate]I have a BCM4212 Dell 56K V.92 winmodem and I am trying to figure out how to get it to work on Ubuntu.  I found this page: [http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/15264](http://www.crynwr.com/cgi-bin/ezmlm-cgi/1/15264), but I'm not sure how to compile it for this system.

Thanks for your assistance.[/QUOTE]
It's better if you start with scanmodem. check out the second link in my signature. The steps, basically, are:

1. Read wiki (link in my signature) section about scanmodem and basics
2. Run scanmodem in your system (on Linux, **not** on windows)
3. read and re-read the generated modemdata.txt (I ended up reading it 18-20 times bf I could make sense of it. I still refer back to it from time to time to see if I'll understand stuff I couldn't understand back then)
4. refer back to wiki if there is a section on your modem
5. configure modem with the help of modemdata.txt and wiki page
6. see end of wiki page to learn how to use one of the dialers (my favorite is wvdial). 

if you get confused and need more help, please attach your modemdata.txt here as well. If no one around can help, you'll have to email linmodems.org mailing list. 

this will take long and you'll need some patience :)

---

