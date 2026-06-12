---
title: "dual monitor on lucid, problem with xorg"
date: 2012-04-28
forum: Hardware
---

### Post by atreyu82 on 2012-04-28
morning everybody, this is my first post, thank you for welcoming me, I hope I can be useful for the community for the time to come.

I hope my post is not misplaced; my problem is that attempting to set up a dual monitor on my ubuntu 10.04, ati radeon x1400 (kms disabled), I found out that there is no /etc/X11/xorg.conf due to the automatic load of the related configuration which no longer need such file.
I read then that it was still possible to create that file and it would have worked anyway

I have to admit I was concerned over the relation betwen the default set up automatically load and the file to be created...but after quite a lot of search I didn't find any warning about some possible conflict between them so I created /etc/X11/xorg.conf putting in the configuaration reportedly good for a second monitor to be used.

After creating that file, I restarted with sudo restart gdm....then I got  black screen where I could write commands but with no way to run them. Therefore, the only way to get out it's been to reset it with alt+ctrl+canc...

After restarting the computer, I have it stuck at the Ubuntu splash screen...and it doesn't go any further, each time I start it.

Now, besides the content of the file I created, my question is: how could I get the default setting working again? would it be enough just to delete /etc/X11/xorg.conf I created that apparently took over? 

I am a bit scared to mess it up even worse, I have some important work trapped in the computer...

thank you.

---

