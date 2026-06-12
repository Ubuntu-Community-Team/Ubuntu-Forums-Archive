---
title: "how to install wireless driver compaq cq40-319tu ubuntu 9.10 karmic"
date: 2010-01-10
forum: Hardware
---

### Post by gabak on 2010-01-10
if you have a laptop compaq cq40-319tu then if you have to install karmic 9.10 do this , after this do all the updates then wireless will work well.


 Originally Posted by Ayuthia  View Post
Check and see if you have the following directory:
Code:

ls /var/lib/dkms/bcmwl

If you do and it returns something like
Code:

5.10.91.9+bdcom

Try the following:
Code:

sudo dkms build -m bcmwl -v 5.10.91.9+bdcom

If that is successful try:
Code:

sudo dkms install -m bcmwl -v 5.10.91.9+bdcom

The first dkms command will build the Broadcom kernel module and create the wl.ko. The second command will install it.

Hope that helps.

Well it worked!!!!

But I did it a different way. I downloaded

dpkg-dev (and some dependencies for it)

[http://packages.ubuntu.com/karmic/dpkg-dev](http://packages.ubuntu.com/karmic/dpkg-dev)

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)

And then I ran

Quote:
sudo dpkg-reconfigure bcmwl-kernel-source
And Then

Quote:
sudo modprobe -r b43 ssb wl
sudo modprobe wl
It finally worked.

Thanks for all your help.

---

