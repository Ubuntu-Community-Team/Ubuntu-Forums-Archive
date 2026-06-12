---
title: "Lucid Laptop Suspend - Toshiba U405D-S2852"
date: 2010-05-12
forum: Hardware
---

### Post by jasonkotenko on 2010-05-12
Hi all,

I just wanted to post this here so others can find it if they need it.  I just went through the process of troubleshooting the suspend on lid close functionality of my Toshiba U405D-S2852 laptop.

I posted the results of this troubleshooting process here: 
[http://jasonkotenko.com/posts/toshiba-laptop-suspend-lucid/](http://jasonkotenko.com/posts/toshiba-laptop-suspend-lucid/)

Please feel free to leave any comments you have on that post.  Thanks.

---

### Post by Zer0Nin3r on 2010-07-19
Thank you for posting this fix!  This works **almost** flawlessly with the exception to Gnome's power menu, which you stated in your blog.

BTW I have the same laptop as you.

I didn't have any problems with suspend in the 9.10 Karmic release; it wasn't until I upgraded I started having problems.  Now I can have my ATI drivers in use as well as being able to suspend.

I had to use the following variation:

```
sudo s2ram -f -a 2
```

**Update**

I notice after certain updates, you have to reconfigure the system in order for the fix to work.  I am finding that the previous variation isn't working for me now and the following is:

```
sudo s2ram -f -a 1
```


**Update**
Actually both work...

---

