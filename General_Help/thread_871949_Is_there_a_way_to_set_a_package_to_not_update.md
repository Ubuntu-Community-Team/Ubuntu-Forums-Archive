---
title: "Is there a way to set a package to not update?"
date: 2008-07-27
forum: General Help
---

### Post by Corfy on 2008-07-27
Is there a way to set a package to not update?

I have a website that I need to visit weekly. For some strange and unknown reason, it doesn't work with Firefox 3, but it worked fine with Firefox 2. So I ended up installing SeaMonkey to work with this one site. But I'm worried that SeaMonkey will update at some point to more closely match Firefox 3, and I would like to keep it from updating, if at all possible (at least until the site works with Firefox 3).

---

### Post by Ryadt on 2008-07-27
Firefox2 is still in synaptic if you want to install it.

---

### Post by cariboo on 2008-07-27
To pin an application so that it doesn't update, Go to System-->Administration-->Synaptic Package Manager, search for the application you don't want to update, highlight the application, then click Packages on the Menu bar and select Lock Version. To see if it has worked, click the status button and it will show as pinned.

---

### Post by Corfy on 2008-07-27
Thanks. I figured that there was probably an easy way to do it, I just couldn't find it.

---

### Post by nikgare on 2008-07-27
Out of interest, which website is it?

---

### Post by Corfy on 2008-07-27
[http://www.sermonplayer.com](http://www.sermonplayer.com)

I upload an MP3 of our church's sermon every week. It works fine up to the point where I have to upload the file, and then I don't have the interface to upload it through (it is a web-based upload). I don't know why it doesn't work with Firefox 3, but I have confirmed that it doesn't work with FF3 in both Ubuntu (or rather, Kubuntu) and Windows, but it works fine with FF2 in both. And it works fine with SeaMonkey.

---

### Post by Corfy on 2008-08-25
I found out why the site isn't working with my Firefox 3.

There is something about the Flashblock extension that the site doesn't like. If I turn off Flashblock, then the site works fine. I previously had told Flashblock to not block anything from that site, but that didn't seem to do it.

So the problem isn't with Firefox, it is with an extension. I didn't think to try that, although I probably should have.

---

