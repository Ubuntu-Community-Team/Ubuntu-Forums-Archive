---
title: "Tomboy Notes won't appear, CPU spike, etc."
date: 2008-07-31
forum: General Help
---

### Post by FilmAficionado on 2008-07-31
I've been using Tomboy notes for months.
Suddenly a few days ago it stopped working:

I can't get it to load on startup or even manually.

```
sysadmin@blue:~$ tomboy
[DEBUG]: NoteManager created with note path "/home/sysadmin/.tomboy".
[INFO]: Initializing Mono.Addins



```

When I startup with it or click to open it, it does load when I check System Monitor: currently taking 49% cpu and 5MB memory. I'm on Hardy Heron, Thinkpad t61 so this seems a bit odd.

How can I get it working again? My notes for work and the hours I'm keeping track of for contracting are all in there (doh!). Any ideas?

Thanks in advance,

---

### Post by braddcadd on 2008-07-31
Have you tried un-installing and reinstalling?  It won't delete you data.  (Trust me)
```

sudo aptitude remove tomboy
sudo aptitude install tomboy

```

---

### Post by FilmAficionado on 2008-08-01
> **braddcadd said:**
> Have you tried un-installing and reinstalling?  It won't delete you data.  (Trust me)
```

sudo aptitude remove tomboy
sudo aptitude install tomboy

```

I took your advice and uninstalled and reinstalled. It did not make a difference, however. I can start it up, nothing will appear, and my CPU will peg to 50%...

I looked at tomboy.log but there was nothing in it besides the code in my original post.

Any other ideas?

---

### Post by FilmAficionado on 2008-08-02
Fixed.

Solution (though I didn't figure out what the problem was):

In the home directory, make a COPY of the .tomboy folder so it can be your backup (if you want to save your old notes)

Now:
sudo apt-get remove tomboy

Now delete the .tomboy directory (remember, if you want to save your old notes, keep a copy of this folder nearby)

Now:
sudo apt-get install tomboy

Now the new install would have recreated the .tomboy directory. Copy the notes from the backup you created to this new directory. Start tomboy. It should start up now and your notes will be loaded automatically.

Cheers!

---

### Post by reemM on 2008-10-05
OMG, 

thank you! I just recently did this and it worked like a charm on my problem!! I couldn't start tomboy without sudo-ing and basically that annoyed me a lot because I couldn't just start it from the panel. I know, such a stupid minor problem but this is what's convenient for me. 

Anyway, thank you again!!

Reem

---

### Post by insub2 on 2008-12-11
> **FilmAficionado said:**
> Fixed.

Solution (though I didn't figure out what the problem was):

In the home directory, make a COPY of the .tomboy folder so it can be your backup (if you want to save your old notes)

Now:
sudo apt-get remove tomboy

Now delete the .tomboy directory (remember, if you want to save your old notes, keep a copy of this folder nearby)

Now:
sudo apt-get install tomboy

Now the new install would have recreated the .tomboy directory. Copy the notes from the backup you created to this new directory. Start tomboy. It should start up now and your notes will be loaded automatically.

Cheers!

HELPFUL!  Thank you!

---

### Post by Gorse on 2009-07-22
Hey, I've got the same problem with tomboy not loading. I maybe being a bit dense, I'll make my excuses as I only just installed ubuntu a couple of days ago, but where can I find the .tomboy folder to make a copy of?

Any help much appreciated

Gorse

---

### Post by directhex on 2009-07-22
> **Gorse said:**
> Hey, I've got the same problem with tomboy not loading. I maybe being a bit dense, I'll make my excuses as I only just installed ubuntu a couple of days ago, but where can I find the .tomboy folder to make a copy of?

Any help much appreciated

Gorse

It's in your home directory. Folders starting with a . are hidden

---

### Post by Gorse on 2009-07-22
That's brilliant. Thanks a lot!

---

### Post by fakeollie on 2009-07-25
You don't even have to "apt-get remove" and "apt-get install tomboy", in case you're offline, for instance.

Remove Tomboy from panel (to stop it from running). To do that, right click the Tomboy icon and select "Remove from panel". Now move the .tomboy folder elsewhere. Add Tomboy again to panel (right click on any panel, add to panel... select Tomboy, press Add). Tomboy will run again and your ~/.tomboy will be recreated. 

Now just remove Tomboy again from panel and move all your .note files and manifest.xml back to your newly created .tomboy folder. Add Tomboy to panel one last time and everything will be like before and no more CPU spikes.

---

### Post by directhex on 2009-07-25
Please note: if this happens to you, keep a backup of your notes folder - the developers will need to inspect it in order to fix bugs!

---

### Post by elmago79 on 2009-08-06
Thanks for the info. I was about to go crazy without Tomboy. Is this a bug or something?

---

### Post by bluenix on 2009-08-08
Thanks FilmAficionado, your fix worked like a charm!


Tomboy was driving me crazy, showing "segfault" or something... maybe the .tomboy profile got corrupted in some way i guess...

---

### Post by ronaldrand on 2009-09-10
This worked for me too! Tomboy broke after upgrading to Jaunty. Thanks!

---

### Post by Bristol_Green on 2009-10-30
I've had a similar problem under Jaunty, and now under Karmic. Nothing happens when I click on the Tomboy icon in Applications. Trying to run it in Terminal gives this:
stephen@stephen-desktop:~$ cd .tomboy
[email]stephen@stephen-desktop:~/.tomboy[/email]$ tomboy

** (/usr/lib/tomboy/Tomboy.exe:4044): WARNING **: The following assembly referenced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tomboy/).


** (/usr/lib/tomboy/Tomboy.exe:4044): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Tomboy.Tomboy' from assembly 'Tomboy, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.
[email]stephen@stephen-desktop:~/.tomboy[/email]$ 




I have no idea what this means, and so don't know what to do next.
(It is quite possible that I am doing something wrong. Please explain patiently! Thank you.)

---

### Post by directhex on 2009-10-30
> **Bristol_Green said:**
> I've had a similar problem under Jaunty, and now under Karmic. Nothing happens when I click on the Tomboy icon in Applications. Trying to run it in Terminal gives this:
stephen@stephen-desktop:~$ cd .tomboy
[email]stephen@stephen-desktop:~/.tomboy[/email]$ tomboy

** (/usr/lib/tomboy/Tomboy.exe:4044): WARNING **: The following assembly referenced from /usr/lib/tomboy/Tomboy.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=1)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/tomboy/).


