---
title: "Reasons why I aint using ubuntu on my personal desktop..."
date: 2004-10-16
forum: General Help
---

### Post by lenkki on 2004-10-16
First of all I don't want rant on you guys, ubuntu is a very good distro that I recommend to folks. But I aint using it myself for a few reasons (which I'd like corrected). 

Second, I don't realy know where to post this  :roll: 

The things keeping me from installing Ubuntu on my own rig is

1) Partitioning during install.  I have several disks and a somewhat advanced partition install. And I want to have my own partitions for /boot /home and /var and a few other partitions mounted under /home/~/storage/ . Also I want to be able to use Reiser4 (or atleast ReiserFS 3 )

2) The Package tree seems (from what I've read) quite thin. 

3) I'd realy want xorg-x11 6.8.0 instead of xfree 4.3.0 

Some suggestions I would also like to point out;
1) Having "sudo apt-get update" and "sudo apt-get upgrade" on a monthly cron-job with nice 19
2) Automagically detect &amp; install ATI/Nvidia drivers for xfree. 

I'm currently using Gentoo w/ gnome 2.8, give me a good reason to make the switch ( mind you I'm quite happy with my current config )

---

### Post by lenkki on 2004-10-16
oh and I'm using the Warty preview relase linked to from /.

---

### Post by ming0 on 2004-10-16
I'm not even going to take the time to argue why a person would want Ubuntu over Gentoo--this is a pretty obnoxious (Inflammatory) post, in my opinion. :?

---

### Post by disposable on 2004-10-16
[quote=lenkki]
3) I'd realy want xorg-x11 6.8.0 instead of xfree 4.3.0 
[/quote]
From the Ubuntu Linux [FAQ](http://www.ubuntulinux.org/support/documentation/faq/x.org): "Warty Warthog includes XFree86 4.3.99 packages with much improved hardware support. The next Ubuntu release, codenamed Hoary Hedgehog will use the X.org server instead."

[quote=lenkki]
2) Automagically detect &amp; install ATI/Nvidia drivers for xfree. 
[/quote]
I thought you wanted X.org?

---

### Post by flygmaskin on 2004-10-16
Well, if you are happy with your current setup there really isn't any reason to switch.

---

### Post by kmoffat on 2004-10-16
[quote=ming0]I'm not even going to take the time to argue why a person would want Ubuntu over Gentoo--this is a pretty obnoxious (Inflammatory) post, in my opinion. :?[/quote]

I don't feel that post was inflammatory. I feel he was stating his reasons for not preferring ubuntu; it did not allow him to set up his machine in the way he wanted, etc.... He stated that he recommended ubuntu! 

As to why to use ubuntu, it's very up to date, it's a single cdrom download, it's quick, and the install is without effort.

---

### Post by kmoffat on 2004-10-16
> **lenkki]
2) Automagically detect &amp said:**
> 
I thought you wanted X.org?

I don't think nvidia drivers and x.org are incompatible, are they? I'm pretty sure I use them togither on Slackware 10, though I don't know about debian packages.

There is always the option of downloading and installing the nvidia driver .run file from nvidia.com.

---

### Post by AndersAA on 2004-10-16
1 : .. the partitioning in the ubuntu installer is the best I've seen in any gui installer.  And while it doesn't support reiser4 (... which is very understandable, wouldn't you agree?..) you can have reiserfs, which you mention in your post.

2 : debian packages you can find anywhere, and you can (through gui) enable the universe list and add package repositories.

3 : Personally I've had quite a lot of problems with xorg 6.8, and I wouldn't have a distro aiming at ease of use to be broke.

Your suggestions:
1: .. you really think this is a good idea?  No, you never want to auto update anything, maybe security updates, upgrades can break, you dont want to automatically break a lot of systems.
Something like a update thing in the icon bar that tells you about new updates is imho a better idea.
2: Because of licensing they can not automatically install binary only drivers.  But ubuntu should auto detect normal xfree/xorg drivers and use them.

---

### Post by Perfect Storm on 2004-10-16
> **kmoffat][quote=lenkki]
2) Automagically detect &amp said:**
> 
I thought you wanted X.org?

