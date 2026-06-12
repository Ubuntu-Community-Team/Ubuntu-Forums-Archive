---
title: "Which Router ?"
date: 2013-06-04
forum: Hardware
---

### Post by Y^2om&amp;#7sgP on 2013-06-04
Hi All

Can someone advise please (hope this is the correct board in the forum)
Currently using Xubuntu 12.04
I recently had a Netgear DGN834v5 router with shares setup on a USB drive hanging off the back of my desktop PC, using Nautilus-share, accessing via wireless on my laptop
Router died and the new one is a Netgear DGN2200 (supplied by ISP) which doesn't support Linux shares (just won't see them at all, even trying smb://ip_address) unable to even see each machine.
So...am now looking to get a new router
Now down to the shorter version of the question.
Can anyone recommend a router which works well, including shares with Linux please? I don't mind getting my hands a little dirty and installing samba if needed, just don't want to buy a new router and have the same problems
(Only way I can see the shares at the moment is by installing Windows on both machines, so Netgear seem to think that the problem is solved !!! :mad:)

Thanks all :D

---

### Post by CharlesA on 2013-06-04
The router has nothing to do with the accessibility of shares on your network unless you are using it to share files via USB.

Was the drive connected to the desktop and doing the sharing from the desktop itself, or what?

---

### Post by Y^2om&amp;#7sgP on 2013-06-04
Thanks for the quick response CharlesA
USB drive was attached to the desktop computer.  Shares setup via Nautilius-share.
Accessed from the laptop by going into either Nautilus or Thunar and then through the network option.
Since new router, can only see Video or Windows Network, and can't open either of them.
Am I doing something really dumb ? :(

---

### Post by CharlesA on 2013-06-04
Run this on the machine serving the files and on the machine you are trying to access them from:

```
smbtree
```

---

### Post by Y^2om&amp;#7sgP on 2013-06-05
Just prompts for my password the returns to a prompt??
What should happen ?

---

### Post by Y^2om&amp;#7sgP on 2013-06-05
Just looking again, nautilus seems to loose the shares I've set?
Now trying to do this again I get the error message
'net usershare' returned error 255: net usershare add: failed to add share ukulele. Error was Operation not permitted
Worked before though.  What have I done wrong???

---

### Post by CharlesA on 2013-06-05
> **hattpa said:**
> Just prompts for my password the returns to a prompt??
What should happen ?

You should be able to just enter your password and get some information back.

> **hattpa said:**
> Just looking again, nautilus seems to loose the shares I've set?
Now trying to do this again I get the error message
'net usershare' returned error 255: net usershare add: failed to add share ukulele. Error was Operation not permitted
Worked before though.  What have I done wrong???

I don't use the nautilus shares system, so I'm not sure what the deal is. What does smbtree return?

---

### Post by Y^2om&amp;#7sgP on 2013-06-06
Thanks again for the reply
I've given up with Nautilus-share.  It always worked fine, but at the same time that I got the new router, it seems that there was an update which now means nautilus-share doesn't work.
I found a link which gives a guide to setting up samba, I had set this up once before on an Arch based distro and it was a real pain, but on Ubuntu it's sooooo simple.
That's now installed and working (hooray)
Thanks again CharlesA for the help, much appreciated :KS

---

### Post by CharlesA on 2013-06-06
Outstanding. I've been using normal Samba for a long time now, so glad it works for you. :)

---

