---
title: "Help on performance tuning."
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by billingsworld on 2007-01-20
Hi,

I am not sure if I am ready to gravitate from the Newb forums just yet, but, I thought this kind of question better to be asked in the "adult swimming pool."

In short, I have gone cold turkey from Windows on my home PC.  I have installed Edgy, everything works, including printing.  I have installed XMMS to play mp3 files and have installed some themes.

Today, I was listening to tunes, checking up on my threads and noticed that while I was visting [www.blogger.com](www.blogger.com), the browser was lagging hard.  I think it has something to do with the flash component in the page - I don't really know.

Is there a way to print out or view what hardware my system has detected and what drivers/packages are being used with said hardware?  I was hoping that if I could get that list and post it, maybe one of you uber ubuntu guru's could take a look and see if I have screwed anything up.

The system itself is pretty snappy, but not as fast as I thought it might be (had always heard Linux can make old hardware sing again - maybe that doesn't equal current hardware reaching Mach 1?)

I can deal with GUI and terminal commands, if you could point me in the right direction I would appreciate it.


Thanks.

---

### Post by studiesrule on 2007-01-20
Try installing the non-opensource version of flash if you already don't have it:
> 
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin


You require the backports for this.

---

### Post by billingsworld on 2007-01-20
> **studiesrule said:**
> Try installing the non-opensource version of flash if you already don't have it:


You require the backports for this.


Hi,

Thanks for your post, what are backports?  Are these special repositories?


Thanks.

---

### Post by bogoliubov on 2007-01-20
Yep, they'are kind of special repositories. 

I don't know how much you know, but add these lines to your /etc/apt/sources.list file:

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

This can also be done through Synaptic.

If you have a look at [www.ubuntuguide.org](www.ubuntuguide.org) , you'll see other repositories as well, that might be interesting.

Anyhow, when you have changed the file, update the packages. In a terminal, you do:
sudo apt-get update
sudo apt-get upgrade
This can also be done in Synaptic...

---

