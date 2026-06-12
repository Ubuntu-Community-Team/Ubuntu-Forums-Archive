---
title: "Need help compiling gobby 0.4.91 on ubuntu 9.04"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by movaxes on 2009-04-25
Hi, I'm having trouble compiling gobby 0.4.91 on ubuntu 9.04, I've compiled libinfinity 0.2.0 withou getting any errors and have all the dependencies for both gobby and libinfinity, used the usual for both:

```

./configure
make
sudo make install

```

I'm getting this error when running configure for gobby:

```

checking pkg-config is at least version 0.9.0... yes
checking for gobby... yes
checking for infinote... configure: error: Package requirements (libinfinity-1.0 >= 0.2 libinftext-1.0 >= 0.2 libinfgtk-1.0 >= 0.2 libinftextgtk-1.0 >= 0.2) were not met:

No package 'libinfinity-1.0' found
No package 'libinftext-1.0' found
No package 'libinfgtk-1.0' found
No package 'libinftextgtk-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables infinote_CFLAGS
and infinote_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I've did try setting infinote_LIBS to /bin where the libs seem to be installed:

```

movaxes@netbook:...es/Downloads/libinfinity-0.2.0$ ll /lib/libinf
libinfgtk-1.0.a             libinfgtk-1.0.so.0.0.0      libinfinity-1.0.so.0        libinftext-1.0.so           libinftextgtk-1.0.la        
libinfgtk-1.0.la            libinfinity-1.0.a           libinfinity-1.0.so.0.0.0    libinftext-1.0.so.0         libinftextgtk-1.0.so        
libinfgtk-1.0.so            libinfinity-1.0.la          libinftext-1.0.a            libinftext-1.0.so.0.0.0     libinftextgtk-1.0.so.0      
libinfgtk-1.0.so.0          libinfinity-1.0.so          libinftext-1.0.la           libinftextgtk-1.0.a         libinftextgtk-1.0.so.0.0.0

```

I'm not an expert at compiling and all that, any ideas? suggestions? solutions? Gobby 0.4.91 has no .deb for ubuntu yet.

Thanks :)

---

### Post by albinootje on 2009-04-25
> **movaxes said:**
> Gobby 0.4.91 has no .deb for ubuntu yet.

Is there really a big difference between Gobby 0.4.91 and the 0.4.9-2 that Jaunty provides ? Just wondering.

It is possible that you need to run "ldconfig -v" or first add /usr/local/lib/ to the library path.
Read this :
[http://ubuntuforums.org/showthread.php?t=100168](http://ubuntuforums.org/showthread.php?t=100168)
[http://www.openguru.com/2009/04/how-to-fix-shared-library-load-problem.html](http://www.openguru.com/2009/04/how-to-fix-shared-library-load-problem.html)

---

### Post by movaxes on 2009-04-25
> **albinootje said:**
> Is there really a big difference between Gobby 0.4.91 and the 0.4.9-2 that Jaunty provides ? Just wondering.

It is possible that you need to run "ldconfig -v" or first add /usr/local/lib/ to the library path.
Read this :
[http://ubuntuforums.org/showthread.php?t=100168](http://ubuntuforums.org/showthread.php?t=100168)
[http://www.openguru.com/2009/04/how-to-fix-shared-library-load-problem.html](http://www.openguru.com/2009/04/how-to-fix-shared-library-load-problem.html)

thanks for the quick answer :)
I'll read that :D

update: about the difference on versions, yep they did lot of changes that I need.

---

### Post by movaxes on 2009-04-25
> **movaxes said:**
> thanks for the quick answer :)
I'll read that :D

update: about the difference on versions, yep they did lot of changes that I need.

I added /usr/local/lib to ld.so.conf with:

```
sudo bash -c 'echo /usr/local/lib >> /etc/ld.so.conf ' && sudo ldconfig
```

runing ldconfig -v I get:

```

/usr/local/lib:
        libinfgtk-1.0.so.0 -> libinfgtk-1.0.so.0.0.0
        libinftext-0.3.so.0 -> libinftext-0.3.so.0.0.0
        libinfinity-0.3.so.0 -> libinfinity-0.3.so.0.0.0
        libinfgtk-0.3.so.0 -> libinfgtk-0.3.so.0.0.0
        libinfinity-1.0.so.0 -> libinfinity-1.0.so.0.0.0
        libinftextgtk-1.0.so.0 -> libinftextgtk-1.0.so.0.0.0
        libinftext-1.0.so.0 -> libinftext-1.0.so.0.0.0
        libinftextgtk-0.3.so.0 -> libinftextgtk-0.3.so.0.0.0
```

Runing ./configure I still get this error:

```

...
checking pkg-config is at least version 0.9.0... yes
checking for gobby... yes
checking for infinote... configure: error: Package requirements (libinfinity-1.0 >= 0.2 libinftext-1.0 >= 0.2 libinfgtk-1.0 >= 0.2 libinftextgtk-1.0 >= 0.2) were not met:

No package 'libinfinity-1.0' found
No package 'libinftext-1.0' found
No package 'libinfgtk-1.0' found
No package 'libinftextgtk-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables infinote_CFLAGS
and infinote_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Another suggestion? did I miss something? 

Thanks :)

---

