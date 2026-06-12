---
title: "problem with apache and .gif images"
date: 2008-07-22
forum: General Help
---

### Post by rwalsh on 2008-07-22
Ok, so I have apache 2 installed and everything works fine.  Except for gif images (it may be other image files as well, but .gif is the only one currently in use, some other image formats such as jpeg and bmp work fine), but for .gif it only shows a placeholder.

There is this message in the apache2 error log

script not found or unable to stat: /usr/lib/cgi-bin/images.cgi

(yes it does say "stat" instead of start, I don't know why)

Now obviously I checked in that directory to see if images.cgi was there, but there is nothing.   

Is my problem with a setting in apache how it handles .gif? or am I supposed to have an images.cgi?  Any help would be appreciated.

-Ryan

---

### Post by kellemes on 2008-07-22
> **rwalsh said:**
> Ok, so I have apache 2 installed and everything works fine.  Except for gif images (it may be other image files as well, but .gif is the only one currently in use, some other image formats such as jpeg and bmp work fine), but for .gif it only shows a placeholder.

There is this message in the apache2 error log

script not found or unable to stat: /usr/lib/cgi-bin/images.cgi

(yes it does say "stat" instead of start, I don't know why)

Now obviously I checked in that directory to see if images.cgi was there, but there is nothing.  Now the site was moved from IIS to Apache, but with IIS it was not using images.cgi for the .gif .  

Is my problem with a setting in apache how it handles .gif? or am I supposed to have an images.cgi?  Any help would be appreciated.

-Ryan

Have you checked the casing of your gif files?
Could it be they are uppercase? Rename them to be lowercase and see if it works.

---

### Post by rwalsh on 2008-07-22
Unfortunately that is not the problem, I have tried it with multiple files and matched their names exactly... :(

---

### Post by spiderbatdad on 2008-07-22
how about permissions or ownership of the .gif. I have never had a problem displaying .gif with apache .html pages. Unable to stat afaik is unable to "copy."

---

### Post by rwalsh on 2008-07-22
No, I chmod 777 just to make sure that wasn't a problem.  Although, something I noticed just now is that

[http://chemesvr3.cheme.cmu.edu/index.html](http://chemesvr3.cheme.cmu.edu/index.html)

This is the website I am testing on right now.  Now when I go to the image properties it gives me the correct address

[http://chemesvr3.cheme.cmu.edu/dk_kiwi_gif.gif](http://chemesvr3.cheme.cmu.edu/dk_kiwi_gif.gif)

But it gives the wrong type (text/html instead of image/gif)
and then when I right click on goto view image ( I am using firefox)  it says it cannot find this URL

/cgi-bin/images.cgi/dk_kiwi_gif.gif

Which is not where the image is supposed to be.

Does this info help shed some more light?  I probably have a stupid setting somewhere but I don't know where, I am new to the whole webhosting thing.

---

### Post by spiderbatdad on 2008-07-22
why not have the .gif in the same folder as the index.html?
Your html code cannot find it otherwise...without a path.

---

### Post by rwalsh on 2008-07-22
They are in the same folder... I don't know why it is trying to go to /cgi-bin/images.cgi/*.gif <-- this doesn't even make sense.

I am guessing it is a config file somewhere that is saying if I have an image redirect to cgi-bin/images.cgi/*.gif  but I would have no idea where that is and haven't been able to find anything useful as of yet :(

I am pretty sure that apache thinks there is a images.cgi handler for gifs, but there isn't and I want it to use the default handler... I have tried setting it in my sites-available default file but to no avail..

---

### Post by spiderbatdad on 2008-07-22
depending how you installed apache (2?) the config file would be in /etc/apache2/apache2.conf...this can be overridden by httpd.conf or directives in sites-available-default.

Generally, I would copy sites-available/default to sites-availabel/my_site and edit the root document and directory to point to a folder called public_html in my home directory. Then run the commands sudo a2dissite /etc/apache2/sites-available/default && sudo a2ensite /etc/apache2/sites-available/my_site

in home/user/public_html you would have your index.html, etc.

---

### Post by rwalsh on 2008-07-22
Ok well I have made a little progress...

When I add "AddHandler default-handler .gif" (Inside of the <Directory> Directive that holds the images) it works and serves up the images. 

But I changed my logging level to debug and found this in my error.log...

[Tue Jul 22 17:44:46 2008] [error] [client xxx] Request exceeded the limit of 30 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://capd.cheme.cmu.edu/](http://capd.cheme.cmu.edu/)


[Tue Jul 22 17:44:46 2008] [debug] core.c(3052): [client xxx] redirected from r->uri = /cgi-bin/images.cgi/cgi-bin/images.cgi/images/yellow_dot.gif, referer: [http://capd.cheme.cmu.edu/](http://capd.cheme.cmu.edu/)

[Tue Jul 22 17:44:46 2008] [debug] core.c(3052): [client xxx] redirected from r->uri = /cgi-bin/images.cgi/images/yellow_dot.gif, referer: [http://capd.cheme.cmu.edu/](http://capd.cheme.cmu.edu/)

[Tue Jul 22 17:44:46 2008] [debug] core.c(3052): [client xxx] redirected from r->uri = /images/yellow_dot.gif, referer: [http://capd.cheme.cmu.edu/](http://capd.cheme.cmu.edu/)

It has a bunch of similar lines with more added /cgi-bin/images.cgi/ , so it's like some sort of recursion that keeps adding /cgi-bin/images.cgi to the path... :-/

---

