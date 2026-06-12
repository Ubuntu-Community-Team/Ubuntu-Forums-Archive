---
title: "Help needed installing Wordpress"
date: 2008-10-10
forum: General Help
---

### Post by Drizzel on 2008-10-10
I decided to start my own site for various reasons. I bought my domain name, paid for a host, and now I'm stuck. I cant get Wordpress to work. I did "sudo apt-get install wordpress" and everything went normally. Synaptic shows its installed. However I cant figure out how to use it. There is no entry under the Applications menu, I cant launch it via alt+F2 or by typing wordpress in a terminal. How can I get Wordpress to work? :confused:

---

### Post by bodhi.zazen on 2008-10-10
[http://codex.wordpress.org/Installing_WordPress](http://codex.wordpress.org/Installing_WordPress)

---

### Post by Drizzel on 2008-10-10
Thanks, I'll go through all of that and if I dont have anymore problems I'll mark this as solved..

---

### Post by Drizzel on 2008-10-12
The Wordpress and lamp tutorials for ubuntu = Major Fail! Off to windows for me.. I'm very disappointed, I thought I was done with windows. Every tutorial I read on installing lamp was missing vital steps, commands didnt work etc.. Fail! Pretty bad when the official tutorial on the wordpress site for installing lamp on ubuntu is so worthless. Way too many individual packages to install and configure. It may have been ok if SO much wasnt left out of the tut. There needs to be a true step by step guide that is actually up to date.

Glad I still have my install of xp on my pc. There should be an all in one install for wordpress. Like "Sudo apt-get install wordpress" and thats it. Why is it so freakin difficult? It just seems so pointless.

---

### Post by p_quarles on 2008-10-12
Lol. If you have specific questions, ask them. If you want to go to Windows, that's fine too, but please don't act like you're punishing people by doing so. :)

---

### Post by aysiu on 2008-10-12
I don't think this has to do with Wordpress or Ubuntu, frankly.

The first time I tried to install software for PHP and MySQL (WebCalendar, I think it was), I had no idea what I was doing. Once I got the hang of creating the MySQL database, uploading the files, and modifying the configuration file to contain the appropriate MySQL database details, I could install pretty much any PHP/MySQL app (Drupal, PhpBB, Wordpress, etc.).

If you don't know how to do this or don't want to learn how to do this, I don't know if you should be running your own server. This has nothing to do with Ubuntu or Windows.

---

### Post by bodhi.zazen on 2008-10-12
> **aysiu said:**
> If you don't know how to do this or don't want to learn how to do this, I don't know if you should be running your own server. This has nothing to do with Ubuntu or Windows.


+1

Or if it is not broken, don't fix it. If windows is working for you, why change ?

The tutorial I linked you to is a step-by-step walk through on how to install wordpress and in fact it can be done in less then 15 minutes, assuming you understand the commands.

The first time i installed wordpress it took me 3 hours to work through the tutorial, but it is accurate and up to date (I just re-installed wordpress with that tutorial and migrated servers without any glitches, well without any glitches that were due to Ubuntu or wordpress).

With that said , we understand your frustration and if you ar stuck at any  particular step, tell us where you are having problems and we will try to help.

---

### Post by alfiejs on 2008-10-24
> **Drizzel said:**
> The Wordpress and lamp tutorials for ubuntu = Major Fail! ... I'm very disappointed,... Every tutorial I read on installing lamp was missing vital steps, commands didnt work etc.. Fail! Pretty bad when the official tutorial on the wordpress site for installing lamp on ubuntu is so worthless. Way too many individual packages to install and configure. It may have been ok if SO much wasnt left out of the tut. There needs to be a true step by step guide that is actually up to date.


Instead of getting all pissy about it, why not try and do something about, it?  Write your own install guide.  Ask an actual question of someone.  I am not an expert but have written admin guides, install guides and user guides for corporate software, it's not that difficult.  It may not work perfectly the first time, but you refine the steps, use the ones that work and redo the ones that don't.

And hey, if it's free dont frickin complain.

---

### Post by aysiu on 2008-11-03
> **Drizzel said:**
> I'm not running my own server or even trying to. I have my own hosting account. I was just trying to install wordpress locally so I could edit my site without doing it "live" as in the web based wordpress. You know, so I could experiment with different things and not have it immediately show up publicly.  So once you try it out locally, you'll replicate the exact same database online with your paid-for web host? It may be rather difficult to maintain that kind of replication.

Your best bet is to just go with your online host and not make your Wordpress blog public until you feel you have it set up just right (there's even an option in the Wordpress dashboard to disallow indexing by search engines, so unless you start advertising your blog, no one's going to see the little changes you make).

If you do want to use it locally, though, I believe you would set up a MySQL database for Wordpress, and then load all the Wordpress files into /var/www (this directory is owned as root, so you'd have to ```
sudo cp -R *the wordpress directory*
``` there).

---

