---
title: "ppd, pipslite, libltdl*, Epson Stylus CX2900, and Ubuntu 10.04 Lucid Lnx"
date: 2010-06-12
forum: Hardware
---

### Post by efrens on 2010-06-12
So here's my problem:
[IMG]http://img821.imageshack.us/img821/6042/packageinstallerpipslit.png[/IMG]

(Error: Dependency is not satisfiable: libltdl3 (>= 1.5.2-2))

But wait, I know what I'm supposed to do... I need to search for libltdl3 in the repository, the thing is, it's not there. It's already replaced by libltdl7 since karmic, and I have no idea about what's going on with libltdl-dev. So install libltdl7 is what I did.

Guess what though? This pipslite doesn't recognize the thing. It still gives the error. Hmmm...

What to do, what to do? I searched the repositories, downloaded and installed manually libltdl3. Pretty good, cause I was able to install this pipslite thing. However though, pipslite is throwing some error that, believe me (it's a long bloddy story of other people's experiences), started to show up since 10.04.

pipslite works only with libltdl3 IN versions before 10.04

Suggestions anyone?

Why do I want to install pipslite anyway? I know, I can read what's in your mind, buddy...

You see, I have this what they call "All-in-one" printer/scanner/copier by Epson from the Stylus series with version CX2900. Oh wait, it's not mine, it's my uncle's, as I finally convinced somebody to choose freedom, in that geeky sort of way.

Anyway, chances must be playing with me, this CX2900 doesn't have a ppd file available anywhere. If you've seen one, I beg you I'll stop breathing to get it, for a few seconds... Please...

Now without ppd (Postscript Printer Description, lurkers), I can't get my printer get understood by CUPS, in short, it won't work. Luckily, there's a tool that can make ppd's for you, made by (an EPSON shoot-off?) Avasys, called pipslite...

pipslite can make the ppd that I need for my Epson Stylus CX2900 to print. I need to be able to print. I need the ppd for my printer. I can't get it anywhere else. That why I think I should make one for myself. That why I need to get pipslite working. Anyone got suggestions?

I love you Ubuntu community! Please?

PS: As I side note, I already got the scanner part of the "All-in-one" to work decades ago when I installed iscan also from Avasys, depending from libltdl. Good for me, I can scan. But print, :cry:

---

### Post by efrens on 2010-06-13
While making this thread I thought about running pipslite on hardy. So I downloaded hardy and installed pipslite. I was able to get the ppd file I need. Yay!

BUT when I brought the file to Lucid, it's useless.

"Printer 'EPSON-Stylus-CX2900' requires the 'pipslite-wrapper' program but it is not currently installed.  Please install it before using this printer."

SO I've got some decision to make in here...

Should I put faith on the ppd file I made in Hardy to work in Lucid and try to fix this new problem about the missing pipslite-wrapper?

OR, is this problem due to the fact that I was using a ppd file I made in Hardy to use it in Lucid?

Also while searching on how to fix 'pipslite-wrapper', [this blogger]("http://blogs.gnome.org/bolsh/2009/05/26/trial-by-fire-distro-upgrade/") said "the pre-built Ubuntu binaries don&#8217;t link to the right versions of some dependencies" so he "compiled a new .deb" from source-code using dpkg-buildpackage." And I do not know how to do that exactly.

Well I've got a lot in my hands in here...
Help, anyone?

---

### Post by efrens on 2010-06-17
Well people, just dropping by to tell you guys that somehow I got this problem sorted out.

Basically, here's how I did it.
1) Give up on trying to make ppd file in 10.04. pipslite-install won't work in there.
2) Run pipslite install in 8.04 and produce the ppd file.
3) Install libltdl7 from repository
4) Download pipslite source, extract the source, cd to the extracted directory.
5) Do dpkg -buildpackage and install the resulting .deb file. (It will no longer look for libltdl3. Yay!)
6) Restart cups.
7) Run the pipslite daemon. (There's an instruction in the pipslite README file for this. Funny thing is, pipslite daemon actually runs, but pislite install still cannot make the ppd file, hence step #2.)
8) Plugin printer. When asked for ppd file, browse to the ppd file created in hardy.

Hope it works for you. If I have time, I'll put the commandline stuff I did but right now I'm just recalling from memory.

---

### Post by gimmejimmy on 2010-07-04
Hi, can you maybe send me the ppd file or post it here as an attachment?  Thanks!

---

### Post by davidmohammed on 2010-07-04
the answer for me was to install the offending package from the [hardy repository]("http://packages.ubuntu.com/hardy/i386/libltdl3/download") - it installs fine in lucid and pipslite install then works.

---

### Post by gimmejimmy on 2010-07-05
I finally got the ppd file (I'm on Mandriva), but the settings are still limited.  Paper size choices are A4 and 4x6, no letter nor legal.  How about you guys?

---

### Post by efrens on 2010-07-21
> **gimmejimmy said:**
> I finally got the ppd file (I'm on Mandriva), but the settings are still limited.  Paper size choices are A4 and 4x6, no letter nor legal.  How about you guys?

oh that. haha.
I googled sample ppd files and I think I got the knack on figuring out the markup. PPD file. Who would have thought it's just a plain text file you can gedit?

So what I did was copy from other ppd files the settings that I think I'd like to have. And then by trial and error you can see which one actually is supported by the printer.

At least that's what I remember I did.

---

### Post by JakcV on 2010-08-03
From the avasys.jp website, the ppd is automatically install in /usr/share/cups/model. Just select it when you configure the printer.
CX2900 use eklite.ppd

---

