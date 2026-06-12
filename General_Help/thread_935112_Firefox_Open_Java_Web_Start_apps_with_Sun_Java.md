---
title: "Firefox Open Java Web Start apps with Sun Java"
date: 2008-10-01
forum: General Help
---

### Post by lazerradial2003 on 2008-10-01
Does anyone know how to setup firefox to open JNLP files with the "Sun Java 6 Web Start" plugin rather than the Open JDK one? In firefox preferences there is no option to select it and I don't know where the relevant files are stored. 

Sadly open JDK doesn't work with some of the web start apps I use and at the moment I'm having to save the JNLP file to the desktop and use open with to open it with the Sun version.

Cheers

---

### Post by TheguywholikesLINUX on 2009-04-01
I am having the same problem, I did it before on my old install, but I have forgotten the commands. :( I should post all my commands and fixes on my blog.

Anyway, there should be a way to reconfigure java webstart to use the sun one rather than the openjdk one, which has a wired line height that makes some of the apps I use not work properly.

If anyone can tell me what to install (I think you needed a 32bit thingy as there is none for 64bit) or what command you need to type to install it.

Thanks in advance!

---

### Post by markharding557 on 2009-04-01
are you using 64bit? i don't think the normal sun java is available on 64bit.

---

### Post by TheguywholikesLINUX on 2009-04-02
I have done it before on my old 64bit install, I just can't seem to do it again :(
I am still working out how to do it, and I will keep you informed on any progress.

---

### Post by TheguywholikesLINUX on 2009-04-02
YES, w00t! I did it! Yeah :popcorn: :!: :idea: \\:D/ :cool: :D :mrgreen: 8) 

I will try to post how ASAP, but you may have to wait a few days, post here if you want to know how.

P.S. I also got the IcedTea firefox amd64 plugin working aswell as the **sun** java webstart.

---

### Post by abonnema on 2009-06-19
> **TheguywholikesLINUX said:**
> YES, w00t! I did it! Yeah :popcorn: :!: :idea: \\:D/ :cool: :D :mrgreen: 8) 

I will try to post how ASAP, but you may have to wait a few days, post here if you want to know how.

P.S. I also got the IcedTea firefox amd64 plugin working aswell as the **sun** java webstart.

Please post, I would very much like to know how to make the SUN jdk my default in stead of OPENJDK. I have an AMD64 machine running Ubuntu 64 bits (and am very happy with it) .

---

### Post by TheguywholikesLINUX on 2009-06-19
OK, I will get to it when I come back if I have time, if not basically you need to uninstall *all* java packages and install ia32-sun-java6-jre or similar (I will check when I get back).

---

### Post by abonnema on 2009-06-21
> **TheguywholikesLINUX said:**
> OK, I will get to it when I come back if I have time, if not basically you need to uninstall *all* java packages and install ia32-sun-java6-jre or similar (I will check when I get back).

In the meantime I will start playing around, trying to get the sun java running (as default).

Thanks for your reply.

---

### Post by TheguywholikesLINUX on 2009-06-21
Ok heres how I did it:

first go into synaptic and search for java (use the search button not the quick search box) purge every java package that you have installed (there are other packages that will show up in the list as well, it is a pretty comprehensive search).

Then install the package:
ia32-sun-java6-bin

Once that is done restart firefox and it should recognize .jnpl files and be able to start them automatically.

If you wan't the firefox plugin then after you have installed ia32-sun-java6-bin install:
icedtea5-plugin

And that is all there is too it.

I think the problem is when there are conflicting java versions firefox uses the original one and not the one you want it to use, so that is why you have to purge ("Mark for complete removal" in synaptic) to get it to remove the old versions completely, then you have to install just the new one so that firefox sees that and uses it. I think you can install other versions after that and it should still work.

---

