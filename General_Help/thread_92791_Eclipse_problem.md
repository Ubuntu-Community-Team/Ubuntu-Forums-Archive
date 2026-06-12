---
title: "Eclipse problem"
date: 2005-11-20
forum: General Help
---

### Post by frank_y on 2005-11-20
I'm having a problem running eclipse. I downloaded the tgz which worked fine on ubuntu hoary hedgehog but on breezy it gives me an error saying I am missing the default java perspective, even though the debug perspective works fine. It starts with a blank window because of that.

When I install it through apt-get it works, and it makes the one I downloaded work too.

Any ideas?

Thanks,

Frank

---

### Post by jliedeka on 2005-11-20
Did you upgrade from Hoary to Breezy?  I did and had to do an update-alternatives for java because Breezy wanted the gij stuff as the default.

---

### Post by jliedeka on 2005-11-20
duplicate, my browser freaked out or something

---

### Post by frank_y on 2005-11-20
So the problem is that gij doesn't run eclipse properly? I didn't upgrade, so gij is all I have. update-alternatives doesn't show the sun java as an alternative, and I think I have all the ubuntu repositories so I'm not sure what's wrong.

---

### Post by jliedeka on 2005-11-20
There are 4 options for Java under linux (okay more) but I think Sun is the way to go.  The problem is that if you want to set it up the Debian way, it involves building packages from the Sun distro.  

There's some really good info here: [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

