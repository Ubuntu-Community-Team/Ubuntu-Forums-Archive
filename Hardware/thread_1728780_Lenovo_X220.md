---
title: "Lenovo X220"
date: 2011-04-14
forum: Hardware
---

### Post by manybodycpa on 2011-04-14
Dear all,

I am planning to buy the new X220 notebook. Since the first models should have been shipped by now, can anyone comment on compatibility with Ubuntu?
Google did not come up with any relevant hits, except for a trackpad issue.

Also, I would appreciate links to any reviews concerning linux on this machine.

Thanks,

Martin

---

### Post by cdgossett on 2011-04-14
As far as I know, Lenovo isn't selling the x220 yet.  The Thinkpad [website]("http://shop.lenovo.com/us/products/professional-grade/thinkpad/x-series/x220/index.html") simply says it is coming in April 2011. 

The [datasheet]("http://shop.lenovo.com/us/ww/pdf/x220_datasheet.pdf") from Lenovo says that the x220 is certified for Redhat, Novell and Ubuntu for what that is worth.

Chris

---

### Post by manybodycpa on 2011-04-14
Thanks Chris. My assumption was based on a German website, which accepts orders and was quoting a shipping time of seven days about three weeks ago. I just checked, it still says seven days :-(.

> **cdgossett said:**
> As far as I know, Lenovo isn't selling the x220 yet.  The Thinkpad [website]("http://shop.lenovo.com/us/products/professional-grade/thinkpad/x-series/x220/index.html") simply says it is coming in April 2011. 



---

### Post by williumbillium on 2011-04-15
I'm also considering buying an x220.

Looking at launchpad there are several bugs that Canonical devs have already fixed which supports the fact that it's certified:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746259)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746652)

According to the [new product showcase]("http://shop.lenovo.com/us/products/new-products/?menu-id=learn&current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=96EBC6A8C8EC47A59E95B3D5E300F333#X220") (scroll up slightly) on the Lenovo site, the release date is April 19th, so hopefully only a few more days to wait for some real world feedback.

---

### Post by blakdogg on 2011-04-20
NotebookReview links to a pdf that claims to be thinkpad x220 specs, and the pdf claims that the machine is Ubuntu certified.

[http://forum.notebookreview.com/lenovo-ibm/559762-thinkpad-x220-specs-revealed.html](http://forum.notebookreview.com/lenovo-ibm/559762-thinkpad-x220-specs-revealed.html)

---

### Post by manybodycpa on 2011-05-03
There is an extensive discussion concerning the X220 (including feedback from people who have already got one).

[http://forum.notebookreview.com/lenovo-ibm/568231-thinkpad-x220-info-ordering-shipping-thread.html](http://forum.notebookreview.com/lenovo-ibm/568231-thinkpad-x220-info-ordering-shipping-thread.html)

PS: I placed my order yesterday.

---

### Post by williumbillium on 2011-06-08
For anyone interested in this laptop, I've created a page on community documentation site:

[https://help.ubuntu.com/community/X220](https://help.ubuntu.com/community/X220)

Would be great for others to add their experiences there too.  I'm particularly interested in improving the support for the clickpad; it's a bit lacking at the moment.

In general this laptop works very well out of the box though.

---

### Post by substanceneil on 2011-06-11
It is unclear from the Ubuntu community documentation whether the x86 or amd_64 version has been testing / certified.  Can you advise which is the better version to install?

---

### Post by williumbillium on 2011-06-11
Good question!  I've only installed 64 bit so I can't say which has better support on this machine but I can say that the various statuses are valid for 64 bit.

I've updated the wiki page.

---

### Post by linuxhobox on 2011-06-12
> **williumbillium said:**
> For anyone interested in this laptop, I've created a page on community documentation site:

[https://help.ubuntu.com/community/X220](https://help.ubuntu.com/community/X220)

Would be great for others to add their experiences there too.  I'm particularly interested in improving the support for the clickpad; it's a bit lacking at the moment.

In general this laptop works very well out of the box though.

I went ahead and added:

[LIST]
[*]Intel Centrino Ultimate-N 6300 = works out of box
[*]display port = works out of box w/ hdmi adapter
[*]CPU throttle (I7) = works out of box
[*]usb3 = works out of box but no usb3 booting
[*]fingerprint reader = works w/ fingerprint gui and libs
[/LIST]

---

### Post by TallyL on 2011-07-18
It should be noted that on my i7 X220 at least, a lack of support for the Sandy Bridge processor leads to lag in OpenGL that is noticeable especially when using the Unity Dash. It has also been linked to the computer locking up but I can't find the link at the moment.

Regardless, the lag at least is resolved by updating the kernel. I updated to Oneiric's 3.0 RC7 and all lag has disappeared.

Has anyone found a way to make two-finger click and drag usable yet? I couldn't install the xf86-input-mtrack drivers successfully, which supposedly have usable two-finger click and drag in multitouch touchpads.

---

### Post by manybodycpa on 2011-07-18
I can confirm that the graphics lag is also gone under gnome after switching
to the 3.0 kernel.

---

### Post by jknotzke on 2011-08-11
I may have a slightly off-topic question..

  I own a LED Apple Cinema Display which uses a mini displayport. I see that the x220 has a displayport.

  Would anyone happen to know if I can use an adapter that converts displayport from the x220 to a mini displayport (male) on the Cinema Display and (most importantly) if the latest Ubuntu 11.04, supports this setup ?

   Thanks

   J

---