I don't think nvidia drivers and x.org are incompatible, are they? I'm pretty sure I use them togither on Slackware 10, though I don't know about debian packages.

There is always the option of downloading and installing the nvidia driver .run file from nvidia.com.[/quote]
--------------------------------------------------------

Xiorg and nvidia drivers aren't incompatible. I'm using Xorg 6.8.1 and nvidia driver 6111 on my Mandrake Linux.
No problem whatsoever.

---

### Post by lenkki on 2004-10-16
> [quote]
lenkki wrote:

2) Automagically detect &amp; install ATI/Nvidia drivers for xfree.

I thought you wanted X.org?[/quote]

Just a typo, xfree/xorg  

kmoffat: No they are not incompatible, I didn't mean that.

You can can choose the partition type in the latest cd ? What about mountpoints ?

Reiser4 isn't realy unstable, sixpack-joe will probably not use the manual partitioner anyhow. I'm currently using Reiser4 with a lovepatched 2.6.8.1 kernel.  And I have to say it's blazingly fast. And I havn't had a single problem with it. 

I also had some problems with the first xorg 6.8 release but it has since made it into the portage stable tree. So I would think it's fixed. 

Maybe not automagic updates, but an easier way for upgrades Joe-Sixpack might have some problems with aptget and the frontend whatever it was called...

Licensing ? ah you mean the user has to "read and accept" the eula. Just prompt like 
"Xorg configurator detected an nVidia TI4800 graphics adapter would you like to install the latest nVidia released drivers? [yes] [no] "  selecting yes pushes the eula to the screen.

---

### Post by FLeiXiuS on 2004-10-16
Hault all of this stupidity.  If he doesn't want Ubuntu then so be it.  He will find his own paths.  One can not flame another for not agreeing with a distrobution.  Gentoo is very well an absolute patriarch to other distrobutions.  Ubuntu is certainly following in its foot steps.  

The ideas in which he wants out of Ubuntu is completely obsurd.  A lazy linux-man in my words.  Take the extra 5-10 minutes to throughly complete the Nvidia / ATI install for your kernel.  Its not all that difficult.  

Also, have you tried manually partitioning?  Or were you too lazy to ignite this  also?

---

### Post by arctic on 2004-10-16
i would say: simply put ubuntu on one extra parttion for playing around with it and keep one other distro for you everyday work. on my box, vidalinux is my current work desktop and ubuntu my "fiddle and tweak around" distro. there are still some things which keep me from using it as my primary os (you guess.... networking troubles....) :P

---

### Post by cybrjackle on 2004-10-16
1.)  The original pre-release cd allowed you to setup your partions anyway you please, I use LVM w/ ext3 and xfs.  (reiser3, jfs and ext2 are there)  Reiser4, check your gentoo livecd, cause I run a gentoo box w/ reiser4 and it wasn't a cd that "GENTOO" puts out, right?  RIGHT!  If your such an elitist, build your own patched kernel, mv/cp re-partion and reboot.  Sweet eh?

2.)  package tree = thin???

```

$ sudo apt-cache stats
Password&#58;
Total Package Names &#58; 18006 &#40;720k&#41;
  Normal Packages&#58; 13921
  Pure Virtual Packages&#58; 226
  Single Virtual Packages&#58; 947
  Mixed Virtual Packages&#58; 161
  Missing&#58; 2751
Total Distinct Versions&#58; 14098 &#40;677k&#41;
Total Dependencies&#58; 90756 &#40;2541k&#41;
Total Ver/File relations&#58; 15078 &#40;241k&#41;
Total Provides Mappings&#58; 2549 &#40;51.0k&#41;
Total Globbed Strings&#58; 132 &#40;1681&#41;
Total Dependency Version space&#58; 400k
Total Slack space&#58; 107k
Total Space Accounted for&#58; 4339k

```

