---
title: "KompoZer crashes"
date: 2008-11-23
forum: General Help
---

### Post by Haruki-kun on 2008-11-23
Someone suggested me to use KompoZer for a school assignment. I looked up a bunch of tutorials and got started. It was all going well until I tried to change the font I was working on. I clicked on format and the moment I moved the pointer over the "Font" submenu, KompoZer closed itself. The same thing happened with "Size".

So I have three questions here:

1) What's happening?
2) How can I fix it?
3) If not, is there any other application I can use for websites?

---

### Post by Herman on 2008-11-23
I use KompoZer all the time and mine crashes too, mine crashes when I try to do anything with a table of insert an image too,  if I try to use it in Intrepid Ibex.
In Hardy Heron and earlier versions of Ubuntu, KompoZer is stable and works great.

I have read some other post in the forums here where someone said that no-one is working on KompoZer at the moment and that's why it hasn't been updated to work well in Intrepid Ibex, so probably it's not worth waiting around for KompoZer to be fixed. EDIT: I have added a correction for this rash statement in [post #5]("http://ubuntuforums.org/showpost.php?p=6243461&postcount=5"), (below), and I apologize for my rudeness.
Either we need to maintain or install an older version of Ubuntu that KompoZer works in or we need to look for some other way of doing things.
I multi-boot, so I still have Feisty, Gutsy and Hardy as well as Intrepid.
Hardy Heron is the 'LTS' (Long Term Support' version of Ubuntu, so it should be good for a very long time, (3 years I think).
There are other programs we can use instead but  unfortunately I don't know of a program that I like as much as good as KompoZer for editing .html pages. 
I hope someone will work on KompoZer before the three year Hardy Heron lifespan is up or some new program comes along that's as good as KompoZer.
It would be nice to learn how to write .html code by hand. We can edit .html pages with 'gedit' text editor if we know how to write the raw .html code. Some people love it, but that means instead of just writing what we want to write, we have to work a little harder and think about code at the same time. It's okay for small web pages, but if there's a lot of information we need to present in a short time...
Open Office.org writer can save as .html format if that's any help, but I haven't seriously tried it out yet. Maybe that will be alright.

---

### Post by Haruki-kun on 2008-11-24
I see... well, thank you very much.

Luckily, Kompozer seems to work fine on Windows..... which is something I will NOT tell my Anti-Linux Mac-User friends. :p

---

### Post by philinux on 2008-11-24
> **Haruki-kun said:**
> Someone suggested me to use KompoZer for a school assignment. I looked up a bunch of tutorials and got started. It was all going well until I tried to change the font I was working on. I clicked on format and the moment I moved the pointer over the "Font" submenu, KompoZer closed itself. The same thing happened with "Size".

So I have three questions here:

1) What's happening?
2) How can I fix it?
3) If not, is there any other application I can use for websites?

It's a train wreck at the the moment. The best advice seems to be either.
1. Install the seamonkey suite and use it's composer.
2. Use wine and install the windows version of Kompozer which works and does not crash.
[https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441](https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/263441)
I only have to look at a submenu and it's gone.

---

### Post by Herman on 2008-11-24
:oops: I'm back to correct myself.
> someone said that no-one is working on KompoZer at the moment and that's why it hasn't been updated to work well in Intrepid Ibex, so probably it's not worth waiting around for KompoZer to be fixed. I'm sorry, I was wrong to say that.
I found KompoZer's web site, [KompoZer]("http://kompozer.sourceforge.net/"), and KompoZer's own web forums, [WysiFreeAuthoring]("http://wysifauthoring.informe.com/"), and it looks like KompoZer is very much alive and well and has a large number of users from a wide range of operating systems, including Windows, MaxOSX and Linux Red Hat, Debian and Ubuntu.
Everyone seems to be happy with KopoZer except Intrepid Ibex users.

---

### Post by philinux on 2008-11-24
> **Herman said:**
> :oops: I'm back to correct myself.
 I'm sorry, I was wrong to say that.
I found KompoZer's web site, [KompoZer]("http://kompozer.sourceforge.net/"), and KompoZer's own web forums, [WysiFreeAuthoring]("http://wysifauthoring.informe.com/"), and it looks like KompoZer is very much alive and well and has a large number of users from a wide range of operating systems, including Windows, MaxOSX and Linux Red Hat, Debian and Ubuntu.
Everyone seems to be happy with KopoZer except Intrepid Ibex users.

Correct Intrepids version is a train wreck. Crashes by looking at it.

---

### Post by adonet on 2008-11-26
Same is happening here. Kompozer crashes with a single mouse click. In Ubuntu 8.04 it all works fine. In 8.10 it doesn't.

I hope that a fix will come available soon.

Jeroen

---

### Post by sippligood on 2008-12-10
FIX: You just have not to use Synaptic to get KompoZer. Instead get the latest release from the kompozer-website
[http://kompozer.net/zip/](http://kompozer.net/zip/)
and download, unpack and start it. No install or compilation needed.
Check here:
[http://nyuviu.wordpress.com/2008/12/...der-usb-stick/](http://nyuviu.wordpress.com/2008/12/...der-usb-stick/) (in German only but with pics)

or follow Bruce:
[https://bugs.launchpad.net/ubuntu/+s...41/comments/40](https://bugs.launchpad.net/ubuntu/+s...41/comments/40)

No crashing anymore . You may even use it from usb-stick.

Regards Sippligood

---

### Post by Herman on 2008-12-14
Thank you sippligood, that works in my i386 computers.

In my AMD64 computer I get,
```
herman@amd64-intrepid:~$ kompozer/kompozer
kompozer/kompozer-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```Regards, Herman :)

---

### Post by elugaro on 2008-12-19
I resolved the problem using wine to run the windows version in Ubuntu. It runs without problems.

---

### Post by dlmoak on 2008-12-22
I had the same problem with Kompozer crashing in Ibex.  Yesterday I discovered that if I used keyboard shortcuts instead of the mouse to access the primary menus, then it would not crash.  You can use the mouse for everything else.

---

