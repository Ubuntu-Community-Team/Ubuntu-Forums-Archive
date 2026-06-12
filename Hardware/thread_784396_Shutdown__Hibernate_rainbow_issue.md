---
title: "Shutdown / Hibernate rainbow issue"
date: 2008-05-06
forum: Hardware
---

### Post by juliohm on 2008-05-06
First of all,

I apologize for the strange title of this post, but I've searched all around the net and couldn't find anything related to the problem that I am having.

It's not critical (as far as I can see anyway), and given my limited English vocabulary those were the only words I could find to describe the issue.

As it turns out, a picture is worth a thousand words. So here it goes. This is what happens to my HP DV6445us laptop when I shutdown or hibernate Ubuntu 8.04.

[IMG]http://juliohm.googlepages.com/IMG_0855.jpg[/IMG]

Anyone seen this before? How do I fix this?

It doesn't seem to be critical. The laptop shutdowns/hibernates normally... it just happens that the screen resolution gets messed up during the process.

Could this possibly damage the screen if it continues like this over time?

---

### Post by juliohm on 2008-05-06
Ok, I think it's fixed now.

Apparently, the screen resolution wasn't quite well detected during installation. All I had to do was this

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
md5sum /etc/X11/xorg.conf |sudo tee /var/lib/x11/xorg.conf.md5sum
sudo dpkg-reconfigure xserver-xorg
```

It's a piece of command lines that I found [here]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

My laptop was running at a 50Hz resolution. After reconfiguring xorg, it now recognizes it at 60Hz. All works well now.

Cheers!

---

