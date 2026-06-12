---
title: "[SOLVED] Xubuntu (Belkin Wireless G USB rt73) HELP!"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by Comascape on 2008-02-19
Sorry if this is a repost..I've searched the forum and can't find a definite answer to my problem.  I'm running xubuntu 7.10 and am trying to use a Belkin F5D7050 (rt73) wireless G USB adapter.  The built-in linux drivers are recognizing it and I can connect to my network using network manager.  The problem is that after I'm connected for about 60 secs or if I try to open firefox it will disconnect from the network and say that I have no network connection availiable (the dreaded red x)  Is this maybe a problem with network manager?  Do I have other options besides terminal?  Has anyone else had this problem.  I've attempted trying to us ndiswapper with the windows drivers from the disk but I am getting the "rt73 invalid driver!" error that alot of other people have gotten.  I know its probably something simple that I am missing but I am at a loss for figuring it out.  I would love to be able to use the linux drivers that already (kinda) work if possible.  Thanks ahead for any help you may provide.:confused:

update: I figured out the problem with ndiswrapper.  I had to wait untill the computer completely booted and logged in before plugging the adapter into the usb port.  I now have the adapter working thanks to this thread:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

After following those directions. (except i used package manager to install ndiswapper and utilities) and blacklisting rt73 and rt73usb it works great!!!  I knew it could be done!  I love the Ubuntu Community!

-Jason

---

