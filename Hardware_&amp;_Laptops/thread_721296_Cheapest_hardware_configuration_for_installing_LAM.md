---
title: "Cheapest hardware configuration for installing LAMP server?"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by shinems on 2008-03-11
Cheapest or the minimal hardware configuration for installing LAMP server?I want to start a software firm with developments in PHP/JAVA etc.


:popcorn:

---

### Post by scragar on 2008-03-11
I've got a LAMP box running with 128MB of ram on a 800MHz CPU without a monitor, and it's got more power than it needs(can handle around 7 or 8 requests/sec when it's not running cronjobs).

I'm sure if you installed the ubuntu server edition over the full version like I did that requirement would be lower still. I've also heard that lighttpd is very small in terms of CPU power, so that could help boost it's potential.

---

### Post by shinems on 2008-03-12
Somebody pls giv a minimal configuration and the dollars needed to buy a machine for doing java/php professional development in ubuntu.



:popcorn:

---

### Post by Biggus on 2008-03-12
I'd estimate that, at a minimum, you would need around 64mb of ram, a P1 processor, and a few gigs of HD space.

They don't sell boxes with such configurations around here, so I don't know how much it would cost these days.

---

### Post by shinems on 2008-03-13
its dead cheap in india.it will cost only 2500 INR or 60 USD ($) for this in india.

but can we do professional php/python developement in such PCs?

Reply please.

:popcorn:

---

### Post by Biggus on 2008-03-13
Ya probably could if you were determined enough, although it might not be enjoyable. (ie you probably won't be able to run Dreamweaver in wine)

The spec I recommended was for a bare minimum LAMP server, if I were you, I would do development work on a different PC, and simply use the LAMP set up for hosting.

---

### Post by shinems on 2008-03-13
pls say a professional configuration.be strait.

i want a PC for website development in php + want to try python.......

i am really fascinated by the syntax and language of python.

i invite other techies to join...

[SIZE=7]Are there no techies around?:confused:[/SIZE]

---

### Post by jimcooncat on 2008-03-13
There are lots of techies here. But your post is a bit hard to understand, so that might be why more aren't joining your discussion.

You said professional, so I take that to mean that you are using this setup to make money for you to live on. In that case, I would not rely on only having one computer; if it stops working for some reason, you've lost your ability to make money. If you misconfigure a computer (not likely) you would still have another one to use to find out how to fix it.

I would say at a minimum, you would want two computers linked together with a crossover network cable, or to an inexpensive four-port switch. These can be older computers, in fact you might be able to get a better quality older computer (two to three years old) than a newer one. Each should have 256 MB RAM, and 40 GB hard drive; though more is always better.

As you work, back up one computer to the other. rsync makes this simple.

If you want a graphical display (I would imagine you would to see your layouts), Xubuntu might be nicer for these older computers than the default Gnome Ubuntu. Epiphany or Galeon might work nicer than Firefox, and should show your work the same way Firefox would.

You should have no problems configuring LAMP, python, text editors, etc. with this kind of setup. If you need to do much graphics work, you should do some research on which packages to use, as these can be memory intensive.

---

### Post by shinems on 2008-03-14
good reply.i expect some standards like this.

i am not interested in graphics but my onus is on functionality.

i am into ERP.

xubuntu is the most commonly used one for development on client side?

:popcorn:

---

### Post by jimcooncat on 2008-03-17
> **shinems said:**
> xubuntu is the most commonly used one for development on client side?

No, I suspect the most common desktop environment for development is KDE (provided by Kubuntu). But your desktop environment is relatively unimportant for web and server-side development; it's a combination of personal preference and how much of your computer's resources you want to devote to it. I suggested Xubuntu as it's light on resources, very flexible, and responds quickly.

Most important is the choice of editor you'll use. There are very many good ones available. Do get used to one nice command-line editor, such as nano, vi, or emacs. If you have to configure or fix a remote server, you'll need to use one of these over ssh. 

You could actually do everything with the command line if you wanted to, except for checking layouts. Some developers do just that. But most use a combination of the command line and graphical (GUI) tools.

If you use a GUI editor you can be up to speed very quickly for your day-to-day coding needs. Check with other people that are into the same kind of programming language you want to use for their preferences. If you use what they use, you can take advantage of the little plugins and scripts that they provide.

You will probably want to use a version control system for your development. Lots of people here use Bazaar, but Subversion and Trac are popular, too.

---

