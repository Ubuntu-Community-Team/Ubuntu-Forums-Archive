---
title: "Cannot start X"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by myha on 2005-08-02
Hi!

I'm new in Linux, I installed it like a week ago and I like it... But im a complete noob so its hard for me to learn smth completely new, but I try... And do stupid things when trying it...  :)

Now my problem: I have a HP omnibook 6100 laptop with ATI radeon M6 mobility video card. With default drivers I got very bad results (2Fps) so I decided to install [XFree86](http://www.xfree86.org/) drivers....
I followed the instructions of installer, restarted X and and can't start it any more...  :(
I get an error 

"Fatal server error: no screens found"
Fatal IO error 104

Can anyone tell me what to do next? Is it all finished and I have to reinstall Ubuntu? Or is there any way to fix this?

Thanks, 
Miha

---

### Post by amohanty on 2005-08-02
ok first off.. hoary uses xorg so you probably want to drop into recovery mode and remove xfree86 and reinstall the xorg.

Also for ATI try the fglrx drivers that are in the repos.

AM

---

### Post by myha on 2005-08-03
Hi!

Thanks for your reply...

XFree86 was making backup of every file it edited so I got them back and replaced them with those newly generated...

But I think that when i startx it tries to use XFree86-4 instead of xorg.conf... How can I tell x server to run xorg.conf instead of XFree86-4?

I think i know how to reinstall the xorg (sudo dpkg-reconfigure xserver-xorg  ??), but I dont know how to remove the XFree86...

Sorry if I talk nonsence but like I said I'm new on Linux so be patient...  :)


Thanks, Miha

---

### Post by amohanty on 2005-08-03
Why do you need to use startx? 
By default Ubuntu loads into GUI mode.
Did you install XFree86 from source or apt-get/synaptic?

AM

---

### Post by myha on 2005-08-04
Hi!

I installed it from source on XFree86 homepage.... I managed to get insto desktop (I replaced XFree86-4 with xorg.conf) and it worked, but I had sone problems with fonts...
But it doesn't matter anymore, cause I decided to format and reinstall Ubuntu and try to install fglrx drivers from HOW-TO on this forum...

Thank you very much for your time and help,
regards, Miha

---

