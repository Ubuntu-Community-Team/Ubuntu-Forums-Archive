---
title: "PHP5.0.5-2ubunut1 missing SQLite"
date: 2005-11-30
forum: General Help
---

### Post by guice on 2005-11-30
Looking at the PHP5 that came with (k)ubuntu's install and I was fairly impressed with everything until ... no SQLite. :(

Don't suppose there's a way to get it added in the next PHP upgrade (given 5.1.1 was just release not 2 days ago and packages needed to be recompiled)?

I don't use SQLite just yet, but it would be nice to have to play with. And I don't feel like dealing with trying to compile PHP myself (all it's dependancies are so g..).

---

### Post by shakin on 2005-12-01
[QUOTE=guice]Looking at the PHP5 that came with (k)ubuntu's install and I was fairly impressed with everything until ... no SQLite. :(

Don't suppose there's a way to get it added in the next PHP upgrade (given 5.1.1 was just release not 2 days ago and packages needed to be recompiled)?

I don't use SQLite just yet, but it would be nice to have to play with. And I don't feel like dealing with trying to compile PHP myself (all it's dependancies are so g..).[/QUOTE]

When you compile PHP yourself you tend to compile in the features you need, but Debian-style is to compile it minimally and then add modules for what you want. You can install the php5-sqlite package to get sqlite support in PHP. Do a Synaptic search for 'php5' to see all the other modules you can load.

FWIW, compiling PHP is easy and I can help you if you need it.

---

### Post by guice on 2005-12-01
Ah, didn't realize everything, even for PHP5, was modularized. How'd they do that? Didn't know you can install dynamic mods in PHP5. I gotta look that up. 

Thanks for the offer for assistance. It's cool. I know how to compile PHP5, too, it's just the idiosyncrasies of Ubuntu's install I didn't know and really care about trying to dig up. I like the setup Ubunut's using for Apache2 and PHP5 set. I'm trying to learn more about how they did it vs just installing it how "default" or how everybody else had done it.

...edit
Ack, no mysqli extensions within the repository! :(

---

### Post by aouie on 2006-02-01
I am now using Dotdeb packages for PHP5 with Kubuntu 5.10 (Breezy). Dotdeb finally got all the things I wanted for PHP5 and Apache 1.3. They recently got the pdo support going. They also have pear, mysql, pgsql, ....
deb [http://packages.dotdeb.org/](http://packages.dotdeb.org/) stable all
deb-src [http://packages.dotdeb.org/](http://packages.dotdeb.org/) stable all
Sincerely,
Aouie

---

