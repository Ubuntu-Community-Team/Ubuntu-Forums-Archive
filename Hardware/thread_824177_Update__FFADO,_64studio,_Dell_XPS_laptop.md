---
title: "Update:  FFADO, 64studio, Dell XPS laptop"
date: 2008-06-09
forum: Hardware
---

### Post by ethanay on 2008-06-09
[This is an update]("http://sourceforge.net/mailarchive/forum.php?thread_name=484D06E8.2040708%40gmail.com&forum_name=ffado-user") of my [attempt to get my Echo Audiofire2 working with my laptop running 64studio 32-bit]("http://www.ffado.org/?q=node/580")

I am posting here because there seems to be a bit of interest in firewire, and 64studio is also debian-based :)

The summary is below

1) FFADO fails to install properly using default prefix /usr/local
error while loading shared libraries: libffado.so: cannot open
shared object file: No such file or directory
fix: cp /usr/local/lib/libffado.so /usr/lib/

2) FFADO fails to install using PREFIX=/usr (scons error)
scons: *** DirNodeInfo instance has no attribute 'csig'

3) tests/test-ffado Discover failure after successful install (using fix
in #1 above)
see ffado_error #3 for full debug output

4) jackd version mismatch after successful compile of jackd with
firewire support
firewire ERR: Incompatible libffado version! (libffado 1.999.36-)
see ffado_error #4 for debug commands as requested in
[http://sourceforge.net/mailarchive/message.php?msg_name=4833D681.8080602%40joow.be](http://sourceforge.net/mailarchive/message.php?msg_name=4833D681.8080602%40joow.be)

hope this is helpful

---

### Post by ethanay on 2008-06-10
[http://www.ffado.org/?q=node/580#comment-192](http://www.ffado.org/?q=node/580#comment-192)

Computer and AudioFire2 are now communicating :)

Now I only need to get FFADO and jackd to communicate by compiling the SVN version of jack...

---

### Post by ethanay on 2008-06-12
More good news: jackd, ffado and wineasio

Full functionality with ffado, jackd, and wineasio:
[http://www.ffado.org/?q=node/580#comment-193](http://www.ffado.org/?q=node/580#comment-193)

seems like wineasio behaves badly when jackd is using ffado as its backend and isn't started before the Wine app...

however, as long as I follow these guidelines, everything seems peachy keen

---

### Post by Stochastic on 2008-06-20
This thread would be of interest to many who frequent the Multimedia & Production section of these forums.  You might consider posting another topic there that links to this.

---

### Post by ethanay on 2008-07-16
done: [http://ubuntuforums.org/showthread.php?p=5399229](http://ubuntuforums.org/showthread.php?p=5399229)

thanks for the suggestion

---

### Post by Cney on 2008-11-20
hey Ethanay,

I have a similar situation as you compiling FFADO through SVN for my Audiofire 4 on my Asus F3SV laptop and my PC using Ubuntu studio64 aswell.
Ive been Nerding on a few occasions
(Mostly all my effort is in my wireless in OSX86 now, but thats a different story :) )

Ive come as far as building the library and completing missing items. im now in scons and all i have to do is installing with the correct options.

when using Ubuntu studio though, it is important to go to administrator items, select ubuntu studio options (where you can find the memlock function) and tick the libraw1394 option.

If you do not, it will be almost impossible to build the package correctly.

as an extra hint i would advise you to check out the site of FFADO, Python and SCons. you know, for reference and stuff.

Im no pro whatsoever. just checking out the forums and tutorials. watch what happens in the terminal.

Ohyeah. last but not least. you have to install al the DEV packages of libraw, qt4. all the packages you need to compile.
or you will just get errors.

I'll keep you posted of my progress to.

Im just one step away.

A journey of a thousand miles begins with a single step" (Confusius)

Windows OS(Confusing)

---

