---
title: "LAMP and 6.10"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by keiffee30 on 2007-04-16
dear all

i have installed 6.10 on my compaq evo N410, and wow everything is working lovely. even my wirelewss worked 1st time. This has taken me 18 months to get to work on any linux. 6.10 did in 14 minuets. Well done for the OS makers. 

Now i have been looking at all the OS's from here and moving all my PC's and home servers over to ubuntu. i would like to run joomla for making web sites. but this need Apache, php 4 or 5, MySQL. I have seen from the server that you can set  up LAMP but can this be done on 6.10. 

any help would be nice

---

### Post by jonallport on 2007-04-17
The 'LAMP' install is a task package name 'lamp-server'.  I'd use aptitude to install it thus;

From a terminal window:
'sudo aptitude'
'u' to update package lists
navigate to Tasks/Unrecognised Tasks
highlight 'lamp-server' and type'+' to select all packages for that task
'g' to download/install

My apologies if these instructions sound a bit condescending, I couldn't really gauge you level of knowlege from the post.

Hope it's of some help

---

### Post by jonallport on 2007-04-18
Me again, quicker/easier method:

sudo tasksel
pick the 'lamp-server' task
done!

---

