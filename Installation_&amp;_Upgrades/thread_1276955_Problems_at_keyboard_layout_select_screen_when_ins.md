---
title: "Problems at keyboard layout select screen when installing 9.04"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by shauni_g on 2009-09-27
Hi all,

Trying to install Ubuntu for the first time as a partition on my EeePC 901. I am trying to install v9.04 from a LiveCD. Everything seems to go fine until I get to the screen where it asks you to select your keyboard layout. I select USA (or just leave it at the default choice which is the same) and then click on forward and the cursor changes like it is doing something but installation never seems to move on. I have waited for over an hour and it doesn't seem to go any further, is it possible it could take longer than this to complete this step? Not sure if it is relevant but I can still type in the text box where it lets you test the keyboard layout you have selected whilst this is going on.

The EeePC has two hard drives and I have de-fragmented and chkdsk'ed the drive I want to partition and there were no reported problems. Should I do this for the other hard drive as well maybe? Also I have error checked the install CD using the option from the installation menu and no problems there either.

It suggests in the Ubuntu Pocket Guide (whose steps I am following to try and get Ubuntu installed on a partition) that the alternate install CD may work better. So I was going to try this. Can anyone recommend this as a possible solution or are there better things to try first?

That's a long post and a lot of questions but hopefully someone can help me get this up and running.

Thanks in advance,
Shaun

---

### Post by stlsaint on 2009-09-27
Hello Shaun and welcome to Ubuntu!
First off no it should be taking that long to setup your keyboard layout. Would you mind doing a few things...first check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso you are using. Then ensure that you are burning the disc for installation at the slowest speed possible probably at (4x)
2) before you go to installing please boot into livecd and go to
System>admin>partition editor and make sure there are no "flags" on the hdd you want to use for ubuntu nor is it mounted somehow.
3)Yes the alt. cd maybe will have better results as it is not the livecd and has no desktop environment as you see with the livecd. Its strictly an installer so it gets rid of all the other aspects the livecd contains.

The first two options are just basic troubleshooting that some will deem un-necessary but you never can be to safe right! :)
Hope this helps...if not post back for further assistance.

---

