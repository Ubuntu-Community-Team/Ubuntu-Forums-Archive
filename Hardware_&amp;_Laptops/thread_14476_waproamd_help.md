---
title: "waproamd help"
date: 2005-02-07
forum: Hardware &amp; Laptops
---

### Post by fu_fish on 2005-02-07
I recently switched from gentoo to ubuntu on my laptop.  I've been really please with ubuntu, but there's one last thing I've not been able to figure out how to do on ubuntu.  I frequently roam between two hidden wireless networks (with dozens or even hundreds of APs), which I'll call foo and bar for this post.  On gentoo I could set in my /etc/conf.d/wireless file a preferred_aps variable, which the networking scripts would use w/ waproamd to scan for these networks if no other networks were found.  Here's an example of that line:

preferred_aps=("foo" "bar")

Now, I'd like to recreate this behavior in ubuntu, but haven't been able to figure this out.  I'd use the mac scripts, but that's highly impracticle, since there are so many APs that could be found and since my wireless driver doesn't support scanning.  Does anyone know a way to set a list of preferred essids for waproamd in ubuntu?

Thanks in advance.

---

