---
title: "Problems with Intel Graphics, AND issue with s-video out."
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by dapaintballer331 on 2008-03-22
I'm now stuck at "Running Boot Scripts...", and here is how I got there.

I wanted s-video out, to my 72" widescreen TV. Before anything, I backed up xorg.conf, which I'm pretty sure has never been used to change my display properties (because those settings didn't match my default resolution).

I plugged in the cord, and hit Fn+F2. It worked!... in 800x600 resolution.

I changed my monitor so the default was "Screen 2", and changed the video driver from "Plug-n-play" to "Generic Widescreen 1600x1200". I hit apply.

Here is when it went bad. I was first told to log off all users. I did that, and then hit Control-Alt-Backspace. 

Now guess where I'm stuck?

"Running Boot Scripts..."

Any ideas please? :)

---

### Post by dapaintballer331 on 2008-03-22
I restored my old xorg.conf using a live cd.

My computer still hangs at "Running local boot scripts (/etc/rc.local)"

---