** (/usr/lib/tomboy/Tomboy.exe:4044): WARNING **: Could not load file or assembly 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.TypeLoadException: Could not load type 'Tomboy.Tomboy' from assembly 'Tomboy, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.
[email]stephen@stephen-desktop:~/.tomboy[/email]$ 




I have no idea what this means, and so don't know what to do next.
(It is quite possible that I am doing something wrong. Please explain patiently! Thank you.)

The common cause of this one is installing a self-compiled Mono to /usr/local. What does "which mono" say?

---

### Post by Bristol_Green on 2009-10-31
It says

stephen@stephen-desktop:~$ which mono
/usr/local/bin/mono

Does that help?

I installed mono at the request of yWriter5. If that is the problem, how do I get rid of it and get the right mono?

---

### Post by Bristol_Green on 2009-10-31
Dear directhex

I followed these instructions to install mono (from the yWriter5 site):

[COLOR="Red"]How to install mono-2.4 and mono-basic-2.4 in Ubuntu linux


I just downloaded the source for mono-2.4 and mono-basic-2.4, compiled them both, and yWriter5 ran perfectly on Ubuntu. The only issue is whether installing mono-2.4 in this way destroys the existing Mono install, but since I don't use any other mono apps on linux I don't really care.

Here are the steps I used. First, open a terminal window (In Ubuntu click Applications, accessories, terminal.)

You need to copy or paste the commands in italics below, or else download, unpack and run the script in this file to have Ubuntu do everything for you. (After unzipping, run the script with sudo sh mono24.sh)

cd ~

