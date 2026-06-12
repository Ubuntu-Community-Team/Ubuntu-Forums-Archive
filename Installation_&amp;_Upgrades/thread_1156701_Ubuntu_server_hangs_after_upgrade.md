---
title: "Ubuntu server hangs after upgrade:"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by ub.rookie on 2009-05-12
Before i resort to wiping out all my work of ubuntu server 8.04 TLS 64 bit, i need to know if this is my last option i mean absolutely no way out... :confused:

My server died :( 
I only made a rookie mistake in the middle of night, i upgraded all the packages and never bother to read the warnings, just keep saying Y how stupid of me to believe whatever i am doing is to up to date my server ;)

Well, now i have dead server which hangs while boots up any help is appreciated.

Here is a detail count of where i stand...

Problem #-o
    The server starts and after grub loader it hangs.
   
  If ESC is pressed when “GRUB loading stage 1.5” comes, and following options appear
   
  Ubuntu karmic (development branch). Kernel 2.6.24-24-server
  Ubuntu karmic (development branch). Kernel 2.6.24-24-server (recovery-->
  Ubuntu karmic (development branch). Kernel 2.6.24-24-generic
  Ubuntu karmic (development branch). Kernel 2.6.24-24-generic (recover-->
  Ubuntu karmic (development branch). Kernel 2.6.24-23-server
  Ubuntu karmic (development branch). Kernel 2.6.24-23-server (recovery-->
  Ubuntu karmic (development branch). Kernel 2.6.24-23-generic
  Ubuntu karmic (development branch). Kernel 2.6.24-23-generic (recover->
  Ubuntu karmic (development branch). Memtest86+
   
  Selected Ubuntu karmic (development branch). Kernel 2.6.24-24-server (recovery-->
  Asks for LUKS passphrase….
  Brings me to following menu
  resume
  clean
  dpkg
  fsck
  grub
  netroot
  root
  xfix
   
  selected dpkg
  pkg libuuid-perl has broken dep on perlapi-5.10.0 
    Removing libuuid-perl because I cant find perlapi-5.10.0
  Investigating doc-base 
  Pkg doc-base broken dep on libuuid-perl
    Removing libuuid-perl because I cant find perlapi-5.10.0
  Pkg libsnmp-dev has broken dep on libsnmp15
    Removing libsnmp-dev  because I cant find libsnmp15
  Done
   
  /usr/share/pyshared/distupgrade/distupgradecache.py:120: DeprecationWarning:Accessed deprecated property package.candidatedownloadable, please see the version class for alternatives.
  If (not pkg.candidatedownloadable and /usr/share/pyshared/distupgrade/distupgradecache.py:882: deprecationWarning: Accessed deprecated property package.candidateorigin, please see the version class for alternatives
    For origin in pkg.candidateorigin:
   
  …. Hung here…. ctrl+alt+del pressed to restart
       

   
   
  Again tried to boot as 
   
  Load everything with [OK]
  Then
   
  MySQL database server mysqld   [failed]
   
  GUI login prompt appears, at the bottom left on desktop “Options” selected
  Click on select session
  Click on Failsafe Terminal
  Click on Change Session
   
  Enter username/pwd
   
  Now I get command prompt…
   
  When exit from command prompt and resume load it takes to GUI login where after entering user name and password it goes into GUI interface and give a blank screen.
   
  At this point there is no other way out but to shut down server through power switch [FONT=Wingdings]:([/FONT]
   
   
  PLEASE HELP !!!

---

### Post by veloce on 2009-05-25
I had a similar problem with an upgrade to Jaunty.  It had failed half way through the update and was just a mess.

I downloaded the alternate disk for Jaunty and managed to get it to finish the install.  Not sure if such a thing is available for karmic ...

---

