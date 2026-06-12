---
title: "Installing TSCLIENT 2.0.1 unstable in 9.04"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by rehilliard on 2009-05-18
I saw this version in action on an opensuse install today, and it's really great.

I can download the tar.bz2 from sourceforge, but am not clear on how to compile/install...or...for that matter, if it'll even work. 

Any insight is appreciated. Or, if there's a repository available that might have it, that would be great also.

Thanks. 
Bob in Atlanta

---

### Post by rehilliard on 2009-05-18
Update:

did some reading, and tried ./configure. 

output posted the following errors:

No package 'glib-2.0' found
No package 'gmodule-2.0' found
No package 'gobject-2.0' found
No package 'gtk+-2.0' found
No package 'libglade-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-desktop-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libnotify' found
No package 'gconf-2.0' found
No package 'libnm_glib' found

obviously, i'm missing components...but found no references in synaptics. 

Will keep trudging along...

---

### Post by Jive Turkey on 2009-05-18
try these commands before running ./configure
```
sudo apt-get install build-essential
sudo apt-get build-dep tsclient
```
this assumes that the package name for tsclient in ubuntu is in fact "tsclient."

build-essential is a bunch of packages including compilers and stuff, build-dep will install the development packages for whatever application, as long as a version is already in the repos, this works for me ~70% of the time.  If ./configure still complains about missing dependencies you will have to hunt them down yourself, synaptic is usually best for that.

Once you get configure to run correctly, you might want to read up on using checkinstall.  It is a program to help you build your own installable packages that can be easily removed, updated, or shared (i.e.: *.deb, *.rpm, etc.)

---

### Post by rehilliard on 2009-05-18
many thanks. that got rid of all but three. i'll track them down. 

i appreciate the info/insight.

thanks.

---

### Post by rehilliard on 2009-05-18
the three remaining were:

gnome-desktop-2.0
libnotify
libnm-glib

found what I think was all three, but the make fails trying to find "gnome.h" header source. tried installing gnome-devel, but no luck.

i read some posting that gnome.h was "old"...but these are the compilation errors:

tsc-main.c:7:19: error: gnome.h: No such file or directory
tsc-main.c: In function ‘tsc_init’:
tsc-main.c:119: warning: implicit declaration of function ‘gnome_program_init’
tsc-main.c:120: error: ‘LIBGNOMEUI_MODULE’ undeclared (first use in this function)
tsc-main.c:120: error: (Each undeclared identifier is reported only once
tsc-main.c:120: error: for each function it appears in.)
tsc-main.c:121: error: ‘GNOME_PARAM_NONE’ undeclared (first use in this function)
tsc-main.c: In function ‘do_logout’:
tsc-main.c:141: error: ‘GnomeClient’ undeclared (first use in this function)
tsc-main.c:141: error: ‘client’ undeclared (first use in this function)
tsc-main.c:143: warning: implicit declaration of function ‘gnome_master_client’
tsc-main.c:150: warning: implicit declaration of function ‘gnome_client_request_save’
tsc-main.c:151: error: ‘GNOME_SAVE_GLOBAL’ undeclared (first use in this function)
tsc-main.c:153: error: ‘GNOME_INTERACT_ANY’ undeclared (first use in this function)
make[4]: *** [tsc-main.o] Error 1

libgnomeui32, -common, -dev, -0 are all installed according to synaptics.

just ran out of tree-limb... 

it was fun, though a little "irritating" to not be able to reason out how to get an updated version of tsclient to run. 

Oh well.

Thanks.

---

### Post by Jive Turkey on 2009-05-19
Aw, don't give up so soon!  The ubuntu forums might not be the best place for help on this though.  If the application has its own help area or launchpad page, or IRC channel you could try there.  You could also try to get the attention of the more elite packagers for help on this.

I don't think it would qualify as a double post if you made a new thread with a title like "need help resolving dependencies for tsclient version X.XX." possibly in the Dev and Packaging forum.

If you see it through you will learn much that will benefit you later.

I'm curious, what new features are in the latest tsclient that got you started on this?

---

### Post by rehilliard on 2009-05-19
actually, a colleague of mine was telling me about how copy/paste was now working right and that the interface had changed (see attached jpg). I installed in suse and was using it and liked it better that the installed version. suse 11.1 made it easy, since this version was available for installation.

it was an adventure, but i now have "experimented" with multiple lib installs that I probably don't really need on the system...and of course, I didn't write them down to be removed!! 

I was just looking for insight into getting my hands on this new version in this distribution...is there a repository where it can be "auto-installed"? 

i'm not backing out just yet...just backed down...had to find out what jack bauer was going to be up to!

