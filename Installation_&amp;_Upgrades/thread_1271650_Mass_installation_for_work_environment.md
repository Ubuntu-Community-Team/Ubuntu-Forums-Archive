---
title: "Mass installation for work environment"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by louigi600 on 2009-09-21
Has anyone ever dealt with massively installing ubuntu desktop on many different pc and laptops.

The company I work for is considering ubuntu as the standard working environment but it's unfeesable to go trough the normal install and update on all pcs.

I was considering setting up a pc and then making an image out of that that can be cloned to other pc's HDU and then just fix up the user stuff. But is all the install time hardware autosensing going to go mad or will it just require a little attention of first reboot on the destination pc ?

---

### Post by raymondh on 2009-09-22
> **louigi600 said:**
> Has anyone ever dealt with massively installing ubuntu desktop on many different pc and laptops.

The company I work for is considering ubuntu as the standard working environment but it's unfeesable to go trough the normal install and update on all pcs.

I was considering setting up a pc and then making an image out of that that can be cloned to other pc's HDU and then just fix up the user stuff. But is all the install time hardware autosensing going to go mad or will it just require a little attention of first reboot on the destination pc ?

Your idea may work assuming that all the workstations are similar in specs. Nevertheless, I think the time involved in cloning, insalling and tweaking would be similar to a straight-up, fresh install.

You may find this interesting or of value to you....

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

Good luck.

---

### Post by Mark Phelps on 2009-09-22
Your success is going to depend critically on the amount of variation between hardware on the different machines.  In our enterprise environment, for example, we have three "types" of configurations, and the other IT folks have made images (albeit, MS Windows) for each of the three types.  So, it is a simple matter to deploy the image to install the workstation.  This works largely because the users are prohibited from changing any hardware or software on the workstations.

If you have a similar situation, in that you have a small number of different types of PCs, you could try booting an example of each type using the appropriate LiveCD to give you an idea of any problems you will run in to during deployment. 

But, if you have the situation where each PC is custom configured (including at worst, both hardware and software), then I would have to agree with raymondhendson that your deployment is most likely to consist of single installations on each machine.  Why? Because you don't really know how well a particular machine will work with Ubuntu until you either run the LiveCD or install it.

If your user base has lots of laptops, that's going to pose an even worse situation because of the tendency of OEMs to customize their hardware and software. I've seen situations where the same make of laptop but slightly different model numbers have total different post-install results.

Anyway ... Good Luck.

---

### Post by louigi600 on 2009-09-23
OK ... let's go with a first report:
Cloning a 32 bit 9.04 from a Fujitsu Esprimo Mobile to a HP NC6220
with different: processors, grafix cards, ethernet cards,disc controllers and various other minor details.

After some strugle I was able to boot but the security schema seems to have gone wrong and hence a lot of applets do not work any more or have limited functionality.
Appart from that I was able to get the standard grafix environment working without any of the feared struggle.
None the less the limited functionality make it rather unusable and unmanagable hence the initial idea of cloning a standard install image is probabbly a bad approach ...
is it possible to make an install media with all the packages I need on board and above all packages updated to the time of making the madia so that subsequent installations take much less time to update.  ?

---

### Post by raymondh on 2009-09-23
> **louigi600 said:**
> OK ... let's go with a first report:
Cloning a 32 bit 9.04 from a Fujitsu Esprimo Mobile to a HP NC6220
with different: processors, grafix cards, ethernet cards,disc controllers and various other minor details.

After some strugle I was able to boot but the security schema seems to have gone wrong and hence a lot of applets do not work any more or have limited functionality.
Appart from that I was able to get the standard grafix environment working without any of the feared struggle.
None the less the limited functionality make it rather unusable and unmanagable hence the initial idea of cloning a standard install image is probabbly a bad approach ...
is it possible to make an install media with all the packages I need on board and above all packages updated to the time of making the madia so that subsequent installations take much less time to update.  ?

Here's an idea David.

-Use the OEM install for each system and update
-See if aptonCD can work for you.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Good luck.

---

