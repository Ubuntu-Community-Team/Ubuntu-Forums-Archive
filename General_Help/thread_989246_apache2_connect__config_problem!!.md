---
title: "apache2 connect / config problem!!"
date: 2008-11-21
forum: General Help
---

### Post by porteclefs on 2008-11-21
Hello, 

Ok, so apache2 is running on my server. But when I go to localhost:80 all i see is a text in the upper left that says "It Works!"

I've located this "It Works!" file in my /var/www/

My question is why am I not seeing whatever I should be seeing on localhost:80 when apache is running?

I'm assuming I need to configure apache.. but I don't know where to start.

---

### Post by Titan8990 on 2008-11-21
Thats what you get under the default Apache configuration. It is telling you that is working.

Did you place HTML files in /var/www you are trying to get to?

If you did you can view it like this (assuming the file is test.html):


localhost/test.html

---

