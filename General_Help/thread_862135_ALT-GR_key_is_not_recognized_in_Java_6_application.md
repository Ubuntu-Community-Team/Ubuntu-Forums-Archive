---
title: "ALT-GR key is not recognized in Java 6 applications"
date: 2008-07-17
forum: General Help
---

### Post by angelinux on 2008-07-17
Hi everybody!

I have this problem on Ubuntu 8.0.4. The keyboard layout is Italian.

Everything works well, except that in every java-based application, when run under jdk 1.6 (only) the ALT-GR on the keyboard is not recognized, and simply the "normal" character associated to the pressed key is typed. 

For who doesn't have familiarity with the Italian keyboard, characters no longer typed are @ # {} [] 

This problem affects ONLY the Java applications, and .... only my laptop. My coworkers have the same softawre combinations, and no problems on the keyboard.

Does someone have any idea???

Thanks

---

### Post by angelinux on 2008-07-17
I finally found:

```
export AWT_TOOLKIT=MToolkit
```

That resolve the keyboard issues.

---

### Post by hena on 2008-12-12
I had similar problem that I couldn't use $ in Finnish keyboard (which also requires the use of ALT-GR) in java 6 web start applications logins password line. However this seems to have helped as I tried it from command line and it worked. Eg.

```
AWT_TOOLKIT=MToolkit javaws http://server/dir/program.jnlp
```

---