Check your gentoo tree again, your thin....

3.)  Why?  You will see it in the next release, but I ask why?  Do you really suck up every resource for transparency that doesn't work all that great?  Ok....

________________________________________________________

1.)  Cron job, no thanks I run a server and what like to know whats upgrading.  Thx for the funny thought.

2.)  Gentoo doesn't, for that matter, not to many Linux distrobutions do.


------------------------------------------------------------------------------------


Do your self a favor, go back and re-think your questions and ask why you shoul run gentoo instead of ubuntu and see if you care.   Keep in mind, I run Ubuntu, Fedora2, Rawhide w/SElinux Active, Gentoo w/ reiser4 and gcc-3.4x and a list of other distros, so please get your facts straight and re-think your thoughts.

Sorry, I hate to come off harsh but your just wrong......

---

### Post by williamroddy on 2004-10-17
Ubuntu is a release CANDIDATE. Some will vote for it, others will not. I vote for it.

I have watched Ubuntu spring up from the earth, show promise, blossom, and beome beautiful to many of us, all in just a month.

It seems to be a grass-roots candidate. I will wait with excitement for what it may become with six more months of growth.

It is sad for us all of us, in all our countries of the world, that we do not have such an excellent selection of candidates from which to chose for our governance as we all freely do with Linux distributions.

This candidate has my support and, if it keeps its promises, I will vote for it again next times.

Meanwhile, I will keep in mind that it really is not a religion, nor a political movement, but something that allows me to do things on my computer.

We may never achieve complete world peace, but we should all work toward it, in our own way.

Thank you for allowing me to say these things.

Toward peace,
Wil

---

### Post by ubuntu-geek on 2004-10-17
Just a quick comment. While the APT respository isn't as complete as gentoo, fedora and some other distro's.. Its simple to rebuild a deb package for Ubuntu. 

Maybe i'll make a quick howto. :)

---

### Post by cybrjackle on 2004-10-17
[quote=ubuntu-geek]Just a quick comment. While the APT respository isn't as complete as gentoo, fedora and some other distro's.. Its simple to rebuild a deb package for Ubuntu. 

Maybe i'll make a quick howto. :)[/quote]

Why do people keep saying this???


>  $ sudo apt-cache stats
Password:
Total Package Names : 18006 (720k)
  Normal Packages: 13921
  Pure Virtual Packages: 226
  Single Virtual Packages: 947
  Mixed Virtual Packages: 161
  Missing: 2751


Like I said, i use gentoo/fedora too, but they come no were close to debian/ubuntu....

---

### Post by ubuntu-geek on 2004-10-17
Not complete in some ways.. Missing some apps.. :)

---

### Post by lenkki on 2004-10-17
Cybrjackle:
 I'm sorry that you feel that way. 
Would you please be a little less offensive ? I'm by no means an elitist unless you missed it. I'm trying to help you guys here. And yes the gentoo livecd doesn't come with a reiser4 enabled kernel. But the thing here is Gentoo is an advanced distro where you are expected to do things your self. Such as booting a love patched liveCD and installing using reiser4 from there.

I can build my own kernel and I can move it to /boot/ but if I repartition I lose the data from the root disk and I need to reinstall and lose the kernel again. Unless I start to copy away my entire root volume somewhere which is troublesome.

Yes I checked the default tree is this, I couldn't find any C++ programming IDE like Kdevelop or Anjuta in the tree.  
Note DEFAULT tree. 

And xorg it's not question i I want transparency or not. It's a question about using an X11 implementation that is activly maintained by a big group of programmers. Or running an unmaintained old version of xfree that has been patched by others. 

Cron job was just a suggestion. And I realise it might not be good for every one. But I'd like to have my system periodically updated. Atleast when I install it for some peeps who get an heart attack everytime they open up anything else but firefox / thunderbird / ooffice . It would be nice if their system was automatically updated. 

