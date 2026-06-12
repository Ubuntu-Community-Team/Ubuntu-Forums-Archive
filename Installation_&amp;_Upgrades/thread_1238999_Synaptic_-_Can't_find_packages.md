---
title: "Synaptic - Can't find packages"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by davomate on 2009-08-13
HI,

I had Win XP on my Toshiba Satellite, and then I installed Ubuntu 9.04 on it as well,
after resizing the XP partition to make room. All was good. Then I unmounted the XP partition, removed it, and re-installed Ubuntu 9.04 to use the entire hard disk.

I partitioned it as - 1GB (boot), 2GB (SWAP), and the rest of the 100GB as Ext3.

I got the install finished, let it download and install all the updates.

The only problem is the Snaptic Package Manager. Currently version 0.62.5.

Under 'Settings --> Repositories' I have the first four ticket in the 'Ubuntu Software' tab.
And 'Server from Australia' as the download from.

In the third party software tab, I have:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty (partner)
[http://archive.canonical.com/ubuntu/jaunty](http://archive.canonical.com/ubuntu/jaunty) (partner(source code))
[http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty (main)
[http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty (main (source code))

So for example, when I type Evolution into the quick search, it will show me all the packages related that 'are already installed'.

But when I search for something else, e.g. Kismet, Wireshark or anything, there is not results.

How can I get this Synaptic Package Manager going please?

I do not want to go back to Windows.

Thankyou

---

### Post by mikewhatever on 2009-08-13
It looks like you are searching through the installed packages only. Make sure to select ALL in the left panel, topmost option.

---

### Post by davomate on 2009-08-13
I have the 'All' selected at the top. But the quick search won't work properly.

The actual packages are now listed if I scroll down and find them.

I think that fixed when I selected 'Origin' in the bottom left options in Synaptic,

and hit reload on a few of the servers listed.

---

### Post by mikewhatever on 2009-08-13
If Origin is selected, you actually need to select the repository of origin, the same is true about Sections. On the other hand if Status is selected, the matching packages show as soon as the first three letters are typed.

---