sudo su
(enter your regular password - you're now the root user)

wget [http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.tar.bz2](http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.tar.bz2)
tar -jxvf mono-2.4.tar.bz2
cd mono-2.4
./configure

At this point, the configure script may stop with an error. On Ubuntu you may see a message about installing bison or gettext. If so, run these commands:

apt-get install bison
apt-get install gettext

Now you can run ./configure again. If you see a message about glib-2.0 missing, run this command:

apt-get install libglib2.0-dev

Keep running ./configure and using apt-get on the packages Ubuntu reports as missing until the error messages stop. Then proceed:

make
make install

Mono 2.4 is now installed. Change back to the original folder so we can do mono-basic:

cd ..

wget [http://ftp.novell.com/pub/mono/sources/mono-basic/mono-basic-2.4.tar.bz2](http://ftp.novell.com/pub/mono/sources/mono-basic/mono-basic-2.4.tar.bz2)
tar -jxvf mono-basic-2.4.tar.bz2
cd mono-basic-2.4
./configure
make
make install

cd ..

Run this to make sure the latest version is installed and running properly:

mono -V
(upper case V)

Now exit from the root shell: by typing

exit

An example: installing yWriter5 on Linux

First, make sure you're in your home directory by typing

cd ~

now enter

wget [http://www.spacejock.com/files/yWriter5.zip](http://www.spacejock.com/files/yWriter5.zip)

and then

unzip yWriter5.zip

This will create a yWriter5 directory, with a bin folder inside it. So, enter

cd yWriter5
cd bin

and now run yWriter with this command:

mono yWriter5.exe

You can set up a shortcut on the Ubuntu desktop by specifying ~/yWriter/bin as the path, mono as the application and yWriter5.exe as the parameter. You can also run yWriter by right-clicking the yWriter5.exe file and selecting 'run with mono'
[/COLOR]

So it looks as though I destroyed the existing mono. I'm not really bothered about using yWriter5 in the future, so I'm happy to get back to the approved version of mono. Do I just install it from the Software Centre, or do I need to do something else first?

---

### Post by directhex on 2009-10-31
> **Bristol_Green said:**
> Dear directhex

I followed these instructions to install mono (from the yWriter5 site):

[COLOR="Red"]How to install mono-2.4 and mono-basic-2.4 in Ubuntu linux


I just downloaded the source for mono-2.4 and mono-basic-2.4, compiled them both, and yWriter5 ran perfectly on Ubuntu. The only issue is whether installing mono-2.4 in this way destroys the existing Mono install, but since I don't use any other mono apps on linux I don't really care.

Here are the steps I used. First, open a terminal window (In Ubuntu click Applications, accessories, terminal.)

You need to copy or paste the commands in italics below, or else download, unpack and run the script in this file to have Ubuntu do everything for you. (After unzipping, run the script with sudo sh mono24.sh)

cd ~

sudo su
(enter your regular password - you're now the root user)

wget [http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.tar.bz2](http://ftp.novell.com/pub/mono/sources/mono/mono-2.4.tar.bz2)
tar -jxvf mono-2.4.tar.bz2
cd mono-2.4
./configure

At this point, the configure script may stop with an error. On Ubuntu you may see a message about installing bison or gettext. If so, run these commands:

apt-get install bison
apt-get install gettext

Now you can run ./configure again. If you see a message about glib-2.0 missing, run this command:

apt-get install libglib2.0-dev

Keep running ./configure and using apt-get on the packages Ubuntu reports as missing until the error messages stop. Then proceed:

make
make install

Mono 2.4 is now installed. Change back to the original folder so we can do mono-basic:

cd ..

wget [http://ftp.novell.com/pub/mono/sources/mono-basic/mono-basic-2.4.tar.bz2](http://ftp.novell.com/pub/mono/sources/mono-basic/mono-basic-2.4.tar.bz2)
tar -jxvf mono-basic-2.4.tar.bz2
cd mono-basic-2.4
./configure
make
make install

cd ..

Run this to make sure the latest version is installed and running properly:

mono -V
(upper case V)

Now exit from the root shell: by typing

exit

An example: installing yWriter5 on Linux

First, make sure you're in your home directory by typing

cd ~

now enter

wget [http://www.spacejock.com/files/yWriter5.zip](http://www.spacejock.com/files/yWriter5.zip)

and then

unzip yWriter5.zip

This will create a yWriter5 directory, with a bin folder inside it. So, enter

cd yWriter5
cd bin

and now run yWriter with this command:

mono yWriter5.exe

You can set up a shortcut on the Ubuntu desktop by specifying ~/yWriter/bin as the path, mono as the application and yWriter5.exe as the parameter. You can also run yWriter by right-clicking the yWriter5.exe file and selecting 'run with mono'
[/COLOR]

So it looks as though I destroyed the existing mono. I'm not really bothered about using yWriter5 in the future, so I'm happy to get back to the approved version of mono. Do I just install it from the Software Centre, or do I need to do something else first?

You need to ensure that there are no mono-related commands in /usr/local. If you don't still have the folder you ran "make install in", then you won't be able to "make uninstall" and will need to do it manually.

---

### Post by Bristol_Green on 2009-10-31
> **directhex said:**
> You need to ensure that there are no mono-related commands in /usr/local.

How do I do that? I don't know what mono-related commands look like. Sorry to be so dim.

/usr/local 

stephen@stephen-desktop:~$ cd /usr/local
stephen@stephen-desktop:/usr/local$ ls
bin  etc  games  include  lib  man  sbin  share  src
stephen@stephen-desktop:/usr/local$ 

Where would I find these commands, and how would I recognise them?*

> **directhex said:**
>  If you don't still have the folder you ran "make install in", then you won't be able to "make uninstall" and will need to do it manually.

I tried to "make uninstall" and got this:

stephen@stephen-desktop:~$ cd mono-2.4
stephen@stephen-desktop:~/mono-2.4$ make uninstall
Making uninstall in po
make[1]: Entering directory `/home/stephen/mono-2.4/po'
Making uninstall in mcs
make[2]: Entering directory `/home/stephen/mono-2.4/po/mcs'
catalogs='es.gmo ja.gmo de.gmo'; \
	for cat in $catalogs; do \
	  cat=`basename $cat`; \
	  lang=`echo $cat | sed -e 's/\.gmo$//'`; \
	  for lc in LC_MESSAGES ; do \
	    rm -f /usr/local/share/locale/$lang/$lc/mcs.mo; \
	  done; \
	done
rm: cannot remove `/usr/local/share/locale/es/LC_MESSAGES/mcs.mo': Permission denied
rm: cannot remove `/usr/local/share/locale/ja/LC_MESSAGES/mcs.mo': Permission denied
rm: cannot remove `/usr/local/share/locale/de/LC_MESSAGES/mcs.mo': Permission denied
make[2]: *** [uninstall-data-yes] Error 1
make[2]: Leaving directory `/home/stephen/mono-2.4/po/mcs'
make[1]: *** [uninstall-recursive] Error 1
make[1]: Leaving directory `/home/stephen/mono-2.4/po'
make: *** [uninstall-recursive] Error 1
stephen@stephen-desktop:~/mono-2.4$ 

which I'm afraid I don't understand. Can't I just delete the mono-2.4 directory from File Browser?

*[color=red]eta this:
/usr/local
stephen@stephen-desktop:/usr/local$ ls
bin  etc  games  include  lib  man  sbin  share  src
stephen@stephen-desktop:/usr/local$ ls bin
al        gmcs                mdoc-update         monograph          resgen1
al1       httpcfg             mdoc-validate       monolinker         resgen2
al2       ilasm               mdvalidater         monop              secutil
caspol    ilasm1              mjs                 monop1             setreg
cert2spc  ilasm2              mkbundle            monop2             sgen
certmgr   installvst          mkbundle1           mono-service       signcode
chktrust  jay                 mkbundle2           mono-service2      smcs
cilc      macpack             mod                 mono-shlib-cop     sn
csharp    makecert            mono                mono-test-install  soapsuds
disco     mconfig             mono-api-info       mono-xmltool       sqlsharp
dtd2rng   mcs                 mono-cil-strip      mozroots           vbnc
dtd2xsd   mcs1                monodis             nunit-console      wsdl
gacutil   mdassembler         monodocer           nunit-console2     wsdl1
gacutil1  mdoc                monodocs2html       pedump             wsdl2
gacutil2  mdoc-assemble       monodocs2slashdoc   permview           xbuild
genxs     mdoc-export-html    mono-find-provides  prj2make           xsd
genxs1    mdoc-export-msxdoc  mono-find-requires  resgen             xsd2
stephen@stephen-desktop:/usr/local$ ls etc
mono
stephen@stephen-desktop:/usr/local$ ls games
stephen@stephen-desktop:/usr/local$ ls include
mono-1.0
stephen@stephen-desktop:/usr/local$ ls lib
libikvm-native.a      libMonoPosixHelper.la      libmono-profiler-aot.so.0.0.0  libmono-profiler-logging.a         libmono.so.0        monodoc
libikvm-native.la     libMonoPosixHelper.so      libmono-profiler-cov.a         libmono-profiler-logging.la        libmono.so.0.0.0    mono-source-libs
libikvm-native.so     libmono-profiler-aot.a     libmono-profiler-cov.la        libmono-profiler-logging.so        libMonoSupportW.a   pkgconfig
libmono.a             libmono-profiler-aot.la    libmono-profiler-cov.so        libmono-profiler-logging.so.0      libMonoSupportW.la  python2.5
libmono.la            libmono-profiler-aot.so    libmono-profiler-cov.so.0      libmono-profiler-logging.so.0.0.0  libMonoSupportW.so  python2.6
libMonoPosixHelper.a  libmono-profiler-aot.so.0  libmono-profiler-cov.so.0.0.0  libmono.so                         mono
stephen@stephen-desktop:/usr/local$ ls sbin
stephen@stephen-desktop:/usr/local$ ls share
applications  ca-certificates  desktop-directories  fonts  games  icons  jay  libgc-mono  locale  man  mime  mono-1.0  ppd  sgml  texmf  xml
stephen@stephen-desktop:/usr/local$ ls src
stephen@stephen-desktop:/usr/local$ 

so do I delete all the files with mono in the name?[/color]

---

### Post by directhex on 2009-10-31
> **Bristol_Green said:**
> rm: cannot remove `/usr/local/share/locale/es/LC_MESSAGES/mcs.mo': Permission denied
rm: cannot remove `/usr/local/share/locale/ja/LC_MESSAGES/mcs.mo': Permission denied
rm: cannot remove `/usr/local/share/locale/de/LC_MESSAGES/mcs.mo': Permission denied

sudo.

---

### Post by Bristol_Green on 2009-10-31
> **directhex said:**
> sudo.

:oops:

That did it!

Thank you for your patience, directhex.

[Solved]

---

