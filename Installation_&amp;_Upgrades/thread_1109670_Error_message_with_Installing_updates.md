---
title: "Error message with Installing updates"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by Usheen on 2009-03-29
Hello Ubuntu people,

I recently downloaded recommended updates to 8.10 Intrepid.

Wish I hadn't bothered - it was running smoothly before, but now it's choking up and crashing with every click I make!

Anyone recognise the following error messages?

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

The above one popped up when I downloaded upgrades.
 My laptop hasn't been the same since then. First it wouldn't play vids, then the internet slowed, now I'm haveing to 'force quit' my way from application to application to move anywhere...

The following error message sometimes comes up when I right-click the mouse:

> 
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:()
9:CM_initMenu([object XULElement],[object XULElement])
10:nsContextMenu([object XULElement],[object XULElement])
11:onpopupshowing([object MouseEvent])

If any one can shed light on these, much appreciated. My laptop's running so slowly now and I've no idea how to go about discovering the flaw, nevermind resolving the issue.

Thanx,

Usheen

---

### Post by cariboo on 2009-03-29
It looks like  your updates  didn't complete, to fix your Medibuntu key problem go [here]("http://help.ubuntu.com/community/Medibuntu") and scroll down to the add GPG Key section and follow the instructions. To make sure your updates have completed open an Application-->Acccessories-->Terminal and type:

```
sudo apt-get install -f
```

then in the same terminal type:

```
sudo apt-get update && sudo  apt-get dist-upgrade
```

Jim

---

### Post by Usheen on 2009-03-29
Thanks Jim,

I followed your instructions. Went without a hitch. I also checked the Synaptic Package Manager - nothing seems to be broken. Things are definitely flowing better for me on firefox. Still not back to regular speed though. And the comp still seizes up when I go near a page with video or flash advertising on it!

When I started up my laptop this morning I received a pop-up message saying that "proprietary drivers were needed for it to work properly." So I agreed to activate the recommended NVIDIA accelerated graphics drive (version 180).

This obviously relates to the problems I've been having... any suggestions re what I should do next?!

Thanx

Usheen

---

### Post by rob2nd9th on 2009-04-01
Thanks mine just did this.

---

### Post by spike_naples on 2009-04-01
mine too.. thanks a bunch.

---

