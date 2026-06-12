---
title: "xserver-xorg-core downgrade"
date: 2008-11-02
forum: Hardware
---

### Post by QIII on 2008-11-02
I have an old IBM Thinkpad iSeries 1200 that I used to run xubuntu Feisty on with no problems.  I just installed xubuntu 8.10.  I knew going in that the latest xserver would not play well with the (unknown) graphics chipset, but I figured I could downgrade to the last known xserver that worked in Fiesty:  xserver-xorg-core=2:1.2.0-3ubuntu8.

So, I installed xubuntu 8.10 and found that I got the dreaded blank screen I expected.

Since I could get to the command line, I thought I'd just be able to install the earlier version.

I've tried apt-get install to get the old version, but when I do that, I get a message that "version '2:1.2.0-3ubuntu8' for 'xserver-xorg-core' was not found".

OK.

So I tried wget using a url to where I found the old package, but when I try to get the .deb from a mirror site I can navigate to and find the package, I get "unable to resolve host address . . ."

This is an old laptop I use for times when I don't want to beat up a newer one, and I'd like to have 8.10 on it.  I'd rather not go back to Feisty, since I want the newer versions of OpenOffice and Emacs.

Can anyone lend a hand?

---