...no much on the sourceforge site in terms of a feature list or forum: 
[http://sourceforge.net/projects/tsclient]("http://sourceforge.net/projects/tsclient")

thanks.

---

### Post by rehilliard on 2009-05-19
Well, persistence paid off. I tripped over a forum posting about installing an rpm using the alien utility. 

After a little trial and error (finding the right rpm), I found this one: [http://rpm.pbone.net/index.php3/stat/4/idpl/11517558/com/tsclient-2.0.2-1.fc11.i386.rpm.html]("http://rpm.pbone.net/index.php3/stat/4/idpl/11517558/com/tsclient-2.0.2-1.fc11.i386.rpm.html")

It's for Fedora 11. 

Alien successfully created a deb installer file and I was able to install just fine.

info on alien: [http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/]("http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/")

This worked on 9.04 netbook version...

So, was this "cheating"?????  ;)

---

### Post by siquad on 2009-05-31
Using alien didn't work for me on 64bit 9.04. Instead I got the tip code from svn as of 5/30/09 and built it. It fixes many issues including an update to use later version of gnome which detects the correct location for it.

The package seems to run smoothly, but of course your mileage could vary. I'm attaching the deb package in the hope it helps someone out. I didn't know what version to give it so I kept the last known one on the site and added the date.

---

### Post by DouglasAWh on 2009-06-02
> **rehilliard said:**
> 

Alien successfully created a deb installer file and I was able to install just fine.

Any chance you could post the deb or get the getdeb.net guys to host it?

---

### Post by DouglasAWh on 2009-06-02
actually, I'll go ahead and upload.

I tested on 8.10 but it does not work (it needed another dependency and I did not go further than that).  It does work on 9.04.

---

### Post by mael on 2009-06-24
Thanks DouglasAWh!

---

### Post by wkearney99 on 2009-07-12
Got anything for a 64bit system?

---

### Post by DouglasAWh on 2009-07-12
> **wkearney99 said:**
> Got anything for a 64bit system?

I don't, but I'd assume the Alien process would work for 64-bit also.  Just go grab the source from the Fedora repos.

---

### Post by Devilotx on 2009-07-31
Perfect! I was just about to run alien myself on the rpm, but this worked perfectly, solved my disconnect/reconnect issue.

---

### Post by DarkDead on 2009-08-19
Worked here too. Many thanks!

Could you upload the deb package for the new version 2.0.2-3?
It fixes an important bug: [_Bug 485976 - tsclient reports "Host is a required field" despite a host name being provided_]("https://bugzilla.redhat.com/show_bug.cgi?id=485976")

---

### Post by DouglasAWh on 2009-08-19
> **DarkDead said:**
> Worked here too. Many thanks!

Could you upload the deb package for the new version 2.0.2-3?
It fixes an important bug: [_Bug 485976 - tsclient reports "Host is a required field" despite a host name being provided_]("https://bugzilla.redhat.com/show_bug.cgi?id=485976")

I'm in the middle of switching my work computer so I don't think I have my VMs up and I think all the laptops at work are Fedora atm, so it could take a while.  Installing and using alien doesn't require any special skill or knowledge.  Someone else can do this.

```

sudo apt-get install alien

```

I'll get to it when I get to it.  Hopefully sooner rather than later!

---

### Post by DarkDead on 2009-08-29
Well I've done it.

Alien worked for the tsclient-2.0.2-3.fc11.i586.rpm file that fixes the problem. I've attached the generated .deb to this post. It works on my computer but use it at your own risk.

There is a newer version, tsclient-2.0.2-4.fc12.i686.rpm but alient can't handle this file. I get:
```
Unpacking of 'tsclient-2.0.2-4.fc12.i686.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 155.
```

---

### Post by kelthuzat on 2009-09-07
In this application, I can't know the way to add local resoures. Any ideas ???

---

### Post by DouglasAWh on 2009-09-07
local? you mean like remoting to a VM? I don't know that that's the best idea, but if you know the VM IP, I assume it's possible.  You should probably start a new thread for questions about the app though...assuming you've got it installed, which it sounds like you do.  Feel free to put a link to that new thread here so we can help you out.

---

### Post by eduardo.heine on 2010-01-22
I was able do resolve all the dependencies, cflags and libraries from the source file, compiled it  and created a .deb package for the 64bit version.

---

### Post by lorisbel on 2010-10-28
I used alien to create a .deb package for the 64bit version of latest tsclient v. 2.0.2-8. 

1. You have to install alien:

```

sudo apt-get install alien

```

2. Download the latest version of tsclient for Fedora distro from [http://www.rpmseek.com/rpm-pl/tsclient.html?hl=com&cx=0::](http://www.rpmseek.com/rpm-pl/tsclient.html?hl=com&cx=0::)

3. Launch this command to create .deb:

```

sudo alien tsclient_2.0.2-8_amd64.deb

```

Enjoy!

---

### Post by roemer2201 on 2011-03-01
I did the same and it works like a charm, but is there a gnome-panel-applet for tsclient v2?

---

