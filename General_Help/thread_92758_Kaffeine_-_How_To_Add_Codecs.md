---
title: "Kaffeine - How To Add Codecs?"
date: 2005-11-20
forum: General Help
---

### Post by config.sys on 2005-11-20
Hi all. I just upgraded to Kubuntu 5.10 and I'm am having issues w/ Kaffeine. I had everything working fine w/ Kubuntu 5.04 and I'm beginning to regret the upgrade. I have been a linux use for almost a year now and prefer it to Windows.

I have a fresh install of Kubuntu and have installed libdvdcss and all the dvdread libraries. However when i try to play a DVD ige the message -  

There were no decoders found to handle the stream, you might need to install the corresponding plugins. 

How do I install the codecs for the gstreamer engine and how do I change the engine to xine?

I also tried to compile a fresh install of xine and after having ./configure find the x11 files sucessfully, it bombs out on make. 

Other than the multimedia issues - I really like 5.1!

---

### Post by config.sys on 2005-11-20
Problem Solved!

I added the new repositories as outlined here:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

The above is in aysiu's sig file. Thanks!

Then I took ownership of ksycoca file found in /var/tmp/kdecache-"user". The issue is outlined here.

[http://kubuntuforums.net/index.php?topic=575.0](http://kubuntuforums.net/index.php?topic=575.0)

After a reboot kaffeine recognizes both gstreamer and xine - WooHoo!

The wiki on restricted formats helped out too:
[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29)



Now it crashes when on exit, but no big deal.

BTW the ksycoca issue was also causing issues with compiling new software. I just compiled the upgrade to gwenview 1.3.1 with no issues. I hope this post helps someone else out.

---

### Post by config.sys on 2005-11-20
Just took care of Kaffeine crashing upon exit, I compiled and upgraded to Kaffeine 7.1. No issues at all now.

Lots of info on these forums and the wiki. Thanks to all that contribute.

---

