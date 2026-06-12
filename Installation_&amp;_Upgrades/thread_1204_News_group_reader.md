---
title: "News group reader"
date: 2004-10-19
forum: Installation &amp; Upgrades
---

### Post by Acid_Wit on 2004-10-19
Is there one?  If there is I can't find it  :cry:

---

### Post by stodge on 2004-10-19
It's called Pan. I don't know if it's on the CD or if you have to get it through Universe.

---

### Post by cybrjackle on 2004-10-19
Pan = universe
Thunderbird = main

```
$ sudo apt-cache show pan
Package&#58; pan
Priority&#58; optional
Section&#58; universe/news
Installed-Size&#58; 3692
Maintainer&#58; S\uffff\uffffren Boll Overgaard &lt;boll@debian.org&gt;
Architecture&#58; i386
Version&#58; 0.14.2.91-1
Provides&#58; news-reader
Depends&#58; libatk1.0-0 &#40;&gt;= 1.6.0&#41;, libc6 &#40;&gt;= 2.3.2.ds1-4&#41;, libglib2.0-0 &#40;&gt;= 2.4.1&#41;, libgnet2.0-0 &#40;&gt;= 2.0.4&#41;, libgtk2.0-0 &#40;&gt;= 2.4.4&#41;, libgtkspell0 &#40;&gt;= 2.0.2&#41;, libpango1.0-0 &#40;&gt;= 1.5.2&#41;, libpcre3 &#40;&gt;= 4.5&#41;, libxml2 &#40;&gt;= 2.6.10&#41;, zlib1g &#40;&gt;= 1&#58;1.2.1&#41;, libpango1.0-common
&#91;b&#93;Filename&#58; pool/universe/p/pan/pan_0.14.2.91-1_i386.deb&#91;/b&#93;
Size&#58; 1191518
MD5sum&#58; 4124c0cfb81d40b78cb1ec35209fddea
Description&#58; A Newsreader based on GTK2, which looks like Forte Agent
 Pan is a newsreader, loosely based on Agent and Gravity,
 which attempts to be pleasant to use for new and advanced
 users alike. It has all the typical features found in
 newsreaders and also supports offline newsreading,
 sophisticated filtering, multiple connections, and a number
 of extra features for power users and alt.binaries fans.
Bugs&#58; mailto&#58;ubuntu-users@lists.ubuntu.com
Origin&#58; Ubuntu

```

or Thunderbird is also a news reader

```

$ sudo apt-cache show mozilla-thunderbird
Package&#58; mozilla-thunderbird
Priority&#58; optional
Section&#58; mail
Installed-Size&#58; 32648
Maintainer&#58; Alexander Sack &lt;asac@debian.org&gt;
Architecture&#58; i386
Version&#58; 0.8-2ubuntu2
Provides&#58; mail-reader, imap-client
Depends&#58; libatk1.0-0 &#40;&gt;= 1.7.2&#41;, libc6 &#40;&gt;= 2.3.2.ds1-4&#41;, libfontconfig1 &#40;&gt;= 2.2.1&#41;, libfreetype6 &#40;&gt;= 2.1.5-1&#41;, libgcc1 &#40;&gt;= 1&#58;3.4.1-3&#41;, libglib2.0-0 &#40;&gt;= 2.4.6&#41;, libgtk2.0-0 &#40;&gt;= 2.4.4&#41;, libpango1.0-0 &#40;&gt;= 1.6.0b&#41;, libstdc++5 &#40;&gt;= 1&#58;3.3.4-1&#41;, libx11-6 | xlibs &#40;&gt;&gt; 4.1.0&#41;, libxext6 | xlibs &#40;&gt;&gt; 4.1.0&#41;, libxft2 &#40;&gt;&gt; 2.1.1&#41;, libxp6 | xlibs &#40;&gt;&gt; 4.1.0&#41;, libxrender1, libxt6 | xlibs &#40;&gt;&gt; 4.1.0&#41;, zlib1g &#40;&gt;= 1&#58;1.2.1&#41;
Recommends&#58; myspell-en-us | myspell-dictionary, xprt-xprintorg
Suggests&#58; mozilla-thunderbird-offline, mozilla-thunderbird-typeaheadfind, mozilla-thunderbird-inspector, mozilla-firefox, ttf-bitstream-vera, ttf-freefont, mozilla-thunderbird-enigmail
Filename&#58; pool/main/m/mozilla-thunderbird/mozilla-thunderbird_0.8-2ubuntu2_i386.deb
Size&#58; 11300686
MD5sum&#58; 5d0c3ea11b6eac8e1addb8b15a2d02b7
Description&#58; Mozilla Thunderbird standalone mail client
 Mozilla Thunderbird is a redesign of the Mozilla mail component. The
 goal is to produce a cross platform stand alone mail application using
 the XUL user interface language. Mozilla Thunderbird leaves a somewhat
 smaller memory footprint than the Mozilla suite.
Bugs&#58; mailto&#58;ubuntu-users@lists.ubuntu.com
Origin&#58; Ubuntu

```