I get the feel that Ubuntu linux is geared towards the home user and not the server market. And this far it has been an distro with minimal ammount of configuration thus aiming at less advanced computer user. Therefore it would be logical to automatically install or propose to install the proper graphics drivers.  Gentoo is once again an advanced distro where you are supposed to do this kind of stuff yourself.

I realise that I missed the manual partitioner and I'm sorry about it.  You're telling me to rethink I'll give the same words to you re-think who this distro is aimed at and what are the goals ? Before you start taking out you'r anger on  a forum post.

Fleixius:
Why is an automatic graphics driver install absurd ? No way Joe-Sixpack will attempt an manual ATI driver install or slim chance at nVidia. 

ubuntu-geek:
Yet again ease of use. You shouldn't need to rebuild packages  from other dists.

And please you're using the debian tree, the default tree in ubuntu is just 4400 some total package names, and I'm not sure if that is with different versions of the same package counted or not.  Gentoo is at about 8000 different programs, not counting different versions FYI.

The thing is I'm stressing the default install to help Joe-Sixpack. Ubunutu is IMO a "complete package" and should thus not require extra tinkering with apt sources or manual install of common drivers.

And please forgive me for being ignorant with the partitioner I just plainly missed it. I guess there is no excuse I can make.

---

### Post by cybrjackle on 2004-10-17
If we really need to go though this whole reiser4 thing again, here is the final example of why it is not there.

1.)  It is not in the Vanilla kernel, until it makes it in there, your not going to see it in very many "normal/good" distro's.  If you have ever read a lot of the things Hans has said, there is a good chance it will be awhile before you see it in vanilla ;-)

2.)  Did you add "universe" ?

3.)  As said several times, next version.
> 
Warty Warthog includes XFree86 4.3.99 packages with much improved hardware support. The next Ubuntu release, codenamed Hoary Hedgehog will use the X.org server instead.

4.)  Can't help with the cron job, I personally just think it is a mistake, if you set people up with ubuntu, make a cron job your self, if there used to windows, tell them to open "synaptic" and click on 2 buttons, no more different than windows.

5.)  
> Ubuntu is suitable for both desktop and server use. The current Ubuntu release supports Intel x86 (IBM-compatible PC), AMD64 (Hammer) and PowerPC (Apple iBook and Powerbook, G4 and G5) architectures.


Check out the licenses for Nvidia/Ati and that is why you wont see them done by default in a Debian or very many Linux distro's.

---

### Post by ubuntu-geek on 2004-10-17
> ubuntu-geek:
Yet again ease of use. You shouldn't need to rebuild packages from other dists.

And please you're using the debian tree, the default tree in ubuntu is just 4400 some total package names, and I'm not sure if that is with different versions of the same package counted or not. Gentoo is at about 8000 different programs, not counting different versions FYI.

 :shock:  Wow so harsh.. I was simply stating it didn't have SOME apps and SOME newer versions of software since its in freeze because of the release of warty.. And was suggesting if someone wants something that isnt available build it..  :shock:

---

### Post by ulrich on 2004-10-17
hi,

i used gentoo for the last 2 years as main os, and really liked the the way some things work. i also thought that compiling for yourself and choose optimization -flags for your system is the best that can happen to you, but after trying ubuntu, i ditched my beloved gentoo.
i think gentoo rocks if youre REALLY into coding and you know what all the compiler-flags are for, you know what program needs what optimization-flag and so on, but if youre an average user, you set some optimizationflags and thats all. but not every programm likes this flags you choose. some programns even slow down if there is too much optimization.

after installing ubuntu, i realized that compiling isnt for me.
leave this to the people who know what theyre doing.
gnome for example is in ubuntu way more responisive than it ever was in gentoo. maybe im too lame for gentoo, but im more into using the desktop than compiling it i realized.

and for youre things you like to see in ubuntu:

