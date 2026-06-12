---
title: "ubuntu 8.10 intrepid comes with a Buggy Perl 5.10"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by superoptimo on 2009-01-11
Hi. I've finally upgrade to ubuntu intrepid, but then I get disappointed  when my perl scripts stop running correctly.

I used to run an script for editing playlists in my Sansa player, which can be downloaded from this link:
[http://www.mazleg.com/sansa/]("http://www.mazleg.com/sansa/")

This script was running fine with perl 5.8x on Ubuntu hardy (8.04). But now on Intrepid(8.10) with perl 5.10  it gives "segmentation faul" errors. By tracing this script I've discovered that most of the errors come from the GTK module on perl.

I've just put some lines for tracing the case when it gives a Segmentation fault. Exactly it gives error when I choose an item from the Folder Tree view, and then it raises memory and executing errors when evaluating the selected Tree item. Check the line 190 in the function update_tree_folder.

However, when running this script on debugging mode, it runs without problems. So what's happening? what is causing that issue?

I guess that some binary component of perl has runtime problems when is compiled on Release mode, and I could think that some optimization options on gcc 4.3 could produce buggy apps. Who knows!! or may there is a problem in perl 5.10, since I've also seen many threads about perl 5.10 issues.

So I've just decided to return to the previous version of ubuntu (8.04) while the intrepid version becomes stable. I need to trust in my linux box, and the only thing that get me worried about are unexplainable runtime errors.

thanks.

---

### Post by Tim Sharitt on 2009-01-11
Maybe you should consider filing a bug report. Guide to filing bugs: [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by superoptimo on 2009-01-12
Hi again.

Thanks for the advice, I already filled a bug in launchpad.

However, after playing a while with some perl tweaks I just found that this is a problem more concerned with the current version of Perl (5.10) rather than an ubuntu problem, neither a GTK problem.

I've decided to try with ActivePerl 5.10 , and after installing it correctly on my Linux Box it still shows the same unwanted behavior: segfaults every where!!

But then I installed the 5.8 version of ActivePerl and surprisely the scripts just ran fine, even with the latest modules of GTK2perl and Tk-perl. So the problem is on the Perl engine itself.

What I could think about this is that Perl 5.10 is a very buggy release, so at this moment it couldn't be used for serious things. In general Perl 5.10 gives a lot of problems with Tk and GTK modules, just take a look to these other threads for example:

[http://www.perlmonks.org/?node_id=657846]("http://www.nntp.perl.org/group/perl.perl5.porters/2008/11/msg142016.html")

[http://groups.google.com/group/comp.lang.perl.tk/browse_thread/thread/a0edf5c2c5a4fc8f]("http://groups.google.com/group/comp.lang.perl.tk/browse_thread/thread/a0edf5c2c5a4fc8f")

[http://forum.freespire.org/showthread.php?t=2914]("http://forum.freespire.org/showthread.php?t=2914")

[http://www.nntp.perl.org/group/perl.perl5.porters/2008/11/msg142016.html]("http://www.nntp.perl.org/group/perl.perl5.porters/2008/11/msg142016.html")

[http://osdir.com/ml/linux.ubuntu.bugs.server/2008-06/msg00218.html]("http://osdir.com/ml/linux.ubuntu.bugs.server/2008-06/msg00218.html")

I think that Ubuntu people mistake was choosing Perl 5.10 for the Intrepid release. They just should keep the Perl 5.8 version because it works fine and it's stable.


Ironically people expects alot of perl, its lemma just says:"Perl is a stable, cross platform programming language. It is used for mission critical projects in the public and private sectors" LOL !! Now, Would you use Perl 5.10 for mission critical projects? 

The are many important components on linux that depend on it. So what about if perl becomes an unstable piece of trash?

My advice: just keep with the old Perl 5.8x version. It just works.

---

