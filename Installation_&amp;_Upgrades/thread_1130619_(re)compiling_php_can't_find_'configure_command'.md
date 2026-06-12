---
title: "(re)compiling php can't find 'configure command'"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by unique2 on 2009-04-20
Hi All,

I am quite new to installing Ubuntu and PHP, so I'm sorry if this is stupid.

Background: I am using this system to hopefully run a CRM server.  I am using this document they provided to make sure my server is to spec with their requirements for the software.  I have made it pretty far I think but I am stuck on the "(re)compiling php" after installing all of the required extensions...

Question: Instructions from the requirements doc are 
"1. create a php page that contains this code:
<?php phpinfo( -1 ); ?>"
-...Done...

"2.  upload this page to your webserver"
-I put the file into "/var/www/" and called it 'recompile.php'

"3.  access the page using your browser and copy and paste the 'configure command' section into a blank file."
-I go to [http://localhost/recompile.php](http://localhost/recompile.php) in my web browser.  It looks just like a normal phpinfo page listing all of the extensions I have installed.  I did a quick search for "configure command" and couldn't find anything in the whole file.  I clicked around but couldn't find anything about a command or anything.  The requirements document said it should look something like
...
‘./configure’ ‘--with-apxs=/usr/local/apache/bin/apxs’ ‘--with-xml’‘--with-libxml-dir=/usr/bin’ ‘--
enable-bcmath’ ‘--enable-calendar’ ‘--enable-ftp’
‘--with-mysql=/usr’ ‘--with-pear’ ‘--enable-sockets’ ‘--enable-track-vars’
‘--enable-versioning’ ‘--with-zlib’ ‘--with-zlib-dir=/usr/local/lib’
‘--with-curl=/usr/local/lib’ ‘--with-mcrypt=/usr/local/lib’ ‘--with-gd’
‘--with-png-dir=/usr/lib’ ‘--enable-mbstring’ ‘--with-xsl’
...

I don't see ANYthing like this in my file on the server.

Can someone help me out with this???

If it helps the requirement document is here : 
pdf: [http://crm.saeven.net/help/dispatch.php?command=download&category=C32&id=29](http://crm.saeven.net/help/dispatch.php?command=download&category=C32&id=29)
html: [http://74.125.47.132/search?q=cache:uY3epoJlBSkJ:crm.saeven.net/help/dispatch.php%3Fcommand%3Ddownload%26category%3DC32%26id%3D29+saeven+auracle+requirements&cd=1&hl=en&ct=clnk&gl=us](http://74.125.47.132/search?q=cache:uY3epoJlBSkJ:crm.saeven.net/help/dispatch.php%3Fcommand%3Ddownload%26category%3DC32%26id%3D29+saeven+auracle+requirements&cd=1&hl=en&ct=clnk&gl=us)

---

### Post by yeats on 2009-04-20
Okay - presumably you've downloaded the source for this into a directory somewhere.  The "normal" way to install from source goes something like this (in the download directory):

```
./configure
make
sudo make install
```

Your ./configure command is specifying options for how to configure the compiling process.  Are you running it in the download directory (the directory created when you extracted the tar.gz file)?

---

### Post by unique2 on 2009-04-20
I used synaptic package manager to select the options I needed for php5, mysql, apache.

Do I need to find where synaptic put the source files for php5 and go to that directory and do the commands you just specified?

---

### Post by yeats on 2009-04-20
Er...  The instructions you're linking to are assuming that you're working from the command line.  So have you been trying to do both?  That is, have you both been working from the instructions AND using synaptic?  Just to be clear...

The PHP extensions mentioned (pear, mysql, etc.) ARE available in the repositories and you *should* be able to find them via a keyword search.  But they may not work with your instructions (which are assuming specific versions of each program/library).  Does that make sense?

If I were you, I would either try to do this all on the command line or all through the repositories - doing both seems like a recipe for frustration :-).

---

### Post by unique2 on 2009-04-20
> **chrissharp123 said:**
> Er...  The instructions you're linking to are assuming that you're working from the command line.  So have you been trying to do both?  That is, have you both been working from the instructions AND using synaptic?  Just to be clear...

The PHP extensions mentioned (pear, mysql, etc.) ARE available in the repositories and you *should* be able to find them via a keyword search.  But they may not work with your instructions (which are assuming specific versions of each program/library).  Does that make sense?

If I were you, I would either try to do this all on the command line or all through the repositories - doing both seems like a recipe for frustration :-).

I agree, this could be a recipe for disaster, haha.  Thanks for the advice. :-)

Luckily, I've been doing everything from Synaptic Package Manager.  I have been looking at the instructions and making sure I have the right things selected in Synaptic.  If I can do a (re)compile some other way using a graphical interface by selecting which options to include like:
--with-xml --with-libxml --with-mcrypt --enable-calendar --with-pear --with-mysql --with-mbstring 

Or maybe editing a file somewhere and then (re)running something in synaptic.  I'm really not extremely comfortable with command line, especially now that I have done everything via Synaptic Package Manager.

Sorry, but if it is the case that I have to do everything via command line, I don't mind learning.  :-) but is there a way to make a clean removal of everything I have added via synaptic?  Is just unchecking things in Synaptic good enough to remove them so I can start all over using the command line...?  Or will I need to re-install Ubuntu to make sure its nice and clean?

Thanks.

---

### Post by yeats on 2009-04-20
> Luckily, I've been doing everything from Synaptic Package Manager. I have been looking at the instructions and making sure I have the right things selected in Synaptic. If I can do a (re)compile some other way using a graphical interface by selecting which options to include like:
--with-xml --with-libxml --with-mcrypt --enable-calendar --with-pear --with-mysql --with-mbstring

Or maybe editing a file somewhere and then (re)running something in synaptic. I'm really not extremely comfortable with command line, especially now that I have done everything via Synaptic Package Manager.

There's not a graphical way to do this that I've seen - plus, even if there is, the main advantage of doing a configure script is that it investigates your system to make sure all dependencies are installed, then returns the result so you can see what's there and what's not.  On required dependencies the configure script exits and lets you know why.

I actually think this would be a good first command line task, myself, since you have line-by-line instructions (that's how everyone ends up learning this stuff anyway :-) ).

> Sorry, but if it is the case that I have to do everything via command line, I don't mind learning. but is there a way to make a clean removal of everything I have added via synaptic? Is just unchecking things in Synaptic good enough to remove them so I can start all over using the command line...? Or will I need to re-install Ubuntu to make sure its nice and clean?

No need to reinstall... Just open a terminal and do:

```
sudo apt-get purge *package-names*
```

with each package name separated by spaces.  Then download each source package as laid out in your instructions.  If something's amiss, the ./configure step will catch it.

Good luck!

---

### Post by unique2 on 2009-04-20
> **chrissharp123 said:**
> There's not a graphical way to do this that I've seen - plus, even if there is, the main advantage of doing a configure script is that it investigates your system to make sure all dependencies are installed, then returns the result so you can see what's there and what's not.  On required dependencies the configure script exits and lets you know why.

I actually think this would be a good first command line task, myself, since you have line-by-line instructions (that's how everyone ends up learning this stuff anyway :-) ).



No need to reinstall... Just open a terminal and do:

```
sudo apt-get purge *package-names*
```

with each package name separated by spaces.  Then download each source package as laid out in your instructions.  If something's amiss, the ./configure step will catch it.

Good luck!

Thanks! At work right now... Can't wait to get home and try this.

---

