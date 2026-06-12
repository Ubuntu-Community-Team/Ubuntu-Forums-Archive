---
title: "libGL error"
date: 2012-11-01
forum: Hardware
---

### Post by brazilbean on 2012-11-01
While running MATLAB 2012a and trying to generate a large figure, I get the following error printed to my terminal:

libGL error: failed to load driver: r600
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.

and then MATLAB crashes. 

I'm running 12.10 Gnome. Any ideas on how to solve this?

---

### Post by brazilbean on 2012-11-01
Running with the LIBGL_DEBUG=verbose, MATLAB printed a segmentation fault stack trace: see below for the last two lines:

[ 43] 0x00007f0a8b454e9a              /lib/x86_64-linux-gnu/libpthread.so.0+00032410

[ 44] 0x00007f0a8b181cbd                    /lib/x86_64-linux-gnu/libc.so.6+00998589 clone+000109

When I first installed 12.10, MATLAB was starting with an error saying it could not find libc.so.6. I followed some instructions (see [here]("http://www.emmalzhang.com/robotTech/2012/05/10/matlab-starting-error-in-ubuntu-12-04-libc-so-6-not-found/")) to fix this warning (essentially providing a symbolic link /lib/x86_64-linux-gnu/libc.so.6 -> libc-2.15.so).

Perhaps this information helps?

---

### Post by silhusk on 2012-11-11
By doing what matlab suggests (enable debugging) we find out the actual problem

> libGL error: dlopen /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so failed (/usr/local/MATLAB/R2011b/bin/glnxa64/../../sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/x86_64-linux-gnu/libLLVM-3.1.so.1))

For me it worked to change the libstdc++ version used by matlab, as follows

```
ln -sf /usr/lib/x86_64-linux-gnu/libstdc++.so.6 /usr/local/MATLAB/R2011b/sys/os/glnxa64/libstdc++.so.6
```

The solution was suggested by this post: [http://judsonsnotes.com/notes/index.php?option=com_content&view=article&id=611:matlab-running-external-programs&catid=57:programming&Itemid=81](http://judsonsnotes.com/notes/index.php?option=com_content&view=article&id=611:matlab-running-external-programs&catid=57:programming&Itemid=81)

---

### Post by lopcaf on 2013-02-01
> **brazilbean said:**
> While running MATLAB 2012a and trying to generate a large figure, I get the following error printed to my terminal:

libGL error: failed to load driver: r600
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.

and then MATLAB crashes. 

I'm running 12.10 Gnome. Any ideas on how to solve this?

Hi brazilbean, 

I was suggested to create a figure with the following command

f=figure;set(f,'renderer','zbuffer')

and then I could make 3D plots, without getting the errors that you described.

Hope it helps!


EDIT: There is a package in the (K)ubuntu repos called matlab-support, this might well correct the problem. It did for me :)

---

### Post by brazilbean on 2013-05-30
Mathworks suggested running the following command before trying to plot (which I have saved in my startup.m file):

```
opengl software
```

This has fixed the problem.

---

