---
title: "Compiz Fusion Experimental Plugins Won't Compile"
date: 2008-10-15
forum: General Help
---

### Post by James78 on 2008-10-15
Hi,

On many videos in youtube, we've seen cool new experimental plugins for Compiz Fusion. Things like, freewins, screensaver, elements (autumn, fireflies, snow, stars), atlantis2.

I like these plugins, but unfortunately I cannot use them. I used git to try to get these from source and install, but I always get errors when compiling, therefore thwarting all my attempts to get some cool plugins.


Messages like..```
compiling : paint.c -> build/paint.lo
compiling : freewins.c -> build/freewins.lofreewins.c: In function &#8216;freewinsInitDisplay&#8217;:
freewins.c:346: warning: passing argument 1 of &#8216;compLogMessage&#8217; from incompatible pointer type
freewins.c:346: warning: passing argument 2 of &#8216;compLogMessage&#8217; makes pointer from integer without a cast
freewins.c:346: error: incompatible type for argument 3 of &#8216;compLogMessage&#8217;
freewins.c:346: error: too few arguments to function &#8216;compLogMessage&#8217;

```

How I'm trying to do this all is...
sudo -s
<enter password>
apt-get install compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev git-core
mkdir -p compiz
cd compiz
git clone git://anongit.compiz-fusion.org/users/pat/elements
cd elements
[COLOR="Red"]make[/COLOR]
make install

------------------
It fails on make, on pretty much every plugin I try to compile. Can anyone please help me?! I really want these plugins!

I'm using Ubuntu 8.0.4.1

---

### Post by loomsen on 2008-10-15
I'm using shames repo for quite a while now.

But It's my duty to point out that you won't have too much fun with them first. Freewins really is awesome, but it's not called experimental beause some summer school schemistry nerds made it, but because it's just there to keep you tensed.

Doesn't work, you may just get a short look at it.

Anyway, here's shames repo:
```

# compiz
deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./

```

Add this to your custom sources.list if you have such, or append it to the bottom of you /etc/apt/sources.list.

Then do this to add the key:
```

wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
```

Then run apt-get update and you should get informed about available updates ;)

As I said, this is the cutting edge. You most likely won't be able to use the newest stuff unless you're prepared for some bug fixing yourself...

But, if so, I think you wouldn't have asked, eh?

However, give it a try if you like :)

---

