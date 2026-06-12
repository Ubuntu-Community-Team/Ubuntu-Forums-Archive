---
title: "Problem with the pad of a Bamboo CTH-460"
date: 2010-09-17
forum: Hardware
---

### Post by zemaniac on 2010-09-17
Hi there,  I have a problem with my Wacom Bamboo CTH-460.  

I installed it last night and the pen works well.    I am not able to clone that git stuff, I'm told that:

linuxwacom.git.sourceforge.net[0: 216.34.181.91]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)

Anyway, it recognizes my finger and the pointer works, but the buttons are crazy.

If I hit any of them, they either do left or right click, but the pointer flyes to the top left corner, making it useless!

I don't know how to solve this.
Any help is appreciated. Btw, I'm running Ubuntu 10.04 x64

Thank you!

---

### Post by Favux on 2010-09-17
Hi zemaniac,

What HOW TO are you using?  Did you install a wacom.ko?  It sounds like the sourceforge site was down temporarily for maintainance or whatever and is probably working by now.

---

### Post by zemaniac on 2010-09-17
> **Favux said:**
> Hi zemaniac,

What HOW TO are you using?  Did you install a wacom.ko?  It sounds like the sourceforge site was down temporarily for maintainance or whatever and is probably working by now.

I used the one in the linuxwacom page...

how can I check that wacom.ko? maybe I made something wrong...



it's only a matter of touchpad...

---

### Post by Favux on 2010-09-17
Hi zemaniac,

Please look over the [Bamboo Pen & Touch HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  That may help.

---

### Post by zemaniac on 2010-09-17
> **Favux said:**
> Hi zemaniac,

Please look over the [Bamboo Pen & Touch HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  That may help.

I succesfully made I.

But cannot go on with II. because of the git problem...

---

### Post by Favux on 2010-09-17
Not sure what's going on.  You installed git-core, correct?  If so there still may be a problem with the site or with some setting you have, like a firewall.  I just downloaded the 0.10.8 tar, you could use that in the meantime:  [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/)

---

### Post by zemaniac on 2010-09-17
> **Favux said:**
> Not sure what's going on.  You installed git-core, correct?  If so there still may be a problem with the site or with some setting you have, like a firewall.  I just downloaded the 0.10.8 tar, you could use that in the meantime:  [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/)


problem during the xorg macro update...

when i "make" the terminal gives me this output:

make: Non c'è da fare nulla per «all»

that can be translated in:

make: There's nothing to do for «all»

---

### Post by Favux on 2010-09-17
> make: There's nothing to do for «all» 
That usually isn't an error message.  So unless there were accompaning error messages go ahead and do 'sudo make install'.

---

### Post by zemaniac on 2010-09-18
> **Favux said:**
> That usually isn't an error message.  So unless there were accompaning error messages go ahead and do 'sudo make install'.

ok, but when I go into the directory "xf..."

I'm told that there's no ./autogen.sh in that directory... :(

---

### Post by Favux on 2010-09-18
Hmmm.  I've never actually done the xf86-input-wacom tar.  I've always cloned the git repository.  If it's saying:
```
./autogen.sh --prefix=/usr
```
doesn't work because there is no autogen.sh does:
```
./configure --prefix=/usr
```
work?

---

### Post by zemaniac on 2010-09-19
> **Favux said:**
> Hmmm.  I've never actually done the xf86-input-wacom tar.  I've always cloned the git repository.  If it's saying:
```
./autogen.sh --prefix=/usr
```doesn't work because there is no autogen.sh does:
```
./configure --prefix=/usr
```work?

it works, thanks... but it's not solved yet...

now i can move the pointer with the tuchpad, but it's buggy... the movement is never completed...

the pointer stops even if my finger is still moving...

---

### Post by Favux on 2010-09-19
Good, you're up and running!  There's a fix for touch in the HOW TO.  Read the line in blue near the top and go to post #110 or Troubleshooting near the bottom.  In wcmCommon.c you change:
```
#define BAMBOO_TOUCH_JUMPED 30
```
to
```
#define BAMBOO_TOUCH_JUMPED 300
```
and recompile xf86-input-wacom.  Remember to do 'make clean' before ./configure.

---

### Post by zemaniac on 2010-09-19
ok it works better now ;) thanks...

last thing:

multitouch doesn't work very well, do I need to configure something else?
I even don't know the "combo"...

I just scroll with two fingers, but it's a bit "laggy"... not as smooth as a mouse wheel...

---

### Post by Favux on 2010-09-19
I think you're good.  Just remember not to line up the two fingers vertically or horizontally.  Have them on a little bit of a diagonal,
> I just scroll with two fingers, but it's a bit "laggy"... not as smooth as a mouse wheel... 
That sounds about right.  At least on first use for me.  Then it gets better.

---

### Post by zemaniac on 2010-09-19
> **Favux said:**
> I think you're good.  Just remember not to line up the two fingers vertically or horizontally.  Have them on a little bit of a diagonal,

That sounds about right.  At least on first use for me.  Then it gets better.

ok, how do I configure the buttons instead?

---

### Post by Favux on 2010-09-19
I've given you a bunch of examples in the sample scripts attached to the first and second posts.  Also in a terminal enter 'man xsetwacom'.  Also look at the LWP's HOWTO:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

---

### Post by zemaniac on 2010-09-20
i have updated the driver through update-manager and now it doesn't work anymore :(

i've tried to compile again the xf86 but it's not working...


how do i make a "fresh install" again?

---

### Post by Favux on 2010-09-20
> i have updated the driver through update-manager and now it doesn't work anymore
Do you mean you let a kernel update through?

If so the new kernel's modules directory has the default wacom.ko, the one that doesn't work.  You have to go through step I. again and compile a wacom.ko from linuxwacom 0.8.8-8 and copy it over the default wacom.ko.

---

### Post by zemaniac on 2010-09-20
it works now...

thank you very much ;)


long live the ubuntu community!

---

