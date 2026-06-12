---
title: "Not so sexy..."
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Aviendha09 on 2009-05-27
I love checkgmail. It does just what I need. I just found out I can now click on a link in the popup notification window to get to it in firefox. Wow. So I download libsexy and gtk2-sexy. I unzip them in desktop folders. I attempt to make them. That does not work. I get a no makefile error (but there is, 2 in fact, for libsexy: Makefile.am and Makefile.in) Now what? I have been with linux for a year, so I am still a noob. There are no instructions, an empty readme file! Which is the good file? (My system is a bit shaky, from playing with it to much.)

I am sticking with Intrepid, on a IBM P4 1.6Ghz netvista. 

[http://checkgmail.sourceforge.net/]("http://checkgmail.sourceforge.net/")

---

### Post by clonne4crw on 2009-05-27
What exactly are you trying to do here? I just installed checkgmail via the command line (# apt-get install checkgmail), it automatically installed the depended packages, including libsexy, gtk2-sexy, and checkgmail works perfectly. Did I misunderstand what the problem here is?

---

### Post by Aviendha09 on 2009-05-28
So I removed -purged checkgmail, then reinstalled it, thinking they had improved the package version to include the libs by default, but no.  The installation does not get gtk2-sexy. I have it on my desk, I just don't know what to do with it! 

The configuration file was intact. I thought when I purged, it was removed ? :-s

---

### Post by clonne4crw on 2009-05-28
What do you need to install gtk2-sexy for? checkgmail runs just fine without it. I'm a little confused.

---

### Post by Aviendha09 on 2009-05-28
So I can click on a URL in the notification window, and access it instantly in Firefox. (Instead of starting up my mail app). That's why the option is offered. Hey, how come it didn't download all it's goodies for *me*, It seems a bit unfair!!

---

### Post by clonne4crw on 2009-05-28
OOOOH! I did some searching, and found a guide on how to install it, because I checked, and it's not in the repos. Sorry about that!

I copied this from tinyurl.com/kpygly

   1. Install Perl ExtUtils dependencies:
      $ sudo apt-get install libextutils-depends-perl libextutils-pkgconfig-perl
   2. Install Libsexy, including header file:
      $ sudo apt-get install libsexy2 libsexy-dev
      The header files will pull in many other libraries.
   3. Install Gtk2-Sexy, the Perl bindings for Libsexy
      $ sudo perl -MCPAN -e 'install Gtk2::Sexy'
   4. Install Crypt:Simple:
      $ sudo perl -MCPAN -e 'install Crypt::Simple'

Seems to work for me.

---

### Post by Aviendha09 on 2009-05-28
Going at it right now...Wonder how I was supposed to guess such a procedure: "just install libsexy and the other"; indeed!

It works! It works! Great! Thank you!!

Now how do I mark this thread as SOLVED! ?

---

### Post by clonne4crw on 2009-05-28
Yeah, I would think that it would be installed automatically. Oh well.

---

### Post by wsonar on 2009-05-28
> **Aviendha09 said:**
> 

Now how do I mark this thread as SOLVED! ?


you have to use the tags feature

---

### Post by clonne4crw on 2009-05-28
The [SOLVED] thing is disabled right now for some reason. 
[http://ubuntuforums.org/showthread.php?t=1040845](http://ubuntuforums.org/showthread.php?t=1040845)
----------edit:-------------
I just added that to the title

---

