---
title: "Building Deb packages for Ubuntu, need information please.."
date: 2005-12-01
forum: General Help
---

### Post by Bandit on 2005-12-01
Hey All,
I am wanting to build some deb packages for Ubuntu.
I do a lot of compiling from source and have no problems what so ever.
I was doing a little reading and decided to try my hand at creating deb's for other users and hosting them on my website.
I think I am missing a step somewhere, but idot proof documentation is hard to come by.
I ./configure, make and install the program.. It works..
Then I make a directory called DEBIAN and add the control file to it.
Seems easy enough..
I build the package using "dpkg -b gstreamer-0.9.6 gstreamer-0.9.6-bandit-i386.deb
It builds without errors..
Then I install it, it install correctly without errors.
But the next program I did is rhythmbox-0.9.2. It does good also up to the point when I go to install it and I get this kind of error:

bandit@Sigel:~/Desktop$ sudo dpkg -i rhythmbox-0.9.2-bandit-i386.deb
Password:
(Reading database ... 85651 files and directories currently installed.)
Unpacking rhythmbox (from rhythmbox-0.9.2-bandit-i386.deb) ...
dpkg: error processing rhythmbox-0.9.2-bandit-i386.deb (--install):
 trying to overwrite `/po/Makefile.in.in', which is also in package gstreamer
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 rhythmbox-0.9.2-bandit-i386.deb

I have tried uninstalling them, reinstalling them, and I also built gnomebaker-0.5.0 into a deb package.
No matter how I mix them up I can only get the one package to install and the others will not. I keep getting the error listed about..

I realy want to help support my favorite distro.. Any information will be highly appriciated.

Thanks,
Joey

---

### Post by akiro.yamamoto on 2005-12-01
I came across these sites..:
[http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)
[http://www.howtoforge.com/howto_linux_debian_deb_checkinstall](http://www.howtoforge.com/howto_linux_debian_deb_checkinstall)
I think that the checkinstall app might be very usefull... :smile:
I hope that helps....
Regards

---

### Post by az on 2005-12-01
" trying to overwrite `/po/Makefile.in.in', which is also in package gstreamer"

That is your problem.  Offhand, I know that Ubuntu does localisations/translations differently than Debian.  Perhaps you are trying to use Debian's policy for translations and are putting the po files in the same place as gstreamer's.

It should be easy to fix.  I do not know what the offical policy is, though.

---

### Post by Bandit on 2005-12-01
Thanks guys..
For the life of me I dont know why or where the /po/crudd is getting writen to. To the best of my knowledge, everthing is in seperate folders even after install via apt.
Like I said all 3 programs install very well installing from source.
Rhythmbox 0.9.0 to 0.9.2 has alot of bug fixes and requires the newest GStreamer. So I wanted to share the apt on my website and set them up so everyone can add them to the repository as well.

Akiro, I havent got a chance to try that check program out yet. I am at work, but this evening that will be my priority.

Also, I did not use the perm, postrm, and other scripts. I only used the control file. 
I looked at some of the sripts that are in the /var directory. I understand XML well enough to code a bit, but I am not fully aware of what the heck they actualy all do. I general idea from reading about them. But a detailed example would be nice.. 

I have googled my butt off. The best website I found so far was a page on IBM's website. It talked about creating the deb package and the control file, but they were very vage on the information about ther scripts that the deb packages need as well.

Thanks everyone for the help.. If anyone happends to find anymore info I would be so greatfull.. 
Thanks,
Joey

---

### Post by Bandit on 2005-12-01
Akiro,
I went home for lunch today and downloaded the checkinstall script. I ran it on rhythmbox and it seems to do the trick. I will try the other 2 programs I compiled and see if they install without issues as well. Everything looks very prommissing.. 
Thanks again :)
Joey

---

### Post by shadow on 2005-12-01
[QUOTE=Bandit]Akiro,
I went home for lunch today and downloaded the checkinstall script. I ran it on rhythmbox and it seems to do the trick. I will try the other 2 programs I compiled and see if they install without issues as well. Everything looks very prommissing.. 
Thanks again :)
Joey[/QUOTE]

Any chance you could keep me posted and possibly post the deb here when you're done? I can't seem to find anyone thats packaged it up.

I'd try myself, just cant be bothered sorting out all my dependencies from the source though. :)

---

### Post by kperkins on 2005-12-02
One way to overcome the problem you're having with overwriting files is:
dpkg -i --force-overwrite <package name>.deb

---

### Post by Bandit on 2005-12-02
Yea, But I am not trying to force them. I want to make quality packages for everyone.

I have had some success with the checkinstall program. But I used the one in the Uby repositories and it is a older version.
I thought I was one a roll today when I ran checkinstall and built a deb of gstreamer and installed it. Then I built and installed Rythmbox,, YEA... But last I built Gnomebaker and couldnt install it. Seems they both want to use a file in /var/log/scrollkeeper.log.
And since Rythmbox already wrote to it, it will not let Gnomebaker write to it and install the deb..

I just downloaded the newest version of checkinstall 1.60 and I am going to give it ago tomarrow afternoon after work and see if it works any better.

Thanks,
Joey

---

### Post by akiro.yamamoto on 2005-12-02
I've made a few deb with checkinstall but never one right after the other....
I've never come across that particular problem...Never fear I'll do a little more research and get back to you with anything useful that I find.. :smile:
BTW If you get a solution post it here so anyone else who has the same problem will be able to use your post as their HOW-To :smile:
Regards

---

### Post by Bandit on 2005-12-02
[QUOTE=akiro.yamamoto]I've made a few deb with checkinstall but never one right after the other....
I've never come across that particular problem...Never fear I'll do a little more research and get back to you with anything useful that I find.. :smile:
BTW If you get a solution post it here so anyone else who has the same problem will be able to use your post as their HOW-To :smile:
Regards[/QUOTE]

I appriciate it..
I tried ./configureing them with --prefix/usr/local and --prefix/opt/filename and still run into issues, esp with rhythmbox not linking correctly.. o'me.. drama :)
I will try the newest version out tomarrow and see if I have better luck.
Thanks again,
Joey

---

### Post by Bandit on 2005-12-02
Akiro,
I woke up early this morning before work and installed checkinstall-1.6.0
It works little nicer, but I am still running into issues that I have concluded have nothing to do with checkinstall directly.
I am still having problems with gnomebaker not wanting to install due to /var/log/scrollkeeper.log already being used by rhythmbox.
I thought by re-configuring gnomebaker and rebuiding it with the location of the var log that it might resolve this issue.
"./configure --prefix=/usr/local --localstatedir=/var/gnomebaker"
that it might make a seperate folder to put the scrollkeeper file in. But instead it only changes /usr/local/var around..
It still doesnt effect $/var/log in anyway.
I am wondering if there is a way to get it to append its data to that file instead of just overrighting it. Becuase when I compile them from source and use "make install" it has both rhythmbox and gnomebaker data appended into that file.
Any suggestions?
Thanks,
Joey

One more question.. The group ID in checkinstall, its listed as checkinstall by default. What would happen if I changed it?

---

### Post by Bandit on 2005-12-03
OK, I have come to the conclusion that Gnomebaker 0.5.0 and Rhythmbox 0.9.2 conflict when writing to /var/log/scrollkeeper.
Using the command "sudo dpkg -i --force-overwrite-dir filename.deb" works fine and does not stop the function of any of the programs. I can not comprehend why there is even a issue, other then someone else did this.. not me type thing :)
Thanks everyone for the help.
Cheers,
Joey:rolleyes:

---

