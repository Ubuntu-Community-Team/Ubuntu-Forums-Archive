---
title: "intltool installation"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by ac13 on 2009-04-16
Hey,

So I am a complete newbie to linux.
I have installed ubuntu 8.10 and I am trying to add a theme from gnome-look.org.

The info said I had to install Murrine 0.90.2 or newer.
That install failed bacause I needed a newer version of intltool.

I downloaded the intltool 0.40.6 (tar.gz) and extracted it.

opened the terminal and browsed to the extracted directory and wrote:
1: ./configure
2: make
3: make check (all ok)
4: make install (failed)

> Making install in tests
make[1]: Entering directory `/home/marcus/Desktop/intltool-0.40.6/tests'
Making install in cases
make[2]: Entering directory `/home/marcus/Desktop/intltool-0.40.6/tests/cases'
make[3]: Entering directory `/home/marcus/Desktop/intltool-0.40.6/tests/cases'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/marcus/Desktop/intltool-0.40.6/tests/cases'
make[2]: Leaving directory `/home/marcus/Desktop/intltool-0.40.6/tests/cases'
Making install in results
make[2]: Entering directory `/home/marcus/Desktop/intltool-0.40.6/tests/results'
make[3]: Entering directory `/home/marcus/Desktop/intltool-0.40.6/tests/results'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/marcus/Desktop/intltool-0.40.6/tests/results'
make[2]: Leaving directory `/home/marcus/Desktop/intltool-0.40.6/tests/results'
make[2]: Entering directory `/home/marcus/Desktop/intltool-0.40.6/tests'
make[3]: Entering directory `/home/marcus/Desktop/intltool-0.40.6/tests'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/marcus/Desktop/intltool-0.40.6/tests'
make[2]: Leaving directory `/home/marcus/Desktop/intltool-0.40.6/tests'
make[1]: Leaving directory `/home/marcus/Desktop/intltool-0.40.6/tests'
Making install in doc
make[1]: Entering directory `/home/marcus/Desktop/intltool-0.40.6/doc'
make[2]: Entering directory `/home/marcus/Desktop/intltool-0.40.6/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/man/man8" || mkdir -p -- "/usr/local/share/man/man8"
mkdir: cannot create directory `/usr/local/share/man/man8': Permission denied
make[2]: *** [install-man8] Error 1
make[2]: Leaving directory `/home/marcus/Desktop/intltool-0.40.6/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/marcus/Desktop/intltool-0.40.6/doc'
make: *** [install-recursive] Error 1


what do I do now? Im pretty lost...
Thanks for any help :)

Edit:
And why do I have to go through all this hassle?
Why can I just install the program through the Add/Remove?

---

### Post by SwordsmanJ on 2009-04-18
try the instructions here: 
[http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html](http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html)

instead of just make install $$.... do sudo make install $$. that should allow you to run the command as root, i believe, which will do the install correctly. seemed to work for me.

Note that you may need to install gettext as well, which I downloaded from here [http://www.gnu.org/software/gettext/](http://www.gnu.org/software/gettext/) and installed similarly to intltools

Edit again: And then I ran into a similar error installing gettext, so I am stuck now as well. Already created my own thread for it, so I won't clutter this one anymore.

---