### Post by lykwydchykyn on 2009-09-23
Have you looked at something like this: [http://www.informatik.uni-koeln.de/fai/](http://www.informatik.uni-koeln.de/fai/)

I generally do a pxe netinstall from a local apt-mirror server.  It's fast and the install is always up-to-date right away.  I don't do mass deployments, though.

How many machines are we talking about here?

---

### Post by louigi600 on 2009-09-23
I've not yet gone trough all the links you guys have given me .... I will though and thanks in advance.
APTonCD takes too much time to keep uptodate (or at least I suspect so)  I'd rather a local networked repository  ... but if the local repository in not possible this may come in handy.

I'm currently trying to downoload the 9.04 install DVD because I gather that the install CD has not got the OEM thing ... just to check out if there is any way it can workout for me.

The local apt-mirror might be the way to go I'll see if it's applicable over here .... getting a server to do it on might be the thing that makes it hard :-(

Anyway we are talking of over 200 employee  ... maybe not all will be migrated and maybe not all in one go ... but on the other hand over such a large install farm there will allways be someone who changed/renewed/mingled pc so it would be a long term investment.

---

### Post by lykwydchykyn on 2009-09-23
> **louigi600 said:**
> 
The local apt-mirror might be the way to go I'll see if it's applicable over here .... getting a server to do it on might be the thing that makes it hard :-(


If it helps, you don't need a massive server to run it on.  My apt-mirror is just an old P4 with some extra hard drives shoved into it.  Granted, I've never tried installing 200 clients simultaneously with it... but it's much faster than going over the internet connection for each machine.

If you're going to have 200 Ubuntu machines, a local apt-mirror is almost a must.

Also, I believe the OEM install thing is on the Alternative install CD.

---

### Post by louigi600 on 2009-09-23
Well I'm rather new to ubuntu ... All I could find is the normal install cd and with some difficulty (after having discovered that install DVD exists) the DVD ....

Yep  ... FAI looks promising .... I already put up a server for our server farm installs (that are all SUSE and REDHAT) that can manage networked kickstart/autoyast installs and it's really handy.

FAI says it can manage other non debian based linux .... it would be intresting to see ...

I'll look into FAI .... if I run into difficulties can I contact you (via phone/skype/icq) ?

---

### Post by lykwydchykyn on 2009-09-23
> **louigi600 said:**
> Well I'm rather new to ubuntu ... All I could find is the normal install cd and with some difficulty (after having discovered that install DVD exists) the DVD ....

No problem; just be aware that there are more effective ways to install, though they require a bit of research.
> 
I'll look into FAI .... if I run into difficulties can I contact you (via phone/skype/icq) ?

TBH I don't know much about FAI; I looked into it a while back as a solution to a problem i was facing, but I did little more than tinker with a setup and get familiar with its capabilities.  I certainly wouldn't want to be in a position of offering someone support on it.

---

### Post by louigi600 on 2009-09-23
Not support .... the company I work for is looking into linux to save money .... would not be able to pay your support even if you felt confident adout it ;-)
What I meant if just someone to ask some hints in a quicker manner then with forum.

Another question: does ubuntu have a native non interactive way of completing an installation like redhat's kickstart and suse's autoyast ?
Something that falls in between FAI and normal interactive install ?

---

### Post by lykwydchykyn on 2009-09-23
> **louigi600 said:**
> Not support .... the company I work for is looking into linux to save money .... would not be able to pay your support even if you felt confident adout it ;-)
What I meant if just someone to ask some hints in a quicker manner then with forum.

eh, TBH I don't really want to get into doing voice support for folks on the forums.  No offense, but I mostly come here to shoot the breeze while I wait for processes to finish at work. 

You can always try the IRC channels.

> 
Another question: does ubuntu have a native non interactive way of completing an installation like redhat's kickstart and suse's autoyast ?
Something that falls in between FAI and normal interactive install ?

I would imagine Ubuntu inherits pre-seeding support from Debian if you use the textmode installer (which you use when doing the alternate install or PXE netboot install).  I don't think the graphical live CD installer has anything like this.

Check out [http://wiki.debian.org/DebianInstaller/Preseed](http://wiki.debian.org/DebianInstaller/Preseed)

---

### Post by louigi600 on 2009-09-24
The Ubuntu 9.04 alternate cd does not appear to have OEM install functionality ... but the normal install CD and DVD seem to have something about it if you press F4.

Can I do an OEM install and also preseed ?
If so can I do that with FAI ?

Creating preseed config with  debconf-get-selections .... will that contain the current system setup including all packages installed manually with apt-get install <package> ?

How do I go about physically mirroring the ubuntu release locally. Is that a manual process like choosing the most convenient mirror and doing wget on it ?
While skimming FAI documentation I saw mkdebmirror command ... does ubuntu have mkubuntumirror or something like that ?
Maybe the ubuntu FAI package has a modified mkdebmirror command that mirrors ubuntu ?

---

### Post by louigi600 on 2009-09-26
> Creating preseed config with debconf-get-selections .... will that contain the current system setup including all packages installed manually with apt-get install <package> ?
It looks as if the answer is no and also it looks like there is some bug currently with ubuntu's "debconf-get-selections --install" which is producing nothing at all

> How do I go about physically mirroring the ubuntu release locally. Is that a manual process like choosing the most convenient mirror and doing wget on it ?
While skimming FAI documentation I saw mkdebmirror command ... does ubuntu have mkubuntumirror or something like that ?
Maybe the ubuntu FAI package has a modified mkdebmirror command that mirrors ubuntu ?

Found some documentation on doing that for version 7 ... testing if it's still applicable to current.

---

### Post by ragtag on 2009-10-09
At work we have a local mirror of Ubuntu 9.04 iso and repositories, pxe boot and pre-seeding. This means that to re-install a machine, all you need to do is hold down F12 during boot (may vary between machines), choose boot from network, and then hit Install when you get to the Ubuntu screen. About 12 min later, the machine is ready with everything configured and installed. Pretty sweet. :)  Currently we've only been using it with identical workstations, but on monday I'm going to try it out on different hardware. I don't see any big reasons it shouldn't work there too.

We also run cfengine.org for configuration files and other stuff. It lets us configure stuff on multiple clients at once, so if you need to change any configuration setting, you only need to make the change in one place. It can also push files to and run processes on the clients, and supports having different categories of machines if you need different configurations for say laptops and workstations. cfengine can be used both to aid with the original install, but also later to change stuff around.

I wouldn't suggest installing 200 machines at the very same minute, as you would be putting a lot of load on the poor server sharing out the image and the repositories, but it should be doable in a weeks time or so. :)

---

### Post by madtom1999 on 2009-10-28
As an extension to this idea:

[http://www.debian-administration.org/articles/406](http://www.debian-administration.org/articles/406) shows you how to share repositories.

I have only 512k as home BB and as the above method fails on updates I'm going to have to upgrade 5 32bit machines and one 64 bit machine.

Does anyone know of a way similar to the debian article so that I could just upgrade 1 machine and then the others can upgrade from that?

---

### Post by nickrout on 2009-10-28
As has been identified, all the machines will need to be updated to current packages after install.

apt-cacher-ng ca do this nicely. Do your first install on a machine that will be the apt-cacher-ng server. All other machines will download their updates from there rather than over the internet.

Useful even on a small SOHO lan.

---

### Post by madtom1999 on 2009-11-03
I've got a server running apt-cacher-ng and updates run/cache  fine.
I've just upgraded it to 9.10 and apt-cacher-ng on it shows no signs of the upgrade - I've yet to update other machines tho and not quite sure if its up to this. I'm hoping it will cache the next upgrade at least..

As for mass install I'm thinking that one might be able to use the minimal install CD to install and setup the server to apt-cacher-ng server point.
The next machine can have a minimal install, set up as apt-cacher-ng client and all then remaining install, all other machines likewise.

Need to sort out this upgrade thing...

---

### Post by slakkie on 2009-11-03
You might want to have a look at puppet

---

