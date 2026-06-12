---
title: "Installing libstdc++-libc6.2-2.so.3 on Ubuntu Hardy Heron (amd64)"
date: 2008-09-24
forum: General Help
---

### Post by tinti on 2008-09-24
[SIZE="5"]ORIGINAL SOLUTION [http://www.terigo.com/?p=30](http://www.terigo.com/?p=30)[/SIZE]

Error:
error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

Installing libstdc++-libc6.2-2.so.3 on Ubuntu Hardy Heron (amd64)
April 14th, 2008 Posted in Computers, Random

I ran into a problem trying to install Websphere Commerce Professional 5.6.1 on Ubuntu it kept complaining about a missing library:
error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

So I started searching the net, and after quite a while I came across someone that had a similar problem when trying to do this under the amd64 arch. There doesn’t seem to be a native amd64 libstdc++-libc6.2-2.so.3 library available, and apparently building the library fails, so how can we get around this?

Well after finding this post on the Ubuntu forums that seems to work for me too!

So you can just

1. Download the .deb
2. Install the .deb overriding the arch
sudo dpkg --force-architecture -i libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
3. BUT, this is generally not a good idea as someone pointed out to me, it works for this situation but you run the risk of overwriting some real amd64 libraries. It just so happens that this package only has 2 files in it, so it works.
[COLOR="Red"]*4. A better solution would be to extract the files manually into /usr/lib32[/COLOR]
5. You’re good to go!

[COLOR="Blue"]*I put on /usr/lib directory.[/COLOR]

---

