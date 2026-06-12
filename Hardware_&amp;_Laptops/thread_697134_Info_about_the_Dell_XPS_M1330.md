---
title: "Info about the Dell XPS M1330"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by stlcoptony on 2008-02-14
I wanted to start a thread concerning the XPS M1330 with intel graphics. I have yet to find a good solution anywhere, but I have gotten Compiz-fusion up and running while playing flash videos with no crash. I went to this site [here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61"), and added this to my /etc/apt/sources.list
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe 

Then the site has you run:
> 
sudo apt-get update
 sudo apt-get install linux-restricted-modules-2.6.24-3-generic linux-image-2.6.24-3-generic linux-ubuntu-modules-2.6.24-3-generic

I believe this updates the kernel to the one from hardy. Compiz will start to work but it's not pretty. I get jagged edges when moving windows whether or not wobbly windows are on. I also do not have smooth transitions when max/minimizing the windows. 

I intend this to be a linux only laptop and am willing to test out fixes for this (as long as there is no danger to the hardware, I'm good....)

thanks,
tony

---

### Post by stlcoptony on 2008-02-15
anyone have any ideas? I'm willing to try them out (and re-install if something breaks)

thanks

---