### Post by oldos2er on 2009-04-25
"No package 'libinfinity-1.0' found 
No package 'libinftext-1.0' found
No package 'libinfgtk-1.0' found
No package 'libinftextgtk-1.0' found"

 Use Synaptic to search for and install the -dev versions of these packages.

---

### Post by albinootje on 2009-04-25
> **movaxes said:**
>  Another suggestion? did I miss something? 

Hmmm, I don't use Gobby myself, but I liked it when some friends showed it to me.
I'd like to make it compile but that'll take some time, .. hang on ;-)

And.. from the download page :
> 
You will have to build Gobby 0.4.91 from source until your distribution ships it. However, since the underlying library, libinfinity is not yet stable, it might take some time until it does.


---

### Post by movaxes on 2009-04-25
You guys rule :D I'm trying to compile myself without success yet.

---

### Post by albinootje on 2009-04-25
Okay, I've started compiling after making the preparations (perhaps  more about that later).
This shows some interesting remark :
```

cat config.log |grep infin

```

Resulting in :
> 
Package libinfinity-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libinfinity-1.0.pc'
No package 'libinfinity-1.0' found

So the configure setup might be flaky or picky, or those libraries need a special location, or a better prefix for configure to handle.

---

### Post by albinootje on 2009-04-25
Found a work-around.
```

ls -latr /usr/lib/pkgconfig/
-rw-r--r--   1 root root   323 Apr 26 03:08 libinftextgtk-0.3.pc
-rw-r--r--   1 root root   271 Apr 26 03:08 libinftext-0.3.pc
-rw-r--r--   1 root root   311 Apr 26 03:08 libinfinity-0.3.pc
-rw-r--r--   1 root root   290 Apr 26 03:08 libinfgtk-0.3.pc
lrwxrwxrwx   1 root root    18 Apr 26 03:13 libinfinity-1.0.pc -> libinfinity-0.3.pc
lrwxrwxrwx   1 root root    16 Apr 26 03:14 libinfgtk-1.0.pc -> libinfgtk-0.3.pc
lrwxrwxrwx   1 root root    20 Apr 26 03:15 libinftextgtk-1.0.pc -> libinftextgtk-0.3.pc
lrwxrwxrwx   1 root root    17 Apr 26 03:15 libinftext-1.0.pc -> libinftext-0.3.pc

```
I got some errors while running "sudo make install" for libinfinity, so I used "sudo make -i install" instead.
After that I've copied the content of /usr/local/lib/pkgconfig/ to /usr/lib/pkgconfig/ and added the symbolic links you can see in the above output 
For example : ln -s libinfinity-0.3.pc libinfinity-1.0.pc

After that configure didn't complain anymore, and compiling of gobby started. GL! :)

---

### Post by movaxes on 2009-04-25
> **albinootje said:**
> Found a work-around.
```

ls -latr /usr/lib/pkgconfig/
-rw-r--r--   1 root root   323 Apr 26 03:08 libinftextgtk-0.3.pc
-rw-r--r--   1 root root   271 Apr 26 03:08 libinftext-0.3.pc
-rw-r--r--   1 root root   311 Apr 26 03:08 libinfinity-0.3.pc
-rw-r--r--   1 root root   290 Apr 26 03:08 libinfgtk-0.3.pc
lrwxrwxrwx   1 root root    18 Apr 26 03:13 libinfinity-1.0.pc -> libinfinity-0.3.pc
lrwxrwxrwx   1 root root    16 Apr 26 03:14 libinfgtk-1.0.pc -> libinfgtk-0.3.pc
lrwxrwxrwx   1 root root    20 Apr 26 03:15 libinftextgtk-1.0.pc -> libinftextgtk-0.3.pc
lrwxrwxrwx   1 root root    17 Apr 26 03:15 libinftext-1.0.pc -> libinftext-0.3.pc

```
I got some errors while running "sudo make install" for libinfinity, so I used "sudo make -i install" instead.
After that I've copied the content of /usr/local/lib/pkgconfig/ to /usr/lib/pkgconfig/ and added the symbolic links you can see in the above output 
For example : ln -s libinfinity-0.3.pc libinfinity-1.0.pc

After that configure didn't complain anymore, and compiling of gobby started. GL! :)

You rock albinootje! :D I'll try that workaround, thanks a lot, I'll let you know how it goes :)

---

### Post by movaxes on 2009-04-25
Thanks albinootje! it worked :) running make install with -i did it for me on libinfinity 0.2.0, also did the links. Now gobby is installed and running, thanks! :D

---

### Post by Jesdisciple on 2010-09-17
With guidance from one PovAddict in #infinote IRC, I was able to get 0.4.93 running on 9.10.  I believe this sums up the steps that actually worked, although I haven't tested it.  (Note that unauthenticated packages are accepted, because apparently Ubuntu packages don't use certificates; neither dget would work without that flag.)```
sudo apt-get install devscripts
dget https://launchpad.net/ubuntu/lucid/+source/libinfinity/0.4.1-1/+files/libinfinity_0.4.1-1.dsc --allow-unauthorized
cd libinfinity-0.4.1
./configure
sudo make
sudo make install
cd ..
dget http://archive.ubuntu.com/ubuntu/pool/universe/g/gobby-infinote/gobby-infinote_0.4.93-1.dsc --allow-unauthorized
cd gobby-infinote-0.4.93
./configure
sudo make
sudo make install
```

---