x.org-6.8:
looks really cool and compromising but its far from being ready.
the composite extension needs way too much ressources and if youre using
an ati-card you have to stick with the dri. which means: no 3d accel. sucks.
6.8 is more for playing around but not for everyday use.

the same goes for reiser4.
it really looks great, but even with gentoo you have to use love-sources and the like to get reiser4. you than have a heavily patched kernel without knowing if some patches break the rest of your system.
also theres no way so far for converting reiser3 to reiser4.

and yeah, the ubuntu-installer lets you choose different mountpoints, you can choose if you want to format, or use the existing data, and so on.
if not, you can always edit your fstab later
.
the reason for ubuntu i give is: it just works.

ulrich
sorry if my english sucks. me is kraut.

---

### Post by lenkki on 2004-10-17
> cyberjackie whatever wrote:
3.) Why? You will see it in the next release, but I ask why? Do you really suck up every resource for transparency that doesn't work all that great? Ok.... 

You asked, I answered you'r question.

> 3.) As said several times, next version.

Warty Warthog includes XFree86 4.3.99 packages with much improved hardware support. The next Ubuntu release, codenamed Hoary Hedgehog will use the X.org server instead.


I'm already aware of xorg being in the next version, I do read the replys I get.

1.)  Acceptable, but I'm kind of in love with reiser4 :oops:

2.) No, I said default tree. Again I don't think you should need to be tweaking the sources list. 

4.) thing is they don't even know how to update it in windows. And even if I told them to, they wouldn't.  (think old geezers)  :wink: 

5.)  I havn't read the license. But I can't see why it would be any different to ask if the user wants it installed, ask if he/she accepts the license and then install it and auto configure X. As compared to the user doing apt-get on nvidia-glx or whatever accepting the license, installing it and reconfiguring X himself? I'm no lawyer but it seems like the same thing to me. 

Oh ulrich, I think the reason ubuntu is more responsive is due to some other programs bosting performance (or you missed some features in the kernel) like prelink (not sure if ubuntu uses prelink but it would surprise me if it didn't).  The optimize flags don't realy affect desktop applications that much, mostly the proggies just sleep waiting for userinput anyhow.  :wink: 

Anyhow I feel like I have gotten the information I wanted. 
And said my 0.02$ , I don't see any reason in keeping arguing. It's like the special olympics....

I'll keep an watch out for ubuntu, the release after reiser4 makes it into vanilla will surely give gentoo a challenge. I'll keep my eye out 'till then.

---

### Post by cybrjackle on 2004-10-17
:lol: 
 :roll: 
 :shock:

---

### Post by daniels on 2004-10-17
[quote=lenkki]And xorg it's not question i I want transparency or not. It's a question about using an X11 implementation that is activly maintained by a big group of programmers. Or running an unmaintained old version of xfree that has been patched by others.[/quote]

For what it's worth, the patches aren't just random crap -- they've been extensively tested in Debian and Ubuntu, and lots of the patches are actually backports from X.Org to XFree86.  Both Fabio and I actively watch upstream, and I also participate in upstream.

So, while 4.3.0 is unmaintained ... it's not really 4.3.0, half a million lines of patches later.  For what it's worth, we've also fixed a lot of bugs that still haven't been fixed in 6.8, but for X11R7, we'll be pushing all our patches upstream, so everyone can enjoy Debian and Ubuntu's bug fixing.

(Obligatory declaration of bias: I'm one half of Ubuntu's X maintainence team.)

---

### Post by cybrjackle on 2004-10-19
lenkki,

If your still listening you might check these out

sudo apt-get install cron-apt apt-watch

They are in "universe" so you will have to add that, or remove the #comment#

---

### Post by surfjdh on 2007-03-28
Doesn't sound like we can change your mind, oh well, i like it alot.  easy to use in fact kinda fun to use

---

### Post by aysiu on 2007-03-28
This thread was more than two years old... and, believe it or not, all those issues have since been resolved. No point in continuing this.

---

