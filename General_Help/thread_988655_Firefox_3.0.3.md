---
title: "Firefox 3.0.3"
date: 2008-11-20
forum: General Help
---

### Post by nigel_salvador on 2008-11-20
When I go to certain sites Firefox automatically shuts down. How do I prevent this from happening.Thanks.

---

### Post by waapwoop1 on 2008-11-20
more information!

---

### Post by andlinux21 on 2008-11-20
Sounds like a bug try to make note of what sites you are on when that happens.

---

### Post by prshah on 2008-11-20
> **nigel_salvador said:**
> When I go to certain sites Firefox automatically shuts down. How do I prevent this from happening.Thanks.
> **waapwoop1 said:**
> more information!

Yes, please give more information. [indent]
a) Is it reproducible?
b) Is it the same site everytime?
c) What version/type of Ubuntu, firefox, flash, Java?
[/indent]

You can also launch firefox from a Terminal (Applications-Accessories-Terminal) with the command ```
firefox
``` This will produce a bunch of output in the terminal. The next time firefox shuts down, posting back the last 20+ lines in the terminal will help in debugging.

---

### Post by nigel_salvador on 2008-11-20
Thanks, I will try that and keep you posted

---

### Post by nigel_salvador on 2008-11-20
I launched firefox from the terminal but there was no output displayed

---

### Post by nigel_salvador on 2008-11-20
I tried to launch [http://icedotcom.blogspot.com](http://icedotcom.blogspot.com) and the firefox automatically shut down

---

### Post by kostkon on 2008-11-20
I think it may be Flash related. Which version of Flash are you using? Which version of Ubuntu?

---

### Post by nigel_salvador on 2008-11-21
How do I check which version of Flash i'm using. As for the version of Ubuntu, I amusing 8.04 (Hardy Heron)

---

### Post by clhsharky on 2008-11-21
about:plugins  in ff, look at shockwave.
Check your logs will tell lots.
I have 8.10 ub with 3.0.4 ff and adobe 64 bit alfa. flash.
It loads and works - but that is very busy sight for flash, ad-blocks,redirects. I know its not easy.

---

### Post by kostkon on 2008-11-21
> **nigel_salvador said:**
> How do I check which version of Flash i'm using. As for the version of Ubuntu, I amusing 8.04 (Hardy Heron)
Since you are using 8.04 then I assume you have *Flash 9* (and maybe you have also the *libflashsupport* package).

*Flash 9* causes Firefox to crash in some sites, especially when combined with *libflashsupport*.

You could install *Flash 10*, which is more stable and you don't to need to have *libflashsupport* installed anymore (which is the cause for most of the *Flash* related crashes).

Thus, if you indeed have *Flash 9*, then open *Synaptic*, search for the *flashplugin-nonfree* package, left-click on it and select it for **complete removal**. Afterwards, search for the *libflashsupport* package and if it is installed then select it for removal. Hit the *Apply* button to remove both of them. Close *Synaptic*.

After doing the above, you can then visit Adobe's download page for *Flash* and download the *Flash 10* deb file for 8.04. Double click on it to install it.

Alternatively, you can activate the *Partner* repository and install *Flash 10* from there. Go to *System &#8594; Administration &#8594; Software Sources* and in the *Third-Party Software* tab you should see the entry for this repository. If it is not enabled, then enable it, hit *Close* and then *Reload*. Then go to *Synaptic*, search for the *adobe-flashplugin* package and select it for installation and hit *Apply*.

Hope that helps.

---