---

### Post by Acid_Wit on 2004-10-19
[quote="cybrjackle"]Pan = universe
Thunderbird = main

[code]$ sudo apt-cache show pan

root@ubuntu:/home/peter # sudo apt-cache show pan
W: Unable to locate package pan

E: No packages found
root@ubuntu:/home/peter #

Ummm, I seem to be missing something *HELP* :oops:

I feel so helpless (hopeless)  What should I be reading to get me started?

---

### Post by cybrjackle on 2004-10-19
Make sure you have "universe" in your sources.list

```

$ sudo vi /etc/apt/sources.list

```

```

deb http&#58;//archive.ubuntu.com/ubuntu/ warty main restricted universe
deb-src http&#58;//archive.ubuntu.com/ubuntu/ warty main restricted universe

```

```

$ sudo apt-get update

```

Then search/show/install

---

### Post by Acid_Wit on 2004-10-20
root@ubuntu:/home/peter # sudo apt-get update
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [88B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [94B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [90B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [96B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release [79B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages [3350B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release [85B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources [174kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release [81B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources [1024B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release [87B]
Fetched 662kB in 15s (44.1kB/s)
Reading Package Lists... Done

Ummm - now what? :?

---

### Post by HungSquirrel on 2004-10-20
Now:

apt-get install pan

If you're already running as root, you don't need sudo.

---

### Post by Acid_Wit on 2004-10-20
root@ubuntu:/home/peter # apt-get install pan
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package pan
root@ubuntu:/home/peter #

Oh DOH! :x

---

### Post by HungSquirrel on 2004-10-20
You didn't add universe to your apt sources.  Open /etc/apt/sources.list as root in your favorite text editor. Change these lines:

```
deb http&#58;//archive.ubuntu.com/ubuntu warty main restricted
deb-src http&#58;//archive.ubuntu.com/ubuntu warty main restricted
```

To:

```
deb http&#58;//archive.ubuntu.com/ubuntu warty main restricted universe
deb-src http&#58;//archive.ubuntu.com/ubuntu warty main restricted universe
```

Then *apt-get update* again.  Then *apt-get install pam*.

More information about the universe repository is here:
[http://www.ubuntuforums.org/viewtopic.php?t=197](http://www.ubuntuforums.org/viewtopic.php?t=197)

---

### Post by Acid_Wit on 2004-10-21
*sigh*
root@ubuntu:/home/peter # deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
bash: deb: command not found

---

### Post by cybrjackle on 2004-10-21
[quote=Acid_Wit]*sigh*
root@ubuntu:/home/peter # deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
bash: deb: command not found[/quote]

What are you trying to do?

You need to add that line to your:

/etc/apt/sources.list

---

### Post by FLeiXiuS on 2004-10-21
**Acid_Wit**

Simply follow these instructions.  Adding 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe

to the apt-get repository list is a method of adding a new location for apt-get to search in.  Inorder to achieve this, Follow these instructions.

Login as root with this command...

```
sudo gedit /etc/apt/sources.list
```

Add the follow lines to the end of the file...

```
deb http&#58;//archive.ubuntu.com/ubuntu warty main restricted universe
deb-src http&#58;//archive.ubuntu.com/ubuntu warty main restricted universe
```

After this, File&gt;Save! :-)  Then 2 more steps...

```
apt-get update
apt-get install pan
```

 :lol: Thats it, goodluck.  Should be pretty self explanatory after that!

---

### Post by Acid_Wit on 2004-10-22
I would like to thank you guys for not blowing your collective cools and being so patient with me.
 I guess this won't be the last time I'll be asking for assistance, and I hope I can count on you in the future. :lol:

Cheers! \:D/

---

### Post by Vlammend on 2004-11-09
Use Synaptic, Although I do not know the english words of the menu, but it will be something as "Tools" - "packagesSources" now check the universe sources. (Instellingen - Pakketbronnen in dutch)
reload and when you search Pan, you willl find it.

hmm, I see that I posted to soon, did not see the second page. sorry!!!  :D

---

