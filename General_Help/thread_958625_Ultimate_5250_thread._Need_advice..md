---
title: "Ultimate 5250 thread. Need advice."
date: 2008-10-25
forum: General Help
---

### Post by josys36 on 2008-10-25
The ultimate 5250 thread. Need advice.
Hello!

I have been using Ubuntu now for about a year and a half. Great product and I have just about made a complete switch to Ubuntu at home, but I have one application left over that I can't seem to find a good Linux equivalent. I work on the IBM System i. Therefore I need a good 5250 emulation product to work from. Right now I run IBM Personal Communications inside a VMWare XP system. what I would like to do is move away from the VM system since all I need it for is 5250. Here is what I have tried and has failed.

1. Wine - Wine would not let the IBM Personal Communications product install. The install would being, but then would fail about midway though with no explanation. I tried then to copy the files from a working windows install to wine folders, but the product still would not load. The initial screen would come up, but there were no sessions to choose from, and none of the buttons worked. I tried another 5250 product that worked in wine, but the fonts were so bad you could't use the product. In fact, only one font worked, and that looked like old english.

2. Linux products - I tried the other products out there like TN5250. Frankly I was very disappointed. Some of them look just plain ugly, and others didn't have full functionality. I even tried a commerical product from Power Term. The product looked ok, but the fonts in the 5250 screens were terrible. The company contacted me to see if I wanted to purchase the product. I said no since the fonts were ugly. From what I gathered this was the first time someone had tried to install the product on Ubuntu. Might even be the case for Debian.

3. I next tried the rdesktop route, but that wasn't great either. The window would load, but if I tried to make a window full screen it would do really funny things. For starters I could not close the window. I had to use the command window and do ctrl + c. Then I had to log back in the windows box and close the window from there.

4. I tried IBM's CA for Linux product. For a company that pushes Linux so much they sure made a god awful product! It almost like fisher price like. The other problem with this product is that it is only good for 5250. Plus, you need to have CA installed on your System i for the product to work. Since I work at customers sites that don't have CA, this offers no solution. Also, since I need to work on System z machines I need 3270.

5. I have read every single post on 5250 on the forum.

6. Googled until I could't google no more!

Anyway, I can live with using a VMWare system for PCOMM, but thought I would give it one last shot to see if anyone has come up with a working solution, or may have a good idea that I can try. Since I have been trying to fix this for a year I am up to doing just about anything.

Thanks!

Jason

---

### Post by josys36 on 2009-01-27
Bump!

---

### Post by slick666 on 2009-02-16
Bump again.

I too am having problems with tn5250. I guess I don't need all the fance options but simple things like automatic login that I can do on windows I cannot do with tn5250.
(I know if has the feature, but I've read the documentation and it doesn't work with my setup)
I'm still looking through the tn5250 alternatives and I'll see what I find but if anyone has some expierence with this please post.

---

### Post by swmiller6 on 2009-03-14
What problems are you having with tn5250? Just curious I have been using it for a couple of years now and am quite happy with it.. However I am only a simple user so not sure I can help you with to much.

---

### Post by josys36 on 2009-05-16
Basically this is my one problem from moving from Windows completely. However I have gotten used to to having to use IBM Client Access from inside Virtual Box. However, I would love there to be a day when I can just use a good Linux 5250, or even using Wine. Wine has never really been that successful in getting Client Access to run, however I have not tried it in a year or so. Maybe, just maybe, it is time to try again. :)

---

### Post by swmiller6 on 2009-05-16
@josys36

Never mind I went back and read the whole thread. What functionality is missing from tn5250?
[IMG]http://trademarkclan.net/images/as400.jpg[/IMG]

---

### Post by mfrauenstein on 2009-05-21
For me I would like to be able to use the F13 through F24 and F1 for System i help, 52550 screen copy to clipboard (as per CA), printing (although nice but not critical). 

CA as per the Windows product would be good! But then again Ops Nav would also do!

Let's hope the Law of Attraction works!

---

### Post by josys36 on 2009-10-11
Well in a brief update to this thread I might have a potential solution. I looked at IBM's Host On Demand software to replace our current CA in specific situations. This software let's you run a 5250 session in a web browser. I tested this at the office with Firefox and it ran just fine. Looks almost EXACTLY like CA 5250! No strange font problems or any weird crap like that. So to run this at home what you would do is install the software in a windows VM, and then run the VM to access the Host On Demand site. Once that is working you setup sessions and run them as normal. I am going to fire up my home system tonight and give this a try. 

Jason

---

### Post by n8bounds on 2009-11-11
Just use the real IBM 5250 iSeries Client Access program if you don't like tn5250.

I have some debs here:

[http://n8.thruhere.net/export/free/ibm5250/](http://n8.thruhere.net/export/free/ibm5250/)

---

### Post by josys36 on 2009-11-19
> **n8bounds said:**
> Just use the real IBM 5250 iSeries Client Access program if you don't like tn5250.

I have some debs here:

[http://n8.thruhere.net/export/free/ibm5250/](http://n8.thruhere.net/export/free/ibm5250/)

I am sorry but the IBM version of CA for Linux looks TERRIBLE! The fonts are god awful, and then menu size is HUGE! If IBM made this product look like the windows version then cool, but for now I will keep searching.

Jason

---

### Post by n8bounds on 2009-11-19
It is truly hideous. The overwhelming unatractiveness if Client Access goes well with iSeries in a general sense anyway.

Seriously though, it does offer more functionality than tn5250 at least.

---

### Post by n8bounds on 2011-05-10
[SIZE="4"]Updated for Natty: [http://n8.thruhere.net/blog/?p=1122]("http://n8.thruhere.net/blog/?p=1122")[/SIZE]

---

