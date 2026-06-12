---
title: "No medibuntu-keyring in Synaptic in Jaunty?"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by mtheultimate on 2009-06-08
I was trying to follow the instructions in this tutorial:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

But when I have a problem at this part:
"When Synaptic Package Manager opens, click on **Search** at the top-right corner and when the *Find* dialogue box appears, search for the word *medibuntu* and then click **Search**. When you find the *medibuntu-keyring* package in the results..."

There is no result for "medibuntu-keyring" in Synaptic. I see a bunch of 
"keyring" results but no "medibuntu" ones. 

Thanks!

---

### Post by kostkon on 2009-06-08
Try using the full search in *Synaptic*, not the quick-search. Nevertheless, try opening a terminal and giving:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
to install the package that will add the key for you.

For more info, check the [*Medibuntu* how-to page at the ubuntu documentation site]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by mtheultimate on 2009-06-08
Thank you. The terminal command worked great.

I hope I was supposed to answer yes to this message:

WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y

> Try using the full search in *Synaptic*, not the quick-search.

Wow, I must have spaced. I thought that search icon beside the text box was like an "enter" button.

---

### Post by kostkon on 2009-06-08
> **mtheultimate said:**
> Thank you. The terminal command worked great.

I hope I was supposed to answer yes to this message:

WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y
Yes, no worry ;)

---

